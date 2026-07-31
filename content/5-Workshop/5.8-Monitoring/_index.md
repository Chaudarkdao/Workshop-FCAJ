---
title: "Monitoring and Data Drift"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

### Custom Processing Job

Official Model Monitor schedule was configured; however, the required feature-level metrics did not appear in CloudWatch at the time of testing. Therefore, the project uses a fallback approach with a custom SageMaker Processing Job.

![Custom Processing Job](../../images/5-Workshop/5.8-Monitoring/W7-01a-custom-processing-job.png)

![Custom Processing Report](../../images/5-Workshop/5.8-Monitoring/W7-02-drift-report.png)

#### Data Drift Detection Results

After performing data monitoring using the Custom SageMaker Processing Job, the system detected drift in the input data distribution compared to the original training data.

#### Summary Statistics

| Metric | Value |
| --- | --- |
| Baseline rows | 4,900 |
| Current rows | 7,000 |
| Features checked | 20 |
| Violations | 6 |
| Drift detected | ✅ True |

#### Features with Drift Detected

![Drift Features Summary](../../images/5-Workshop/5.8-Monitoring/W7-03a-drift-features-summary.png)

The system detected **six features** with significant deviation from the training data:

| No. | Feature | Description |
| --- | --- | --- |
| 1 | **age** | Patient's age |
| 2 | **resting_bp** | Resting systolic blood pressure |
| 3 | **cholesterol** | Cholesterol (mg/dl) |
| 4 | **bmi** | Body Mass Index |
| 5 | **smoking_status** | Smoking status |
| 6 | **stress_level** | Stress level |

#### Drift Detection Methods

To identify drifted features, the system applies the following detection methods and thresholds:

##### 1. For Numeric Features

| Method | Threshold | Drift Condition |
| --- | --- | --- |
| Standardized Mean Shift | > 0.5 | Standardized mean difference exceeds 0.5 |

##### 2. For Categorical Features

| Method | Threshold | Drift Condition |
| --- | --- | --- |
| Total Variation Distance (TVD) | > 0.20 | TVD exceeds 0.20 |

#### Interpretation of Results

Detecting **six drifted features** indicates:

- **Patient data distribution has changed** over time compared to the original training data
- **Model accuracy may degrade** if it continues predicting on new data without retraining
- **Model retraining is needed** with new data to maintain performance

#### Limitations

> ⚠️ **Important Note:**
>
> The drift detection thresholds (`standardized mean shift > 0.5` and `TVD > 0.20`) are set for **Proof of Concept (POC) purposes** to demonstrate the system's drift detection capability.
>
> These thresholds:
> - **Are not** official statistical standards for production environments
> - **Are not** clinical diagnostic standards
> - Are for reference and illustration of the MLOps process only
>
> In a real production environment, these thresholds should be:
> - Calculated based on standard statistical distributions (e.g., p-value, confidence intervals)
> - Adjusted according to the characteristics of each feature and the medical domain
> - Aligned with stakeholders (data scientists, domain experts, medical doctors)

---

### CloudWatch Metrics

![Custom Metrics](../../images/5-Workshop/5.8-Monitoring/W7-04-custom-metrics.png)

We have:
- `DriftDetected = 1`
- `DataQualityViolationCount = 6`
- Namespace = `Custom/HeartRisk`

![Custom Alarm](../../images/5-Workshop/5.8-Monitoring/W7-05-custom-alarm.png)

- The alarm uses statistic `Maximum`, threshold `1`, and comparison operator `GreaterThanOrEqualToThreshold`.
- Missing data is configured as `ignore` to accommodate the custom Processing Job, which only publishes metrics when a monitoring run completes.