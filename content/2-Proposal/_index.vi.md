---
title: "Bản đề xuất"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# SCADA Fault Prediction Platform
## Giải pháp dự đoán sự cố công nghiệp sử dụng Amazon SageMaker

### 1. Tóm tắt điều hành

SCADA Fault Prediction Platform được xây dựng nhằm phát hiện và dự đoán sớm các sự cố thiết bị công nghiệp dựa trên dữ liệu cảm biến SCADA. Hệ thống sử dụng bộ dữ liệu công khai **SKAB (Skoltech Anomaly Benchmark)** kết hợp với các dịch vụ Machine Learning trên nền tảng AWS để tự động hóa toàn bộ quy trình từ tiền xử lý dữ liệu, xây dựng đặc trưng, huấn luyện mô hình, đánh giá, triển khai đến giám sát hệ thống.

Giải pháp được phát triển chủ yếu trên Amazon SageMaker cùng các dịch vụ AWS liên quan, giúp sinh viên và nhóm nghiên cứu dễ dàng xây dựng hệ thống Predictive Maintenance có khả năng mở rộng mà không cần quản lý hạ tầng phức tạp. Hệ thống cung cấp API dự đoán theo thời gian thực và hỗ trợ giám sát trạng thái hoạt động của mô hình.

---

### 2. Tuyên bố vấn đề

#### Vấn đề hiện tại

Các hệ thống SCADA trong công nghiệp liên tục sinh ra lượng lớn dữ liệu cảm biến theo thời gian thực. Việc giám sát và phát hiện sự cố bằng phương pháp thủ công tốn nhiều thời gian, khó phát hiện các dấu hiệu bất thường trước khi thiết bị xảy ra hỏng hóc và không phù hợp với các hệ thống có quy mô lớn.

Mặc dù Machine Learning có thể hỗ trợ bảo trì dự đoán hiệu quả, việc xây dựng một quy trình hoàn chỉnh từ xử lý dữ liệu đến triển khai mô hình thường yêu cầu nhiều hạ tầng và kinh nghiệm triển khai trên Cloud.

#### Giải pháp

Hệ thống sử dụng Amazon S3 để lưu trữ dữ liệu SCADA, SageMaker Processing Jobs để tiền xử lý và xây dựng đặc trưng, sau đó huấn luyện nhiều mô hình như XGBoost, Isolation Forest và LSTM bằng SageMaker Training Jobs. Hyperparameter Optimization được sử dụng để tự động tìm bộ tham số tối ưu.

Sau khi lựa chọn được mô hình tốt nhất, hệ thống đăng ký mô hình vào SageMaker Model Registry và triển khai thành SageMaker Endpoint. AWS Lambda kết hợp Amazon API Gateway cung cấp REST API cho việc dự đoán thời gian thực, trong khi Amazon CloudWatch và Amazon SNS đảm nhiệm việc giám sát và gửi cảnh báo khi phát hiện bất thường.

#### Lợi ích và hiệu quả mang lại

Giải pháp giúp sinh viên và nhóm nghiên cứu tiếp cận đầy đủ quy trình xây dựng một hệ thống Machine Learning trên AWS theo hướng MLOps. Toàn bộ quá trình xử lý dữ liệu, huấn luyện, đánh giá và triển khai được tự động hóa, giảm đáng kể công sức triển khai thủ công.

Ngoài ra, nền tảng còn tạo ra một kiến trúc có thể tái sử dụng cho các bài toán Predictive Maintenance trong tương lai. Do sử dụng bộ dữ liệu công khai SKAB nên không phát sinh chi phí thu thập dữ liệu, đồng thời có thể tận dụng AWS Academy Credits hoặc AWS Free Tier để giảm chi phí triển khai.

---

### 3. Kiến trúc giải pháp

Hệ thống được xây dựng theo kiến trúc Machine Learning hoàn chỉnh trên AWS. Dữ liệu SCADA được lưu trữ trong Amazon S3, sau đó được xử lý bằng SageMaker Processing Jobs và Feature Engineering trước khi huấn luyện các mô hình Machine Learning. Mô hình có kết quả tốt nhất sẽ được đăng ký trong Model Registry và triển khai thành SageMaker Endpoint để phục vụ dự đoán trực tuyến. AWS Lambda và API Gateway cung cấp REST API, trong khi CloudWatch và SNS đảm nhiệm việc giám sát và gửi cảnh báo.

![SCADA System Architecture](/images/2-Proposal/scada_architecture.png)

### Dịch vụ AWS sử dụng

- **Amazon S3**: Lưu trữ dữ liệu gốc, dữ liệu đã xử lý và đặc trưng.
- **Amazon SageMaker Processing**: Tiền xử lý dữ liệu và Feature Engineering.
- **Amazon SageMaker Training**: Huấn luyện các mô hình Machine Learning.
- **Amazon SageMaker Experiments**: Theo dõi các lần huấn luyện.
- **Amazon SageMaker Hyperparameter Optimization**: Tối ưu tham số mô hình.
- **Amazon SageMaker Model Registry**: Quản lý phiên bản mô hình.
- **Amazon SageMaker Endpoint**: Cung cấp dịch vụ dự đoán thời gian thực.
- **AWS Lambda**: Xử lý các yêu cầu dự đoán.
- **Amazon API Gateway**: Cung cấp REST API.
- **Amazon CloudWatch**: Giám sát hiệu năng hệ thống.
- **Amazon SNS**: Gửi cảnh báo khi phát hiện lỗi.

### Thiết kế thành phần

