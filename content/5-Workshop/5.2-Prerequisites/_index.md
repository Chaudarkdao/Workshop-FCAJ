---
title: "Prerequisites"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

### Objective
Prepare a controlled environment before creating billed resources.

- Use an AWS account and select us-east-1.
- Install Git, Python 3, AWS CLI v2, Hugo extended 0.134.3 or compatible.
- Configure SageMaker Studio/JupyterLab without embedding access keys.
- Create a private bucket and SageMaker/Lambda execution roles.
- Configure AWS Budget alert.

```bash
export AWS_REGION="us-east-1"
export PROJECT_BUCKET="heart-risk-mlops-<ACCOUNT_ID>-us-east-1-fcaj"
export PREFIX="heart-risk"
export ENDPOINT_NAME="heart-risk-endpoint"
export PIPELINE_NAME="heart-risk-pipeline"
```

**Expectation**: Identity recognition successful and principal is authorized to access the bucket. If access denied, check role/bucket policy or Region; do not enable public access to "fix".

**Cost/Security**: Enable alerts before running jobs; keep Block Public Access; use roles and least privilege permissions.

---

### Evidence and Technical Explanation

#### 1. Region Selection and Budget Creation

Region us-east-1 is used consistently throughout the entire project.

![Region us-east-1](../../images/5-Workshop/5.2-Prerequisites/AWS-01-selected-region.png)

AWS Budget is configured to monitor project costs.

![AWS Budget](../../images/5-Workshop/5.2-Prerequisites/AWS-02-budget-overview.png)

#### 2. IAM Permissions

Set up permissions for the IAM account.

![IAM](../../images/5-Workshop/5.2-Prerequisites/AWS-08-sagemaker-role-permissions.png)

Lambda is only granted permission to invoke the project's endpoint.

![Lambda](../../images/5-Workshop/5.2-Prerequisites/AWS-14-lambda-invoke-policy.png)

---

#### SageMaker Tasks in the Project

- Read and write data to S3.
- Create Processing Jobs, Training Jobs, HPO Jobs, and Pipelines.
- Write logs and metrics to CloudWatch.

#### Lambda Tasks in the Project

- Write logs to CloudWatch Logs.
- Call `sagemaker:InvokeEndpoint`.
- Limit resource access to the `heart-risk-endpoint`.

#### Observations

The permission design separates the SageMaker execution role and Lambda execution role. Lambda is not granted permissions to train models, access the entire S3 bucket, or manage SageMaker; the function only needs to write logs and invoke the endpoint. This permission separation helps reduce the blast radius if the API is compromised or abused.