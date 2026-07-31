---
title: "Proposal"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# SCADA Fault Prediction Platform
## An AWS SageMaker-Based Predictive Maintenance Solution

### 1. Executive Summary

The SCADA Fault Prediction Platform is designed to provide an intelligent predictive maintenance solution for industrial equipment using SCADA sensor data. The platform utilizes the publicly available SKAB (Skoltech Anomaly Benchmark) dataset and AWS cloud services to automate the complete machine learning lifecycle, including data preprocessing, feature engineering, model training, evaluation, deployment, and monitoring.

The solution is built primarily on Amazon SageMaker and related AWS services, enabling researchers and students to develop scalable anomaly detection systems with minimal infrastructure management. The platform provides real-time prediction through REST APIs and supports automated model deployment and monitoring.

---

### 2. Problem Statement

### What's the Problem?

Industrial SCADA systems continuously generate large volumes of sensor data. Detecting equipment faults manually is inefficient and often fails to identify abnormal conditions before failures occur. Traditional monitoring methods require significant human effort and cannot easily scale as industrial systems become more complex.

Although machine learning can improve predictive maintenance, deploying an end-to-end ML pipeline requires considerable infrastructure setup, operational effort, and cloud expertise.

### The Solution

The proposed platform leverages Amazon S3 for data storage, Amazon SageMaker Processing Jobs for preprocessing and feature engineering, and SageMaker Training Jobs to train multiple machine learning models such as XGBoost, Isolation Forest, and LSTM. Hyperparameter Optimization (HPO) automatically searches for the optimal model configuration.

The best-performing model is registered in Amazon SageMaker Model Registry and deployed as a SageMaker Endpoint. AWS Lambda and Amazon API Gateway provide REST APIs for real-time predictions, while Amazon CloudWatch and Amazon SNS monitor endpoint health and notify users when abnormal system behavior is detected.

### Benefits and Return on Investment

The platform provides students and researchers with practical experience in building an end-to-end MLOps workflow on AWS. It automates repetitive machine learning tasks, reduces deployment complexity, and creates a reusable architecture for predictive maintenance research.

Compared to manually managing the machine learning lifecycle, the proposed solution improves development efficiency, supports scalable deployment, and simplifies future research projects. Since the project uses the public SKAB dataset, no additional data acquisition cost is required, and AWS Academy credits or Free Tier services can significantly reduce cloud expenses.

---

### 3. Solution Architecture

The proposed architecture follows a complete machine learning workflow. Sensor datasets are stored in Amazon S3, processed using SageMaker Processing Jobs, transformed through feature engineering, and used to train machine learning models. The best model is registered and deployed for online inference. AWS Lambda and API Gateway expose prediction services, while CloudWatch and SNS provide monitoring and alerting.

![SCADA System Architecture](/images/2-Proposal/scada_architecture.png)

### AWS Services Used

- **Amazon S3**: Stores raw datasets, processed datasets, and engineered features.
- **Amazon SageMaker Processing**: Performs preprocessing and feature engineering.
- **Amazon SageMaker Training**: Trains machine learning models.
- **Amazon SageMaker Experiments**: Tracks training experiments.
- **Amazon SageMaker Hyperparameter Optimization**: Tunes model parameters automatically.
- **Amazon SageMaker Model Registry**: Manages model versions.
- **Amazon SageMaker Endpoint**: Provides real-time inference.
- **AWS Lambda**: Processes prediction requests.
- **Amazon API Gateway**: Exposes REST APIs.
- **Amazon CloudWatch**: Monitors endpoint performance.
- **Amazon SNS**: Sends alert notifications.

### Component Design

- **Dataset Layer**: SKAB dataset stored in Amazon S3.
- **Data Processing**: SageMaker Processing performs preprocessing and feature engineering.
- **Model Training**: SageMaker trains multiple ML models and performs hyperparameter optimization.
- **Model Deployment**: The best model is registered and deployed as a SageMaker Endpoint.
- **Prediction API**: Lambda and API Gateway provide prediction services.
- **Monitoring**: CloudWatch monitors system performance and SNS sends alerts.

