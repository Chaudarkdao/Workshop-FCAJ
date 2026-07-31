---
title : "Data Capture"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.7.5 </b> "
---

### Data Capture
```bash
EnableCapture=true
InitialSamplingPercentage=100
CaptureOptions=[Input, Output]
```

Các file Data Capture được lưu dưới dạng JSONL trên S3.
![capture-files](../../../../images/5-Workshop/5.7-Deploy/W6-12-capture-files.png)
Các record JSONL chứa endpointInput và endpointOutput, eventMetadata và inferenceTime. Đây là nguồn dữ liệu để kiểm tra hoạt động endpoint và hỗ trợ quy trình monitoring.
![capture-record](../../../../images/5-Workshop/5.7-Deploy/W6-13-capture-record.png)