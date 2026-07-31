---
title : "Thiết lập IAM Policy"
date :  2026-07-30 
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

### Phân quyền an toàn với AWS IAM

Trong AWS, các dịch vụ không tự động có quyền truy cập vào nhau nhằm đảm bảo tính bảo mật. Để Amazon SageMaker có thể tự động kéo dữ liệu SCADA từ S3, ghi lại logs quá trình huấn luyện và đăng ký mô hình vào Model Registry, nó cần một danh tính định danh an toàn. 

Bài thực hành này hướng dẫn bạn tạo một **IAM Execution Role** cho SageMaker dựa trên nguyên tắc đặc quyền tối thiểu.

---

### Các bước tạo SageMaker Execution Role

1. Đăng nhập vào **AWS Management Console**, tìm kiếm và mở dịch vụ **IAM (Identity and Access Management)**.
2. Ở thanh menu bên trái, chọn **Roles** và nhấn nút **Create role** (Tạo vai trò mới).
3. **Select trusted entity (Chọn thực thể tin cậy):**
   * Trusted entity type: Chọn **AWS service**.
   * Use case: Tìm kiếm trong danh sách và chọn **SageMaker**, sau đó tiếp tục chọn **SageMaker - Execution** ở mục tùy chọn thả xuống.
   * Nhấn **Next**.
4. **Add permissions (Thêm quyền hạn):**
   * AWS sẽ tự động đính kèm policy `AmazonSageMakerFullAccess`.
   * Vì SageMaker cần đọc/ghi dữ liệu vào Data Lake, bạn cần cấp thêm quyền truy cập S3. Tìm kiếm từ khóa `S3` và đánh dấu tích vào policy `AmazonS3FullAccess`.
   * *(Lưu ý: Trong môi trường doanh nghiệp khắt khe, bạn không nên dùng quyền FullAccess mà nên tự viết một Custom Policy chỉ cấp quyền Read/Write đúng vào tên bucket `scada-mlops-project-bucket-2026` của dự án)*.
   * Nhấn **Next**.
5. **Name, review, and create:**
   * **Role name:** Đặt tên gợi nhớ cho dự án, ví dụ: `SageMaker-SCADA-ExecutionRole`.
   * Kiểm tra lại danh sách các quyền đã thêm.
   * Kéo xuống dưới cùng và nhấn **Create role**.

![IAM Role Creation](/images/5-Workshop/5.5-Policy/iam-role.png)

---

### Giám sát hệ thống

{{% notice info %}}
**Quyền tự động ghi Logs:**
Bạn không cần phải cấp quyền riêng lẻ cho việc giám sát. Policy `AmazonSageMakerFullAccess` mặc định đã bao gồm các quyền cơ bản (như `logs:CreateLogGroup`, `logs:CreateLogStream`, `logs:PutLogEvents`) để SageMaker có thể tự động đẩy các thông số hàm mất mát (Loss) và các thông báo lỗi (Errors) trong lúc chạy thuật toán XGBoost lên dịch vụ **Amazon CloudWatch**.
{{% /notice %}}

Hoàn tất bước này, kiến trúc bảo mật của bạn đã vững chắc. Hãy chuyển sang phần cuối cùng: **Dọn dẹp tài nguyên** để đảm bảo không phát sinh chi phí ngoài ý muốn sau khi kết thúc môn học.