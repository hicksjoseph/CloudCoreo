---
title: ELB is using most recent Amazon SSL policy
tags: [elb]
keywords: ""
last_updated: "December 29, 2016"
summary: Elastic Load Balancing (ELB) SSL policy is current (most recent Amazon predefined SSL policy).
published: true
sidebar: mydoc_sidebar
permalink: mydoc_elb-current-ssl-policy.html
folder: mydoc
toc: false
---

### Details  
The affected Elastic Load Balancer (ELB) has a current SSL policy (most recent Amazon predefined SSL policy). This alert is an Inventory check and does not indicate that you have a problem with your ELB SSL policy.

SSL Negotiation Configurations for Classic Load Balancers (ELB SSL security policy)
Elastic Load Balancing uses an Secure Socket Layer (SSL) negotiation configuration, known as a security policy, to negotiate SSL connections between a client and the load balancer. A security policy is a combination of SSL protocols, SSL ciphers, and the Server Order Preference option. A security policy determines which ciphers and protocols are supported during SSL negotiations between a client and a load balancer.  

Elastic Load Balancing provides security policies that have predefined SSL negotiation configurations to use to negotiate SSL connections between clients and your load balancer. If you are using the HTTPS/SSL protocol for your listener, you can use one of the predefined security policies, or use your own custom security policy. If you create an HTTPS/SSL listener without associating a security policy, Elastic Load Balancing associates the current predefined security policy, ELBSecurityPolicy-2016-08, with your load balancer.  

The RSA- and DSA-based ciphers are specific to the signing algorithm used to create SSL certificate. Make sure to create an SSL certificate using the signing algorithm that is based on the ciphers that are enabled for your security policy.  
[http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-table.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-table.html)
[http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-ssl-security-policy.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-ssl-security-policy.html)
[http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/ssl-config-update.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/ssl-config-update.html)
[http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-options.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-options.html)

### Suggested Action
None. You are already using the most recent Amazon ELB SSL Policy.  
