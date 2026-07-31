---
title : "Prerequisites"
date :  2026-07-30 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

### Preparing the Working Environment

To successfully deploy the SCADA anomaly detection MLOps system on AWS, you need to prepare both the cloud resources and the programming environment on your local machine. Below are the mandatory requirements.

---

### 1. AWS Account & Access Rights

You need an active AWS account. To ensure security and comply with practical standards, **ABSOLUTELY DO NOT** use the Root account for practice. 

*   **IAM User:** Create a new IAM User and grant this user administrative rights (`AdministratorAccess`) or the right to initialize basic services including: **Amazon S3**, **AWS IAM**, and **Amazon SageMaker**.
*   **Security Credentials:** Create and download the `Access Key ID` and `Secret Access Key` of the newly created IAM User. These are the keys for your local machine to communicate with AWS.
*   **AWS Region:** Determine and remember the Region where you will deploy the project (e.g., `ap-southeast-1` for the Singapore region) to ensure data and models are in the same place, minimizing latency.

![AWS Region](/images/5-Workshop/5.2-Prerequisite/region1.png)
*Hint: Always check and unify the Region in the top right corner of the AWS Management Console.*

---

### 2. Local Machine Environment

All configuration files to call SageMaker services will be written in Python. You need to set up a programming environment on your personal computer.

#### Installing Python and Libraries
Ensure your computer has **Python 3.10+** installed. Then, open Terminal (or Command Prompt) and install essential libraries for the project using the `pip` package manager. For example:

```bash
pip install awscli sagemaker boto3 xgboost pandas scikit-learn

```

**Library Details:**

* `awscli`: The official AWS command-line interface.
* `boto3`: AWS SDK for Python, used to interact with Amazon S3 and IAM.
* `sagemaker`: SageMaker Python SDK, a specialized library for configuring and launching MLOps scripts.
* `xgboost`, `pandas`, `scikit-learn`: Basic data processing and machine learning libraries used for preprocessing and setting up evaluation scripts.

---

### 3. Configuring AWS CLI

After installing the libraries, the most important step is to link your Local environment with your AWS account via AWS CLI.

From Terminal, run the following command:

```bash
aws configure

```

The system will ask you to enter 4 pieces of information sequentially (Use the Security Credentials created in section 1):

1. **AWS Access Key ID [None]:** `AKIAIOSFODNN7EXAMPLE` *(enter your Key)*
2. **AWS Secret Access Key [None]:** `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` *(enter your Secret Key)*
3. **Default region name [None]:** `ap-southeast-1` *(enter your Region code)*
4. **Default output format [None]:** `json`

{{% notice info %}}
**Check connection:**
To ensure AWS CLI is successfully configured, try running the command `aws s3 ls`. If the system returns no errors (displays nothing if there are no buckets, or shows a list of current buckets), your environment is ready!
{{% /notice %}}

---

### 4. Preparing Source Code and Data

Make sure you have the SCADA MLOps project folder ready on your machine containing the following files:

* Raw dataset: `SCADA_data.csv`
* Python Scripts: `train.py` (XGBoost training script) and `evaluate.py` (Model evaluation script).

Once all prerequisites are complete, let's move on to the next practice session to start building our first **Data Lake** on Amazon S3!