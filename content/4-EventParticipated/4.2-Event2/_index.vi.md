---
title: "Event 2"
date: 2026-07-28
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "Workshop: Xu hướng Cloud & AI - Chuẩn bị hành trang cho sinh viên"

### Mục Đích Của Sự Kiện

- Cập nhật xu hướng thị trường Cloud & AI hiện tại
- Trang bị kỹ năng và tư duy cần thiết cho sinh viên trước làn sóng AI
- Kết nối sinh viên với các chuyên gia trong ngành

### Danh Sách Diễn Giả

- **Anh Nguyễn Gia Hưng** - Head of SA, AWS Vietnam
- **Anh Bành Cẩm Vĩnh** - Renova Cloud
- **Chị Như Trần** - Account Manager, AWS Vietnam
- **Anh Khang Nguyễn** - Cloud Kinetics, cựu SV Swinburne


---

### Nội Dung Nổi Bật

#### 1. Thị trường việc làm & Xu hướng Cloud (Anh Nguyễn Gia Hưng - Head of SA, AWS Vietnam)

##### Thực tế thị trường hiện nay:

- **Intern đã yêu cầu Kubernetes + Container** – một bạn intern fail phỏng vấn ngân hàng vì không nắm rõ K8S
- Một intern khác có tiếng Anh tốt, chứng chỉ, nền tảng vững nhưng vẫn bị đánh giá là **"non"** – doanh nghiệp không còn kiên nhẫn với Fresher
- **90% công việc không đăng tuyển public**, mà qua referral và network nội bộ. Đó là lý do cần tham gia cộng đồng.

##### AWS tại Việt Nam:

- AWS đã tăng trưởng **20 lần trong 6 năm**, trong khi hạ tầng phần cứng truyền thống giảm 10 lần
- **Cloud first** – mọi ứng dụng mới phải thiết kế chạy trên cloud trước, chỉ đưa về on-premise khi thực sự cần (như CCTV)
- AWS cam kết đầu tư lâu dài với **3 trụ cột**:
  - **Local talent** – 99,9% nhân sự AWS Việt Nam là người Việt
  - **Infrastructure** – đầu tư Local Zone tại HN (hàng trăm triệu USD), hướng tới AWS Region (6+ tỷ USD, 15-20 năm mới hòa vốn)
  - **Skill & Future Talent** – xây dựng đội ngũ builder tương lai cho Việt Nam

##### 6 nhóm ngành lớn sử dụng AWS:

| Nhóm ngành | Ví dụ khách hàng |
| --- | --- |
| Banking & Fintech | Ngân hàng, tài chính, bảo hiểm |
| Retail & E-commerce | Bán lẻ, thương mại điện tử |
| Manufacturing | Sản xuất |
| Media & Entertainment | VTV, giải trí |
| Telco | Viễn thông |
| Healthcare | Y tế |

##### Lời khuyên:

Ngoài chọn roll (Data Eng, DevOps, AI), sinh viên nên **chọn thêm industry** để hồ sơ nổi bật hơn.

##### Mô hình kim tự tháp đảo ngược:

- **Trước đây:** 3-5 Junior → 2-3 Middle → 1 Senior
- **Hiện nay:** 1-2 Junior → AI Agent thay thế Middle → Nhiều Senior hơn

Nhu cầu Junior giảm, nhưng tổng cơ hội toàn ngành không giảm – chỉ là thị trường ép các bạn phải **trưởng thành nhanh hơn**.

##### Công thức thành công:

> **Kết quả = Capability × Visibility × Consistency**

- **Capability:** Năng lực chuyên môn
- **Visibility:** Sự hiện diện, mạng lưới quan hệ
- **Consistency:** Kiên trì, liên tục học hỏi

> *"Chứng chỉ chỉ giúp qua vòng lọc CV. AI sẽ scan CV, scan side project, scan blog của bạn. Profile bạn đã chuẩn bị đến đâu rồi?"*

##### Ví dụ bóng đèn LED:

> Đèn LED tiết kiệm 90% điện, nhưng tổng điện tiêu thụ toàn cầu không giảm – vì người ta dùng đèn nhiều hơn, chiếu sáng nhiều nơi hơn

AI cũng vậy: **làm phần mềm rẻ hơn → nhu cầu phần mềm tăng → cơ hội việc làm tăng về dài hạn**

---


#### 2. Data Engineering – Trường vs Doanh nghiệp (Anh Bành Cẩm Vĩnh - Renova Cloud)

