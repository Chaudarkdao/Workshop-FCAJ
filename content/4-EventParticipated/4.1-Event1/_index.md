---
title: "Event 1"
date: 2026-07-28
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Report on "AWS First Cloud AI Journey Community Day"

### Event Objectives

- New perspectives on the AI wave shaping the future of enterprises
- AI applications in business

### Speaker List

- **Steve Tran** - CTO/Founder CloudThinker
- **Mr. Trung** - CEO Revve AI
- **Ms. Bao & Mr. Nguyen** - Cloud Kinetics
- **Mr. Truong & Ms. Minh Anh** - Noventis
- **Mr. Nghi & Mr. Toan** - Renova Cloud & AWS Security Builder

### Key Content

#### Cloud Agent (Mr. Steve Tran - Cloud Thinker)

##### Problems Cloud Thinker solves:

- Traditional server operations consume human resources, costs, and time
- When businesses move to the cloud, complexity increases, creating "technical debt"
- Need AI to support cloud infrastructure operations, especially in critical sectors (banking, finance)

##### Cloud Thinker provides AI Agent solving 4 key problems:

- **Incident Response:** AI investigates incidents many times faster (in minutes instead of hours)
- **Code Review:** Automatically reviews infrastructure code changes before production deployment
- **Cost Optimization:** AI automatically optimizes cloud costs (reduces 100% of manual operations)
- **Security Testing:** Automated penetration testing, detects security vulnerabilities

##### Agent Architecture

Cloud Thinker uses Multi-Agent Architecture instead of Single Agent because:

- Cost optimization (using smaller models for simple tasks)
- Better context control
- Easier role-based access control management

##### Advice for students

- Cloud and AI are changing the job market. Experience the enterprise environment early. AI will not completely replace humans but will support them. However, there will be a need for truly skilled people who know how to use AI effectively.

#### Voice AI Agent (Mr. Trung - CEO Revve AI)

##### Basic Voice AI Structure

- Speech-to-Speech architecture: receives audio → processes → returns audio (common in English)
- 3-component architecture (used for Vietnamese): Speech → Text → LLM processing → Text → TTS (Text-to-Speech)

##### Why use 3-component architecture for Vietnamese

- Speech-to-Speech doesn't support Vietnamese well yet (low-resource language)
- LLM processing Vietnamese text is already very good
- Easy content control and tool calling
- Easy security and audit

##### Challenges when deploying Voice Agent for banks (VVBank, VPBank)

- **Speed**: Stream the entire pipeline to reduce latency
- **Gender**: Detect speaker's gender for proper address (anh/chị)
- **Interruption**: Handle when customers interrupt or pause mid-sentence
- **Regional accents**: Model trained with 10-20% regional accent data
- **Tool Calling**: Perform real tasks (block cards, inquiries, etc.)
- **Fallback to Human**: Transfer to staff when AI cannot handle

#### DevOps Agent (Ms. Bao & Mr. Nguyen - Cloud Kinetics)

##### Current issues for DevOps Engineers:

- **Fragmented Telemetry**: Logs and traces scattered across multiple locations (CloudWatch, Splunk, etc.)
- **Knowledge Gap**: Each log/trace belongs to different teams, different domains
- **Context Loss**: Difficulty linking information to find root cause

##### DevOps Agent (AWS DevOps Guru) solves with 6 pillars:

- **Context Learning**: Learns entire infrastructure topology through Agent Space
- **Control**: Granular permissions based on tags/resources
- **Integration**: Connects via MCP to expand capabilities
- **Collaboration**: Chat interface, integrates with Slack/ServiceNow
- **Cost Effective**: Billed by runtime ($0.083/second)

##### 4-step operational process:

- **Classification & Extraction**: Aggregates logs/traces when triggered (alert or chat)
- **Investigation**: Generates hypotheses and proves/rejects them to find root cause
- **Mitigation**: Proposes remediation plans (not automatically executed)
- **Improvement**: Proposes long-term system improvements

#### AI & HR (Mr. Truong & Ms. Minh Anh - Noventis)

##### HR challenges in the AI era:

- Manual CV screening → missing talent
- Subjective evaluation, lack of standardized data
- Security risks when uploading data to public AI
- Time-to-hire extended 1-2 months
- Difficulty retaining good employees

##### Amazon Q (Quick) - Solution:

