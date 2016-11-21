---
title: Composite creation
summary: CloudCoreo Composite creation
tags:
keywords: ""
last_updated: "November 20, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_compositecreation.html
folder: conceptdocs
toc: false
---

## Composite creation  
CloudCoreo enables users to create and layer inheritable cloud reference designs called Composites. A Composite specifies the desired end state of your cloud deployment, including all required resources and service dependencies.  Any supported cloud resource can be included in your design from including networking, security, storage, compute as well as container and serverless functions offered by a cloud provider.  

### Composites  
There are a number of files and directories that comprise a Composite. These files are stored as part of a repository (repo) in git, the popular version control system. Github and Bitbucket are two examples of hosted git repository services. 

Cloud Resources are defined in the `config.rb` file. The `config.rb` file resides in the `<repo-dir>/services` directory and exists to define interactions within the cloud provider in which you are operating.  

We define a ***resource*** as the actual cloud service you are interacting with, such as a [*VPC*](https://aws.amazon.com/vpc/). Cloud Resources are defined by the desired configuration within your cloud provider account.  

The structure of a Cloud Resource is:  

~~~ ruby  
<resource> "<name>" do
    <property1> <value>
    <property2> <value>
    <property3> <value>
end
~~~  

Here is an example of a VPC Cloud Resource:

~~~ ruby  
coreo_aws_vpc_vpc "my-vpc" do
  action :sustain
  cidr "12.0.0.0/16"
  internet_gateway true
end
~~~    

This Cloud Resource will create a VPC with the CIDR address "12.0.0.0/16" and attach an *Internet gateway* to the VPC to allow traffic to a public subnet (the public subnet Cloud Resource is assumed to already exist in this example). This example shows statically created Cloud Resources. In many cases, it would be better to use variables which allow you to specify values such as the VPC name and VPC cidr address when you create Composite Plans for each part of your infrastructure.

### Composite Plans  
A Composite Plan (Plan) is an instance of your infrastructure design that includes your specified deployment variables and policy controls. The Coreo Engine uses a Plan to deploy and maintain the set of running cloud infrastructure resources.  Plans can be used to partition and drive separate infrastructure and cloud policies.  

Plans allow variables to be inserted into the system at runtime, allowing a single Composite to be used in many different environments. The Plan variables can be supplied in a number of ways:  

* Values provided at Plan creation / modification in the CloudCoreo WebUI  
* Values set during the use of the CloudCoreo CLI (called coreo)  
* Defaults set in the config.yaml file in the Composite Repository  

The look of the variables is similar to *bash* but many "bash-isms" do not apply. To define a variable use `${ }` to contain it, for example `${VARIABLE_NAME}`. Let's see what the previous example of the VPC Cloud Resource would be look like with the use of variables for VPC name and VPC cidr octets:  

~~~ ruby
coreo_aws_vpc_vpc "${VPC_NAME}" do
  action :sustain
  cidr "${VPC_OCTETS}/16"
  internet_gateway true
end
~~~  

Plan variables are defined in the `config.yaml` file which resides in the `<repo-dir>` base directory. Within the `config.yaml` file, you can now call out a `VPC_NAME` and `VPC_OCTETS` variables and apply defaults. In this case, the variable `VPC_NAME` and `VPC_OCTETS` will show up in the web UI for any users to modify.  This is what the `config.yaml` would look like in this case:

~~~ ruby
variables:
    VPC_NAME:
        required: true
        description: Enter the name of the VPC. (Default is test-vpc)
        default: test-vpc
    VPC_OCTETS:
        required: true
        description: Enter the /16 CIDR address / network of the VPC. (Default is 10.11.0.0)
        default: 10.11.0.0
~~~

### Plan Variables
There are a few fields in the `config.yaml` file that control the behavior of the WebUI. These are `required`, `description`, and `default`.

* `default:`
You use the `default` field to pre-populate the default value for your particular variable when a Plan is created and when no other value has been entered. Valid entries for this field are whatever is appropriate for your particular variable.  

`default: 10.11.0.0`  

or  

`default: us-east-1,eu-west-1,ap-southeast-1`   


* `required:`
You use the `required` field to indicate whether the WebUI requires this variable to have a value entered when a Plan is created. Valid entries for this field are true or false.  

`required: true`  

or  

`required: false`   

* `description:`
You use the `description` field to enter a human readable description that will show as a tooltip in the WebUI for the particular variable when a Plan is created. Valid entries for this field are any plain text (yaml compatible) enclosed in double quotes `" "`.  

`description: "This is a sample description"`  

or  

`description: "Enter the value for this variable. Valid values are apple, ball, and/or cat."`   


**Note:** Be careful when you edit your config.yaml file since this file **cannot contain tab characters**. When you do line spacing, use spaces instead. 

-----

These are the basics concepts of Composite creation. Learn more about Advanced Composite creation at [*Advanced Composites*](http://kb.cloudcoreo.com/conceptdocs/advancedcomposites.html/) .  

-----

As you build new Composites, you will need to reference the [*CloudCoreo API Documentation*](http://docs.cloudcoreo.com/docs/frames/index) to know what options and parameters that you can use in your Composites.  
