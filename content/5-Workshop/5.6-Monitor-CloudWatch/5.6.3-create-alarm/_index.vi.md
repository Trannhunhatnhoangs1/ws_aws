---
title: "Tạo CloudWatch Alarm"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.6.3. </b> "
---



CloudWatch Alarm cho phép giám sát tự động các chỉ số của SageMaker Endpoint và phát cảnh báo khi vượt quá ngưỡng đã cấu hình.

## Bước 1

Mở

```
CloudWatch

→ Alarms
```

Nhấn

```
Create alarm
```

> **Hình 1**

>![Figure 1](/images/5-Workshop/5.8/create-alarm/new.png)

---

## Bước 2

Chọn chỉ số

```
ModelLatency và ModelError
```

Thiết lập ngưỡng.

Ví dụ

```
Lớn hơn 1000 ms đối với ModelLatency
Lớn hơn 5 đối với ModelError 
```

> **Hình 2**

>![Figure 2](/images/5-Workshop/5.8/create-alarm/metric.png)

---

## Bước 3

Liên kết Alarm với một Amazon SNS Topic và nhấn **Create alarm**.

> **Hình 3**

>![Figure 3](/images/5-Workshop/5.8/create-alarm/sns.png)

Sau khi được tạo, CloudWatch sẽ tự động theo dõi Endpoint và chuyển trạng thái Alarm khi chỉ số vượt quá ngưỡng đã thiết lập.