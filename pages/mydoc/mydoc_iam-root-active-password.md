---
title: Root user has active password
tags: [iam]
keywords: ""
last_updated: "September 17, 2016"
summary: Root user has been logging in with a password.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-root-active-password.html
folder: mydoc
toc: false
---

### Details  
All AWS accounts have root account credentials (that is, the credentials of the account owner). These credentials allow full access to all resources in the account. Because you can't restrict permissions for root account credentials, we recommend that you delete your root access keys and then create AWS Identity and Access Management (IAM) user credentials for everyday interaction with AWS.  
[http://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html](http://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html)  

By creating individual IAM users for people accessing your account, you can give each IAM user a unique set of security credentials. You can also grant different permissions to each IAM user. If necessary, you can change or revoke an IAM user's permissions any time. If you give out your AWS root credentials, it can be difficult to revoke them, and it is impossible to restrict their permissions.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)  

With IAM, you can securely control access to AWS services and resources for users in your AWS account. For example, if you require administrator-level permissions, you can create an IAM user, grant that user full access, and then use those credentials to interact with AWS. If you need to modify or revoke your permissions, you can delete or modify the policies that are associated with that IAM user. If you have multiple users that require access to your AWS account, you can create unique credentials for each user and define who has access to which resources. You don't need to share credentials. For example, you can create IAM users with read-only access to resources in your AWS account and distribute those credentials to your users.  
[http://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html](http://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html)  

### Suggested Action  
Don't use your AWS root account credentials to access AWS, and don't give your credentials to anyone else. Instead, create individual users for anyone who needs access to your AWS account. Create an IAM user for yourself as well, give that user administrative privileges, and use that IAM user for all your work. Re-set your root account password, don't log in to your root account, and secure root account password in a safe place.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_change-root.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_change-root.html)
