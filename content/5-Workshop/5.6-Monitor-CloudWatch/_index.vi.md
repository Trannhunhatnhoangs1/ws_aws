---
title: "Giám sát Endpoint với CloudWatch"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---



Sau khi triển khai và kiểm thử thành công SageMaker Endpoint, bước tiếp theo là theo dõi trạng thái hoạt động và hiệu năng của Endpoint.

Amazon CloudWatch tự động thu thập các chỉ số (Metrics) và nhật ký (Logs) từ SageMaker Endpoint, giúp người quản trị dễ dàng giám sát hệ thống, phát hiện sự cố và đánh giá hiệu năng của mô hình.

Sau khi hoàn thành chương này, bạn sẽ có thể:

- Theo dõi các chỉ số hoạt động của Endpoint.
- Xem nhật ký thực thi của Endpoint.
- Tạo CloudWatch Alarm để giám sát tự động.

## Nội dung

1. [Xem Metrics của Endpoint](5.6.1-view-metrics/)
2. [Xem Logs của Endpoint](5.6.2-view-logs/)
3. [Tạo CloudWatch Alarm](5.6.3-create-alarm/)