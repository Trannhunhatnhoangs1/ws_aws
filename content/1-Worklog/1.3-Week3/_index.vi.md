---
title: "Worklog Tuần 3"
date: 2026-06-14
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Chuyển đổi dữ liệu SCADA đã làm sạch thành các tín hiệu toán học tối ưu cho mô hình học máy.
* Thiết kế các đặc trưng động học nhằm bắt được đạo hàm biến thiên vật lý của hệ thống cơ khí.
* Xóa bỏ sự chênh lệch về đơn vị đo lường (m/s, kW, °C) bằng các kỹ thuật chuẩn hóa không gian dữ liệu.
* Đánh giá và lọc ra 6 đặc trưng cốt lõi đóng góp cao nhất vào phương sai của toàn bộ tập dữ liệu.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Phân tích tương quan:**<br>&emsp; + Sử dụng ma trận tương quan và Heatmap của Seaborn để phân tích mối quan hệ tuyến tính giữa tất cả các biến cảm biến trong file SCADA.<br>&emsp; + Loại bỏ các biến bị đa cộng tuyến quá cao để giảm thiểu nhiễu và độ phức tạp tính toán cho mô hình sau này. | 15/06/2026 | 15/06/2026 | <https://seaborn.pydata.org/generated/seaborn.heatmap.html> |
| 3 | - **Thiết kế đặc trưng động học:** <br>&emsp; + Tính toán sai phân bậc 1 (`diff_1`) cho hai biến quan trọng nhất là Vận tốc gió và Công suất thực tế. <br>&emsp; + Mục đích: Chuyển đổi từ việc chỉ quan sát "giá trị tĩnh" tại một thời điểm sang việc giám sát "tốc độ thay đổi" giữa các khung thời gian liên tiếp nhằm bắt được các sự cố sụt áp đột ngột. | 16/06/2026 | 16/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.diff.html> |
| 4 | - **Chuẩn hóa Không gian Dữ liệu:** <br>&emsp; + Áp dụng thuật toán `StandardScaler` (Z-score Normalization) từ thư viện Scikit-learn. <br>&emsp; + Ép toàn bộ các biến số học về cùng một phân phối (mean = 0, variance = 1), giúp các thuật toán dựa trên khoảng cách (như GMM hay LOF) có thể hội tụ nhanh và không bị thiên lệch bởi thang đo vật lý. | 17/06/2026 | 17/06/2026 | <https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html> |
| 5 | - **Lựa chọn Đặc trưng Lõi:** <br>&emsp; + Chạy các kỹ thuật phân tích phương sai để đánh giá tầm quan trọng của từng đặc trưng. <br>&emsp; + Chốt danh sách 6 đặc trưng tối ưu nhất (bao gồm cả biến tĩnh và biến động học `diff_1`) để làm đầu vào cho bước huấn luyện mô hình. | 18/06/2026 | 18/06/2026 | <https://scikit-learn.org/stable/modules/feature_selection.html> |
| 6 | - **Đóng gói Dữ liệu Huấn luyện:** <br>&emsp; + Chuyển đổi định dạng dữ liệu từ Pandas DataFrame sang cấu trúc thuần Numpy Array (`.values`) để chuẩn bị sẵn sàng cho luồng đưa lên AWS SageMaker. <br>&emsp; + Xuất file `features_train.csv` và `features_test.csv`. | 19/06/2026 | 19/06/2026 | Tài liệu chuẩn bị dữ liệu nội bộ |

### Kết quả đạt được tuần 3:

*   **Kết quả trích xuất:** Lọc và thiết kế thành công 6 đặc trưng cốt lõi đóng góp cao nhất vào phương sai của tập dữ liệu. Hoàn tất việc đồng nhất không gian dữ liệu bằng phương pháp chuẩn hóa Z-score, đảm bảo mọi biến số đều có trọng số tác động công bằng khi đưa vào mô hình học máy.
*   **Góc nhìn động lực học & toán học:** Các mô hình phát hiện bất thường cực kỳ nhạy cảm với thang đo. Z-score normalization đã ép các biến số đo lường (m/s, kW, °C) về cùng một không gian toán học, giúp thuật toán hội tụ nhanh và chính xác hơn, tránh tình trạng mô hình bị "mù" bởi các biến có giá trị tuyệt đối lớn.
*   **Cải tiến kỹ thuật đặc trưng:** Triển khai phương pháp toán học sai phân bậc 1 (`diff_1`) nhằm số hóa tốc độ biến thiên của tín hiệu cảm biến theo thời gian. Dựa trên đặc tính quán tính cơ học lớn của hệ thống tuabin gió, các dao động tín hiệu có biên độ bất thường trong khung thời gian hẹp thường phản ánh lỗi phần cứng hoặc nhiễu đo lường. Việc tích hợp đặc trưng động học này cung cấp cho mô hình cơ sở đánh giá toàn diện hơn, kết hợp giữa giá trị tĩnh tại thời điểm thực và gia tốc biến thiên của hệ thống.