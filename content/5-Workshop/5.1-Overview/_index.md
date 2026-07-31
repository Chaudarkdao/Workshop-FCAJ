---
title: "Overview"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Objectives and Success Criteria

The traceability flow is built from versioned raw data to the monitored API, with Pipeline quality gates. The final Logistic Regression model achieved test AUC of 0.885515, F1 of 0.768903, and recall of 0.818594, exceeding the gates of 0.84/0.70/0.65.

| Component | Verified Results |
| --- | --- |
| Processing | 4,900/1,050/1,050; 36 features; no missing values |
| Registry/Deployment | version 2 Approved and deployed |
| API | 200, 400 and 502 error handling in place |
| Drift | 6/20 violations; alarm status: ALARM |
| Pipeline | success → version 3 registered as PENDING; failure → blocked |

![Architecture Diagram](../../images/2-Proposal/ml_architecture.png)

### Source
https://github.com/DuoChip/heart-risk-aws

{{% notice warning %}}
⚠️ Note: This system is for educational and demonstration purposes only; it is not a medical diagnostic tool.
{{% /notice %}}