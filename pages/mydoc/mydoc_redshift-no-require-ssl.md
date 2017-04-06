---
title: Redshift connections not SSL
tags: [redshift]
keywords: ""
last_updated: "September 17, 2016"
summary: Connections to Redshift aren't set to require the use of SSL encryption.
published: true
sidebar: mydoc_sidebar
permalink: mydoc_redshift-no-require-ssl.html
folder: mydoc
toc: false
---

### Details  
Amazon Redshift supports Secure Sockets Layer (SSL) connections to encrypt data and server certificates to validate the server certificate that the client connects to. By default, cluster databases accept a connection whether it uses SSL or not. Currently, connections to the affected Redshift cluster aren't set to require the use of SSL encryption.  

### Suggested Action  
Enable Redshift to require the use of SSL encrypted connections. To configure your cluster to require an SSL connection, set the require_SSL parameter to true in the parameter group that is associated with the cluster. To support SSL connections, Amazon Redshift creates and installs a self-signed SSL certificate on each cluster. SSL support in Amazon Redshift is strictly for encrypting the connection between your client and your cluster; it should not be relied on for authenticating the server.
[http://docs.aws.amazon.com/redshift/latest/mgmt/connecting-ssl-support.html](http://docs.aws.amazon.com/redshift/latest/mgmt/connecting-ssl-support.html)
