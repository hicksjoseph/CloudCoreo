---
title: What is the best way to grant CloudCoreo access to my AWS account?
tags:
keywords: ""
last_updated: "October 19, 2016"
summary: Granting CloudCoreo access to your AWS account.
published: true
sidebar: faq_sidebar
permalink: mydoc_awsrolepolicy.html
folder: faq
toc: false
---

### Question  
What is the best way to grant CloudCoreo access to my AWS account?

### Answer  

CloudCoreo uses AWS keys entered in to the CloudCoreo WebUI to create an AWS Role / Policy in your AWS account so that the CloudCoreo engine can perform requested functions in your AWS account. Once the Role and Policy has been created in your AWS account, CloudCoreo no longer needs the AWS keys you supplied and does not store or continue to use those AWS keys for any reason.

To ensure that the correct and minimum amount of access to your AWS account is granted to CloudCoreo, the best practice is to:
* Create an IAM user in your AWS account  
* Grant that IAM user specific permissions  
* Generate an AWS key for this user  
* Add the AWS account to the CloudCoreo WebUI using this newly generated key  
* Inactivate and delete the key from this AWS IAM user and then delete the AWS IAM user  

Create an IAM user ( eg cloudcoreo ) in your AWS account and grant the user specific permissions with this policy:
~~
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:GetUser",
        "iam:CreatePolicy",
        "iam:GetPolicy",
        "iam:CreateRole",
        "iam:GetRole",
        "iam:AttachRolePolicy"
      ],
      "Resource": "*"
    }
  ]
}
~~~  

Generate an AWS key for the user you just made.

Add the AWS account to the CloudCoreo WebUI using this newly generated key.

The CloudCoreo WebUI uses the keys to make a role named ~~ CloudCoreoAssumedRolePolicy ~~~ that contains this policy:  
~~
{"Version":"2012-10-17","Statement":[{"Action":["*"],"Effect":"Allow","Resource":"*"},{"Action":["iam:CreateUser"],"Effect":"Deny","Resource":"*"}]}
~~~  

You can then immediately delete the user keys after we make the CloudCoreoAssumedRolePolicy policy.


