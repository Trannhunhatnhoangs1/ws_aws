---
title: "Kiểm tra thông báo"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.7.3. </b> "
---

Trước khi sử dụng Amazon SNS với CloudWatch Alarm, hãy kiểm tra xem SNS Topic có thể gửi thông báo qua email thành công hay không.

---

## Bước 1

Đi đến

**Amazon SNS** → **Topics**

Chọn topic **scada-fault-alerts**, sau đó nhấn

```text
Publish message
```

> **Hình 1**

![Hình 1](/images/5-Workshop/5.9/test-notification/publish.png)

---

## Bước 2

Nhập tiêu đề và nội dung thông báo thử nghiệm.

Ví dụ

**Tiêu đề**

```text
SCADA SNS Test
```

**Nội dung**

```text
This is a test notification from Amazon SNS.

If you receive this email, the SNS topic has been configured successfully.
```

Sau đó nhấn

```text
Publish message
```

> **Hình 2**

![Hình 2](/images/5-Workshop/5.9/test-notification/message.png)

---

## Bước 3

Mở hộp thư email và kiểm tra xem bạn đã nhận được email thông báo thử nghiệm hay chưa.

> **Hình 3**

![Hình 3](/images/5-Workshop/5.9/test-notification/test-email.png)

Nếu email được gửi thành công, điều đó cho thấy Amazon SNS đã được cấu hình chính xác.

---

## Bước 4

Sau khi xác minh Amazon SNS hoạt động bình thường, hãy kích hoạt một CloudWatch Alarm (hoặc mô phỏng một sự cố) để kiểm tra toàn bộ quy trình giám sát.

Khi cảnh báo được kích hoạt, Amazon CloudWatch sẽ tự động gửi một thông báo đến SNS Topic và email nhận được sẽ chứa thông tin về sự cố thực tế.

> **Hình 4**

![Hình 4](/images/5-Workshop/5.9/test-notification/email.png)

Hệ thống thông báo hiện đã được cấu hình hoàn chỉnh và sẵn sàng hoạt động cùng với Amazon CloudWatch Alarm.