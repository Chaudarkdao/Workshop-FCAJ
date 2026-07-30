---
title: "Event 1"
date: 2026-07-28
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch "AWS First Cloud AI Journey Community Day"

### Mục Đích Của Sự Kiện

- Những góc nhìn mới về làn sóng AI định hình tương lai doanh nghiệp
- Ứng dụng AI trong doanh nghiệp

### Danh Sách Diễn Giả

- **Steve Tran** - CTO/Founder CloudThinker
- **Anh Trung** - CEO Revve AI
- **Chị Bảo & Anh Nguyên** - Cloud Kinetics
- **Anh Trường & Chị Minh Anh** - Noventis
- **Anh Nghị & Anh Toàn** - Renova Cloud & AWS Security Builder

### Nội Dung Nổi Bật

#### Cloud Agent (Anh Steve Trần - Cloud Thinker)

##### Bài toán Cloud Thinker giải quyết:

- Vận hành server truyền thống tốn sức người, chi phí và thời gian
- Khi doanh nghiệp chuyển lên cloud, độ phức tạp tăng lên, phát sinh "món nợ công nghệ"
- Cần AI hỗ trợ vận hành cloud infrastructure, đặc biệt trong các lĩnh vực quan trọng (ngân hàng, tài chính)

##### Cloud Thinker cung cấp AI Agent giải quyết 4 bài toán chính:

- **Incident Response:** AI điều tra sự cố nhanh gấp nhiều lần (tính bằng phút thay vì giờ)
- **Code Review:** Tự động review thay đổi code hạ tầng trước khi lên production
- **Cost Optimization:** AI tự động tối ưu chi phí cloud (giảm 100% thao tác thủ công)
- **Security Testing:** Pen-testing tự động, phát hiện lỗ hổng bảo mật

##### Kiến trúc Agent

Cloud Thinker sử dụng Multi-Agent Architecture thay vì Single Agent, vì:

- Tối ưu chi phí (dùng model nhỏ cho tác vụ đơn giản)
- Kiểm soát context tốt hơn
- Dễ quản lý phân quyền (role-based access control)

##### Lời khuyên cho sinh viên

- Cloud và AI đang thay đổi thị trường việc làm. Hãy trải nghiệm môi trường doanh nghiệp sớm. AI sẽ không thay thế hoàn toàn mà sẽ hỗ trợ, nhưng sẽ cần những người thực sự giỏi và biết dùng AI hiệu quả.

#### Voice AI Agent (Anh Trung - CEO Revve AI)

##### Cấu trúc Voice AI cơ bản

- Kiến trúc Speech-to-Speech: nhận âm thanh → xử lý → trả về âm thanh (phổ biến ở tiếng Anh)
- Kiến trúc 3 thành phần (dùng cho tiếng Việt): Speech → Text → LLM xử lý → Text → TTS (Text-to-Speech)

##### Tại sao dùng kiến trúc 3 thành phần cho tiếng Việt

- Speech-to-Speech chưa hỗ trợ tốt tiếng Việt (low-resource language)
- LLM xử lý text tiếng Việt đã rất tốt
- Dễ dàng kiểm soát nội dung và tool calling
- Dễ dàng bảo mật và audit

##### Các thách thức khi triển khai Voice Agent cho ngân hàng (VVBank, VPBank)

- **Tốc độ**: Stream toàn bộ pipeline để giảm latency
- **Giới tính**: Detect giới tính người nói để xưng hô đúng (anh/chị)
- **Ngắt lời (Interruption)**: Xử lý khi khách hàng ngắt lời hoặc dừng giữa chừng
- **Accent vùng miền**: Model được train với 10-20% dữ liệu giọng vùng miền
- **Tool Calling**: Thực hiện tác vụ thực tế (khóa thẻ, tra cứu, v.v.)
- **Fallback to Human**: Chuyển sang nhân viên khi AI không handle được

#### DevOps Agent (Chị Bảo & Anh Nguyên - Cloud Kinetics)

##### Vấn đề hiện tại của DevOps Engineer:

- **Fragmented Telemetry**: Log và trace nằm rải rác nhiều nơi (CloudWatch, Splunk, v.v.)
- **Knowledge Gap**: Mỗi log/trace thuộc về team khác nhau, domain khác nhau
- **Context Loss**: Khó liên kết các thông tin để tìm ra root cause

