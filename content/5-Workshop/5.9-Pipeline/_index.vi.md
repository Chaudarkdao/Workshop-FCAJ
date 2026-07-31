---
title : "SageMaker Pipeline"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---
### 7. SageMaker Pipeline - Tự động hóa và Quality Gate

SageMaker Pipeline được xây dựng để tự động hóa toàn bộ quy trình từ tiền xử lý dữ liệu, huấn luyện mô hình, đánh giá chất lượng, đến đăng ký mô hình hoặc chặn nếu không đạt yêu cầu.

---

#### Pipeline Graph

![Pipeline Graph](../../../images/5-Workshop/5.9-Pipeline/W8-01-pipeline-graph.png)

*SageMaker Pipeline tự động hóa preprocessing, training, evaluation và registration*

#### Quality Gate - Ngưỡng chất lượng

| Chỉ số | Ngưỡng yêu cầu |
| --- | --- |
| **ROC-AUC** | ≥ 0.84 |
| **F1-Score** | ≥ 0.70 |
| **Recall** | ≥ 0.65 |

#### Success execution
Execution kết thúc `Succeeded`: PreprocessData, TrainModel, EvaluateModel, CheckModelQuality, and RegisterModel đều thành công. Kết quả là Model Package version 3 với `PendingManualApproval`.

```bash
aws sagemaker list-pipeline-executions   --pipeline-name "$PIPELINE_NAME" --region "$AWS_REGION"
```
Pipeline execution thành công.
![Succes Pipeline ](../../../images/5-Workshop/5.9-Pipeline/W8-02-pipeline-success.png)
Các step nếu thành công
![Succes Pipeline Graph](../../../images/5-Workshop/5.9-Pipeline/W8-03-success-steps.png)
Model vượt quality gate và được chuyển sang RegisterModel.
![Succes Pipeline Graph](../../../images/5-Workshop/5.9-Pipeline/W8-04-condition-pass.png)

**Kết luận:**Success execution tạo Model Package version 3 ở trạng thái PendingManualApproval. Pipeline không tự deploy endpoint, do đó vẫn duy trì được bước kiểm soát thủ công.

#### Intentional Failure - Pipeline thất bại có chủ đích
**AucThreshold** được tăng lên **0.99**, cao hơn ROC-AUC thực tế của mô hình (0.8855)
```bash
aws sagemaker start-pipeline-execution   --pipeline-name "$PIPELINE_NAME"   --pipeline-parameters Name=AucThreshold,Value=0.99   --region "$AWS_REGION"
```

Pipeline execution thất bại có chủ đích.
![Succes Pipeline ](../../../images/5-Workshop/5.9-Pipeline/W8-05-pipeline-failure.png)
AucThreshold được override thành 0,99
![Succes Pipeline Graph](../../../images/5-Workshop/5.9-Pipeline/W8-06-failure-parameters.png)
MetricThresholdFailed được kích hoạt và RegisterModel không chạy.
![Succes Pipeline Graph](../../../images/5-Workshop/5.9-Pipeline/W8-07-fail-step.png)

**Đây là kết quả mong đợi, không phải lỗi hệ thống.** Pipeline hoạt động đúng như thiết kế: chỉ cho phép đăng ký mô hình khi đáp ứng đủ các ngưỡng chất lượng.