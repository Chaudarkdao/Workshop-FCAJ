---
title: "Event 3"
date: 2026-07-28
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---

# Bài thu hoạch "Aentic AI Buildwick 2026 - Hackathon Journey"

### Mục Đích Của Sự Kiện

- Tạo sân chơi cho sinh viên và các builder trải nghiệm xây dựng sản phẩm AI trong thời gian ngắn (24-48 giờ)
- Kết nối cộng đồng, học hỏi và phát triển kỹ năng làm việc nhóm dưới áp lực
- Thúc đẩy tinh thần sáng tạo và ứng dụng AI vào giải quyết các bài toán thực tế

### Các Đội Thi Tiêu Biểu

#### 1. One Team - Giải Nhất Track AI

- **Sản phẩm:** KFC Chatbot Agent - Đặt hàng qua Zalo bằng hội thoại tự nhiên
- **Công nghệ:** AWS Bedrock Agent, Tiny Fish, Multi-Agent Architecture
- **Thành tích:** Giải Nhất Aentic AI Buildwick 2026

#### 2. SignalCount - Giải Nhì Track AI

- **Sản phẩm:** Dream AI - Phân tích chiến lược đối thủ cạnh tranh
- **Công nghệ:** AWS Bedrock, LangField, Tiny Fish, Multi-Agent System

#### 3. Team3 

- **Sản phẩm:** AI Solution Architect - Tự động vẽ kiến trúc và deploy IAC
- **Công nghệ:** AWS Bedrock, Claude, Terraform, Diagram Generation

#### 4. 3K Team 

- **Sản phẩm:** SHIELD - Hệ thống giám sát đám đông bằng Computer Vision
- **Công nghệ:** YOLOv6, ByteTrack, Amazon Rekognition, AWS Fargate

#### 5. Six Pillers Team 

- **Sản phẩm:** Adaptive Workflow Engine - Phát hiện và điều tra giao dịch rửa tiền
- **Công nghệ:** AWS Bedrock Agent, Step Functions, XGBoost, OpenSearch


---

### Nội Dung Nổi Bật

#### Phát Biểu Khai Mạc - Mr. Joseph Marazota (Head of Technology, Asia)

##### Tầm quan trọng của sự kiện

- Đây là cơ hội lớn để sinh viên học hỏi và trải nghiệm thực tế
- AWS đầu tư mạnh mẽ vào các tài năng trẻ, điều mà trước đây không có
- 20 năm trước, thế hệ đi trước phải tự học; bây giờ có hệ sinh thái hỗ trợ

##### Bài học từ hành trình sự nghiệp

- **Trăn trở ban đầu:** Lo lắng về việc tìm việc làm và hòa nhập với các kỹ sư khác
- **Mental model khác biệt:** Người trẻ muốn thay đổi liên tục, trong khi thế hệ trước chỉ muốn giữ ổn định
- **Từ quarterly release đến minute release:** Sự thay đổi công nghệ qua các thế hệ

##### Cơ hội cho sinh viên

- **Tư duy mới, cách tiếp cận mới:** Sinh viên mang đến góc nhìn khác, không bị ràng buộc bởi cách làm cũ
- **Sẽ thông minh hơn, nhanh hơn:** Thế hệ trẻ sẽ học hỏi và phát triển nhanh hơn rất nhiều
- **Trở thành lãnh đạo tương lai trong 2-3 năm tới**, không phải 20-30 năm

##### Robot và AI trong tương lai

- AWS sở hữu hơn 1 triệu robot quản lý trung tâm fulfillment
- Robot không có con người là vô dụng - chúng làm những gì được lập trình
- **"You're going to be the human in the loop"** - Con người sẽ quyết định dựa trên gợi ý từ AI

##### Lời khuyên cho sinh viên

> *"Hãy tham gia hành trình này với ít lo lắng và nhiều niềm tin rằng bạn sẽ là người đổi mới, thay đổi ngành công nghiệp của mình. Hãy đầu tư vào bản thân, là người học tập suốt đời - nếu bạn là người học suốt đời, bạn sẽ thành công trong cuộc sống và sự nghiệp."*

---

