Oracle Clusterware uses policy-based management of servers and resources used by Oracle databases or applications.

This chapter includes the following topics:

- Overview of Server Pools and Policy-Based Management

- Default Server Pools

- Overview of Server Categorization

- Overview of Cluster Configuration Policies and the Policy Set

- [Server Weight-Based Node Eviction](oracle-clusterware-administration.md)

- Load-Aware Resource Placement

- Server Configuration and Server State Attributes

- Server Category Attributes

- An Example Policy Set Configuration

### Overview of Server Pools and Policy-Based Management

Resources managed by Oracle Clusterware are contained in logical groups of servers called server pools. This was introduced in Oracle Clusterware 11g release 2 (11.2).

[Resources](glossary.md) are hosted on a shared infrastructure and are contained within [server pools](glossary.md). Examples of resources that Oracle Clusterware manages are database instances, database services, application VIPs, and application components.

In an Oracle Cluster you can use server pools to run particular types of workloads on cluster member nodes, while providing simplified administration options. You can use a [cluster configuration policy set](glossary.md) to provide dynamic management of cluster policies across the cluster.

You can continue to manage resources in an Oracle Clusterware standard Cluster by using the Oracle Clusterware 11g release 2 (11.2) server pool model, or you can manually manage resources by using the traditional fixed, non-server pool method.

This section includes the following topics:

- Server Pools and Server Categorization

- Server Pools and Policy-Based Management

- How Server Pools Work

- Default Server Pools

- Server Pool Attributes

- How Oracle Clusterware Assigns New Servers Using Server Pools

- Managing Server Pools Using Default Attributes

#### Server Pools and Server Categorization

Administrators can deploy and manage servers dynamically using server pools by identifying servers distinguished by particular attributes, a process called [server categorization](glossary.md). In this way, you can create clusters made up of heterogeneous nodes.

**Related Topics**

- Overview of Server Categorization

#### Server Pools and Policy-Based Management

With policy-based management, administrators specify the server pool (excluding the Generic and Free pools) in which the servers run.

For example, a database administrator uses SRVCTL to create a server pool for servers hosting a database or database service. A clusterware administrator uses CRSCTL to create server pools for non-database use, such as creating a server pool for servers hosting an application.

Policy-based management:

- Enables online server reallocation based on a defined policy to satisfy workload capacity requirements

- Guarantees the allocation of required resources for critical work as defined by the policy

- Ensures isolation where necessary, so that you can provide dedicated servers in a cluster for applications and databases

- Enables policies to be configured to change pools in accordance with business needs or application demand, so that pools provide the required capacity at the right time

Server pools provide resource isolation to prevent applications running in one server pool from accessing resources running in another server pool. Oracle Clusterware provides fine-grained role separation between server pools. This capability maintains required management role separation between these groups in organizations that have clustered environments managed by separate groups.

Oracle Clusterware efficiently allocates servers in the cluster. Server pool attributes, defined when the server pool is created, dictate placement and prioritization of servers based on the `IMPORTANCE` server pool attribute.

**Related Topics**

- [Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md)
- Overview of Cluster Configuration Policies and the Policy Set

#### How Server Pools Work

Server pools divide the cluster into logical groups of servers hosting both singleton and uniform applications. The application can be a database service or a non-database application. An application is uniform when the application workload is distributed over all servers in the server pool. An application is singleton when it runs on a single server within the server pool. Oracle Clusterware role-separated management determines access to and use of a server pool.

You manage server pools that contain Oracle RAC databases with the Server Control (SRVCTL) utility. Use the Oracle Clusterware Control (CRSCTL) utility to manage all other server pools. Only cluster administrators have permission to create top-level server pools.

Database administrators use the Server Control (SRVCTL) utility to create and manage server pools that will contain Oracle RAC databases. Cluster administrators use the Oracle Clusterware Control (CRSCTL) utility to create and manage all other server pools, such as server pools for non-database applications. Only cluster administrators have permission to create top-level server pools.

Top-level server pools:

- Logically divide the cluster

- Are always exclusive, meaning that one server can only reside in one particular server pool at a certain point in time

#### Default Server Pools

When Oracle Clusterware is installed, two internal server pools are created automatically: Generic and Free. All servers in a new installation are assigned to the Free server pool, initially. Servers move from Free to newly defined server pools automatically.

##### The Free Server Pool

The Free server pool contains servers that are not assigned to any other server pools. The attributes of the Free server pool are restricted, as follows:

- `SERVER_NAMES`, `MIN_SIZE`, and `MAX_SIZE` cannot be edited by the user

- `IMPORTANCE` and `ACL` can be edited by the user

##### The Generic Server Pool

The Generic server pool stores any server that is not in a top-level server pool and is not policy managed. Servers that host non-policy-managed applications, such as administrator-managed databases, are statically assigned to the Generic server pool.

The Generic server pool's attributes are restricted, as follows:

