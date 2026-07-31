---
title: "Tạo thông báo SNS"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

Trong phần này, chúng ta sẽ cấu hình **Amazon Simple Notification Service (Amazon SNS)** để nhận email cảnh báo tự động khi CloudWatch Alarm được kích hoạt.

Amazon SNS là dịch vụ nhắn tin được quản lý hoàn toàn của AWS, hỗ trợ gửi thông báo qua nhiều phương thức như Email, SMS và HTTPS Endpoint.

Kết hợp Amazon SNS với CloudWatch Alarm giúp người quản trị nhanh chóng nhận được cảnh báo khi Endpoint xảy ra lỗi hoặc hoạt động bất thường, từ đó có thể xử lý kịp thời.

Sau khi hoàn thành chương này, bạn sẽ có thể:

- Tạo một Amazon SNS Topic.
- Đăng ký nhận thông báo qua Email.
- Kiểm tra hoạt động của hệ thống thông báo.

## Nội dung

1. [Tạo SNS Topic](5.7.1-create-topic/)
2. [Đăng ký Email nhận thông báo](5.7.2-subscribe-email/)
3. [Kiểm tra thông báo](5.7.3-test-notification/)