---
title : "Introduction"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Introduction to SCADA MLOps System

In real-world industrial processes, predicting and detecting system anomalies early from sensor data (SCADA) plays a vital role in minimizing machine downtime. However, developing a Machine Learning model to solve this problem often encounters two major challenges:

1. **Class Imbalance:** Error signals occur very rarely compared to normal operating states, making models prone to biased predictions.
2. **Operations:** Bringing a model from a personal computer to a production environment requires a strict, transparent, and automatable management process.

This workshop is designed to completely solve the two problems above by building an **End-to-End MLOps** architecture on the AWS platform. We will use the **XGBoost** algorithm combined with a class imbalance control mechanism (`scale_pos_weight`), and automate the entire model lifecycle via **Amazon SageMaker**.

---

### Architecture Diagram

The architecture below describes the data flow and interaction between AWS cloud services in our MLOps system.

![Architecture Diagram](/images/5-Workshop/5.1-Workshop-overview/pic1.png)

---

### Core AWS Service Components

This project is a tight integration of industry-standard cloud services:

*   **Amazon S3 (Simple Storage Service):** Acts as a centralized Data Lake. All data (from raw to clean) and model weight files (`model.tar.gz`) are stored securely and at low cost here.
*   **AWS IAM (Identity and Access Management):** Ensures system security by applying the "least privilege" principle. SageMaker will be granted a separate IAM Role, allowing read/write access only to the project's exact S3 Bucket and writing Logs to CloudWatch.
*   **Amazon SageMaker:** A comprehensive Fully Managed Machine Learning platform, performing 3 main roles:
    1.  *Training:* Automatically provisioning virtual servers (EC2) to run the XGBoost training script.
    2.  *Automatic Model Tuning (HPO):* Automatically launching batches of experiments to find the set of hyperparameters that yield the highest F1-Score.
    3.  *Model Registry:* Managing catalogs, versioning, and integrating a manual Approval Workflow before putting the model into use.
*   **Amazon CloudWatch:** A real-time monitoring service. The entire process of calculating loss functions, epoch logs, and metrics is recorded here, helping engineers easily monitor and debug.