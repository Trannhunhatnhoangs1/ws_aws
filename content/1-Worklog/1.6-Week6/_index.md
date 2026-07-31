---
title: "Week 6 Worklog"
date: 2026-07-12
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Weekly Objectives:

* Implement a Deep Learning neural network architecture specialized for time-series data.
* Restructure the input data format into 3D tensors to serve the recurrent neural network layers.
* Construct and train an LSTM-Autoencoder model to learn the non-linear representations of normal operational states.
* Quantify the Reconstruction Error into anomaly warning scores.

### Tasks Implemented This Week:

| Day | Tasks | Start Date | End Date | References |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Data Reshaping:**<br>&emsp; + Apply the Sliding Window technique to convert 2D tabular data into 3D tensors `(samples, time_steps, features)`.<br>&emsp; + Isolate the dataset containing only Normal labels (`0`) to serve the Autoencoder training process. | 06/07/2026 | 06/07/2026 | <https://keras.io/api/layers/recurrent_layers/lstm/> |
| Tue | - **LSTM-Autoencoder Architecture Design:** <br>&emsp; + Initialize the Encoder flow with LSTM layers to compress time-series data into a latent vector. <br>&emsp; + Initialize the Decoder flow with a symmetrical structure to reconstruct the input signal sequence from the latent vector. | 07/07/2026 | 07/07/2026 | |
| Wed | - **Deep Learning Model Training:** <br>&emsp; + Compile the model with the Mean Squared Error (MSE) loss function and the Adam optimization algorithm. <br>&emsp; + Conduct training on the Normal dataset, applying the Early Stopping technique to prevent overfitting. | 08/07/2026 | 08/07/2026 | <https://keras.io/api/callbacks/early_stopping/> |
| Thu | - **Reconstruction Error Extraction:** <br>&emsp; + Execute the inference flow on the entire Test set (including data with label `1`). <br>&emsp; + Calculate the Mean Absolute Error (MAE) between the original data and the reconstructed data for each time frame. | 09/07/2026 | 09/07/2026 | |
| Fri | - **Deep Learning Signal Integration:** <br>&emsp; + Convert the Reconstruction Error array into corresponding anomaly scores for each original data point. <br>&emsp; + Append the LSTM-Autoencoder prediction column to the consolidated DataFrame initialized in Week 5. | 10/07/2026 | 10/07/2026 | |

### Results Achieved in Week 6:

*   **Spatio-Temporal Feature Extraction:** Applying the LSTM structure over a time-step window successfully mitigates the blind spots of static algorithms. The system is now capable of identifying trend anomalies rather than solely detecting local point spikes.
*   **Anomaly Quantization via Reconstruction Error:** The model is configured to learn and memorize exclusively the structure of normal operational data. Consequently, upon receiving faulty signals, the model fails to decode them accurately, thereby generating a significant deviation (error). This mechanism allows for intuitive measurement of the anomaly degree without forcing the data to comply with prior statistical distribution assumptions (e.g., normal distribution).
*   **Benchmarking Ecosystem Completion:** Successfully implemented the complex Deep Learning architecture and synchronized the output results (Anomaly Scores) into the same storage space as the traditional Machine Learning block. The system has gathered sufficient parameters from 3 core algorithms (GMM, iForest, LSTM-AE), establishing a comprehensive data foundation ready for the performance evaluation phase.