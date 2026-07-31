---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Deploying an MLOps System for SCADA Anomaly Detection on AWS

In this workshop section, our team will provide a detailed guide on how to deploy an end-to-end Machine Learning Operations (MLOps) system on the AWS platform to solve the problem of anomaly detection from SCADA sensor data.

The project architecture replaces manual operations by automating the entire machine learning lifecycle: from setting up a data storage space (Data Lake) and security authorization, to training the XGBoost model (handling class imbalance), optimizing hyperparameters (HPO), and managing model versions in the cloud.

#### Content

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Upload Data to Amazon S3](5.3-Upload-S3/)
4. [Data Preprocessing with SageMaker](5.4-Processing/)
5. [Model Training and Management](5.5-SageMaker/)
6. [Monitor Endpoint with CloudWatch](5.6-Monitor-CloudWatch/)
7. [Create SNS Notification](5.7-Create-SNS-Notification/)
8. [Set up IAM Policy](5.8-Policy/)
9. [Resource Cleanup](5.9-Cleanup/)