---
title: Security group contains a port range
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: Security group contains a port range rather than specifying individual ports.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-ports-range.html
folder: mydoc
toc: false
---

### Details  
A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. For each security group, you add rules that control the inbound traffic to instances, and a separate set of rules that control the outbound traffic. For each security group, you add rules that control the inbound traffic to instances, and a separate set of rules that control the outbound traffic.
The following are the basic parts of a security group rule:
(Inbound rules only) The source of the traffic (CIDR range or security group) and the destination port or port range.
(Outbound rules only) The destination for the traffic (CIDR range or security group) and the destination port or port range.
Any protocol that has a standard protocol number."
http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_SecurityGroups.html

It is the best practice to specify specific ports versus a range of ports. When specifying a range of ports, there is the potential to open more ports than is necessary for your application, which can introduce security vulnerabilities into your environment.

### Suggested Action  
When creating or modifying your security groups, only add rules to your Security group that specify individual ports and don't use port ranges unless they are required.
