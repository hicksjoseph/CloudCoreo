---
title: TCP port 1433 is open
tags:
keywords: "TCP 1433 TCP1433 Security Groups"
last_updated: "September 14, 2016"
summary: Important TCP port is open and / or open to the world.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-TCP-1433.html
folder: mydoc
toc: false
---

### Description
"In order to prevent [unauthorized users] from gaining privileged access to your virtual server and $

Here is a list of [some of the] common ports you should consider locking down: 20/21 - FTP, 22 - SSH$
[https://aws.amazon.com/articles/1233/](https://aws.amazon.com/articles/1233/)

Ports 20, 21, 22, 23 are checked to see if they are open at all (even privately), including being op$
Ports 1433, 1521, 27017, 3306, 3389, 5432 are checked to see if they are open to the world (0.0.0.0/$

### Suggested action
Security Groups can be used to secure ports over TCP, UDP, and ICMP protocols. We recommend that you$
[https://aws.amazon.com/articles/1233/](https://aws.amazon.com/articles/1233/)
