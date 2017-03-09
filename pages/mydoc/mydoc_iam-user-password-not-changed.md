---
title: Active user passwords not changed recently
tags:
keywords: ""
last_updated: "March 9, 2017"
summary: User has active password that have not been changed within specified time.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-user-password-not-changed.html
folder: mydoc
toc: false
---

### Details  
As a security best practice, we recommend that all users, regularly change their IAM user console access password. Regularly changing passwords helps to limit how long a stolen password is useful to an attacker or how long they potentially have access to your account.  

You can also apply a password policy to your account to require that all of your IAM users periodically rotate their passwords,. You can choose how often they must do so. For more information, see [Setting an Account Password Policy for IAM Users](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html).  

### Suggested Action  
We recommend that you require your users to regularly change their passwords. Ideally, on accounts that require console access, you should implement Multi Factor Authentication (MFA). In some scenarios, you don't need a user to have console access at all. Instead, you can create IAM roles and generate temporary security credentials as needed.  

[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_user-change-own.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_user-change-own.html)
[http://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPracticesAndUseCases.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPracticesAndUseCases.html)  
