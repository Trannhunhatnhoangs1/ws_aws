---
title: "Worklog Tuần 8"
date: 2026-07-26
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu trong tuần:

* Triển khai mô hình XGBoost đã huấn luyện lên Amazon SageMaker Endpoint để phục vụ dự đoán thời gian thực.
* Kiểm thử quá trình suy luận (Inference) thông qua Amazon SageMaker Runtime API.
* Cấu hình giám sát hệ thống bằng Amazon CloudWatch và thiết lập thông báo với Amazon SNS.
* Kiểm thử toàn bộ hệ thống, hoàn thiện tài liệu Workshop và báo cáo thực tập.

### Các công việc đã thực hiện trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| Thứ 2 | - **Triển khai mô hình:**<br>&emsp; + Tạo **SageMaker Model** từ mô hình XGBoost đã được huấn luyện và lưu trên Amazon S3.<br>&emsp; + Tạo **Endpoint Configuration**, cấu hình loại máy (Instance Type) và số lượng Instance.<br>&emsp; + Triển khai mô hình thành **Amazon SageMaker Endpoint** phục vụ dự đoán thời gian thực. | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html> |
| Thứ 3 | - **Kiểm thử Endpoint:**<br>&emsp; + Thực hiện gửi dữ liệu SCADA mẫu đến Endpoint bằng Amazon SageMaker Runtime.<br>&emsp; + Kiểm tra kết quả dự đoán trả về từ mô hình.<br>&emsp; + Xác nhận Endpoint hoạt động ổn định và có thể xử lý yêu cầu dự đoán theo thời gian thực. | 21/07/2026 | 21/07/2026 | <https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints-test-endpoints.html> |
| Thứ 4 | - **Giám sát hệ thống:**<br>&emsp; + Theo dõi các chỉ số hoạt động của Endpoint trên Amazon CloudWatch.<br>&emsp; + Kiểm tra CloudWatch Logs để phân tích quá trình xử lý yêu cầu dự đoán.<br>&emsp; + Đánh giá các thông số như số lượng Request, độ trễ (Latency) và tình trạng Endpoint. | 22/07/2026 | 22/07/2026 | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html> |
| Thứ 5 | - **Thiết lập thông báo:**<br>&emsp; + Tạo **Amazon SNS Topic** phục vụ gửi thông báo.<br>&emsp; + Đăng ký địa chỉ Email nhận cảnh báo.<br>&emsp; + Kiểm thử việc gửi Email thông báo để xác nhận hệ thống hoạt động chính xác. | 23/07/2026 | 23/07/2026 | <https://docs.aws.amazon.com/sns/latest/dg/welcome.html> |
| Thứ 6 | - **Kiểm thử và hoàn thiện dự án:**<br>&emsp; + Thực hiện kiểm thử toàn bộ quy trình từ triển khai mô hình, dự đoán đến giám sát và gửi thông báo.<br>&emsp; + Dọn dẹp các tài nguyên AWS không còn sử dụng nhằm tối ưu chi phí.<br>&emsp; + Hoàn thiện Workshop, báo cáo thực tập và slide trình bày dự án. | 24/07/2026 | 24/07/2026 | |

### Kết quả đạt được trong tuần:

* Triển khai thành công mô hình XGBoost lên **Amazon SageMaker Endpoint**, cho phép thực hiện dự đoán lỗi thiết bị SCADA theo thời gian thực thông qua giao thức HTTPS.

* Kiểm thử thành công quá trình suy luận bằng cách gửi dữ liệu cảm biến SCADA đến Endpoint và nhận kết quả dự đoán chính xác từ mô hình.

* Cấu hình và sử dụng **Amazon CloudWatch** để theo dõi hiệu năng Endpoint, bao gồm các chỉ số về số lượng yêu cầu, độ trễ xử lý và nhật ký hoạt động của hệ thống.

* Thiết lập **Amazon SNS** để gửi Email thông báo khi xảy ra các sự kiện cần giám sát, giúp tăng khả năng theo dõi và vận hành hệ thống.

* Hoàn thành việc kiểm thử toàn bộ quy trình của nền tảng **SCADA Fault Prediction Platform**, từ huấn luyện mô hình, triển khai, dự đoán, giám sát đến gửi cảnh báo trên nền tảng AWS.

* Hoàn thiện tài liệu Workshop, báo cáo thực tập và nội dung trình bày dự án, sẵn sàng cho quá trình nghiệm thu và báo cáo kết quả.