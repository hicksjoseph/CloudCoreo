---
title: TCP port is open
tags: [ec2, cis]
keywords: "TCP port open Security Groups, cis"
last_updated: "March 29, 2017"
summary: Important TCP port is open, potentially to the world.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_ec2-tcpportopen.html
folder: mydoc
toc: false
---

### Details  
In order to prevent unauthorized users from gaining privileged access to your virtual server and planting malware or stealing data, you need to make sure that important ports/protocols are only accessible by trusted IP addresses and networks. For example, as recommended by [Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 4.1 and 4.2, remote administration ports like 22 (SSH) and 3389 (RDP) should only allow access from your private network or bastion hosts, and not the entire Internet (which is specified in security groups as 0.0.0.0/0).  

In addition to remote administration ports 22 and 3389, there are several other ports that allow privileged or database access. Make sure you restrict these ports to IPs or subnets you trust, and don't allow public Internet access (0.0.0.0/0) to them. Here is a list of [some of the] common ports you should consider locking down: 
- 20/21 - FTP  
- 22 - SSH  
- 23 - Telnet  
- 1433 - MSSQL Server  
- 1434 - MSSQL Monitor  
- 1521 - Oracle database  
- 3389 - RDP  
- 3306 - MySQL  
- 3389 - Microsoft Terminal Server (RDP)
- 4333 - MSQL  
- 5432 - PostgreSQL
- 5500 - VNC RDP  
- 27017 - MongoDB  

[https://aws.amazon.com/articles/1233/](https://aws.amazon.com/articles/1233/)

Ports 20, 21, 22, 23 are checked to see if they are open at all (even privately), including being open to the world (0.0.0.0/0).  

Ports 1433, 1521, 27017, 3306, 3389, 5432 are checked to see if they are open to the world (0.0.0.0/0).

### Suggested Action   
Security Groups can be used to secure ports over TCP, UDP, and ICMP protocols. We recommend that you open only those ports that must be open for your service to operate. Consider deleting or modifying the affected security group.  
[https://aws.amazon.com/articles/1233/](https://aws.amazon.com/articles/1233/)

