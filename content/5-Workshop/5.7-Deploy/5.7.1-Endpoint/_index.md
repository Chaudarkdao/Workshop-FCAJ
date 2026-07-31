---
title: "Deployment Endpoint"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.7.1 </b> "
---

### Deployment Endpoint

Deploy the approved Model Package version 2 as `heart-risk-endpoint` on an `ml.m5.large` instance and wait for `InService` status.

```bash
aws sagemaker describe-endpoint   --endpoint-name "$ENDPOINT_NAME" --region "$AWS_REGION"   --query 'EndpointStatus'
```
Expected response fields include `prediction`, `risk_probability`, `threshold`, `model_type` or `model_version`, and `disclaimer`. `W6-01a/b` should demonstrate status/configuration; `W6-03` demonstrates direct inference. `ml.t3.medium` previously failed package validation and was resolved by using the supported `ml.m5.large`.

{{% notice warning %}}
⚠️ Note: This system is for educational and demonstration purposes only; it is not a medical diagnostic tool.
{{% /notice %}}

**Cost**: The endpoint incurs continuous charges; calls are made via IAM with scoped permissions and are not directly public.

---

### Evidence and Technical Explanation

The real-time endpoint `heart-risk-endpoint` is in `InService` status.

![Endpoint](../../../images/5-Workshop/5.7-Deploy/W6-01a-endpoint-inservice.png)

**Technical significance**: `InService` confirms that the approved package is ready for managed real-time inference.

Successful endpoint invocation.

![Success Endpoint](../../../images/5-Workshop/5.7-Deploy/W6-03-direct-inference.png)

**Technical significance**: This confirms that the endpoint has been successfully deployed and invoked. Next, we will proceed to `Lambda`.