#### One Team - KFC Chatbot Agent (Giải Nhất)

##### Vấn đề

- McDonald's từng thử AI drive-through nhưng thất bại vì AI không hiểu ngữ cảnh
- Người dùng phải chuyển đổi app, tạo tài khoản, học menu → tạo friction
- Các đơn hàng bị sai do AI bị ảo giác (hallucination)

##### Giải pháp

- **KFC Chatbot Agent:** Đặt hàng tự nhiên qua Zalo/WhatsApp
- **Không cần chuyển app, không cần tạo tài khoản**
- **Hỗ trợ đa kênh (Multi-channel)** - Zalo, WhatsApp

##### Kiến trúc

- **Multi-Agent Architecture:** Supervisor Agent điều phối các Sub-Agent
- **Memory Management:** Lưu lịch sử đặt hàng để gợi nhớ
- **Tiny Fish + Web Scraping:** Lấy dữ liệu menu từ website KFC
- **Tool Calling:** Áp dụng voucher, tính tiền, xác nhận đơn hàng

##### Thách thức

- **Hallucination Prevention:** Xác nhận đơn hàng trước khi gửi bếp
- **Speed & Latency:** Stream toàn bộ pipeline để giảm thời gian phản hồi
- **Cost Optimization:** $0.006/order với tổng $88/tháng

##### Demo

- Nhắn tin trên Zalo để đặt KFC
- AI gợi ý menu, áp dụng voucher, xác nhận đơn hàng
- Dashboard cho nhân viên quản lý đơn hàng

---


#### SignalCount - Dream AI (Giải Nhì)

##### Vấn đề

- Các công ty cần phân tích chiến lược đối thủ cạnh tranh
- Thông tin rời rạc, nằm ở nhiều nguồn khác nhau (báo cáo tài chính, tọa đàm, tin tức)
- Thủ công mất thời gian và khó tổng hợp

##### Giải pháp

- **Dream AI:** Tổng hợp và phân tích chiến lược đối thủ
- **Competitor Intelligence:** Tự động thu thập và tổng hợp thông tin rời rạc
- **Forecasting:** Dự đoán ROI khi áp dụng chiến lược tương tự

##### Kiến trúc

- **Multi-Agent Core:** Supervisor + Sub-Agent (Crawler, Analysis)
- **Crawler Sub-Agent:** Sử dụng Tiny Fish hoặc Apify để thu thập dữ liệu
- **Analysis Sub-Agent:** Phân tích dữ liệu với Bedrock + LangField
- **Human-in-the-loop:** Người dùng cuối cùng quyết định

##### Cost Analysis

| Mức sử dụng | Chi phí | Ghi chú |
| --- | --- | --- |
| Min | $35/tháng | Sử dụng thấp |
| Medium | $94/tháng | Sử dụng vừa phải |
| Max | $130/tháng | Sử dụng tối đa |

##### Bài học

- **Business Model Canvas quan trọng:** Xác định rõ problem, customer, value proposition
- **Công nghệ chỉ là công cụ:** Phải giải quyết được vấn đề thực tế
- **Bắt đầu với problem, không bắt đầu với tool**

---


#### Team3 - AI Solution Architect

##### Vấn đề

- SA (Solution Architect) cần vẽ kiến trúc và tính chi phí trong 2 ngày
- Khách hàng có thể yêu cầu gấp trong một đêm
- Làm thủ công mất thời gian và khó đảm bảo chất lượng

##### Giải pháp

- **AI Solution Architect:** Tự động vẽ kiến trúc từ yêu cầu tự nhiên
- **Tính chi phí tự động** từ kiến trúc đã vẽ
- **Generate IaC (Terraform/CloudFormation)** và deploy tự động

##### Luồng hoạt động

1. **Input:** Người dùng nhập yêu cầu bằng ngôn ngữ tự nhiên + upload tài liệu
2. **AI phân tích:** Xác định requirement, business process, policy
3. **Vẽ kiến trúc:** Tự động vẽ trên Draw.io với icon AWS
4. **Tính chi phí:** Dựa trên service và instance type
5. **Generate IaC:** Tạo Terraform/CloudFormation
6. **Deploy:** Tự động deploy lên AWS nếu được xác nhận

