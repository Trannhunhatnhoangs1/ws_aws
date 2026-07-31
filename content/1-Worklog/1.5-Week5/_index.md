---
title: "Week 5 Worklog"
date: 2026-06-28
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Weekly Objectives:

* Implement traditional Unsupervised Learning algorithms for anomaly detection based on standardized features.
* Develop a Gaussian Mixture Model (GMM) to evaluate anomalies based on probability density distribution.
* Construct an Isolation Forest (iForest) model to evaluate anomalies utilizing a tree-based branching structure.
* Store anomaly scores from each model to facilitate the comprehensive benchmarking phase in the evaluation week.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **GMM Model Training:**<br>&emsp; + Initialize the Gaussian Mixture Model from the Scikit-learn library.<br>&emsp; + Fine-tune the `n_components` hyperparameter based on the BIC/AIC information criterion to accurately model the turbine's operational states (cut-in, rated, cut-out). | 29/06/2026 | 29/06/2026 | <https://scikit-learn.org/stable/modules/mixture.html> |
| Tue | - **Log-Likelihood Extraction (GMM):** <br>&emsp; + Calculate the log-likelihood function for each data point in the Test set. <br>&emsp; + Points falling into extreme low-probability distributions (exceeding the lower percentile threshold) are assigned the anomaly prediction label. | 30/06/2026 | 30/06/2026 | |
| Wed | - **Isolation Forest Model Training:** <br>&emsp; + Build the model based on the ensemble learning algorithm. <br>&emsp; + Configure the `contamination` hyperparameter (expected anomaly rate) based on the class imbalance ratio calculated from the Week 4 pseudo-labels. | 01/07/2026 | 01/07/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html> |
| Thu | - **Anomaly Score Extraction (iForest):** <br>&emsp; + Extract the average path length from root to leaf for the data points. <br>&emsp; + Identify points with the shortest branching depth (most easily isolated) as equipment fault warning signals. | 02/07/2026 | 02/07/2026 | |
| Fri | - **Prediction Aggregation:** <br>&emsp; + Create a DataFrame for parallel storage of: Ground Truth - GMM Predictions - iForest Predictions. <br>&emsp; + Prepare the data foundation to benchmark against complex Deep Learning models in the subsequent week. | 03/07/2026 | 03/07/2026 | |

### Results Achieved in Week 5:

*   **Traditional Machine Learning Baseline Establishment:** Completed the implementation of two anomaly detection algorithms with orthogonal classification characteristics: GMM (based on probability density estimation) and Isolation Forest (based on data space partitioning). The application of two distinct architectures establishes an objective baseline, mitigating bias caused by algorithmic structures on the SCADA dataset.
*   **Hyperparameter Quantization:** Model configurations were fine-tuned based on specific mathematical metrics. The GMM cluster space (`n_components`) was determined via the minimum value of the BIC/AIC information criterion to accurately reflect the aerodynamic phases of the wind turbine. The iForest `contamination` parameter was directly referenced from the pseudo-label distribution established in Week 4.
*   **Prediction Storage Standardization:** Extracted and merged anomaly scores and prediction labels from both models into a unified DataFrame. This step completes the output data architecture for the traditional ML block, preparing the data readiness for the experimental and comparative phase with the Deep Learning models in the upcoming weeks.