- **Lớp dữ liệu**: Bộ dữ liệu SKAB được lưu trên Amazon S3.
- **Xử lý dữ liệu**: SageMaker Processing thực hiện tiền xử lý và xây dựng đặc trưng.
- **Huấn luyện mô hình**: SageMaker Training huấn luyện XGBoost, Isolation Forest và LSTM, kết hợp HPO để tối ưu tham số.
- **Triển khai mô hình**: Mô hình tốt nhất được đăng ký vào Model Registry và triển khai thành SageMaker Endpoint.
- **API dự đoán**: Lambda và API Gateway cung cấp giao diện REST API cho người dùng.
- **Giám sát hệ thống**: CloudWatch theo dõi hiệu năng, SNS gửi cảnh báo khi xảy ra bất thường.

---

### 4. Triển khai kỹ thuật

#### Các giai đoạn triển khai

Dự án được chia thành bốn giai đoạn chính:

1. **Chuẩn bị dữ liệu:** Thu thập bộ dữ liệu SKAB, thực hiện EDA và xử lý lỗi gán nhãn vô nghĩa (Label_Error).
2. **Xây dựng đặc trưng:** Xử lý góc gió bằng lượng giác (Sin/Cos), thêm đặc trưng thời gian (Giờ, Tháng), tối ưu biến trễ (Lag_1) thay cho Rolling, và bảo toàn các điểm dữ liệu dị thường thay vì dùng Z-score.
3. **Huấn luyện mô hình:** Huấn luyện và so sánh XGBoost, Isolation Forest và LSTM dựa trên F1 Score và AUC-ROC.
4. **Triển khai và giám sát:** Triển khai SageMaker Endpoint, xây dựng Lambda, API Gateway, CloudWatch, SNS và SageMaker Pipeline.

#### Yêu cầu kỹ thuật

**Môi trường phát triển**

- Python 3.10 trở lên
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- TensorFlow
- PyTorch
- XGBoost

**Dịch vụ AWS**

- Amazon S3
- Amazon SageMaker
- AWS Lambda
- Amazon API Gateway
- Amazon CloudWatch
- Amazon SNS
- AWS IAM

---

### 5. Lộ trình & Mốc triển khai

- **Tuần 1:** Chuẩn bị bộ dữ liệu, cấu hình môi trường AWS và thực hiện EDA.
- **Tuần 2:** Tiền xử lý dữ liệu và Feature Engineering.
- **Tuần 3:** Huấn luyện mô hình trên môi trường Local.
- **Tuần 4:** Triển khai SageMaker Processing và Training Jobs.
- **Tuần 5:** Hyperparameter Optimization và Model Registry.
- **Tuần 6:** Triển khai SageMaker Endpoint và xây dựng REST API.
- **Tuần 7:** Tích hợp SageMaker Pipeline và kiểm thử toàn bộ hệ thống.
- **Tuần 8:** Hoàn thiện tài liệu, kiểm thử cuối cùng và trình bày dự án.

---

### 6. Ước tính ngân sách

Chi phí hạ tầng chủ yếu đến từ các dịch vụ AWS:

- Amazon S3
- Amazon SageMaker Processing
- Amazon SageMaker Training
- Amazon SageMaker Endpoint
- AWS Lambda
- Amazon API Gateway
- Amazon CloudWatch
- Amazon SNS

Dự án hướng đến mục đích học tập và nghiên cứu nên có thể sử dụng AWS Academy Credits hoặc AWS Free Tier để giảm đáng kể chi phí triển khai. SageMaker Endpoint sẽ được tắt ngay sau khi hoàn thành việc kiểm thử hoặc trình diễn nhằm tối ưu chi phí vận hành.

**Chi phí phần cứng**

- Không phát sinh chi phí phần cứng do sử dụng bộ dữ liệu công khai SKAB thay vì thu thập dữ liệu trực tiếp từ thiết bị SCADA.

---

### 7. Đánh giá rủi ro

#### Ma trận rủi ro

- Độ chính xác mô hình chưa đạt yêu cầu: Ảnh hưởng cao, xác suất trung bình.
- Chất lượng dữ liệu không tốt: Ảnh hưởng cao, xác suất trung bình.
- Gián đoạn dịch vụ AWS: Ảnh hưởng trung bình, xác suất thấp.
- Chi phí Cloud vượt dự kiến: Ảnh hưởng trung bình, xác suất thấp.

#### Chiến lược giảm thiểu

- Thực hiện tiền xử lý và Feature Engineering đầy đủ.
- Sử dụng Hyperparameter Optimization để cải thiện hiệu suất mô hình.
- Giám sát bằng Amazon CloudWatch và thiết lập AWS Budget Alerts.
- Tắt SageMaker Endpoint sau khi kiểm thử để giảm chi phí.

#### Kế hoạch dự phòng

- Tiếp tục huấn luyện và đánh giá mô hình trên môi trường Local khi không thể sử dụng tài nguyên AWS.
- Triển khai lại phiên bản mô hình đã được phê duyệt từ SageMaker Model Registry khi xảy ra lỗi.
- Khôi phục phiên bản Pipeline trước đó nếu phiên bản mới làm giảm chất lượng dự đoán.

---

### 8. Kết quả kỳ vọng

#### Cải tiến kỹ thuật

- Tự động hóa toàn bộ quy trình Machine Learning trên AWS.
- Dự đoán sự cố thiết bị công nghiệp theo thời gian thực.
- Cung cấp REST API phục vụ dự đoán trực tuyến.
- Tự động triển khai và quản lý vòng đời mô hình.
- Xây dựng quy trình MLOps có thể tái sử dụng.

#### Giá trị dài hạn

- Tạo nền tảng nghiên cứu về Predictive Maintenance và Industrial AI.
- Giúp sinh viên tiếp cận quy trình triển khai Machine Learning trên AWS.
- Có thể mở rộng để áp dụng cho các hệ thống SCADA thực tế và các dự án công nghiệp trong tương lai.