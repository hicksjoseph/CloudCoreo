---
title: Redshift user activity logging disabled
tags: [redshift]
keywords: ""
last_updated: "September 17, 2016"
summary: Redshift user activity logging is disabled.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-no-user-logging.html
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
Enable Redshift user activity logging. "The user activity log is useful primarily for troubleshooting purposes. It tracks information about the types of queries that both the users and the system perform in the database. For the user activity log, you must also enable the enable_user_activity_logging database parameter. The enable_user_activity_logging parameter is disabled (false) by default, but you can set it to true to enable the user activity log."
[http://docs.aws.amazon.com/redshift/latest/mgmt/db-auditing.html](http://docs.aws.amazon.com/redshift/latest/mgmt/db-auditing.html)
