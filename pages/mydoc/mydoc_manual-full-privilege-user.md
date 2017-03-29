---
title: Manually check if any IAM policies allow full administrative privileges on the account
tags:
keywords: "manual-check, cis"
last_updated: “March 28, 2017"
summary:  Using the AWS CLI, manually check if any IAM policies allow full administrative privileges on the account
published: true
sidebar: mydoc_sidebar
permalink: mydoc_manual-full-privilege-user.html
folder: mydoc
toc: false
---

### Details  
[Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 1.24 is to Ensure IAM policies that allow full "*:*" administrative privileges are not created. [https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=69](https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=69) 

This is a check that must be performed manually as there are either no appropriate API calls or it may require an account-specific judgement call.
