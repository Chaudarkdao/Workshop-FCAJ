---
title: "SageMaker Pipeline"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

### 7. SageMaker Pipeline - Automation and Quality Gate

The SageMaker Pipeline is built to automate the entire workflow from data preprocessing, model training, quality evaluation, to model registration or blocking if requirements are not met.

---

#### Pipeline Graph

![Pipeline Graph](../../images/5-Workshop/5.9-Pipeline/W8-01-pipeline-graph.png)

*SageMaker Pipeline automating preprocessing, training, evaluation, and registration*

#### Quality Gate - Performance Thresholds

| Metric | Required Threshold |
| --- | --- |
| **ROC-AUC** | ≥ 0.84 |
| **F1-Score** | ≥ 0.70 |
| **Recall** | ≥ 0.65 |

#### Success Execution

Execution finished with `Succeeded` status: PreprocessData, TrainModel, EvaluateModel, CheckModelQuality, and RegisterModel all completed successfully. Result is Model Package version 3 with `PendingManualApproval` status.

```bash
aws sagemaker list-pipeline-executions   --pipeline-name "$PIPELINE_NAME" --region "$AWS_REGION"
```
Pipeline execution succeeded.

![Success Pipeline](../../images/5-Workshop/5.9-Pipeline/W8-02-pipeline-success.png)

All steps completed successfully.

![Success Pipeline Graph](../../images/5-Workshop/5.9-Pipeline/W8-03-success-steps.png)

Model passed the quality gate and was routed to RegisterModel.

![Condition Pass](../../images/5-Workshop/5.9-Pipeline/W8-04-condition-pass.png)

**Conclusion:** Success execution creates Model Package version 3 with `PendingManualApproval` status. The Pipeline does not automatically deploy the endpoint, thus maintaining a manual control step.

---

#### Intentional Failure - Pipeline Failure on Purpose

**AucThreshold** was increased to **0.99**, higher than the actual ROC-AUC of the model (0.8855).
```bash
aws sagemaker start-pipeline-execution   --pipeline-name "$PIPELINE_NAME"   --pipeline-parameters Name=AucThreshold,Value=0.99   --region "$AWS_REGION"
```
Pipeline execution failed intentionally.

![Pipeline Failure](../../images/5-Workshop/5.9-Pipeline/W8-05-pipeline-failure.png)

AucThreshold was overridden to 0.99.

![Failure Parameters](../../images/5-Workshop/5.9-Pipeline/W8-06-failure-parameters.png)

MetricThresholdFailed was triggered and RegisterModel did not run.

![Fail Step](../../images/5-Workshop/5.9-Pipeline/W8-07-fail-step.png)

**This is an expected result, not a system error.** The Pipeline works exactly as designed: it only allows model registration when all quality thresholds are met.