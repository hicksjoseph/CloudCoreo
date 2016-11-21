---
title: Composite boot scripts, execution order, and examples
summary: CloudCoreo Composite boot scripts, execution order, and examples
tags:
keywords: ""
last_updated: "November 20, 2016"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_bootscripts.html
folder: conceptdocs
toc: false
---


As an example, if your directory structure contains the following paths CloudCoreo will run each script in the `extends/composite-example/extends/boot-scripts/order.yaml` file before moving on to the `extends/composite-example/boot-scripts/order.yaml`:

* `extends/composite-example/extends/boot-scripts`
* `extends/composite-example/boot-scripts`

As a matter of fact, each of the scripts in the base directory can be overridden at any point.
