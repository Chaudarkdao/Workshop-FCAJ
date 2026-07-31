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
Data Capture files are stored as JSONL on S3.

![capture-files](../../../images/5-Workshop/5.7-Deploy/W6-12-capture-files.png)

The JSONL records contain `endpointInput` and `endpointOutput`, `eventMetadata`, and `inferenceTime`. This is the data source for checking endpoint activity and supporting the monitoring process.

![capture-record](../../../images/5-Workshop/5.7-Deploy/W6-13-capture-record.png)