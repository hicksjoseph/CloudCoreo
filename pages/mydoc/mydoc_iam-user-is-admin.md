---
title: IAM user with administrator access
tags: [iam]
keywords: "iam, permissions"
last_updated: “November 4, 2017"
summary:  Checks for users that have administrator level access, no matter how the access is/was granted.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-user-is-admin.html
folder: mydoc
toc: false
---

### Details  
This rule checks for the existence of any IAM user with administrator-level access, regardless of the method by which those permissions have been granted. This is in line with the [best practice recommendation](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#use-access-levels-to-review-permissions) that IAM user permissions are restricted as much as possible. 
