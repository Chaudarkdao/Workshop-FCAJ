---
title : "Các bước chuẩn bị"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---
### Mục tiêu
Chuẩn bị môi trường có kiểm soát trước khi tạo tài nguyên tính phí.
- Dùng AWS account và chọn us-east-1.
- Cài Git, Python 3, AWS CLI v2, Hugo extended 0.134.3 hoặc tương thích.
- Cấu hình SageMaker Studio/JupyterLab không nhúng access key.
- Tạo bucket private và execution role SageMaker/Lambda.
- Cấu hình AWS Budget alert.
```bash
export AWS_REGION="us-east-1"
export PROJECT_BUCKET="heart-risk-mlops-<ACCOUNT_ID>-us-east-1-fcaj"
export PREFIX="heart-risk"
export ENDPOINT_NAME="heart-risk-endpoint"
export PIPELINE_NAME="heart-risk-pipeline"
```
aws sts get-caller-identity
aws s3api head-bucket --bucket "$PROJECT_BUCKET"

**Kỳ vọng**: Nhận diện identity thành công và principal được phép truy cập bucket. Nếu access denied, kiểm tra role/bucket policy hoặc Region; không bật public để “sửa”.
**Chi phí/bảo mật**: bật alert trước khi chạy job; giữ Block Public Access; dùng role và đặc quyền tối thiểu.
### Minh chứng và diễn giải kỹ thuật
#### 1. Chọn region và tạo budget
Region us-east-1 được sử dụng thống nhất trong toàn bộ dự án
![Region us-east-1 ](../../../images/5-Workshop/5.2-Prerequisites/AWS-01-selected-region.png)
AWS Budget được cấu hình để theo dõi chi phí dự án.
![AWS Budget](../../../images/5-Workshop/5.2-Prerequisites/AWS-02-budget-overview.png)
#### 2. IAM permissions
Thiết lập các quyền cho tài khoản IAM
![IAM](../../../images/5-Workshop/5.2-Prerequisites/AWS-08-sagemaker-role-permissions.png)
Lambda chỉ được cấp quyền gọi endpoint của dự án
![Lambda](../../../images/5-Workshop/5.2-Prerequisites/AWS-14-lambda-invoke-policy.png)

#### Nhiệm vụ SageMaker trong project

- Đọc và ghi dữ liệu vào S3.
- Tạo Processing Job, Training Job, HPO Job và Pipeline.
- Ghi log và metric vào CloudWatch.
#### Nhiệm vụ Lambda trong project
- Ghi log vào CloudWatch Logs.
- Gọi sagemaker:InvokeEndpoint.
- Giới hạn resource vào endpoint heart-risk-endpoint.
#### Nhận xét
Thiết kế quyền tách biệt SageMaker execution role và Lambda execution role. Lambda không được cấp quyền train model, truy cập toàn bộ S3 hoặc quản trị SageMaker; function chỉ cần ghi log và gọi endpoint. Cách phân quyền này giúp giảm blast radius khi API bị lỗi hoặc bị lạm dụng. 