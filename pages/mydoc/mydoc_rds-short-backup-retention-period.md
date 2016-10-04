---
title: RDS short backup retention period
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: The affected RDS database has a short backup retention period (less than 30 days).
published: true
sidebar: mydoc_sidebar
permalink: mydoc_rds-short-backup-retention-period.html
folder: mydoc
toc: false
---

### Details  
Amazon RDS creates a storage volume snapshot of your DB instance, backing up the entire DB instance and not just individual databases. Automated backups automatically back up your DB instance during a specific, user-definable backup window, and keeps the backups for a limited, user-specified period of time (called the backup retention period); you can later recover your database to any point in time during that retention period. You can set the backup retention period when you create a DB instance.  If you don't set the backup retention period, Amazon RDS uses a default period retention period of one day. You can modify the backup retention period; valid values are 0 (for no backup retention) to a maximum of 35 days.  

### Suggested Action  
"Modify the backup retention period to increase it to greater than 30 days."  
[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.BackingUpAndRestoringAmazonRDSInstances.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.BackingUpAndRestoringAmazonRDSInstances.html)
[Working with Automated Backups](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html#USER_WorkingWithAutomatedBackups.Enabling)
