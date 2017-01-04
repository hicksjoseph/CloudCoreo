---
title: Unused EC2 Security Group
tags:
keywords: ""
last_updated: "January 3, 2017"
summary: EC2 Security Group is unused 
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-unused-security-group.html
folder: mydoc
toc: false
---

### Detail  
Security groups enable you to control traffic to your instance, including the kind of traffic that can reach your instance. For example, you can allow computers from only your home network to access your instance using SSH. If your instance is a web server, you can allow all IP addresses to access your instance via HTTP, so that external users can browse the content on your web server.  
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html)

The affected Security Group is unused since it is not attached to any EC2 instances or Elastic Load Balancers (ELBs). Having an unused Security Group is not necessarily a problem, however, it might indicate improper or temporary access that was never removed. For internal access between instances in an AWS region, it is best practice to add the other Security Group to the target Security Group to grant access for those instances.  

### Suggested Action  
Review your security groups to ensure that you don't have unused or unneeded security groups. Decide who requires access to your instance; for example, a single host or a specific network that you trust.  
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html)
