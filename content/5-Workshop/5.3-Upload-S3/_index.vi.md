---
title: "Tải dữ liệu lên Amazon S3"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Tổ chức lưu trữ dữ liệu trên AWS

Trong kiến trúc MLOps, **Amazon S3 (Simple Storage Service)** đóng vai trò là "Data Lake" trung tâm. Để xử lý và huấn luyện mô hình bằng SageMaker, dữ liệu thô và các đoạn mã nguồn xử lý bắt buộc phải được đẩy lên S3 trước tiên.

Chúng ta sẽ sử dụng script Python cùng thư viện `boto3` để tự động hóa quá trình đẩy dữ liệu thô và source code lên đám mây, thay vì thao tác thủ công trên AWS Console. Điều này giúp đồng bộ hóa dữ liệu nhanh chóng và tuân thủ nguyên tắc tự động hóa của MLOps.

---

### 1. Chuẩn bị thư mục cục bộ

Trong cấu trúc thư mục dự án trên máy cục bộ của bạn, hãy đảm bảo dữ liệu thô và mã nguồn đã nằm đúng vị trí:

- `data/raw/T1.csv`: Tập dữ liệu cảm biến SCADA gốc chưa qua xử lý.
- `src/preprocessing.py`: Kịch bản Python chứa logic làm sạch và xử lý dữ liệu.
- `scripts/setupS3.py`: Script tự động đẩy dữ liệu lên S3 bằng `boto3`.

---

### 2. Tự động hóa tải lên S3 bằng Boto3

Thay vì phải tự tạo từng thư mục trên giao diện AWS, script `setupS3.py` dưới đây sẽ tự động kết nối với S3 bằng tài khoản IAM Role của bạn và đẩy các file lên đúng vị trí trong bucket.

Mở Terminal tại thư mục gốc của dự án và chạy kịch bản đẩy dữ liệu lên S3:

```bash
# Đảm bảo bạn đang ở môi trường ảo (virtual environment)
.\.venv\Scripts\python scripts/setupS3.py
```

**Quá trình thực thi sẽ hiển thị tương tự như sau:**

```text
📂 Upload dữ liệu thô...
 ⬆️ data/raw/T1.csv → s3://amznce23/T1_AD/data/raw/T1.csv

📂 Upload source code (src/)...
 ⬆️ src/preprocessing.py → s3://amznce23/T1_AD/scripts/src/preprocessing.py

📂 Upload entry-point script...
 ⬆️ src/preprocessing.py → s3://amznce23/T1_AD/scripts/preprocessing.py

**Upload hoàn tất!**
 Raw data : s3://amznce23/T1_AD/data/raw/T1.csv
 Scripts : s3://amznce23/T1_AD/scripts/
```

*(Lưu ý: Tên bucket `amznce23` và tiền tố `T1_AD` được cấu hình sẵn trong file `setupS3.py` của dự án, bạn có thể điều chỉnh lại thông số này theo bucket của riêng mình nếu cần thiết).*

---

### 3. Kiểm tra kết quả trên AWS Console

1. Truy cập vào **AWS Management Console** và mở dịch vụ **Amazon S3**.
2. Tìm và bấm vào bucket của bạn (ví dụ: `amznce23`).
3. Đi vào thư mục `T1_AD/` (hoặc tên dự án bạn cấu hình).
4. Bạn sẽ thấy hai cấu trúc thư mục quan trọng đã được tạo và chứa file:
   - `data/raw/`: Chứa file `T1.csv`.
   - `scripts/`: Chứa các script tiền xử lý (`preprocessing.py`).

{{% notice success %}}
**Hoàn tất:**
Xin chúc mừng! Dữ liệu thô và source code của bạn đã được tải lên "Data Lake" an toàn. Giờ đây, "nguồn nguyên liệu" đã sẵn sàng để đưa vào máy chủ xử lý dữ liệu tự động của SageMaker trong bước tiếp theo.
{{% /notice %}}