---
title: Passwords not set to expire
tags:
keywords: ""
last_updated: "March 29, 2017"
summary: The current password policy doesn't require users to regularly change their passwords. User passwords are set to never expire.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-expirepasswords.html
folder: mydoc
toc: false
---

### Details  
This rule checks for adherence to [Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 1.11, Ensure IAM password policy expires passwords within 90 days or less.  
[https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=32](https://benchmarks.cisecurity.org/tools2/amazon/CIS_Amazon_Web_Services_Foundations_Benchmark_v1.1.0.pdf#page=32)  

You should set a password policy on your AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords. You can use a password policy to do these things:
- Set a minimum password length.
- Require specific character types, including uppercase letters, lowercase letters, numbers, and non-alphanumeric characters.
- Allow all IAM users to change their own passwords.
- Require IAM users to change their password after a specified period of time (enable password expiration).
- Prevent IAM users from reusing previous passwords.
- Force IAM users to contact an account administrator when the user has allowed his or her password to expire.
[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html)

### Suggested Action
Configure a strong password policy for your users so that passwords expire such that users must change their passwords periodically.  

If you allow users to change their own passwords, require that they create strong passwords and that they rotate their passwords periodically. On the Account Settings page of the IAM console, you can create a password policy for your account. You can use the password policy to define password requirements, such as minimum length, whether it requires non-alphabetic characters, how frequently it must be rotated, and so on.
[http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#configure-strong-password-policy](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#configure-strong-password-policy)