##### 5 môn học nền tảng quan trọng:

1. Cơ sở dữ liệu
2. Ngôn ngữ lập trình
3. Cấu trúc dữ liệu & Giải thuật
4. Cơ sở dữ liệu phân tán
5. BI (Business Intelligence)

##### So sánh Trường vs Doanh nghiệp:

| Tiêu chí | Trường học | Doanh nghiệp |
| --- | --- | --- |
| Dữ liệu | Sạch, nhỏ, có sẵn | Nhiều nguồn, dơ, thiếu, định nghĩa khác nhau, thay đổi liên tục |
| Yêu cầu | Rõ ràng, 5-6 requirement | Thay đổi liên tục, không rõ ràng |
| Thời gian | Có vài tháng | *"Có cho tôi ngày mai không?"* |
| Team | 4-5 người, quen biết | Làm việc với nhiều phòng ban (Product, Marketing, Finance, DevOps, Security) |
| Hậu quả | Mất điểm, học lại | Ảnh hưởng production, mất tiền, mất việc |

##### 90% project sinh viên chỉ làm "bề nổi":

- Đọc data → transform → load → dashboard = **chỉ 10%**
- **Thiếu:** xử lý khi pipeline fail, data quality, bảo mật, monitoring, alerting

##### Cách cải thiện:

> Dùng AI (Kiro, Claude) để scan project và so với Well-Architected Framework, yêu cầu nó gợi ý các tính năng production còn thiếu.

##### Hành trình 5 năm của anh Vĩnh:

| Công ty | Bài học |
| --- | --- |
| Siêu Việt Group (startup) | **Ownership** – được xây dựng từ đầu, chịu trách nhiệm cho mọi quyết định |
| Heineken (tập đoàn lớn) | **Business understanding** – cùng một từ "active user" có nghĩa khác với DevOps, Marketing, Finance |
| VNG ZaloPay (fintech) | **Think big, think future** – mỗi dòng code phải đáp ứng tăng trưởng sau này, không thể để hệ thống sập |
| Renova Cloud (consulting) | **Start with problem** – chọn tool/service sau khi hiểu bài toán, không chọn tool trước |

##### AI có thay thế data engineer không?

- **AI thay thế được:** viết SQL, viết code, tạo dashboard đơn giản, viết documentation
- **AI không thay thế được:** hiểu business problem, design architecture, decision making, communication, align process giữa các team

##### 5 bài học tâm đắc của anh Vĩnh:

1. **Connect the dots** – mọi việc đều có ý nghĩa, kể cả thất bại
2. **Kiên định** – đừng từ bỏ khi mới nộp vài chục CV
3. **Growth mindset** – mở lòng học từ mọi người, mọi nơi
4. **Communication là technical skill**, không phải soft skill
5. **AI không thay thế bạn**, người biết dùng AI sẽ thay thế người không biết dùng AI

---

#### 3. Nỗi Sợ & Kỹ Năng Mềm (Chị Như Trần - Account Manager, AWS Vietnam)

##### Nỗi sợ phổ biến:

- **Sợ sai:** thực chất là sợ hệ quả (điểm thấp, ánh mắt phán xét, gia đình thất vọng)
- **Sợ public speaking:** sợ bị đánh giá, sợ nói sai

##### Cách khắc phục:

- **Nhận diện đúng nỗi sợ** của mình
- **Thực hành** – không ai giỏi public speaking từ lần đầu
- **Giao tiếp với ba mẹ:** nhiều khi kỳ vọng của ba mẹ chỉ đơn giản là *"con sống an vui, vui vẻ, về ăn cơm cùng ba mẹ"*

##### Cách small talk với sếp:

- Bắt đầu bằng cái chào – sếp không bao giờ chào mình trước
- *"Sáng nay sếp ăn gì chưa?"*, *"Cuối tuần sếp có gì vui không?"*, *"Tuần này có gì em cần hỗ trợ thêm không?"*
- **Visibility bắt đầu từ những điều nhỏ nhất**

##### Câu chuyện 11 lần apply AWS:

- Chị Như apply AWS **11 lần**, 10 lần đầu bị reject
- Lần thứ 11 được một "bác" trong AWS refer trực tiếp đến Hiring Manager
- Bác nói với HM: *"Tao có một người khá thú vị. Đây là những trade nó có và khó để huấn luyện. Đây là những trade nó thiếu nhưng có thể đào tạo (coachable)"*
- Trong buổi gặp, chị nói: *"Trong tất cả ứng viên anh đang tuyển, có ai tìm được cách ngồi trước mặt anh như em không? Và em không ở Singapore, em ở Việt Nam."*
- Buổi interview sau đó, HM **coach** chị cách phỏng vấn thay vì chỉ hỏi

##### Bài học về cơ hội:

- Cơ hội đăng tuyển công khai là **"Red Ocean"** – nhiều cạnh tranh
- Cơ hội tốt nhất là **"Blue Ocean"** – ít ai thấy, đòi hỏi làm những việc không ai muốn làm

> *"Cơ hội không phân biệt đối xử, nó dành cho người muốn nó nhất"*

> *"Hạt giống cơ hội gieo từ hôm nay, có thể nảy mầm trong tương lai"*

---


#### 4. Skill & Mindset cho AI Era (Anh Khang Nguyễn - Cloud Kinetics, cựu SV Swinburne)

##### Thực tế tuyển dụng:

- **Năm trước:** đề bài chatbot, thời gian 1 tuần
- **Năm nay:** cùng đề bài + khó hơn, thời gian 3 ngày
- **Kết quả:** 90% bài làm dùng AI nhưng ứng viên không hiểu gì → bị loại

> *"You can outsource your thinking, but you cannot outsource your understanding."*

##### Cách dùng AI đúng:

- Dùng AI để **tăng tốc**, không để **làm thay tư duy**
- Phải hiểu được **tại sao** AI đi đến kết luận đó
- Có kiến thức nền tảng để **validate output** của AI

##### AI chỉ là công cụ khuếch đại:

- Nếu bạn hiểu sai → AI dẫn bạn đi sai
- Nếu bạn có nền tảng tốt → AI giúp bạn làm được **gấp nhiều lần** công việc

##### Lời khuyên cho sinh viên:

- **Đặt câu hỏi WHY** – hiểu tầng cơ bản, không học thuộc lòng
- **Embrace mistake** – sai ở trường là bình thường, đừng sợ; đi làm là được trả tiền để không làm sai
- **Stay hungry** – vượt xa kỳ vọng; 10 module là chưa đủ, tự tìm module 11, 12, 13
- **Integrity** – làm những phần không có điểm nhưng đúng là cần làm; nhà tuyển dụng sẽ hỏi những phần đó
- **Không đi một mình** – form team với cả technical lẫn business để có nhiều góc nhìn
- **Consistency** – kiên trì trong học tập và phát triển

##### Lương và lợi ích công việc:

> **Đừng quá quan trọng lương khởi điểm**

**3 vòng tròn cần đánh giá công việc:**

1. **Đam mê** – bạn thích làm gì?
2. **Trách nhiệm** – những việc bạn phải làm dù không thích
3. **Lợi ích** – lương, network, knowledge, personal growth

> *"Công việc đầu tiên là bàn đạp – lấy kinh nghiệm, network, knowledge để nhảy mức lương tiếp theo"*

##### 5 tiêu chí nhà tuyển dụng đánh giá (theo thứ tự ưu tiên):

| Thứ tự | Tiêu chí | Ý nghĩa |
| --- | --- | --- |
| 1 | **Thái độ** | Quan trọng nhất, thể hiện tiềm năng học hỏi |
| 2 | **Trình độ** | Kỹ năng chuyên môn |
| 3 | **Kinh nghiệm** | Số năm (đơn vị thời gian) |
| 4 | **Trải nghiệm** | Bề rộng, bao nhiêu dự án, bao nhiêu loại khách hàng – **quan trọng hơn kinh nghiệm** |
| 5 | **Tố chất** | Năng khiếu bẩm sinh |

---


### Bài Học Rút Ra

Sau khi tham gia sự kiện "Workshop: Xu hướng Cloud & AI - Chuẩn bị hành trang cho sinh viên", tôi đã rút ra được nhiều bài học quý giá về thị trường lao động, kỹ năng cần thiết và tư duy phát triển trong thời đại AI:

#### 1. Thị trường lao động đang thay đổi nhanh chóng

