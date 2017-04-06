---
title: Multi-Factor Authentication not enabled
tags: [iam]
keywords: ""
last_updated: "September 17, 2016"
summary: Affected user does not have Multi-Factor Authentication enabled on their account
published: true
sidebar: mydoc_sidebar
permalink: mydoc_iam-no-mfa.html
folder: mydoc
toc: false
---

### Details
Multi-Factor Authentication (MFA) is a simple best practice that adds an extra layer of protection on top of your user name and password. With MFA enabled, when a user signs in, they will be prompted for their user name and password (the first factor—what they know), as well as for an authentication code from their MFA device (the second factor—what they have). Taken together, these multiple factors provide increased security for your account settings and resources. You can enable MFA for your account and for individual users you have created under your account. MFA can be also be used to control access to service APIs.  
[https://aws.amazon.com/iam/details/mfa/](https://aws.amazon.com/iam/details/mfa/)

A virtual MFA device uses a software application to generate a six-digit authentication code that is compatible with the time-based one-time password (TOTP) standard, as described in RFC 6238. The app can run on mobile hardware devices, including smartphones. With most virtual MFA applications, you can host more than one virtual MFA device, which makes them more convenient than hardware MFA devices.
[http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)

### Suggested Action  
Enable Multi-Factor Authentication for every user.  
[Enabling a Virtual MFA](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)
[Enabling a Hardware MFA](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_physical.html)
