---
title: "Training and Model Comparison"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Training

In this project, we use three main models: Logistic Regression, XGBoost, and XGBoost after HPO.

#### Logistic Regression

![Logistic Regression Training](../../images/5-Workshop/5.5-Model-training/W3-01-lr-training.png)

![Logistic Regression](../../images/5-Workshop/5.5-Model-training/W3-02-lr-metrics.png)

**Results:**

- Validation ROC-AUC: 0.863949
- F1: 0.747583
- Recall: 0.789116
- Precision: 0.710204
- Threshold: 0.36

**Conclusion:**
Logistic Regression is used as the baseline because of its good interpretability, short training time, and suitability for binary classification problems. The model achieved a validation ROC-AUC of 0.863949 and exceeded the project's quality gates.

---

#### XGBoost

![XGBoost Training](../../images/5-Workshop/5.5-Model-training/W3-03-xgb-training.png)

![XGBoost](../../images/5-Workshop/5.5-Model-training/W3-04-xgb-metrics.png)

**Results:**

- Validation ROC-AUC: 0.854283
- F1: 0.749749
- Recall: 0.845805
- Precision: 0.673285

**Conclusion:**
XGBoost achieved higher recall than Logistic Regression but had lower ROC-AUC and precision. Since the primary selection criterion is validation ROC-AUC, Logistic Regression is prioritized as the candidate before HPO.

---

### Model Performance Evaluation

After training and hyperparameter optimization (HPO), we evaluate and compare model performance based on the following metrics:

- **ROC-AUC**: Measures the ability to distinguish between classes (higher is better)
- **F1-Score**: Harmonic mean of Precision and Recall
- **Recall**: True Positive Rate (TPR) - ability to correctly detect patients with the disease
- **Precision**: Accuracy of positive predictions

| Model | ROC-AUC | F1-Score | Recall | Precision |
| --- | --- | --- | --- | --- |
| Logistic Regression | 0.8639 | 0.7476 | 0.7891 | 0.7102 |
| XGBoost (default) | 0.8543 | 0.7497 | 0.8458 | 0.6733 |
| XGBoost (after HPO) | 0.8610 | 0.7495 | 0.8889 | - |

**Conclusion:**
Hyperparameter Optimization was performed for XGBoost with three trials using `validation:auc` as the objective metric. The best trial achieved a validation ROC-AUC of approximately 0.860982. Although recall increased to approximately 0.888889, ROC-AUC remained lower than Logistic Regression. Therefore, Logistic Regression continues to be selected as the deployment candidate.