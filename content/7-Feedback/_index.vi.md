---
title: "Chia sẻ, đóng góp ý kiến"
date: 2026-07-30
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

### Đánh giá chung

**1. Môi trường làm việc**  
Chương trình First Cloud AI Journey (FCAJ) đã mang lại một môi trường thực hành đám mây (Cloud) chuyên nghiệp và năng động. Việc được tiếp cận trực tiếp với hệ sinh thái AWS giúp mình làm quen với nhịp độ công việc thực tế của một Kỹ sư MLOps. Không gian làm việc nhóm và các công cụ hỗ trợ luôn hoạt động trơn tru, giúp mình dễ dàng thảo luận các vấn đề kỹ thuật với mọi người.

**2. Sự hỗ trợ của mentor / team admin**  
Mình cực kỳ ấn tượng với sự hỗ trợ nhiệt tình từ các Mentor. Khi gặp khó khăn trong việc xử lý mất cân bằng nhãn cho tập dữ liệu SCADA hay cấu hình phân quyền IAM Role cho SageMaker, các anh không chỉ gợi ý sử dụng tham số `scale_pos_weight` mà còn giải thích rất cặn kẽ về bản chất toán học cũng như cách luồng dữ liệu hoạt động trên AWS. Các anh chị admin cũng rất sát sao trong việc nhắc nhở tiến độ và cung cấp tài liệu kịp thời.

**3. Sự phù hợp giữa công việc và chuyên ngành học**  
Dự án "Phát hiện dị thường từ dữ liệu SCADA bằng MLOps" hoàn toàn trùng khớp với định hướng chuyên ngành Trí tuệ Nhân tạo / Khoa học Dữ liệu mà mình đang theo đuổi. Những kiến thức hàn lâm ở trường về thuật toán XGBoost hay Data Preprocessing (ví dụ: biến đổi góc gió bằng lượng giác, bảo toàn outlier) nay được đặt vào một quy trình kỹ thuật nghiêm ngặt trên nền tảng Amazon SageMaker, giúp mình hiểu rõ vòng đời thực tế của một mô hình học máy.

**4. Cơ hội học hỏi & phát triển kỹ năng**  
Thông qua FCAJ, mình đã rèn luyện được rất nhiều kỹ năng cốt lõi:
- **Kỹ năng Cloud Computing:** Làm chủ các dịch vụ AWS như S3 (Data Lake), IAM (Bảo mật), và SageMaker (Huấn luyện, HPO, Model Registry).
- **Kỹ năng Data Science:** Tiền xử lý dữ liệu cảm biến IoT/SCADA (xử lý Label_Error, time-series lag), tối ưu hóa siêu tham số tự động.
- **Kỹ năng làm việc nhóm & Giải quyết vấn đề:** Biết cách đọc log từ CloudWatch để debug lỗi và phối hợp công việc khi triển khai kiến trúc hệ thống.

**5. Văn hóa & tinh thần đồng đội**  
Tinh thần đồng đội trong nhóm mình rất tuyệt vời. Khi có lỗi về nhãn `Label_Error` bị biến đổi khi scale (như bạn Chương gặp phải), hay khi bạn Hạnh cần bổ sung tinh chỉnh mô hình local, mọi người đều xúm lại tìm cách giải quyết. Sự gắn kết và tinh thần "cùng tiến" luôn được duy trì ở mức cao nhất.

**6. Chính sách / phúc lợi cho thực tập sinh**  
Chương trình cung cấp tài khoản thực hành AWS giúp sinh viên chúng mình thoải mái triển khai kiến trúc mà không lo lắng về rào cản chi phí (Cloud Billing). Các buổi chia sẻ, workshop nội bộ được tổ chức bài bản, thực tế và mang tính ứng dụng rất cao.

### Một số câu hỏi khác

- **Điều bạn hài lòng nhất trong thời gian thực tập?**  
  Điều mình tự hào nhất là đã tự tay triển khai thành công một kiến trúc End-to-End MLOps lên đám mây AWS thay vì chỉ chạy code trên máy tính cá nhân. Nhìn thấy mô hình tự động lấy dữ liệu từ S3, tự động tuning (HPO), và lưu trữ vào Model Registry mang lại một cảm giác rất "thành tựu".

- **Điều bạn nghĩ công ty cần cải thiện cho các thực tập sinh sau?**  
  Mình hy vọng chương trình có thể bổ sung thêm một số buổi thực hành về cách theo dõi hiệu suất mô hình sau khi Deploy (ví dụ: xử lý Data Drift / Model Drift với SageMaker Model Monitor), vì đây cũng là một phần rất thực tế và quan trọng trong MLOps.

- **Nếu giới thiệu cho bạn bè, bạn có khuyên họ thực tập ở đây không? Vì sao?**  
  Chắc chắn là CÓ! Đây là bước đệm hoàn hảo để thu hẹp khoảng cách giữa lý thuyết Machine Learning ở trường đại học và kỹ năng vận hành mà các công ty công nghệ lớn đang yêu cầu.

### Đề xuất & mong muốn

- **Bạn có đề xuất gì để cải thiện trải nghiệm trong kỳ thực tập?**  
  Mong chương trình FCAJ có hỗ trợ thêm về phần cứng như các IoT Gateway hoặc vi điều khiển tại biên (Edge) để giả lập việc thu thập và đẩy luồng dữ liệu thời gian thực lên Amazon S3. Điều này sẽ hoàn thiện một bức tranh MLOps công nghiệp toàn diện từ thiết bị đến đám mây.
- **Bạn có muốn tiếp tục chương trình này trong tương lai?**  
  Mình rất mong muốn được tiếp tục đồng hành cùng chương trình, có thể ở các dự án nâng cấp thêm luồng CI/CD (như SageMaker Pipelines) hoặc với vai trò hỗ trợ các bạn khóa sau.
- **Góp ý khác (tự do chia sẻ):**  
  Cảm ơn đội ngũ FCAJ, Mentor và các anh chị admin đã tạo ra một sân chơi công nghệ vô cùng chất lượng và ý nghĩa!