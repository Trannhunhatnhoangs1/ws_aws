---
title: "Xem Metrics của Endpoint"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.6.1. </b> "
---


Amazon CloudWatch tự động thu thập các chỉ số hiệu năng của SageMaker Endpoint.

Các chỉ số này giúp theo dõi mức độ sử dụng và đánh giá hiệu năng của Endpoint.

## Bước 1

Mở **Amazon CloudWatch**.

Chọn

```
Metrics

→ AWS/SageMaker
```

> **Hình 1**

>![Figure 1](/images/5-Workshop/5.8/view-metrics/metrics.png)

---

## Bước 2

Chọn

```
Endpoint Metrics
```

Sau đó chọn Endpoint đã triển khai.

> **Hình 2**

>![Figure 1](/images/5-Workshop/5.8/view-metrics/endpoint.png)

---

## Bước 3

Quan sát các chỉ số quan trọng:

- InvocationCount
- ModelLatency
- ModelError
- ...

> **Hình 3**
>![Figure 1](/images/5-Workshop/5.8/view-metrics/dashboard1.png)

Các chỉ số này giúp đánh giá hiệu năng và mức sử dụng tài nguyên của Endpoint.