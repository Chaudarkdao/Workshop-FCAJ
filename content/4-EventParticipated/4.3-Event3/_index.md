---
title: "Event 3"
date: 2026-07-28
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---

# Report on "Aentic AI Buildwick 2026 - Hackathon Journey"

### Event Objectives

- Create a playground for students and builders to experience building AI products in a short time (24-48 hours)
- Connect the community, learn and develop teamwork skills under pressure
- Promote creativity and application of AI to solve real-world problems

### Featured Teams

#### 1. One Team - 1st Prize AI Track

- **Product:** KFC Chatbot Agent - Ordering via Zalo through natural conversation
- **Technology:** AWS Bedrock Agent, Tiny Fish, Multi-Agent Architecture
- **Achievement:** 1st Prize Aentic AI Buildwick 2026

#### 2. SignalCount - 2nd Prize AI Track

- **Product:** Dream AI - Competitor strategy analysis
- **Technology:** AWS Bedrock, LangField, Tiny Fish, Multi-Agent System

#### 3. Team3

- **Product:** AI Solution Architect - Automatic architecture diagram and IAC deployment
- **Technology:** AWS Bedrock, Claude, Terraform, Diagram Generation

#### 4. 3K Team

- **Product:** SHIELD - Crowd monitoring system using Computer Vision
- **Technology:** YOLOv6, ByteTrack, Amazon Rekognition, AWS Fargate

#### 5. Six Pillers Team

- **Product:** Adaptive Workflow Engine - Money laundering transaction detection and investigation
- **Technology:** AWS Bedrock Agent, Step Functions, XGBoost, OpenSearch

---

### Key Content

#### Opening Speech - Mr. Joseph Marazota (Head of Technology, Asia)

##### Importance of the event

- This is a great opportunity for students to learn and gain practical experience
- AWS invests heavily in young talents, which wasn't available before
- 20 years ago, the previous generation had to learn on their own; now there's a support ecosystem

##### Lessons from career journey

- **Initial concerns:** Worrying about finding a job and integrating with other engineers
- **Different mental models:** Young people want continuous change, while the older generation wants stability
- **From quarterly release to minute release:** Technology changes across generations

##### Opportunities for students

- **New thinking, new approach:** Students bring different perspectives, not bound by old ways
- **Will be smarter, faster:** The younger generation will learn and develop much faster
- **Become future leaders in 2-3 years**, not 20-30 years

##### Robots and AI in the future

- AWS owns over 1 million robots managing fulfillment centers
- Robots without humans are useless - they do what they're programmed to do
- **"You're going to be the human in the loop"** - Humans will decide based on AI suggestions

##### Advice for students

> *"Enter this journey with little concern and a lot of conviction that you will be the ones to innovate, change your industry. Invest in yourself, be a lifelong learner - if you're a lifelong learner, you will inevitably succeed in life and career."*

---

#### One Team - KFC Chatbot Agent (1st Prize)

##### Problem

- McDonald's once tried AI drive-through but failed because AI couldn't understand context
- Users had to switch apps, create accounts, learn menus → creates friction
- Orders were wrong due to AI hallucinations

##### Solution

- **KFC Chatbot Agent:** Natural ordering via Zalo/WhatsApp
- **No app switching, no account creation required**
- **Multi-channel support** - Zalo, WhatsApp

##### Architecture

- **Multi-Agent Architecture:** Supervisor Agent coordinates Sub-Agents
- **Memory Management:** Stores order history for reminders
- **Tiny Fish + Web Scraping:** Gets menu data from KFC website
- **Tool Calling:** Apply vouchers, calculate total, confirm orders

##### Challenges

- **Hallucination Prevention:** Confirm orders before sending to kitchen
- **Speed & Latency:** Stream entire pipeline to reduce response time
- **Cost Optimization:** $0.006/order with total $88/month

##### Demo

- Send messages on Zalo to order KFC
- AI suggests menu, applies vouchers, confirms orders
- Dashboard for staff to manage orders

---

#### SignalCount - Dream AI (2nd Prize)

