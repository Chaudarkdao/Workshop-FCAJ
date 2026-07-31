---
title : "Tổng quan"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---
### Mục tiêu và tiêu chí thành công
Luồng truy vết được xây dựng từ raw data có version đến API được monitor và Pipeline có quality gate. Logistic Regression cuối đạt test AUC 0,885515, F1 0,768903, recall 0,818594, vượt gate 0,84/0,70/0,65.

| Thành phần | Kết quả đã xác minh |
| --- | --- |
| Processing | 4.900/1.050/1.050; 36 feature; không missing |
| Registry/deployment | version 2 Approved và deployed |
| API | 200, 400 và 502 có kiểm soát |
| Drift | 6/20 violation; alarm ALARM |
| Pipeline | success đăng ký v3 pending; fail chặn |

![Kiến trúc](../../../images/2-Proposal/ml_architecture.png)

### Nguồn 
https://github.com/DuoChip/heart-risk-aws

{{% notice warning %}}
⚠️ Lưu ý: Hệ thống chỉ phục vụ mục đích học tập và minh họa; không phải là chẩn đoán y khoa.
{{% /notice %}}