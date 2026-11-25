This appendix is a reference for Oracle Clusterware resources. This appendix includes descriptions and usage examples of resource attributes and detailed descriptions and examples of resource attribute action scripts. This appendix includes the following topics:

- Resource Attributes

- Examples of Action Scripts for Third-party Applications

### Resource Attributes

This section lists and describes attributes used when you register applications as resources in Oracle Clusterware. Use these attributes with the `crsctl add resource` command, as follows:

    $ crsctl add resource resource_name -type resource_type -group group_name
    {[-attr "attribute_name='attribute_value', attribute_name='attribute_value'
    , ..."] | [-file file_name]}

List attribute-value pairs in a comma-delimited list after the `-attr` flag and enclose the value of each attribute in single quotation marks (`''`). Some resource attributes you cannot configure and are read only.

Alternatively, you can create a text file that contains the attribute-value pairs. For example:

    PLACEMENT=favored
    HOSTING_MEMBERS=node1 node2 node3
    RESTART_ATTEMPTS@CARDINALITYID(1)=0
    RESTART_ATTEMPTS@CARDINALITYID(2)=0
    FAILURE_THRESHOLD@CARDINALITYID(1)=2
    FAILURE_THRESHOLD@CARDINALITYID(2)=4
    FAILURE_INTERVAL@CARDINALITYID(1)=300
    FAILURE_INTERVAL@CARDINALITYID(2)=500
    CHECK_INTERVAL=2
    CARDINALITY=2

**Note:**

The length limit for these attributes is 254 characters.

This section includes the following topics:

- Configurable Resource Attributes

- Read-Only Resource Attributes

#### Configurable Resource Attributes

This section describes the following resource attributes that you can configure when registering an application as a resource in Oracle Clusterware:

**Note:**

Values for all attributes must be in lowercase. Attribute names must be in all uppercase letters.

- ACL

- ACTION_SCRIPT

- ACTION_TIMEOUT

- ACTIONS

- ACTIVE_PLACEMENT

- AGENT_FILENAME

- ALERT_TEMPLATE

- AUTO_START

- CARDINALITY

- CARDINALITY_ID

- CHECK_INTERVAL

- CHECK_TIMEOUT

- CLEAN_TIMEOUT

- CRITICAL_RESOURCES

- DELETE_TIMEOUT

- DESCRIPTION

- ENABLED

- FAILURE_INTERVAL

- FAILURE_THRESHOLD

- HOSTING_MEMBERS

- INSTANCE_FAILOVER

- INTERMEDIATE_TIMEOUT

- LOAD

- MODIFY_TIMEOUT

- NAME

- OFFLINE_CHECK_INTERVAL

- ONLINE_RELOCATION_TIMEOUT

- PLACEMENT

- RELOCATE_BY_DEPENDENCY

- RELOCATE_KIND

- RESTART_ATTEMPTS

- SCRIPT_TIMEOUT

- SERVER_CATEGORY

- SERVER_POOLS

- START_CONCURRENCY

- START_DEPENDENCIES

- START_TIMEOUT

- STOP_CONCURRENCY

- STOP_DEPENDENCIES

- STOP_TIMEOUT

- UPTIME_THRESHOLD

- USER_WORKLOAD

- USE_STICKINESS

##### ACL

ACL defines the owner of a resource and the access privileges granted to various operating system users and groups. The resource owner defines the operating system user of the owner and its privileges.

You configure this optional attribute when you create a resource. If you do not configure this attribute, then the value is based on the identity of the process creating the resource. You can change the value of the attribute if such a change is allowed based on the existing privileges of the resource.

**Note:**

All operating system user names and user groups, including `owner`, `pgrp`, `user`, and `group`, must be registered on all servers in the cluster.

In the string:

- `owner`: The operating system user who owns a resource and the user under which the action script or application-specific agent runs, followed by the privileges of the owner.

- `pgrp`: The operating system group that is the primary group of the owner of a resource, followed by the privileges of members of the primary group.

- `other`: Operating system users that are neither the owner nor member of the primary group

- `r`: The read option, which gives the ability to only see a resource, its state, and configuration

- `w`: The write option, which gives the ability to modify a resource's attributes and to delete the resource

- `x`: The execute option, which gives the ability to start, stop, and relocate a resource

By default, the identity of the client that creates a resource is the `owner`. Also by default, `root`, and the user specified in `owner` have full privileges. You can grant required operating system users and operating system groups their privileges by adding the following lines to the `ACL` attribute:

    user:user_name:rwx
    group:group_name:rwx

##### Usage Example

    ACL=owner:user_1:rwx,pgrp:osdba:rwx,other::r-

In the preceding example, the owner of the resource is `user_1`, whose primary group is `osdba`. The user, `user_1`, has all privileges, as does the `osdba` group, while other users can only view the resource.

##### ACTION_SCRIPT

An absolute file name that includes the path and file name of an action script. The agent specified in the `AGENT_FILENAME` attribute calls the script specified in the `ACTION_SCRIPT` attribute.

##### Usage Example

    ACTION_SCRIPT=fully_qualified_path_to_action_script

##### ACTION_TIMEOUT

A single timeout value, in seconds, for all supported actions that Oracle Clusterware can perform on a resource.

##### Usage Example

    ACTION_TIMEOUT=30

##### ACTIONS

The `ACTIONS` attribute declares a table of names that lists the actions that Oracle Clusterware can perform on a resource and the permissions that correspond to the actions. The `ACTIONS` attribute contains a space-delimited list of action specifications, where each specification has the following format, where:

- `actionName` is the name of the action (the maximum length is 32 US7ASCII alphanumeric, case-sensitive characters)

- `userName` is an operating system user name that is enabled to perform the action

- `groupName` is an operating system group name that is enabled to perform the action

<!-- -->

    actionName [,user:userName | group:groupName][ ...]

If you do not specify a `userName` or `groupName`, then Oracle Clusterware assumes that the actions are universally accessible.

##### Usage Example

The following example enables multiple actions:

    ACTIONS='action1 action2,user:user2 action3,group:group1'

##### ACTIVE_PLACEMENT

When set to `1`, Oracle Clusterware uses this attribute to reevaluate the placement of a resource during addition or restart of a cluster server. For resources where `PLACEMENT=favored`, Oracle Clusterware may relocate running resources if the resources run on a non-favored server when a favored one joins the cluster.

##### Usage Example

    ACTIVE_PLACEMENT=1

##### AGENT_FILENAME

A fully qualified file name of an agent program that a resource type uses to manage its resources. Every resource type must have an agent program to manage its resources. Resource types use agent programs by either specifying a value for this attribute or inheriting it from their base resource type. There are two script agents included with Oracle Clusterware 12c and later releases: `application` and `scriptagent`. Oracle Clusterware uses the `application` script agent for resources of the deprecated `application` resource type. The default value for this attribute is `scriptagent`.

**Note:**

Once the resource is created, you can no longer modify this attribute.

##### Usage Example

    AGENT_FILENAME=%Grid_home%/bin/application

##### ALERT_TEMPLATE

Use to specify additional resource attributes that are to be included in resource state alert messages. You can specify the attribute as a space-delimited list of resource attributes. These attributes must be accessible from the resource type to display in alert messages.

##### Usage Example

    ALERT_TEMPLATE="DESCRIPTION HOSTING_MEMBERS"

##### AUTO_START

Indicates whether Oracle Clusterware automatically starts a resource after a cluster server restart. Valid `AUTO_START` values are:

- `always`: Restarts the resource when the server restarts regardless of the state of the resource when the server stopped.

- `restore`: Restores the resource to the same state that it was in when the server stopped. Oracle Clusterware attempts to restart the resource if the value of `TARGET` was `ONLINE` before the server stopped.

- `never`: Oracle Clusterware never restarts the resource regardless of the state of the resource when the server stopped.

##### CARDINALITY

The number of servers on which a resource or resource group can run, simultaneously. This is the upper limit for resource cardinality.

##### Usage Example

    CARDINALITY=1

You can also use a value such that cardinality always increases and decreases with the number of servers that are assigned to the server pool in which the resource or resource group is configured to run. The values are:

    CARDINALITY=%CRS_SERVER_POOL_SIZE%
    CARDINALITY=%CRS_HUB_SIZE%

Only resources with `PLACEMENT=restricted` and that use the `SERVER_POOLS` attribute can use this value.

##### CARDINALITY_ID

An integer different for each of the INSTANCE_COUNT resource instances.

The value for this parameter varies from 1 to CARDINALITY\*2. The number of resource instances can be greater than that of the value of CARDINALITY only when you use online relocation (RELOCATE_KIND=online), or if you decrease the resource instance count.

##### CHECK_INTERVAL

The time interval, in seconds, between repeated executions of the `check` action. Shorter intervals enable more frequent checks but also increase resource consumption if you use the script agent. Use an application-specific agent to reduce resource consumption.

##### Usage Example

    CHECK_INTERVAL=60

##### CHECK_TIMEOUT

The maximum time, in seconds, in which a check action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify this attribute or if you specify 0 seconds, then Oracle Clusterware uses the value of the `SCRIPT_TIMEOUT` attribute.

##### Usage Example

    CHECK_TIMEOUT=30

##### CLEAN_TIMEOUT

The maximum time, in seconds, in which a clean action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify a value for this attribute or you specify `0` seconds, then Oracle Clusterware uses the value of the `STOP_TIMEOUT` attribute.

##### Usage Example

    CLEAN_TIMEOUT=30

##### CRITICAL_RESOURCES

Resource group attribute that contains a list of resources marked critical for a resource group.

You specify a space-delimited list of critical resources in the CRITICAL_RESOURCES attribute of a resource group. Use this attribute for both local and cluster resource group types. You can add a `type:` option followed by a resource type name to indicate that all member resources of the specified type are critical resources of the group.

Example B-1 Usage Examples

    CRITICAL_RESOURCES="r1 r2 r3"
    CRITICAL_RESOURCES="appvip type:ora.export.type"

##### DELETE_TIMEOUT

The maximum time, in seconds, in which a delete action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify a value for this attribute or you specify `0` seconds, then Oracle Clusterware uses the value of the SCRIPT_TIMEOUT attribute.

##### Usage Example

    DELETE_TIMEOUT=30

##### DESCRIPTION

Enter a description of the resource you are adding.

##### Usage Example

    DESCRIPTION=Apache Web server

##### ENABLED

Oracle Clusterware uses this attribute to manage the state of the resource. Oracle Clusterware does not attempt to manage a disabled (`ENABLED=0`) resource either directly or because of a dependency to another resource. A disabled resource cannot be started but it can be stopped. Oracle Clusterware does not actively monitor disabled resources, meaning that Oracle Clusterware does not check their state.

##### Usage Example

    ENABLED=1

##### FAILURE_INTERVAL

The interval, in seconds, before which Oracle Clusterware stops a resource if the resource has exceeded the number of failures specified by the `FAILURE_THRESHOLD` attribute. If the value is zero (`0`), then tracking of failures is disabled.

##### Usage Example

    FAILURE_INTERVAL=30

##### FAILURE_THRESHOLD

The number of failures of a resource detected within a specified `FAILURE_INTERVAL` for the resource before Oracle Clusterware marks the resource as unavailable and no longer monitors it. If a resource fails the specified number of times, then Oracle Clusterware stops the resource. If the value is zero (`0`), then tracking of failures is disabled. The maximum value is `20`.

##### Usage Example

    FAILURE_THRESHOLD=3

##### HOSTING_MEMBERS

A space-delimited, ordered list of cluster server names that can host a resource. This attribute is required only when using administrator management, and when the value of the `PLACEMENT` attribute is set to `favored` or `restricted`. When registering applications as Oracle Clusterware resources, use the `SERVER_POOLS` attribute, instead.

**Note:**

For resources of `application` type, Oracle Clusterware places servers listed in the `HOSTING_MEMBERS` attribute in the Generic server pool.

**See Also:**

- "[Default Server Pools](policy-based-cluster-and-capacity-management.md) " for more information about the Generic server pool

- "LOAD" for more information about this attribute

- "PLACEMENT" for more information about this attribute

To obtain a list of candidate node names, run the `olsnodes` command to display a list of your server names.

##### Usage Example

    HOSTING_MEMBERS=server1 server2 server3

##### INSTANCE_FAILOVER

Use the `INSTANCE_FAILOVER` attribute for resources of type `CLUSTER_RESOURCE`. Using this attribute enables you to disallow the failover of resource instances from the servers on which they fail. This enables you to bind the resource to a particular server.

Set to `0` to disable instance failover.

##### Usage Example

    INSTANCE_FAILOVER=1

##### INTERMEDIATE_TIMEOUT

Denotes the maximum amount of time in seconds that a resource can remain in the `INTERMEDIATE` state before the resource is declared as failed. The value of `INTERMEDIATE_TIMEOUT` must be greater than `0` to take effect.

##### Usage Example

    INTERMEDIATE_TIMEOUT=60

##### LOAD

Oracle Clusterware interprets the value of this attribute along with that of the `PLACEMENT` attribute. When the value of `PLACEMENT` is `balanced`, the value of `LOAD` determines where best to place a resource. A nonnegative, numeric value that quantitatively represents how much server capacity an instance of a resource consumes relative to other resources. Oracle Clusterware attempts to place resources on servers with the least total load of running resources.

##### Usage Example

    LOAD=1

##### MODIFY_TIMEOUT

The maximum time, in seconds, in which a modify action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify a value for this attribute or you specify `0` seconds, then Oracle Clusterware uses the value of the `SCRIPT_TIMEOUT` attribute.

##### Usage Example

    MODIFY_TIMEOUT=30

##### NAME

A case-sensitive alphanumeric string that names the resource. Oracle recommends a naming convention that starts with an alphanumeric prefix, such as `myApache`, and complete the name with an identifier to describe it. A resource name can contain any platform-supported characters except the exclamation point (!) and the tilde (~). A resource name cannot begin with a period (.) nor with the string ora.

##### Usage Example

    NAME=myApache

##### OFFLINE_CHECK_INTERVAL

Controls offline monitoring of a resource. The value represents the interval (in seconds) that Oracle Clusterware monitors a resource when its state is `OFFLINE`. Monitoring is disabled if the value is `0`.

##### Usage Example

    OFFLINE_CHECK_INTERVAL=30

##### ONLINE_RELOCATION_TIMEOUT

The amount of time (minutes) after the relocated instance starts and services are migrated, before the former instance of the service stops. The default value is 30 minutes.

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-oracle-rac-one-node.md) for information about online database relocation

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for information about `srvctl` `relocate` `database`

##### PLACEMENT

Specifies how Oracle Clusterware selects a cluster server on which to start a resource. Valid values are `balanced`, `favored`, or `restricted`.

If you set the `PLACEMENT` attribute to `favored` or `restricted`, then you must also assign values to the `SERVER_POOLS` and `HOSTING_MEMBERS` attributes. If you set the value of the `PLACEMENT` attribute to `balanced`, then the `HOSTING_MEMBERS` attribute is not required.

**See Also:**

- "[Application Placement Policies](making-applications-highly-available-using-oracle-clusterware.md)" for more information about the `PLACEMENT` attribute

- "HOSTING_MEMBERS" for more information about this attribute

- "SERVER_POOLS" for more information about this attribute

##### Usage Example

    PLACEMENT=favored

##### RELOCATE_KIND

Use to control how a resource is relocated. During an offline relocation operation, the target resource instance is stopped on the source server and subsequently started on the destination server. An online relocation operation first starts the resource instance on the destination server before stopping it on the source server. Start-only starts the resource instance on the destination server, but will not stop the resource instance on the source server. Instead, the agent stops the resource instance once the relocate is complete.

You can choose either `offline/0`, `online/1`, or `start-only/2` as a value for this parameter.

##### Usage Examples

    RELOCATE_KIND=1
    RELOCATE_KIND=start-only

##### RELOCATE_BY_DEPENDENCY

Use to declare whether a resource will be enabled for relocation if requested to do so because of a dependency on the resource for which the relocation was requested. If 0, the resource will not be allowed to relocate because of a dependency on the resource for which relocate request was issued. The valid values are `1` or `0`.

##### Usage Example

    RELOCATE_BY_DEPENDENCY=1

##### RESTART_ATTEMPTS

The number of times that Oracle Clusterware attempts to restart a resource on the resource's current server before attempting to relocate it. A value of `1` indicates that Oracle Clusterware only attempts to restart the resource once on a server. A second failure causes Oracle Clusterware to attempt to relocate the resource. A value of `0` indicates that there is no attempt to restart but Oracle Clusterware always tries to fail the resource over to another server.

##### Usage Example

    RESTART_ATTEMPTS=2

##### SCRIPT_TIMEOUT

The maximum time (in seconds) for an action to run. Oracle Clusterware returns an error message if the action script does not complete within the time specified. The timeout applies to all actions (`start`, `stop`, `check`, and `clean`).

##### Usage Example

    SCRIPT_TIMEOUT=45

##### SERVER_CATEGORY

For local resources, the definition of a `local_resource` type is extended to be category-aware. In other words, you can restrict local resources to belong to a particular server category. For cluster resources, the value for the `SERVER_CATEGORY` attribute always functions with the value for the `PLACEMENT` attribute. Set `SERVER_POOLS` to `*` when `PLACEMENT` is restricted and `SERVER_CATEGORY` is used. If you set `PLACEMENT` to `restricted`, then Oracle Clusterware expects one of the following attributes to also be set:

- `HOSTING_MEMBERS`

- `SERVER_POOLS`

- `SERVER_CATEGORY`

For example, a resource, known as `resource1,` can have a policy that sets the value of `PLACEMENT` to be `restricted`, and `SERVER_CATEGORY` is set to `HubCategory`. In such a case, Oracle Clusterware would only enable `resource1` to run on the servers that belong to the `HubCategory`.

If `PLACEMENT` is set to `favored` and if only one of `HOSTING_MEMBERS`, `SERVER_POOLS`, or `SERVER_CATEGORY` is set, then that value expresses a preference. If `HOSTING_MEMBERS` is populated and one of `SERVER_POOLS` or `SERVER_CATEGORY` is set, then the `HOSTING_MEMBERS` indicates placement preference and `SERVER_POOLS` or `SERVER_CATEGORY` indicates a restriction. For example, the `ora.cluster.vip` resource can have a policy that sets the value of `PLACEMENT` to `favored`, and `SERVER_CATEGORY` is set to `HubCategory` and `HOSTING_MEMBERS` is set to `server_name1`. In such a case, Oracle Clusterware restricts the placement of `ora.cluster.vip` to the servers in the `HubCategory` and then it prefers the server known as `server_name1`.

##### Usage Example

    SERVER_CATEGORY=my_category

##### SERVER_POOLS

The SERVER_POOLS resource attribute is described.

A space-delimited list of the server pools to which a particular resource can belong. If a resource can run on any server in a cluster, then use the default value, `*`, unless the resource is a `cluster_resource` type, in which case, the default value for the `SERVER_POOLS` attribute is empty. Only cluster administrators can specify `*` as the value for this attribute.

- Use the `PLACEMENT` attribute with the `SERVER_POOLS` attribute, as follows: If you set the value of the `PLACEMENT` attribute to either `restricted` or `favored`, then you must also provide a value for the `SERVER_POOLS` attribute when using policy management for the resource.

- If the value for `PLACEMENT` is set to `balanced`, then the resource only runs in the Generic and Free pools, unless `SERVER_POOLS=*`.

This attribute creates an affinity between a resource and one or more server pools regarding placement, and depends on the value of the `PLACEMENT` attribute.

##### Usage Example

    SERVER_POOLS=pool1 pool2 pool3

**See Also:**

- [Policy-Based Cluster and Capacity Management](policy-based-cluster-and-capacity-management.md) for more information about server pools

  "[Role-Separated Management](oracle-clusterware-administration.md)" for more information about cluster administrators

- "HOSTING_MEMBERS" for more information about this attribute

- "PLACEMENT" for more information about this attribute

##### START_CONCURRENCY

Describes the maximum number of start actions that can be concurrent at a time. A value of `0` means “no limit."

##### Usage Example

    START_CONCURRENCY=10

##### START_DEPENDENCIES

Specifies a set of relationships that Oracle Clusterware considers when starting a resource. You can specify a space-delimited list of dependencies on several resources and resource types on which a particular resource can depend.

##### Syntax

    START_DEPENDENCIES=dependency(resource_set) [dependency(resource_set)] [...]

In the preceding syntax example the variables are defined, as follows:

- `dependency`: Possible values are `attraction`, `dispersion`, `exclusion`, `hard`, `pullup`, and `weak`. You can specify each dependency only once, except for `pullup`, which you can specify multiple times.

- `resource_set`: A comma-delimited list of resource entities—either individual resources or resource types—enclosed in parentheses `()`, in the form of `res1[, res2[, ...]]`, upon which the resource you are configuring depends.

  Each resource entity is defined, as follows:

      [modifier1:[modifier2:]] {resource_name | type:resource_type}

  In the preceding syntax example, `resource_name` is the name of a specific resource and `type:``resource_type` is the name of a specific resource type. The resource type must be preceded by `type` and the `type` modifier must be the last resource entity in the list.

  Optionally, you can specify modifiers to further configure resource entity dependencies. You can modify each dependency by prefixing the following modifiers to the resource entity:

  - `attraction([intermediate:]{``resource_name`` | ``type:``resource_type``})`—Use the `attraction` start dependency when you want this resource to run on the same server with a particular named resource or any resource of a particular type.

    Use `intermediate` to specify that this resource is attracted to resource entities on which it depends that are in the `INTERMEDIATE` state. If not specified, then resources must be in the `ONLINE` state to attract the dependent resource.

    If you specify the `attraction` dependency on a resource type for a resource, then any resource of that particular type attracts the dependent resource.

  - `exclusion([[preempt_pre: | preempt_post:]]` `target_resource_name`` | type:``target_resource_type``])`—Use the `exclusion` start dependency to keep resources with this dependency from running on the same node.

    Use the `preempt_pre` modifier to configure the `exclusion` dependency to stop the specified target resource or resources defined by a specific resource type before starting the source resource.

    Use the `preempt_post` modifier to configure the `exclusion` dependency to stop and relocate, if possible, the specified target resource or resources defined by a specific resource type after starting the source resource.

  - `dispersion[:active]([intermediate:][pool:]{``resource_name`` | ``type:``resource_type``})`—Specify the `dispersion` start dependency for a resource that you want to run on a server that is different from the named resources or resources of a particular type. Resources may still end up running on the same server, depending on availability of servers.

    Use the `active` modifier to configure the `dispersion` dependency so that Oracle Clusterware attempts to relocate the dependent resource to another server if it is collocated with another resource and another server comes online. Oracle Clusterware does not relocate resources to newly available servers unless you specify the `active` modifier.

    Use the `intermediate` modifier to specify that Oracle Clusterware can relocate the dependent resource if a resource is in either the `ONLINE` or `INTERMEDIATE` state. If not specified, then resources must be in the `ONLINE` state for dispersion of the dependent resource to occur.

    Use the `pool` modifier if you want a resource to be located in a different server pool than the target, rather than just a different server.

  - `hard([intermediate:][global:][uniform:]{``resource_name`` | ``type:``resource_type``})`—Specify a `hard` start dependency for a resource when you want the resource to start only when a particular resource or resource of a particular type starts.

    Use the `intermediate` modifier to specify that Oracle Clusterware can start this resource if a resource on which it depends is in either the `ONLINE` or `INTERMEDIATE` state. If not specified, then resources must be in the `ONLINE` state for Oracle Clusterware to start this resource.

    Use the `global` modifier to specify that resources are not required to reside on the same server as a condition to Oracle Clusterware starting this resource. If not specified, then resources must reside on the same server for Oracle Clusterware to start this resource.

    Use the `uniform` modifier to attempt to start all instances of resource B, but only one instance, at least must start to satisfy the dependency.

    If you specify the `hard` dependency on a resource type for a resource, then the resource can start if any resource of that particular type is running.

    **Note:**

    Oracle recommends that resources with `hard` start dependencies also have `pullup` start dependencies.

  - `pullup[:always]([intermediate:][global:]{``resource_name`` | ``type:``resource_type``})`—When you specify the `pullup` start dependency for a resource, then this resource starts because of named resources starting.

    Use the `always` modifier for `pullup` so that Oracle Clusterware starts this resource despite the value of its `TARGET` attribute, whether that value is `ONLINE` or `OFFLINE`. Otherwise, if you do not specify the `always` modifier, then Oracle Clusterware starts this resource only if the value of the `TARGET` attribute is `ONLINE` for this resource.

    Use the `intermediate` modifier to specify that Oracle Clusterware can start this resource if a resource on which it depends is in either the `ONLINE` or `INTERMEDIATE` state. If not specified, then resources must be in the `ONLINE` state for Oracle Clusterware to start this resource.

    Use the `global` modifier to specify that resources on which this resource depends are not required to reside on the same server as a condition to Oracle Clusterware starting this resource. If not specified, then resources on which this resource depends must reside on the same server for Oracle Clusterware to start this resource.

    If you specify the `pullup` dependency on a resource type for a resource, then, when any resource of that particular type starts, Oracle Clusterware can start this resource.

    **Note:**

    Oracle recommends that resources with `hard` start dependencies also have `pullup` start dependencies.

  - `weak([concurrent:][global:][uniform:]{``resource_name`` | ``type:``resource_type``})`—Specify a `weak` start dependency for a resource when you want that resource to start despite whether named resources are running, or not. An attempt to start this resource also attempts to start any resources on which this resource depends if they are not running.

    Use the `concurrent` modifier to specify that Oracle Clusterware can start a dependent resource while a resource on which it depends is in the process of starting. If `concurrent` is not specified, then resources must complete startup before Oracle Clusterware can start the dependent resource.

    Use the `global` modifier to specify that resources are not required to reside on the same server as a condition to Oracle Clusterware starting the dependent resource.

    Use the `uniform` modifier to start all instances of the resource everywhere the resource can run. If you do not specify a modifier (the default), then the resource starts on the same server as the resource on which it depends.

    If you specify the `weak` start dependency on a resource type for a resource, then the resource can start if any resource of that particular type is running.

**See Also:**

"[Start Dependencies](making-applications-highly-available-using-oracle-clusterware.md)" for more details about start dependencies

##### START_TIMEOUT

The maximum time (in seconds) in which a start action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify a value for this attribute or you specify `0` seconds, then Oracle Clusterware uses the value of the `SCRIPT_TIMEOUT` attribute.

##### Usage Example

    START_TIMEOUT=30

**See Also:**

"SCRIPT_TIMEOUT" for more information about this attribute

##### STOP_CONCURRENCY

Describes the maximum number of stop actions that can be concurrent at a time. A value of `0` means “no limit."

##### Usage Example

    STOP_CONCURRENCY=10

##### STOP_DEPENDENCIES

Specifies a set of relationships that Oracle Clusterware considers when stopping a resource.

##### Syntax

    STOP_DEPENDENCIES=dependency(resource_set) [dependency(resource_set)] ...

In the preceding syntax example the variables are defined, as follows:

- `dependency`: The only possible value is `hard`.

- `resource_set`: A comma-delimited list, in the form of `res1[, res2 [,...]]`, of resource entities—either individual resources or resource types—upon which the resource you are configuring depends.

  Each resource entity is defined, as follows:

      [modifier1:[modifier2:][modifier3:]] resource_name | type:resource_type

  In the preceding syntax example, `resource_name` is the name of a specific resource and `type:``resource_type` is the name of a specific resource type. The resource type must be preceded by `type:`.

  Optionally, you can specify modifiers to further configure resource entity dependencies. You can modify each dependency by prefixing the following modifiers to the resource entity:

  `hard([intermediate:][global:][shutdown:]{``resource_name`` | ``type:``resource_type``})`—Specify a `hard` stop dependency for a resource that you want to stop when named resources or resources of a particular resource type stop.

  Use `intermediate` to specify that the dependent resource can remain in an `ONLINE` state if a resource is in either the `ONLINE` or `INTERMEDIATE` state. If not specified, then Oracle Clusterware stops the dependent resource unless resources are in the `ONLINE` state.

  Use `global` to specify that the dependent resource remains in an `ONLINE` state if a resource is in an `ONLINE` state on any node in the cluster. If not specified, then when resources residing on the same server go offline, Oracle Clusterware stops the dependent resource.

  Use `shutdown` to apply this dependency when the Oracle Clusterware stack is shut down. This is a convenient way to affect the order of stopping resources when stopping the stack, without having any affect on planned or unplanned events on the individual resources. This dependency, when used with the `shutdown` modifier, does not go into effect if somebody stops the resource directly, but only when the stack is shut down.

**See Also:**

"[Stop Dependencies](making-applications-highly-available-using-oracle-clusterware.md)" for more details about stop dependencies

##### STOP_TIMEOUT

The maximum time (in seconds) in which a `stop` or `clean` action can run. Oracle Clusterware returns an error message if the action does not complete within the time specified. If you do not specify this attribute or if you specify `0` seconds, then Oracle Clusterware uses the value of the `SCRIPT_TIMEOUT` attribute.

##### Usage Example

    STOP_TIMEOUT=30

**See Also:**

- "SCRIPT_TIMEOUT" for more information about this attribute

- "START_TIMEOUT" for more information about this attribute

##### UPTIME_THRESHOLD

The value for `UPTIME_THRESHOLD` represents the length of time that a resource must be up before Oracle Clusterware considers the resource to be stable. By setting a value for the `UPTIME_THRESHOLD` attribute, you can indicate the stability of a resource.

Enter values for this attribute as a number followed by a letter that represents seconds (s), minutes (m), hours (h), days (d), or weeks (w). For example, a value of `7h` represents an uptime threshold of seven hours.

After the time period you specify for `UPTIME_THRESHOLD` elapses, Oracle Clusterware resets the value for `RESTART_COUNT` to `0` at the next resource state change event, such as stop, start, relocate, or failure. Oracle Clusterware can alert you when the value for `RESTART_COUNT` reaches the value that you set for `RESTART_ATTEMPTS`. The counter is effectively reset the next time the resource fails or restarts. The threshold represents the amount of time that restarts are to be counted and discarded. If the resource fails after the threshold, it will still restart.

**Note:**

Oracle Clusterware writes an alert to the clusterware alert log file when the value for `RESTART_COUNT` reaches the value that you set for `RESTART_ATTEMPTS`.

**See Also:**

- "RESTART_ATTEMPTS" for more information about this attribute

- "RESTART_COUNT" for more information about this attribute

##### USER_WORKLOAD

Use to indicate whether a resource is a workload generating resource for what-if analysis. Possible values are `yes` or `no`.

##### Usage Example

    USER_WORKLOAD=yes

##### USE_STICKINESS

Use to indicate that a resource should run where it last ran, if possible, and to not permit load-balancing that would otherwise apply. If set to `1`, Oracle Clusterware attempts to start the resource where it last ran. Enabling `USE_STICKINESS` also disables load-balancing. The default value is `0`. Possible values are `0` and `1`.

##### Usage Example

    USE_STICKINESS=1

#### Read-Only Resource Attributes

You can view these attributes when you run the `crsctl status resource` command on a particular resource. Oracle Clusterware sets these attributes when you register resources.

- ACTION_FAILURE_EVENT_TEMPLATE

- INSTANCE_COUNT

- INTERNAL_STATE

- LAST_SERVER

- LAST_STATE_CHANGE

- PROFILE_CHANGE_EVENT_TEMPLATE

- RESTART_COUNT

- STATE

- STATE_CHANGE_EVENT_TEMPLATE

- STATE_DETAILS

- TARGET

- TARGET_SERVER

- TYPE

##### ACTION_FAILURE_EVENT_TEMPLATE

This is an internally-managed attribute for an `ora.*` resource. You cannot edit this attribute.

##### INSTANCE_COUNT

The `INSTANCE_COUNT` attribute is an internally managed attribute that contains the number of instances that the resource currently has.

##### INTERNAL_STATE

An internally managed, read-only attribute that describes what, if any, action the policy engine is currently running on the resource.

Possible values and their meanings are as follows:

- `STARTING`: The policy engine is currently starting the resource

- `STOPPING`: The policy engine is currently stopping the resource

- `CLEANING`: The policy engine is currently cleaning the resource

- `STABLE`: The policy engine is not currently running any action on the resource

  Note, however, that the resource can still be locked as part of some other command.

##### LAST_SERVER

For `cluster_resource`-type resources, this is an internally managed, read-only attribute that contains the name of the server on which the last `start` action for the resource succeeded.

For `local_resource`-type resources, this is the name of the server to which the resource instance is pinned.

##### LAST_STATE_CHANGE

An internally managed, read-only attribute that describes when the policy engine registers the current state of the resource. Note that this may either be the timestamp of when state of the resource changed or when the policy engine discovered the state, as occurs when CRSD restarts.

##### PROFILE_CHANGE_EVENT_TEMPLATE

This is an internally-managed attribute for an `ora.*` resource. You cannot edit this attribute.

##### RESOURCE_LIST

List of resources belonging to a resource group. Oracle Clusterware populates and updates this attribute when resources are added to the group.

Use this attribute with resource groups.

##### RESTART_COUNT

An internally-managed attribute used by the Oracle Clusterware daemon to count the number of attempts to restart a resource, starting from zero up to the value specified in the `RESTART_ATTEMPTS` attribute. You cannot edit this attribute.

##### STATE

An internally-managed attribute that reflects the current state of the resource as reported by Oracle Clusterware. The state of a resource can be one of the following:

- `ONLINE`: The resource is online and resource monitoring is enabled (see `CHECK_INTERVAL`).

- `OFFLINE`: The resource is offline and only offline resource monitoring is enabled, if configured (see `OFFLINE_CHECK_INTERVAL`).

- `INTERMEDIATE`: The resource is either partially online or was known to be online before and subsequent attempts to determine its state have failed; resource monitoring is enabled (see `CHECK_INTERVAL`).

- `UNKNOWN`: The resource is unmanageable and its current state is unknown; manual intervention is required to resume its operation. A resource in this state is not monitored.

##### STATE_CHANGE_EVENT_TEMPLATE

This is an internally-managed attribute for an `ora.*` resource. You cannot edit this attribute.

##### STATE_DETAILS

An internally managed, read-only attribute that contains details about the state of a resource.

The four resource states—`ONLINE`, `OFFLINE`, `UNKNOWN`, and `INTERMEDIATE`—may map to different resource-specific values, such as mounted, unmounted, and open. Resource agent developers can use the `STATE_DETAILS` attribute to provide a more detailed description of this mapping, resource to the resource state.

Providing details is optional. If details are not provided, then Oracle Clusterware uses only the four possible resource states. Additionally, if the agent cannot provide these details (as may also happen to the value of the resource state), then Oracle Clusterware sets the value of this attribute to provide minimal details about why the resource is in its current state.

##### TARGET

An internal, read-only attribute that describes the desired state of a resource. Using the `crsctl start ``resource_name` or `crsctl stop ``resource_name` commands, however, can affect the value of this attribute.

##### TARGET_SERVER

This is an internally-managed attribute that contains the name of the server where the resource is starting. This value is relevant when the resource is starting.

##### TYPE

The type of resource indicated when you create a resource. This attribute is required when creating a resource and cannot be changed after the resource is created.

**See Also:**

"[Oracle Clusterware Resource Types](making-applications-highly-available-using-oracle-clusterware.md)" for details of resource types

#### Deprecated Resource Attributes

The following resource attributes are deprecated in Oracle Clusterware 12c:

##### DEGREE

The number of instances of a cluster resource that can run on a single server.

### Examples of Action Scripts for Third-party Applications

This section includes examples of third-party applications using script agents.

Example B-2 shows an action script that fails over the Apache Web server.

Example B-2 Apache Action Script

    #!/bin/sh

    HTTPDCONFLOCATION=/etc/httpd/conf/httpd.conf
    WEBPAGECHECK=http://<MyVIP>:80/icons/apache_pb.gif

    case $1 in
    'start')
        /usr/sbin/apachectl -k start -f $HTTPDCONFLOCATION
       RET=$?
        ;;
    sleep(10)
        ;;
    'stop')
        /usr/sbin/apachectl -k stop
       RET=$?
        ;;
    'clean')
        /usr/sbin/apachectl -k stop
       RET=$?
        ;;
    'check')
        /usr/bin/wget -q --delete-after $WEBPAGECHECK
       RET=$?
        ;;
    *)
       RET=0
        ;;
    esac
    # 0: success; 1 : error
    if [ $RET -eq 0 ]; then
    exit 0
    else
    exit 1
    fi

