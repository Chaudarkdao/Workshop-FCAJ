---
title: "Blog 3"
date: 2026-07-29
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# $200 and 13 Decisions That Helped Me Avoid "Bill Shock" When Doing an AWS Project

When I started the project with a $200 budget, I thought it was a generous amount. But AWS has its own way of teaching you humility. One forgotten endpoint, one bucket without lifecycle, one HPO job running 30 trials instead of 6 — each small mistake compounds into an unexpected bill.

This article shares **13 decisions** that helped me complete an ML project on AWS with an actual cost of only **~$80-110** for the entire 8 weeks, instead of over $113 without optimization. From choosing the right instance, leveraging S3 Lifecycle, limiting HPO, to avoiding NAT Gateway — all are hard-earned lessons I want to share with those working on AWS projects with limited budgets.

---

## INTRODUCTION: $200 SOUNDS LIKE A LOT — UNTIL YOU DO THE MATH

When I first read the brief, $200 seemed like a generous budget. Then I sat down and did some simple math:

- 8 weeks × 2 sessions/week × 4 hours/session = **64 hours** working with AWS
- One ml.t2.medium endpoint running 24/7: approximately **$35/month**
- One HPO job training 6 trials × approximately 20 minutes/trial on ml.m5.large: approximately **$3/run**
- S3 storage accumulating data, logs, artifacts over 8 weeks: approximately **$5–8**
- CloudWatch, Lambda, API Gateway, Data Capture: approximately **$5–10**

Adding it up still seemed manageable. But AWS costs don't scale linearly with effort — they scale with **carelessness**.

One endpoint left running all week instead of shutting down after demo.  
One S3 bucket without lifecycle rules.  
One HPO job running 30 trials instead of 6.  

Each small mistake compounds into an unexpected bill.

I learned that:  
> *"On the cloud, shutting down after use is a more important skill than running correctly or incorrectly."*

Here are **13 decisions** that helped me complete the project with a $200 budget without worrying about the bill.

---

## DECISIONS 1–4: COMPUTE

### Decision #1: Choose ml.t3.medium as the default instance

Instead of using ml.m5.large, I tried training XGBoost with approximately 7,000 rows of data on ml.t3.medium.

**Results:**
- Training took approximately **4 minutes**
- AUC reached **0.86**

=> For small datasets (<100K rows), t3.medium is more than sufficient.

**Lesson Learned:**  
Don't upgrade instances just to "be safe." **Benchmark first.**

**Cost:**
- ml.t3.medium: approximately **$0.05/hour**
- ml.m5.large: approximately **$0.134/hour**

---

### Decision #2: Don't use GPU

The project didn't require a GPU.  
An idle ml.g4dn.xlarge notebook would have cost approximately **$0.736/hour**.

**Lesson Learned:**  
GPU is only worth the cost when the model or dataset is large enough.

---

### Decision #3: Use only one Region

I chose **ap-southeast-1 (Singapore)**.  
Not for performance, but to avoid duplicating IAM Roles, S3 Buckets, Security Groups...

**Lesson Learned:**  
Student projects don't need multi-region.

---

### Decision #4: Shut down the Endpoint immediately after Demo

This was the biggest money-saving decision.

- If the endpoint runs 24/7 for 8 weeks: **≈$35**
- If only turned on during demos: **≈$5**

**Savings: approximately $30.**

**Lesson Learned:**  
An existing endpoint is already costing you money, even without any requests.

---

## DECISIONS 5–8: DATA & STORAGE

### Decision #5: Use S3 Lifecycle Rules

Logs, artifacts, and models will be automatically deleted after **30 days**.

**Lesson Learned:**  
Lifecycle is nearly free but saves quite a bit on storage costs.

**Savings: approximately $3–5.**

---

### Decision #6: Preprocess the dataset only once

Instead of preprocessing data every training run, I saved the processed dataset in the `processed/` folder.  
Subsequent runs just read it directly.

**Savings: approximately $1–2.**

---

### Decision #7: Don't retrain for very small improvements

An AUC improvement from 0.850 to 0.855 may not deliver real-world value.

**Lesson Learned:**  
*"Good enough"* is also an engineering decision.

**Savings: approximately $3–5.**

---

### Decision #8: Tag all Resources

Every resource was tagged with:
- `Project`
- `Owner`
- `Environment`
- `AutoDelete=true`

After the project ended, I just ran a cleanup script.

**Lesson Learned:**  
Without tags, it's very easy to forget resources and keep getting charged.

---

## DECISIONS 9–11: PIPELINE & TRAINING

### Decision #9: Limit HPO

- `max_parallel_jobs = 1`
- `max_jobs = 6`

No need to increase the number of trials.  
The entire HPO cost only about **$0.6**.

---

### Decision #10: Run a cleanup script every week

The script will:
- Delete old endpoints
- Clean up CloudWatch Logs
- Remove unnecessary resources

**Lesson Learned:**  
CloudWatch doesn't automatically clean up logs.

---

### Decision #11: Don't use Notebook Instance for training

I only used **SageMaker Training Jobs**.  
The instance terminates automatically when training completes.

**Lesson Learned:**  
Notebooks and Training Jobs have completely different pricing models.

---

## DECISIONS 12–13: IAM & NETWORK

### Decision #12: Never use AdministratorAccess

IAM only grants the minimum required permissions.

**Lesson Learned:**  
Least Privilege is both secure and prevents costly mistakes.

---

### Decision #13: Don't use NAT Gateway

NAT Gateway can cost approximately **$30/month**.  
Replace with:
- Gateway Endpoint
- Interface Endpoint
- Public Internet (when appropriate)

**Lesson Learned:**  
Don't enable NAT Gateway unless you really need it.

---

## COST SUMMARY (ESTIMATES)

| Item | Without Optimization | With Optimization |
|------|----------------------|-------------------|
| Endpoint | 35 USD → | 5 USD |
| S3 | 10 USD → | 5 USD |
| HPO | 3 USD → | 0.6 USD |
| Training | 10 USD → | 3 USD |
| NAT Gateway | 30 USD → | 0 USD |
| CloudWatch | 5 USD → | 1 USD |
| Misc | 10 USD → | 2 USD |
| **Total** | **≈113 USD** | **≈26.6 USD** |

**My actual project cost ranged approximately $80–110 for the entire 8 weeks**, still well under the $200 budget with plenty of buffer.

---

## PRE-RESOURCE CREATION CHECKLIST

☐ Is this resource really necessary?  
☐ Can I use t3.medium instead of m5?  
☐ Does the resource auto-delete?  
☐ Have I added Project and AutoDelete tags?  
☐ Is IAM scoped correctly?  
☐ Does the Endpoint or Notebook have a shutdown schedule?  
☐ Does S3 have Lifecycle Rules configured?  
☐ If I forget to shut it down, how much will it cost per week?

---

## CONCLUSION

Before, I thought using AWS was simply about building and then cleaning up.  
After this project, I realized:  

> *You have to think about cleanup from the very beginning of the design phase.*

A budget cap isn't a limitation.  
It forces you to design a better pipeline:
- With lifecycle
- With tagging
- With cleanup
- With clear IAM

These practices remain valuable even when your budget increases tenfold.

If you're working on an AWS project with a limited budget, don't see it as a disadvantage.  
See it as an opportunity to learn how to design systems **the right way from the start**.

What AWS project are you working on? Have you ever experienced "bill shock"? Share your experience in the comments below! 🚀

---

### Image
![Blog post image](../../images/3-BlogsPosted/post3/p3.jpg)
### Link
This post has not been approved yet