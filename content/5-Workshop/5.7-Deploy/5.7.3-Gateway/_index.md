---
title: "API Gateway"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.7.3 </b> "
---

### API Gateway

**Amazon API Gateway** is a fully managed API service that allows you to create, publish, secure, and monitor APIs easily. In the Heart Disease Prediction system, API Gateway serves as the **entry point** for medical applications and doctors to interact with the Machine Learning model.

**Role of API Gateway in this project:**

1. **Single Entry Point:** All client requests go through API Gateway, enabling centralized management and security.
2. **Integration with Lambda:** API Gateway invokes the Lambda function, which in turn calls the SageMaker Endpoint, forming a complete processing pipeline.
Create API Gateway:
```bash
curl -i "$API_BASE_URL/health"
curl -i -X POST "$API_BASE_URL/predict"   -H 'content-type: application/json' --data @sample-request.json
```
Result:
![API Gateway](../../../images/5-Workshop/5.7-Deploy/W6-07-api-routes.png)

### API Endpoints

The system provides two main endpoints for interacting with the heart disease prediction model:

| Method | Endpoint | Description |
| --- | --- | --- |
| `GET` | `/health` | Check API health status |
| `POST` | `/predict` | Send clinical data and receive prediction results |

---

#### 1. GET /health - API Health Check

This endpoint is used to check whether the API wrapper is operating normally. It is useful for monitoring and connection testing.

#### 2. POST /predict - Heart Disease Prediction

This endpoint returns the prediction result. The workflow is as follows:

- Receive JSON input
- Lambda validates the input
- Call SageMaker Endpoint
- Return prediction result