- **Yêu cầu ngày càng cao**: Intern đã cần biết Kubernetes, doanh nghiệp không còn kiên nhẫn với Fresher. Sinh viên cần trang bị kiến thức thực tế ngay từ sớm.
- **Cloud là xu hướng tất yếu**: AWS đã tăng trưởng 20 lần trong 6 năm, Cloud First là chiến lược của mọi doanh nghiệp. Cần nắm vững kiến thức cloud để không bị tụt hậu.
- **Mạng lưới quan hệ quan trọng**: 90% công việc không đăng tuyển public. Tham gia cộng đồng, xây dựng network là yếu tố sống còn để tìm kiếm cơ hội.

#### 2. Sự khác biệt giữa trường học và doanh nghiệp

- **Dữ liệu thực tế không sạch sẽ**: Trường học cho dữ liệu đã được làm sạch, doanh nghiệp thì dữ liệu đến từ nhiều nguồn, thiếu, dơ và thay đổi liên tục.
- **Yêu cầu thay đổi liên tục**: Trường có yêu cầu rõ ràng, doanh nghiệp thì yêu cầu thay đổi liên tục, không rõ ràng và luôn gấp rút.
- **Project sinh viên mới chỉ làm 10%**: 90% sinh viên mới chỉ làm phần nổi (đọc data → transform → load → dashboard), thiếu các phần quan trọng như: xử lý fail, data quality, bảo mật, monitoring, alerting.

#### 3. Tư duy và kỹ năng cần thiết trong thời đại AI

- **AI là công cụ khuếch đại**: Nếu bạn hiểu sai → AI dẫn bạn đi sai. Nếu bạn có nền tảng tốt → AI giúp bạn làm được gấp nhiều lần công việc.
- **Không outsource tư duy**: Có thể dùng AI để tăng tốc, nhưng không thể dùng AI để thay thế sự hiểu biết. Phải hiểu được tại sao AI đi đến kết luận đó.
- **Communication là technical skill**: Kỹ năng giao tiếp không còn là soft skill mà là kỹ năng kỹ thuật cần thiết để làm việc hiệu quả trong doanh nghiệp.

#### 4. Nỗi sợ và cách vượt qua

- **Sợ sai và sợ public speaking là bình thường**: Cần nhận diện đúng nỗi sợ và thực hành thường xuyên để vượt qua.
- **Visibility bắt đầu từ những điều nhỏ nhất**: Small talk với sếp, chào hỏi đồng nghiệp, xây dựng mối quan hệ từ những hành động nhỏ.
- **Cơ hội ở Blue Ocean**: Những cơ hội đăng tuyển công khai là Red Ocean - nhiều cạnh tranh. Cơ hội tốt nhất là làm những việc không ai muốn làm.

#### 5. Định hướng phát triển bản thân

- **Đặt câu hỏi WHY**: Hiểu tầng cơ bản, không học thuộc lòng.
- **Embrace mistake**: Sai ở trường là bình thường, đừng sợ. Đi làm được trả tiền để không làm sai.
- **Stay hungry**: Vượt xa kỳ vọng, tự tìm thêm kiến thức ngoài chương trình học.
- **Integrity**: Làm những phần không có điểm nhưng đúng là cần làm.
- **Consistency**: Kiên trì trong học tập và phát triển.
- **Đừng quá quan trọng lương khởi điểm**: Công việc đầu tiên là bàn đạp để lấy kinh nghiệm, network, knowledge cho mức lương tiếp theo.

### Kết luận

Sự kiện đã mang đến một góc nhìn toàn diện và thực tế về thị trường lao động ngành Cloud & AI, những kỹ năng cần thiết và tư duy phát triển trong thời đại AI. Từ câu chuyện của các diễn giả, tôi nhận ra rằng:

1. **Thị trường đang thay đổi nhanh** – cần liên tục cập nhật và phát triển bản thân
2. **Nền tảng vững là chìa khóa** – AI chỉ là công cụ, nền tảng kiến thức mới là quan trọng
3. **Kỹ năng mềm quyết định thành công** – communication, visibility, consistency là những yếu tố giúp bạn vượt trội
4. **Không ngừng học hỏi và phát triển** – hành trình học tập không dừng lại khi ra trường

Đây là thời điểm vàng để trang bị kiến thức, kỹ năng và tư duy cần thiết để sẵn sàng cho thị trường lao động tương lai. Sự kiện đã cho tôi thêm động lực và định hướng rõ ràng hơn cho con đường sự nghiệp của mình.
---


### Hình Ảnh Sự Kiện

![Toàn cảnh sự kiện AWS First Cloud AI Journey Community Day](/images/event/event2/checkin2.jpg)