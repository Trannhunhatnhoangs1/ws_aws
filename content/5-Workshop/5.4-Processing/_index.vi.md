---
title: "Tiền xử lý dữ liệu bằng SageMaker"
date: 2026-07-30
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Tự động hóa tiền xử lý với SageMaker Processing Job

Trong dự án thực tế, dữ liệu thô (SCADA data) thường chứa nhiều giá trị dị thường, thiếu sót và định dạng không phù hợp để đưa ngay vào mô hình học máy. Hơn nữa, việc xử lý dữ liệu quy mô lớn (Big Data) đòi hỏi máy tính có cấu hình mạnh mà máy tính cá nhân không thể đáp ứng.

Để giải quyết vấn đề này, AWS cung cấp tính năng **SageMaker Processing Job**. Chức năng này cho phép chúng ta cấp phát một cụm máy chủ đám mây, tải mã nguồn xử lý (`preprocessing.py`) và dữ liệu thô từ S3 về máy chủ này, thực thi code và sau đó đẩy dữ liệu đã xử lý ngược lại lên S3.

---

### 1. Kịch bản tiền xử lý dữ liệu (Data Engineering)

Kịch bản `preprocessing.py` (chạy trên SageMaker) đóng vai trò cốt lõi trong việc "làm sạch" dữ liệu SCADA. Ở phần này, chúng ta đã áp dụng các giải pháp kỹ thuật tinh chỉnh đặc biệt phù hợp với định luật vật lý thay vì chỉ xử lý bằng thống kê thuần túy:

1. **Xử lý nhãn lỗi (Label_Error):** Dữ liệu gốc không có nhãn. Chúng ta đã fix lỗi gán nhãn vô nghĩa và tạo ra cột `Label_Error` (0: Bình thường, 1: Lỗi) chuẩn xác. Output này cho phép sử dụng ngay lập tức các mô hình học có giám sát như XGBoost.
2. **Toán học hóa góc gió (Wind Direction):** Xóa bỏ cột góc gió thô (0-360 độ). Góc 1 độ và 359 độ vốn rất gần nhau trong thực tế, nhưng máy tính lại hiểu là cách xa 358 đơn vị. Bằng cách đẻ ra 2 cột mới là `Wind_Dir_Sin` và `Wind_Dir_Cos`, thuật toán giờ đây hiểu hoàn hảo tính chất chu kỳ vòng tròn.
3. **Bảo toàn dữ liệu dị thường (Outlier Integrity):** Thay vì dùng Z-Score hoặc IQR để cắt cụt (capping) và ép các giá trị quá cao/thấp về mức trung bình, chúng ta giữ nguyên vẹn các điểm đột biến này. Trong bảo trì dự đoán, các dị biệt chính là "dấu vết hỏng hóc". Việc gọt đi sẽ xóa mất dấu vết. Chúng ta chỉ làm sạch các nhiễu vô lý về mặt vật lý (vd: tuabin sinh công suất âm).
4. **Tích hợp nhận thức thời gian (Time Awareness):** Bổ sung 2 cột `Month` và `Hour` để biến mô hình XGBoost (vốn mù mờ về index thời gian) có khả năng học các quy luật ngầm như lỗi thường xảy ra vào ban đêm của mùa đông.
5. **Tối ưu đa cộng tuyến (Dimensionality):** Thay vì tạo ra quá nhiều cột Rolling Mean, Std làm phình to dữ liệu và gây bối rối cho mô hình, chúng ta chỉ giữ lại cột biến trễ đơn giản `Lag_1` (thông số của 10 phút trước) để mô hình nắm được "quán tính" hệ thống.

---

### 2. Thực thi Processing Job trên AWS

Để yêu cầu SageMaker cấp phát máy chủ và chạy đoạn mã `preprocessing.py` ở trên, chúng ta dùng thư viện `sagemaker.sklearn.processing` qua script `processing_job.py`.

Mở Terminal và chạy lệnh sau:

```bash
# Đảm bảo bạn đang ở môi trường ảo (virtual environment)
.\.venv\Scripts\python aws/processing_job.py
```

**Quá trình hoạt động của hệ thống:**
1. Khởi tạo một `SKLearnProcessor` với môi trường Python 1.2, loại máy chủ `ml.t3.medium`.
2. Tạo các luồng input (`ProcessingInput`): Kéo dữ liệu thô từ `s3://.../data/raw/` và source code từ `s3://.../scripts/src/` vào máy chủ SageMaker.
3. Thực thi kịch bản `preprocessing.py`.
4. Tạo các luồng output (`ProcessingOutput`): Đẩy các file kết quả (`train.csv`, `test.csv`, `processed.csv`) ngược lại lên S3.

**Kết quả màn hình hiển thị sau khi hoàn tất:**

```text
Đang submit SageMaker Processing Job...
...
Processing Job hoàn tất!
 Processed : s3://amznce23/T1_AD/data/processed/
 Train     : s3://amznce23/T1_AD/data/features/train/
 Test      : s3://amznce23/T1_AD/data/features/test/
```

{{% notice tip %}}
**Sẵn sàng cho huấn luyện:**
Dữ liệu lúc này đã được chia tập Train/Test, làm sạch chuyên sâu và lưu tại các thư mục S3 tương ứng. Ở bước tiếp theo, chúng ta sẽ nạp dữ liệu này vào thuật toán XGBoost để bắt đầu học.
{{% /notice %}}