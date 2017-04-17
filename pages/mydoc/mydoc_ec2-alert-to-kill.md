---
title: EC2 instance - Alert to Kill
tags: [ec2]
keywords: ""
last_updated: "December 30, 2016"
summary: EC2 - Alert to Kill - Checks for instances with improper or no tags then kills any matching instances within the first 5 minutes.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-alert-to-kill.html
folder: mydoc
toc: false
---

### Details  
This alert checks for instances with improper (or no) tags then generates a kill list / script to kill any matching instances in the specified region. This alert matches instance tags with tags that you specify and does not indicate that you have a problem with your EC2 instances. This alert has been nicknamed: "Alert to Kill".  

A number of variables can be set / modified via the CloudCoreo WebUI or via the `<repository directory>/config.yaml` file.  
* Matching tags can be specified / modified  
* Multiple tags can be combined together for a more accurate match  
* The frequency of how often EC2 instances are checked can be specified / modified  
* You can specify / modify the instance age after which the instance will not be killed  

Read more about [EC2 Instances](https://aws.amazon.com/ec2/) .

### Suggested Action
None. This alert matches instance tags with tags that you specify and does not indicate that you have a problem with your EC2 instances.  
