---
title: "Week 3 Worklog"
date: 2026-06-14
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Weekly Objectives:

* Transform the cleaned SCADA dataset into optimal mathematical signals for Machine Learning models.
* Design dynamic features to capture the physical variation derivative of the mechanical system.
* Eliminate measurement unit discrepancies (m/s, kW, °C) using data space normalization techniques.
* Evaluate and extract the 6 core features that contribute the highest variance to the entire dataset.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Correlation Analysis:**<br>&emsp; + Utilize correlation matrices and Seaborn's Heatmap to analyze the linear relationships among all sensor variables in the SCADA file.<br>&emsp; + Eliminate variables with high multicollinearity to reduce noise and computational complexity for subsequent modeling. | 15/06/2026 | 15/06/2026 | <https://seaborn.pydata.org/generated/seaborn.heatmap.html> |
| Tue | - **Dynamic Feature Engineering:** <br>&emsp; + Calculate the 1st-order difference (`diff_1`) for the two most critical variables: Wind Speed and Actual Power. <br>&emsp; + Purpose: Shift from solely observing "static values" at a specific timestamp to monitoring the "rate of change" between consecutive timeframes to capture sudden power drops. | 16/06/2026 | 16/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.diff.html> |
| Wed | - **Data Normalization:** <br>&emsp; + Apply the `StandardScaler` (Z-score Normalization) algorithm from the Scikit-learn library. <br>&emsp; + Force all numerical variables into a standard distribution (mean = 0, variance = 1), enabling distance-based algorithms (such as GMM or LOF) to converge rapidly without being biased by physical scales. | 17/06/2026 | 17/06/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html> |
| Thu | - **Core Feature Selection:** <br>&emsp; + Execute variance analysis techniques to evaluate the Feature Importance of each variable. <br>&emsp; + Finalize the list of the 6 optimal features (including both static variables and the `diff_1` dynamic feature) as the input shape for the model training phase. | 18/06/2026 | 18/06/2026 | <https://scikit-learn.org/stable/modules/feature_selection.html> |
| Fri | - **Training Data Packaging:** <br>&emsp; + Convert the data format from Pandas DataFrame to a pure Numpy Array (`.values`) structure to prepare for the AWS SageMaker pipeline flow. <br>&emsp; + Export the `features_train.csv` and `features_test.csv` files. | 19/06/2026 | 19/06/2026 | Internal Data Preparation Documentation |

### Results Achieved in Week 3:

*   **Extraction Results:** Successfully filtered and shaped the 6 core features with the highest variance contribution to the dataset. Completed the data space homogenization process via Z-score normalization, ensuring equitable impact weights for all input variables.
*   **Mathematical & Dynamics Perspective:** The Z-score normalization technique brought measurement variables with distinct physical units (m/s, kW, °C) into a standardized normal distribution space. This operation is a mandatory prerequisite that helps distance calculation algorithms converge stably, simultaneously eliminating model bias caused by absolute scale disparities.
*   **Feature Engineering Optimization:** Deployed the 1st-order difference (`diff_1`) mathematical method to digitize the variation rate of sensor signals over time. Given the high mechanical inertia of the wind turbine system, signal fluctuations with abnormal amplitudes within narrow timeframes typically reflect hardware faults or measurement noise. Integrating this dynamic feature provides the model with a more comprehensive evaluation basis, combining the static value at real-time and the variation acceleration of the system.