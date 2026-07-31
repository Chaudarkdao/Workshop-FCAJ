---
title: "Lambda"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.7.2 </b> "
---

### Lambda

Lambda is the middleware layer between API Gateway and SageMaker Runtime. It acts as an **orchestrator** that processes client requests, invokes the model on the SageMaker Endpoint, and returns prediction results to the user.
```bash
endpoint = os.environ["ENDPOINT_NAME"]
response = runtime.invoke_endpoint(
    EndpointName=endpoint, ContentType="application/json", Body=json.dumps(payload)
)
```
### Lambda Configuration

![Lambda Configuration](../../../images/5-Workshop/5.7-Deploy/W6-04-lambda-config.png)

Environment variables linking Lambda to the SageMaker Endpoint.

![Lambda Environment Variables](../../../images/5-Workshop/5.7-Deploy/W6-05-lambda-environment.png)

Detailed permissions for Lambda to invoke the endpoint.

![Lambda Endpoint Permissions](../../../images/5-Workshop/5.7-Deploy/W6-06b-lambda-role-details.png)

**Results:**
- Valid events return a structured result; missing fields return 400; prediction service unavailable returns 502 without exposing stack traces. In case of timeout, check Lambda/endpoint logs. Lambda and log retention incur costs.