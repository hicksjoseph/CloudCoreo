---
title: What is the best way to grant CloudCoreo access to my AWS account?
tags:
keywords: ""
last_updated: "February 17, 2017"
summary: Granting CloudCoreo access to your AWS account.
published: true
sidebar: faq_sidebar
permalink: faq_awsrolepolicy.html
folder: faq
toc: false
---

##CloudCoreo Service Cloud Account (AWS) Access and Permissions FAQ##


###Granting CloudCoreo Access to your Cloud Account (AWS)###

The ability for the CloudCoreo Service to perform any function in your Cloud Account (AWS) is completely governed by the AWS IAM Role that you create which is used by the AWS AssumeRole functionality control (IAM Roles).

Currently, there are two ways to add a Cloud Account (AWS) to the CloudCoreo Service:

####Option 1 | Create a Cross-Account Access Role in IAM####

Have an administrative user in the target Cloud Account (AWS) create a Cross-Account Access Role in IAM using the CloudCoreo Service AWS “Account ID” and “External ID” to grant access to only the CloudCoreo Service.

+ The Role privileges can be set to the minimum required by the CloudCoreo Service to perform the requested function.
  + Auditing a target Cloud Account only requires a ‘SecurityAudit’ role, while deploying or creating AWS objects such as EC2 instances may require ‘AdministrativeAccess’ or other access permissions.
  + Role privileges can be configured very granularly as needed (eg Read Only access for just one AWS service)

+ The Role ARN is then supplied to CloudCoreo Service (see CloudCoreo WebUI picture below)

+ The Role and/or Role permissions can be disabled / deleted at any time, for example, after a one-time Audit is performed on a target Cloud Account (AWS)
  + Deleting the Role would disable the ability to constantly and consistent perform a security audit or deploy infrastructure in the target Cloud Account.

> ######Adding a Cloud Account Using a Cross-Account Access Role in the CloudCoreo Web UI######
>
> ![Create a Cross-Account Access Role in IAM](http://kb.cloudcoreo.com/images/awsrole2.png "Adding a Cloud Account in the CloudCoreo Web UI")

####Option 2 | Provide an IAM user’s Access and Secret Key####

Provide CloudCoreo with an IAM user’s Access and Secret Key. CloudCoreo then creates a Role in the target Cloud Account (AWS) using the Access keys provided.
+ The Access and Secret Keys are not stored and are only used to create a Role for the CloudCoreo Service.
  + AWS credentials are never written to disk.
+ By default, the CloudCoreo service creates an Role named CloudCoreoAssumedRole with full privileges (except for user creation) in the target Cloud Account.
  + Here is the IAM Policy attached to the CloudCoreoAssumedRole in the target account:

```
{ "Version": "2012-10-17",
    "Statement": [
        { "Action": [ "*" ], "Effect": "Allow", "Resource": "*" },
        { "Action": [ "iam:CreateUser" ], "Effect": "Deny", "Resource": "*"  } ] }
```

+ The Access Keys provided to the CloudCoreo Service can be from any AWS user in the target Cloud Account that has at least the following minimum permissions. (These permissions allow CloudCoreo to create the necessary Role.) 

```
{  "Version": "2012-10-17",
  "Statement": [
     { "Effect": "Allow",
        "Action": [ "iam:GetUser", "iam:CreatePolicy", "iam:GetPolicy", "iam:CreateRole", "iam:GetRole", "iam:AttachRolePolicy" ],
        "Resource": "*" } ] }
```

+ It is recommended that the AWS Access keys provided to CloudCoreo immediately be inactivated and deleted.
+ Optionally, AWS user account that generated the keys that were provided to CloudCoreo can also immediately be inactivated and/or deleted.

> ######Adding a Cloud Account Using a Access Keys in the CloudCoreo Web UI######
>
>![Provide an IAM user’s Access and Secret Key](http://kb.cloudcoreo.com/images/awsrole1.png "Adding a Cloud Account in the CloudCoreo Web UI")

---

###How the CloudCoreo Service isolates Cloud Accounts, Teams, and Plans###

Internal to the CloudCoreo Service, there are separate EC2 instances that make the API calls to AWS on behalf of CloudCoreo Service users. These CloudCoreo Service EC2 instances have no ports open to the internet. The communication to AWS happens through queuing systems which are governed by AWS Roles.

---

###Does CloudCoreo Store or Back-Up the Results from my Plan Runs?###

CloudCoreo Service Plan Run Results are stored for display purposes only. Results stored for display purposes may be deleted by the CloudCoreo Service at any time, however CloudCoreo does maintain encrypted backups of the Results database that may be retained up to 5 years. 

Upon request, the CloudCoreo Service can exclude any Plan Run Results from backups, however, CloudCoreo does not guarantee Plan Run Results availability in the case of a complete failure of the Results database (where the Results database needs to be restored from backup).

