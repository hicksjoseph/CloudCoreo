---
title: CloudCoreo Results Table specification
tags:
keywords: ""
last_updated: "March 8, 2017"
summary: CloudCoreo Results Table specification
published: true
sidebar: faq_sidebar
permalink: faq_resultstablespecification.html
folder: faq
toc: false
---

## Result Tables Specification

CloudCoreo users would like to be able to specify what to display for results behind the Results Cards that are displayed in CloudCoreo Audit HTML email reports and/or an Audit Results Panel. CloudCoreo provides the ability to be able to display any data collected, instead of simply displaying a fixed set of generic information with generic header labels. There is a specification for tables per rule definition, that is specified in a table.yaml file that is stored in the Composite root directory. 

For each Alert Rule, you should provide an entry for:  
  `column_header : column_spec`

For example  
  `rds-short-backup-retention-period: "AWS Tags": "__TAGS__"`


In the column_specs several "macros" and special characters are processed:  

* `__OBJECT__`  
    The violating object id at the top of the result structure - corresponds to the id_map  


* `__TAGS__`  
    tag=value space delimited list of all AWS tags on the object  


* `__RULE__`  
    The alert-id, for example, rds-db-publicly-accessible  


* `__TAGKEYS__`  
    Space delimited list of all AWS tag keys on the object - does not include the tag values  


* `tilde ~`  
    Denotes a hyperlink. The text to the left of the `~` is the display text and the text to the right is the hyperlink HREF  


* `dotted notation`  
    specifies a "key" into the JSON return structure  
    The path delimited with +'s is looked up in the results structure and the result of the lookup is substituted  
    Example: `+(a.b.c.d.e)+`  
  
  

**The output is a JSON object with an element for each Result Card.**  
  
  

Here is an example [table.yaml](https://github.com/CloudCoreo/audit-aws-rds/blob/master/table.yaml) for the RDS service as a component in the `audit-aws-rds` Composite:  

~~~  
rds-short-backup-retention-period:
  "RDS Instance": "__OBJECT__~https://console.aws.amazon.com/rds/home?region=+__OBJECT__.violations.__RULE__.region+#dbinstances:id=__OBJECT__;sf=all"
  "Backup Retention Period": "+__OBJECT__.violations.__RULE__.result_info.0.object.backup_retention_period+"
  "AWS Region": "+__OBJECT__.violations.__RULE__.region+"
  "AWS Tags": "__TAGS__"
rds-no-auto-minor-version-upgrade:
  "RDS Instance": "__OBJECT__~https://console.aws.amazon.com/rds/home?region=+__OBJECT__.violations.__RULE__.region+#dbinstances:id=__OBJECT__;sf=all"
  "AWS Region": "+__OBJECT__.violations.__RULE__.region+"
  "AWS Tags": "__TAGS__"
rds-db-publicly-accessible:
  "RDS Instance": "__OBJECT__~https://console.aws.amazon.com/rds/home?region=+__OBJECT__.violations.__RULE__.region+#dbinstances:id=__OBJECT__;sf=all"
  "AWS Region": "+__OBJECT__.violations.__RULE__.region+"
  "AWS Tags": "__TAGS__"
rds-inventory:
  "RDS Instance": "__OBJECT__~https://console.aws.amazon.com/rds/home?region=+__OBJECT__.violations.__RULE__.region+#dbinstances:id=__OBJECT__;sf=all"
  "AWS Region": "+__OBJECT__.violations.__RULE__.region+"
  "Engine Type": "+__OBJECT__.violations.__RULE__.result_info.0.object.engine+"
  "Engine Version": "+__OBJECT__.violations.__RULE__.result_info.0.object.engine_version+"
  "Instance Type": "+__OBJECT__.violations.__RULE__.result_info.0.object.db_instance_class+"
  "AWS Tags": "__TAGS__"  
~~~  

Here is an example of JSON output from this RDS audit-aws-rds table.yaml :  





