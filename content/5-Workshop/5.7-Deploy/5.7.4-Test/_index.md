---
title: "Test"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.7.4 </b> "
---

### Test

#### Success

`GET /health` response successful.

![Success Health](../../../images/5-Workshop/5.7-Deploy/W6-08-health-200.png)

`POST /predict` response successful.

![Success Predict](../../../images/5-Workshop/5.7-Deploy/W6-10-predict-400.png)

#### Failure

Request missing field returns HTTP 400.

![Failure HTTP](../../../images/5-Workshop/5.7-Deploy/W6-09-predict-200.png)

Prediction service unavailable returns HTTP 502.

![Failure Predict](../../../images/5-Workshop/5.7-Deploy/W6-11-predict-502.png)

| Test | Expected | Operational Meaning |
| --- | --- | --- |
| Health | 200 | Wrapper is accessible |
| Valid Prediction | 200 | API-endpoint integration is working |
| Missing field | 400 | Client-side validation is working |
| Service unavailable | 502 | Downstream errors are controlled |