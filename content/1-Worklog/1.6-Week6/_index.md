---
title: "Week 6 Worklog"
date: 2026-07-25
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Connect and get familiar with members of First Cloud AI Journey.
* Understand basic AWS services, how to use console & CLI.

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Package and register model to SageMaker Model Registry <br> - Set up model versioning | 20/07/2026   | 20/07/2026      |
| 3   | - Deploy model to SageMaker Endpoint <br> - Integrate API Gateway + Lambda to expose REST API | 21/07/2026   | 21/07/2026      | 
| 4   | - Set up monitoring with SageMaker Model Monitor and CloudWatch <br> - Detect data drift | 22/07/2026   | 22/07/2026      |
| 5   | - Automate the entire pipeline with SageMaker Pipelines | 23/07/2026   | 23/07/2026      |
| 6   | - Finalize, Compile, Write report | 24/07/2026   | 24/07/2026      |

### Week 6 Achievements:

* Package and register model to SageMaker Model Registry:
  * Successfully packaged the selected model as a model artifact (model.tar.gz).
  * Registered the model to SageMaker Model Registry for centralized management.
  * Set up model versioning to track different versions of the model.
  * Assigned metadata and tags to the model for easy retrieval and management.

* Deploy model to SageMaker Endpoint:
  * Successfully created a SageMaker Endpoint for real-time inference.
  * Configured the appropriate instance type based on performance and cost requirements.
  * Tested the endpoint with sample data to ensure accurate operation.

* Integrate API Gateway + Lambda to expose REST API:
  * Built and deployed an AWS Lambda function to handle requests from clients.
  * Integrated Lambda with SageMaker Endpoint to invoke model inference.
  * Created a REST API on API Gateway to expose the endpoint externally.
  * Configured CORS, authentication, and necessary security settings.
  * Tested the API with tools such as Postman or curl.

* Set up monitoring with SageMaker Model Monitor and CloudWatch:
  * Configured SageMaker Model Monitor to track prediction quality.
  * Set up data drift detection to identify changes in input data distribution.
  * Created CloudWatch Alarms to alert when anomalies occur.
  * Built a monitoring dashboard to track important metrics.

* Automate the entire pipeline with SageMaker Pipelines:
  * Built an automated pipeline for the Machine Learning process from preprocessing to deployment.
  * Integrated steps: data loading, preprocessing, training, evaluation, model registration.
  * Configured pipeline triggers to automatically run when new data is available.

* Finalize and compile the project:
  * Wrote a summary report of the project implementation process.
  * Compiled the results achieved, lessons learned, and future development directions.
  * Prepared user documentation and system operation guides.
  * Completed all tasks on schedule.