---
title: "Bản đề xuất"
date: 2026-07-27
weight: 2
chapter: false
pre: " <b> 2. </b> "
---



## Hệ thống Dự đoán Bệnh Tim với Machine Learning trên AWS

### Giải pháp end-to-end sử dụng Amazon SageMaker cho chẩn đoán hỗ trợ y tế

---

### 1. Tóm tắt điều hành

Hệ thống Dự đoán Bệnh Tim được thiết kế nhằm hỗ trợ các cơ sở y tế trong việc sàng lọc và đánh giá nguy cơ bệnh tim mạch dựa trên dữ liệu lâm sàng của bệnh nhân. Nền tảng sử dụng các dịch vụ Machine Learning trên AWS để xây dựng, huấn luyện và triển khai mô hình dự đoán khả năng mắc bệnh tim với độ chính xác cao. Hệ thống được phát triển theo quy trình MLOps hoàn chỉnh, từ xử lý dữ liệu, huấn luyện mô hình, tối ưu siêu tham số, đến triển khai dưới dạng REST API với khả năng giám sát và phát hiện sai lệch dữ liệu theo thời gian thực.

---

### 2. Tuyên bố vấn đề

#### Vấn đề hiện tại

Bệnh tim mạch là nguyên nhân gây tử vong hàng đầu trên toàn cầu. Việc chẩn đoán sớm và chính xác đóng vai trò then chốt trong điều trị, nhưng hiện tại các bác sĩ phải dựa chủ yếu vào kinh nghiệm lâm sàng và các chỉ số đơn lẻ, dễ dẫn đến bỏ sót hoặc chẩn đoán sai. Các mô hình dự đoán hiện có thường không được tích hợp vào quy trình khám chữa bệnh một cách hệ thống, thiếu khả năng cập nhật liên tục và giám sát hiệu suất.

#### Giải pháp

Hệ thống sử dụng Amazon SageMaker để xây dựng pipeline ML hoàn chỉnh:

- Dữ liệu được tiền xử lý và kỹ thuật đặc trưng với **SageMaker Processing Jobs**
- Mô hình được huấn luyện với các thuật toán như XGBoost hoặc Scikit-learn
- Siêu tham số được tối ưu hóa tự động với **Automatic Model Tuning**
- Mô hình được đóng gói, đăng ký trong **SageMaker Model Registry** để quản lý phiên bản
- Mô hình sau đó được triển khai lên **SageMaker Endpoint** cho suy luận thời gian thực
- Kết hợp với **API Gateway** và **AWS Lambda** để tạo REST API cho ứng dụng y tế
- **SageMaker Model Monitor** và **CloudWatch** được thiết lập để phát hiện data drift và theo dõi chất lượng dự đoán

#### Lợi ích và hoàn vốn đầu tư (ROI)

Hệ thống giúp các bác sĩ đưa ra quyết định nhanh hơn và chính xác hơn, giảm thiểu rủi ro chẩn đoán sai và nâng cao hiệu quả điều trị. Nền tảng này có thể được tích hợp vào các bệnh viện và phòng khám với chi phí vận hành thấp nhờ mô hình serverless và khả năng tự động hóa. Với ước tính chi phí khoảng vài đô la mỗi tháng, hệ thống mang lại giá trị lâu dài về mặt y tế và nghiên cứu, đồng thời có thể mở rộng để dự đoán nhiều loại bệnh khác.

---

### 3. Kiến trúc giải pháp

Hệ thống áp dụng kiến trúc AWS Serverless và MLOps để xây dựng pipeline ML end-to-end. Dữ liệu bệnh nhân từ các nguồn khác nhau được tải lên Amazon S3, sau đó được tiền xử lý bằng SageMaker Processing Jobs. Mô hình được huấn luyện và tối ưu hóa trong SageMaker Training Jobs và Automatic Model Tuning. Phiên bản mô hình được quản lý trong Model Registry và triển khai lên SageMaker Endpoint. Lambda và API Gateway cung cấp REST API cho ứng dụng y tế, trong khi CloudWatch và Model Monitor đảm bảo hiệu suất theo dõi.

![System Architecture](../../images/2-Proposal/ml_architecture.png)

