---
title: "Event 1"
date: 2026-06-13
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “AWS Study Group Community Sharing Session”

### Mục Đích Của Sự Kiện

- Chia sẻ bức tranh thực tế về công việc, cơ hội nghề nghiệp và lộ trình phát triển trong các lĩnh vực Cloud, DevOps, Data Analytics và AI.
- Giới thiệu quy trình tuyển dụng tiêu chuẩn, kỹ năng cốt lõi và văn hóa làm việc tại các Tập đoàn Đa quốc gia (MNCs).
- Phân tích kiến trúc hệ thống thực tế (case study URL Shortener) và các nguyên lý thiết kế ứng dụng có khả năng mở rộng cao trên AWS.
- Giới thiệu cộng đồng AWS Student Builder Group và lộ trình đồng hành, học tập thực chiến dành cho sinh viên.

### Danh Sách Diễn Giả

- **Mr. Cường Nguyễn** - Process Engineer
- **Mr. Đạt Phạm** - Data Analytics Engineer (Kamereo / Colgate-Palmolive)
- **Mr. Trương Hoàng Trọng** - DevOps Engineer @ Endava Vietnam
- **Mr. Danh Hoàng Hiếu Nghị** - AI Engineer, AWS Community Builder & AWS Student Builder Group Leader
- **Mr. Đinh Trung Kiên** - Lead Developer at Startup
- **Mr. Nguyễn Minh Thọ** - Student

---

### Nội Dung Nổi Bật

#### 1. Thực tế công việc Data Analytics & Văn hóa tại tập đoàn đa quốc gia (MNC)
- **Công việc thực tế:** Phân tích chỉ số vận hành/kinh doanh (GMV, Fill Rate, Last Mile Cost), thiết kế Dashboard quản lý xu hướng, phát hiện bất thường và tối ưu chi phí sản xuất/IoT trong nhà máy.
- **Bộ kỹ năng cốt lõi:** Tư duy phản biện, kỹ năng giao tiếp, giải quyết vấn đề và đặc biệt là "Kể chuyện với dữ liệu" (Data Storytelling).
- **Mô hình phát triển 5 cấp độ:** Follower → Learner → Problem Solver → System Thinker → Super Star.
- **Quy trình tuyển dụng MNC:** Sàng lọc ATS/Sơ vấn → Test năng lực → Phỏng vấn chuyên môn (STAR model) → Hòa hợp văn hóa.
- **Văn hóa doanh nghiệp nổi bật:** Văn hóa *No-Blame Post-Mortem* (tập trung tìm nguyên nhân gốc rễ thay vì đổ lỗi cá nhân) và văn hóa *Caring & Inclusive*.

#### 2. Góc nhìn thực tế về nghề DevOps (DevOps Engineer)
- **Thực tế công việc:** Không chỉ viết pipeline CI/CD hay quản lý Docker/Kubernetes, công việc thực tế đòi hỏi giải quyết các bài toán vận hành 24/7, incident handling, troubleshooting, hỗ trợ môi trường, tối ưu chi phí Cloud và xác định quyền sở hữu hệ thống.
- **Lộ trình học tập cơ bản:** Làm chủ Linux, Networking, lập trình (Python/Golang), Git/CI-CD, Containers và xây dựng các project nhỏ thực chiến.
- **Tư duy DevOps giỏi:** "Tools change, Fundamentals stay" — Tập trung tư duy hệ thống (System Thinking), tự động hóa công việc lặp lại và dùng AI như công cụ đòn bẩy nâng cao hiệu suất.

#### 3. Thiết kế hệ thống URL Shortener mở rộng quy mô (Scalable URL Shortener on AWS)
- **Vấn đề của hệ thống truyền thống:** Dễ bị nghẽn (Single Point of Failure), độ trễ đọc cao, khó mở rộng scale.
- **Kiến trúc tối ưu trên AWS:**
  - *Front-end & Security:* Amazon CloudFront, AWS WAF, Amazon Amplify, Route 53, Cognito.
  - *Key Generation Service (KGS):* Tiền tạo mã ngắn (short code) lưu vào Amazon ElastiCache (Redis) giúp việc tạo URL diễn ra tức thì, tránh đụng độ (collision-free).
  - *Backend & Database:* AWS Fargate (ECS Cluster), Amazon DynamoDB, ElastiCache Redis áp dụng mô hình Cache-aside Pattern để tối ưu latency.
- **Các nguyên lý kiến trúc rút ra:** Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, và Cache-aside Pattern.

