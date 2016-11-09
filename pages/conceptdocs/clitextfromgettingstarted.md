---
title: Getting started with CloudCoreo
keywords: homepage
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: index.html
summary: These brief instructions will help you get started quickly with CloudCoreo.
toc: false
---

### Get Started — No signup necessary!  

CloudCoreo makes it simple to get up and running quickly in the cloud.

### Download git and the CloudCoreo CLI

CloudCoreo uses git and git concepts.
If you don't already have Git, download and install it.

CloudCoreo requires the use of AWS access keys to be able to deploy to the cloud. CloudCoreo never stores your credentials.

### Install the CloudCoreo CLI
The CloudCoreo CLI allows full control over your CloudCoreo account.

$ (Insert instructions for downloading and installing the CLI)

### Create Your Deployment Project
The following steps outline the process of deploying a VPC (virtual private cloud) in Amazon Web Services. 

A CloudCoreo Composition is defined by a single repository in Git a directory:

$ mkdir -p ~/composition1  
$ cd ~/composition1

Pull down the public CloudCoreo github repository for a sample VPC composition:

$ (Insert the new CLI command) vpc-network-only_284bd

### Deploy the composition
$ (insert new cli command)

The CLI will ask you for the keys to the AWS account you would like us to integrate with. If you already have the AWS CLI set up, we'll see those keys and apply them.

### Verify what was built in AWS
After completing the steps above to deploy you will end up with the following, assuming you left all the defaults alone:
* 1 VPC (10.11.0.0/16)
* 1 Internet Gateway
* 3 Public Subnets
* 3 Private Subnets
* 3 Private Route Tables
* 1 Public Route Table

### Next steps / call to action  



