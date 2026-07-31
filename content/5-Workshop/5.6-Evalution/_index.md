---
title: "Evaluation and Model Registry"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

### Evaluation and Model Registry

#### Evaluation

![Evaluation Result](../../images/5-Workshop/5.6-Evalution/W5-02-evaluation-metrics-and-confusion-matrix.png)

| Metric | Value |
| --- | --- |
| ROC-AUC | 0.8855 |
| Accuracy | 0.7933 |
| Precision | 0.7249 |
| Recall | 0.8186 |
| F1-Score | 0.7689 |
| False Negative Rate | 0.1814 |

#### Confusion Matrix

| | Predicted: No Disease (0) | Predicted: Disease (1) |
| --- | --- | --- |
| **Actual: No Disease (0)** | 472 | 137 |
| **Actual: Disease (1)** | 80 | 361 |

**Conclusion:**
The model achieved a ROC-AUC of 0.885515. Recall reached 0.818594, meaning the model correctly identifies the majority of positive cases in the test set. However, there are still 80 false negatives. This is a significant limitation because in health-related problems, missing a high-risk case is often more serious than a false alarm.

---

#### Model Registry

![Code Register](../../images/5-Workshop/5.6-Evalution/code-regist.jpg)

![Model Versions](../../images/5-Workshop/5.6-Evalution/W5-01-model-versions.png)

| Version | State | Meaning |
| --- | --- | --- |
| 1 | Approved | Approved version kept for reference |
| 2 | Approved | Deployment source for heart-risk-endpoint |
| 3 | PendingManualApproval | Created by successful Pipeline execution |

**Conclusion:**
After obtaining results, we proceed to register the model. The image shows two approved versions: 1 and 2. Version 3 is not approved because it is a product of the Pipeline process. It remains unapproved, demonstrating that the Pipeline does not automatically approve or deploy models, maintaining a manual control step before production deployment.