- No one can modify configuration attributes of the Generic server pool (all attributes are read-only)

- You can only create administrator-managed databases in the Generic Pool, if the server you want to create the database on is one of the following:

  - Online and exists in the Generic server pool

  - Online and exists in the Free server pool, in which case Oracle Clusterware moves the server into the Generic server pool

  - Online and exists in any other server pool and the user is either a cluster administrator or is allowed to use the server pool's servers, in which case, the server is moved into the Generic server pool

  - Offline and the user is a cluster administrator

#### Server Pool Attributes

You can use SRVCTL or CRSCTL to create server pools for databases and other applications, respectively.

If you use SRVCTL to create a server pool, then you can only use a subset of the server pool attributes described in this section. If you use CRSCTL to create server pools, then you can use the entire set of server pool attributes.

Server pool attributes are the attributes that you define to create and manage server pools.

The decision about which utility to use is based upon the type of resource being hosted in the server pool. You must use SRVCTL to create server pools that host Oracle databases. You must use CRSCTL to create server pools that host non-database resources such as middle tiers and applications.

When you use SRVCTL to create a server pool, the server pool attributes available to you are:

- `-category`
- `-importance`
- `-min`
- `-max`
- `-serverpool`
- `-servers`

SRVCTL prepends "ora." to the name of the server pool.

When you use CRSCTL to create a server pool, all attributes listed and described in the following table are available to you.

Table 3-1 Server Pool Attributes

| Attribute         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ACL`             | String in the following format:<br>`owner:user:rwx,pgrp:group:rwx,other::r—`<br>Defines the owner of the server pool and which privileges are granted to various operating system users and groups. The server pool owner defines the operating system user of the owner, and which privileges that user is granted.<br>The value of this optional attribute is populated at the time a server pool is created based on the ACL of the user creating the server pool, unless explicitly overridden. The value can subsequently be changed, if such a change is allowed based on the existing privileges of the server pool.<br>In the string:<br>• `owner`: The operating system user of the server pool owner, followed by the privileges of the owner<br>• `pgrp`: The operating system group that is the primary group of the owner of the server pool, followed by the privileges of members of the primary group<br>• `other`: Followed by privileges of others<br>• `r`: Read only<br>• `w`: Modify attributes of the pool or delete it<br>• `x`: Assign resources to this pool<br>By default, the identity of the client that creates the server pool is the `owner`. Also by default, `root`, and the `user` specified in `owner` have full privileges. You can grant required operating system users and operating system groups their privileges by adding the following lines to the `ACL` attribute:<br>`user:user_name:rwx`<br>`group:group_name:rwx`<br>The operating system user that creates the server pool is the owner of the server pool, and the `ACL` attribute for the server pool reflects the UNIX-like read, write, and execute ACL definitions for the user, primary group, group, and other. |
| `ACTIVE_SERVERS`  | A string of server names in the following format:<br>`server_name1 server_name2 ...`<br>Oracle Clusterware automatically manages this attribute, which contains the space-delimited list of servers that are currently assigned to a server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `EXCLUSIVE_POOLS` | This optional attribute indicates if servers assigned to this server pool are shared with other server pools. A server pool can explicitly state that it is mutually exclusive of any other server pool that has the same value for this attribute. Two or more server pools are mutually exclusive when the sets of servers assigned to them do not have a single server in common. For example, server pools A and B must be mutually exclusive if they both have the value of this attribute set to the same string, such as `pools_A_B`.<br>Top-level server pools are mutually exclusive, by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `IMPORTANCE`      | Relative importance of the server pool, expressed as an integer from 0 to 1000, with 0 denoting the lowest level of importance and 1000, the highest. This optional attribute is used to determine how to reconfigure the server pools when a node joins or leaves the cluster. The default value is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `MIN_SIZE`        | The minimum size of a server pool expressed as any nonnegative integer. If the number of servers contained in a server pool is below the number you specify in this attribute, then Oracle Clusterware automatically moves servers from other pools into this one until that number is met.<br>Note: The value of this optional attribute does not set a hard limit. It governs the priority for server assignment whenever the cluster is reconfigured. The default value is `0`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `MAX_SIZE`        | The maximum number of servers a server pool can contain, expressed as any nonnegative integer. This attribute is optional and is set to `-1` (no limit), by default.<br>Note: A value of `-1` for this attribute spans the entire cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `NAME`            | The name of the server pool, which you must specify when you create the server pool. Server pool names must be unique within the domain of names of user-created entities, such as resources, types, and servers. A server pool name has a 254 character limit and can contain any platform-supported characters except the exclamation point (!), the tilde (~), and spaces. A server pool name cannot begin with a period nor with ora.<br>Note: When you create server pools using SRVCTL, the utility prepends "ora." to the name of the server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PARENT_POOLS`    | Use of this attribute makes it possible to create nested server pools. Server pools, listed as a string of space-delimited server pool names, in this attribute are referred to as parent server pools. A server pool included in a parent server pool is referred to as a child server pool.<br>Note: If you use SRVCTL to create the server pool, then you cannot specify this attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `SERVER_CATEGORY` | The name of a registered server category, used as part of server categorization. Oracle Clusterware standard clusters and Oracle Flex Clusters have a default category of `hub`. When you create a server pool, if you set a value for `SERVER_CATEGORY`, then you cannot set a value for `SERVER_NAMES`. Only one of these parameters may have a non-empty value.<br>Use the `SERVER_CATEGORY` attribute to classify servers assigned to a server pool based on server attributes. You can organize servers and server pools in a cluster to match specific workload to servers and server pools, based on server attributes that you define.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `SERVER_NAMES`    | A list of candidate node names, expressed as a string of space-delimited server names, that may be associated with a server pool. If you do not provide a set of server names for this optional attribute, then Oracle Clusterware is configured so that any server may be assigned to any server pool, to the extent allowed by values of other attributes, such as `PARENT_POOLS`.<br>The server names identified as candidate node names are not validated to confirm that they are currently active cluster members. Use this attribute to define servers as candidates that have not yet been added to the cluster.<br>If you set a value for `SERVER_NAMES`, then you cannot set a value for `SERVER_CATEGORY`; Only one of these attributes may have a non-empty value.<br>Note: If you set the `SERVER_CATEGORY` attribute and you need to specify individual servers, then you can list servers by name using the `EXPRESSION` server category attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

