---
title: "Proposal"
date: 2026-07-27
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## Heart Disease Prediction System with Machine Learning on AWS

### End-to-end solution using Amazon SageMaker for medical diagnostic support

---

### 1. Executive Summary

The Heart Disease Prediction System is designed to assist healthcare facilities in screening and assessing cardiovascular disease risk based on patient clinical data. The platform uses AWS Machine Learning services to build, train, and deploy a model for predicting the likelihood of heart disease with high accuracy. The system is developed following a complete MLOps process, from data processing, model training, hyperparameter optimization, to deployment as a REST API with real-time monitoring and data drift detection capabilities.

---

### 2. Problem Statement

#### Current Problem

Cardiovascular disease is the leading cause of death globally. Early and accurate diagnosis plays a crucial role in treatment, but currently doctors must rely primarily on clinical experience and individual indicators, which can easily lead to missed or incorrect diagnoses. Existing prediction models are often not systematically integrated into the medical examination process, lacking continuous update capabilities and performance monitoring.

#### Solution

The system uses Amazon SageMaker to build a complete ML pipeline:

- Data is preprocessed and feature engineered with **SageMaker Processing Jobs**
- Models are trained with algorithms such as XGBoost or Scikit-learn
- Hyperparameters are automatically optimized with **Automatic Model Tuning**
- Models are packaged and registered in **SageMaker Model Registry** for version management
- Models are then deployed to **SageMaker Endpoint** for real-time inference
- Combined with **API Gateway** and **AWS Lambda** to create REST APIs for medical applications
- **SageMaker Model Monitor** and **CloudWatch** are set up to detect data drift and monitor prediction quality

#### Benefits and Return on Investment (ROI)

The system helps doctors make faster and more accurate decisions, minimizing the risk of misdiagnosis and improving treatment effectiveness. This platform can be integrated into hospitals and clinics with low operational costs thanks to serverless architecture and automation capabilities. With estimated costs of just a few dollars per month, the system provides long-term value in healthcare and research, while being scalable to predict many other diseases.

---

### 3. Solution Architecture

The system applies AWS Serverless and MLOps architecture to build an end-to-end ML pipeline. Patient data from various sources is uploaded to Amazon S3, then preprocessed using SageMaker Processing Jobs. Models are trained and optimized in SageMaker Training Jobs and Automatic Model Tuning. Model versions are managed in Model Registry and deployed to SageMaker Endpoint. Lambda and API Gateway provide REST APIs for medical applications, while CloudWatch and Model Monitor ensure performance tracking.

![System Architecture](../images/2-Proposal/ml_architecture.png)

#### AWS Services Used

| Service | Purpose |
| --- | --- |
| **Amazon SageMaker** | Data processing, training, optimization, model registration, endpoint deployment, and monitoring |
| **Amazon S3** | Store raw data, processed data, and model artifacts |
| **AWS Lambda** | Process requests from API Gateway and invoke SageMaker Endpoint |
| **Amazon API Gateway** | Provide REST API for client applications |
| **Amazon CloudWatch** | Monitor endpoints, log, and set up alerts |
| **AWS IAM** | Manage access permissions between services |
| **SageMaker Model Registry** | Store and manage model versions |
| **SageMaker Pipelines** | Automate the entire ML workflow |

#### Component Design

- **Data:** Raw data stored in S3 bucket, then processed and stored in a separate bucket for training
- **Data Processing:** SageMaker Processing Jobs perform cleaning, normalization, missing value handling, and feature engineering
- **Training and Optimization:** Training Jobs run XGBoost algorithms or custom scripts with PyTorch; Automatic Model Tuning optimizes hyperparameters
- **Model Management:** Model Registry stores versions with statuses (PENDING, APPROVED, REJECTED)
- **Deployment:** SageMaker Endpoint provides real-time inference; Lambda acts as middleware processing requests from API Gateway
- **Monitoring:** Model Monitor detects data drift and quality drift; CloudWatch alerts when endpoint issues occur
- **Automation:** SageMaker Pipelines combine all steps into an automated workflow from preprocessing to deployment

---

### 4. Technical Implementation

#### Implementation Phases

The project consists of 8 main phases:

