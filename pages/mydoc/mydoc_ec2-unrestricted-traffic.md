---
title: Security group allows unrestricted traffic
tags: [ec2]
keywords: ""
last_updated: "September 17, 2016"
summary: All IP addresses are allowed to access resources in the affected security group.                                                     
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-unrestricted-traffic.html
folder: mydoc
toc: false
---

### Details  
"A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group. When AWS decides whether to allow traffic to reach an instance, it evaluates all the rules from all of the security groups that are associated with that instance."
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)

If you enable 0.0.0.0/0 in a security group, you enable all IP addresses to access your instance on the specified port (or perhaps any port). This might be acceptable for a short time in a test environment or for certain specific circumstances, but it's generally unsafe for production environments.

### Suggested Action  
The best practice in production is to restrict access to the minimum specific set of IP address or ports necessary. Review your Security Groups against your real world requirements and change them as necessary. Learn more about how to edit and delete rules from your Security Groups:  
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#deleting-security-group-rule](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#deleting-security-group-rule)