**Related Topics**

- [crsctl add serverpool](oracle-clusterware-control-crsctl-utility-reference.md)
- [crsctl status server](oracle-clusterware-control-crsctl-utility-reference.md)
- Server Category Attributes
- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)

#### How Oracle Clusterware Assigns New Servers Using Server Pools

Oracle Clusterware assigns new servers to server pools in the following order:

1.  Generic server pool

2.  User-created server pool

3.  Free server pool

Oracle Clusterware continues to assign servers to server pools until the following conditions are met:

1.  Until all server pools are filled in order of importance to their minimum (`MIN_SIZE`).

2.  Until all server pools are filled in order of importance to their maximum (`MAX_SIZE`).

3.  By default, any servers not placed in a server pool go into the Free server pool.

    You can modify the `IMPORTANCE` attribute for the Free server pool. If the value of the `IMPORTANCE` attribute of the Free server pool is greater than one or more of the other server pools, then the Free server pool will receive any remaining servers once the value of their `MIN_SIZE` attribute is met.

When a server joins a cluster, several things occur.

Consider the server pools configured in Table 3-2:

Table 3-2 Sample Server Pool Attributes Configuration

| NAME    | IMPORTANCE | MIN_SIZE | MAX_SIZE | PARENT_POOLS | EXCLUSIVE_POOLS |
|:--------|:-----------|:---------|:---------|:-------------|:----------------|
| `sp1`   | `1`        | `1`      | `10`     |              |                 |
| `sp2`   | `3`        | `1`      | `6`      |              |                 |
| `sp3`   | `2`        | `1`      | `2`      |              |                 |
| `sp2_1` | `2`        | `1`      | `5`      | `sp2`        | `S123`          |
| `sp2_2` | `1`        | `1`      | `5`      | `sp2`        | `S123`          |

For example, assume that there are no servers in a cluster; all server pools are empty.

When a server, named `server1`, joins the cluster:

1.  Server-to-pool assignment commences.

2.  Oracle Clusterware only processes top-level server pools (those that have no parent server pools), first. In this example, the top-level server pools are `sp1`, `sp2`, and `sp3`.

3.  Oracle Clusterware lists the server pools in order of `IMPORTANCE`, as follows: `sp2`, `sp3`, `sp1`.

4.  Oracle Clusterware assigns `server1` to `sp2` because `sp2` has the highest `IMPORTANCE` value and its `MIN_SIZE` value has not yet been met.

5.  Oracle Clusterware processes the remaining two server pools, `sp2_1` and `sp2_2`. The sizes of both server pools are below the value of the `MIN_SIZE` attribute (both server pools are empty and have `MIN_SIZE` values of `1`).

6.  Oracle Clusterware lists the two remaining pools in order of `IMPORTANCE`, as follows: `sp2_1`, `sp2_2`.

7.  Oracle Clusterware assigns `server1` to `sp2_1` but cannot assign `server1` to `sp2_2` because `sp2_1` is configured to be exclusive with `sp2_2`.

After processing, the cluster configuration appears, as follows

Table 3-3 Post Processing Server Pool Configuration

| Server Pool Name | Assigned Servers |
|:-----------------|:-----------------|
| `sp1`            |                  |
| `sp2`            | `server1`        |
| `sp3`            |                  |
| `sp2_1`          | `server1`        |
| `sp2_2`          |                  |

##### Servers Moving from Server Pool to Server Pool

