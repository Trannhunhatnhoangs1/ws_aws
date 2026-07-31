---
title: "Upload Data to Amazon S3"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Data Storage Organization on AWS

In an MLOps architecture, **Amazon S3 (Simple Storage Service)** serves as the central "Data Lake". To process data and train models using SageMaker, raw data and processing source code must first be pushed to S3.

We will use a Python script with the `boto3` library to automate the process of pushing raw data and source code to the cloud, rather than doing it manually on the AWS Console. This ensures fast data synchronization and adheres to the MLOps principle of automation.

---

### 1. Prepare Local Directory

In your local project directory structure, ensure that the raw data and source code are in the correct locations:

- `data/raw/T1.csv`: The original, unprocessed SCADA sensor dataset.
- `src/preprocessing.py`: The Python script containing data cleaning and processing logic.
- `scripts/setupS3.py`: The script to automatically push data to S3 using `boto3`.

---

### 2. Automate S3 Upload with Boto3

Instead of manually creating each folder in the AWS UI, the `setupS3.py` script will automatically connect to S3 using your IAM Role and push the files to their proper locations in the bucket.

Open a Terminal at the root of the project and run the S3 upload script:

```bash
# Ensure you are in the virtual environment
.\.venv\Scripts\python scripts/setupS3.py
```

**The execution process will display output similar to the following:**

```text
📂 Uploading raw data...
 ⬆️ data/raw/T1.csv → s3://amznce23/T1_AD/data/raw/T1.csv

📂 Uploading source code (src/)...
 ⬆️ src/preprocessing.py → s3://amznce23/T1_AD/scripts/src/preprocessing.py

📂 Uploading entry-point script...
 ⬆️ src/preprocessing.py → s3://amznce23/T1_AD/scripts/preprocessing.py

🎉 Upload complete!
 Raw data : s3://amznce23/T1_AD/data/raw/T1.csv
 Scripts : s3://amznce23/T1_AD/scripts/
```

*(Note: The bucket name `amznce23` and prefix `T1_AD` are pre-configured in the `setupS3.py` file. You can adjust these parameters to match your own bucket if necessary).*

---

### 3. Verify Results on AWS Console

1. Access the **AWS Management Console** and open the **Amazon S3** service.
2. Find and click on your bucket (e.g., `amznce23`).
3. Navigate to the `T1_AD/` folder (or your configured project name).
4. You will see two important directory structures created, containing files:
   - `data/raw/`: Contains the `T1.csv` file.
   - `scripts/`: Contains the preprocessing scripts (`preprocessing.py`).

{{% notice success %}}
**Complete:**
Congratulations! Your raw data and source code have been safely uploaded to the Data Lake. The "raw materials" are now ready to be fed into SageMaker's automated data processing server in the next step.
{{% /notice %}}