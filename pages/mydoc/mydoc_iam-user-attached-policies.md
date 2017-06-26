---
title: Account using inline policies
tags: [iam, cis]
keywords: ""
last_updated: "March 29, 2017"
summary: User account is using custom inline policies versus using IAM group managed policies.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-user-attached-policies.html
folder: mydoc
toc: false
---

### Details  
This rule checks for adherence to [Center for Internet Security (CIS)](https://www.cisecurity.org/) Recommendation 1.16, Ensure IAM policies are attached only to groups or roles.  
[https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=42](https://d0.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf#page=42)  

Different types of policies are for different use cases. In most cases, we recommend that you use managed policies instead of inline policies. Managed policies provide the following features: Reusability, Central change management, Versioning and rolling back, and Delegating permissions management."
[http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#choosing-managed-or-inline](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#choosing-managed-or-inline)

### Suggested Action  
Switch all inline policies to IAM Managed Policies then assign policies to identities (users, groups, and roles).

[Creating a new IAMs policy](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html)

### Additional information  
Using IAM, you apply permissions to IAM users, groups, and roles (which are referred to as principal entities) by creating policies. You can create two types of IAM, or identity-based policies:  

Managed policies – Standalone policies that you can attach to multiple users, groups, and roles in your AWS account. Managed policies apply only to identities (users, groups, and roles) - not resources. You can use two types of managed policies:
AWS managed policies – Managed policies that are created and managed by AWS. If you are new to using policies, we recommend that you start by using AWS managed policies.
Customer managed policies – Managed policies that you create and manage in your AWS account. Using customer managed policies, you have more precise control over your policies than when using AWS managed policies.  

Inline policies – Policies that you create and manage, and that are embedded directly into a single user, group, or role. Resource-based policies are another form of inline policy. Resource-based policies are not discussed here. For more information about resource-based policies, see Identity-Based (IAM) Permissions and Resource-Based Permissions.  
[http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)  

[Choosing Managed or Inline Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#choosing-managed-or-inline)