If the number of servers in a server pool falls below the value of the `MIN_SIZE` attribute for the server pool (such as when a server fails), based on values you set for the `MIN_SIZE` and `IMPORTANCE` attributes for all server pools, Oracle Clusterware can move servers from other server pools into the server pool whose number of servers has fallen below the value for `MIN_SIZE`. Oracle Clusterware selects servers from other server pools to move into the deficient server pool that meet the following criteria:

- For server pools that have a lower `IMPORTANCE` value than the deficient server pool, Oracle Clusterware can take servers from those server pools even if it means that the number of servers falls below the value for the `MIN_SIZE` attribute.

- For server pools with equal or greater `IMPORTANCE`, Oracle Clusterware only takes servers from those server pools if the number of servers in a server pool is greater than the value of its `MIN_SIZE` attribute.

#### Managing Server Pools Using Default Attributes

By default, each server pool is configured with the following attribute options for managing server pools:

- `MIN_SIZE`: The minimum number of servers the server pool should contain.

  If the number of servers in a server pool is below the value of this attribute, then Oracle Clusterware automatically moves servers from elsewhere into the server pool until the number of servers reaches the attribute value.

- `MAX_SIZE`: The maximum number of servers the server pool should contain.

- `IMPORTANCE`: A number from 0 to 1000 (0 being least important) that ranks a server pool among all other server pools in a cluster.

In addition, you can assign additional attributes to provide more granular management of server pools, as part of a cluster configuration policy. Attributes such as `EXCLUSIVE_POOLS` and `SERVER_CATEGORY` can assist you to create policies for your server pools that enhance performance and build tuning design management into your server pool.

### Overview of Server Categorization

Server categorization enables you to organize servers into particular categories by using attributes such as processor types, memory, and other distinguishing system features.

You can configure server pools to restrict eligible members of the pool to a category of servers, which share a particular set of attributes. Originally, server pools were restricted to a set of basic attributes characterizing servers as belonging to a given pool, with no way to distinguish between types of servers; all servers were considered to be equal in relation to their processors, physical memory, and other characteristics. Server categorization now provides a way to distinguish these servers.

**Note:**

If you create policies with Oracle Database Quality of Service Management (Oracle Database QoS Management), then you categorize servers by setting server pool directive overrides, and CRSCTL commands using the `policy` and `policyset` nouns are disabled. Also if you switch from using Oracle Clusterware policies to using Oracle Database QoS Management policies, then the Oracle Clusterware policies are replaced, because the two policy types cannot coexist. Oracle recommends that you create a backup using `crsctl status policyset -file ``file_name` before you switch policies.

**Related Topics**

- [Oracle Clusterware Control (CRSCTL) Utility Reference](oracle-clusterware-control-crsctl-utility-reference.md)

### Overview of Cluster Configuration Policies and the Policy Set

A cluster configuration policy is a document that contains exactly one definition for each server pool managed by the cluster configuration policy set. A cluster configuration policy set is a document that defines the names of all server pools configured for the cluster and definitions for all policies.

In Oracle Clusterware 12c and later releases, you use the policies defined in the [cluster configuration policy set](glossary.md) for server pool specification and management, and Oracle Clusterware manages the server pools according to the policies in the policy set. With a cluster configuration policy set, for example, you can allocate more servers to OLTP workload during weekly business hours to respond to email demand, and on the weekends and evenings, allocate more servers to batch workloads, and perform transitions of server pool configuration or server allocation, atomically.

At any point in time, only one policy is in effect for the cluster. But you can create several different policies, so that you can configure pools of servers with parameters to reflect differences in requirements for the cluster based on business needs or demand, or based on calendar dates or times of the day.

**Related Topics**

- An Example Policy Set Configuration

### Load-Aware Resource Placement

You can configure a database so that Oracle Clusterware is aware of the CPU requirements and limits for the given database.

Oracle Clusterware uses this information to place the database resource only on servers that have a sufficient number of CPUs, amount of memory, or both.

If you have configured resources with CPU or memory requirements in Oracle Clusterware, then Oracle Clusterware will only attempt to start those resources on the servers that have that meet those requirements. For database resources, specifically, you can configure the CPU or memory values into the `CPU_COUNT` and `MEMORY_TARGET` instance parameters, respectively.

**Note:**

Configuring the instance parameters requires the following:

- For CPU (Instance Caging), the Resource Manager must be enabled

- For memory, Automatic Memory Management must be used for the database

When you add or modify a database instance, you can configure load-aware resource placement, as follows:

    $ srvctl modify database -db db_unique_name -cpucount cpu_count -memorytarget memory_target

In the preceding example, `cpu_count` refers to the number of workload CPUs and `memory_target` refers to the target memory, in MB, used by the resource.

If the Resource Manager is enabled in the database, then Oracle Clusterware sets the CPU_COUNT parameter to the value of `-cpucount`. Also, if Automatic Memory Management is enabled for the database, then Oracle Clusterware sets the MEMORY_TARGET database parameter to the value of `-memorytarget`.

