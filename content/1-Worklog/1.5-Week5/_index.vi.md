---
title: "Worklog Tuần 5"
date: 2026-06-28
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Triển khai nhóm thuật toán Học không giám sát truyền thống để phát hiện bất thường dựa trên các đặc trưng đã chuẩn hóa.
* Xây dựng mô hình Gaussian Mixture Model (GMM) để đánh giá dị thường dựa trên mật độ phân phối xác suất.
* Xây dựng mô hình Isolation Forest (iForest) để đánh giá dị thường dựa trên cấu trúc phân nhánh dạng cây.
* Lưu trữ điểm số dị thường của từng mô hình nhằm phục vụ cho bước đối sánh tổng thể ở tuần đánh giá.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Huấn luyện mô hình GMM:**<br>&emsp; + Khởi tạo Gaussian Mixture Model từ thư viện Scikit-learn.<br>&emsp; + Tinh chỉnh tham số `n_components` (số lượng cụm) dựa trên tiêu chuẩn thông tin BIC/AIC để mô hình hóa chính xác các trạng thái vận hành của tuabin (cut-in, rated, cut-out). | 29/06/2026 | 29/06/2026 | <https://scikit-learn.org/stable/modules/mixture.html> |
| 3 | - **Trích xuất Log-Likelihood (GMM):** <br>&emsp; + Tính toán hàm log-likelihood cho từng điểm dữ liệu trong tập Test. <br>&emsp; + Các điểm có xác suất rơi vào phân phối cực thấp (vượt ngưỡng phần trăm dưới) sẽ được gán nhãn dự đoán là bất thường. | 30/06/2026 | 30/06/2026 | |
| 4 | - **Huấn luyện mô hình Isolation Forest:** <br>&emsp; + Xây dựng mô hình dựa trên thuật toán tập hợp. <br>&emsp; + Cấu hình siêu tham số `contamination` (tỷ lệ dị thường dự kiến) dựa trên tỷ lệ mất cân bằng phân lớp đã tính toán ở tập nhãn giả của Tuần 4. | 01/07/2026 | 01/07/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html> |
| 5 | - **Trích xuất Anomaly Score (iForest):** <br>&emsp; + Trích xuất đường đi trung bình từ gốc đến lá cho các điểm dữ liệu. <br>&emsp; + Xác định các điểm có độ sâu phân nhánh ngắn nhất (dễ bị cô lập nhất) làm tín hiệu cảnh báo hỏng hóc thiết bị. | 02/07/2026 | 02/07/2026 | |
| 6 | - **Tổng hợp kết quả dự đoán :** <br>&emsp; + Tạo một DataFrame lưu trữ song song: Nhãn giả - Dự đoán của GMM - Dự đoán của iForest. <br>&emsp; + Chuẩn bị nền tảng dữ liệu để đối đầu với các mô hình Deep Learning phức tạp ở tuần kế tiếp. | 03/07/2026 | 03/07/2026 | |

### Kết quả đạt được tuần 5:

*   **Thiết lập baseline học máy truyền thống:** Hoàn thiện triển khai hai thuật toán phát hiện bất thường mang đặc tính phân loại trực giao: GMM (dựa trên ước lượng mật độ xác suất) và Isolation Forest (dựa trên phân chia không gian dữ liệu). Việc áp dụng hai kiến trúc khác biệt thiết lập một mốc cơ sở (baseline) khách quan, hạn chế sai lệch (bias) do cấu trúc thuật toán gây ra trên tập dữ liệu SCADA.
*   **Lượng hóa siêu tham số:** Cấu hình của các mô hình được tinh chỉnh dựa trên các đại lượng đo lường toán học cụ thể. Không gian cụm `n_components` của GMM được xác định qua giá trị cực tiểu của tiêu chuẩn thông tin BIC/AIC nhằm phản ánh chính xác các pha khí động học của tuabin. Tham số tỷ lệ nhiễu `contamination` của iForest được tham chiếu trực tiếp từ phân phối nhãn giả đã thiết lập.
*   **Chuẩn hóa không gian lưu trữ dự đoán:** Trích xuất và hợp nhất các mảng điểm số dị thường và nhãn dự đoán từ cả hai mô hình vào một DataFrame thống nhất. 