##### Kiến trúc kỹ thuật

- **Natural Language Processing:** Hiểu yêu cầu từ người dùng
- **Diagram Generation:** Tự động vẽ kiến trúc với AWS icons
- **Template Validation:** Đảm bảo tuân thủ policy của doanh nghiệp
- **Blacklist Services:** Chặn các service không được phép sử dụng
- **Cost Calculator:** Ước tính chi phí deployment

##### Demo

- Người dùng nhập: *"Tôi cần một hệ thống web scalable với RDS và S3"*
- AI vẽ kiến trúc tự động với các service tương ứng
- Tính chi phí và hiển thị Terraform code

---

#### 3K Team - SHIELD (Giải Khuyến Khích)

##### Vấn đề

- Tắc nghẽn tại sân bay, siêu thị, sự kiện
- Quản lý đám đông bằng camera giám sát cần nhiều nhân sự
- Khó phản ứng kịp thời khi có ách tắc

##### Giải pháp

- **SHIELD (Small Human Flow Location Respond System):** Hệ thống giám sát đám đông tự động
- **Computer Vision + AI Agent:** Phát hiện và điều phối đám đông
- **Real-time Monitoring:** Theo dõi mật độ người tại các zone

##### Kiến trúc

- **Camera Input:** Video stream từ camera (giả lập bằng điện thoại)
- **YOLOv6 + ByteTrack:** Phát hiện và tracking người
- **Zone Management:** Xác định zone để đếm người
- **Amazon Rekognition:** Nhận diện hình ảnh
- **AWS Fargate:** Containerized service cho xử lý video
- **Bedrock Agent:** Phân tích và đề xuất giải pháp

##### Quy trình hoạt động

1. **Detect:** YOLOv6 phát hiện người trong frame
2. **Track:** ByteTrack gắn ID cho từng người
3. **Zone Counting:** Đếm số lượng trong từng zone
4. **Analysis:** AI phân tích và đưa ra đề xuất
5. **Alert:** Cảnh báo khi zone quá đông

##### Thử thách

- **Network Stability:** Video stream bị lag, cần connection ổn định
- **Camera Position:** Phải đặt camera phù hợp để quan sát nhiều zone
- **Integration:** Tích hợp AI Agent vào hệ thống

##### Bài học

- **Trải nghiệm > Kết quả:** Code có thể học sau, nhưng trải nghiệm không thể thay thế
- **Scope vừa đủ:** Đừng mở rộng project quá mức, biết điểm dừng
- **Teamwork quan trọng:** Cùng nhau sửa lỗi, cùng nhau ăn KFC lúc 3h sáng

---


#### Six Pillers Team - AML Solution (Giải Khuyến Khích)

##### Vấn đề

- **90-95% false positive rate** trong các cảnh báo giao dịch
- Mỗi lần review thủ công tốn 20-25 USD
- Nhân viên bị burnout vì xử lý quá nhiều case
- Quy định chống rửa tiền ngày càng siết chặt

##### Giải pháp

- **Adaptive Workflow Engine:** Tự động điều tra và phân loại giao dịch
- **Giảm thời gian từ 3 giờ xuống còn vài phút**
- **Explainable AI:** Trace được từng quyết định của AI

##### Kiến trúc

- **Layer 1 - Fast Detection:** Phát hiện nhanh bằng XGBoost
  - Kinesis Data Stream → Feature Engineering Lambda → Bedrock Endpoint → Rule-based Alert
- **Layer 2 - Deep Investigation:** Điều tra sâu bằng Multi-Agent
  - Supervisor Agent → 3 Sub-Agent (KYC, Money Flow, Sanction)
  - Knowledge Base: Legal + Typology trong Vector DB
  - Double-check với 2 LLM để tránh hallucination
- **Layer 3 - Case Management:** Con người quyết định cuối cùng
  - Dashboard + Human Review

##### Enterprise Trust

- **Security:** KMS, IAM, Secret Manager, GuardDuty, Security Hub
- **Monitoring:** CloudWatch, X-Ray, CloudTrail
- **Human-in-the-loop:** Người dùng cuối quyết định Dis/Escalate/Request Info

