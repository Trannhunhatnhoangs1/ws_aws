---
title: "Blog 2"
date: 2026-07-17
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---
## 1. ARTICLE OVERVIEW & PROJECT CONTEXT

* **Author:** Huynh Duy Chuong.
* **Context:** Participating in the *AWS Study Group* program, facing the challenge of optimizing limited study time to achieve the highest efficiency for actual work in an enterprise.
* **Article Objective:** Determine the strategy for allocating study time, shifting from the habit of working on local Jupyter Notebooks to a standardized cloud operations workflow. [LINK](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2226421048122855/?rdid=Qh4KrhITN1dA0Io4#)
---

## 2. PROFESSIONAL ANALYSIS OF KNOWLEDGE PILLARS

The article logically categorizes and prioritizes AWS services according to the ML Lifecycle of a Machine Learning project:

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                       1. Storage & Security Layer                       │
│                         (Amazon S3, AWS IAM, VPC)                       │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       2. MLOps & Training Engine                        │
│             (SageMaker Data Wrangler, Feature Store, HPO,               │
│                        SageMaker Model Registry)                        │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     3. Inference & Deployment Layer                     │
│               (SageMaker Endpoints, API Gateway, AWS Lambda)            │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     4. Monitoring & Governance                          │
│                      (AWS CloudWatch, EC2 Types)                        │
└─────────────────────────────────────────────────────────────────────────┘
```

### A. Cloud Platform & Security (S3, IAM, VPC)

* Many students often overlook this part and jump straight into model training. Understanding **S3** (centralized storage), **IAM** (Least Privilege principle), and **VPC Endpoints** (internal network security) helps ensure enterprise data is not leaked to the Internet.

### B. Standardized MLOps with Amazon SageMaker

* **Feature Engineering & Feature Store:** Shifting from standalone data processing using Pandas to centralized Feature management helps reuse data for multiple models, avoiding Data Leakage / Redundancy.
* **Automatic Hyperparameter Tuning (HPO):** Transitioning from manual parameter guessing to automated parameter space search, freeing up time for engineers to focus on architectural design.
* **Model Registry:** Establish a transparent model versioning process (**v1.0**, **v1.1**, **Approved**). This is the backbone of any modern MLOps pipeline.

### C. Model Deployment & Serverless Architecture

* **SageMaker Endpoints:** Taking the model out of the experimental environment to package it as an API service ready to serve Client applications.
* **API Gateway + AWS Lambda (Serverless):** An optimal choice for the Prototype/Demo phase. This combination helps optimize costs — the system only incurs costs when there are actual API calls.

---

## 3. REFERENCES

* [AWS Documentation: Amazon SageMaker Developer Guide](https://docs.aws.amazon.com/sagemaker/)
* [AWS Architecture Center: MLOps Foundation Roadmap on AWS](https://www.google.com/search?q=https://aws.amazon.com/architecture/mlops/)
* [AWS Workshop: SageMaker Immersion Day Hands-on Labs](https://www.google.com/search?q=https://sagemaker-immersionday.workshop.aws/)