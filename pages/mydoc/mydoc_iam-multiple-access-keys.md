---
title: Account has multiple active access keys
tags: [iam]
keywords: ""
last_updated: "September 17, 2016"
summary: The affected account has multiple active AWS access keys.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-multiple-access-keys.html
folder: mydoc
toc: false
---

### Details  
You use different types of security credentials depending on how you interact with AWS. For example, you use a user name and password to sign in to the AWS Management Console. You use access keys to make programmatic calls to AWS API actions. For security reasons, AWS doesn't allow you to retrieve your passwords or secret access keys and does not store the private keys that are part of a key pair. However, you can create new credentials and then disable or delete the old credentials. Access keys consist of an access key ID and a secret access key. You use access keys to sign programmatic requests that you make to AWS if you use the AWS SDKs, REST, or Query APIs. You can have a maximum of two access keys (active or inactive) at a time.  

However, having multiple access keys may lead to increased complexity or security risks involved in tracking and securing these keys.  
[http://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html](http://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html)

### Suggested Action  
Ideally, you should reduce or eliminate your use of AWS keys and reduce the number of keys used entirely. In many scenarios, you don't need a long-term access key that never expires (as you have with an IAM user). Instead, you can create IAM roles and generate temporary security credentials.  
[http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html)  

If you must use keys, rotate them regularly. You can create, modify, or view AWS keys [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey) .
