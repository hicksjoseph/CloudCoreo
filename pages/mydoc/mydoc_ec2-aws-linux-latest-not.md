---
title: EC2 instance not launched from latest Amazon Linux AMI
tags: [ec2]
keywords: ""
last_updated: "January 3, 2017"
summary: Alerts if an EC2 instance was not launched from the latest Amazon Linux AMI
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-amazon-linux-not-latest.html
folder: mydoc
toc: false
---

### Details  

Alerts if an EC2 instance was not launched from the latest Amazon Linux AMI

This alert checks for instances that were not launched from the latest Amazon Linux AMI. This alert matches the AWS instance_id against the list of Amazon Linux AMI IDs in the variable $AWS_LINUX_AMI in `audit-aws-ec2-aws-linux-check/config.yaml`. This list can be modified and updated by modifying the `config.yaml` file. If notified of a violation, it does not necessarily indicate that you have a problem with your EC2 instances.  

Read more about [EC2 Instances](https://aws.amazon.com/ec2/) and about [Amazon Linux AMIs](https://aws.amazon.com/amazon-linux-ami/) .  

### Suggested Action
This alert checks for instances that were not launched from the latest Amazon Linux AMI. If you run Amazon Linux, verify that you launch instances from the latest Amazon Linux AMIs. It does not necessarily indicate that you have a problem with your EC2 instances.  