##### Cost & Performance

- Chi phí vận hành hợp lý với AWS service
- Scalability: Data Analyst có thể xử lý nhiều case hơn

---

### Bài Học Rút Ra

Sau khi tham gia sự kiện "Aentic AI Buildwick 2026", tôi đã rút ra được nhiều bài học quý giá từ hành trình của các đội thi:

#### 1. Tầm quan trọng của việc xác định vấn đề

- **Start with problem, not with technology:** Các đội thi thành công đều bắt đầu từ việc xác định rõ vấn đề cần giải quyết
- **Pain point rõ ràng:** KFC bot giải quyết friction khi đặt hàng, AML bot giải quyết false positive rate
- **Business model canvas:** Xác định customer, value proposition và kênh phân phối

#### 2. Kiến trúc và công nghệ

- **Multi-Agent Architecture:** Hầu hết các đội đều sử dụng Supervisor + Sub-Agents để tối ưu và kiểm soát
- **AWS Native:** Tận dụng tối đa các service AWS: Bedrock, Lambda, Step Functions, Fargate, Kinesis
- **Memory & Context:** Quản lý memory để AI nhớ lịch sử giao dịch/đặt hàng
- **Cost Optimization:** Luôn tính toán và tối ưu chi phí khi thiết kế kiến trúc

#### 3. Quản lý dự án trong hackathon

- **Scope vừa đủ:** Đừng mở rộng quá mức, tập trung MVP (Minimum Viable Product)
- **Phân công rõ ràng:** Xác định ai làm gì, tránh conflict và trùng lặp
- **Giấc ngủ và sức khỏe:** Phân bổ thời gian nghỉ ngơi hợp lý
- **Demo plan:** Luôn chuẩn bị kịch bản demo và test trước khi trình bày

#### 4. Kỹ năng pitching và thuyết trình

- **Kể câu chuyện:** Bắt đầu từ vấn đề, giải thích giải pháp, sau đó là technical
- **Chuẩn bị cho câu hỏi:** Giám khảo sẽ hỏi sâu về architecture, cost, security
- **Bình tĩnh và tự tin:** Quan trọng hơn việc có giải hay không là bài học rút ra

#### 5. Teamwork và tinh thần đồng đội

- **Hạ cái tôi:** Các đội đều có conflict nhưng biết lắng nghe và thương lượng
- **Bổ sung kỹ năng:** Team cần có đủ technical (AI, Backend, Frontend) và business (pitching, business model)
- **Networking:** Kết nối với các builder khác, xây dựng network trong cộng đồng

#### 6. Sử dụng AI hiệu quả

- **AI là công cụ, không thay thế:** Con người luôn là decision maker cuối cùng
- **Hallucination Prevention:** Luôn có cơ chế kiểm tra và xác nhận output của AI
- **Explainability:** Phải trace được từng quyết định của AI để audit
- **Human-in-the-loop:** Không bao giờ để AI tự động hoàn toàn

### Kết luận

Aentic AI Buildwick 2026 là một trải nghiệm vô cùng quý giá cho tất cả các đội thi tham gia. Từ những bài học về kỹ thuật, quản lý dự án, đến kỹ năng làm việc nhóm và thuyết trình, tất cả đều góp phần trang bị cho sinh viên những kỹ năng cần thiết cho thị trường lao động tương lai.

Những điểm mấu chốt để thành công:

1. **Start with problem** - Xác định rõ vấn đề và pain point của khách hàng
2. **Build MVP** - Tập trung vào sản phẩm tối thiểu có thể hoạt động
3. **Human-in-the-loop** - Luôn có con người kiểm soát quyết định cuối cùng
4. **Learn by doing** - Trải nghiệm thực tế quan trọng hơn lý thuyết
5. **Teamwork** - Làm việc nhóm hiệu quả là chìa khóa thành công

> *"Opportunity doesn't discriminate, it belongs to those who want it the most."* - Ms. Nhu Tran
---

### Hình Ảnh Sự Kiện

![Toàn cảnh sự kiện Aentic AI Buildwick 2026](images/event/event3/checkin3.jpg)



