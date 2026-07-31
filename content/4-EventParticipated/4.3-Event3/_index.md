---
title: "Event 3"
date: 2026-07-25
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Summary Report: "Agentic AI Build Week & Hackathon Journey"

### Purpose of the Event

- **Practical 24-Hour Hackathon Experience:** Journeying through an intense 24-hour cycle from ideation, building an MVP, encountering failures, to delivering a complete Agentic AI solution on AWS.
- **Exploring Cutting-Edge Agentic AI Technology:** Discovering how to combine real-time Computer Vision, AI Agents (Amazon Bedrock Agents, Strands Agent), and modern Cloud architectures.
- **Solving Real-World Problems:** Analyzing practical AI solutions built by student teams for crowd monitoring, cloud architecture automation, and enterprise risk analysis.
- **Building Product Mindset & Resilience:** Learning how to optimize project scope, navigate tight deadlines, handle sleep deprivation, and overcome unexpected technical hurdles during development.

### Key Featured Projects Presented

#### 1. S.H.E.P.H.E.R.D (Smart Human-flow Evaluation, Prediction, Hazard Detection, Response, and Dispatch) — Team 3KA
- **Goal & Vision:** A real-time system for monitoring, evaluating, and predicting crowd density while automatically suggesting personnel dispatch plans.
- **Problem Solved:** Replaces slow, non-scalable, and error-prone manual monitoring at venue entrances, queues, and event areas.
- **Core Technology Stack:**
  - *Computer Vision:* YOLO + ByteTrack analyzing live camera streams for person counting and density tracking.
  - *AWS & AI Layer:* Kinesis Video Streams, Amazon SageMaker Endpoints, Amazon Bedrock AgentCore + Strands Agent, AWS Lambda, DynamoDB, and React Dashboard.
  - *Agentic Features:* Autonomous early-warning monitoring for congestion (Autonomous Monitor) and an natural-language Q&A interface using live metrics (Operator Copilot).

#### 2. Solution Architect Professional Native App — Team Plan V
- **Goal & Vision:** An AI Native assistant tailored for Solution Architects to automate end-to-end system design workflows.
- **Problem Solved:** Eliminates manual line-by-line reading of BRD/PRD documents, starting diagrams from blank canvases, and guesswork in cloud cost estimation.
- **Core Technology & Workflow:**
  - *Architecture:* Amazon Bedrock, Knowledge Base (RAG), Draw.io MCP, AWS Pricing MCP, ECS Fargate, PostgreSQL, CloudFront, Cognito.
  - *Key Features:* Automated requirements extraction, generating editable Draw.io/AWS architecture diagrams, producing Infrastructure as Code (IaC - Terraform), and calculating region-specific AWS cost estimates.

#### 3. Signal Scout — Team Signal Scout
- **Goal & Vision:** An AI Agent platform that aggregates and connects signals regarding corporate strategy changes, restructurings, or financial fluctuations.
- **Problem Solved:** Assists strategy and risk management teams in detecting major competitor/partner moves early through verifiable evidence.
- **Core Technology:**
  - *Multi-Agent Architecture:* Crawler Subagent and Analysis Subagent running on AgentCore Runtime, combined with Bedrock Guardrails, Langfuse, Apify, and TinyFish.
  - *UI & Output:* An executive dashboard displaying event timelines and transparent financial metrics backed by cited evidence.

---

### Key Takeaways (Results Achieved)

#### Lessons from the Hackathon Journey
- **"Done is Better Than Perfect" Mindset:** Delivering a small, fully functional feature (Scope it tiny) is far better than presenting a grand but broken concept.
- **The Value of Preparation:** Having starter templates ready, assigning clear team roles (coding, design, pitching), and rehearsing the 3-minute story early makes time management smooth.
- **Leveraging Emerging Tech Stack:** Mastering the synergy between Generative/Agentic AI models and AWS cloud infrastructure to deliver end-to-end solutions.

#### Technical & Operational Skills
- **Mastering AI Infrastructure on AWS:** Gaining hands-on experience with AWS Bedrock, SageMaker Endpoints, ECS Fargate, Serverless Backends (Lambda, API Gateway), and MCP (Model Context Protocol) integration.
- **Real-World Troubleshooting:** Handling repository management best practices (avoiding accidental `.env` pushes), resolving late-night code conflicts, and optimizing data processing latency.

---

### Practical Applications & Future Direction

- **Building Actionable AI Solutions:** Applying Agentic AI patterns (combining analysis with automated action recommendations) to personal and capstone projects.
- **Streamlining Cloud Architecture Design:** Adopting automated IaC generation (Terraform) and standardized AWS diagramming practices inspired by the SA Native App project.
- **Fostering Team Collaboration:** Establishing clear team workflows, maintaining proactive communication, and keeping a positive attitude through major technical challenges.

---

### Event Experience

The **“Agentic AI Build Week & Hackathon Journey”** session provided an authentic, relatable, and inspiring experience:

#### The Vibrant Atmosphere of a 24-Hour Hackathon
- Hearing relatable stories: late-night debugging until 3 AM, drinking 5 Red Bulls, sharing KFC meals with teammates, and pushing through code failures together.
- Experiencing the emotional shift from feeling overwhelmed to entering "the zone" and feeling immense pride when successfully demoing a self-built product.

#### Insights from Experienced Builders
- Receiving genuine advice for first-time hackathon participants: "Just sign up even if you don't feel ready," and "The relationships and lessons gained matter far more than the prize."

#### Event Photos
<div style="display: flex; flex-direction: column; gap: 16px;">
  <div style="display: flex; gap: 16px;">
    <img src="/images/4-Events/event3/1.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Photo 1">
    <img src="/images/4-Events/event3/2.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Photo 2">
  </div>

  <div style="display: flex; justify-content: center;">
    <img src="/images/4-Events/event3/3.png"
         style="width: 50%; height: 250px; object-fit: cover;" alt="Photo 3">
  </div>
</div>

> Summary: The event not only enriched my technical knowledge in Agentic AI and AWS Cloud but also served as a powerful inspiration to embrace hands-on building, experimentation, and learning from practical execution.