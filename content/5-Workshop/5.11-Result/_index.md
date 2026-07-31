---
title: "Results"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

### Summary of Achieved Results

| Category | Result |
| --- | --- |
| **Data** | 7,000 rows; 20 raw / 36 processed features; train-only fit |
| **Model** | Selected Logistic Regression; test AUC 0.885515, F1 0.768903, Recall 0.818594 |
| **API** | Health / Predict endpoints and 200 / 400 / 502 behavior |
| **Drift** | Six features; custom metrics 1 and 6; alarm ALARM |
| **Pipeline** | Pass → registered v3 pending; test 0.99 → registry blocked |

### Source
https://github.com/DuoChip/heart-risk-aws