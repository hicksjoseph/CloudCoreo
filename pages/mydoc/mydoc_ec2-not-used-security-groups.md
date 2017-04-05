---
title: EC2 security group not used
tags:
keywords: ""
last_updated: "April 5, 2017"
summary: EC2 security group is not being used
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-not-used-security-groups.html
folder: mydoc
toc: false
---

### Details  
EC2 security groups have been found that are not being used. A security group acts as a virtual firewall that controls the traffic for one or more instances. Unused security groups can create an attack vulnerability, and it's recommended to remove any orphan security groups that an no longer being used.  

Read more about [EC2 Security Groups](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html).

### Suggested Action
Remove the unused security groups.