| No. | Task |
| --- | --- |
| **1** | Research ML workflow and AWS ML ecosystem; configure environment (IAM, S3, SageMaker Studio) |
| **2** | Prepare and process data (Data preprocessing, feature engineering) with SageMaker Processing Jobs |
| **3** | Train models (Training Jobs) on SageMaker; test built-in algorithms or custom scripts |
| **4** | Track experiments with SageMaker Experiments; optimize hyperparameters with Automatic Model Tuning (HPO) |
| **5** | Package and register models in SageMaker Model Registry; set up model versioning |
| **6** | Deploy models to SageMaker Endpoint (real-time inference); integrate API Gateway + Lambda to expose REST API |
| **7** | Set up monitoring with SageMaker Model Monitor and CloudWatch; detect data drift |
| **8** | Automate the entire pipeline with SageMaker Pipelines; compile results and complete report |

#### Technical Requirements

- **Programming Language:** Python, using Scikit-learn, XGBoost, PyTorch libraries
- **Framework:** Amazon SageMaker, boto3, sagemaker SDK
- **Data:** Heart disease dataset (e.g., UCI Heart Disease Dataset or Framingham) with features such as age, blood pressure, cholesterol, heart rate, blood sugar, smoking, etc.
- **Tools:** Jupyter Notebook in SageMaker Studio, AWS CLI, Git
- **Skills:** Python, AWS ML services, MLOps, basic CI/CD

---

### 5. Roadmap & Milestones

| Phase | Milestone |
| --- | --- |
| **Environment Setup & Preprocessing** | Complete data processing, ready for training |
| **Training & Optimization** | Model achieves accuracy ≥ 85%, hyperparameters optimized |
| **Management & Deployment** | Model registered and deployed to endpoint |
| **Monitoring** | Data drift monitoring system operational |
| **Automation & Report** | Complete automated pipeline, final report |
| **Post-deployment** | Expand to other diseases and integrate into actual hospitals |

---

### 6. Budget Estimate

> **Note:** Costs can be referenced on [AWS Pricing Calculator](https://calculator.aws/).

| Service | Estimated Cost | Note |
| --- | --- | --- |
| SageMaker Studio | ~$2.52/month | ml.t3.medium, 40 hours/month |
| SageMaker Endpoint | ~$5.52/month | ml.m5.large, 40 hours (24/7 would be $99.36) |
| S3 Storage | ~$0.115/month | 5 GB |
| Lambda | ~$0.002/month | 10,000 requests |
| API Gateway | ~$0.01/month | 10,000 requests |
| CloudWatch | ~$0.01/month | 1 GB log |
| **Total** | **~$8.117/month** | SageMaker Studio costs won't be incurred after deployment (unless retraining) |

#### Cost Notes

- Development and testing costs can be significantly reduced by turning off endpoints when not in use
- Use SageMaker Serverless Inference if continuous real-time is not required
- Leverage AWS Free Tier for basic services (S3, Lambda, API Gateway) to reduce costs during development phase

---

### 7. Risk Assessment

#### Risk Matrix

| Risk | Impact Level | Probability |
| --- | --- | --- |
| Data drift | High | Medium |
| Budget overrun | Medium | Low |
| Poor model performance | High | Medium |
| API integration errors | Medium | Low |

#### Mitigation Strategies

- **Data drift:** Use SageMaker Model Monitor for early detection and alerts; retrain models periodically
- **Cost:** Set up budget alerts and use SageMaker Serverless Inference to reduce costs
- **Performance:** Use Automatic Model Tuning and test multiple algorithms; store old versions for rollback
- **Integration errors:** Thorough testing with API Gateway mock and CloudWatch logs

#### Contingency Plan

- If endpoint fails, switch to batch inference mode or fallback to previously approved model
- Use CloudFormation to restore pipeline in case of system failure

---

### 8. Expected Outcomes

#### Technical Improvements

- Heart disease prediction system with accuracy above 85%
- Integrated into the medical examination process via REST API
- ML process automated from preprocessing to deployment, enabling easy updates and maintenance

#### Long-term Value

- Platform can be extended to predict other diseases such as diabetes, cancer, or respiratory diseases
- System provides analytical data and models that can be reused for medical research
- Contributes to improving community healthcare quality and supporting doctors in decision-making