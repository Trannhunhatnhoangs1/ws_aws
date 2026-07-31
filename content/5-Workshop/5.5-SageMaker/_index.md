---
title : "Model Training and Management"
date :  2026-07-30 
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

### The Core of MLOps: Amazon SageMaker

In this practice session, we will proceed with the heaviest computational process of the project: Training the XGBoost algorithm. Running on Amazon SageMaker allows us to easily scale compute resources and automate the entire hyperparameter tuning process, as well as model version management.

Specifically, to solve the class imbalance problem of industrial SCADA data, we will configure the `scale_pos_weight` parameter directly into the training pipeline.

---

### 1. Initializing Training Job

We use the `sagemaker` library (Python SDK) on the local machine to define an **Estimator**. This Estimator will inform AWS about what type of virtual server (EC2) to rent, where to get the data, and what algorithm to run.

Create a Jupyter Notebook file or Python script on the local machine and run the following configuration snippet:

```python
import sagemaker
from sagemaker.xgboost.estimator import XGBoost

# Retrieve the established execution role
role = 'arn:aws:iam::<ACCOUNT_ID>:role/SageMaker-SCADA-ExecutionRole'

# Configure XGBoost Estimator
xgb_estimator = XGBoost(
    entry_point='train.py', # Script containing the team's training source code
    role=role,
    instance_count=1,
    instance_type='ml.m5.large', # Server used for training
    framework_version='1.3-1',
    output_path='s3://scada-mlops-project-bucket-2026/model-artifacts/', # Where to save model.tar.gz
    hyperparameters={
        'objective': 'binary:logistic',
        'eval_metric': 'aucpr', # Optimize on Area Under the PR Curve (Precision-Recall)
        'scale_pos_weight': '99', # Compensate for rare SCADA anomaly data
        'num_round': '100'
    }
)

# Trigger the training process with data from S3
xgb_estimator.fit({'train': 's3://scada-mlops-project-bucket-2026/processed-data/train.csv',
                   'validation': 's3://scada-mlops-project-bucket-2026/processed-data/validation.csv'})

```

---

### 2. Automatic Hyperparameter Tuning (HPO)

Instead of manually experimenting with parameters (`max_depth`, `eta`, `subsample`...), we will set up a **Hyperparameter Tuning Job**. SageMaker will automatically generate multiple Training Jobs in parallel or sequentially to find the parameter combination that yields the highest F1-Score (or AUCPR).

![image](/images/5-Workshop/5.4-SageMaker/HPO.png)

---

### 3. Model Registry

After HPO is complete and the model is evaluated via the Test set, the obtained Metrics will be saved in the `evaluation.json` file. The Best Model along with these metrics will automatically be pushed into the **SageMaker Model Registry**.

Model Registry acts as a central repository for model versioning.

**Approval Workflow:**
When a new model version is successfully registered into a Model Package Group, its default status will be **PendingManualApproval**. It cannot be immediately put into production (Deploy to Endpoint).

The MLOps Engineer (or Project Manager) needs to access the interface, evaluate the results file, and change the status to **Approved** to complete the lifecycle.

![Model Registry](/images/5-Workshop/5.4-SageMaker/Model_Registry.png)

{{% notice success %}}
**Training Completion:**
At this step, you have successfully automated the training, evaluation, and versioning flow. In the next lab, we will delve into setting up security IAM Policies behind the scenes to ensure the entire above process runs smoothly.
{{% /notice %}}
