---
title : "Tiền xử lý dữ liệu"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

### Data Processing
#### Upload S3
Upload CSV 7.000 dòng chuẩn lên `s3://$PROJECT_BUCKET/heart-risk/raw/heart_attack_dataset.csv`
![UpS3](../../../images/5-Workshop/5.4-Preparation/code-ups3.jpg)
#### SageMaker Processing Job
Tạo train/validation/test có thể tái lập mà không leakage.
Numeric missing dùng median imputation và scaling; categorical dùng most-frequent imputation và one-hot encoding. Loại `patient_id`.
| Kiểm tra | Kỳ vọng |
| --- | --- |
| Số dòng split | 4,900 / 1,050 / 1,050 |
| Feature raw / processed | 20 / 36 |
| Missing sau xử lý | 0 |
| Phạm vi fit | train_only |

![Code](../../../images/5-Workshop/5.4-Preparation/code-processing.jpg)
![Processing Complete](../../../images/5-Workshop/5.4-Preparation/W2-01-processing-completed.png)
Trạng thái Completed xác nhận toàn bộ preprocessing đã được thực hiện trên hạ tầng managed. 
#### Result SageMaker Processing Job
Kết quả sau khi thực hiện bước Processing:
![Processing Complete](../../../images/5-Workshop/5.4-Preparation/W2-02-processing-log.png)
Log xác minh 4.900/1.050/1.050 dòng, 36 feature, không còn missing và fit train-only.

Lưu kết quả vào S3:
![Save S3](../../../images/5-Workshop/5.4-Preparation/W2-03-processed-s3.png)