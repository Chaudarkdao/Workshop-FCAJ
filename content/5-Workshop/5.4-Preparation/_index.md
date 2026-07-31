---
title: "Data Processing"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Data Processing

#### Upload to S3

Upload the standard CSV with 7,000 rows to `s3://$PROJECT_BUCKET/heart-risk/raw/heart_attack_dataset.csv`

![Upload S3](../../images/5-Workshop/5.4-Preparation/code-ups3.jpg)

#### SageMaker Processing Job

Create reproducible train/validation/test splits without data leakage.

- Numeric missing values: median imputation and scaling
- Categorical missing values: most-frequent imputation and one-hot encoding
- `patient_id` column is dropped

| Check | Expected |
| --- | --- |
| Row split | 4,900 / 1,050 / 1,050 |
| Raw / processed features | 20 / 36 |
| Missing after processing | 0 |
| Fit scope | train_only |

![Code](../../images/5-Workshop/5.4-Preparation/code-processing.jpg)

![Processing Complete](../../images/5-Workshop/5.4-Preparation/W2-01-processing-completed.png)

The `Completed` status confirms that all preprocessing has been executed on managed infrastructure.

#### SageMaker Processing Job Results

Results after the Processing step:

![Processing Log](../../images/5-Workshop/5.4-Preparation/W2-02-processing-log.png)

The log confirms 4,900/1,050/1,050 rows, 36 features, no missing values, and train-only fit.

Results saved to S3:

![Save to S3](../../images/5-Workshop/5.4-Preparation/W2-03-processed-s3.png)