##### DevOps Agent (AWS DevOps Guru) giải quyết bằng 6 trụ cột:

- **Context Learning**: Học topology toàn bộ infrastructure qua Agent Space
- **Control**: Phân quyền chi tiết dựa trên tag/resource
- **Integration**: Kết nối qua MCP để mở rộng khả năng
- **Collaboration**: Giao diện chat, tích hợp Slack/ServiceNow
- **Cost Effective**: Tính phí theo thời gian chạy ($0.083/giây)

##### Quy trình hoạt động 4 bước:

- **Phân loại & Trích xuất**: Tổng hợp log/trace khi có trigger (alert hoặc chat)
- **Điều tra**: Đưa ra giả thuyết và chứng minh/loại bỏ để tìm root cause
- **Mitigation**: Đề xuất phương án khắc phục (không tự động thực thi)
- **Improvement**: Đề xuất cải thiện hệ thống dài hạn

#### AI & HR (Anh Trường & Chị Minh Anh - Noventis)

##### Thách thức của HR trong kỷ nguyên AI:

- Sàng lọc CV thủ công → bỏ lỡ talent
- Đánh giá dựa trên cảm tính, thiếu dữ liệu chuẩn
- Rủi ro bảo mật khi đưa dữ liệu lên AI public
- Time-to-hire kéo dài 1-2 tháng
- Khó giữ chân nhân sự giỏi

##### Amazon Q (Quick) - Giải pháp:

- **Chat Agent**: Custom agent cho từng nghiệp vụ (tuyển dụng, policy, sale)
- **Research**: Tổng hợp thông tin từ web + tài liệu nội bộ, xuất báo cáo
- **Quick BI**: Tự động phân tích dữ liệu, trực quan hóa
- **Flow & Automate**: Tự động hóa tác vụ admin lặp lại
- **Kết nối dữ liệu đa dạng**: SharePoint, Outlook, OneDrive, Gmail, Google Drive, Jira, Salesforce, GitHub, S3, database,...

##### Demo HR Talent Review:

1. Tạo JD (Job Description) cho Junior Cloud Engineer chỉ trong vài câu lệnh
2. Review 6 CV, tự động chấm điểm dựa trên bộ tiêu chí (technical 40%, problem-solving 25%, communication 15%, etc.)
3. Phân loại: Strong/Good/Low/Very Low
4. Xuất report HTML trực quan với benchmark so sánh
5. Tự động đề xuất mức lương dự kiến

- **Kết quả**: Giảm thời gian tuyển dụng, tiết kiệm cost, tăng chất lượng nhân sự.

#### Security & MCP Server (Anh Nghị & Anh Toàn - Renova Cloud & AWS Security Builder)

##### Vấn đề:

Amazon Q (trên internet) cần kết nối với MCP Server chứa dữ liệu nội bộ. Kết nối qua public internet tiềm ẩn rủi ro bảo mật (DDoS, Man-in-the-Middle, data leakage).

##### Giải pháp:

Dùng VPC Connection để kết nối Amazon Q với MCP Server trong Private Subnet

##### Kiến trúc:

Amazon Q → VPC Connection → Interface Endpoint → ALB (HTTPS) → MCP Server (EC2)

##### Các thành phần bảo mật:

- VPC Endpoint (Interface Endpoint): Kết nối riêng tư, không qua internet
- Private DNS: Chỉ truy cập được trong VPC
- ALB với TLS (mã hóa) và ACM certificate
- Route 53 Resolver: DNS nội bộ để truy vấn MCP Server
- Cognito: Authentication cho người dùng

### Bài Học Rút Ra

Sau khi tham gia sự kiện "GenAI-powered App-DB Modernization workshop", tôi đã rút ra được nhiều bài học quý giá về ứng dụng của AI trong doanh nghiệp cũng như định hướng phát triển bản thân:

#### 1. AI đang thay đổi cách vận hành doanh nghiệp

