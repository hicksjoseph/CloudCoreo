---
title: Advanced Composites part 1 - CloudCoreo Directory structure
summary: CloudCoreo Advanced Composites part 1 - CloudCoreo Directory structure
tags:
keywords: ""
last_updated: "November 20, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_directorystructure.html
folder: conceptdocs
toc: false
---

## Directory Structure
CloudCoreo relies on [convention](https://en.wikipedia.org/wiki/Coding_conventions) instead of configuration for enabling advanced Composite functionality. There are a number of files and directories that comprise a Composite. These files are stored as part of a repository (repo) in git, the popular version control system. Github and Bitbucket are two examples of hosted git repository services. While each Composite / repository can include any files and code that you would like, there are some directories are reserved for CloudCoreo advanced functionality. In this document, we list those directories and their functions.  

The CloudCoreo convention around directory structure precisely dictates to how Composites are actually compiled and executed. The directory structure specifies execution aspects such as inherited infrastructure, server boot script run order, inheritence overrides, and more.  The [CloudCoreo CLI](http://kb.cloudcoreo.com/conceptdocs_cli.html) will do much of the work in setting up the correct directory structure, but understanding what each directory convention does is essential.  

### Extending and Inheriting Composites from others
Often when using Composites, you will want to leverage the best practices of others by inheriting their base infrastructure deployments. You can do this by extending other's Composites and then adding and/or modifying the execution of their infrastructure to meet your needs. This also allows you to continually inherit changes to their original, if desired, so that you can always be up to date with your infrastructure definitions (and potentially security) or override as aspect of the inherited Composite.

You inherit the base infrastructure of others when you `extend` a Composite using the [CloudCoreo CLI](http://kb.cloudcoreo.com/conceptdocs_cli.html). This process creates an `extends` directory in your Composite's repository. Because you are using the base infrastructure of others, anything defined via the `extends` directory will be compiled and executed first. **All infrastructure defined in `extends` will be completed first before executing anything in any other directory in the Composite repository.**  

**Insert tree diagram here with this `extends-` directory highlighted with bold.**

**Questions: Can there be multiple `extends-` directories? If so, in what order will they execute between each other? I think that they will execute alphabetically.**

**Insert link to more information about inheritance and extends.**

### composite-
Any subdirectory beginning with `composite-` is reserved in CloudCoreo. The infrastructure specification in these directories is executed after any infrastructure in the `extends` directory at the Composite repository root (if it exists) but before anything else in the current repository. An example of a `composite-` directory might be a directory for your tomcat server definition or MongoDB cluster creation.  For example

```
 `composite-tomcat`
 `composite-mongodb`

**Insert tree diagram here with an example `composite-` directory highlighted with bold. 

Using the `composite-` directory enables you to specify your own infrastructure that will execute after any `extends-` directories in the root of the Composite repository.  **Discuss and give examples of what files would exist in the `composite-` directory and what those files might contain.

**Insert link to more information about the composite directory and more examples.**

### services
The `services` directory exists to define the composite's interaction with the particular cloud provider in which the infrastructure is being created. Infrastructure specification is kept in the `config.rb` file (`<repo-dir>/services/config.rb`) with variables defined in `config.yaml` file (`<repo-dir>/config.yaml`). Read more about the services directory, config.rb, and config.yaml [here](http://kb.cloudcoreo.com/conceptdocs_compositecreation.html). 

### boot-scripts
The `boot-scripts` directory exists to enable you to specify boot time configuration of a particular server. The `boot-scripts` directory can exist in one or more places in the Composite repository depending on your infrastructure requirements. You can create a `boot-scripts` directory in the root of the repository directory, in a composite- directory, and/or an extends directory. If the boot-scripts directory exists in any of these locations, the Composite will execute the boot scripts in a particular order which is:

1. The CloudCoreo directory execution convention (`extends`, `composite-*`). For example:  
   1. `<repo-dir>/extends/boot-scripts`)
   2. `<repo-dir>/overrides/boot-scripts`)
   3. `<repo-dir>/composite-/boot-scripts`)
2. The order specified in an `order.yaml` file that is created inside of the particular `boot-scripts` directory.

**To learn more about boot scripts and examples of execution order, read more [here](http://kb.cloudcoreo.com/conceptdocs_bootscripts.html)**
**To learn more about the format of the `order.yaml` file and to see examples, read more [here](http://kb.cloudcoreo.com/conceptdocs_orderdotyaml.html))**

### operational-scripts
The files contained within the `<repo-dir>/operational-scripts` directory are scripts you can execute as needed on the particular server from the CloudCoreo WebUI or CLI. 

**To learn more about operational scripts and to see examples, read more [here](http://kb.cloudcoreo.com/conceptdocs_operationalscripts.html)**

**Previously, the CloudCoreo docs specified that "The structure and scripts within the `operational-scripts` directory honor the order and overrides defined within the rest of this document." However, since these operational-scripts are not execution order dependent, a review of the behavior is necessary before documenting the behavior.**

### shutdown-scripts
The `<repo-dir>/shutdown-scripts` directory contains scripts that CloudCoreo will attempt to run when the particular server is shutting down.

**These scripts are used to..... For example, .....**

**Note:** These scripts are not guaranteed to execute because servers can shut down abnormally or abpruptly.

The `shutdown-scripts` directory can exist in one or more places in the Composite repository depending on your infrastructure requirements. You can create a `shutdown-scripts` directory in the root of the repository directory, in a composite- directory, and/or an extends directory. If the shutdown-scripts directory exists in any of these locations, the Composite will execute the shutdown scripts in this order:

**Previously, the CloudCoreo docs specified that "The structure and scripts within the `shutdown-scripts` directory honor the order and overrides defined within the rest of this document." However, since these operational-scripts are not execution order dependent, a review of the behavior is necessary before documenting the behavior.**

### overrides
When inheriting and extending other's Composites, you will often need to modifying or prevent the execution of certain aspects of the inherited infrastructure to meet your needs. This is accomplished by the use of the `overrides` directory and the Composite infrastructure specifications contained therein. Anything contained in the `overrides` directory will act as an override for the Composite in which it is contained. You can override any aspect of a Composite (including Composite inheritance).

The `overrides` directory can exist in one or more places in the Composite repository depending on your infrastructure requirements. You can create an `overrides` directory in the root of the repository directory, in a composite- directory, and/or an extends directory. If the overrides directory exists in any of these locations, the Composite will override any inherited infrastructure definition that is defined using the exact same convention and structure of the infrastructure specification that it is overriding. The infrastructure specification specified in any particular `overrides` directory executes per a specified order.

**To learn more about the overrides directory and to see examples as well as execution order, read more [here](http://kb.cloudcoreo.com/conceptdocs_advancedcomposites.html)**  
  


----  
  
  