---
title: Bucket policy gives world Put permission
tags: [s3]
keywords: ""
last_updated: "September 17, 2016"
summary: Bucket policy allows the world to put data into the affected bucket.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_s3-world-open-policy-put.html
folder: mydoc
toc: false
---

### Details  
The bucket policy allows the world to put data into the affected bucket. S3 bucket policies are a type of access control list but are different than S3 ACLs. S3 bucket policies specify what actions are allowed or denied for which principals on the bucket that the bucket policy is attached to. You attach S3 bucket policies at the bucket level, but the permissions specified in the bucket policy apply to all the objects in the bucket.  

An S3 Bucket Policy has been added that grants public access to your bucket.  Put access has been granted to the world on the affected bucket. This allows anyone to put (and overwrite) data in your bucket. You can use bucket policies to grant permissions to individual AWS accounts; however, it is strongly recommended that you do not grant public access to your bucket unless you are absolutely certain. Consider alternative methods to provide public access to your buckets.  
[https://aws.amazon.com/articles/5050](https://aws.amazon.com/articles/5050)  
[https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc](https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc)

### Suggested Action  
Remove the bucket permission that enables the world to put (and overwrite) data in this bucket. See [Updating ACL to Remove Public Access to Your Buckets](https://aws.amazon.com/articles/5050)

### Additional Information  
See [Alternatives to Public Access](https://aws.amazon.com/articles/5050) for more information.  

To learn more about ACLs, see the following topics in Amazon S3 Developer Guide.  
[Access Control List (ACL) Overview](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ACLOverview.html)  
[Managing ACLs in the AWS Management Console](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ManageACLsUsingConsole.html)
