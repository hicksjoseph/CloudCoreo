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

Are you ready to take your cloud infrastructure to the next level? CloudCoreo makes it simple to get up and running quickly in the cloud. The fastest way to go from zero to deployed is to use our CLI tool, built in Node.

The following steps outline the process of deploying a VPC (virtual private cloud) in Amazon Web Services. 

### Download pre-requisite tools: Nodejs, Git,
There are just a few things you need to have handy before diving into the deployment setup, including Git and Node.js.

CloudCoreo uses git and git concepts.
If you don't already have Git, go ahead and download and install it.

Our CLI is built in Node.js. This means you need Node installed, or specifically npm. 
Go get Node before moving on.

CloudCoreo also requires the use of AWS access keys to be able to deploy to the cloud. We never store your credentials. Follow this tutorial to obtain keys if you don't already have them.


### Install the CloudCoreo CLI
The CloudCoreo CLI allows full control over your CloudCoreo account. The cloudcoreo “solo” subcommands allow many operations and deployment options.

$ npm install -g cloudcoreo-cli

### Create Your Deployment Project
A CloudCoreo composition is defined by a single repository in Git, or in the case of the “solo” subcommand, a directory:

$ mkdir -p ~/composition1 
$ cd ~/composition1

Pull down the public CloudCoreo github repository for a sample VPC composition:

$ coreo composition extend vpc-network-only_284bd

### Deploy the composition
$ coreo solo run

The CLI will ask you for the keys to the AWS account you would like us to integrate with. If you already have the AWS CLI set up, we'll see those keys and apply them. Otherwise, just enter the keys on the command line. 

### Verify what was built in AWS
After completing the steps above to deploy you will end up with the following, assuming you left all the defaults alone:
* 1 VPC (10.11.0.0/16)
* 1 Internet Gateway
* 3 Public Subnets
* 3 Private Subnets
* 3 Private Route Tables
* 1 Public Route Table

### Connect with CloudCoreo to find out more
info at cloudcoreo dot com

