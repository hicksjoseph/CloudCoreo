---
title: Global Cloudtrail is not enabled
tags:
keywords: ""
last_updated: “December 27, 2016"
summary: Global CloudTrail logging is not enabled. It should be enabled.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_cloudtrail-trail-with-global.html
folder: mydoc
toc: false
---

### Details  
Global CloudTrail logging is not enabled. It should be enabled.

AWS CloudTrail is a web service that records AWS API calls for your account and delivers log files to you. The recorded information includes the identity of the API caller, the time of the API call, the source IP address of the API caller, the request parameters, and the response elements returned by the AWS service.

With CloudTrail, you can get a history of AWS API calls for your account, including API calls made via the AWS Management Console, AWS SDKs, command line tools, and higher-level AWS services (such as AWS CloudFormation). The AWS API call history produced by CloudTrail enables security analysis, resource change tracking, and compliance auditing.  

A trail can be applied to all regions or a single region. As a best practice, create a trail that applies to all regions. If you have a single region trail, you should enable the Include global services option. A trail that applies to all regions has the following advantages:  

* The configuration settings for the trail apply consistently across all regions.  
* You receive log files from all regions in a single S3 bucket and optionally in a CloudWatch Logs log group.  
* If you configured an Amazon SNS topic for the trail, SNS notifications about log file deliveries in all regions are sent to that single SNS topic.  
* You manage trail configuration for all regions from one location.  
* You immediately receive events from a new region. When a new region launches, CloudTrail automatically creates a trail for you in the new region * with the same settings as your original trail.  
* You can create trails in regions that you don't use often to monitor for unusual activity.  

For most services, events are sent to the region where the action happened. For global services such as IAM, AWS STS, and Amazon CloudFront, events are delivered to any trail that has the Include global services option enabled.  

[https://aws.amazon.com/cloudtrail/](https://aws.amazon.com/cloudtrail/)
[https://aws.amazon.com/cloudtrail/faqs/](https://aws.amazon.com/cloudtrail/faqs/)
http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html

### Suggested Action  
Enable CloudTrail logs for each active region.  
[http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)

