---
title: "Week 1 Worklog"
date: 2026-05-31
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Weekly Objectives:

* Grasp the overall business context of the anomaly detection problem for Wind Turbines using industrial SCADA data.
* Familiarize with the Amazon Web Services (AWS) cloud computing ecosystem, specifically focusing on fundamental storage, computing, and identity access management services.
* Successfully configure the local development environment and establish a secure programmatic API connection to the cloud account.
* Conceptualize and architect the blueprint for the Hybrid Machine Learning system (Local-Hybrid MLOps Workflow).

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Business and Data Analysis:**<br>&emsp; + Survey project documentation and the raw SCADA datasets (`T1_train.csv`, `T1_test.csv`).<br>&emsp; + Analyze the structural specifications of the time-series data, identifying core features such as Wind Speed and LV ActivePower. <br>&emsp; + Unify the technical approach: Utilize Unsupervised Learning models to detect sensor faults or mechanical performance degradation. | 01/06/2026 | 01/06/2026 | <https://www.kaggle.com/code/aliakbaryaghoubi/wind-turbine-status-classification-via-power-curve> |
| Tue | - **MLOps System Architecture Research:** <br>&emsp; + Investigate the standard lifecycle of an MLOps pipeline: Data Engineering → Training → Evaluation → Model Registry. <br>&emsp; + Finalize the Local-Hybrid architecture strategy: Execute data processing and preprocessing locally, and leverage the AWS cloud to offload Training Jobs, optimizing costs while bypassing personal hardware limitations. | 02/06/2026 | 02/06/2026 | <https://aws.amazon.com/sagemaker/mlops/> |
| Wed | - **AWS Account Initialization & Configuration:** <br>&emsp; + Install the AWS Command Line Interface (CLI) on the local workstation. <br>&emsp; + **Hands-on Practice:** Utilize the `aws configure` command to securely map credentials via Access Key ID and Secret Access Key, setting the default region to `ap-southeast-1` (Singapore). | 03/06/2026 | 03/06/2026 | <https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html> |
| Thu | - **Security and Access Management (AWS IAM):** <br>&emsp; + Explore core IAM concepts including Users, Groups, Policies, and Roles, strictly applying the Principle of Least Privilege. | 04/06/2026 | 04/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html> |
| Fri | - **Cloud Storage Infrastructure Setup (Amazon S3):** <br>&emsp; + Research AWS Object Storage (Amazon S3) and evaluate its structural advantages over Block Storage (EBS) for handling Machine Learning Data Lakes. <br>&emsp; + **Hands-on Practice:** Access the AWS Management Console to provision a Globally Unique S3 Bucket. Establish a baseline Data Lake directory hierarchy, preparing the infrastructure for automated data and source code ingestion in the upcoming weeks. | 05/06/2026 | 05/06/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |

### Results Achieved in Week 1:

*   **Business Knowledge Mastery:** Gained a deep understanding of the time-series nature of industrial SCADA systems. Successfully defined the core objective of the Anomaly Detection problem for Wind Turbines, establishing a solid theoretical foundation for the subsequent feature engineering phase.
*   **Cloud Infrastructure Proficiency:** Mastered the fundamental concepts of AWS cloud computing, particularly the core services that act as the backbone of this project: Amazon S3 (Unstructured Object Storage), AWS IAM (Identity & Access Control), and the automated cloud computing provisioning model.
*   **Successful Environment Setup:** 
    *   Configured the AWS CLI on the local machine flawlessly. Environment variables and Credentials are securely managed, guaranteeing seamless, uninterrupted two-way API communication between the local workstation and the AWS Cloud.
*   **Cloud Practice & Preliminary Troubleshooting:** 
    *   Successfully initialized the Amazon S3 Bucket. This serves as a critical architectural milestone, enabling the automation of data ingestion pipelines (via Python Boto3) into the Data Lake next week.
*   **Systems Engineering Mindset:** Clearly mapped out the Local-Hybrid MLOps Workflow. Solidified the architectural justification for offloading resource-heavy computations (Model Training) to Amazon SageMaker rather than executing them locally a decision that demonstrates a strong grasp of FinOps (cost optimization) and scalable engineering practices.