---
title: "Week 7 Worklog"
date: 2026-07-19
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Weekly Objectives:

* Establish a comprehensive benchmarking pipeline for the three deployed algorithms (GMM, iForest, LSTM-AE).
* Measure the empirical performance of each model based on the established ground truth.
* Select the optimal model to proceed with packaging and deployment on AWS infrastructure.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Metrics Calculation:**<br>&emsp; + Apply the Scikit-learn library to extract the classification report.<br>&emsp; + Calculate Precision, Recall, and F1-Score metrics for each model based on the consolidated DataFrame. | 13/07/2026 | 13/07/2026 | <https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics> |
| Tue | - **Performance Visualization:** <br>&emsp; + Plot the ROC (Receiver Operating Characteristic) curve for all 3 models on the same chart. <br>&emsp; + Calculate the Area Under the Curve (AUC) to evaluate the models' label separation capacity independent of thresholds. | 14/07/2026 | 14/07/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_curve.html> |
| Wed | - **Trade-off Analysis:** <br>&emsp; + Evaluate the cost weight between Type I errors (False Positives) and Type II errors (False Negatives). <br>&emsp; + Recalibrate the decision threshold to prioritize the Recall metric, minimizing the risk of undetected turbine failures. | 15/07/2026 | 15/07/2026 | |
| Thu | - **Optimal Model Selection:** <br>&emsp; + Based on the aggregated quantitative results from the F1-Score and AUC, conduct a head-to-head performance comparison between the traditional machine learning and deep learning blocks. <br>&emsp; + Formally decide which algorithmic architecture is most suitable for the project's time-series monitoring task. | 16/07/2026 | 16/07/2026 | |
| Fri | - **Model Packaging:** <br>&emsp; + Serialize the architecture, weights, and preprocessing objects of the Best Fit model into a standard `.pkl` format file. <br>&emsp; + Isolate the library environment (`requirements.txt`) in preparation for the integration pipeline onto AWS SageMaker. | 17/07/2026 | 17/07/2026 | |

### Results Achieved in Week 7:

*   **Benchmarking Report Establishment:** Completed the quantitative evaluation for the three algorithmic architectures (GMM, iForest, LSTM-AE). Based on classification performance metrics (Precision, Recall, F1-Score) and the area under the curve (ROC-AUC), the model with the best noise separation capability was identified using the baseline ground truth.
*   **Cost-sensitive Adjustment:** Applied trade-off analysis on the confusion matrix. The model's classification threshold was recalibrated to maximize the Recall metric, prioritizing early detection of fault signals (reducing False Negatives) to meet equipment risk management requirements.
*   **Artifacts Packaging:** The highest-performing model was extracted into static files (`.pkl` format). The data preprocessing block and execution environment configuration were successfully isolated, establishing deployment readiness for the cloud platform.