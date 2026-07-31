---
title: "Worklog Tuần 6"
date: 2026-07-12
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Triển khai kiến trúc mạng nơ-ron học sâu chuyên dụng cho dữ liệu chuỗi thời gian.
* Cấu trúc lại định dạng dữ liệu đầu vào thành các tensor 3 chiều phục vụ cho lớp mạng hồi quy.
* Xây dựng và huấn luyện mô hình LSTM-Autoencoder để học các biểu diễn phi tuyến tính của trạng thái vận hành bình thường.
* Lượng hóa Sai số tái tạo thành điểm số cảnh báo dị thường.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Chuyển đổi cấu trúc dữ liệu:**<br>&emsp; + Áp dụng kỹ thuật Cửa sổ trượt để chuyển đổi dữ liệu dạng bảng 2D thành tensor 3D `(samples, time_steps, features)`.<br>&emsp; + Tách riêng tập dữ liệu chỉ chứa nhãn Bình thường (`0`) để phục vụ huấn luyện kiến trúc Autoencoder. | 06/07/2026 | 06/07/2026 | <https://keras.io/api/layers/recurrent_layers/lstm/> |
| 3 | - **Thiết kế kiến trúc LSTM-Autoencoder:** <br>&emsp; + Khởi tạo luồng Mã hóa với các lớp LSTM để nén dữ liệu chuỗi thời gian thành vector tiềm ẩn <br>&emsp; + Khởi tạo luồng Giải mã với cấu trúc đối xứng để tái tạo lại chuỗi tín hiệu đầu vào từ vector tiềm ẩn. | 07/07/2026 | 07/07/2026 | |
| 4 | - **Huấn luyện mô hình học sâu:** <br>&emsp; + Biên dịch mô hình với hàm mất mát MSE và thuật toán tối ưu Adam. <br>&emsp; + Tiến hành huấn luyện trên tập dữ liệu bình thường, áp dụng kỹ thuật Early Stopping để ngăn chặn quá khớp (Overfitting). | 08/07/2026 | 08/07/2026 | <https://keras.io/api/callbacks/early_stopping/> |
| 5 | - **Trích xuất sai số tái tạo (Reconstruction Error):** <br>&emsp; + Thực hiện luồng suy diễn trên toàn bộ tập Test (bao gồm cả dữ liệu chứa nhãn `1`). <br>&emsp; + Tính toán độ lệch tuyệt đối trung bình (MAE) giữa dữ liệu gốc và dữ liệu được tái tạo cho từng khung thời gian. | 09/07/2026 | 09/07/2026 | |
| 6 | - **Tích hợp tín hiệu Deep Learning:** <br>&emsp; + Chuyển đổi mảng Sai số tái tạo thành điểm bất thường tương ứng cho từng điểm dữ liệu ban đầu. <br>&emsp; + Bổ sung cột dự đoán của LSTM-Autoencoder vào DataFrame tổng hợp đã khởi tạo từ Tuần 5. | 10/07/2026 | 10/07/2026 | |

### Kết quả đạt được tuần 6:

*   **Khai thác đặc trưng không gian - thời gian:** Việc áp dụng cấu trúc LSTM trên khung cửa sổ thời gian đã khắc phục hoàn toàn điểm mù của các thuật toán tĩnh. Hệ thống nay có khả năng nhận diện các dị thường mang tính xu hướng thay vì chỉ phát hiện các điểm đột biến cục bộ.
*   **Định lượng dị thường thông qua sai số tái tạo:** Mô hình được thiết lập để học và ghi nhớ duy nhất cấu trúc của dữ liệu vận hành bình thường. Do đó, khi hệ thống nhận vào các tín hiệu hỏng hóc, mô hình sẽ không thể giải mã chính xác, từ đó sinh ra sai số lớn. Cơ chế này giúp đo lường mức độ bất thường một cách trực quan mà không cần ép buộc dữ liệu phải tuân theo các giả định phân phối thống kê (như phân phối chuẩn) từ trước.
*   **Hoàn thiện hệ sinh thái đối sánh:** Triển khai thành công kiến trúc học sâu phức tạp và đồng bộ hóa kết quả đầu ra vào cùng một không gian lưu trữ với khối học máy truyền thống. Hệ thống đã thu thập đủ tham số từ 3 thuật toán lõi (GMM, iForest, LSTM-AE), tạo nền tảng dữ liệu toàn diện sẵn sàng cho pha đánh giá hiệu năng.