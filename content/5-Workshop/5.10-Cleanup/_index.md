---
title: "Clean Up Resources"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 5.10. </b> "
---

### Clean Up Resources

Use the code snippet below to delete all created resources.
```bash
# 1. Monitoring and alarm
aws sagemaker delete-monitoring-schedule --monitoring-schedule-name heart-risk-monitor --region "$AWS_REGION"
aws cloudwatch delete-alarms --alarm-names heart-risk-custom-drift heart-risk-age-drift --region "$AWS_REGION"

# 2. Endpoint; deletion is asynchronous
aws sagemaker delete-endpoint --endpoint-name "$ENDPOINT_NAME" --region "$AWS_REGION"
aws sagemaker wait endpoint-deleted --endpoint-name "$ENDPOINT_NAME" --region "$AWS_REGION"

# 3. Discover exact dependent names before deleting configs/models
aws sagemaker list-endpoint-configs --name-contains heart-risk --region "$AWS_REGION"
aws sagemaker list-models --name-contains heart-risk --region "$AWS_REGION"

# 4. API and Lambda (resolve API_ID first; do not paste an active URL)
aws apigatewayv2 get-apis --region "$AWS_REGION"
aws lambda delete-function --function-name heart-risk-api --region "$AWS_REGION"
```
Studio/JupyterLab applications can be found at **SageMaker AI → Domains → User profiles → Applications**. Delete from the inside out.