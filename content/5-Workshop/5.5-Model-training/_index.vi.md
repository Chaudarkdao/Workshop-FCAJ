---
title : "Training và Model Comparison"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

### Training
Ở project này, chúng ta sẽ sử dụng 3 model chính là Logistic Regression, XGBoost và XGBoost sau HPO

#### Logistic Regression
![Logistic Regression Training](../../../images/5-Workshop/5.5-Model-training/W3-01-lr-training.png)
![Logistic Regression](../../../images/5-Workshop/5.5-Model-training/W3-02-lr-metrics.png)

Kết quả:
- Validation ROC-AUC: 0,863949
- F1: 0,747583
- Recall: 0,789116
- Precision: 0,710204
- Threshold: 0,36
Kết luận:
Logistic Regression được sử dụng làm baseline vì có khả năng giải thích tốt, thời gian train ngắn và phù hợp với bài toán phân loại nhị phân. Mô hình đạt validation ROC-AUC 0,863949 và vượt các quality gate của dự án.
#### XGBoost
![XGBoost Training](../../../images/5-Workshop/5.5-Model-training/W3-03-xgb-training.png)
![XGBoost](../../../images/5-Workshop/5.5-Model-training/W3-04-xgb-metrics.png)
Kết quả:
- Validation ROC-AUC: 0,854283
- F1: 0,749749
- Recall: 0,845805
- Precision: 0,673285

Kết luận:
XGBoost đạt recall cao hơn Logistic Regression nhưng có ROC-AUC và precision thấp hơn. Do tiêu chí lựa chọn chính là validation ROC-AUC, Logistic Regression được ưu tiên làm candidate trước HPO.

### Đánh giá hiệu suất các mô hình

Sau quá trình huấn luyện và tối ưu hóa siêu tham số (HPO), chúng tôi tiến hành đánh giá và so sánh hiệu suất của các mô hình dựa trên các chỉ số sau:

- **ROC-AUC**: Đo lường khả năng phân biệt giữa các lớp (càng cao càng tốt)
- **F1-Score**: Trung bình điều hòa giữa Precision và Recall
- **Recall**: Tỷ lệ dương tính thật (TPR) - khả năng phát hiện đúng bệnh nhân mắc bệnh
- **Precision**: Độ chính xác của dự đoán dương tính

| Mô hình | ROC-AUC | F1-Score | Recall | Precision |
| --- | --- | --- | --- | --- |
| Logistic Regression | 0.8639 | 0.7476 | 0.7891 | 0.7102 |
| XGBoost (mặc định) | 0.8543 | 0.7497 | 0.8458 | 0.6733 |
| XGBoost (sau HPO) | 0.8610 | 0.7495 | 0.8889 | - |

Kết luận:
Hyperparameter Optimization được thực hiện cho XGBoost với ba trials và sử dụng validation:auc làm objective metric. Best trial đạt validation ROC-AUC khoảng 0,860982. Mặc dù recall tăng lên khoảng 0,888889, ROC-AUC vẫn thấp hơn Logistic Regression. Vì vậy, Logistic Regression tiếp tục được chọn làm deployment candidate.
