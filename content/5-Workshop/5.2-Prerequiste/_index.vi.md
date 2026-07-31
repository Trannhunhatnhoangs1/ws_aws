---
title : "Điều kiện tiên quyết"
date :  2026-07-30 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

### Chuẩn bị môi trường làm việc

Để triển khai thành công hệ thống MLOps dự đoán lỗi SCADA trên AWS, bạn cần chuẩn bị sẵn sàng cả tài nguyên đám mây lẫn môi trường lập trình tại máy cục bộ. Dưới đây là các yêu cầu bắt buộc.

---

### 1. Tài khoản AWS & Quyền truy cập

Bạn cần có một tài khoản AWS đang hoạt động. Để đảm bảo an toàn bảo mật và tuân thủ các tiêu chuẩn thực tế, **TUYỆT ĐỐI KHÔNG** sử dụng tài khoản Root để thực hành. 

*   **IAM User:** Khởi tạo một IAM User mới và cấp cho user này quyền quản trị (`AdministratorAccess`) hoặc quyền khởi tạo các dịch vụ cơ bản bao gồm: **Amazon S3**, **AWS IAM**, và **Amazon SageMaker**.
*   **Security Credentials:** Tạo và tải xuống `Access Key ID` và `Secret Access Key` của IAM User vừa tạo. Đây là chìa khóa để máy cục bộ của bạn có thể giao tiếp với AWS.
*   **AWS Region:** Xác định và ghi nhớ Khu vực (Region) bạn sẽ triển khai dự án (ví dụ: `ap-southeast-1` cho khu vực Singapore) để đảm bảo dữ liệu và mô hình nằm cùng một nơi, giảm thiểu độ trễ.

![AWS Region](/images/5-Workshop/5.2-Prerequisite/region1.png)
*Gợi ý: Luôn kiểm tra và đồng nhất Region ở góc trên cùng bên phải của AWS Management Console.*

---

### 2. Môi trường máy cục bộ

Toàn bộ các tệp cấu hình để gọi dịch vụ SageMaker sẽ được viết bằng Python. Bạn cần thiết lập môi trường lập trình trên máy tính cá nhân của mình.

#### Cài đặt Python và Thư viện
Đảm bảo máy tính của bạn đã cài đặt **Python 3.10+**. Sau đó, mở Terminal (hoặc Command Prompt) và cài đặt các thư viện thiết yếu cho dự án bằng trình quản lý gói `pip`. Ví dụ:

```bash
pip install awscli sagemaker boto3 xgboost pandas scikit-learn

```

**Chi tiết các thư viện:**

* `awscli`: Công cụ dòng lệnh chính thức của AWS.
* `boto3`: AWS SDK dành cho Python, dùng để tương tác với Amazon S3 và IAM.
* `sagemaker`: SageMaker Python SDK, thư viện chuyên dụng để cấu hình và khởi chạy các kịch bản MLOps.
* `xgboost`, `pandas`, `scikit-learn`: Các thư viện xử lý dữ liệu và học máy cơ bản dùng để tiền xử lý và thiết lập script đánh giá.

---

### 3. Cấu hình AWS CLI

Sau khi cài đặt xong các thư viện, bước quan trọng nhất là liên kết môi trường Local của bạn với tài khoản AWS thông qua AWS CLI.

Từ Terminal, chạy lệnh sau:

```bash
aws configure

```

Hệ thống sẽ yêu cầu bạn nhập lần lượt 4 thông tin (Sử dụng thông tin Security Credentials đã tạo ở phần 1):

1. **AWS Access Key ID [None]:** `AKIAIOSFODNN7EXAMPLE` *(nhập Key của bạn)*
2. **AWS Secret Access Key [None]:** `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` *(nhập Secret Key của bạn)*
3. **Default region name [None]:** `ap-southeast-1` *(nhập mã Region của bạn)*
4. **Default output format [None]:** `json`

{{% notice info %}}
**Kiểm tra kết nối:**
Để chắc chắn AWS CLI đã được cấu hình thành công, hãy chạy thử lệnh `aws s3 ls`. Nếu hệ thống không báo lỗi (không hiện gì nếu chưa có bucket, hoặc hiện danh sách các bucket hiện tại), môi trường của bạn đã sẵn sàng!
{{% /notice %}}

---

### 4. Chuẩn bị Mã nguồn và Dữ liệu

Hãy đảm bảo bạn đã có sẵn thư mục dự án SCADA MLOps trên máy chứa các tệp sau:

* Tập dữ liệu thô: `SCADA_data.csv`
* Các kịch bản (Scripts) Python: `train.py` (Kịch bản huấn luyện XGBoost) và `evaluate.py` (Kịch bản đánh giá mô hình).

Khi tất cả các điều kiện tiên quyết đã hoàn tất, hãy chuyển sang bài thực hành tiếp theo để bắt đầu xây dựng **Data Lake** đầu tiên của chúng ta trên Amazon S3!