---
title: "Worklog Tuần 1"
date: 2026-05-31
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Nắm bắt tổng quan về bài toán phát hiện bất thường cho Tuabin gió dựa trên dữ liệu SCADA trong môi trường công nghiệp.
* Làm quen với hệ sinh thái điện toán đám mây Amazon Web Services (AWS) và các dịch vụ lưu trữ, tính toán, quản lý quyền truy cập cơ bản.
* Thiết lập thành công môi trường làm việc cục bộ và kết nối API bảo mật với tài khoản đám mây.
* Lên ý tưởng và phác thảo kiến trúc hệ thống máy học lai.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Phân tích nghiệp vụ và dữ liệu:**<br>&emsp; + Khảo sát tài liệu dự án và tập dữ liệu thô SCADA (`T1_train.csv`, `T1_test.csv`).<br>&emsp; + Phân tích đặc tả cấu trúc dữ liệu chuỗi thời gian, xác định các trường biến cốt lõi như tốc độ gió, công suất thực tế. <br>&emsp; + Thống nhất phương pháp tiếp cận: Sử dụng các mô hình Không giám sát để phát hiện lỗi cảm biến hoặc suy giảm hiệu suất thiết bị. | 01/06/2026 | 01/06/2026 | <https://www.kaggle.com/code/aliakbaryaghoubi/wind-turbine-status-classification-via-power-curve> |
| 3 | - **Nghiên cứu kiến trúc hệ thống MLOps:** <br>&emsp; + Tìm hiểu quy trình vòng đời của một dự án MLOps tiêu chuẩn: Data Engineering → Training → Evaluation → Model Registry. <br>&emsp; + Chốt phương án kiến trúc Lai: Xử lý dữ liệu và tiền xử lý tại Local, tận dụng đám mây AWS để thực thi Training Job nhằm tiết kiệm chi phí và vượt qua rào cản phần cứng cá nhân. | 02/06/2026 | 02/06/2026 | <https://aws.amazon.com/sagemaker/mlops/> |
| 4 | - **Khởi tạo và cấu hình tài khoản AWS:** <br>&emsp; + Cài đặt AWS CLI (Command Line Interface) trên môi trường máy tính cục bộ. <br>&emsp; + **Thực hành:** Sử dụng lệnh `aws configure` để thiết lập thông tin xác thực thông qua Access Key ID và Secret Access Key, cấu hình khu vực mặc định là `ap-southeast-1` (Singapore). | 03/06/2026 | 03/06/2026 | <https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html> |
| 5 | - **Tìm hiểu về bảo mật và phân quyền (AWS IAM):** <br>&emsp; + Khảo sát các khái niệm cơ bản về IAM Users, Groups, Policies, và Roles áp dụng nguyên tắc đặc quyền tối thiểu. | 04/06/2026 | 04/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html> |
| 6 | - **Khởi tạo hạ tầng Lưu trữ Đám mây (Amazon S3):** <br>&emsp; + Nghiên cứu dịch vụ Object Storage của AWS (Amazon S3) và đánh giá lý do tại sao nó phù hợp cho lưu trữ dữ liệu Machine Learning hơn so với Block Storage (EBS). <br>&emsp; + **Thực hành:** Truy cập AWS Console để khởi tạo Bucket S3 với tính chất Globally Unique. Thiết lập cấu trúc thư mục Data Lake cơ bản chuẩn bị sẵn sàng cho việc đẩy mã nguồn và dữ liệu ở các tuần sau. | 05/06/2026 | 05/06/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |

### Kết quả đạt được tuần 1:

*   **Về kiến thức nghiệp vụ:** Hiểu rõ bản chất dữ liệu chuỗi thời gian của hệ thống SCADA công nghiệp. Xác định được mục tiêu cốt lõi của bài toán Phát hiện bất thường cho thiết bị Tuabin gió, từ đó có cơ sở để thiết kế các đặc trưng về sau.
*   **Về kiến thức hạ tầng:** Nắm vững các khái niệm cơ bản về điện toán đám mây AWS, đặc biệt là các dịch vụ cốt lõi sẽ đóng vai trò then chốt trong dự án bao gồm: Amazon S3 (Lưu trữ phi cấu trúc), AWS IAM (Phân quyền & Kiểm soát truy cập), và mô hình tính toán đám mây cấp phát tự động.
*   **Thiết lập môi trường thành công:** 
    *   Thiết lập AWS CLI trên máy Local thành công. Các biến môi trường và Credentials được lưu trữ bảo mật, đảm bảo khả năng giao tiếp API hai chiều từ máy tính cá nhân lên Đám mây mà không bị gián đoạn.
*   **Thực hành Cloud & Xử lý sự cố sơ bộ:** 
    *   Khởi tạo thành công không gian lưu trữ Amazon S3 Bucket. Đây là bước đệm kiến trúc cực kỳ quan trọng để tuần tới có thể lập trình tự động hóa đẩy dữ liệu (bằng Python Boto3) lên Data Lake.
*   **Tư duy hệ thống:** Định hình rõ ràng quy trình MLOps Lai. Đã trả lời được câu hỏi kiến trúc: Vì sao cần đẩy tác vụ tốn kém tài nguyên (Huấn luyện Mô hình - Training) lên Amazon SageMaker thay vì chạy cục bộ, giúp giải quyết bài toán tối ưu chi phí (FinOps) và vượt rào cản phần cứng.