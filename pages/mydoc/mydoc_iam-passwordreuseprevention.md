---
title: Users can reuse old passwords
tags:
keywords: ""
last_updated: "September 17, 2016"
summary: The current password policy doesn't prevent users from reusing their old passwords.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-passwordreuseprevention.html
folder: mydoc
toc: false
---

### Details  
You should set a password policy on your AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords. You can use a password policy to do these things:  
* Set a minimum password length.  
* Require specific character types, including uppercase letters, lowercase letters, numbers, and non-alphanumeric characters.  
* Allow all IAM users to change their own passwords.  
* Require IAM users to change their password after a specified period of time (enable password expiration).  
* Prevent IAM users from reusing previous passwords.  
* Force IAM users to contact an account administrator when the user has allowed his or her password to expire.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html)  

### Suggested Action  
Configure a strong password policy for your users so that they can't reuse old passwords.  
If you allow users to change their own passwords, require that they create strong passwords, that they rotate their passwords periodically, and don't reuse old passwords. On the Account Settings page of the IAM console, you can create a password policy for your account. You can use the password policy to define password requirements, such as minimum length, whether it requires non-alphabetic characters, how frequently it must be rotated, and so on.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#configure-strong-password-policy](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#configure-strong-password-policy)
