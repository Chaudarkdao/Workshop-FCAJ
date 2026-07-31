---
title : "Test"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.7.4 </b> "
---
### Test
#### Thành công
response get /health thành công.
![succ http](../../../../images/5-Workshop/5.7-Deploy/W6-08-health-200.png)
response post /predict thành công.
![succ pre](../../../../images/5-Workshop/5.7-Deploy/W6-10-predict-400.png)
### Thất bại
request thiếu field trả http 400.
![fail http](../../../../images/5-Workshop/5.7-Deploy/W6-09-predict-200.png)
prediction service không sẵn sàng trả http 502.
![fail pre](../../../../images/5-Workshop/5.7-Deploy/W6-11-predict-502.png)

| Test | Kỳ vọng | Ý nghĩa vận hành |
| --- | --- | --- |
| Health | 200 | wrapper truy cập được |
| Prediction hợp lệ | 200 | tích hợp API-endpoint hoạt động |
| Thiếu field | 400 | validate phía client hoạt động |
| Service không sẵn sàng | 502 | lỗi downstream được kiểm soát |