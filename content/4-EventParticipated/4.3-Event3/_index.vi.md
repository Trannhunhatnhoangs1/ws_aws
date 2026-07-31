---
title: "Event 3"
date: 2026-07-25
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Bài thu hoạch “Agentic AI Build Week & Hackathon Journey”

### Mục Đích Của Sự Kiện

- **Hành trình Hackathon 24h thực chiến:** Trải nghiệm chuỗi 24 giờ liên tục từ ý tưởng, xây dựng MVP, thất bại đến hoàn thiện sản phẩm AI Agentic trên AWS.
- **Tiếp cận công nghệ AI Agentic tiên tiến:** Khám phá cách kết hợp giữa Real-time Computer Vision, AI Agents (Amazon Bedrock Agents, Strands Agent), và kiến trúc Cloud thế hệ mới.
- **Giải quyết các bài toán thực tế:** Lắng nghe và phân tích các giải pháp AI thực chiến do sinh viên và các nhóm phát triển triển khai phục vụ giám sát đám đông, tự động hóa kiến trúc Cloud, và phân tích rủi ro doanh nghiệp.
- **Rèn luyện bản lĩnh & tư duy sản phẩm:** Học cách tối ưu hóa phạm vi dự án (scope), vượt qua áp lực thời gian, thiếu ngủ và các sự cố kỹ thuật bất ngờ trong quá trình phát triển.

### Các Dự Án Nổi Bật Được Trình Bày

#### 1. S.H.E.P.H.E.R.D (Smart Human-flow Evaluation, Prediction, Hazard Detection, Response, and Dispatch) — Team 3KA
- **Mục tiêu & Tầm nhìn:** Hệ thống giám sát, đánh giá, dự báo mật độ đám đông và tự động đề xuất phương án điều phối nhân sự theo thời gian thực.
- **Bài toán giải quyết:** Thay thế việc giám sát thủ công tại các lối vào, hàng đợi hay khu vực sự kiện — vốn chậm trễ, khó mở rộng và dễ bỏ lỡ sự cố.
- **Công nghệ cốt lõi:**
  - *Computer Vision:* YOLO + ByteTrack phân tích luồng camera live, đếm người và theo dõi mật độ.
  - *AWS & AI Layer:* Kinesis Video Streams, Amazon SageMaker Endpoints, Amazon Bedrock AgentCore + Strands Agent, AWS Lambda, DynamoDB, và React Dashboard.
  - *Tính năng Agentic:* Tự động cảnh báo sớm ùn tắc (Autonomous Monitor) và hỗ trợ vận hành hỏi đáp dữ liệu trực tiếp bằng ngôn ngữ tự nhiên (Operator Copilot).

#### 2. Solution Architect Professional Native App — Team Plan V
- **Mục tiêu & Tầm nhìn:** Trợ lý AI Native dành riêng cho Solution Architect giúp tự động hóa toàn bộ quy trình thiết kế hệ thống.
- **Bài toán giải quyết:** Loại bỏ việc đọc tài liệu BRD/PRD thủ công, vẽ sơ đồ từ trang giấy trắng hay tính toán chi phí đám mô hình đoán mò.
- **Công nghệ cốt lõi & Workflow:**
  - *Kiến trúc:* Amazon Bedrock, Knowledge Base (RAG), Draw.io MCP, AWS Pricing MCP, ECS Fargate, PostgreSQL, CloudFront, Cognito.
  - *Tính năng chính:* Trích xuất yêu cầu từ tài liệu, tạo sơ đồ kiến trúc Draw.io/AWS editable, phát sinh mã Infrastructure as Code (IaC - Terraform) và ước tính chi phí AWS tự động theo khu vực.

#### 3. Signal Scout — Team Signal Scout
- **Mục tiêu & Tầm nhìn:** Nền tảng AI Agent thu thập và kết nối các tín hiệu thay đổi chiến lược, tái cấu trúc hoặc biến động tài chính của doanh nghiệp.
- **Bài toán giải quyết:** Giúp các đội ngũ chiến lược và quản trị rủi ro phát hiện sớm các thay đổi lớn của đối thủ/đối tác dựa trên minh chứng xác thực.
- **Công nghệ cốt lõi:**
  - *Multi-Agent Architecture:* Cấu trúc Crawler Subagent và Analysis Subagent chạy trên AgentCore Runtime kết hợp Bedrock Guardrails, Langfuse, Apify và TinyFish.
  - *Giao diện & Output:* Dashboard hiển thị tiến trình sự kiện (timeline), số liệu tài chính minh bạch có trích dẫn nguồn (cited evidence).

