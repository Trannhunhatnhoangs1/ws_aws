---
title: "Create CloudWatch Alarm"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.6.3. </b> "
---


CloudWatch Alarms continuously monitor endpoint metrics and trigger notifications when predefined thresholds are exceeded.

## Step 1

Navigate to

```
CloudWatch

→ Alarms
```

Click

```
Create alarm
```

> **Figure 1**

>![Figure 1](/images/5-Workshop/5.8/create-alarm/new.png)

---

## Step 2

Select the metric

```
ModelLatency and ModelError
```

Configure a threshold.

Example

```
Greater than 1000 ms (with ModelLatency) 
Greater than 5 with ModelError
```

> **Figure 2**

>![Figure 2](/images/5-Workshop/5.8/create-alarm/metric.png)

---

## Step 3

Associate the alarm with an Amazon SNS topic and create the alarm.

> **Figure 3**

>![Figure 3](/images/5-Workshop/5.8/create-alarm/sns.png)

Once created, CloudWatch continuously monitors the endpoint and changes the alarm state whenever the configured threshold is exceeded.