##### Problem

- Companies need to analyze competitor strategies
- Information is scattered across multiple sources (financial reports, talks, news)
- Manual work takes time and is difficult to synthesize

##### Solution

- **Dream AI:** Synthesize and analyze competitor strategies
- **Competitor Intelligence:** Automatically collect and synthesize scattered information
- **Forecasting:** Predict ROI when applying similar strategies

##### Architecture

- **Multi-Agent Core:** Supervisor + Sub-Agent (Crawler, Analysis)
- **Crawler Sub-Agent:** Uses Tiny Fish or Apify to collect data
- **Analysis Sub-Agent:** Analyzes data with Bedrock + LangField
- **Human-in-the-loop:** End user makes the final decision

##### Cost Analysis

| Usage Level | Cost | Note |
| --- | --- | --- |
| Min | $35/month | Low usage |
| Medium | $94/month | Moderate usage |
| Max | $130/month | Maximum usage |

##### Lessons

- **Business Model Canvas is important:** Clearly define problem, customer, value proposition
- **Technology is just a tool:** Must solve real problems
- **Start with problem, not with tool**

---

#### Team3 - AI Solution Architect

##### Problem

- SA (Solution Architect) needs to draw architecture and calculate costs within 2 days
- Customers may request urgently overnight
- Manual work is time-consuming and hard to ensure quality

##### Solution

- **AI Solution Architect:** Automatically draws architecture from natural language requirements
- **Automatic cost calculation** from the drawn architecture
- **Generate IaC (Terraform/CloudFormation)** and auto-deploy

##### Workflow

1. **Input:** User enters natural language requirements + uploads documents
2. **AI analyzes:** Identifies requirements, business processes, policies
3. **Draw architecture:** Automatically draws on Draw.io with AWS icons
4. **Calculate cost:** Based on services and instance types
5. **Generate IaC:** Creates Terraform/CloudFormation
6. **Deploy:** Auto-deploys to AWS if confirmed

##### Technical Architecture

- **Natural Language Processing:** Understands user requirements
- **Diagram Generation:** Automatically draws architecture with AWS icons
- **Template Validation:** Ensures compliance with enterprise policies
- **Blacklist Services:** Blocks disallowed services
- **Cost Calculator:** Estimates deployment costs

##### Demo

- User enters: *"I need a scalable web system with RDS and S3"*
- AI automatically draws architecture with corresponding services
- Calculates costs and displays Terraform code

---

#### 3K Team - SHIELD

##### Problem

- Congestion at airports, supermarkets, events
- Crowd management with surveillance cameras requires many staff
- Difficult to respond promptly when congestion occurs

##### Solution

- **SHIELD (Small Human Flow Location Respond System):** Automated crowd monitoring system
- **Computer Vision + AI Agent:** Detects and coordinates crowds
- **Real-time Monitoring:** Tracks people density in zones

##### Architecture

- **Camera Input:** Video stream from camera (simulated with phone)
- **YOLOv6 + ByteTrack:** People detection and tracking
- **Zone Management:** Define zones for counting people
- **Amazon Rekognition:** Image recognition
- **AWS Fargate:** Containerized service for video processing
- **Bedrock Agent:** Analyzes and suggests solutions

##### Workflow

1. **Detect:** YOLOv6 detects people in frame
2. **Track:** ByteTrack assigns IDs to each person
3. **Zone Counting:** Counts people in each zone
4. **Analysis:** AI analyzes and provides recommendations
5. **Alert:** Warns when a zone is overcrowded

##### Challenges

- **Network Stability:** Video stream lags, need stable connection
- **Camera Position:** Must position camera appropriately to observe multiple zones
- **Integration:** Integrate AI Agent into the system

##### Lessons

- **Experience > Results:** Code can be learned later, but experience is irreplaceable
- **Right scope:** Don't expand project excessively, know when to stop
- **Teamwork is important:** Fix bugs together, eat KFC together at 3 AM

---

#### Six Pillers Team - AML Solution

##### Problem

