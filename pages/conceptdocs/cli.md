---
title: CloudCoreo CLI - Coreo
summary: CloudCoreo CLI - Coreo
tags:
keywords: ""
last_updated: "November 9, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_cli.html
folder: conceptdocs
toc: false
---

# CloudCoreo CLI
======================================================================

## Install

Installation of the [CloudCoreo](http://www.cloudcoreo.com/) CLI tool is simple and managed via NPM. For a global install (recommended) run:

```
npm install -g cloudcoreo-cli
```

## Commands

The following is a list of commands that can be run with the CLI tool. This is auto-generated.

##### Options

```
-h, --help output usage information
-V, --version output the version number
```

The [CloudCoreo](http://www.cloudcoreo.com/) CLI uses git-style subcommands.
For help, try:
```
coreo help <command>
```
or
```
coreo <command> help <subcommand>
```

### coreo init

The init command houses everything necessary to create new AppStacks
#### Options

```
-h, --help output usage information
-V, --version output the version number
-D, --directory <fully-qualified-path> the working directory
```
#### Actions

##### Action: new-stack

  new description

###### Options:

```
-h, --help output usage information
-s, --stack-type <stack type> What will this stack be? (server | stack)
```
###### Examples:

```

Excluding the -D (--directory) option assumes your working directory is
where your AppStack exists

$ coreo init new-stack -s server
$ coreo init new-stack --stack-type stack
```

### coreo stack

Subcommands and Actions housed within the stack command will handle all types of AppStack manipulation
#### Options

```
-h, --help output usage information
-V, --version output the version number
-D, --directory <fully-qualified-path> the working directory
```
#### Actions

##### Action: add

  Add a sibling stack

###### Options:

```
-h, --help output usage information
-s, --stack-type <stack type> What will this stack be? (server | stack)
-n, --stack-name <stack name> The name you would like to give to the sibling stack
-g, --from-git <git ssh url> The git ssh url from which this stack will be extended.
```
###### Examples:

```

Excluding the -D (--directory) option assumes your working directory is
where your AppStack exists

This command will add a VPN server to your AppStack

$ coreo stack add -s "server" -g "git@github.com:CloudCoreo/servers-vpn.git" -n "vpn"
$ coreo stack add --stack-type "server" --from-git "git@github.com:CloudCoreo/servers-vpn.git" -stack-name "vpn"
```
##### Action: extend

  Extend a stack

###### Options:

```
-h, --help output usage information
-g, --from-git <git ssh url> The git ssh url from which this stack will be extended.
```
###### Examples:

```

Excluding the -D (--directory) option assumes your working directory is
where your AppStack exists

This command will set your AppStack up to extend the CloudCoreo VPC

$ coreo stack extend -g git@github.com:cloudcoreo/cloudcoreo-vpc
```

### coreo account

work on a CloudCoreo Account
#### Options

```
-h, --help output usage information
-V, --version output the version number
```
#### Actions

##### Action: create

  create a new CloudCoreo account

###### Options:

```
-h, --help output usage information
-u, --username <username> What username to use on your new account
-e, --email <email> What email address to use on your new account
```
###### Examples:

```

This will create a new CloudCoreo account and key pairs
which can be used for accessing your account via the CLI tool.

The CLI tool will create a $HOME/.cloudcoreo directory and add a
config file with a JSON representation of the key pair and your username

$ coreo account create -u my_new_username -e me@example.com
```

### coreo solo

run processes on a stack without a CloudCoreo Account
#### Options

```
-h, --help output usage information
```
#### Actions

##### Action: run

  create a new CloudCoreo account

###### Options:

```
-h, --help output usage information
-p, --profile <profile> the CloudCoreo profile to use. if it does not exist, it will be created and associated with the cloud account
-a, --access-key-id <access-key-id> What amazon aws access key id to use
-e, --secret-access-key <secret-access-key> The secret access key associated with the corresponding access key id
-r, --region <region> The region in which this should be launched. If nothing is specified, it will look to launch in the default region supplied by a aws cli config file. If there is no cli config specified, an error will occur.
```
###### Examples:

```

This will create a new CloudCoreo account and key pairs
which can be used for accessing your account via the CLI tool.

The CLI tool will create a $HOME/.cloudcoreo directory and add a
config file with a JSON representation of the key pair and your username

$ coreo account create -u my_new_username -e me@example.com
```


-------


CLI Getting Started Example

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