- **Chat Agent**: Custom agent for each business function (recruitment, policy, sales)
- **Research**: Synthesizes information from web + internal documents, exports reports
- **Quick BI**: Automatically analyzes data, visualizes
- **Flow & Automate**: Automates repetitive admin tasks
- **Diverse data connections**: SharePoint, Outlook, OneDrive, Gmail, Google Drive, Jira, Salesforce, GitHub, S3, database,...

##### HR Talent Review Demo:

1. Create JD (Job Description) for Junior Cloud Engineer in just a few commands
2. Review 6 CVs, automatically score based on criteria set (technical 40%, problem-solving 25%, communication 15%, etc.)
3. Classify: Strong/Good/Low/Very Low
4. Export visual HTML report with comparison benchmark
5. Automatically suggest expected salary

- **Results**: Reduced hiring time, cost savings, improved employee quality.

#### Security & MCP Server (Mr. Nghi & Mr. Toan - Renova Cloud & AWS Security Builder)

##### Problem:

Amazon Q (on the internet) needs to connect to MCP Server containing internal data. Connecting via public internet poses security risks (DDoS, Man-in-the-Middle, data leakage).

##### Solution:

Use VPC Connection to connect Amazon Q with MCP Server in Private Subnet

##### Architecture:

Amazon Q → VPC Connection → Interface Endpoint → ALB (HTTPS) → MCP Server (EC2)

##### Security components:

- VPC Endpoint (Interface Endpoint): Private connection, not via internet
- Private DNS: Only accessible within VPC
- ALB with TLS (encryption) and ACM certificate
- Route 53 Resolver: Internal DNS to query MCP Server
- Cognito: Authentication for users

### Lessons Learned

After participating in the "GenAI-powered App-DB Modernization workshop", I gained many valuable lessons about AI applications in business as well as personal development directions:

#### 1. AI is changing how businesses operate

- **Intelligent Automation**: AI not only automates repetitive tasks but also has the ability to analyze, make decisions, and solve complex problems across multiple fields from cloud operations, HR to finance.
- **Cost and Time Optimization**: AI solutions like Cloud Agent, DevOps Agent have demonstrated significant reduction in incident handling time (from hours to minutes) and manual operations (up to 100%).
- **Improved Work Quality**: AI helps humans make more accurate decisions based on data, for example in HR Talent Review helping to evaluate candidates objectively and effectively.

#### 2. AI architecture and deployment need careful design

- **Multi-Agent vs Single Agent**: Using Multi-Agent Architecture (like Cloud Thinker) helps optimize costs, better context control, and easier permission management.
- **Suitable for local language and culture**: For Vietnamese, the 3-component architecture (Speech → Text → LLM → Text → TTS) is more effective than Speech-to-Speech because LLM's Vietnamese text processing capability is already very good.
- **Security is key**: When deploying AI in enterprises, secure connections between systems (VPC Connection, Private Subnet, TLS encryption) are extremely important to protect internal data.

#### 3. Challenges when deploying AI in practice

- **Handling complex situations**: Voice Agent for banks faces many challenges such as processing speed, interruptions, regional accents, and tool calling.
- **Integration with existing systems**: DevOps Agent must process data from multiple sources (CloudWatch, Splunk, etc.) and link information to find root cause.
- **Fallback to Human**: Current AI cannot handle 100% of situations, requiring a mechanism to transfer to staff when necessary.

#### 4. Future of the job market

- **AI will not completely replace humans**: AI will be a powerful supporting tool, but there will still be a need for truly skilled people who know how to use AI effectively.
- **Cloud and AI are changing the job market**: Students need to experience the enterprise environment early, access and become familiar with AI technologies to avoid falling behind.
- **Need to develop new skills**: Besides professional knowledge, need to equip skills to work with AI, understand prompt engineering, and the ability to integrate AI into workflows.

#### 5. Personal development direction

- **Real-world experience**: Participate in workshops and events to learn from experts and understand AI applications in business.
- **Access new technologies**: Learn about AWS AI services (SageMaker, Bedrock, Q), Agent-building frameworks (LangChain, CrewAI), and how to integrate AI into real applications.
- **Build problem-solving mindset**: Instead of just learning theory, apply AI to solve real problems, from simple to complex.

### Conclusion

The event provided a comprehensive and in-depth view of how AI is shaping the future of enterprises. From Cloud Agent, Voice AI, DevOps Agent, AI in HR to Security & MCP Server, all demonstrate the enormous potential of AI in optimizing operations, improving efficiency, and creating new value. This is the golden time for us students to equip knowledge and skills about AI to be ready for the future job market.

### Event Photos
![Overview of AWS First Cloud AI Journey Community Day](../../images/event/event1/checkin1.jpg)
