

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

-----


From Composite Creation:
-----
Put this back in:

As you build new Composites, you will need to reference the [*CloudCoreo API Documentation*](http://beta.api.docs.cloudcoreo.com/docs/frames) to know what options and parameters that you can use in your Composites.  


--------

This section was taken from the Variables Concept Doc:

Variables allow a user to create many copies of CloudCoreo stacks without creating conflict (unless conflict is desired, of course). 

This is the original example that includes the overrides.

~~~  
variables:
  MY_DNS_ZONE:
    default: cloudcoreo.com
    description: this dns zone variable is used for setting up route53 entries
    required: true
    type: string
    overrides:
      - stack-tomcat:DNS_ZONE
  SWAP_SIZE_IN_GB:
    default: 2
    description: create a swap file of this size in gigabytes
    required: false
    type: number
  SERVER_AMI:
    description: the ami to launch
    switch: INSTANCE::region
    cases:
      us-east-1: ami-1ecae776
      us-west-1: ami-d114f295
      us-west-2: ami-e7527ed7
    type: case
~~~  

--------

This section was taken from the Variables Concept Doc. Add it to an advanced overrides document and then add the link to the overrides doc to the Variables Concept Doc 

### property: overrides
Overrides allow you to effectively take ownership of or rename a variable used in extended stacks. This is useful if your stack includes multiples of the same stack but you wish the variables to be set differently.

In the following stack structure `my-stack` is the the one being created. Also, the same stack has been added twice, perhaps a web server and a scheduler. The directory structure might look like this:
```
my-stack/
├── config.yaml
├── stack-scheduler
│   └── config.yaml
└── stack-webserver
    └── config.yaml
```
Both of these `stack-*` directories are pointers to the exact same external stack.

Now, look at the `config.yaml` in the `stack-*` directories. Knowing that each of these stacks are identical, we also know that the `config.yaml` files are identical. Check it out:
```
variables:
  DNS_ENTRY:
    default: my-server.example.com
    required: true
    type: string
    description: this is the dns record to assign to the server
```

Adding the `DNS_ENTRY` variable to your top level under-your-control `config.yaml` file allows you to override all of the `DNS_ENTRY` values below you. This is global though, meaning that it will change **both** the `stack-scheduler` value and the `stack-webserver` value, as well as anything below them.

Here, both stacks will get the same variable, which isn't good in this case. Assuming this variable is used to manage DNS, it means that the DNS records will stomp on each other and one record won't have an entry.

We can't have that! The answer is `overrides`.

When you add an overrides property to a `config.yaml` file in the `<stack>::<name>` format, it modifies the variable(s) it calls out, and *only* those variables. It also modifies the variable **starting in the stack**, and then everything from that stack down. If the `<stack>::` is left out, it will modify the variable in all stacks. Let's whip up an example with our directory structure:
```
my-stack/
├── config.yaml      | empty file
├── stack-scheduler
│   └── config.yaml  | DNS_ENTRY variable, default "my-server.example.com"
└── stack-webserver 
    └── config.yaml  | DNS_ENTRY variable, default "my-server.example.com"
```
We can *override* this by adding a new variable to the top level `config.yaml` file, calling out an override on `DNS_ENTRY`. So:
```
MY_NEW_DNS:
  overrides:
    - DNS_ENTRY
  default: my-new-dns.example.com
```
Whatever the `MY_NEW_DNS` variable is set to will also be propagated down to all `DNS_ENTRY` values in all stacks added 'under' this `config.yaml`. Any stack inheriting or adding this stack must use `MY_NEW_DNS` because `DNS_ENTRY` effectively no longer exists (it has been overridden).

If the `<stack>::` notation is used the same rules apply, but this time only to the stack(s) it calls out. For instance, if you change our override property slightly:
```
MY_NEW_DNS:
  overrides:
    - stack-scheduler::DNS_ENTRY
  default: my-new-dns.example.com
```
You will have added a `stack-scheduler::` prefix to the overrides `DNS_ENTRY` entry. This will override `DNS_ENTRY` within the `stack-scheduler` and ***not*** in the `stack-webserver`. The `stack-webserver` will still honor any entries for `DNS_ENTRY` and will know nothing of the `MY_NEW_DNS` variable that has been added.

This section was taken from the Variables Concept Doc. Add this right back in after git push

#### string
The `string` type is fairly self-explanatory. This expects a string value and will treat the validation as such.
#### number
The `number` type validates numbers. This can be integers, floats etc.
#### array
The `array` type expects arrays in the yaml file. It will also display in the web-ui as a list.
#### case
The `case` type is used in order to select values without asking the user for input. For instance:

```
MY_SWAP_GB:
  switch: SIZE
    cases:
      m3.medium: 1
      m3.large: 1.5
      m3.xlarge: 2
    type: case
```
In this case an AMI will be selected based on the region. The user has no option of which AMI is selected, but instead it is selected for them based on the value of the region.



### Instance Variables
Instance variables are variables set by the AppStack that is actually running. You can use them simply by adding the `INSTANCE::` prefix to the variable you wish to use.
#### `INSTANCE::region`
This will return a string representing the region in which the AppStack instance is requested to run.

### Stack Variables
Stack variables are set during runtime and can be used to access various values created during the stack creation/update runtime. Access STACK variables using `STACK::`.