Example B-3 shows the xclock script, which is a simple action script using `xclock` available as a default binary on all Linux and UNIX platforms.

Example B-3 xclock Action Script

    #!/bin/bash
    # start/stop/check script for xclock example
    # To test this change BIN_DIR to the directory where xclock is based
    # and set the DISPLAY variable to a server within your network.

    BIN_DIR=/usr/X11R6/bin
    LOG_DIR=/tmp
    BIN_NAME=xclock
    DISPLAY=yourhost.domain.com:0.0
    export DISPLAY
    exit_code=0

    if [ ! -d $BIN_DIR ]
    then
            echo "start failed"
            exit 2
    fi

    PID1=`ps -ef | grep $BIN_NAME | grep -v grep | grep -v xclock_app | awk '{ print $2 }'`
    case $1 in
    'start')
            if [ "$PID1" != "" ]
            then
               status_p1="running"
            else
               if [ -x $BIN_DIR/$BIN_NAME ]
               then
                 umask 002
                 ${BIN_DIR}/${BIN_NAME} & 2>${LOG_DIR}/${BIN_NAME}.log
                 status_p1="started"
               else
                 echo `basename $0`": $BIN_NAME: Executable not found"
                 exit_code=1
               fi
            fi

             echo "$BIN_NAME: $status_p1"
             exit $exit_code
            ;;

    'stop')
            if [ "${PID1}" != "" ]
            then
               kill -9 ${PID1} && echo "$BIN_NAME daemon killed"
            else
               echo "$BIN_NAME: no running Process!"
            fi
            exit $exit_code
            ;;
    'check')
            if [ "$PID1" != "" ]
            then
               echo "running"
               exit 0
            else
               echo "not running"
               exit 1
            fi
            ;;*)
            echo "Usage: "`basename $0`" {start|stop|check}"
            ;;
    esac

