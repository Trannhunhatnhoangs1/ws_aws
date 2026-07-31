---
title : "Setting up IAM Policy"
date :  2026-07-30 
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

### Secure Authorization with AWS IAM

In AWS, services do not automatically have access to each other to ensure security. For Amazon SageMaker to automatically pull SCADA data from S3, write training process logs, and register models to the Model Registry, it needs a secure identity. 

This practice session guides you on creating an **IAM Execution Role** for SageMaker based on the principle of least privilege.

---

### Steps to create SageMaker Execution Role

1. Log in to the **AWS Management Console**, search for and open the **IAM (Identity and Access Management)** service.
2. On the left menu bar, select **Roles** and click the **Create role** button.
3. **Select trusted entity:**
   * Trusted entity type: Select **AWS service**.
   * Use case: Search the list and select **SageMaker**, then proceed to select **SageMaker - Execution** in the dropdown options.
   * Click **Next**.
4. **Add permissions:**
   * AWS will automatically attach the `AmazonSageMakerFullAccess` policy.
   * Because SageMaker needs to read/write data to the Data Lake, you need to grant additional S3 access permissions. Search for the keyword `S3` and check the `AmazonS3FullAccess` policy.
   * *(Note: In strict corporate environments, you should not use FullAccess rights but rather write a Custom Policy granting Read/Write access exactly to the project's bucket name `scada-mlops-project-bucket-2026`)*.
   * Click **Next**.
5. **Name, review, and create:**
   * **Role name:** Set a memorable name for the project, e.g., `SageMaker-SCADA-ExecutionRole`.
   * Review the list of added permissions.
   * Scroll down to the bottom and click **Create role**.

![IAM Role Creation](/images/5-Workshop/5.5-Policy/iam-role.png)

---

### System Monitoring

{{% notice info %}}
**Automatic Logging Permission:**
You do not need to grant individual permissions for monitoring. The default `AmazonSageMakerFullAccess` policy already includes basic permissions (like `logs:CreateLogGroup`, `logs:CreateLogStream`, `logs:PutLogEvents`) so SageMaker can automatically push Loss function parameters and Errors while running the XGBoost algorithm to the **Amazon CloudWatch** service.
{{% /notice %}}

Upon completing this step, your security architecture is solid. Let's move on to the final part: **Resource Cleanup** to ensure no unexpected costs arise after finishing the course.
