---
title: "View Endpoint Metrics"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.6.1. </b> "
---

Amazon CloudWatch automatically collects performance metrics from SageMaker Endpoints.

These metrics help monitor endpoint usage and identify performance bottlenecks.

## Step 1

Open **Amazon CloudWatch**.

Navigate to

```
Metrics

→ AWS/SageMaker
```

> **Figure 1**

>![Figure 1](/images/5-Workshop/5.8/view-metrics/metrics.png)

---

## Step 2

Select

```
Endpoint Metrics
```

Choose your deployed endpoint.

> **Figure 2**

>![Figure 1](/images/5-Workshop/5.8/view-metrics/endpoint.png)

---

## Step 3

Review important metrics, including:

- InvocationCount
- ModelLatency
- ModelError
- ...
> **Figure 3**

>![Figure 1](/images/5-Workshop/5.8/view-metrics/dashboard1.png)

These metrics provide insight into endpoint performance and resource utilization.