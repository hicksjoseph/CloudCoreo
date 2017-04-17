---
title: Redshift cluster is publicly accessible
tags: [redshift]
keywords: ""
last_updated: "September 17, 2016"
summary: The affected Redshift cluster is publicly accessible to the world.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-publicly-accessible.html
folder: mydoc
toc: false
---

### Details  
Redshift clusters deployed within a VPC can be accessed from the Internet or from EC2 Instances outside the VPC via VPN or bastion hosts that you can launch in your public subnet, or using Amazon Redshift's Publicly Accessible option. To use public connectivity, simply create your Redshift clusters with the Publicly Accessible option set to yes. With Publicly Accessible active, your Redshift clusters within a VPC will be fully accessible outside your VPC." If you do not want your Redshift clusters accessible from the Internet or outside your VPC, disable the Redshift Publicly Accessible option. If your AWS account allows you to create EC2-Classic clusters, the default option for Publicly Accessible is no, otherwise the default is yes.  
[http://docs.aws.amazon.com/redshift/latest/mgmt/getting-started-cluster-in-vpc.html](http://docs.aws.amazon.com/redshift/latest/mgmt/getting-started-cluster-in-vpc.html)

### Suggested Action  
Consider whether the affected Redshift cluster should be publicly accessible to the world. If not, modify the option which enables your Redshift cluster to become publicly accessible and/or configure Security Groups for Redshift.
[http://docs.aws.amazon.com/redshift/latest/mgmt/getting-started-cluster-in-vpc.html](http://docs.aws.amazon.com/redshift/latest/mgmt/getting-started-cluster-in-vpc.html)