#### 4. Hành trình từ Sinh viên đến AWS Partner & Cộng đồng AWS Student Builder Group
- **8 bước phát triển:** 
Student Curiosity → First Cloud Journey → Workshop & Community → Hands-on Labs → School Projects → Portfolio → AWS Partner → Share Back.
- **Cộng đồng AWS Student Builder Group:** Giới thiệu các chương trình hỗ trợ sinh viên, quyền lợi nhận AWS Credits, Swag, Voucher thi chứng chỉ AWS và tham gia các sự kiện chuyên ngành (AWS Community Day).

---

### Kết quả đạt được

#### Tư Duy Định Hướng Sự Nghiệp
- **Chủ động trong học tập:** Chuyển dịch từ thế thụ động (Follower) sang tư duy giải quyết vấn đề (Problem Solver) và tư duy hệ thống toàn cảnh (System Thinker).
- **Giá trị của nền tảng:** Công cụ công nghệ thay đổi liên tục, nhưng kiến thức nền tảng (Linux, Networking, Data, System Design) mới là cốt lõi lâu dài.
- **Thực hành đòn bẩy AI:** Tận dụng AI để tăng tốc công việc thay vì phụ thuộc hoàn toàn khiến tư duy bị thụ động.

#### Kiến Trúc Kỹ Thuật & Thực Chiến
- **Thiết kế kiến trúc chịu tải:** Nắm vững cách tách biệt luồng xử lý (Read/Write path), đưa bảo mật và cache ra mép mạng (Defense at the Edge).
- **Ứng dụng dịch vụ Cloud linh hoạt:** Hiểu cách phối hợp giữa Compute (Fargate/EC2), Database (DynamoDB), In-memory Cache (ElastiCache Redis) và Edge Services (CloudFront/WAF).

---

### Ứng Dụng Vào Công Việc

- **Rèn luyện tư duy System Thinking:** Áp dụng mô hình phân tích nguyên nhân gốc rễ (Root cause analysis) khi gặp sự cố hệ thống.
- **Cải thiện kỹ năng Data/Report:** Luyện tập cách trình bày số liệu gắn liền với ngữ cảnh kinh doanh/vận hành (Data Storytelling).
- **Thực hành thiết kế hệ thống:** Áp dụng các kiến trúc mẫu như Cache-aside, Async Queuing vào các đồ án và bài tập thiết kế phần mềm.
- **Tham gia cộng đồng:** Đăng ký và sinh hoạt tích cực tại AWS Student Builder Group, thực hành các bài lab trên First Cloud Journey để tích lũy kinh nghiệm thực chiến.

---

### Trải nghiệm trong event

Buổi Meetup **“AWS Study Group Community Sharing Session”** là một sự kiện vô cùng ý nghĩa, mang lại nhiều giá trị practical từ góc nhìn của các diễn giả dày dặn kinh nghiệm trong ngành. Một số trải nghiệm nổi bật:

#### Học hỏi từ câu chuyện thực tế
- Lắng nghe những chia sẻ thẳng thắn về môi trường làm việc tại MNCs, giúp xóa bỏ các lầm tưởng về công việc của Data Analytics Engineer và DevOps Engineer.
- Học hỏi được tư duy *No-Blame Culture* – một bài học văn hóa quan trọng khi làm việc nhóm và xử lý sự cố.

#### Trải nghiệm phân tích kiến trúc chuyên sâu
- Ấn tượng với phần phân tích case study URL Shortener, từ việc chỉ ra điểm yếu của mô hình đơn giản đến cách nâng cấp từng bước lên kiến trúc Cloud đáp ứng lượng truy cập lớn.

#### Mở rộng mạng lưới kết nối
- Được giao lưu trực tiếp với các diễn giả, anh chị đi trước và các bạn sinh viên cùng định hướng, qua đó hiểu rõ hơn về các chương trình hỗ trợ sinh viên của AWS.

#### Một số hình ảnh khi tham gia sự kiện
<div style="display: flex; gap: 20px;">
  <img src="/images/4-Events/event1/1.png" alt="Sự kiện 1" style="width: 50%; height: 300px; object-fit: cover;">
  <img src="/images/4-Events/event1/2.png" alt="Sự kiện 2" style="width: 50%; height: 300px; object-fit: cover;">
</div>

> Tổng kết: Sự kiện đã tiếp thêm cho em nhiều động lực, củng cố định hướng nghề nghiệp rõ ràng và cung cấp những bài học kiến thức kỹ thuật lẫn kỹ năng mềm rất giá trị cho chặng đường phát triển sắp tới.