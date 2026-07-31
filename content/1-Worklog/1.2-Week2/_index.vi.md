---
title: "Worklog Tuần 2"
date: 2026-06-07
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Thực hiện Phân tích Khám phá Dữ liệu (EDA) trên tập dữ liệu SCADA thô của tuabin gió để hiểu rõ phân phối và quy luật tiềm ẩn.
* Xác định và xử lý triệt để các giá trị khuyết thiếu (NaN) mà không làm phá vỡ tính liên tục của dữ liệu chuỗi thời gian.
* Phát hiện và lọc bỏ các dị thường vật lý (ví dụ: nhiễu cảm biến, công suất âm khi vận tốc gió cao) bằng kiến thức chuyên ngành năng lượng gió.
* Trực quan hóa và thiết lập đường cong công suất lý thuyết của tuabin nhằm tạo cơ sở đối sánh cho trạng thái vận hành bình thường.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Tải và khảo sát dữ liệu sơ bộ:**<br>&emsp; + Sử dụng thư viện Pandas để đọc file `T1_train.csv` vào DataFrame.<br>&emsp; + Đánh giá thống kê cơ bản thông qua hàm `.info()` và `.describe()` để đo lường độ thưa của dữ liệu và khoanh vùng các điểm khuyết thiếu (NaNs). | 08/06/2026 | 08/06/2026 | <https://pandas.pydata.org/docs/user_guide/10min.html> |
| 3 | - **Xử lý giá trị khuyết thiếu:** <br>&emsp; + Phân tích bản chất của việc mất mát dữ liệu (do rớt mạng ngắn hạn hay hỏng hóc thiết bị viễn thông dài hạn). <br>&emsp; + Áp dụng phương pháp nội suy tuyến tính (Linear Interpolation) để điền vào các khoảng trống ngắn hạn, bảo toàn tuyệt đối tính toàn vẹn của chuỗi thời gian và ngăn chặn sự sai lệch thuật toán. | 09/06/2026 | 09/06/2026 | <https://scikit-learn.org/stable/modules/impute.html> |
| 4 | - **Lọc nhiễu vật lý:** <br>&emsp; + Áp dụng các ràng buộc vật lý để loại bỏ các giá trị vô lý (ví dụ: Công suất thực tế < 0 kW trong khi Vận tốc gió nằm trong ngưỡng hoạt động, hoặc Vận tốc gió vượt ngưỡng giới hạn cắt > 25m/s). <br>&emsp; + Phân biệt rạch ròi giữa "Nhiễu hệ thống đo lường" (cần loại bỏ) và "Dấu hiệu hư hỏng thiết bị" (cần giữ lại để huấn luyện mô hình). | 10/06/2026 | 10/06/2026 | |
| 5 | - **Trực quan hóa và lập bản đồ đường cong công suất:** <br>&emsp; + Sử dụng Matplotlib và Seaborn để vẽ biểu đồ phân tán (Scatter Plot) biểu diễn mối tương quan giữa Vận tốc gió (trục X) và công suất thực tế (trục Y). <br>&emsp; + Khắc họa thành công đường cong công suất lý thuyết, trực quan hóa rõ ràng 3 vùng: tốc độ gió khởi động (cut-in), định mức (rated), và ngưỡng cắt (cut-out). | 11/06/2026 | 11/06/2026 | <https://seaborn.pydata.org/tutorial/relational.html> |
| 6 | - **Chuẩn hóa tập dữ liệu:** <br>&emsp; + Thực hiện khâu kiểm thử chất lượng (QA) cuối cùng để đảm bảo tập dữ liệu sạch 100%. <br>&emsp; + Xuất dữ liệu đã xử lý ra định dạng `.csv` trung gian, tạo nền tảng vững chắc cho giai đoạn trích xuất đặc trưng. | 12/06/2026 | 12/06/2026 | <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html> |

### Kết quả đạt được tuần 2:

*   **Đảm bảo chất lượng dữ liệu:** Xử lý thành công 100% các giá trị khuyết thiếu (NaNs) và loại bỏ hoàn toàn các dị thường vật lý do thời tiết khắc nghiệt hoặc rớt mạng truyền tải. Tập dữ liệu SCADA thô đã được làm sạch và tối ưu hóa hoàn toàn cho quá trình mô hình hóa toán học.
*   **Góc nhìn kỹ thuật hệ thống:** Thao tác nội suy tuyến tính đã phát huy tối đa hiệu quả trong việc duy trì biên độ dao động tự nhiên của thiết bị cơ khí. Bước xử lý này đảm bảo tính toàn vẹn và liền mạch của chuỗi thời gian, giúp thuật toán Machine Learning đọc được chính xác trạng thái vật lý của hệ thống mà không bị giật cục hay sai lệch tín hiệu.
*   **Ứng dụng kiến thức chuyên ngành:** Chuyển hóa thành công các ràng buộc cơ khí của tuabin gió thành tư duy lập trình logic. Bằng việc vẽ chính xác đường cong công suất, hệ thống đã có một hệ quy chiếu vững chắc để dễ dàng bóc tách các sai lệch trong các pha học không giám sát.