---
title : "Lambda"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.7.2 </b> "
---
### Lambda

Lambda là lớp trung gian giữa API Gateway và SageMaker Runtime. Nó đóng vai trò như một **"bộ điều phối"** (orchestrator) xử lý các request từ client, gọi mô hình trên SageMaker Endpoint, và trả về kết quả dự đoán cho người dùng.
```bash
endpoint = os.environ["ENDPOINT_NAME"]
response = runtime.invoke_endpoint(
    EndpointName=endpoint, ContentType="application/json", Body=json.dumps(payload)
)
```
Cấu hinh Lambda
![Cấu hình Lambda](../../../../images/5-Workshop/5.7-Deploy/W6-04-lambda-config.png)

Các biến môi trường liên kết Lambda với SageMaker Endpoint.
![biến Lambda](../../../../images/5-Workshop/5.7-Deploy/W6-05-lambda-environment.png)

Chi tiết quyền gọi endpoint của lambda.
![Endpoint Lambda](../../../../images/5-Workshop/5.7-Deploy/W6-06b-lambda-role-details.png)

Kết quả:
- Event hợp lệ trả result có cấu trúc; thiếu field trả 400; prediction service không sẵn sàng trả 502 không lộ stack trace. Khi timeout, đọc log Lambda/endpoint. Lambda và log retention phát sinh phí.