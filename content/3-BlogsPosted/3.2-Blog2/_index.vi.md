---
title: "Blog 2"
date: 2026-07-17
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---
## 1. TỔNG QUAN BÀI VIẾT & BỐI CẢNH DỰ ÁN

* **Tác giả:** Huỳnh Duy Chương.
* **Bối cảnh:** Tham gia chương trình *AWS Study Group*, đối mặt với bài toán tối ưu hóa thời gian học tập hạn chế để đạt hiệu quả cao nhất cho công việc thực tế tại doanh nghiệp.
* **Mục tiêu bài viết:** Xác định chiến lược phân bổ thời gian học tập, dịch chuyển từ thói quen làm việc trên Jupyter Notebook local sang quy trình vận hành đám mây chuẩn hóa. [LINK](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2226421048122855/?rdid=Qh4KrhITN1dA0Io4#)
---

## 2. PHÂN TÍCH CHUYÊN MÔN VỀ CÁC TRỤ CỘT KIẾN THỨC

Bài viết đã phân loại và sắp xếp thứ tự ưu tiên các dịch vụ AWS một cách rất logic theo đúng vòng đời phát triển của một dự án Machine Learning (ML Lifecycle):

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                       1. Storage & Security Layer                       │
│                         (Amazon S3, AWS IAM, VPC)                       │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                       2. MLOps & Training Engine                        │
│             (SageMaker Data Wrangler, Feature Store, HPO,               │
│                        SageMaker Model Registry)                        │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     3. Inference & Deployment Layer                     │
│               (SageMaker Endpoints, API Gateway, AWS Lambda)            │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     4. Monitoring & Governance                          │
│                      (AWS CloudWatch, EC2 Types)                        │
└─────────────────────────────────────────────────────────────────────────┘

```

### A. Nền tảng Đám mây & Bảo mật (S3, IAM, VPC)

* Nhiều bạn sinh viên thường xem nhẹ phần này và nhảy ngay vào huấn luyện mô hình. Việc hiểu rõ **S3** (lưu trữ tập trung), **IAM** (nguyên tắc Least Privilege) và **VPC Endpoints** (bảo mật đường truyền nội bộ) giúp đảm bảo dữ liệu doanh nghiệp không bị rò rỉ ra ngoài Internet.

### B. MLOps chuẩn hóa với Amazon SageMaker

* **Feature Engineering & Feature Store:** Việc chuyển từ xử lý dữ liệu đơn lẻ bằng Pandas sang quản lý Feature tập trung giúp tái sử dụng dữ liệu cho nhiều mô hình, tránh hiện tượng tính toán lặp lại (Data Leakage / Redundancy).
* **Automatic Hyperparameter Tuning (HPO):** Chuyển dịch từ việc "mò mẫm" thủ công sang tự động hóa tìm kiếm không gian tham số tối ưu, giúp giải phóng thời gian cho kỹ sư tập trung vào thiết kế kiến trúc.
* **Model Registry:** Thiết lập quy trình quản lý phiên bản mô hình (**v1.0**, **v1.1**, **Approved**) minh bạch. Đây là xương sống của mọi pipeline MLOps hiện đại.

### C. Triển khai mô hình & Kiến trúc Serverless

* **SageMaker Endpoints:** Đưa mô hình ra khỏi môi trường thử nghiệm để đóng gói thành dịch vụ API sẵn sàng phục vụ các ứng dụng Client.
* **API Gateway + AWS Lambda (Serverless):** Lựa chọn tối ưu cho giai đoạn Prototype/Demo. Việc kết hợp này giúp tối ưu hóa chi phí — hệ thống chỉ phát sinh chi phí khi có lượt gọi API thực tế.

---

## 3. LINK TÀI LIỆU THAM KHẢO

* [AWS Documentation: Amazon SageMaker Developer Guide](https://docs.aws.amazon.com/sagemaker/)
* [AWS Architecture Center: MLOps Foundation Roadmap on AWS](https://www.google.com/search?q=https://aws.amazon.com/architecture/mlops/)
* [AWS Workshop: SageMaker Immersion Day Hands-on Labs](https://www.google.com/search?q=https://sagemaker-immersionday.workshop.aws/)