---
title: Security Group contains IP address
tags: [ec2]
keywords: ""
last_updated: "September 17, 2016"
summary: Security Group contains IP address
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-ip-address-whitelisted.html
folder: mydoc
toc: false
---

### Detail  
Security groups enable you to control traffic to your instance, including the kind of traffic that can reach your instance. For example, you can allow computers from only your home network to access your instance using SSH. If your instance is a web server, you can allow all IP addresses to access your instance via HTTP, so that external users can browse the content on your web server.  
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html)

Having a host IP address in a Security Group itself is not necessarily a problem, however, it might indicate improper access or temporary access that was never removed. For internal access between instances in an AWS region, it is best practice to add the other Security Group to the target Security Group to grant access for those instances. This alert checks for a /32 host address added to a Security Group (ip-address-whitelisted).  

### Suggested Action  
Review your security groups to ensure that the host ip address added is to allowed access. Decide who requires access to your instance; for example, a single host or a specific network that you trust. You can check the public IP address of your local computer using a service, (for example: http://checkip.amazonaws.com ).  
[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html)
