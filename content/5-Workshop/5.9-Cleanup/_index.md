---
title : "Resource Cleanup"
date :  2026-07-30 
weight: 9
chapter : false
pre : " <b> 5.9 </b> "
---

### System Cleanup and Cost Optimization

Cloud computing operates on a pay-as-you-go model. Therefore, after completing the MLOps project development lifecycle or finishing the course, cleaning up and revoking services is a **mandatory operation** for Cost Optimization.

Below is a list of resources you need to review and completely delete from your AWS account.

### Content

1. [Delete SageMaker Endpoints](5.9.1-delete-endpoint/)
2. [Delete SageMaker Model Registry](5.9.2-delete-model-registry/)
3. [Delete Amazon S3 Resources](5.9.3-delete-s3/)
4. [Delete IAM Role](5.9.4-delete-iam/)
5. [Delete CloudWatch and Amazon SNS](5.9.5-delete-cloudwatch-sns/)

{{% notice warning %}}
**Cost Warning (Cloud Billing):**
Carefully check the AWS Billing Dashboard to ensure no compute resources are running in the background. MLOps automation is very convenient, but forgetting to turn off servers can cause you to be unjustly charged overnight!
{{% /notice %}}

![Cleanup Resources](/images/5-Workshop/5.9-Cleanup/cleanup.png)
