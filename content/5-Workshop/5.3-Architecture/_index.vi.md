---
title : "Kiến trúc"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---
### Mục tiêu và luồng
![Kiến trúc](../../../images/2-Proposal/ml_architecture.png)

- **Offline**: raw S3 → Processing → split/artifact → Training/HPO → Evaluation → Registry.
- **Online**: API Gateway → Lambda validate → endpoint → response; Data Capture ghi JSONL vào S3.
- **Monitoring**: capture/baseline → custom Processing → report → custom metric → alarm.
- **Pipeline**: condition kiểm tra AUC/F1/recall; pass đăng ký, fail tạo MetricThresholdFailed

| Đã hiện thực trong PoC | Khuyến nghị production |
| --- | --- |
| Một endpoint instance | Auto Scaling và thiết kế vận hành multi-AZ |
| HTTP integration chưa có production auth | Cognito/API key/WAF và throttling |
| Service IAM role, S3 private | VPC-only và chiến lược KMS key |
| Script thủ công và Pipeline | IaC, CI/CD, automated retraining có phê duyệt |


{{% notice warning %}}
⚠️ Lưu ý: Hệ thống chỉ phục vụ mục đích học tập và minh họa; không phải là chẩn đoán y khoa.
{{% /notice %}}