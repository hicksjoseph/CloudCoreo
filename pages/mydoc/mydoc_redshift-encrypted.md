---
title: Redshift cluster data is not encrypted at rest
tags: [redshift]
keywords: ""
last_updated: "September 17, 2016"
summary: Redshift cluster data in the affected cluster is not encrypted at rest.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-encrypted.html
folder: mydoc
toc: false
---

### Details  
In Amazon Redshift, you can enable database encryption for your clusters to help protect data at rest. When you enable encryption for a cluster, the data blocks and system metadata are encrypted for the cluster and its snapshots. Redshift cluster data in the affected cluster is not encrypted at rest.

### Suggested Action  
Encryption is an optional, immutable setting of a cluster. To encrypt the data in all your user-created tables, you can enable cluster encryption when you launch the cluster. If you want to go from an encrypted cluster to an unencrypted cluster or the other way around, you must unload your data from the existing cluster and reload it in a new cluster with the chosen encryption setting.  

Though encryption is an optional setting in Amazon Redshift, we recommend enabling it for clusters that contain sensitive data. Additionally, you might be required to use encryption depending on the guidelines or regulations that govern your data. For example, the Payment Card Industry Data Security Standard (PCI DSS), the Sarbanes-Oxley Act (SOX), the Health Insurance Portability and Accountability Act (HIPAA), and other such regulations provide guidelines for handling specific types of data.  
[http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html)
