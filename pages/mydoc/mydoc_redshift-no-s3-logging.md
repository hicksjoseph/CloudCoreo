---
title: Redshift S3 logging disabled
tags: [redshift, nist]
keywords: "redshift, nist, logging"
last_updated: "November 5th, 2017"
summary: Redshift S3 logging is disabled.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-no-s3-logging.html
folder: mydoc
toc: false
---

### Details  
Amazon Redshift logs information about connections and user activities in your database. These logs help you to monitor the database for security and troubleshooting purposes, which is a process often referred to as database auditing. The logs are stored in the Amazon Simple Storage Service (Amazon S3) buckets for convenient access with data security features for users who are responsible for monitoring activities in the database.

Amazon Redshift logs information in the following log files:  
* Connection log — logs authentication attempts, and connections and disconnections.  
* User log — logs information about changes to database user definitions.  
* User activity log — logs each query before it is run on the database.  

### Suggested Action  
Enable Redshift S3 logging.
[http://docs.aws.amazon.com/redshift/latest/mgmt/db-auditing.html](http://docs.aws.amazon.com/redshift/latest/mgmt/db-auditing.html)
