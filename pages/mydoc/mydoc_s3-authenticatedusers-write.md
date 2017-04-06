---
title: All authenticated AWS users can write to the affected bucket
tags: [s3]
keywords: ""
last_updated: "September 17, 2016"
summary: Bucket has permissions which lets any AWS users write to the bucket.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_s3-authenticatedusers-write.html
folder: mydoc
toc: false
---

### Details   
An S3 ACL is a sub-resource that’s attached to every S3 bucket and object. It defines which AWS accounts or groups are granted access and the type of access. When you create a bucket or an object, Amazon S3 creates a default ACL that grants the resource owner full control over the resource. Some users have changed the S3 default permissions and granted public access to their buckets via S3 ACLs.  

The affected bucket has permissions which let any authenticated AWS users write to the bucket. It is recommended that buckets are not world writeable. When a bucket is world writeable, any user is able to delete or overwrite data which can cause data loss or add to your bucket which can cause you to incur unnecessary costs.  

### Suggested Action  
Remove the bucket permissions that allows 'Any Authenticated AWS User' to write to the bucket. In general, it is strongly recommended that you remove any public access grants in your bucket ACL so that your bucket is protected from a potentially malicious user performing operations like listing all your objects, modifying objects or changing your ACLs.  

See [Updating ACL to Remove Public Access to Your Buckets via an Access Control List (ACL)](https://aws.amazon.com/articles/5050) for more information.  

### Additional Information  
Sometimes S3 Bucket Policies are sometimes confused with S3 ACLs, which is a separate S3 feature. S3 bucket policies are a type of access control list but are different than S3 ACLs. S3 bucket policies specify what actions are allowed or denied for which principals on the bucket that the bucket policy is attached to. You attach S3 bucket policies at the bucket level, but the permissions specified in the bucket policy apply to all the objects in the bucket. As a general rule, we recommend using S3 bucket policies or IAM policies for access control. S3 ACLs is a legacy access control mechanism that predates IAM. However, if you already use S3 ACLs and you find them sufficient, there is no need to change.
[https://aws.amazon.com/articles/5050](https://aws.amazon.com/articles/5050)  
[https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc](https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resourc)  

To learn more about ACLs, see the following topics in Amazon S3 Developer Guide.  
[Access Control List (ACL) Overview](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ACLOverview.html)  
[Managing ACLs in the AWS Management Console](http://docs.amazonwebservices.com/AmazonS3/latest/dev/ManageACLsUsingConsole.html)