---

### 4. Technical Implementation

**Implementation Phases**

The project follows four major development phases:

- **Phase 1 – Data Preparation:** Collect the SKAB dataset, perform exploratory data analysis (EDA), clean missing values, and fix meaningless labels (Label_Error).
- **Phase 2 – Feature Engineering:** Process wind direction using trigonometry (Sin/Cos), add time awareness (Month, Hour), optimize dimensionality using lag variables (Lag_1) instead of Rolling statistics, and preserve outliers instead of capping them with Z-scores.
- **Phase 3 – Model Development:** Train XGBoost, Isolation Forest, and LSTM models; compare their performance using F1 Score and AUC-ROC.
- **Phase 4 – Deployment and Monitoring:** Deploy the selected model to SageMaker Endpoint, implement Lambda and API Gateway, configure CloudWatch monitoring, SNS notifications, and SageMaker Pipeline automation.

**Technical Requirements**

- Python 3.10+
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- TensorFlow
- PyTorch
- XGBoost

AWS Services:

- Amazon S3
- Amazon SageMaker
- AWS Lambda
- Amazon API Gateway
- Amazon CloudWatch
- Amazon SNS
- AWS IAM

---

### 5. Timeline & Milestones

**Project Timeline**

- **Week 1:** Dataset collection, AWS environment setup, and exploratory data analysis (EDA).
- **Week 2:** Data preprocessing and feature engineering.
- **Week 3:** Local machine learning model development and performance comparison.
- **Week 4:** Model evaluation, hyperparameter optimization, and best model selection.
- **Week 5:** Upload datasets to Amazon S3 and train the selected model using Amazon SageMaker.
- **Week 6:** Deploy the trained model as a SageMaker Endpoint and develop prediction APIs using AWS Lambda and Amazon API Gateway.
- **Week 7:** Integrate the end-to-end prediction pipeline, configure Amazon CloudWatch monitoring, and create Amazon SNS notifications.
- **Week 8:** Perform final system testing, clean up AWS resources, complete documentation, and prepare the final presentation.
---

### 6. Budget Estimation

Infrastructure costs mainly consist of AWS cloud services:

- Amazon S3
- Amazon SageMaker Processing
- Amazon SageMaker Training
- Amazon SageMaker Endpoint
- AWS Lambda
- Amazon API Gateway
- Amazon CloudWatch
- Amazon SNS

The project is primarily intended for educational purposes and can be deployed using AWS Academy credits or AWS Free Tier resources. Endpoint instances should be terminated after demonstrations to minimize operational costs.

Hardware Cost:

- No additional hardware is required because the project uses the public SKAB dataset.

---

### 7. Risk Assessment

#### Risk Matrix

- Low model prediction accuracy: High impact, medium probability.
- Poor data quality: High impact, medium probability.
- AWS service interruption: Medium impact, low probability.
- Unexpected cloud costs: Medium impact, low probability.

#### Mitigation Strategies

- Apply comprehensive data preprocessing and feature engineering.
- Perform Hyperparameter Optimization to improve model performance.
- Enable CloudWatch monitoring and AWS Budget alerts.
- Stop SageMaker Endpoints immediately after testing.

#### Contingency Plans

- Continue local model development if AWS resources become unavailable.
- Redeploy previously approved models from SageMaker Model Registry.
- Roll back to the previous deployment if performance degrades.

---

### 8. Expected Outcomes

#### Technical Improvements

- Automated end-to-end machine learning workflow.
- Accurate fault prediction using SCADA sensor data.
- Real-time prediction through REST APIs.
- Automated model deployment and monitoring.
- Reproducible MLOps pipeline using AWS.

#### Long-term Value

- A reusable predictive maintenance platform for future industrial applications.
- Practical experience with AWS SageMaker and cloud-based machine learning.
- A scalable foundation for future research in industrial AI and anomaly detection.