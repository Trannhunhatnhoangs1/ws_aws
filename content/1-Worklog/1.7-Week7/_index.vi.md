---
title: "Worklog Tuần 7"
date: 2026-07-19
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Thiết lập một quy trình chuẩn đối sánh toàn diện cho 3 thuật toán đã triển khai (GMM, iForest, LSTM-AE).
* Đo lường hiệu năng thực tế của từng mô hình dựa trên bộ nhãn giả đã xây dựng.
* Lựa chọn mô hình tối ưu nhất để tiến hành đóng gói và triển khai trên hạ tầng AWS.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Tính toán chỉ số đánh giá:**<br>&emsp; + Áp dụng thư viện Scikit-learn để trích xuất báo cáo phân loại.<br>&emsp; + Tính toán các chỉ số Precision, Recall và F1-Score cho từng mô hình dựa trên DataFrame đã tổng hợp. | 13/07/2026 | 13/07/2026 | <https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics> |
| 3 | - **Trực quan hóa hiệu năng:** <br>&emsp; + Vẽ đường cong ROC (Receiver Operating Characteristic) cho cả 3 mô hình trên cùng một biểu đồ. <br>&emsp; + Tính toán chỉ số diện tích dưới đường cong (AUC) để đánh giá khả năng phân tách nhãn của mô hình độc lập với các ngưỡng. | 14/07/2026 | 14/07/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_curve.html> |
| 4 | - **Phân tích đánh đổi:** <br>&emsp; + Đánh giá trọng số thiệt hại giữa sai lầm loại 1 (False Positives - Cảnh báo giả) và sai lầm loại 2 (False Negatives - Bỏ sót lỗi). <br>&emsp; + Định chuẩn lại ngưỡng quyết định để ưu tiên chỉ số Recall, giảm thiểu tối đa rủi ro tuabin hỏng hóc mà không được cảnh báo. | 15/07/2026 | 15/07/2026 | |
| 5 | - **Chốt Mô hình Tối ưu:** <br>&emsp; + Dựa trên kết quả định lượng tổng hợp từ F1-Score và AUC, so sánh trực diện hiệu năng của khối học máy truyền thống và học sâu. <br>&emsp; + Chính thức quyết đinh kiến trúc thuật nào phù hợp nhất cho bài toán giám sát chuỗi thời gian của dự án. | 16/07/2026 | 16/07/2026 | |
| 6 | - **Đóng gói Mô hình:** <br>&emsp; + Lưu trữ kiến trúc, bộ trọng số và các đối tượng tiền xử lý của mô hình Best Fit thành tệp tin định dạng tiêu chuẩn `.pkl`. <br>&emsp; + Cô lập môi trường thư viện (requirements.txt) chuẩn bị cho luồng tích hợp lên AWS SageMaker. | 17/07/2026 | 17/07/2026 | |

### Kết quả đạt được tuần 7:

*   **Thiết lập báo cáo đối sánh:** Hoàn thành đánh giá định lượng cho ba kiến trúc thuật toán (GMM, iForest, LSTM-AE). Căn cứ trên các chỉ số hiệu năng phân loại (Precision, Recall, F1-Score) và diện tích dưới đường cong (ROC-AUC), mô hình có năng lực phân tách nhiễu tốt nhất được xác định thông qua bộ nhãn giả cơ sở.
*   **Hiệu chỉnh trọng số thiệt hại:** Áp dụng phân tích đánh đổi trên ma trận nhầm lẫn. Ngưỡng phân loại của mô hình được hiệu chỉnh nhằm tối đa hóa chỉ số Recall, ưu tiên phát hiện sớm tín hiệu hỏng hóc (giảm False Negatives) để đáp ứng yêu cầu quản lý rủi ro thiết bị.
*   **Đóng gói Artifacts:** Mô hình đạt hiệu năng cao nhất được trích xuất thành các tệp tin tĩnh (dạng `.pkl`). Khối tiền xử lý dữ liệu và cấu hình môi trường thực thi được cô lập thành công, xác lập trạng thái sẵn sàng cho quy trình triển khai lên nền tảng đám mây.