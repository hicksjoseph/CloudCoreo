

Extra phrases that can be worked back into the docs.



## Configuration Files
There are a few configuration files that exist in the CloudCoreo convention. These files are all able to be overridden.



------


Consider making boot scripts their own item.
Also consider making a document that gives an overview of ordering and all of the things that affect ordering
- extends (multiple extends?), overrides and anchors, convention, order.yaml

Make a boot scripts file and Add this along with more information about the boot scripts.
### Script Order
The configuration file that travels along with, and is located in, the `boot-scripts` directory is defined by the `order.yaml` file. The format is yaml, which means that tab indentations are an error. Here is an example:  

```  
order:  
    - install_packages.sh
    - run_chef.sh
```  

CloudCoreo will run (as root) each script in order. The process is to **chmod +x** the files and run with a **./<filename>** So make sure the shebang is correct.

-----


- extends    <-- runs 1st
- stack-joe  
  - extends  <-- runs 2nd
  -          <-- runs 3rd
- stack-tom
  - extends
  - 

Write this:
Using the CLI to extend a different stack.

-----

Create an advanced tricks and tips type of document that would contain stuff like this:
For instance, creating blank directories for dropping in bits of code and overrides will make everyone's life easier in the future. To help ease the administration efforts of creating these directories, use `composite-` in the CLI tool.

-------

The use of `stack-` directories can be very powerful for creating infrastructure, inlcuding constructs where you can include an `extends-` directory inside of a `stack-` directory or even have nested `stack-` directories. Learn more about this in [Composite Tricks and Tips](http://kb.cloudcoreo.com).  

## `extends` within a `stack-` directory


## nested `stack-` directories

Because you used a `stack-*` directory to the `<repository-dir>`, it will run **after** `<repository-dir>/extends`. Because you have added the stack to `<repository-dir>/stack-tomcat/extends` it will run **before** everything else inside the `stack-tomcat*` directory. Now, anyone utilizing your stack has a convenient place to insert configuration and setup between your stack and the added Tomcat composite.

When adding a composite, consider the needs of others who may extend and override your Composite in the future.

you can only have one "extends" in any "stack-" or root dir

if you have a "stack-" it can be looked at like another root
any "stack-" can have one "extends" and/or one or more "stack-" dirs


nested stack- directories
each stack- directory can have one extends directory in it

extends in a stack- directory runs the configuration in the extends directory before anything else in the stack- directory

stack- directories execute after extends but before anything else in current repository.

-------

Deterministic order: for stack- is done with extends/extends/extends

--------

This would go in a 201 level document:
The whole repo, including extends directories, gets copied down to each server? Even stuff unrelated to that server.

-------


boot-scripts / operational-scripts questions. We also need "agent" documentation. Not sure that we have even internal documentation on the agent yet. 

The whole repo gets copied down to each server? Even stuff unrelated to that server? Yes.

So each server gets a complete map of everything in the infrastructure? Yes.

So, if someone somehow hacks into one server and looks in `/opt/cloudcoreo/<plan-id>/repo/`, they will get a map to the entire deployment?
Yes.

Does it copy the stuff in extends directories?
Yes.

All extends are "followed" as part of a normal git clone and therefore copied down (especially if you have an extends/extends/extends directory where the 3rd extends boot-scripts run first.

Do you see this as a problem?
pallen: not really - if someone is on your system there are worse things to worry about

What happens if you have a lot of boot-scripts and it takes a long time to copy them to the server?

pallen: github 100MB limit.
joe: This is currently probably an edge case.

Will the server boot wait until the scripts are copied?

What is the piece of software that copies and executes the files?
(the agent of course, but I need more detail)

How exactly does the agent get there?

At what exact time in the boot process does the agent run these boot scripts?

What if there somehow happens to be a lack of space on the target server....or at least on the volume that we are copying stuff to?

We could probably copy the operational scripts out somewhere and then delete the repo directory on the server after the server has completed booting.

As an example, if your directory structure contains the following paths CloudCoreo will run each script in the `extends/composite-example/extends/boot-scripts/order.yaml` file before moving on to the `extends/composite-example/boot-scripts/order.yaml`:

* `extends/composite-example/extends/boot-scripts`
* `extends/composite-example/boot-scripts`

As a matter of fact, each of the scripts in the base directory can be overridden at any point.

-----

Operational scripts:
Paul: For operational scripts, is this sentence 100% true with regard to order? The structure and scripts within this directory honor the order and overrides defined within the rest of this document.

For example, if you have an operational script in an extends directory, will it take precedence over an operational script of the same name somewhere else lower in the order?

This behavior should be tested to see what happens.

------

shutdown-scripts
The structure and scripts within this directory honor the order and overrides defined within the rest of this document.

This behavior should be tested to see what happens.

-------

### overrides
Anything contained in this directory will act as an override for the composite in which it is contained.

The paths should be considered relative to the parent of this directory.

If you have a directory structure like this...

```
+-- parent
|   +-- overrides
|   |   +-- composite-a
|   |   |   +-- boot-scripts
|   |   |   |   +-- order.yaml
|   +-- composite-a
|   |   +-- boot-scripts
|   |   |   +-- order.yaml
```
The `order.yaml` file will be ignored in the `composite-a directory`, and instead the `overrides/composite-a order.yaml` file will be used, because the directory structure within the override directory matches the structure of the parent.








