---
title: Inactive user Access Key not rotated
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: User has inactive keys that have not been rotated in the last 90 days.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-inactive-key-no-rotation.html
folder: mydoc
toc: false
---

### Details  
As a security best practice, we recommend that you, an administrator, regularly rotate (change) the access keys for IAM users in your account. If your users have the necessary permissions, they can rotate their own access keys. For information about how to give your users permissions to rotate their own access keys, see Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys.

You can also apply a password policy to your account to require that all of your IAM users periodically rotate their passwords. You can choose how often they must do so. For more information, see [Setting an Account Password Policy for IAM Users](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html).

### Suggested Action  
If you regularly use the AWS access keys, we recommend that you also regularly rotate or delete them.  

Ideally, you should reduce or eliminate your use of AWS keys and reduce the number of keys used entirely. In many scenarios, you don't need a long-term access key that never expires (as you have with an IAM user). Instead, you can create IAM roles and generate temporary security credentials.  
[http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html)

How to rotate access keys for IAM users:  
[https://blogs.aws.amazon.com/security/post/Tx15CIT22V4J8RP/How-to-rotate-access-keys-for-IAM-users](https://blogs.aws.amazon.com/security/post/Tx15CIT22V4J8RP/How-to-rotate-access-keys-for-IAM-users)
