---
title: All authenticated AWS users can read the affected bucket
tags: [s3]
keywords: ""
last_updated: "September 17, 2016"
summary: Bucket has permissions which let any AWS authenticated user list the bucket contents.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_s3-authenticatedusers-read.html
folder: mydoc
toc: false
---

### Details   
An S3 ACL is a sub-resource that’s attached to every S3 bucket and object. It defines which AWS accounts or groups are granted access and the type of access. When you create a bucket or an object, Amazon S3 creates a default ACL that grants the resource owner full control over the resource. Some users have changed the S3 default permissions and granted public access to their buckets via S3 ACLs.  

Although you can grant public access to your bucket using ACLs, you must take the following issues into consideration: Bucket public "READ" access: This is sometimes referred to as "list" access. It allows anyone to get a complete list of your bucket content. It does not grant permissions to read content of an object. However, a list of object names can often provide more information than necessary to the public. You can use ACLs to grant permissions to individual AWS accounts; however, it is strongly recommended that you do not grant public access to your bucket using an ACL.  
[https://aws.amazon.com/articles/5050](https://aws.amazon.com/articles/5050)

### Suggested Action  
Remove the entry from the bucket permissions that allows 'Any Authenticated AWS User' to list the bucket. See [Updating ACL to Remove Public Access to Your Buckets](https://aws.amazon.com/articles/5050) for more information.

### Additional Information  
Sometimes S3 Bucket Policies are sometimes confused with S3 ACLs, which is a separate S3 feature. S3 bucket policies are a type of access control list but are different than S3 ACLs. S3 bucket policies specify what actions are allowed or denied for which principals on the bucket that the bucket policy is attached to. You attach S3 bucket policies at the bucket level, but the permissions specified in the bucket policy apply to all the objects in the bucket. As a general rule, we recommend using S3 bucket policies or IAM policies for access control. S3 ACLs is a legacy access control mechanism that predates IAM. However, if you already use S3 ACLs and you find them sufficient, there is no need to change.
[https://aws.amazon.com/articles/5050](https://aws.amazon.com/articles/5050)  
[https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc](https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc)  

To learn more about ACLs, see the following topics in Amazon S3 Developer Guide.  
[Access Control List (ACL) Overview](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ACLOverview.html)  
[Managing ACLs in the AWS Management Console](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ManageACLsUsingConsole.html)