#### Dịch vụ AWS sử dụng

| Dịch vụ | Mục đích |
| --- | --- |
| **Amazon SageMaker** | Xử lý dữ liệu, huấn luyện, tối ưu, đăng ký mô hình, triển khai endpoint và giám sát |
| **Amazon S3** | Lưu trữ dữ liệu thô, dữ liệu đã xử lý và artifacts của mô hình |
| **AWS Lambda** | Xử lý yêu cầu từ API Gateway và gọi SageMaker Endpoint |
| **Amazon API Gateway** | Cung cấp REST API cho ứng dụng khách |
| **Amazon CloudWatch** | Giám sát endpoint, ghi log và thiết lập cảnh báo |
| **AWS IAM** | Quản lý quyền truy cập và phân quyền giữa các dịch vụ |
| **SageMaker Model Registry** | Lưu trữ và quản lý phiên bản mô hình |
| **SageMaker Pipelines** | Tự động hóa toàn bộ quy trình ML |

#### Thiết kế thành phần

- **Dữ liệu:** Lưu trữ thô trong S3 bucket, sau đó xử lý và lưu trữ trong bucket riêng cho training
- **Xử lý dữ liệu:** SageMaker Processing Jobs thực hiện làm sạch, chuẩn hóa, xử lý missing values, và feature engineering
- **Huấn luyện và tối ưu:** Training Jobs chạy thuật toán XGBoost hoặc custom script với PyTorch; Automatic Model Tuning tối ưu siêu tham số
- **Quản lý mô hình:** Model Registry lưu trữ các phiên bản với trạng thái (PENDING, APPROVED, REJECTED)
- **Triển khai:** SageMaker Endpoint cung cấp real-time inference; Lambda làm middleware xử lý request từ API Gateway
- **Giám sát:** Model Monitor phát hiện data drift và quality drift; CloudWatch cảnh báo khi endpoint có vấn đề
- **Tự động hóa:** SageMaker Pipelines kết hợp tất cả các bước thành workflow tự động từ preprocessing đến triển khai

---

### 4. Triển khai kỹ thuật

#### Các giai đoạn triển khai

Dự án gồm 8 giai đoạn chính:

| STT | Công việc |
| --- | --- |
| **1** | Nghiên cứu ML workflow và hệ sinh thái AWS ML; cấu hình môi trường (IAM, S3, SageMaker Studio) |
| **2** | Chuẩn bị và xử lý dữ liệu (Data preprocessing, feature engineering) với SageMaker Processing Jobs |
| **3** | Huấn luyện mô hình (Training Jobs) trên SageMaker; thử nghiệm built-in algorithms hoặc custom script |
| **4** | Theo dõi thí nghiệm với SageMaker Experiments; tối ưu siêu tham số với Automatic Model Tuning (HPO) |
| **5** | Đóng gói và đăng ký mô hình vào SageMaker Model Registry; thiết lập model versioning |
| **6** | Triển khai mô hình lên SageMaker Endpoint (real-time inference); tích hợp API Gateway + Lambda để expose REST API |
| **7** | Thiết lập monitoring với SageMaker Model Monitor và CloudWatch; phát hiện data drift |
| **8** | Tự động hoá toàn bộ pipeline với SageMaker Pipelines; tổng hợp kết quả và hoàn thiện báo cáo |

#### Yêu cầu kỹ thuật

- **Ngôn ngữ lập trình:** Python, sử dụng thư viện Scikit-learn, XGBoost, PyTorch
- **Framework:** Amazon SageMaker, boto3, sagemaker SDK
- **Dữ liệu:** Tập dữ liệu bệnh tim (ví dụ: UCI Heart Disease Dataset hoặc Framingham) với các đặc trưng như tuổi, huyết áp, cholesterol, nhịp tim, đường huyết, hút thuốc, v.v.
- **Công cụ:** Jupyter Notebook trong SageMaker Studio, AWS CLI, Git
- **Kỹ năng:** Python, AWS ML services, MLOps, CI/CD cơ bản

---

### 5. Lộ trình & Mốc triển khai