**Related Topics**

- [Oracle Database Reference](../refrn/CPU_COUNT.md)
- [Oracle Database Reference](../refrn/MEMORY_TARGET.md)
- [Oracle Database Administrator’s Guide](../admin/managing-memory.md)

### Server Configuration and Server State Attributes

Oracle Clusterware assigns each server a set of attributes as soon as you add a server to a cluster.

Some of these attributes describe the physical characteristics of the server, while others describe the state conditions of the server. Also, there are other server attributes which you can modify that help further categorize servers. If you remove the server from the cluster, then Oracle Clusterware deletes the server object.

You use server configuration attributes to categorize servers, as part of a server categorization management policy.

The following table lists and describes server configuration attributes.

Table 3-4 Server Configuration Attributes

| Attribute              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ACTIVE_CSS_ROLE`      | Role being performed by the server. A server can have the `hub` role, which is a designated role for a server in an Oracle Flex Cluster or the designated role for any node in an Oracle Clusterware standard Cluster.<br>Note: You cannot configure this attribute.                                                                                                                                                                                                                                                                                                                                                                        |
| `CONFIGURED_CSS_ROLE`  | Configured role for the server. A server can have the `hub` role, which is the designated role for a server in an Oracle Flex Cluster or the designated role for any node in an Oracle Clusterware standard Cluster.<br>Note: You cannot configure this attribute.                                                                                                                                                                                                                                                                                                                                                                          |
| `CPU_CLOCK_RATE`       | CPU clock rate in megahertz (MHz)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `CPU_COUNT`            | Number of processors                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CPU_EQUIVALENCY`      | The relative value (expressed as a positive integer greater than or equal to 1) that Oracle Clusterware uses to describe that the CPU power provided by a server may deviate (positively or negatively) from its physical representation using a baseline of 1000, for example. A value lower than 1000 describes that, despite a certain value for the `CPU_COUNT` and `CPU_CLOCK_RATE` parameters, the equivalent power provided by this server is respectively lower.<br>Use the following commands to view or modify, respectively, this attribute on the local server:<br>`crsctl get cpu equivalency`<br>`crsctl set cpu equivalency` |
| `CPU_HYPERTHREADING`   | Status of hyperthreading for the CPU. A value of `0` signifies that hyperthreading is not in use. A value of `1` signifies that hyperthreading is in use.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `MEMORY_SIZE`          | Memory size in megabytes (MB)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `NAME`                 | The name of the server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `RESOURCE_USE_ENABLED` | A server pool resource management parameter. If the value for this attribute is 1, which is the default, then the server can be used for resource placement. If the value is 0, then Oracle Clusterware disallows starting server pool resources on the server. The server remains in the Free pool.<br>You can review the setting and control this attribute for each cluster member node by using the `crsctl get resource use` and `crsctl set resource use` commands.                                                                                                                                                                   |
| `SERVER_LABEL`         | An arbitrary value that you can use to label the server. You can use this attribute when setting up server categories. For example, you can specify a location (such as building_A or building_B), which makes it possible to put servers into pools where location is a requirement, by creating an appropriate server category and using it for the server pool.<br>Use the following commands to view or modify, respectively, this attribute on the local server:<br>`crsctl get server label`<br>`crsctl set server label`                                                                                                             |

The following table lists and describes read-only server state and configuration attributes:

Table 3-5 Server State Attributes

