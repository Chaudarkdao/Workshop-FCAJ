---
title : "Kết quả"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b> 5.11. </b> "
---
### Tổng kết kết quả đạt được

| Nhóm | Kết quả |
| --- | --- |
| **Dữ liệu** | 7.000 dòng; 20 raw / 36 processed feature; fit train-only |
| **Mô hình** | Chọn Logistic Regression; test AUC 0,885515, F1 0,768903, Recall 0,818594 |
| **API** | Health / Predict và hành vi 200 / 400 / 502 |
| **Drift** | Sáu feature; custom metric 1 và 6; alarm ALARM |
| **Pipeline** | Pass → đăng ký v3 pending; test 0,99 → chặn registry |
### Nguồn 
https://github.com/DuoChip/heart-risk-aws
