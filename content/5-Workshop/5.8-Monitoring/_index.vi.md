---
title : "Monitoring và Data Drift"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---
### Custom Processing Job
Official Model Monitor schedule đã được cấu hình, tuy nhiên metric feature-level cần thiết chưa xuất hiện trên CloudWatch tại thời điểm kiểm thử. Vì vậy, dự án sử dụng phương án fallback bằng custom SageMaker Processing Job.
![Custom Processing Job](../../../images/5-Workshop/5.8-Monitoring/W7-01a-custom-processing-job.png)
![Custom Processing Report](../../../images/5-Workshop/5.8-Monitoring/W7-02-drift-report.png)
#### Kết quả phát hiện Data Drift

Sau khi thực hiện giám sát dữ liệu bằng Custom SageMaker Processing Job, hệ thống đã phát hiện sự sai lệch (drift) trong phân phối dữ liệu đầu vào so với dữ liệu huấn luyện ban đầu.

#### Thống kê tổng quan

| Chỉ số | Giá trị |
| --- | --- |
| Baseline rows (Dữ liệu huấn luyện) | 4.900 |
| Current rows (Dữ liệu mới) | 7.000 |
| Features checked (Số đặc trưng kiểm tra) | 20 |
| Violations (Số đặc trưng bị drift) | 6 |
| Drift detected (Phát hiện drift) | ✅ True |

#### Các đặc trưng bị phát hiện drift
![drift feature](../../../images/5-Workshop/5.8-Monitoring/W7-03a-drift-features-summary.png)

Hệ thống phát hiện **sáu đặc trưng** có sự sai lệch đáng kể so với dữ liệu huấn luyện:

| STT | Đặc trưng (Feature) | Mô tả |
| --- | --- | --- |
| 1 | **age** | Tuổi của bệnh nhân |
| 2 | **resting_bp** | Huyết áp tâm thu khi nghỉ |
| 3 | **cholesterol** | Cholesterol (mg/dl) |
| 4 | **bmi** | Chỉ số khối cơ thể |
| 5 | **smoking_status** | Tình trạng hút thuốc |
| 6 | **stress_level** | Mức độ căng thẳng |





#### Phương pháp phát hiện Drift

Để xác định các đặc trưng bị drift, hệ thống áp dụng các phương pháp và ngưỡng phát hiện như sau:

##### 1. Đối với đặc trưng dạng số (Numeric Features)

| Phương pháp | Ngưỡng phát hiện | Điều kiện Drift |
| --- | --- | --- |
| Standardized Mean Shift | > 0,5 | Chênh lệch trung bình chuẩn hóa vượt ngưỡng 0,5 |



##### 2. Đối với đặc trưng dạng phân loại (Categorical Features)

| Phương pháp | Ngưỡng phát hiện | Điều kiện Drift |
| --- | --- | --- |
| Total Variation Distance (TVD) | > 0,20 | Khoảng cách biến thiên tổng vượt ngưỡng 0,20 |



#### Ý nghĩa của kết quả

Việc phát hiện **sáu đặc trưng bị drift** cho thấy:

- *Phân phối dữ liệu bệnh nhân đã thay đổi** theo thời gian so với dữ liệu huấn luyện ban đầu
- **Mô hình có thể giảm độ chính xác** nếu tiếp tục dự đoán trên dữ liệu mới mà không được retrain
- **Cần retrain mô hình** với dữ liệu mới để duy trì hiệu suất

#### Giới hạn (Limitations)

> ⚠️ **Lưu ý quan trọng:**
>
> Các ngưỡng phát hiện drift (`standardized mean shift > 0,5` và `TVD > 0,20`) được thiết lập nhằm mục đích **phục vụ cho giai đoạn Proof of Concept (POC)** của dự án, giúp chứng minh khả năng phát hiện drift của hệ thống.
>
> Các ngưỡng này:
> - **Không phải** là tiêu chuẩn thống kê chính thức cho môi trường production
> - **Không phải** là tiêu chuẩn chẩn đoán lâm sàng
> - Chỉ mang tính chất tham khảo và minh họa cho quy trình MLOps
>
> Trong môi trường production thực tế, các ngưỡng này cần được:
> - Tính toán dựa trên phân phối thống kê chuẩn (ví dụ: p-value, confidence interval)
> - Điều chỉnh theo đặc thù của từng đặc trưng và lĩnh vực y tế
> - Thống nhất với các bên liên quan (data scientist, domain expert, y bác sĩ)

### CloudWatch metrics
![Custom Processing Job](../../../images/5-Workshop/5.8-Monitoring/W7-04-custom-metrics.png)
Ta có:
- DriftDetected = 1
- DataQualityViolationCount = 6
- Namespace = Custom/HeartRisk

![Custom Processing Report](../../../images/5-Workshop/5.8-Monitoring/W7-05-custom-alarm.png)
- Alarm sử dụng statistic Maximum, threshold 1 và comparison operator GreaterThanOrEqualToThreshold. 
- Missing data được cấu hình ở chế độ ignore để phù hợp với custom Processing Job chỉ publish metric khi một monitoring run kết thúc.
