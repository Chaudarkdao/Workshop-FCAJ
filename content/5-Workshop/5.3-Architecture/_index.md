---
title: "Architecture"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Objectives and Workflow

![Architecture Diagram](../../images/2-Proposal/ml_architecture.png)

- **Offline**: raw S3 → Processing → split/artifact → Training/HPO → Evaluation → Registry.
- **Online**: API Gateway → Lambda validate → endpoint → response; Data Capture writes JSONL to S3.
- **Monitoring**: capture/baseline → custom Processing → report → custom metric → alarm.
- **Pipeline**: condition checks AUC/F1/Recall; pass → register, fail → creates MetricThresholdFailed.

| Implemented in PoC | Production Recommendation |
| --- | --- |
| Single endpoint instance | Auto Scaling and multi-AZ operational design |
| HTTP integration without production auth | Cognito/API key/WAF and throttling |
| Service IAM role, S3 private | VPC-only and KMS key strategy |
| Manual scripts and Pipeline | IaC, CI/CD, automated retraining with approval |

{{% notice warning %}}
⚠️ Note: This system is for educational and demonstration purposes only; it is not a medical diagnostic tool.
{{% /notice %}}