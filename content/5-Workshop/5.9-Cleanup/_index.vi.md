---
title : "Dọn dẹp tài nguyên"
date :  2026-07-30 
weight: 9
chapter : false
pre : " <b> 5.9 </b> "
---

### Dọn dẹp hệ thống và tối ưu chi phí

Điện toán đám mây hoạt động theo mô hình chi trả theo mức sử dụng thực tế. Do đó, sau khi hoàn tất vòng đời phát triển dự án MLOps hoặc khi kết thúc môn học, việc dọn dẹp và thu hồi các dịch vụ là **thao tác bắt buộc** để tối ưu hóa chi phí (Cost Optimization).

Dưới đây là danh sách các tài nguyên bạn cần rà soát và xóa bỏ hoàn toàn khỏi tài khoản AWS của mình.

### Nội dung

1. [Xóa SageMaker Endpoints](5.9.1-delete-endpoint/)
2. [Xóa SageMaker Model Registry](5.9.2-delete-model-registry/)
3. [Xóa tài nguyên Amazon S3](5.9.3-delete-s3/)
4. [Xóa IAM Role](5.9.4-delete-iam/)
5. [Xóa CloudWatch và Amazon SNS](5.9.5-delete-cloudwatch-sns/)

{{% notice warning %}}
**Cảnh báo Chi phí (Cloud Billing):**
Hãy kiểm tra thật kỹ AWS Billing Dashboard để đảm bảo không còn tài nguyên tính toán nào đang chạy ngầm. Quá trình tự động hóa MLOps rất tiện lợi, nhưng việc quên tắt máy chủ có thể khiến bạn bị trừ tiền oan uổng chỉ sau một đêm!
{{% /notice %}}

![Cleanup Resources](/images/5-Workshop/5.9-Cleanup/cleanup.png)
