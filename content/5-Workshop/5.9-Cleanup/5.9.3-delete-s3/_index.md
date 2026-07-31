---
title: "Delete Amazon S3 Resources"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 5.9.3 </b> "
---

Amazon S3 charges based on the volume of data you store (including raw data, processed data, and model weight files). AWS also establishes a safety mechanism: you cannot delete a Bucket if there is still data inside.

## Step 1: Empty the Bucket

1. Access the **S3 Console**, find the project's bucket (e.g., `scada-mlops-project-bucket-2026`).
2. Select that bucket and click the **Empty** button.
3. AWS will require you to type the phrase `permanently delete` to confirm deleting all CSV data and `model.tar.gz` files.

>![Figure 1](/images/5-Workshop/5.10/delete-s3/bucket.png)
>![Figure 2](/images/5-Workshop/5.10/delete-s3/files.png)

## Step 2: Delete the Bucket Completely

After emptying successfully, return to the Buckets list, select the project bucket again, and click **Delete** to completely remove this container.
