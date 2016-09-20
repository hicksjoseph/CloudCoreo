---
title: Active root Access Key
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: Root user has an Access Key that is active
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-root-active-key.html
folder: mydoc
toc: false
---

### Details  
One of the best ways to protect your account is to not have an access key for your root account. Unless you must have a root access key (which is very rare), it is best not to generate one. Instead, the recommended best practice is to create one or more AWS Identity and Access Management (IAM) users, give them the necessary permissions, and use IAM users for everyday interaction with AWS.  

An access key is required in order to sign requests that you make using the AWS Command Line Tools, the AWS SDKs, or direct API calls. Anyone who has the access key for your root account has unrestricted access to all the resources in your account, including billing information. You cannot restrict the permissions for your root account.  
[http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#root-password](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#root-password)

### Suggested Action  
If you already have an access key for your account, we recommend that you find places in your applications where you are currently using that key (if any), replace the root access key with an IAM user access key, and then disable and remove the root access key.
[http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#root-password](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#root-password)  
[http://docs.aws.amazon.com/general/latest/gr/managing-aws-access-keys.html](http://docs.aws.amazon.com/general/latest/gr/managing-aws-access-keys.html)
