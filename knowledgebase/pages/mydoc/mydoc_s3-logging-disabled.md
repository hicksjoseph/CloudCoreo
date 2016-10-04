---
title: S3 bucket logging not enabled
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: S3 bucket logging has not been enabled for the affected resource.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_s3-logging-disabled.html
folder: mydoc
toc: false
---

### Details  
S3 bucket logging has not been enabled for the affected resource. Logging provides a way to get detailed access logs delivered to a bucket you choose. An access log record contains details about the request, such as the request type, the resources specified in the request worked, and the time and date the request was processed.  Server access logs are useful for many applications because they give bucket owners insight into the nature of requests made by clients not under their control. By default, Amazon S3 doesn't collect service access logs, but when you enable logging Amazon S3 delivers access logs to your bucket on an hourly basis.
[http://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html](http://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html)  

### Suggested Action  
In order to track requests for access to your bucket, you can enable access logging. Each access log record provides details about a single access request, such as the requester, bucket name, request time, request action, response status, and error code, if any. Access log information can be useful in security and access audits. It can also help you learn about your customer base and understand your Amazon S3 bill.
[http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html)
