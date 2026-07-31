---
title: "Week 4 Worklog"
date: 2026-06-21
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Weekly Objectives:

* Construct a pseudo-labeling database based on the deviation between the Actual Power and Theoretical Power of the wind turbine.
* Establish objective statistical thresholds to classify the boundary between Normal (0) and Anomalous (1) operational states.
* Generate a small-scale Ground Truth dataset to serve as an evaluation metric for Unsupervised Learning models in subsequent phases.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Residual Calculation:**<br>&emsp; + Apply the Power Curve equation interpolated from Week 2 to calculate the expected Theoretical Power for each Wind Speed level.<br>&emsp; + Subtract the Theoretical Power from the Actual Power to obtain the residual array for each data point. | 22/06/2026 | 22/06/2026 | <https://numpy.org/doc/stable/reference/generated/numpy.subtract.html> |
| Tue | - **Statistical Thresholding:** <br>&emsp; + Analyze the distribution of the residual dataset. <br>&emsp; + Apply the Interquartile Range (IQR) method to determine the Upper Control Limit (UCL) and Lower Control Limit (LCL), isolating data points that fall outside the system's normal variance. | 23/06/2026 | 23/06/2026 | <https://docs.scipy.org/doc/scipy/reference/stats.html> |
| Wed | - **Pseudo-labeling Implementation:** <br>&emsp; + Program a mapping function utilizing Pandas. <br>&emsp; + Assign label `1` (Anomaly) to data points with residuals exceeding the control limits, and label `0` (Normal) to points within the safe operational margin. | 24/06/2026 | 24/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html> |
| Thu | - **Sanity Check Visualization:** <br>&emsp; + Reconstruct the scatter plot of Wind Speed versus Actual Power. <br>&emsp; + Color-code the plot to differentiate between label `0` and `1`, visually verifying whether the physical rules align with the actual clustering state. | 25/06/2026 | 25/06/2026 | <https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html> |
| Fri | - **Label Integration:** <br>&emsp; + Directly integrate the pseudo-label array as a new feature into the current in-memory DataFrame structure for the upcoming pipeline. <br>&emsp; + Evaluate the class distribution to quantify the degree of data imbalance. | 26/06/2026 | 26/06/2026 | |

### Results Achieved in Week 4:

*   **Baseline Labeling Construction:** Successfully resolved the core obstacle of industrial SCADA data: the lack of labels (unlabeled data). By standardizing physical residuals into binary labels, the project has established a benchmark dataset for model evaluation.
*   **Statistical & Mathematical Basis:** The application of the Interquartile Range (IQR) method on the residual distribution provides a non-parametric evaluation technique to identify outliers. This technique establishes control thresholds based on actual data dispersion, mitigating reliance on normal distribution assumptions, thereby quantifying the boundary between natural power fluctuations and abnormal equipment states.
*   **Benchmarking Establishment:** Provided a quantifiable reference frame. This pseudo-label dataset acts as the foundational "Ground Truth," enabling direct measurement of accuracy metrics (Precision, Recall, F1-Score) for clustering algorithms in upcoming weeks, thoroughly overcoming the non-quantifiable weakness of traditional Unsupervised Learning pipelines.