---

### Kết quả đạt được

#### Bài Học Từ Hành Trình Hackathon
- **Tư duy "Done is better than perfect":** Thà hoàn thiện một tính năng nhỏ nhưng chạy mượt mà (Scope it tiny) còn hơn triển khai một ý tưởng đồ xộ nhưng bị lỗi.
- **Giá trị của sự chuẩn bị:** Chuẩn bị sẵn bộ công cụ (starter templates), phân chia vai trò rõ ràng (code, design, pitch) và luyện tập bài thuyết trình 3 phút từ sớm giúp làm chủ thời gian.
- **Tư duy đòn bẩy công nghệ:** Nắm vững cách phối hợp giữa các mô hình Generative AI / Agentic AI với hạ tầng đám mây AWS để giải quyết trọn vẹn một bài toán từ End-to-End.

#### Kỹ Năng Kỹ Thuật & Vận Hành
- **Làm chủ hạ tầng AI trên AWS:** Hiểu sâu hơn về việc triển khai AWS Bedrock, SageMaker Endpoints, ECS Fargate, Serverless Backend (Lambda, API Gateway) và tích hợp các công cụ MCP (Model Context Protocol).
- **Giải quyết sự cố thực tế (Troubleshooting):** Kỹ năng quản lý repo GitHub (tránh push lầm file `.env`), xử lý xung đột code khi làm việc nhóm đêm muộn và tối ưu độ trễ xử lý dữ liệu.

---

### Ứng Dụng Vào Công Việc & Định Hướng

- **Xây dựng giải pháp AI có tính thực thi:** Áp dụng mô hình Agentic AI (vừa phân tích vừa tự động đưa ra hành động/đề xuất) vào các dự án cá nhân và đồ án tốt nghiệp.
- **Tối ưu hóa quy trình thiết kế Cloud:** Áp dụng tư duy tự động hóa IaC (Terraform) và vẽ sơ đồ kiến trúc chuẩn AWS từ bài chia sẻ của dự án SA Native App.
- **Rèn luyện tinh thần làm việc nhóm:** Xây dựng quy trình làm việc nhóm rõ ràng, giao tiếp chủ động và giữ năng lượng tích cực trước các thử thách kỹ thuật lớn.

---

### Trải nghiệm trong event

Sự kiện **“Agentic AI Build Week & Hackathon Journey”** mang đến những cảm xúc và trải nghiệm vô cùng chân thực, gần gũi:

#### Muôn màu không khí Hackathon 24h
- Lắng nghe những câu chuyện "dở khóc dở cười" rất đời thường: thức đêm debug đến 3 giờ sáng, uống liền 5 lon Redbull, ăn KFC cùng đồng đội và cùng nhau vượt qua những lúc code không chạy.
- Cảm nhận rõ sự dịch chuyển cảm xúc từ lo lắng, bối rối (Overwhelmed) sang tập trung cao độ (In the Zone) và vỡ òa tự hào khi demo thành công sản phẩm tự tay làm ra.

#### Học hỏi từ những người đi trước
- Nhận được những lời khuyên chân thành cho lần đầu tham gia Hackathon: "Hãy cứ đăng ký tham gia dù chưa sẵn sàng", "Mọi mối quan hệ và bài học thu được quan trọng hơn giải thưởng".

#### Một số hình ảnh khi tham gia sự kiện
<div style="display: flex; flex-direction: column; gap: 16px;">
  <div style="display: flex; gap: 16px;">
    <img src="/images/4-Events/event3/group-photo.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Ảnh 1">
    <img src="/images/4-Events/event3/2.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Ảnh 2">
  </div>

  <div style="display: flex; justify-content: center;">
    <img src="/images/4-Events/event3/3.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Ảnh 3">
  </div>
</div>

> Tổng kết: Sự kiện không chỉ nạp thêm nhiều kiến thức chuyên sâu về Agentic AI và AWS Cloud mà còn truyền cảm hứng mạnh mẽ về tinh thần dám dấn thân, thử nghiệm và học hỏi từ những trải nghiệm thực chiến.
