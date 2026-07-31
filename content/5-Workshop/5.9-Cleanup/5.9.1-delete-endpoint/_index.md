---
title: "Delete SageMaker Endpoints"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 5.9.1 </b> "
---

SageMaker Endpoint is the most costly resource because it constantly maintains a server (EC2) running 24/7 waiting to serve predictions.

Although the focus of this project is automating the Training flow and Model Registry, if during practice you experimented with deploying the model to an Endpoint for trial prediction (Inference), you **must delete it immediately**. 

## Step 1: Go to Inference Section

1. Access the **SageMaker Console** interface.
2. On the left menu, find the **Inference** section, then select **Endpoints**.

## Step 2: Delete Endpoint

1. Select the running Endpoint of the SCADA project (e.g., `scada-xgboost-endpoint`) and click **Delete**.
2. Confirm the deletion operation and wait until the Endpoint disappears from the list.

>![Figure 1](/images/5-Workshop/5.10/delete-endpoint/endpoints.png)

## Step 3: Delete Related Configurations

Continue into the **Endpoint configurations** and **Models** sections (under Inference) to delete related configurations.
