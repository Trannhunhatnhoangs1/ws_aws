---
title: "Data Preprocessing with SageMaker"
date: 2026-07-30
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Automated Preprocessing with SageMaker Processing Job

In real-world projects, raw data (SCADA data) often contains anomalies, missing values, and formatting issues making it unsuitable for direct ingestion into machine learning models. Furthermore, processing large-scale data (Big Data) requires substantial compute power that local machines cannot handle.

To solve this, AWS provides **SageMaker Processing Job**. This feature allows us to provision a cluster of cloud instances, download the processing source code (`preprocessing.py`) and raw data from S3 to these instances, execute the code, and finally push the processed data back to S3.

---

### 1. Data Engineering Script

The `preprocessing.py` script (running on SageMaker) is the core of cleaning the SCADA data. In this phase, we applied specialized technical solutions tailored to physical laws rather than purely statistical methods:

1. **Label Error Handling:** The original data had no labels. We fixed the meaningless label assignment issue and created an accurate `Label_Error` column (0: Normal, 1: Error). This output allows immediate use of supervised learning models like XGBoost.
2. **Trigonometric Wind Direction:** Removed the raw wind direction column (0-360 degrees). While 1 degree and 359 degrees are physically very close, a computer sees them as 358 units apart. By generating 2 new columns, `Wind_Dir_Sin` and `Wind_Dir_Cos`, the algorithm perfectly understands the circular, cyclical nature of wind direction.
3. **Outlier Integrity:** Instead of using Z-Score or IQR to cap and squash extreme values to the mean, we preserved these anomalous points. In predictive maintenance, anomalies are the "footprints of failure." Capping them would erase crucial evidence. We only cleaned physically impossible noise (e.g., a turbine generating negative power).
4. **Time Awareness Integration:** Added 2 columns, `Month` and `Hour`. This gives the XGBoost model (which is natively blind to time indices) the ability to learn hidden patterns, such as errors frequently occurring on winter nights.
5. **Dimensionality Optimization:** Instead of creating numerous Rolling Mean and Std columns that bloat the dataset and confuse the model with multicollinearity, we kept only a simple `Lag_1` column (data from 10 minutes prior) to give the model a sense of system "inertia".

---

### 2. Execute Processing Job on AWS

To instruct SageMaker to provision the server and run the `preprocessing.py` script, we use the `sagemaker.sklearn.processing` library via our local script `processing_job.py`.

Open a Terminal and run the following command:

```bash
# Ensure you are in the virtual environment
.\.venv\Scripts\python aws/processing_job.py
```

**System Workflow:**
1. Initializes a `SKLearnProcessor` with Python 1.2 environment and an `ml.t3.medium` instance type.
2. Creates input streams (`ProcessingInput`): Pulls raw data from `s3://.../data/raw/` and source code from `s3://.../scripts/src/` into the SageMaker instance.
3. Executes the `preprocessing.py` script.
4. Creates output streams (`ProcessingOutput`): Pushes the resulting files (`train.csv`, `test.csv`, `processed.csv`) back to S3.

**Console Output Upon Completion:**

```text
Submitting SageMaker Processing Job...
...
Processing Job complete!
 Processed : s3://amznce23/T1_AD/data/processed/
 Train     : s3://amznce23/T1_AD/data/features/train/
 Test      : s3://amznce23/T1_AD/data/features/test/
```

{{% notice tip %}}
**Ready for Training:**
The data is now split into Train/Test, deeply cleaned, and saved in their respective S3 directories. In the next step, we will feed this data into the XGBoost algorithm to begin learning.
{{% /notice %}}