| Giai đoạn | Mốc quan trọng |
| --- | --- |
| **Thiết lập môi trường & Tiền xử lý** | Hoàn thành xử lý dữ liệu, sẵn sàng training |
| **Huấn luyện & Tối ưu** | Mô hình đạt accuracy ≥ 85%, tối ưu siêu tham số |
| **Quản lý & Triển khai** | Mô hình được đăng ký và triển khai lên endpoint |
| **Giám sát** | Hệ thống giám sát data drift hoạt động |
| **Tự động hóa & Báo cáo** | Pipeline tự động hoàn chỉnh, báo cáo tổng kết |
| **Sau triển khai** | Mở rộng cho các bệnh khác và tích hợp vào bệnh viện thực tế |

---

### 6. Ước tính ngân sách

> **Lưu ý:** Có thể tham khảo chi phí trên [AWS Pricing Calculator](https://calculator.aws/).

| Dịch vụ | Chi phí ước tính | Ghi chú |
| --- | --- | --- |
| SageMaker Studio | ~2.52 USD/tháng | ml.t3.medium, 40 giờ/tháng |
| SageMaker Endpoint | ~5.52 USD/tháng | ml.m5.large, 24/7 sẽ có giá 99,36, nhưng ở đây bọn em chỉ deploy 40h |
| S3 Storage | ~0.115 USD/tháng | 5 GB |
| Lambda | ~0.002 USD/tháng | 10.000 request |
| API Gateway | ~0.01 USD/tháng | 10.000 request |
| CloudWatch | ~0.01 USD/tháng | 1 GB log |
| **Tổng** | **~8,117 USD/tháng** | Khi đã deploy rồi thì sẽ ko phát sinh chi phí của  SageMaker Studio(trừ khi train lại)|

#### Lưu ý về chi phí

- Chi phí phát triển và kiểm thử có thể thấp hơn đáng kể nhờ tắt endpoint khi không sử dụng
- Sử dụng SageMaker Serverless Inference nếu không cần real-time liên tục 
- Tận dụng AWS Free Tier cho các service cơ bản (S3, Lambda, API Gateway) để giảm chi phí trong giai đoạn phát triển

---

### 7. Đánh giá rủi ro

#### Ma trận rủi ro

| Rủi ro | Mức độ ảnh hưởng | Xác suất |
| --- | --- | --- |
| Sai lệch dữ liệu (data drift) | Cao | Trung bình |
| Chi phí vượt ngân sách | Trung bình | Thấp |
| Hiệu suất mô hình kém | Cao | Trung bình |
| Lỗi tích hợp API | Trung bình | Thấp |

#### Chiến lược giảm thiểu

- **Data drift:** Sử dụng SageMaker Model Monitor để phát hiện và cảnh báo sớm; retrain mô hình định kỳ
- **Chi phí:** Thiết lập cảnh báo ngân sách và sử dụng SageMaker Serverless Inference để giảm chi phí
- **Hiệu suất:** Sử dụng Automatic Model Tuning và thử nghiệm nhiều thuật toán; lưu trữ phiên bản cũ để rollback
- **Lỗi tích hợp:** Kiểm thử kỹ lưỡng bằng API Gateway mock và CloudWatch logs

#### Kế hoạch dự phòng

- Nếu endpoint lỗi, chuyển sang chế độ batch inference hoặc fallback đến mô hình đã được phê duyệt trước đó
- Sử dụng CloudFormation để khôi phục pipeline trong trường hợp lỗi hệ thống

---

### 8. Kết quả kỳ vọng

#### Cải tiến kỹ thuật

- Hệ thống dự đoán bệnh tim với độ chính xác trên 85%
- Được tích hợp vào quy trình khám chữa bệnh thông qua REST API
- Quy trình ML được tự động hóa từ preprocessing đến triển khai, giúp dễ dàng cập nhật và bảo trì

#### Giá trị dài hạn

- Nền tảng có thể mở rộng để dự đoán nhiều bệnh khác như tiểu đường, ung thư, hoặc bệnh hô hấp
- Hệ thống cung cấp dữ liệu phân tích và mô hình có thể được tái sử dụng cho các nghiên cứu y tế
- Góp phần nâng cao chất lượng chăm sóc sức khỏe cộng đồng và hỗ trợ ra quyết định cho bác sĩ