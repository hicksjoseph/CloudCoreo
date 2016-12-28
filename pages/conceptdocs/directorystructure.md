---
title: CloudCoreo Directory structure
summary: CloudCoreo Directory structure
tags:
keywords: ""
last_updated: "December 27, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_directorystructure.html
folder: conceptdocs
toc: false
---

## Composite / Repository Directory Structure
CloudCoreo relies on convention over configuration for the most part, achieving simplicity and flexibility. Since the basic structure of a Composite is that only one Composite is contained within a particular repository, a repository can contain whatever code you would like to build your infrastructure using CloudCoreo. However, there are some directories that CloudCoreo reserves for certain functions.

The CloudCoreo directory naming structure directly conveys what each CloudCoreo reserved directory actually does. For example, the `overrides` directory specifies which inherited directives will be overridden so as to enable modified inherited behavior or perhaps to not execute the inherited directives at all. Another example is the `boot-scripts` directory which contains and specifies the scripts that will run when a particular server boots.  

Here is a list of the CloudCoreo reserved directories and their function.  

### services  
The `services` directory is where you can use code to definte cloud infrastructure such as servers, VPCs, Load Balancers, DNS, or other infrastructure. The `services` directory is also where you would define audit definitions for your cloud deployments. When using the `services` directory, infrastructure code goes into the `<repository-dir>/services/config.rb` file while variable definitions for the WebUI live in the `<repository-dir>/config.yaml` file.  

To learn more about the `services` directory, see [Composite Creation](http://kb.cloudcoreo.com/conceptdocs_compositecreation.html)

### extends  
The `extends` directory is a type of symbolic link that points to a different git repository. The `extends` directory enables you to inherit infrastructure definition from a different Composite (repositories) as a base Composite definition. By using the `extends` directory to point to other Composites (repositories), you can **leverage the best practice code of others** for use your own deployments. Many Composites are based on and inherited from other Composites via use of the `extends` directory. "Golden Master" Composites can be created for commonly created infrastructure so that other people can extend them to create Composites that combines many "Golden Master" Composites that can be used for day-to-day deployment and operation of their infrastructure.  

Any code in the `extends` directory will execute first before any other code in the current Composite (repository) in which it is contained. The use of this directory is required when inheriting from a different Composite, but is optional otherwise. Only one `extends` directory can exist at the root level of a Composite repository, however a Composite may have other `extends` directories contained within some of the other directories listed below.  

### stack  
The stack- directory is a way to organize related infrastructure components into a modular and easy to understand structure. You may want to group certain similar configuration components together in a `stack-` directory for ease of understanding, editing, and related execution order. An example of the usage of a `stack-` directory would be to group together  configuration for a tomcat server deployment and might be labeled `stack-tomcat`. Other examples of a `stack-` directory might be for a MySQL deployment, labelled `stack-mysql` or a time-series Cassandra deployment, labelled `stack-cassandra-timeseries`. You can create `stack-` directories with anything following `stack-` (`stack-example`). The use of this directory is optional otherwise.  

The configuration in a `stack-` directory is executed after the code in the root repository `extends` directory (if exists) and before any other code in the rest of the resposity. You may have multiple `stack-` directories in a Composite / repository, but their execution order will be indeterminate. There are no limits on the number of `stack-` directories you can have in a composite. The use of `stack-` directories can be very powerful for creating infrastructure, including constructs where you can include an `extends-` directory inside of a `stack-` directory or even have nested `stack-` directories. Learn more about this in [Composite Tricks and Tips](http://kb.cloudcoreo.com).  

### boot-scripts  
The `<repository-dir>/boot-scripts` directory is used for scripts that define boot time configuration of a server. The use of this directory is optional otherwise.  

To add a script to the boot time execution of scripts that run at server start up, copy the file(s) to the `boot-scripts` directory and add the file name to the correct `order.yaml` file. Here is an example `order.yaml` file containing the list of scripts in the correct execution order.  

~~~~
script-order:
 - install_docker.sh
 - start_docker.sh
 - update_route_tables.sh  
~~~~

The overall order that boot scripts will be run is defined by:  
1. The directory structure.  
2. Then the order defined in the `order.yaml` file within this directory  

For example, boot scripts in the `<repository-dir>/extends` will run before scripts at the root of the Composite.

Note: A script must be copied to the appropriate `boot-script` directory and defined in the correct `order.yaml` file for it to run at server startup. Any file that is placed into the boot-scripts directory will be copied to the server at boot time.  

### operational-scripts  
The `<repository-dir>/operational-scripts` directory is used for scripts that you may want to run on the server on an ad-hoc basis from the CloudCoreo GUI or CLI. The use of this directory is optional otherwise.  

### shutdown-scripts  
The `<repository-dir>/shutdown-scripts` directory contains scripts that you want to run when a server shuts down. CloudCoreo will attempt to run these scripts, but their execution is not guaranteed due to unpredicatble server shutdown by the cloud and other situations that improperly terminate a server.  

### overrides  
The `<repository-dir>/overrides` directory contains code and files that will override the execution plan from inherited Composites or preceding directories.  

Read more about how overrides work in [Introduction to overrides](http://kb.cloudcoreo.com/) .  

The CloudCoreo CLI is an essential tool if you will be creating Composites from the very beginning. The CLI can initialize a repository with all of the directories required for proper Composite construction ( use `coreo init` ).  Otherwise, cloning an existing repository or or creating the appropriate directories manually can also be a useful way to get started with Composites.  

Read more about the [CloudCoreo CLI](http://kb.cloudcoreo.com/conceptdocs_cli.html) .  