| Attribute       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ACTIVE_POOLS`  | A space-delimited list of the names of the server pools to which a server belongs. Oracle Clusterware manages this list automatically.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `STATE`         | A server can be in one of the following states:<br>• `ONLINE`: The server is a member of the cluster and is available for resource placement.<br>• `OFFLINE`: The server is not currently a member of the cluster. Subsequently, it is not available for resource placement.<br>• `JOINING`: When a server joins a cluster, Oracle Clusterware processes the server to ensure that it is valid for resource placement. Oracle Clusterware also checks the state of resources configured to run on the server. Once the validity of the server and the state of the resources are determined, the server transitions out of this state.<br>• `LEAVING`: When a planned shutdown for a server begins, the state of the server transitions to `LEAVING`, making it unavailable for resource placement.<br>• `VISIBLE`: Servers that have Oracle Clusterware running, but not the Cluster Ready Services daemon (CRSD), are put into the `VISIBLE` state. This usually indicates an intermittent issue or failure and Oracle Clusterware trying to recover (restart) the daemon. Oracle Clusterware cannot manage resources on servers while the servers are in this state.<br>• `RECONFIGURING`: When servers move between server pools due to server pool reconfiguration, a server is placed into this state if resources that ran on it in the current server pool must be stopped and relocated. This happens because resources running on the server may not be configured to run in the server pool to which the server is moving. As soon as the resources are successfully relocated, the server is put back into the `ONLINE` state.<br>Use the `crsctl status server` command to obtain server information. |
| `STATE_DETAILS` | This is a read-only attribute that Oracle Clusterware manages. The attribute provides additional details about the state of a server. Possible additional details about a server state are:<br>Server state: `ONLINE`:<br>• `AUTOSTARTING RESOURCES`<br>• Indicates that the resource autostart procedure (performed when a server reboots or the Oracle Clusterware stack is restarted) is in progress for the server.<br>• `AUTOSTART QUEUED`<br>• The server is waiting for the resource autostart to commence. Once that happens, the attribute value changes to `AUTOSTARTING RESOURCES`.<br>Server state: `RECONFIGURING`:<br>• `STOPPING RESOURCES`<br>• Resources that are restricted from running in a new server pool are stopping.<br>• `STARTING RESOURCES`<br>• Resources that can run in a new server pool are starting.<br>• `RECONFIG FAILED`<br>• One or more resources did not stop and thus the server cannot transition into the `ONLINE` state. At this point, manual intervention is required. You must stop or unregister resources that did not stop. After that, the server automatically transitions into the `ONLINE` state.<br>Server state: `JOINING`:<br>• `CHECKING RESOURCES`<br>• Whenever a server reboots, the Oracle Clusterware stack restarts, or CRSD on a server restarts, the policy engine must determine the current state of the resources on the server. While that procedure is in progress, this value is returned.                                                                                                                                                                                                                                                 |

#### Memory Pressure Management for Database Servers

Enterprise database servers can use all available memory due to too many open sessions or runaway workloads. Running out of memory can result in failed transactions or, in extreme cases, a restart of the server and the loss of a valuable resource for your applications. Oracle Database QoS Management detects memory pressure on a server in real time and redirects new sessions to other servers to prevent using all available memory on the stressed server.

When Oracle Database QoS Management is enabled and managing an Oracle Clusterware server pool, Cluster Health Monitor sends a metrics stream that provides real-time information about memory resources for the cluster servers to Oracle Database QoS Management. This information includes the following:

- Amount of available memory

- Amount of memory currently in use

If Oracle Database QoS Management determines that a node is under memory stress, then the database services managed by Oracle Clusterware are stopped on that node, preventing new connections from being created. After the memory stress is relieved, the services on that node are restarted automatically, and the listener starts sending new connections to that server. Memory pressure can be relieved in several ways (for example, by closing existing sessions or by user intervention).

Rerouting new sessions to different servers protects the existing workloads on the memory-stressed server and enables the server to remain available. Managing the memory pressure for servers adds a new resource protection capability in managing service levels for applications hosted on Oracle RAC databases.

### Server Category Attributes

You define servers into named categories, and assign attributes that define servers as members of that category.

Some attributes that you can use to define members of a category describe the state conditions for the server, and others describe the physical characteristics of the server. You can also create your own characteristics to define servers as members of a particular category.

**Note:**

If you change the value of any of the server attributes listed in the `EXPRESSION` server category attribute, then you must restart the Oracle Clusterware technology stack on the affected servers before the new values take effect.

The following table lists and describes possible server category attributes.

Table 3-6 Server Category Attributes

| Attribute         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`            | The name of the server category, which you must specify when you create the server category. Server category names must be unique within the domain of names of user-created entities, such as resources, types, and servers. A server pool name has a 254 character limit and can contain any platform-supported characters except the exclamation point (!) and the tilde (~). A server pool name cannot begin with a period nor with ora.                                                                                                                                                                                                                                                                                                   |
| `ACTIVE_CSS_ROLE` | Active role for the server, which is `hub` for a server that is a Hub Node in either an Oracle Flex Cluster or an Oracle Clusterware standard Cluster. This is the default value in either case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `EXPRESSION`      | A set of server attribute names, values, and conditions that can be evaluated for each server to determine whether it belongs to the category. Table 3-4 lists and describes server attributes.<br>Acceptable comparison operators include:<br>• =: equal<br>• eqi: equal, case insensitive<br>• \>: greater than<br>• \<: less than<br>• !=: not equal<br>• co: contains<br>• coi: contains, case insensitive<br>• st: starts with<br>• en: ends with<br>• nc: does not contain<br>• nci: does not contain, case insensitive<br>Acceptable boolean operators include:<br>• AND<br>• OR<br>Note: Spaces must surround the operators used in the `EXPRESSION` string.<br>For example:<br>`EXPRESSION='((NAME = server1) OR (NAME = server2))'"` |

### An Example Policy Set Configuration

In this example, you have a four-node cluster that is used by three different applications, app1, app2, and app3, and that you have created three server pools, pool1, pool2, and pool3. You configure the server pools such that each application is assigned to run in its own server pool, and that app1 wants to have two servers, and app2 and app3 each want one server.