Example B-4 shows an example of a shell script for an agent to monitor a file. When the agent is started, it creates the file (which is specified through an attribute) and when it is stopped, it deletes the file. The CHECK action consists of only checking whether the file exists. The variables with the `_CRS_` prefix are attribute values that are provided to the script in its environment.

Example B-4 Action Script Example

    #!/bin/sh
    TOUCH=/bin/touch
    RM=/bin/rm
    PATH_NAME=/tmp/$_CRS_NAME

    #
    # These messages go into the CRSD agent log file.
    echo " *******   `date` ********** "
    echo "Action script '$_CRS_ACTION_SCRIPT' for resource[$_CRS_NAME] called for action $1"
    #

    case "$1" in
      'start')
         echo "START entry point has been called.."
         echo "Creating the file: $PATH_NAME"
         $TOUCH $PATH_NAME
         exit 0
         ;;

      'stop')
         echo "STOP entry point has been called.."
         echo "Deleting the file: $PATH_NAME"
         $RM $PATH_NAME
         exit 0
         ;;

      'check')
        echo "CHECK entry point has been called.."
        if [ -e $PATH_NAME ]; then
            echo "Check -- SUCCESS"
            exit 0
        else
            echo "Check -- FAILED"
            exit 1
        fi
        ;;

      'clean')
         echo "CLEAN entry point has been called.."
         echo "Deleting the file: $PATH_NAME"
         $RM -f $PATH_NAME
         exit 0
         ;;

    esac
