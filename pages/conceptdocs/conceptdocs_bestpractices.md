---
title: Advanced Composites part 3 - Composite Creation Best Practices  
summary: CloudCoreo Advanced Composites part 3 - Composite Creation Best Practices
tags:
keywords: ""
last_updated: "November 20, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_bestpractices.html
folder: conceptdocs
toc: false
---


## Composite Creation Best Practices  


### composite-*

When adding a composite, consider the needs of people *overriding* or *extending* your composite in the future. For instance, creating blank directories for dropping in bits of code and overrides will make everyone's life easier in the future. To help ease the administration efforts of creating these directories, use `composite-` in the CLI tool.

This makes it suitable to *add an external composite* to your composite.


You can also inherit / extend additional external Composites into this `composite-` directory to augment your own infrastructure definitions.


For example, say you want to add a composite from Git (github.com:example/tomcat.git) into your own composite and call it 'tomcat'. The ideal directory structure would require you to create a `composite-tomcat` directory to signify that it's special within the CloudCoreo framework. Next, create an `extends` directory inside that, and extend the composite into this directory. Now you are utilizing both concepts. Because you used a `composite-*` directory to the `<repository-dir>`, it will run **after** `<repository-dir>/extends`. Because you have added the composite to `<repository-dir>/composite-tomcat/extends` it will run **before** everything else inside the `composite-tomcat*` directory. Now, anyone utilizing your composite has a convenient place to insert configuration and setup between your composite and the added Tomcat composite.