The server pool configurations are as follows:

    $ crsctl status serverpool pool1 -p
    NAME=pool1
    IMPORTANCE=0
    MIN_SIZE=2
    MAX_SIZE=2
    SERVER_NAMES=
    PARENT_POOLS=
    EXCLUSIVE_POOLS=
    ACL=owner:mjk:rwx,pgrp:g900:rwx,other::r--
    SERVER_CATEGORY=

    $ crsctl status serverpool pool2 -p
    NAME=pool2
    IMPORTANCE=0
    MIN_SIZE=1
    MAX_SIZE=1
    SERVER_NAMES=
    PARENT_POOLS=
    EXCLUSIVE_POOLS=
    ACL=owner:mjk:rwx,pgrp:g900:rwx,other::r--
    SERVER_CATEGORY=

    $ crsctl status serverpool pool3 -p
    NAME=pool3
    IMPORTANCE=0
    MIN_SIZE=1
    MAX_SIZE=1
    SERVER_NAMES=
    PARENT_POOLS=
    EXCLUSIVE_POOLS=
    ACL=owner:mjk:rwx,pgrp:g900:rwx,other::r--
    SERVER_CATEGORY=

**Note:**

The `crsctl status serverpool` command shown in the preceding examples only functions if you created the server pools using CRSCTL.

This configuration, however, does not consider the fact that some applications need server time at different times of the day, week, or month. Email applications, for example, typically use more resources during business hours and use less resources at night and on weekends.

Further assume that app1 requires two servers during business hours, but only requires one server at night and does not require any servers on weekends. At the same time, app2 and app3 each require one server during business hours, while at night, app2 requires two servers and app3 requires one. On the weekend, app2 requires one server and app3 requires three. This scenario suggests three configurations that you must configure for the cluster:

1.  Day Time:

    - app1 uses two servers
    - app2 and app3 use one server, each

2.  Night Time:

    - app1 uses one server
    - app2 uses two servers
    - app3 uses one server

3.  Weekend:

    - app1 is not running (0 servers)
    - app2 uses one server
    - app3 uses three servers

Policy Set Creation

Given these assumptions, run the `crsctl create policyset` command to create a policy set with a single policy named `Default`, which reflects the configuration displayed by the `crsctl status serverpool` command. You can use the `Default` policy to create other policies to meet the needs assumed in this example. The `crsctl create policyset` command creates a text file similar to Example 3-1.

Example 3-1 Policy Set Text File

    SERVER_POOL_NAMES=Free pool1 pool2 pool3
    POLICY
      NAME=Default
      SERVERPOOL
        NAME=pool1
        IMPORTANCE=0
        MAX_SIZE=2
        MIN_SIZE=2
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool2
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool3
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=

Policy Modification

To modify the preceding policy set to meet the needs assumed in this example, edit the text file to define policies for the three scenarios discussed previously, by changing the name of the policy from `Default` to `DayTime`. Then, copy the policy and paste it twice to form two subsequent policies, which you name `NightTime` and `Weekend`, as shown in Example 3-2.

Example 3-2 Modified Policy Set Text File

    SERVER_POOL_NAMES=Free pool1 pool2 pool3
    POLICY
      NAME=DayTime
      SERVERPOOL
        NAME=pool1
        IMPORTANCE=0
        MAX_SIZE=2
        MIN_SIZE=2
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool2
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool3
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
    POLICY
      NAME=NightTime
      SERVERPOOL
        NAME=pool1
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool2
        IMPORTANCE=0
        MAX_SIZE=2
        MIN_SIZE=2
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool3
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
    POLICY
      NAME=Weekend
      SERVERPOOL
        NAME=pool1
        IMPORTANCE=0
        MAX_SIZE=0
        MIN_SIZE=0
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool2
        IMPORTANCE=0
        MAX_SIZE=1
        MIN_SIZE=1
        SERVER_CATEGORY=
      SERVERPOOL
        NAME=pool3
        IMPORTANCE=0
        MAX_SIZE=3
        MIN_SIZE=3
        SERVER_CATEGORY=

Notice that, in addition to changing the names of the individual policies, the `MAX_SIZE` and `MIN_SIZE` policy attributes for each of the server pools in each of the policies were also modified according to the needs of the applications.

The following command registers the policy set stored in a file with Oracle Clusterware:

    $ crsctl modify policyset -file file_name

You can achieve the same results as shown in the previous examples by editing the `Default` policy set, as a whole, using the `crsctl modify policyset` command, and by using the `crsctl modify serverpool` command to change individual server pool attributes for a specific policy.

The following command modifies the `Default` policy set to manage the three server pools:

    $ crsctl modify policyset -attr "SERVER_POOL_NAMES=Free pool1 pool2 pool3"

The following commands add the three policies:

    $ crsctl add policy DayTime
    $ crsctl add policy NightTime
    $ crsctl add policy Weekend

