---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai hệ thống MLOps dự đoán lỗi SCADA trên AWS

Trong phần workshop này, nhóm chúng tôi sẽ hướng dẫn chi tiết cách triển khai toàn trình (end-to-end) một hệ thống Machine Learning Operations (MLOps) trên nền tảng AWS nhằm giải quyết bài toán phát hiện dị thường từ dữ liệu cảm biến SCADA.

Kiến trúc của dự án thay thế các thao tác thủ công bằng việc tự động hóa toàn bộ vòng đời học máy: từ việc thiết lập không gian lưu trữ dữ liệu (Data Lake), phân quyền bảo mật, huấn luyện mô hình XGBoost (xử lý mất cân bằng nhãn), cho đến việc tối ưu hóa siêu tham số (HPO) và quản lý phiên bản mô hình trên đám mây.

#### Nội dung

1. [Giới thiệu](5.1-Workshop-overview/)
2. [Điều kiện tiên quyết](5.2-Prerequiste/)
3. [Tải dữ liệu lên Amazon S3](5.3-Upload-S3/)
4. [Tiền xử lý dữ liệu bằng SageMaker](5.4-Processing/)
5. [Huấn luyện và quản lý mô hình](5.5-SageMaker/)
6. [Giám sát Endpoint với CloudWatch](5.6-Monitor-CloudWatch/)
7. [Tạo thông báo SNS](5.7-Create-SNS-Notification/)
8. [Thiết lập IAM Policy](5.8-Policy/)
9. [Dọn dẹp tài nguyên](5.9-Cleanup/)