---
title: "Event 1"
date: 2026-06-13
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Summary Report: "AWS Study Group Community Sharing Session"

### Purpose of the Event

- Share a realistic picture of day-to-day work, career opportunities, and development roadmaps in the fields of Cloud, DevOps, Data Analytics, and AI.
- Introduce standard recruitment processes, core skills, and working cultures at Multinational Corporations (MNCs).
- Analyze real-world system architectures (case study: Scalable URL Shortener) and design principles for highly scalable applications on AWS.
- Introduce the AWS Student Builder Group community along with hands-on learning roadmaps designed specifically for students.

### List of Speakers

- **Mr. Cường Nguyễn** - Process Engineer
- **Mr. Đạt Phạm** - Data Analytics Engineer (Kamereo / Colgate-Palmolive)
- **Mr. Trương Hoàng Trọng** - DevOps Engineer @ Endava Vietnam
- **Mr. Danh Hoàng Hiếu Nghị** - AI Engineer, AWS Community Builder & AWS Student Builder Group Leader
- **Mr. Đinh Trung Kiên** - Lead Developer at Startup
- **Mr. Nguyễn Minh Thọ** - Student

---

### Key Highlights

#### 1. Real-World Data Analytics Work & Culture at Multinational Corporations (MNCs)
- **Actual Work:** Analyzing operational and business metrics (GMV, Fill Rate, Last Mile Cost), designing dashboards to track trends, detecting anomalies, and optimizing production/IoT costs in manufacturing plants.
- **Core Skillset:** Critical thinking, communication skills, problem-solving, and particularly "Data Storytelling."
- **5-Level Growth Model:** Follower → Learner → Problem Solver → System Thinker → Super Star.
- **MNC Recruitment Process:** ATS Screening / Initial Interview → Competency Assessment → Technical Interview (STAR model) → Cultural Fit.
- **Notable Corporate Culture:** *No-Blame Post-Mortem* culture (focusing on finding root causes rather than placing individual blame) and a *Caring & Inclusive* environment.

#### 2. Practical Insights into DevOps Engineering
- **Actual Work:** Far beyond writing CI/CD pipelines or managing Docker/Kubernetes, real-world DevOps involves solving 24/7 operational challenges, handling incidents, troubleshooting, maintaining environments, optimizing Cloud costs, and establishing system ownership.
- **Fundamental Learning Roadmap:** Mastering Linux, Networking, Programming (Python/Golang), Git/CI-CD, Containers, and building practical small-scale projects.
- **Effective DevOps Mindset:** "Tools change, Fundamentals stay" — Focus on System Thinking, automating repetitive tasks, and leveraging AI as an efficiency force multiplier.

#### 3. System Design: Scalable URL Shortener on AWS
- **Drawbacks of Traditional Systems:** Vulnerable to bottlenecks (Single Point of Failure), high read latency, and difficulty in scaling.
- **Optimized AWS Architecture:**
  - *Front-end & Security:* Amazon CloudFront, AWS WAF, Amazon Amplify, Route 53, Cognito.
  - *Key Generation Service (KGS):* Pre-generating short codes and storing them in Amazon ElastiCache (Redis) allows instant URL creation while remaining collision-free.
  - *Backend & Database:* AWS Fargate (ECS Cluster), Amazon DynamoDB, and ElastiCache Redis utilizing the Cache-aside Pattern to minimize latency.
- **Architectural Principles Learned:** Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, and Cache-aside Pattern.

#### 4. The Journey from Student to AWS Partner & AWS Student Builder Group
- **8 Growth Steps:** 
Student Curiosity → First Cloud Journey → Workshop & Community → Hands-on Labs → School Projects → Portfolio → AWS Partner → Share Back.
- **AWS Student Builder Group Community:** Overview of student support programs, benefits including AWS Credits, Swag, AWS certification exam vouchers, and opportunities to attend specialized events (such as AWS Community Day).

---

### Key Takeaways

#### Career Orientation & Mindset
- **Proactive Learning:** Shifting from a passive approach (Follower) toward a problem-solving mindset (Problem Solver) and holistic view (System Thinker).
- **The Value of Fundamentals:** While tech tools evolve constantly, core knowledge (Linux, Networking, Data, System Design) remains the long-term foundation.
- **Leveraging AI Effectively:** Utilizing AI to accelerate productivity rather than relying on it blindly, which stifles critical thinking.

#### Technical & Practical Architecture
- **Designing High-Load Architectures:** Mastering the separation of execution paths (Read/Write path) and pushing security and caching to the network edge (Defense at the Edge).
- **Flexible Cloud Service Integration:** Understanding how to coordinate Compute (Fargate/EC2), Databases (DynamoDB), In-memory Caching (ElastiCache Redis), and Edge Services (CloudFront/WAF).

---

### Practical Applications

- **Applying System Thinking:** Implementing Root Cause Analysis methods when troubleshooting system incidents.
- **Enhancing Data/Reporting Skills:** Practicing data presentation tied directly to business and operational contexts (Data Storytelling).
- **System Design Practice:** Applying architectural patterns like Cache-aside and Async Queues to academic software design projects.
- **Community Engagement:** Joining and actively participating in the AWS Student Builder Group, completing hands-on labs on the First Cloud Journey platform to build practical experience.

---

### Event Experience

The **“AWS Study Group Community Sharing Session”** meetup was an incredibly meaningful event that provided immense practical value through the perspectives of seasoned industry speakers. Key highlights include:

#### Learning from Real Stories
- Listening to candid discussions about working in MNC environments, which dispelled common misconceptions about the roles of Data Analytics Engineers and DevOps Engineers.
- Learning about the *No-Blame Culture* — an essential cultural insight for teamwork and incident response.

#### In-Depth Architectural Analysis
- Impressed by the URL Shortener case study, which clearly demonstrated the flaws of a naive model and guided the step-by-step evolution to a high-concurrency Cloud architecture.

#### Expanding Professional Networks
- Interacting directly with speakers, senior engineers, and peers with shared interests, leading to a clearer understanding of AWS student support initiatives.

#### Event Photos
<div style="display: flex; gap: 20px;">
  <img src="/images/4-Events/event1/1.png" alt="Sự kiện 1" style="width: 50%; height: 300px; object-fit: cover;">
  <img src="/images/4-Events/event1/2.png" alt="Sự kiện 2" style="width: 50%; height: 300px; object-fit: cover;">
</div>

> Summary: The event served as a strong source of motivation, providing clear career guidance and delivering actionable technical and soft skill lessons for my future growth.