The following commands configure the three server pools according to the requirements of the policies:

    $ crsctl modify serverpool pool1 -attr "MIN_SIZE=2,MAX_SIZE=2" -policy DayTime
    $ crsctl modify serverpool pool1 -attr "MIN_SIZE=1,MAX_SIZE=1" -policy NightTime
    $ crsctl modify serverpool pool1 -attr "MIN_SIZE=0,MAX_SIZE=0" -policy Weekend

    $ crsctl modify serverpool pool2 -attr "MIN_SIZE=1,MAX_SIZE=1" -policy DayTime
    $ crsctl modify serverpool pool2 -attr "MIN_SIZE=2,MAX_SIZE=2" -policy NightTime
    $ crsctl modify serverpool pool2 -attr "MIN_SIZE=1,MAX_SIZE=1" -policy Weekend

    $ crsctl modify serverpool pool3 -attr "MIN_SIZE=1,MAX_SIZE=1" -policy DayTime
    $ crsctl modify serverpool pool3 -attr "MIN_SIZE=1,MAX_SIZE=1" -policy NightTime
    $ crsctl modify serverpool pool3 -attr "MIN_SIZE=3,MAX_SIZE=3" -policy Weekend

There are now three distinct policies to manage the server pools to accommodate the requirements of the three applications.

Policy Activation

The policy set is now configured and controlling the three server pools with three different policies. You can activate policies when necessary, prompting Oracle Clusterware to reconfigure a server pool according to each policy's configuration.

The following command activates the `DayTime` policy:

    $ crsctl modify policyset -attr "LAST_ACTIVATED_POLICY=DayTime"

The current status of the resources is as follows:

    $ crsctl status resource -t
    --------------------------------------------------------------------------------
    Name           Target  State        Server                   State details
    --------------------------------------------------------------------------------
    Cluster Resources
    --------------------------------------------------------------------------------
    app1
          1        ONLINE  ONLINE       mjk_has3_2               STABLE
          2        ONLINE  ONLINE       mjk_has3_0               STABLE
    app2
          1        ONLINE  ONLINE       mjk_has3_1               STABLE
    app3
          1        ONLINE  ONLINE       mjk_has3_3               STABLE

The status of the server pools is as follows:

    $ crsctl stat serverpool
    NAME=Free
    ACTIVE_SERVERS=

    NAME=Generic
    ACTIVE_SERVERS=

    NAME=pool1
    ACTIVE_SERVERS=mjk_has3_0 mjk_has3_2

    NAME=pool2
    ACTIVE_SERVERS=mjk_has3_1

    NAME=pool3
    ACTIVE_SERVERS=mjk_has3_3

The servers are allocated according to the `DayTime` policy and the applications run on their respective servers.

The following command activates the `Weekend` policy (remember, because the server pools have different sizes, as servers move between server pools, some applications will be stopped and others will be started):

    $ crsctl modify policyset -attr "LAST_ACTIVATED_POLICY=Weekend"
    CRS-2673: Attempting to stop 'app1' on 'mjk_has3_2'
    CRS-2673: Attempting to stop 'app1' on 'mjk_has3_0'
    CRS-2677: Stop of 'app1' on 'mjk_has3_0' succeeded
    CRS-2672: Attempting to start 'app3' on 'mjk_has3_0'
    CRS-2677: Stop of 'app1' on 'mjk_has3_2' succeeded
    CRS-2672: Attempting to start 'app3' on 'mjk_has3_2'
    CRS-2676: Start of 'app3' on 'mjk_has3_2' succeeded
    CRS-2676: Start of 'app3' on 'mjk_has3_0' succeeded

The current status of the resources is as follows:

    $ crsctl status resource -t
    --------------------------------------------------------------------------------
    Name           Target  State        Server                   State details
    --------------------------------------------------------------------------------
    Cluster Resources
    --------------------------------------------------------------------------------
    app1
          1        ONLINE  OFFLINE                               STABLE
          2        ONLINE  OFFLINE                               STABLE
    app2
          1        ONLINE  ONLINE       mjk_has3_1               STABLE
    app3
          1        ONLINE  ONLINE       mjk_has3_0               STABLE
          2        ONLINE  ONLINE       mjk_has3_2               STABLE
          3        ONLINE  ONLINE       mjk_has3_3               STABLE
    --------------------------------------------------------------------------------

The status of the server pools is as follows:

    $ crsctl status serverpool
    NAME=Free
    ACTIVE_SERVERS=

    NAME=Generic
    ACTIVE_SERVERS=

    NAME=pool1
    ACTIVE_SERVERS=

    NAME=pool2
    ACTIVE_SERVERS=mjk_has3_1

    NAME=pool3
    ACTIVE_SERVERS=mjk_has3_0 mjk_has3_2 mjk_has3_3

Using the `crsctl modify policyset` command, Oracle Clusterware changed server pool configuration, moved servers according to the requirements of the policy, and stopped and started the applications.

**Related Topics**

- [Oracle Clusterware Control (CRSCTL) Utility Reference](oracle-clusterware-control-crsctl-utility-reference.md)
