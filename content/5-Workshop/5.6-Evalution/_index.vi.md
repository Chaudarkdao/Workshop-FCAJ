---
title : "Evaluation và Model Registry"
date : 2024-01-01 
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---
### Evaluation và Model Registry
#### Evaluation

![evalution result](../../../images/5-Workshop/5.6-Evalution/W5-02-evaluation-metrics-and-confusion-matrix.png)
| Metric | Giá trị |
| --- | --- |
| ROC-AUC | 0.8855 |
| Accuracy | 0.7933 |
| Precision | 0.7249 |
| Recall | 0.8186 |
| F1-Score | 0.7689 |
| False Negative Rate | 0.1814 |

#### Confusion Matrix

| | Dự đoán: Không bệnh (0) | Dự đoán: Có bệnh (1) |
| --- | --- | --- |
| **Thực tế: Không bệnh (0)** | 472 | 137 |
| **Thực tế: Có bệnh (1)** | 80 | 361 |
    
Kết luận:
Mô hình đạt ROC-AUC 0,885515. Recall đạt 0,818594, nghĩa là mô hình nhận diện được phần lớn các trường hợp positive trong tập test. Tuy nhiên, vẫn còn 80 false negatives. Đây là hạn chế quan trọng vì trong bài toán liên quan đến sức khỏe, bỏ sót trường hợp có nguy cơ thường nghiêm trọng hơn cảnh báo nhầm.
#### Model Registry
![Code Regist](../../../images/5-Workshop/5.6-Evalution/code-regist.jpg)
![Model Versions](../../../images/5-Workshop/5.6-Evalution/W5-01-model-versions.png)
| Version | State | Ý nghĩa |
| --- | --- | --- |
| 1 | Approved | version được duyệt và giữ lại |
| 2 | Approved | nguồn triển khai cho heart-risk-endpoint |
| 3 | PendingManualApproval | được Pipeline thành công tạo |


**Kết luận:**
Sau khi có kết quả ta tiến hành đăng kí model. Nhìn vào hình có 2 version được duyệt là 1 và 2. Version 3 ko được duyệt vì nó là sản phẩm của quá trình pipeline. Ở đây nó ko được duyệt chứng tỏ Pipeline không tự động phê duyệt hoặc triển khai model, giúp duy trì bước kiểm soát thủ công trước production deployment.


