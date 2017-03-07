---
title: CloudCoreo Runtime Variables
summary: CloudCoreo Runtime Variables
tags:
keywords: ""
last_updated: "March 7, 2017"
published: true
sidebar: conceptdocs_sidebar
permalink: conceptdocs_runtimevariables.html
folder: conceptdocs
toc: false
---

**Note:** Be careful when you edit your config files since these files **cannot contain tab characters**. When you do line spacing, use spaces instead.  

## Runtime Variables  

There are several collections of variables which can be used in authoring composites that are evaluated at run time. These Runtime Variables are different than [compile time variables.](http://kb.cloudcoreo.com/conceptdocs_variables.html)  

### Plan Runtime Variables  

Variables in the `PLAN::` namespace are read-only and contain information about the currently running plan.  
**Valid `PLAN::` variable names are:**  

|Variable Name |Variable Description|
|:------|:-----------|
|**PLAN::run_id**             |The id of the current execution for this plan|  
|**PLAN::team_id**            |The id of the team which is running this plan|  
|**PLAN::team_name**          |The name of the team wich is running this plan|  
|**PLAN::cloud_account_name** |The name of the cloud account assigned to this plan|  
|**PLAN::cloud_account_id**   |The id of the cloud account assigned to this plan|  
|**PLAN::cloud_account_arn**  |The ARN in AWS for the cloud account assigned to this plan|  
|**PLAN::revision**           |The git commit SHA for the composite being executed by this plan|  
|**PLAN::branch**             |The git branch name for the composite being executed by this plan|  
|**PLAN::id**                 |The id of this plan|  
|**PLAN::name**               |The name of this plan|  
|**PLAN::stack_name**         |The name of this composite|  
|**PLAN::region**             |The AWS region that this plan is being executed in|  

#### Example 1: Setting the default region for a variable in config.yaml  

~~~ ruby  
       variables:
         REGION:
           default: "PLAN::region"
           required: true
          type: string
~~~  

#### Example 2:  Using the Plan name for naming resources  
Consider using a dash "-" character to separate the variable from additional text.  
Note that the variable name must be separated from other text by characters that are not regular letters or an underscore "_" character.

~~~ ruby  
       coreo_aws_vpc_vpc "PLAN::name-vpc" do
        # actions and attributes here
      end
~~~  

For a Plan that is named "TEST", the code block above will resolve the resource name to "TEST-vpc".  


### Composite Runtime Variables  

Variables in the `COMPOSITE::` namespace are read/write and must be scoped to an existing resolved resource. These are identified as `COMPOSITE::coreo_resource_type.resource_name.variable_name` where `variable_name` may be arbitrarily nested using dot notation.  

These variables must be set using the `coreo_uni_util_variables` resource _after_ that resource has been executed.

**Important:** Setting COMPOSITE variables will not alter the deployed state of a resource since variable setting occurs after the resource has been executed.

#### Example:
Capture the run time of jsrunner script variables that are exported by the jsrunner function `coreoExport()` and are automatically stored in a `COMPOSITE::` variable on the jsrunner resource.  

~~~ ruby  
  coreo_uni_util_jsrunner "my_js_runner" do
    acion :run
    function <<-JAVASCRIPT
let startTime = Date.now();

// JSRunner behavior here

coreoExport('startTime', startTime);
coreoExport('endTime', Date.now());
    JAVASCRIPT

    # other jsrunner methods as needed
  end

  coreo_uni_util_variables "js_runner_vars" do
    action :set
    variables [
      { 'COMPOSITE::coreo_uni_util_jsrunner.my_js_runner.runtime' =>
          'COMPOSITE::coreo_uni_util_jsrunner.my_js_runner.endTime' - 'COMPOSITE::coreo_uni_util_jsrunner.my_js_runner.startTime' }
    ]
  end
~~~  

### Global Runtime Variables  

Variables in the `GLOBAL::` namespace are read/write, always user-generated, and do not need to be scoped to a resource. These can be used for storing metadata or aggregated information about other resources. GLOBAL variables can be nested map/hash data structures.  

#### Example:
Sum violations from multiple jsrunner resources  

~~~ ruby  
  coreo_uni_util_jsrunner "first_jsrunner" do
    action :run
    function <<-JAVASCRIPT1
let violations = 0;

// JSRunner behavior which counts violations and increments the variable

coreoExport('violations', violations);
    JAVASCRIPT1
  end

  coreo_uni_util_jsrunner "second_jsrunner" do
    action :run
    function <<-JAVASCRIPT2
let violations = 0;

// JSRunner behavior which counts violations and increments the variable

coreoExport('violations', violations);
    JAVASCRIPT2
  end

  coreo_uni_util_variables "violations" do
    action :set
    variables [
      { 'GLOBAL::jsrunner_rollups.violations' =>
          'COMPOSITE::coreo_uni_util_jsrunner.first_jsrunner.violations' + 'COMPOSITE::coreo_uni_util_jsrunner.second_jsrunner.violations' }
    ]
  end
~~~  

Remember that runtime variables are different than Compile Time Variables. Read more about [Compile Time Variables here.](http://kb.cloudcoreo.com/conceptdocs_variables.html)  
