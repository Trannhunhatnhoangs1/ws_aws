---
title: "Worklog Tuần 4"
date: 2026-06-21
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Xây dựng cơ sở dữ liệu nhãn giả dựa trên sự sai lệch giữa Công suất thực tế và Công suất lý thuyết của tuabin gió.
* Thiết lập các ngưỡng thống kê khách quan để phân loại ranh giới giữa trạng thái vận hành Bình thường (0) và Bất thường (1).
* Tạo lập tập dữ liệu nhãn cơ sở quy mô nhỏ nhằm làm thước đo đánh giá hiệu năng cho các mô hình Học không giám sát ở các giai đoạn sau.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Tính toán Sai số phần dư:**<br>&emsp; + Áp dụng phương trình Đường cong công suất đã nội suy từ tuần 2 để tính toán Công suất lý thuyết dự kiến cho từng mức Vận tốc gió.<br>&emsp; + Trừ Công suất thực tế cho Công suất lý thuyết để thu được mảng sai số phần dư cho từng điểm dữ liệu. | 22/06/2026 | 22/06/2026 | <https://numpy.org/doc/stable/reference/generated/numpy.subtract.html> |
| 3 | - **Định chuẩn Ngưỡng thống kê:** <br>&emsp; + Phân tích phân phối của tập sai số phần dư. <br>&emsp; + Áp dụng phương pháp khoảng tứ phân vị (IQR - Interquartile Range) để xác định các giới hạn kiểm soát trên (UCL) và dưới (LCL), khoanh vùng các điểm dữ liệu nằm ngoài phương sai thông thường của hệ thống. | 23/06/2026 | 23/06/2026 | <https://docs.scipy.org/doc/scipy/reference/stats.html> |
| 4 | - **Triển khai Gán nhãn giả (Pseudo-labeling):** <br>&emsp; + Lập trình hàm ánh xạ trên Pandas. <br>&emsp; + Gán nhãn `1` (Bất thường) cho các điểm dữ liệu có sai số phần dư vượt ngưỡng kiểm soát, và nhãn `0` (Bình thường) cho các điểm nằm trong biên độ an toàn. | 24/06/2026 | 24/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html> |
| 5 | - **Trực quan hóa Đối sánh:** <br>&emsp; + Xây dựng lại biểu đồ phân tán của Vận tốc gió và Công suất. <br>&emsp; + Phủ màu phân biệt hai tập nhãn `0` và `1` để kiểm chứng bằng mắt thường xem các quy tắc vật lý có khớp với trạng thái phân cụm thực tế hay không. | 25/06/2026 | 25/06/2026 | <https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html> |
| 6 | - **Tích hợp Nhãn cơ sở:** <br>&emsp; + Tích hợp trực tiếp mảng nhãn giả thành một đặc trưng mới vào cấu trúc DataFrame hiện tại trên bộ nhớ phục vụ cho pipeline tiếp theo. <br>&emsp; + Đánh giá tỷ lệ phân bổ lớp (Class distribution) để định lượng mức độ mất cân bằng dữ liệu. | 26/06/2026 | 26/06/2026 | |

### Kết quả đạt được tuần 4:

*   **Xây dựng nhãn cơ sở:** Giải quyết thành công rào cản lớn nhất của dữ liệu SCADA công nghiệp là sự thiếu hụt nhãn. Bằng việc quy chuẩn hóa sai số vật lý thành các nhãn nhị phân, dự án đã có một bộ dữ liệu đầu vào hoàn chỉnh để đối chuẩn.
*   **Góc nhìn toán học thống kê:** Sử dụng phương pháp thống kê IQR trên mảng phần dư đảm bảo tính khách quan tuyệt đối. Phương pháp này định lượng hóa chính xác biên giới giữa một đợt sụt áp tự nhiên do nhiễu gió và một sự cố bất thường về cơ điện.
*   **Thiết lập chuẩn đối sánh:** Cung cấp một hệ quy chiếu bằng số liệu cụ thể. Tập nhãn giả này sẽ đóng vai trò là dữ liệu nhãn cơ sở, cho phép đo lường trực tiếp các chỉ số độ chính xác (Precision, Recall, F1-Score) của các thuật toán phân cụm phức tạp ở các tuần kế tiếp, khắc phục triệt để điểm yếu "hộp đen" của Học không giám sát.