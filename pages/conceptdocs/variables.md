---
title: CloudCoreo Variables
summary: CloudCoreo Variables
tags:
keywords: ""
last_updated: "January 3, 2017"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_variables.html
folder: conceptdocs
toc: false
---

**Note:** Be careful when you edit your config.yaml file since this file **cannot contain tab characters**. When you do line spacing, use spaces instead. 

## Composite Variables

Composite variables are a great way to enable a variety of user defined options for your Composites as you create Plans to build and audit your infrastructure. These variables are implemented with variable definitions in your Composite code and are exposed in the WebUI via the contents of the `<repository-directory>/config.yaml`. This file is optional for Composites, but required if you will be defining and exposing variables in your Composite.

### Plan Variables
There are a few fields in the `config.yaml` file that control the behavior of the WebUI. These are `required`, `description`, `default`, `type`, and `overrides`.

* `default:`
You use the `default` field to pre-populate the default value for your particular variable when a Plan is created and when no other value has been entered. Valid entries for this field are whatever is appropriate for your particular variable. If a value for a particular variable is set via the WebUI, that value will be used instead of the value specified in `default`.  

Example entries for the `default:` field include:  
`default: 10.11.0.0`  
`default: us-east-1,eu-west-1,ap-southeast-1`   
`default: notify`

* `required:`
You use the `required` field to indicate whether the WebUI requires this variable to have a value entered when a Plan is created. Valid entries for this field are true or false.  Required variables *must* be supplied in order to Add and Run a Plan. If required variables are not supplied, CloudCoreo will display an error in the WebUI.

Example entries for the `required:` field include:  
`required: true`  
`required: false`   

Example entries for the `description:` field include:  
* `description:`
You use the `description` field to enter a human readable description that will show as a tooltip in the WebUI for the particular variable when a Plan is created. Valid entries for this field are any plain text (yaml compatible) enclosed in double quotes `" "`.  

`description: "This is a sample description"`  
`description: "Enter the value for this variable. Valid values are apple, ball, and/or cat."`   

* `type:`
You use the `type` field to define the type of input that this variable accepts. The type will also change how the variable input is displayed in the WebUI. Valid entries for this field include `array`, `string`, `number`, and `case`.  

Example entries for the `type:` field include:  

`type: string`  
`type: array`  

Here is an example `config.yaml` file showing a few different `type:` statements :

~~~  
variables:
  MY_DNS_ZONE:
    default: example.com
    description: This dns zone variable is used for setting up Route53 DNS entries.
    required: true
    type: string

  SWAP_SIZE_IN_GB:
    default: 2
    description: What size swap file would you like to create? (Gigabytes)
    required: false
    type: number

  SERVER_AMI:
    description: Which AMI should the instance be launched from?
    switch: INSTANCE::region
    cases:
      us-east-1: ami-1ecae776
      us-west-1: ami-d114f295
      us-west-2: ami-e7527ed7
    type: array
~~~  

