---
title: Redshift automatic major version upgrades not enabled.
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: Redshift automatic major version upgrades not enabled.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-no-version-upgrade.html
folder: mydoc
toc: false
---

### Details  
Amazon Redshift provides a setting, Allow Version Upgrade, to specify whether to automatically upgrade the Amazon Redshift engine in your cluster if a new version of the engine becomes available. This setting does not affect the database version upgrades, which are applied during the maintenance window that you specify for your cluster. Amazon Redshift engine upgrades are major version upgrades, and Amazon Redshift database upgrades are minor version upgrades. You can disable automatic version upgrades for major versions only.  

### Suggested Action  
Enable major version upgrades by setting Allow Version Upgrade to true. This will allow major version upgrades to be applied automatically to the cluster during the maintenance window.  
[http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html)
