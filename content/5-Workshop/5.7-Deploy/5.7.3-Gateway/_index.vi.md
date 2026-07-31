---
title : "API Gateway"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.7.3 </b> "
---
### API Gateway
**Amazon API Gateway** là dịch vụ quản lý API hoàn chỉnh, cho phép bạn tạo, xuất bản, bảo mật và giám sát các API một cách dễ dàng. Trong hệ thống Dự đoán Bệnh Tim, API Gateway đóng vai trò là **"cửa ngõ"** (entry point) để ứng dụng y tế và bác sĩ có thể tương tác với mô hình Machine Learning.

**Vai trò của API Gateway trong dự án này:**

1. **Cổng vào duy nhất (Single Entry Point):** Tất cả các request từ client đều đi qua API Gateway, giúp tập trung quản lý và bảo mật.
2. **Tích hợp với Lambda:** API Gateway gọi Lambda function, Lambda lại gọi SageMaker Endpoint, tạo thành một pipeline xử lý hoàn chỉnh.

Tạo API Gateway:
```bash
curl -i "$API_BASE_URL/health"
curl -i -X POST "$API_BASE_URL/predict"   -H 'content-type: application/json' --data @sample-request.json
```
Kết quả:
![API Gateway](../../../../images/5-Workshop/5.7-Deploy/W6-07-api-routes.png)
### API Endpoints

Hệ thống cung cấp hai endpoint chính để tương tác với mô hình dự đoán bệnh tim:

| Method | Endpoint | Mô tả |
| --- | --- | --- |
| `GET` | `/health` | Kiểm tra trạng thái hoạt động của API |
| `POST` | `/predict` | Gửi dữ liệu lâm sàng và nhận kết quả dự đoán |

---

#### 1. GET /health - Kiểm tra sức khỏe API

Endpoint này dùng để kiểm tra API wrapper có đang hoạt động bình thường hay không. Hữu ích cho việc monitoring và kiểm tra kết nối.

#### 1. GET /health - Kiểm tra sức khỏe người dùng
Endpoint này dùng để trả ra dự đoán Quy trình như sau:
- nhận JSON đầu vào
- Lambda validate
- gọi SageMaker Endpoint
- trả prediction
