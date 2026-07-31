---
title: "Week 2 Worklog"
date: 2026-06-07
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Weekly Objectives:

* Perform Exploratory Data Analysis (EDA) on the raw wind turbine SCADA dataset to understand data distribution and underlying patterns.
* Identify and thoroughly resolve missing values (NaN) without disrupting the continuity of the time-series data.
* Detect and filter out physical anomalies (e.g., sensor noise, negative active power at high wind speeds) by applying wind energy domain knowledge.
* Visualize and establish the theoretical Power Curve of the turbine to serve as a baseline for normal operational behavior.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Data Loading & Initial Inspection:**<br>&emsp; + Utilize the Pandas library to read the `T1_train.csv` file into a DataFrame.<br>&emsp; + Conduct basic statistical evaluation using the `.info()` and `.describe()` functions to measure data sparsity and isolate missing values (NaNs). | 08/06/2026 | 08/06/2026 | <https://pandas.pydata.org/docs/user_guide/10min.html> |
| Tue | - **Missing Value Imputation:** <br>&emsp; + Analyze the nature of data loss (e.g., short-term network drops vs. long-term telecommunication hardware failures). <br>&emsp; + Apply Linear Interpolation to fill in short-term gaps, strictly preserving the integrity of the time series and preventing algorithmic distortion. | 09/06/2026 | 09/06/2026 | <https://scikit-learn.org/stable/modules/impute.html> |
| Wed | - **Physical Outlier Filtering:** <br>&emsp; + Apply physical constraints to eliminate illogical values (e.g., Actual Power < 0 kW while Wind Speed is within operational range, or Wind Speed exceeding the 25m/s cut-out limit). <br>&emsp; + Clearly differentiate between "Measurement System Noise" (to be discarded) and "Equipment Degradation Signs" (to be retained for model training). | 10/06/2026 | 10/06/2026 | |
| Thu | - **Data Visualization & Power Curve Mapping:** <br>&emsp; + Use Matplotlib and Seaborn to plot a Scatter Plot representing the correlation between Wind Speed (X-axis) and Actual Power (Y-axis). <br>&emsp; + Successfully depict the theoretical Power Curve, clearly visualizing the three operational zones: cut-in, rated, and cut-out wind speeds. | 11/06/2026 | 11/06/2026 | <https://seaborn.pydata.org/tutorial/relational.html> |
| Fri | - **Dataset Standardization:** <br>&emsp; + Perform final Quality Assurance (QA) to ensure a 100% clean dataset. <br>&emsp; + Export the processed data to an intermediate `.csv` format, establishing a robust foundation for the Feature Engineering phase next week. | 12/06/2026 | 12/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html> |

### Results Achieved in Week 2:

*   **Data Quality Assurance:** Successfully resolved 100% of missing values (NaNs) and completely eliminated physical anomalies caused by extreme weather or transmission network drops. The raw SCADA dataset is now fully sanitized and optimized for mathematical modeling.
*   **Systems Engineering Perspective:** The linear interpolation operation maximized its effectiveness in maintaining the natural fluctuation amplitude of the mechanical equipment. This processing step ensures the integrity and continuity of the time series, enabling the Machine Learning algorithm to accurately read the physical state of the system without abrupt signal jumps or distortion.
*   **Domain Knowledge Application:** Successfully translated the mechanical constraints of the wind turbine into a logical programming mindset. By accurately mapping the Power Curve, the system now possesses a robust reference frame to easily isolate and extract deviations in the upcoming Unsupervised Learning phases.