- **Tự động hóa thông minh**: AI không chỉ tự động hóa các tác vụ lặp lại mà còn có khả năng phân tích, đưa ra quyết định và giải quyết vấn đề phức tạp trong nhiều lĩnh vực từ vận hành cloud, nhân sự đến tài chính.
- **Tối ưu chi phí và thời gian**: Các giải pháp AI như Cloud Agent, DevOps Agent đã chứng minh khả năng giảm đáng kể thời gian xử lý sự cố (từ giờ xuống phút) và giảm thao tác thủ công (lên đến 100%).
- **Nâng cao chất lượng công việc**: AI hỗ trợ con người đưa ra quyết định chính xác hơn dựa trên dữ liệu, ví dụ như trong HR Talent Review giúp đánh giá ứng viên khách quan và hiệu quả.

#### 2. Kiến trúc và triển khai AI cần được thiết kế cẩn thận

- **Multi-Agent vs Single Agent**: Việc sử dụng Multi-Agent Architecture (như Cloud Thinker) giúp tối ưu chi phí, kiểm soát context tốt hơn và dễ quản lý phân quyền.
- **Phù hợp với ngôn ngữ và văn hóa địa phương**: Đối với tiếng Việt, kiến trúc 3 thành phần (Speech → Text → LLM → Text → TTS) hiệu quả hơn Speech-to-Speech do khả năng xử lý của LLM với text tiếng Việt đã rất tốt.
- **Bảo mật là yếu tố then chốt**: Khi triển khai AI trong doanh nghiệp, việc kết nối an toàn giữa các hệ thống (VPC Connection, Private Subnet, TLS encryption) là vô cùng quan trọng để bảo vệ dữ liệu nội bộ.

#### 3. Thách thức khi triển khai AI trong thực tế

- **Xử lý các tình huống phức tạp**: Voice Agent cho ngân hàng phải đối mặt với nhiều thách thức như tốc độ xử lý, ngắt lời, accent vùng miền và tool calling.
- **Tích hợp với hệ thống hiện có**: DevOps Agent phải xử lý dữ liệu từ nhiều nguồn khác nhau (CloudWatch, Splunk, v.v.) và liên kết thông tin để tìm ra root cause.
- **Fallback to Human**: AI hiện tại chưa thể xử lý 100% tình huống, cần có cơ chế chuyển sang nhân viên khi cần thiết.

#### 4. Tương lai của thị trường lao động

- **AI sẽ không thay thế hoàn toàn con người**: AI sẽ là công cụ hỗ trợ đắc lực, nhưng vẫn cần những người thực sự giỏi và biết sử dụng AI hiệu quả.
- **Cloud và AI đang thay đổi thị trường việc làm**: Sinh viên cần sớm trải nghiệm môi trường doanh nghiệp, tiếp cận và làm quen với các công nghệ AI để không bị tụt hậu.
- **Cần phát triển kỹ năng mới**: Bên cạnh kiến thức chuyên môn, cần trang bị kỹ năng làm việc với AI, hiểu cách prompt engineering, và khả năng tích hợp AI vào quy trình làm việc.

#### 5. Định hướng phát triển bản thân

- **Trải nghiệm thực tế**: Tham gia các workshop, sự kiện để học hỏi từ các chuyên gia và hiểu rõ ứng dụng của AI trong doanh nghiệp.
- **Tiếp cận công nghệ mới**: Tìm hiểu về AWS AI services (SageMaker, Bedrock, Q), các framework xây dựng Agent (LangChain, CrewAI), và cách tích hợp AI vào ứng dụng thực tế.
- **Xây dựng tư duy giải quyết vấn đề**: Thay vì chỉ học lý thuyết, hãy áp dụng AI để giải quyết các bài toán thực tế, từ đơn giản đến phức tạp.

### Kết luận

Sự kiện đã mang đến cái nhìn tổng quan và sâu sắc về cách AI đang định hình tương lai của doanh nghiệp. Từ Cloud Agent, Voice AI, DevOps Agent, AI trong HR đến Security & MCP Server, tất cả đều cho thấy tiềm năng to lớn của AI trong việc tối ưu hóa vận hành, nâng cao hiệu quả và tạo ra giá trị mới. Đây là thời điểm vàng để sinh viên chúng tôi trang bị kiến thức và kỹ năng về AI để sẵn sàng cho thị trường lao động tương lai.

### Hình ảnh sự kiện
![Toàn cảnh sự kiện AWS First Cloud AI Journey Community Day](/images/event/event1/checkin1.jpg)