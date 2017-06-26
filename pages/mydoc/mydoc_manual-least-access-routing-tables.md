---
title: Manually review routing tables for VPC peering to ensure they are "least access"
tags:
keywords: "manual-check, cis"
last_updated: “March 28, 2017"
summary:  Using the AWS CLI, manually review routing tables for VPC peering to ensure they are "least access"
published: true
sidebar: mydoc_sidebar
permalink: mydoc_manual-least-access-routing-tables.html
folder: mydoc
toc: false
---

### Details  
[Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 4.5 is to Ensure routing tables for VPC peering are "least access." [https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=141](https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=141) 

This is a check that must be performed manually as there are either no appropriate API calls or it may require an account-specific judgement call.
