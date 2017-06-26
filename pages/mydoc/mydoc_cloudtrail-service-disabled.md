---
title: Cloudtrail Service is disabled
tags: [cloudtrail, cis]
keywords: "cloudtrail, cis"
last_updated: “December 22, 2016"
summary: CloudTrail logging is not enabled for this region. It should be enabled.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_cloudtrail-service-disabled.html
folder: mydoc
toc: false
---

### Details  
This rule checks for adherence to [Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 2.1, Ensure CloudTrail is enabled in all regions.  
[https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=71](https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=71)  

CloudTrail logging is not enabled for this region. It should be enabled.

AWS CloudTrail is a web service that records AWS API calls for your account and delivers log files to you. The recorded information includes the identity of the API caller, the time of the API call, the source IP address of the API caller, the request parameters, and the response elements returned by the AWS service.

With CloudTrail, you can get a history of AWS API calls for your account, including API calls made via the AWS Management Console, AWS SDKs, command line tools, and higher-level AWS services (such as AWS CloudFormation). The AWS API call history produced by CloudTrail enables security analysis, resource change tracking, and compliance auditing.  
[https://aws.amazon.com/cloudtrail/](https://aws.amazon.com/cloudtrail/)

### Suggested Action  
Enable CloudTrail logs for each active region.  
[http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)

