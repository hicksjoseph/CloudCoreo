---
title: Active user Access Key not rotated
tags:
keywords: ""
last_updated: "March 29, 2017"
summary: User has active keys that have not been rotated in the last 90 days.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-active-key-no-rotation.html
folder: mydoc
toc: false
---

### Details  
This rule checks for adherence to [Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 1.4, Ensure access keys are rotated every 90 days or less.  
[https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=18](https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=18)

As a security best practice, we recommend that you, an administrator, regularly rotate (change) the access keys for IAM users in your account. If your users have the necessary permissions, they can rotate their own access keys. For information about how to give your users permissions to rotate their own access keys, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_delegate-permissions_examples.html#creds-policies-credentials).  

You can also apply a password policy to your account to require that all of your IAM users periodically rotate their passwords,. You can choose how often they must do so. For more information, see [Setting an Account Password Policy for IAM Users](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html).  

### Suggested Action  
We recommend that you also regularly rotate user account keys. Ideally, you should reduce or eliminate your use of AWS keys and reduce the number of keys used entirely. In many scenarios, you don't need a long-term access key that never expires (as you have with an IAM user). Instead, you can create IAM roles and generate temporary security credentials.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access keys.html#Using_RotateAccessKey](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access keys.html#Using_RotateAccessKey)
[http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html)  

If you must use keys, rotate them regularly. You can create, modify, or view AWS keys [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey) .  

Also consider using [Amazon's Key Management Service](http://docs.aws.amazon.com/kms/latest/developerguide/overview.html) .
