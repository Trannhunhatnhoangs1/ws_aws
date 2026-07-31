---
title: "Test the Notification"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.7.3. </b> "
---

Before using Amazon SNS with CloudWatch Alarms, verify that the SNS topic can successfully deliver email notifications.

---

## Step 1

Navigate to

**Amazon SNS** → **Topics**

Select the topic **scada-fault-alerts**, then click

```text
Publish message
```

> **Figure 1**

![Figure 1](/images/5-Workshop/5.9/test-notification/publish.png)

---

## Step 2

Enter a test subject and message.

Example

**Subject**

```text
SCADA SNS Test
```

**Message**

```text
This is a test notification from Amazon SNS.

If you receive this email, the SNS topic has been configured successfully.
```

Click

```text
Publish message
```

> **Figure 2**

![Figure 2](/images/5-Workshop/5.9/test-notification/message.png)

---

## Step 3

Open your email inbox and verify that the test notification has been received successfully.

> **Figure 3**

![Figure 3](/images/5-Workshop/5.9/test-notification/test-email.png)

If the email is received successfully, Amazon SNS has been configured correctly.

---

## Step 4

After Amazon SNS has been verified, trigger a CloudWatch Alarm (or simulate a fault) to validate the end-to-end monitoring workflow.

When the alarm is triggered, Amazon CloudWatch automatically publishes a notification to the SNS topic, and the email should contain the actual fault information.

> **Figure 4**

![Figure 4](/images/5-Workshop/5.9/test-notification/email.png)

The notification system is now fully configured and ready to work with Amazon CloudWatch Alarms.