- **90-95% false positive rate** in transaction alerts
- Each manual review costs $20-25
- Staff burnout from processing too many cases
- Anti-money laundering regulations are increasingly strict

##### Solution

- **Adaptive Workflow Engine:** Automatically investigates and classifies transactions
- **Reduces time from 3 hours to minutes**
- **Explainable AI:** Each AI decision can be traced

##### Architecture

- **Layer 1 - Fast Detection:** Rapid detection using XGBoost
  - Kinesis Data Stream → Feature Engineering Lambda → Bedrock Endpoint → Rule-based Alert
- **Layer 2 - Deep Investigation:** Deep investigation with Multi-Agent
  - Supervisor Agent → 3 Sub-Agents (KYC, Money Flow, Sanction)
  - Knowledge Base: Legal + Typology in Vector DB
  - Double-check with 2 LLMs to avoid hallucination
- **Layer 3 - Case Management:** Human makes final decision
  - Dashboard + Human Review

##### Enterprise Trust

- **Security:** KMS, IAM, Secret Manager, GuardDuty, Security Hub
- **Monitoring:** CloudWatch, X-Ray, CloudTrail
- **Human-in-the-loop:** End user decides Dismiss/Escalate/Request Info

##### Cost & Performance

- Reasonable operational costs with AWS services
- Scalability: Data Analysts can handle more cases

---

### Lessons Learned

After participating in "Aentic AI Buildwick 2026", I gained many valuable lessons from the teams' journeys:

#### 1. Importance of identifying the problem

- **Start with problem, not with technology:** Successful teams all started by clearly identifying the problem to solve
- **Clear pain point:** KFC bot solves ordering friction, AML bot solves false positive rate
- **Business model canvas:** Identify customer, value proposition, and distribution channels

#### 2. Architecture and technology

- **Multi-Agent Architecture:** Most teams used Supervisor + Sub-Agents for optimization and control
- **AWS Native:** Maximize use of AWS services: Bedrock, Lambda, Step Functions, Fargate, Kinesis
- **Memory & Context:** Manage memory so AI remembers transaction/order history
- **Cost Optimization:** Always calculate and optimize costs when designing architecture

#### 3. Project management in hackathons

- **Right scope:** Don't expand excessively, focus on MVP (Minimum Viable Product)
- **Clear division of labor:** Define who does what, avoid conflicts and duplication
- **Sleep and health:** Allocate reasonable rest time
- **Demo plan:** Always prepare demo script and test before presenting

#### 4. Pitching and presentation skills

- **Tell a story:** Start with the problem, explain the solution, then the technical details
- **Prepare for questions:** Judges will ask deep questions about architecture, cost, security
- **Stay calm and confident:** More important than winning is the lessons learned

#### 5. Teamwork and team spirit

- **Lower your ego:** All teams had conflicts but knew how to listen and negotiate
- **Complementary skills:** Team needs both technical (AI, Backend, Frontend) and business (pitching, business model)
- **Networking:** Connect with other builders, build network in the community

#### 6. Using AI effectively

- **AI is a tool, not a replacement:** Humans are always the final decision maker
- **Hallucination Prevention:** Always have mechanisms to check and verify AI output
- **Explainability:** Must be able to trace each AI decision for audit
- **Human-in-the-loop:** Never let AI operate fully autonomously

### Conclusion

Aentic AI Buildwick 2026 was an extremely valuable experience for all participating teams. From technical lessons, project management, to teamwork and presentation skills, all contribute to equipping students with the necessary skills for the future job market.

Key success factors:

1. **Start with problem** - Clearly identify the problem and customer pain point
2. **Build MVP** - Focus on the minimum viable product that works
3. **Human-in-the-loop** - Always have humans control final decisions
4. **Learn by doing** - Practical experience is more important than theory
5. **Teamwork** - Effective teamwork is the key to success

> *"Opportunity doesn't discriminate, it belongs to those who want it the most."* - Ms. Nhu Tran

---

### Event Photos

![Overview of Aentic AI Buildwick 2026 event](../../images/event/event3/checkin3.jpg)