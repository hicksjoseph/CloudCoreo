---
title: RDS not set to automatically upgrade
tags: [rds]
keywords: ""
last_updated: "September 17, 2016"
summary: RDS is not set to automatically upgrade minor versions on your database instance
published: true
sidebar: mydoc_sidebar
permalink: mydoc_rds-no-auto-minor-version-upgrade.html
folder: mydoc
toc: false
---

### Details  
RDS automatic minor version upgrades have been disabled for the affected DB Instance.

Amazon RDS allows you to control if and when the relational database software powering your DB Instance (i.e. MySQL) is upgraded to new versions supported by Amazon RDS. This provides you with the flexibility to maintain compatibility with specific MySQL versions, test new versions with your application before deploying in production, and perform version upgrades on your own terms and timelines. By default, your DB Instance will automatically be upgraded to new MySQL minor versions as they are supported by Amazon RDS. Since major version upgrades involve some compatibility risk, they will not occur automatically and must be initiated by you.

In the context of MySQL, version numbers are organized as follows:
MySQL version = X.Y.Z
X = Major version, Y = Release level, Z = Version number within release series.
From the Amazon RDS standpoint, a version change would be considered major if either major version or release level is being changed. Example: going from 5.1.X -> 5.5.X. A version change would be considered minor if the version number within the release is being changed. Example: going from 5.1.45 -> 5.1.49.  
[https://aws.amazon.com/rds/faqs/](https://aws.amazon.com/rds/faqs/)  

### Suggested Action  
Consider whether you would like AWS to automatically upgrade to minor versions on your database instance. Modify your settings to allow minor version upgrades if possible. If you wish to turn on automatic version upgrades, you can do so by setting the AutoMinorVersionUpgrade parameter to “true.”  
