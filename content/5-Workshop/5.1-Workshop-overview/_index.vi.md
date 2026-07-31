---
title : "Giới thiệu"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Giới thiệu hệ thống MLOps SCADA

Trong các quy trình công nghiệp thực tế, việc dự đoán và phát hiện sớm các lỗi hệ thống từ dữ liệu cảm biến (SCADA) đóng vai trò sống còn giúp giảm thiểu thời gian "chết" (downtime) của máy móc. Tuy nhiên, việc phát triển một mô hình học máy (Machine Learning) giải quyết bài toán này thường gặp hai thách thức lớn:

1. **Mất cân bằng dữ liệu (Class Imbalance):** Tín hiệu lỗi thường rất hiếm khi xảy ra so với trạng thái hoạt động bình thường, khiến các mô hình dễ bị dự đoán lệch.
2. **Khó khăn trong vận hành (Operations):** Việc đưa mô hình từ máy tính cá nhân lên môi trường sản xuất đòi hỏi một quy trình quản lý khắt khe, minh bạch và có khả năng tự động hóa.

Workshop này được thiết kế để giải quyết triệt để hai bài toán trên bằng cách xây dựng một kiến trúc **MLOps toàn trình (End-to-End MLOps)** trên nền tảng AWS. Chúng ta sẽ sử dụng thuật toán **XGBoost** kết hợp cơ chế kiểm soát mất cân bằng nhãn (`scale_pos_weight`), và tự động hóa toàn bộ vòng đời mô hình thông qua **Amazon SageMaker**.

---

### Sơ đồ kiến trúc (Architecture Diagram)

Kiến trúc dưới đây mô tả luồng dữ liệu và sự tương tác giữa các dịch vụ đám mây của AWS trong hệ thống MLOps của chúng ta.

![Architecture Diagram](/images/5-Workshop/5.1-Workshop-overview/pic1.png)

---

### Các thành phần dịch vụ AWS cốt lõi

Dự án này là sự kết hợp chặt chẽ của các dịch vụ đám mây chuẩn công nghiệp:

*   **Amazon S3 (Simple Storage Service):** Đóng vai trò là Data Lake tập trung. Mọi dữ liệu (từ thô đến sạch) và các tệp trọng số của mô hình (`model.tar.gz`) đều được lưu trữ an toàn, chi phí thấp tại đây.
*   **AWS IAM (Identity and Access Management):** Đảm bảo an ninh cho hệ thống bằng cách áp dụng nguyên tắc "đặc quyền tối thiểu". SageMaker sẽ được cấp một IAM Role riêng biệt, chỉ cho phép đọc/ghi vào đúng S3 Bucket của dự án và ghi Log lên CloudWatch.
*   **Amazon SageMaker:** Nền tảng Machine Learning toàn diện được quản lý hoàn toàn (Fully Managed), đảm nhiệm 3 vai trò chính:
    1.  *Training:* Cấp phát máy chủ ảo (EC2) tự động để chạy kịch bản huấn luyện XGBoost.
    2.  *Automatic Model Tuning (HPO):* Tự động khởi chạy hàng loạt thực nghiệm để tìm ra bộ tham số (hyperparameters) mang lại chỉ số F1-Score cao nhất.
    3.  *Model Registry:* Quản lý danh mục, lập phiên bản (versioning) và tích hợp cơ chế phê duyệt thủ công (Approval Workflow) trước khi đưa mô hình vào sử dụng.
*   **Amazon CloudWatch:** Dịch vụ giám sát theo thời gian thực. Toàn bộ quá trình tính toán loss function, epoch logs và metrics đều được ghi lại tại đây giúp kỹ sư dễ dàng theo dõi và gỡ lỗi (debug).
