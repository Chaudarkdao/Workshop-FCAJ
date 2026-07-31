---
title : "Deployment Endpoint"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.7.1 </b> "
---
### Deployment Endpoint
Triển khai Approved Model Package version 2 thành `heart-risk-endpoint` trên một instance `ml.m5.large` và chờ `InService`.
```bash
aws sagemaker describe-endpoint   --endpoint-name "$ENDPOINT_NAME" --region "$AWS_REGION"   --query 'EndpointStatus'
```
Các field response kỳ vọng gồm `prediction`, `risk_probability`, `threshold`, `model_type` or `model_version`, and `disclaimer`. `W6-01a/b` cần chứng minh trạng thái/cấu hình; `W6-03` chứng minh inference trực tiếp. `ml.t3.medium` từng fail package validation và được xử lý bằng `ml.m5.large` được hỗ trợ.

{{% notice warning %}}
⚠️ Lưu ý: Hệ thống chỉ phục vụ mục đích học tập và minh họa; không phải là chẩn đoán y khoa.
{{% /notice %}}
Chi phí: Endpoint bị tính phí liên tục; gọi qua IAM có phạm vi và không public trực tiếp.
### Minh chứng và diễn giải kỹ thuật 
Real-time endpoint heart-risk-endpoint ở trạng thái InService.
![Endpoint](../../../../images/5-Workshop/5.7-Deploy/W6-01a-endpoint-inservice.png)

**Ý nghĩa kỹ thuật**: InService chứng minh package đã duyệt sẵn sàng cho suy luận thời gian thực managed.

Gọi endpoint thành công
![Success Endpoint](../../../../images/5-Workshop/5.7-Deploy/W6-03-direct-inference.png)
**Ý nghĩa kỹ thuật**: Điều này chứng tỏ endpoint đã được deploy thành công và gọi thành công. Tiếp theo chúng ta sẽ đi đến với `Lambda`