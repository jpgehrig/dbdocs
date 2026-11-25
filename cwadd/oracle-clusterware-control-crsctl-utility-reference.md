This appendix contains reference information for the Oracle Clusterware Control (CRSCTL) utility.

**Note:**

Do not use CRSCTL commands on Oracle entities (such as resources, resource types, and server pools) that have names beginning with ora unless you are directed to do so by My Oracle Support. The Server Control utility (SRVCTL) is the correct utility to use on Oracle entities.

This appendix includes the following topics:

- CRSCTL Overview

- Dual Environment CRSCTL Commands

- Oracle RAC Environment CRSCTL Commands

- Oracle Restart Environment CRSCTL Commands

- Troubleshooting and Diagnostic Output

### CRSCTL Overview

CRSCTL is an interface between you and Oracle Clusterware, parsing and calling Oracle Clusterware APIs for Oracle Clusterware objects.

CRSCTL provides cluster-aware commands with which you can perform check, start, and stop operations on the cluster. You can run these commands from any node in the cluster on another node in the cluster, or on all nodes in the cluster, depending on the operation.

You can use CRSCTL commands to perform several operations on Oracle Clusterware, such as:

- Starting and stopping Oracle Clusterware resources

- Enabling and disabling Oracle Clusterware daemons

- Checking the health of the cluster

- Managing resources that represent third-party applications

- Integrating Intelligent Platform Management Interface (IPMI) with Oracle Clusterware to provide failure isolation support and to ensure cluster integrity

- Debugging Oracle Clusterware components

This section includes the following topics:

- Clusterized (Cluster Aware) Commands

- CRSCTL Operational Notes

- Deprecated Subprograms or Commands

#### Clusterized (Cluster Aware) Commands

You can run clusterized commands on one node to perform operations on another node in the cluster. These are referred to as remote operations. This simplifies administration because, for example, you no longer have to log in to each node to check the status of the Oracle Clusterware on all of your nodes.

Clusterized commands are completely operating system independent; they rely on the OHASD (Oracle High Availability Services daemon). If this daemon is running, then you can perform remote operations, such as the starting, stopping, and checking the status of remote nodes.

Clusterized commands include the following:

- `crsctl check cluster`

- `crsctl start cluster`

- `crsctl stop cluster`

#### CRSCTL Operational Notes

Information about using the CRSCTL command-line interface.

##### Usage Information

- The CRSCTL utility is located in the `Grid_home``/bin` directory. To run CRSCTL commands, type in `crsctl` at the operating system prompt followed by the command and arguments, as shown in the following example:

      crsctl stop crs

- There are three categories of CRSCTL commands:

  - Those that you use in either the Oracle Real Application Clusters (Oracle RAC) environment or in the Oracle Restart environment

  - Those that you use in the Oracle RAC environment, only

  - Those that you use in the Oracle Restart environment, only

- Many CRSCTL commands use the `-f` parameter to force the command to run and ignore any checks.

  For example, if you specify the force parameter for the `crsctl stop resource` command on a resource that is running and has dependent resources that are also running, then the force parameter omits the error message and instead stops or relocates all the dependent resources before stopping the resource you reference in the command.

- Do not use versions of CRSCTL earlier than 12c release 1 (12.1) to manage Oracle Clusterware 12c.

##### Filters

You can use filters to narrow down Oracle Clusterware entities upon which a CRSCTL command operates, as follows:

- Simple filters are attribute-value pairs with an operator.

- Operators must be surrounded by spaces, as shown in the examples.

- You can combine simple filters into expressions called expression filters using Boolean operators.

Supported filter operators are:

- `=`
- `>`
- `<`
- `!=`
- `co`: Contains
- `st`: Starts with
- `en`: Ends with
-

Supported Boolean operators are `AND` and `OR`.

Examples of filters are:

- `TYPE = type1`

- `((TYPE = type1) AND (CHECK_INTERVAL > 50))`

- `(TYPE = type1) AND ((CHECK_INTERVAL > 30) OR (AUTO_START co never))`

- `NAME en network.res`

- `TYPE st ora.db`

##### Using CRSCTL Help

To print the help information for CRSCTL, use the following command:

    crsctl -help

If you want help for a specific command, such as `start`, then enter the command and append `-help` to the end, as shown in the following example:

    crsctl start -help

You can also use the abbreviations `-h` or `-?` (this parameter functions in Linux, UNIX, and Windows environments) instead of `-help`.

#### Deprecated Subprograms or Commands

Table E-1 lists deprecated commands and their replacements that you can use to perform the same or similar functionality.

Table E-1 Deprecated CRSCTL Commands and Replacements

| Deprecated Command                                                                            | Replacement Commands                                                                                                                               |
|:----------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `crs_stat`                                                                                    | `crsctl check cluster`<br>`crsctl status resource`                                                                                                 |
| `crs_register`                                                                                | `crsctl add resource`<br>`crsctl add type`<br>`crsctl modify resource`<br>`crsctl modify type`                                                     |
| `crs_unregister`                                                                              | `crsctl stop resource`<br>`crsctl delete resource`                                                                                                 |
| `crs_start`                                                                                   | `crsctl start resource`<br>`crsctl start crs`<br>`crsctl start cluster`                                                                            |
| `crs_stop`                                                                                    | `crsctl stop resource`<br>`crsctl stop crs`<br>`crsctl stop cluster`                                                                               |
| `crs_getperm`                                                                                 | `crsctl getperm resource`<br>`crsctl getperm type`                                                                                                 |
| `crs_profile`                                                                                 | `crsctl add resource`<br>`crsctl add type`<br>`crsctl status resource`<br>`crsctl status type`<br>`crsctl modify resource`<br>`crsctl modify type` |
| `crs_relocate`                                                                                | `crsctl relocate resource`                                                                                                                         |
| `crs_setperm`                                                                                 | `crsctl setperm resource`<br>`crsctl setperm type`                                                                                                 |
| `crsctl add crs administrator`                                                                | Use the access control list (ACL) to control who can add server pools.                                                                             |
| `crsctl check crsd`                                                                           | `crsctl check crs`                                                                                                                                 |
| `crsctl check cssd`                                                                           | `crsctl check css`                                                                                                                                 |
| `crsctl check evmd`                                                                           | `crsctl check evm`                                                                                                                                 |
| `crsctl debug res log`<br>` resource_name:level`                                              | `crsctl set log`                                                                                                                                   |
| `crsctl set css votedisk`                                                                     | `crsctl add css votedisk`<br>`crsctl delete css votedisk`<br>`crsctl query css votedisk`<br>`crsctl replace votedisk`                              |
| `crsctl start resources`                                                                      | `crsctl start resource -all`                                                                                                                       |
| `crsctl stop resources`                                                                       | `crsctl stop resource -all`                                                                                                                        |
| `crsctl set css logfilesize`                                                                  | `crsctl get tracefileopts css`<br>`crsctl set tracefileopts css`                                                                                   |
| `crsctl get css logfilesize`                                                                  | `crsctl set tracefileopts css`                                                                                                                     |
| `crsctl set trace module_name "component:debugging_level [,component:debugging_level][,...]"` |                                                                                                                                                    |
| `crsctl get trace`                                                                            |                                                                                                                                                    |

### Dual Environment CRSCTL Commands

Use these commands in either the Oracle RAC or the Oracle Restart environments.

The commands listed in this section manage the Oracle Clusterware resources in both Oracle RAC and Oracle Restart environments.

#### crsctl check css

Checks the status of Cluster Synchronization Services.

This command is most often used when Oracle Automatic Storage Management (Oracle ASM) is installed on the local server.

##### Syntax

    crsctl check css

##### Example

This command returns output similar to the following:

    CRS-4529: Cluster Synchronization Services is online

#### crsctl check evm

Checks the status of the Event Manager.

##### Syntax

    crsctl check evm

##### Example

This command returns output similar to the following:

    CRS-4533: Event Manager is online

#### crsctl get hostname

Retrieves the host name of the local server.

##### Syntax

    crsctl get hostname

##### Example

Oracle Clusterware returns the host name of the local server:

    $ crsctl get hostname

    node2

#### crsctl add resource

Registers a resource to be managed by Oracle Clusterware.

A resource can be an application process, a database, a service, a listener, and so on.

##### Syntax

    crsctl add resource resource_name -type resource_type [-group group_name [-file file_path |
       -attr "attribute_name=attribute_value[,...]"]
      [-i] [-f]

##### Parameters

Table E-2 crsctl add resource Command Parameters

| Parameter                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                                        | Specify a short, descriptive name for the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-type ``resource_type`                                | Specify the type of resource that you are adding preceded by the `-type` flag.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-group ``group_name`                                  | Specify a resource group to which you want to add the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-file ``file_path`                                    | Path name (either absolute or relative) for a text file containing line-delimited attribute name-value pairs that define the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-attr "``attribute_name``=``attribute_value``[,...]"` | You can specify attributes for a resource you are adding in two different ways:<br>• Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs enclosed in double quotations marks (`""`). For example:<br>`-attr "CHECK_INTERVAL=30,START_TIMEOUT=25"`<br>• Some attributes can have multiple values. In those cases, separate the values with a space and enclose the list of values in single quotation marks. For example:<br>`-attr "SERVER_POOL_NAMES=`<br>`'ora.pool1 ora.pool2',START_TIMEOUT=25"`<br>• Additionally, you can specify attribute values for resource instances with a particular cardinality value, and with a particular degree value. This method can be useful for applications that are tied to a particular server. Following the `-attr` flag, the syntax is as follows:<br>`attribute_name{@SERVERNAME(server_name)`<br>`[@DEGREEID(did)] | @CARDINALITYID(cid)`<br>`[@DEGREEID(did)]}=attribute_value`<br>• If you specify the `@SERVERNAME(``server_name``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances residing on the server you specify.<br>• Alternatively, if you specify the `@CARDINALITYID(``cid``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances with a specific cardinality ID (`cid`).<br>• Optionally, you can combine the `@DEGREEID(``did``)` syntax with either the `SERVERNAME` or `CARDINALITYID` syntax, or both, to limit the attribute value to resources with the specific `DEGREE`.<br>• Examples:<br>`CHECK_INTERVAL@SERVERNAME(node1)=45`<br>`STOP_TIMEOUT@CARDINALITYID(2)=65`<br>`STOP_TIMEOUT@SERVERNAME(node1)@DEGREEID(2)=65`<br>`STOP_TIMEOUT@CARDINALITYID(3)@DEGREEID(2)=65` |
| `-i`                                                   | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-f`                                                   | Use the force parameter:<br>• To add a resource that has dependencies on other resources that do not yet exist. The force parameter overrides checks that would prevent a command from being completed.<br>• To add a resource if the resource has hard dependencies on other resources and the owner of the resources does not have execute permissions on one or more of the dependencies. If you do not specify the force parameter in this case, an error displays.<br>• To add resources of `application` type because you may need to move servers into the Generic server pool. If the servers currently host resources that must be stopped, then the force parameter is required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

##### Usage Notes

- Both the `resource_name` and `-type` `resource_type` parameters are required. You can create an associated resource type using the `crsctl add type` command.

- Any user can create a resource but only clusterware administrators can create resources of type `local_resource` or resources of type `cluster_resource` that have `SERVER_POOLS=*`.

  Once a resource is defined, its ACL controls who can perform particular operations with it. The Oracle Clusterware administrator list is no longer relevant.

  On Windows, a member of the Administrators group has full control over everything.

  **See Also:**

  "`crsctl setperm resource`" for more information about setting ACLs

- If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`).

- Following is an example of an attribute file:

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

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources.

##### Examples

Example E-1 Example 1

To register a VIP as a resource with Oracle Clusterware:

    $ crsctl add resource app.appvip -type app.appvip.type -attr "RESTART_ATTEMPTS=2,
    START_TIMEOUT=100,STOP_TIMEOUT=100,CHECK_INTERVAL=10,
    USR_ORA_VIP=172.16.0.0,
    START_DEPENDENCIES=hard(ora.net1.network)pullup(ora.net1.network),
    STOP_DEPENDENCIES=hard(ora.net1.network)"

Example E-2 Example 2

To register a resource based on the `test_type1` resource type:

    $ crsctl add resource r1 -type test_type1 -attr "PATH_NAME=/tmp/r1.txt"
    $ crsctl add resource r1 -type test_type1 -attr "PATH_NAME=/tmp/r2.txt"

Example E-3 Example 3

To register a Samba server resource of the `generic_application` resource type, using the `EXECUTABLE_NAMES` attribute:

    # crsctl add resource my_samba -type generic_application -attr
    "EXECUTABLE_NAMES=smbd,START_PROGRAM='/etc/rc.d/init.d/smb start',
    STOP_PROGRAM='/etc/rc.d/init.d/smb stop'"

Example E-4 Example 4

To register a DNS server of the `generic_application` resource type, using the `EXECUTABLE_NAMES` attribute:

    # crsctl add resource my_dns -type generic_application -attr
    "EXECUTABLE_NAMES=named,START_PROGRAM='/etc/rc.d/init.d/named start',
    STOP_PROGRAM='/etc/rc.d/init.d/named stop'"

Example E-5 Example 5

To register an Apache web server of the `generic_application` resource type using the PID_FILES attribute:

    # crsctl add resource my_apache -type generic_application -attr
    "START_PROGRAM='/usr/sbin/httpd -k start',STOP_PROGRAM='/usr/sbin/httpd -k stop',
    PID_FILES=/etc/httpd/run/httpd.pid"

Example E-6 Example 6

To register an application of `generic_application` resource type using environment variables:

    # crsctl add resource my_app -type generic_application -attr
    "START_PROGRAM='/opt/my_app start', EXECUTABLE_NAMES=my_app,
    ENVIRONMENT_VARS='USE_NETAPP=no,USE_BACKUP=yes,CLEAN_ON_KILL=yes'"

**Related Topics**

- [Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md)

#### crsctl delete resource

Removes resources from the Oracle Clusterware configuration.

##### Syntax

    crsctl delete resource {"resource_name [...]" | -w "filter"} [-i] [-f]

##### Parameters

Table E-3 crsctl delete resource Command Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`   | Specify one or more resource names that you want to delete. Multiple resources must be space-delimited and enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-w "``filter``"` | Specify a resource filter that Oracle Clusterware uses to limit the number of resources evaluated for deletion. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>Note: All operators must be surrounded by spaces.<br>See Also: Filters for more information about operators |
| `-i`              | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-f`              | Use this parameter to delete a resource that is online.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

##### Usage Notes

- Either the `resource_name` or `-w "``filter``"` parameter is required

- You must have read and write permissions to delete the specified resources

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources

##### Example

To delete a resource from Oracle Clusterware:

    # crsctl delete resource myResource

#### crsctl eval add resource

Predicts the effects of adding a resource without making changes to the system.

This command may be useful to application administrators.

##### Syntax

    crsctl eval add resource resource_name -type resource_type [-file file_path
        | -attr "attribute_name=attribute_value[,...]"]] [-group group_name] [-f]

##### Parameters

Table E-4 crsctl eval add resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                                  | Specify a short, descriptive name for the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-type ``resource_type`                          | Specify the type of resource that you are adding following the `-type` flag.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-file ``file_path`                              | Path name (either absolute or relative) for a text file containing line-delimited attribute name-value pairs that define the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-attr "``attribute_name``=``attribute_value``"` | You can specify attributes for a resource you are adding in two different ways:<br>• Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs enclosed in double quotations marks (`""`). For example:<br>`-attr "CHECK_INTERVAL=30,START_TIMEOUT=25"`<br>• Some attributes can have multiple values. In those cases, separate the values with a space and enclose the list of values in single quotation marks. For example:<br>`-attr "SERVER_POOL_NAMES=`<br>`'ora.pool1 ora.pool2',START_TIMEOUT=25"`<br>• Optionally, you can specify attribute values for resource instances with a particular cardinality value, and with a particular degree value. This method can be useful for applications that are tied to a particular server. Following the `-attr` flag, the syntax is as follows:<br>`attribute_name{@SERVERNAME(server_name)`<br>`[@DEGREEID(did)] | @CARDINALITYID(cid)`<br>`[@DEGREEID(did)]}=attribute_value`<br>• If you specify the `@SERVERNAME(``server_name``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances residing on the server you specify.<br>• Alternatively, if you specify the `@CARDINALITYID(``cid``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances with a specific cardinality ID (`cid`).<br>• Optionally, you can combine the `@DEGREEID(``did``)` syntax with either the `SERVERNAME` or `CARDINALITYID` syntax, or both, to limit the attribute value to resources with the specific `DEGREE`.<br>• Examples:<br>`CHECK_INTERVAL@SERVERNAME(node1)=45`<br>`STOP_TIMEOUT@CARDINALITYID(2)=65`<br>`STOP_TIMEOUT@SERVERNAME(node1)@DEGREEID(2)=65`<br>`STOP_TIMEOUT@CARDINALITYID(3)@DEGREEID(2)=65` |
| `-group ``group_name`                            | Specify a resource group to which you want to add the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-f`                                             | Use the force parameter:<br>• To add a resource that has dependencies on other resources that do not yet exist. The force parameter overrides checks that would prevent a command from being completed.<br>• To add a resource if the resource has hard dependencies on other resources and the owner of the resources does not execute permissions on one or more of the dependencies. If you do not specify the force parameter in this case, an error displays.<br>• To add resources of `application` type because you may need to move servers into the Generic server pool. If the servers currently host resources that must be stopped, then the force parameter is required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

#### crsctl eval fail resource

Predicts the consequences of a resource failing.

##### Syntax

    crsctl eval fail resource {resource_name | -w "filter"} [-n server]
       [-env "attr=val[,...]"]

##### Parameters

Table E-5 crsctl eval fail resource Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                 | Specify the name of a resource for which you want to simulate a failure. You must specify either the name of a resource or resource filters using the `-w` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-w "``filter``"`               | Alternatively, you can specify a resource filter that Oracle Clusterware uses to limit the number of resources evaluated. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>Note: All operators must be surrounded by spaces.<br>See Also: Filters for more information about operators |
| `-n ``server`                   | Specify the name of the server on which the resource that you want to simulate a failure resides.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-env "``attr``=``val``[,...]"` | You can optionally override one or more resource profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).<br>For example, you could use `-env` `"RESTART_ATTEMPTS=0"` to predict what would happen if the resource has run out of local restart attempts and cannot be restarted locally.                                                                                                                                                                                                                                                                                                                                                                                                                                     |

##### Example

This command returns output similar to the following:

    $ crsctl eval fail res cs1

    Stage Group 1:
    -----------------------------------------------------------------------------
    Stage Number    Required       Action
    -----------------------------------------------------------------------------

         1              Y   Resource 'cs1' (1/1) will be in state
                            [ONLINE|INTERMEDIATE] on server
                            [mjkeenan_node_0]
                        Y   Resource 'cs1' (2/1) will be in state
                            [ONLINE|INTERMEDIATE] on server
                            [mjkeenan_node_1]

    -----------------------------------------------------------------------------

#### crsctl eval relocate resource

Simulates relocating a resource without making changes to the system.

##### Syntax

    crsctl eval relocate resource {resource_name | -all} {-s source_server | -w "filter"}
      [-n destination_server] [-f]

##### Parameters

Table E-6 crsctl eval relocate resource Command Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`           | Specify the name of a resource you want to relocate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-all`                    | Alternatively, you can use this parameter to specify all resources for relocation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-s ``source_server`      | Specify a particular server from which you want to relocate the resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-w "``filter``"`         | Alternative to using `-s`, you can specify a resource filter that CRSCTL uses to limit the number of resources relocated. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: Filters for more information |
| `-n ``destination_server` | Specify the name of the server to which you want to relocate resources. If you do not specify a destination server, then CRSCTL relocates the resources to the best server according to the attribute profile of each resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `–f`                      | Specify the `-f` parameter to force the relocation of the resource when it has other resources running that depend on it. CRSCTL stops or relocates dependent resources when you use this parameter.<br>Note: When you are relocating resources that have cardinality greater than 1, you must use either `-k` or `-s` to narrow down which resource instances are to be relocated.                                                                                                                                                                                                                                                                                                                                                                                                                                           |

#### crsctl eval modify resource

Predicts the effects of modifying a resource without making changes to the system.

##### Syntax

    crsctl eval modify resource resource_name -attr "attribute_name=attribute_value[,...]"
        [-group group_name] [-f]

##### Parameters

Table E-7 crsctl eval modify resource Command Parameters

| Parameter                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                                        | Specify the name of the resource you want to evaluate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-attr "``attribute_name``=``attribute_value``[,...]"` | You can specify attributes for a resource you want to evaluate in two different ways:<br>• Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs to modify enclosed in double quotations marks (`""`). For example:<br>`-attr "CHECK_INTERVAL=30, START_TIMEOUT=25"`<br>• Some attributes can have multiple values. In those cases, separate the values with a space and enclose the list of values in single quotation marks. For example:<br>`-attr "SERVER_POOL_NAMES=`<br>`'ora.pool1 ora.pool2',START_TIMEOUT=25"`<br>• Alternatively, you can specify attribute values for resources on a particular server, with a particular cardinality value, and with a particular degree value. This method can be useful for applications that are somehow tied to a particular server. Following the `-attr` flag, the syntax is as follows:<br>`attribute_name{@SERVERNAME(server_name)`<br>`[@DEGREEID(did)] | @CARDINALITYID(cid)`<br>`[@DEGREEID(did)]}=attribute_value`<br>• If you specify the `@SERVERNAME(``server_name``)` syntax, then the attribute value you specify for the attribute you specify is limited to resources residing on the server you specify.<br>• Alternatively, if you specify the `@CARDINALITYID(``cid``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances with a specific cardinality ID (`cid`).<br>• Optionally, you can combine the `@DEGREEID(``did``)` syntax with either the `SERVERNAME` or `CARDINALITYID` syntax, or both, to limit the attribute value to resources with the specific `DEGREE`.<br>• Examples:<br>`CHECK_INTERVAL@SERVERNAME(node1)=45`<br>`STOP_TIMEOUT@CARDINALITYID(2)=65`<br>`STOP_TIMEOUT@SERVERNAME(node1)@DEGREEID(2)=65`<br>`STOP_TIMEOUT@CARDINALITYID(3)@DEGREEID(2)=65` |
| `-group ``group_name`                                  | Specify a resource group to which the resource belongs that you want to evaluate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `–f`                                                   | Specify this parameter to evaluate what happens if you run the command with the force parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### crsctl eval start resource

Predicts the effects of starting a resource without making changes to the system.

##### Syntax

    crsctl eval start resource {resource_name [...] | -w "filter"}
       [-n server_name] [-f]

##### Parameters

Table E-8 crsctl eval start resource Command Parameters

| Parameter               | Description                                                                                                                                                                                                                           |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]` | Specify one or more space-delimited resource names to start.                                                                                                                                                                          |
| `-w "``filter``"`       | Specify a resource filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resources. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: "Filters" for more information |
| `-n ``server_name`      | Specify the name of the server on which the resources you want to start reside. If you do not specify a server, then Oracle Clusterware starts the resources on the best server according to the attribute profile of each resource.  |
| `–f`                    | Use the `-f` parameter to relocate a resource running on another server on which the resource you want to start has a hard start dependency. If you do not specify the force parameter in this case, then the start command fails.    |

#### crsctl eval stop resource

Predicts the effect of stopping a resource without making changes to the system.

##### Syntax

    crsctl eval stop resource {resource_name [...] | -w "filter"} [-f]

##### Parameters

Table E-9 crsctl eval stop resource Command Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]` | Specify one or more space-delimited resource names to stop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-w "``filter``"`       | Specify a resource filter that Oracle Clusterware uses to limit the number of resources stopped. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to stop only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to stop resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to stop resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: Filters for more information |
| `–f`                    | Specify the `-f` parameter to force the stopping of the resource when it has other resources running that depend on it. Dependent resources are relocated or stopped when you use this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

#### crsctl getperm resource

Displays the user and group permissions for the specified resource.

##### Syntax

    crsctl getperm resource resource_name [{-u user_name | -g group_name}]

##### Parameters

Table E-10 crsctl getperm resource Command Parameters

| Parameter         | Description                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------|
| `resource_name`   | Specify the name of the resource for which you want to obtain permissions.               |
| `-u ``user_name`  | If you specify `-u`, then Oracle Clusterware obtains permissions for a particular user.  |
| `-g ``group_name` | If you specify `-g`, then Oracle Clusterware obtains permissions for a particular group. |

##### Usage Notes

- The `resource_name` parameter is required

- You must have read permission on the specified resources to obtain their permissions

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources

**See Also:**

[Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md) for more information about resources and resource attributes

##### Examples

The `crsctl getperm resource` command returns output similar to the following, depending on the command option you choose:

    $ crsctl getperm resource app.appvip

    Name: app.appvip
    owner:root:rwx,pgrp:oinstall:rwx,other::r--

    $ crsctl getperm resource app.appvip -u oracle

    Name: app.appvip
    rwx

    $ crsctl getperm resource app.appvip -g dba

    Name: app.appvip
    r--

#### crsctl modify resource

Modifies the attributes of a particular resource in Oracle Clusterware.

##### Syntax

    crsctl modify resource resource_name -attr "attribute_name=attribute_value"
    [-i] [-f] [-delete] [-group group_name]  [-env "env1=val1,env2=val2,..."]

##### Parameters

Table E-11 crsctl modify resource Command Parameters

| Parameter                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                                   | The name of the resource you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-attr "``attribute_name``= ``attribute_value``"` | You can specify attributes for a resource you want to modify in two different ways:<br>• Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs to modify enclosed in double quotations marks (`""`). For example:<br>`-attr "CHECK_INTERVAL=30, START_TIMEOUT=25"`<br>• Some attributes can have multiple values. In those cases, separate the values with a space and enclose the list of values in single quotation marks. For example:<br>`-attr "SERVER_POOL_NAMES=`<br>`'ora.pool1 ora.pool2',START_TIMEOUT=25"`<br>• Alternatively, you can specify attribute values for resources on a particular server, with a particular cardinality value, and with a particular degree value. This method can be useful for applications that are somehow tied to a particular server. Following the `-attr` flag, the syntax is as follows:<br>`attribute_name{@SERVERNAME(server_name)`<br>`[@DEGREEID(did)] | @CARDINALITYID(cid)`<br>`[@DEGREEID(did)]}=attribute_value`<br>• If you specify the `@SERVERNAME(``server_name``)` syntax, then the attribute value you specify for the attribute you specify is limited to resources residing on the server you specify.<br>• Alternatively, if you specify the `@CARDINALITYID(``cid``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances with a specific cardinality ID (`cid`).<br>• Optionally, you can combine the `@DEGREEID(``did``)` syntax with either the `SERVERNAME` or `CARDINALITYID` syntax, or both, to limit the attribute value to resources with the specific `DEGREE`.<br>• Examples:<br>`CHECK_INTERVAL@SERVERNAME(node1)=45`<br>`STOP_TIMEOUT@CARDINALITYID(2)=65`<br>`STOP_TIMEOUT@SERVERNAME(node1)@DEGREEID(2)=65`<br>`STOP_TIMEOUT@CARDINALITYID(3)@DEGREEID(2)=65` |
| `-i`                                              | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-f`                                              | Use the `-f` parameter when:<br>• The resource has a hard dependency on a non-existing resource<br>• The owner of the resource does not have execute permissions on one or more hard dependencies<br>• The modification results in servers being moved into the Generic pool and resources being stopped or relocated to accomplish the server move                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-delete`                                         | If you specify the `-delete` parameter, then Oracle Clusterware deletes the named attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-group ``group_name`                             | Specify a resource group to which the resource belongs. The resource group must exist, and the resource cannot be a member of any other explicit resource group. If you do not specify a resource group, then CRSCTL adds the resource to a resource group with the same name as the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-env "``env1``=``val1``,``env2``=``val2``,..."`  | You can optionally override one or more resource profile attribute values for this command. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks ("").                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

##### Usage Notes

- The `resource_name` parameter is required

- If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

      "START_DEPENDENCIES='hard(res1,res2,res3)'"

- You must have read and write permissions on the specified resources to modify them

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources

##### Example

To modify the attributes of the `appsvip` resource:

    $ crsctl modify resource appsvip -attr USR_ORA_VIP=10.1.220.17 -i

**Related Topics**

- [Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md)

#### crsctl relocate resource

Relocates resources to another server in the cluster.

##### Syntax

    crsctl relocate resource {resource_name [-k cid] | -all | -w "filter"} -s source_server |
      [-n destination_server] [-env "env1=val1,env2=val2,..."] [-i] [-f]

##### Parameters

Table E-12 crsctl relocate resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:-------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`                                  | Specify the name of a resource you want to relocate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-k ``cid`                                       | Optionally, you can specify the resource cardinality ID. If you specify this parameter, then CRSCTL relocates the resource instance that has the cardinality you specify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-all`                                           | Alternatively, you can use this parameter to specify all resources for relocation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-w "``filter``"`                                | Alternative to using `-k` or `-all`, you can specify a resource filter that CRSCTL uses to limit the number of resources relocated. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: "Filters" for more information |
| `-s ``source_server`                             | Specify a particular server from which you want to relocate the resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-n ``destination_server`                        | Specify the name of the server to which you want relocate resources. If you do not specify a destination server, then CRSCTL relocates the resources to the best server according to the attribute profile of each resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values for this command. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `–i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `–f`                                             | Specify the `-f` parameter to force the relocation of the resource when it has other resources running that depend on it. CRSCTL stops or relocates dependent resources when you use this parameter.<br>Note: When you are relocating resources that have cardinality greater than 1, you must use either `-k` or `-s` to narrow down which resource instances are to be relocated.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

##### Usage Notes

- Any one of the three following options is required to specify which resources you want to relocate:

  - You can specify one particular resource to relocate.

  - Or you can specify one particular or all the resources to relocate from a particular source server.

  - Thirdly, you can specify a resource filter that CRSCTL uses to match resources to relocate.

- If a resource has a degree ID greater than 1, then CRSCTL relocates all instances of the resource.

- You must have read and execute permissions on the specified resources to relocate them

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources.

##### Examples

To relocate one particular resource from one server to another:

    # crsctl relocate resource myResource1 -s node1 -n node3

#### crsctl restart resource

Restarts idle resources in the cluster, instead of having to run two commands to stop and start the resource.

##### Syntax

    crsctl restart resource {resource_name [...] | -w "filter"} [-k cid] [-d did]
       [-env "env1=val1,env2=val2,..."] [-i] [-f]

##### Parameters

Table E-13 crsctl restart resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]`                          | Specify one or more space-delimited names of resources you want to restart.                                                                                                                                                                                                              |
| `-w "``filter``"`                                | Specify a resource filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resources. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: "Filters" for more information                                                    |
| `-k ``cid`                                       | Specify the resource cardinality ID. If you specify this parameter, then Oracle Clusterware restarts the resource instances that have the cardinality you specify.                                                                                                                       |
| `-d ``did`                                       | Specify the resource degree ID. If you specify this parameter and the degree ID is greater than 1, then Oracle Clusterware restarts all resource instances that meet this criteria.<br>Note: You cannot use the `-d` parameter without specifying the `-k` parameter.                    |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).           |
| `-i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other. |
| `–f`                                             | Use the `-f` parameter to relocate a resource running on another server on which the resource you want to restart has a hard start dependency. If you do not specify the force parameter in this case, then the start command fails.                                                     |

##### Usage Notes

- Either of the following options is required to specify which resources you want to restart:

  - You can specify one or more resources by name to restart

  - You can specify a resource filter that Oracle Clusterware uses to match resources to restart

- You must have read and execute permissions on the specified resources to restart them

- Do not use this command to restart any resources with names that begin with ora because these resources are Oracle resources

#### crsctl setperm resource

Sets permissions for a particular resource.

##### Syntax

    crsctl setperm resource resource_name {-u acl_string | -x acl_string |
    -o user_name | -g group_name}

##### Parameters

Table E-14 crsctl setperm resource Command Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`     | Specify the name of the resource for which you want to set permissions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-u | -x | -o | -g` | You can set only one of the following permissions for a resource:<br>• `-u ``acl_string`: You can update the access control list (ACL) for a resource<br>• `-x ``acl_string`: You can delete the ACL for a resource<br>• `-o ``user_name`: You can change the owner of a resource by entering a user name<br>• `-g ``group_name`: You can change the primary group of a resource by entering a group name<br>Specify a user, group, or other ACL string, as follows:<br>`user:user_name[:readPermwritePermexecPerm] |`<br>`group:group_name[:readPermwritePermexecPerm] |`<br>`other[::readPermwritePermexecPerm]`<br>• `user`: User ACL<br>• `group`: Group ACL<br>• `other`: Other ACL<br>• `readPerm`: Read permission for the resource; the letter `r` grants a user, group, or other read permission, the minus sign (`-`) denies read permission<br>• `writePerm`: Write permission for the resource; the letter `w` grants a user, group, or other write permission, the minus sign (`-`) denies write permission<br>• `execPerm`: Execute permission for the resource; the letter `x` grants a user, group, or other execute permission, the minus sign (`-`) denies execute permission |

**See Also:**

[Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md) for more information about resources and resource attributes

##### Usage Notes

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources.

- You must have read and write permissions on the specified resources to set their permissions

##### Examples

To grant read, write, and execute permissions on a resource for user Scott:

    $ crsctl setperm resource myResource -u user:scott:rwx

#### crsctl start resource

Starts idle resources on a particular server in the cluster.

##### Syntax

    crsctl start resource {resource_name [...] | -w "filter" | -all}
       [-n server_name | -s server_pool_names] [-k cid] [-d did]
       [-env "env1=val1,env2=val2,..."] [-begin] [-end] [-i] [-f] [-l]

##### Parameters

Table E-15 crsctl start resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]`                          | Specify one or more space-delimited names of resources you want to start.                                                                                                                                                                                                                |
| `-w "``filter``"`                                | Specify a resource filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resources. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: "Filters" for more information                                                    |
| `–all`                                           | Use this parameter to start all resources in the cluster.                                                                                                                                                                                                                                |
| `-n ``server_name`                               | Specify the name of the server on which the resources you want to start reside. If you do not specify a server, then Oracle Clusterware starts the resources on the best server according to the attribute profile of each resource.                                                     |
| `-s ``server_pool_names`                         | Specify a single server pool name or a space-delimited list of server pools in which a resource resides that you want to start.                                                                                                                                                          |
| `-k ``cid`                                       | Specify the resource cardinality ID. If you specify this parameter, then Oracle Clusterware starts the resource instances that have the cardinality you specify.                                                                                                                         |
| `-d ``did`                                       | Specify the resource degree ID. If you specify this parameter and the degree ID is greater than 1, then Oracle Clusterware starts all resource instances that meet this criteria.<br>Note: You cannot use the `-d` parameter without specifying the `-k` parameter.                      |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).           |
| `-begin`                                         | You can specify this parameter to begin a transparent HA action.                                                                                                                                                                                                                         |
| `-end`                                           | You can specify this parameter to end a transparent HA action.                                                                                                                                                                                                                           |
| `–i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other. |
| `–f`                                             | Use the `-f` parameter to relocate a resource running on another server on which the resource you want to start has a hard start dependency. If you do not specify the force parameter in this case, then the start command fails.                                                       |
| `–l`                                             | Use the `-l` parameter to leave the resources in the state they were in if the start command fails.                                                                                                                                                                                      |

##### Usage Notes

- Any one of the three following options is required to specify which resources you want to start:

  - You can specify one or more resources to start

  - You can specify a resource filter that Oracle Clusterware uses to match resources to start

  - You can specify the `-all` parameter to start all resources on the specified server

- You must have read and execute permissions on the specified resources to start them

- Do not use this command to start any resources with names that begin with ora because these resources are Oracle resources

- Oracle does not support starting managed applications outside of the Oracle Grid Infrastructure

##### Example

To start a resource:

    # crsctl start resource myResource -n server1

#### crsctl status resource

Obtains the status and configuration information of any number of particular resources.

##### Syntax

    crsctl status resource resource_name [...] | -w "filter" [-p | -v] | [-f | -l
       | -g] [[-k cid | -n server_name] [ -e [-p | -v]] [-d did]] | [-s -k cid
       [-d did]] [-p [-attr attribute_name[,...] [-noname]]

To print the status of the resources in tabular form:

    crsctl status resource resource_name [...] | -w "filter" -t

To print a list of the resource dependencies:

    crsctl status resource [resource_name [...]] -dependency [-stop | -pullup]

##### Parameters

Table E-16 crsctl status resource Command Parameters

| Parameter                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...] | -w "``filter``"`                                                        | Specify one or more space-delimited names of resources of which you want to check the status.<br>Optionally, you can specify a resource filter that CRSCTL uses to limit the number of resources displayed. The filter must be enclosed in double quotation marks (`""`). Values that contain parentheses or spaces must be enclosed in single quotation marks (`''`). Operators must be surrounded by spaces. Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits the display to only resources of `cluster_resource` type.<br>• `"CHECK_INTERVAL > 10"`: This filter limits the display to resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits the display to resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`.<br>• `"START_DEPENDENCIES='hard(appsvip)'"`: This filter limits the display to resources that have a hard start dependency on the `appsvip` resource.<br>See Also: "Filters" for more information |
| `[-p | -v] | [-f | -l | -g]`                                                                     | You can optionally specify the following parameters:<br>• Specify either the `-p` parameter to display the static configuration of the resource or the `-v` parameter to display the run-time configuration of the resource.<br>• Specify the `-f` parameter to display the full configuration of the resource; or specify the `-l` parameter to display all cardinal and degree values of the resource; or specify the `-g` parameter to check whether the specified resources are registered                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `[[-k ``cid`` | -n ``server_name``] [ -e [-p | -v]] [-d ``did`` | [-s -k ``cid`` [-d ``did``]]]` | You can specify one of the following two options:<br>• Specify the `-k ``cid` parameter to specify a cardinality ID of the resources you want to query. Or you can specify the `-n` parameter to specify a particular server on which to check resources. Optionally, you can specify the `-d` parameter with the `-n` parameter to specify the degree ID of resources you want to check. If you specify a degree ID greater than 1, then Oracle Clusterware checks all resource instances on the server that meet this criteria.<br>• Use the `-e` parameter to evaluate the special values of a resource instance. You must also specify `-p` or `-v` with the `-e` parameter.<br>• Specify the `-s` parameter with the `-k` parameter to obtain a list of target servers for relocation. You can further limit the output by specifying a degree ID with the `-d` parameter.                                                                                                                                                                                                                                                                                |
| `–t`                                                                                             | Specify the `-t` parameter to display the output in tabular form.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-p [-attr ``attribute_name``[,...] [-noname]`                                                   | Specify `-attr` (followed by a single attribute name or a comma-delimited list of attribute names) or `-noname` following `-p` to either print specific attributes or bypass the default printing of the resource name, respectively.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-dependency [-stop | -pullup]`                                                                  | Specify the `-dependency` parameter to display resource dependencies. If you do not specify either the `-stop` or `-pullup` option, then CRSCTL displays the start dependencies of the resource.<br>Use either of the following options with the `-dependency` parameter:<br>• Specify the `-stop` parameter to display resource stop dependencies.<br>• Specify the `-pullup` parameter to display resource pull up dependencies.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

##### Usage Notes

- Either a space-delimited list of resources or a resource filter is required.

- You must have read permissions on the specified resources to obtain their status.

- Use `crsctl status resource` to query the status information of any resource deployed in the cluster. Oracle recommends, however, that you use the respective SRCVTL command to query the status information of Oracle (`ora.*`) resources.

##### Examples

The `crsctl status resource` command returns output similar to the following:

    $ crsctl status resource ora.staii14.vip

    NAME=ora.staii14.vip
    TYPE=ora.cluster_vip_net1.type
    TARGET=ONLINE
    STATE=ONLINE on staii14

The following example shows the start dependencies for a resource named `ora.newdb.db`:

    $ crsctl status resource ora.newdb.db -dependency ora.newdb.db(ora.database.type)

      ora.ACFS_DG1.dg(ora.diskgroup.type)[hard,pullup]
        ora.asm(ora.asm.type)[hard,pullup]
          ora.LISTENER.lsnr(ora.listener.type)[weak]
            type:ora.cluster_vip_net1.type[hard:type,pullup:type]
              ora.net1.network(ora.network.type)[hard,pullup]
      ora.dbhome_dg.dbhome_dg_v.acfs(ora.acfs.type)[hard,pullup]
        ora.asm(ora.asm.type)[pullup:always]

#### crsctl stop resource

Stops running resources.

##### Syntax

    crsctl stop resource {resource_name [...] | -w "filter" | -all} [-n server_name
       | -s server_pool] [-k cid] [-d did] [-env "env1=val1,env2=val2,..."]
       [-begin | -end] [-i] [-f] [-l]

##### Parameters

Table E-17 crsctl stop resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]`                          | Alternative to using `-w` or `-all`, you can specify one or more space-delimited resource names that you want to stop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-w "``filter``"`                                | Alternative to specifying a resource name or using `-all`, you can specify a resource filter that CRSCTL uses to limit the number of resources stopped. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to stop only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to stop resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to stop resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: "Filters" for more information |
| `-all`                                           | Alternative to specifying a resource name or using `-w`, you can use this parameter to stop all resources in the cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-n ``server_name`` | -s ``server_pool`          | Optionally, you can specify the name of the server on which the resource instances you want to stop reside, or the name of a server pool in which the resource instances you want to stop reside. If you do not specify a server or server pool, then CRSCTL stops all instances of the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-k ``cid`                                       | Optionally, you can specify the resource cardinality ID. If you specify this parameter, then CRSCTL stops the resource instances that have the cardinality you specify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-d ``did`                                       | Specify the resource degree ID. If you specify this parameter and the degree ID is greater than 1, then CRSCTL stops all resource instances that meet this criteria.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-begin | -end`                                  | Optionally, you can specify either of these parameters to begin or end a transparent HA action, respectively.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `–i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `–f`                                             | Specify the `-f` parameter to force the stopping of the resource when it has other resources running that depend on it. Dependent resources are relocated or stopped when you use this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `–l`                                             | Use the `-l` parameter to leave the resources in the state they were in if the stop command fails.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

##### Usage Notes

- Any one of the three following options is required to specify which resources you want to stop:

  - You can specify by name one or more resources to stop.

  - You can specify a resource filter that CRSCTL uses to match resources to stop

  - You can specify the `-all` parameter to stop all resources on a particular server

- You must have read and execute permissions on the specified resources to stop them

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources

- Oracle does not support stopping managed applications outside of the Oracle Grid Infrastructure

##### Example

To stop a resource:

    $ crsctl stop resource -n node1 -k 2

#### crsctl add resourcegroup

Creates a resource group based on a resource group type.

Use this command to create an empty resource group into which you can add resources.

##### Syntax

    crsctl add resourcegroup group_name –type group_type
      [[-file file_path] | [-attr "attribute_name=
      attribute_value"]] [-f] [-i]

##### Parameters

Table E-18 crsctl add resourcegroup Command Parameters

| Parameter                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                                                                 | Specify the name of the resource group.                                                                                                                                                                                                                                                                                                                                         |
| `–type ``group_type`                                                         | Specify a group type for the resource group.                                                                                                                                                                                                                                                                                                                                    |
| `-file ``file_path`` | -attr "``attribute_name``=``attribute_value``[,...]"` | Provide either a file or a list of attributes that define the resource group.<br>Path name (either absolute or relative) for a text file containing line-delimited attribute name-value pairs that define the resource group.<br>Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs enclosed in double quotations marks (`""`). |
| `–f`                                                                         | Use this parameter to add a resource group that is online.                                                                                                                                                                                                                                                                                                                      |
| `–i`                                                                         | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                             |

#### crsctl check resourcegroup

Initiates a check operation on all member resources of the specified groups.

##### Syntax

    crsctl check resourcegroup {group_name [...] | -w "filter"}
      [-n server_name] [-k cid]

##### Parameters

Table E-19 crsctl check resourcegroup Command Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                 |
|:-------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`       | Specify a resource group or a number of resource groups in a space-delimited list that you want to check.                                                                                                                                                                                   |
| `-w "``filter``"`  | Alternatively, you can specify a resource group filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about using filters. |
| `-n ``server_name` | Optionally, you can specify the name of the server on which the resource group you want to check resides.                                                                                                                                                                                   |
| `-k ``cid`         | Optionally, you can specify the resource group cardinality ID. If you specify this parameter, then Oracle Clusterware checks the resource instances that have the cardinality you specify.                                                                                                  |

#### crsctl delete resourcegroup

Deletes one or more resource groups from Oracle Clusterware.

##### Syntax

    crsctl delete resourcegroup {"group_name [...]" | -w "filter"} [-f] [-i]

##### Parameters

Table E-20 crsctl delete resourcegroup Command Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`      | Specify one or more group names that you want to delete. Multiple groups must be space-delimited and enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-w "``filter``"` | Specify a resource filter that Oracle Clusterware uses to limit the number of resources evaluated for deletion. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>Note: All operators must be surrounded by spaces.<br>See Also: Filters for more information about operators |
| `-f`              | Use this parameter to delete a resource group that is online.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-i`              | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

- You must specify either a group name (or several group names) or a resource filter.

- You can only delete a resource group if no other resource groups have dependencies to it.

#### crsctl eval add resourcegroup

Predicts the effects of adding a resource group without making changes to the system.

##### Syntax

    crsctl eval add resourcegroup group_name -type group_type [-file file_path
       | -attr "attribute_name=attribute_value[,...]"] [-f]

##### Parameters

Table E-21 crsctl eval add resourcegroup Command Parameters

| Parameter                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                                                                 | Specify the name of the resource group.                                                                                                                                                                                                                                                                                                                                         |
| `-type ``group_type`                                                         | Specify a group type for the resource group.                                                                                                                                                                                                                                                                                                                                    |
| `-file ``file_path`` | -attr "``attribute_name``=``attribute_value``[,...]"` | Provide either a file or a list of attributes that define the resource group.<br>Path name (either absolute or relative) for a text file containing line-delimited attribute name-value pairs that define the resource group.<br>Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs enclosed in double quotations marks (`""`). |
| `–f`                                                                         | Use this parameter to add a resource group that is online.                                                                                                                                                                                                                                                                                                                      |

#### crsctl eval fail resourcegroup

Predicts the consequences of a resource failing.

##### Syntax

    crsctl eval fail resourcegroup {group_name | -w filter} [-n server]
       [-env "attr=val[,...]"]

##### Parameters

Table E-22 crsctl eval fail resourcegroup Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                                                       |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                    | Specify the name of a resource group you want to evaluate.                                                                                                                                                                                                                                                        |
| `-w ``filter`                   | Alternative you specifying a particular resource group, you can specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about filters |
| `-n ``server`                   | Optionally, you can specify the name of the server to which resource groups reside that you want to evaluate.                                                                                                                                                                                                     |
| `-env "``attr``=``val``[,...]"` | You can optionally override one or more resource group profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                              |

#### crsctl eval relocate resourcegroup

Predicts the effect of relocating a resource group without making changes to the system.

##### Syntax

    crsctl eval relocate resourcegroup {group_name | -all} -s server | -w filter}
       {-n server} [-f]

##### Parameters

Table E-23 crsctl eval relocate resourcegroup Command Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                         |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`  | Specify the name of a resource group that you want to evaluate.                                                                                                                                                                                                                                                                                                     |
| `-all`        | Alternative to specifying a particular resource group, you can use this parameter to evaluate relocating all resource groups.                                                                                                                                                                                                                                       |
| `-s ``server` | Specify the name of the source server on which the resource group resides that you want to relocate. This parameter is required.                                                                                                                                                                                                                                    |
| `-w ``filter` | Alternative to specifying a particular resource group, you can specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`. This parameter is required if you do not use `-s`.<br>See Also: Filters for more information about filters |
| `-n ``server` | Specify the name of the server to which you want to relocate the resource groups. This parameter is required.                                                                                                                                                                                                                                                       |
| `–f`          | Use this parameter to evaluate the operation with the force option.                                                                                                                                                                                                                                                                                                 |

#### crsctl eval start resourcegroup

Predicts the effects of starting a resource group without making changes to the system.

##### Syntax

    crsctl eval start resourcegroup {group_name | -w filter} [-n server] [-f]

##### Parameters

Table E-24 crsctl eval start resourcegroup Command Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                            |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`  | Specify a resource group or a number of resource groups in a space-delimited list that you want to evaluate. This parameter is required.                                                                                                                                                                                                               |
| `-w ``filter` | Alternatively, you can specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`. This parameter is required if you do not specify a particular resource group.<br>See Also: Filters for more information about filters |
| `-n ``server` | Specify the name of the server on which the resource group you want to evaluate resides.                                                                                                                                                                                                                                                               |
| `–f`          | Use the `-f` parameter to evaluate a resource group on a server on which one of the resources in the resource group you want to start has a hard start dependency.                                                                                                                                                                                     |

#### crsctl eval stop resourcegroup

Predicts the effect of stopping a resource group without making changes to the system.

##### Syntax

    crsctl eval stop resourcegroup {group_name | -w filter} [-f]

##### Parameters

Table E-25 crsctl eval stop resourcegroup Command Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                  |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`      | Specify a resource group or a number of resource groups in a space-delimited list that you want to stop.                                                                                                                                                                                                     |
| `-w "``filter``"` | Alternative to specifying a resource group, you can specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about using filters. |
| `–f`              | Use the `-f` parameter to stop a resource running on another server on which one of the resources in the resource group you want to stop has a hard stop dependency.                                                                                                                                         |

#### crsctl export resourcegroup

Exports the complete information and attributes of a resource groups and its member resources to a script file.

This command also exports configuration information of the resource group type and member resource types. You can run the script file on another cluster to import the resource group configuration.

##### Syntax

    crsctl export resourcegroup [group_name [...]] –file file_name

##### Parameters

Table E-26 crsctl export resource Command Parameters

| Parameter           | Description                                                                                                |
|:--------------------|:-----------------------------------------------------------------------------------------------------------|
| `group_name`        | Specify a resource group or a number of resource groups in a space-delimited list that you want to export. |
| `–file ``file_name` | Specify a name for the output script file that you will run to import the group.                           |

#### crsctl modify resourcegroup

Modifies a resource group to add attributes or update the values of existing attributes.

##### Syntax

    crsctl modify resourcegroup group_name -attr "attribute_name=
    attribute_value"} [-i] [-f] [-delete]

##### Parameters

Table E-27 crsctl modify resourcegroup Command Parameters

| Parameter                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:--------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                                      | Specify the name of the resource group you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-attr "``attribute_name``= ``attribute_value``"` | You can specify attributes for a resource group you want to modify in two different ways:<br>• Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs to modify enclosed in double quotations marks (`""`). For example:<br>`-attr "CHECK_INTERVAL=30, START_TIMEOUT=25"`<br>• Some attributes can have multiple values. In those cases, separate the values with a space and enclose the list of values in single quotation marks. For example:<br>`-attr "SERVER_POOL_NAMES=`<br>`'ora.pool1 ora.pool2',START_TIMEOUT=25"`<br>• Alternatively, you can specify attribute values for resources on a particular server, with a particular cardinality value, and with a particular degree value. This method can be useful for applications that are somehow tied to a particular server. Following the `-attr` flag, the syntax is as follows:<br>`attribute_name{@SERVERNAME(server_name)`<br>`[@DEGREEID(did)] | @CARDINALITYID(cid)`<br>`[@DEGREEID(did)]}=attribute_value`<br>• If you specify the `@SERVERNAME(``server_name``)` syntax, then the attribute value you specify for the attribute you specify is limited to resources residing on the server you specify.<br>• Alternatively, if you specify the `@CARDINALITYID(``cid``)` syntax, then the attribute value you specify for the attribute you specify is limited to resource instances with a specific cardinality ID (`cid`).<br>• Optionally, you can combine the `@DEGREEID(``did``)` syntax with either the `SERVERNAME` or `CARDINALITYID` syntax, or both, to limit the attribute value to resources with the specific `DEGREE`.<br>• Examples:<br>`CHECK_INTERVAL@SERVERNAME(node1)=45`<br>`STOP_TIMEOUT@CARDINALITYID(2)=65`<br>`STOP_TIMEOUT@SERVERNAME(node1)@DEGREEID(2)=65`<br>`STOP_TIMEOUT@CARDINALITYID(3)@DEGREEID(2)=65` |
| `–i`                                              | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource group or its dependents. Sometimes, Oracle Clusterware locks resource groups or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `–f`                                              | Use the `-f` parameter when:<br>• The resource group has a hard dependency on a non-existing resource.<br>• The owner of the resource group does not have execute permissions on one or more hard dependencies.<br>• The modification results in servers being moved into the Generic pool and resources being stopped or relocated to accomplish the server move.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `–delete`                                         | If you specify the `-delete` parameter, then Oracle Clusterware deletes the named attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

You can modify the name of the resource group and add or change existing attributes.

#### crsctl relocate resourcegroup

Relocates online resource groups from a source server to a target server.

This command first stops the resource groups you specify on the source server and then starts them on the target server.

##### Syntax

    crsctl relocate resourcegroup {group_name [...] [-k cid] | -all | -w "filter"}
       [-env "attr=val[,...]"] [-f] [-i]

##### Parameters

Table E-28 crsctl relocate resourcegroup Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                              |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                    | Specify a resource group or a number of resource groups in a space-delimited list that you want to relocate.                                                                                                                                                                             |
| `-k ``cid`                      | Optionally, you can specify the resource group cardinality ID. If you specify this parameter, then CRSCTL relocates the resource instances that have the cardinality you specify.                                                                                                        |
| `-all`                          | Specify this parameter to relocate all resource groups on the source server.                                                                                                                                                                                                             |
| `-w "``filter``"`               | Specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about filters                                        |
| `-s ``source_server_name`       | Specify the name of the source server on which the resource groups reside that you want to relocate. This parameter is required.                                                                                                                                                         |
| `-n ``target_server_name`       | Optionally, you can specify the name of the server to which you want to relocate the resource groups. If you do not specify a target server, then CRSCTL relocates the resource groups on the best server according to the attribute profile of each resource group.                     |
| `-env "``attr``=``val``[,...]"` | You can optionally override one or more resource group profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).     |
| `–f`                            | Specify this option force the relocation of the resource groups you specify.                                                                                                                                                                                                             |
| `–i`                            | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other. |

##### Example

To relocate all resource groups running on `node1` to `node2`:

    $ crsctl relocate resourcegroup resGrp1 -s node1 -n node2

#### crsctl restart resourcegroup

Restarts resource groups on the server where they currently reside.

##### Syntax

    crsctl restart resourcegroup {group_name [...] | -w "filter"} [-k cid]
       [-env "env1=val1,env2=val2,..."] [-f] [-i]

##### Parameters

Table E-29 crsctl restart resourcegroup Command Parameters

| Parameters                                       | Description                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                                     | Specify a resource group or a number of resource groups in a space-delimited list that you want to restart.                                                                                                                                                                              |
| `-w "``filter``"`                                | Specify a resource group filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about filters                            |
| `-k ``cid`                                       | Specify the resource group cardinality ID. If you specify this parameter, then Oracle Clusterware restarts the resource instances that have the cardinality you specify.                                                                                                                 |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource group profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).     |
| `–f`                                             | Use the `-f` parameter to restart a resource, running on the server on which the resource group resides that you want to restart, that has a hard start dependency on another resource. If you do not specify the force parameter in this case, then the start command fails.            |
| `–i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other. |

##### Example

The following command restarts resource group `resGrp1`:

    $ crsctl restart resourcegroup resGrp1

#### crsctl start resourcegroup

Starts one or more resource groups on specific or preconfigured servers or server pools.

CRSCTL starts resource groups to which there is a hard or weak start dependency, and all enabled member resources of the group. This command reports progress messages for each resource and resource group that CRSCTL starts.

##### Syntax

    crsctl start resourcegroup {group_name [...] | -w "filter"] | -all}
      [-n server_name | -s server_pool] [-k cid] [-env "attr=val[,..."]]
      [-f] [-i] [-l]

##### Parameters

Table E-30 crsctl start resourcegroup Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                              |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                    | Specify a resource group or a number of resource groups in a space-delimited list that you want to start.                                                                                                                                                                                |
| `-w "``filter``"`               | Specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about filters                                        |
| `-all`                          | Specify this parameter to start all resource groups on the cluster.                                                                                                                                                                                                                      |
| `-n ``server_name`              | Specify the name of the server on which the resource group you want to start resides. If you do not specify a server, then CRSCTL starts the resources on the best server according to the attribute profile of each resource.                                                           |
| `-s ``server_pool`              | Specify a single server pool name or a space-delimited list of server pools in which a resource group resides that you want to start.                                                                                                                                                    |
| `-k ``cid`                      | Specify the resource group cardinality ID. If you specify this parameter, then CRSCTL starts the resource instances that have the cardinality you specify.                                                                                                                               |
| `-env "``attr``=``val``[,...]"` | You can optionally override one or more resource group profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).     |
| `–f`                            | Use the `-f` parameter to start a resource group on a server on which one of the resources in the resource group you want to start has a hard start dependency. If you do not specify the force parameter in this case, then the start command fails.                                    |
| `–i`                            | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other. |
| `–l`                            | Use the `-l` parameter to leave the resource groups in the state they were in if the start command fails.                                                                                                                                                                                |

##### Examples

To start a resource group in a server pool:

    $ crsctl start resourcegroup rg1 -s pool1

#### crsctl status resourcegroup

Displays the state of resource groups.

##### Syntax

    crsctl status resourcegroup [group_name [...] | -w "filter"]
       [-p [-attr "attribute_name=attribute_value" [-noname]] | -v [-attr
       "attribute_name=attribute_value"] [-noname]]] | [-f] [-l] [-g] | [[-k cid |
       -n server_name] [-e [-p | -v]]] [-s -k cid] | -noauto]]

##### Parameters

Table E-31 crsctl status resourcegroup Command Parameters

| Parameter                                                        | Description                                                                                                                                                                                                                                                   |
|:-----------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                                                     | Specify a resource group or a number of resource groups in a space-delimited list that you want to query. If you do not specify a resource group name or filters, then CRSCTL displays the status for all resource groups.                                    |
| `-w "``filter``"`                                                | Specify a resource group filter surrounded by double quotation marks (`""`) that Oracle Clusterware uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about filters |
| `-p -attr "``attribute_name``=``attribute_value``" [-noname]`    |                                                                                                                                                                                                                                                               |
| `-v [-attr "``attribute_name``=``attribute_value``"] [-noname]]` | Optionally, you can specify this parameter to display the status for all member resources of a particular resource group.                                                                                                                                     |
| `–f`                                                             | Optionally, you can specify this parameter to display the full configuration of the resource group.                                                                                                                                                           |
| `-l`                                                             |                                                                                                                                                                                                                                                               |
| `-g`                                                             |                                                                                                                                                                                                                                                               |
| `-k ``cid`                                                       | Specify the resource group cardinality ID. If you specify this parameter, then CRSCTL displays the status of the resource groups that have the cardinality you specify.                                                                                       |
| `-n ``server_name`                                               |                                                                                                                                                                                                                                                               |
| `–e`                                                             | Optionally, you can specify this parameter to exclude automatic resource groups. The default is to display the status of all resource groups.                                                                                                                 |
| `-p | -v`                                                        |                                                                                                                                                                                                                                                               |
| `-s -k ``cid`                                                    |                                                                                                                                                                                                                                                               |
| `-noauto`                                                        |                                                                                                                                                                                                                                                               |

##### Example

The following command shows the status of resource group `rg1`, which resides on `node1`:

    $ crsctl status resourcegroup rg1 -n node1

#### crsctl stop resourcegroup

Stops one or more resource groups on optionally specified preconfigured servers or server pools.

CRSCTL stops all member resources of the resource group. You must use the `-f` to stop the resource group if other resource groups have stop dependencies on it.

##### Syntax

    crsctl stop resourcegroup {group_name [...] | -w "filter"] | -all}
      [-n server_name | -s server_pool] [-k cid] [-env "attr=val[,...]"]
      [-f] [-i] [-l]

##### Parameters

Table E-32 crsctl stop resourcegroup Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                                                                       |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_name`                    | Alternative to using `-w` or `-all`, you can specify a resource group or a number of resource groups in a space-delimited list that you want to stop.                                                                                                                                                                             |
| `-w "``filter``"`               | Alternative to specifying a resource group name or using `-all`, you can specify a resource group filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource groups. For example, `-w "TYPE = ora.database.type"` or `-w "NAME = cs1"`.<br>See Also: Filters for more information about using filters. |
| `-all`                          | Alternative to specifying a resource name or using `-w`, you can specify this parameter to stop all resource groups on the cluster.                                                                                                                                                                                               |
| `-n ``server_name`              | Specify the name of the server on which the resource group you want to stop resides. If you do not specify a server, then CRSCTL stops the resources on the best server according to the attribute profile of each resource.                                                                                                      |
| `-s ``server_pool`              | Specify a single server pool name or a space-delimited list of server pools in which a resource group resides that you want to stop.                                                                                                                                                                                              |
| `-k ``cid`                      | Specify the resource group cardinality ID. If you specify this parameter, then Oracle Clusterware stops the resource instances that have the cardinality you specify.                                                                                                                                                             |
| `-env "``attr``=``val``[,...]"` | You can optionally override one or more resource group profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                                              |
| `–f`                            | Use the `-f` parameter to stop a resource running on another server on which one of the resources in the resource group you want to stop has a hard stop dependency. If you do not specify the force parameter in this case, then the stop command fails.                                                                         |
| `–i`                            | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                          |
| `–l`                            | Use the `-l` parameter to leave the resource groups in the state they were in if the stop command fails.                                                                                                                                                                                                                          |

##### Example

The following command stops resource group `rg1`:

    $ crsctl stop resourcegroup rg1

#### crsctl add resourcegrouptype

Registers a new resource group type in Oracle Clusterware.

Oracle recommends that applications that are made up of multiple resources define a resource group type to obtain a distinct identity and also to create new group-level attributes.

##### Syntax

    crsctl add resourcegrouptype group_type_name –basetype base_group_type
      {-file file_path | -attr "attribute_name=attribute_value"} [-i]

##### Parameters

Table E-33 crsctl add resourcegrouptype Command Parameters

| Parameter                                                              | Description                                                                                                                                                                                                                                                                                                                                                                                        |
|:-----------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_type_name`                                                      | Specify the name of the resource group type.                                                                                                                                                                                                                                                                                                                                                       |
| `–basetype ``base_group_type`                                          | Specify the base group type of the resource group type.                                                                                                                                                                                                                                                                                                                                            |
| `-file ``file_path`` | -attr "``attribute_name``=``attribute_value``"` | You must provide either a file or a list of attributes that define the resource group type.<br>Path name (either absolute or relative) for a text file containing line-delimited attribute name-value pairs that define the resource group type.<br>Following the `-attr` flag, you can specify one or more comma-delimited attribute name-value pairs enclosed in double quotations marks (`""`). |
| `-i`                                                                   | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                |

#### crsctl delete resourcegrouptype

Deletes one or more resource group types from Oracle Clusterware.

##### Syntax

    crsctl delete resourcegrouptype {"group_type_name [...]" | -w "filter" [-i]

##### Parameters

Table E-34 crsctl delete resourcegrouptype Command Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `group_type_name` | Specify one or more group type names that you want to delete. Multiple group types must be space-delimited and enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-w "``filter``"` | Specify a resource filter that Oracle Clusterware uses to limit the number of resources evaluated for deletion. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>Note: All operators must be surrounded by spaces.<br>See Also: Filters for more information about operators |
| `-i`              | If you specify `-i`, then CRSCTL returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### crsctl modify resourcegrouptype

Modifies a resource group type to add attributes or update the values of existing attributes.

##### Syntax

    crsctl modify resourcegrouptype group_type_name -attr "attribute_name=attribute_value"

##### Usage Notes

You can modify the name of the resource group type and add or change existing attributes.

#### crsctl get tracefileopts

Returns the tracing settings for a specific module.

##### Syntax

    crsctl get tracefileopts module_name

##### Usage Notes

Specify one of the following modules to obtain tracing information:

- `mdns`: Multicast domain name server
- `gpnp`: Grid Plug and Play service
- `css`: Cluster Synchronization Services
- `crf`: Cluster Health Monitor
- `crs`: Cluster Ready Services
- `ctss`: Cluster Time Synchronization Service
- `evm`: Event Manager
- `gipc`: Grid Interprocess Communication

#### crsctl set tracefileopts

Sets the tracing parameters for a specific module.

##### Syntax

    crsctl set tracefileopts module_name [-filesize file_size[K|k|M|m|G|g]]
       [-numsegments number_of_segments]

##### Parameters

Table E-35 crsctl set tracefileopts Command Parameters

| Parameter                           | Description                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `module_name`                       | Specify one of the following modules to set tracing information:<br>• `mdns`: Multicast domain name server<br>• `gpnp`: Grid Plug and Play service<br>• `css`: Cluster Synchronization Services<br>• `crf`: Cluster Health Monitor<br>• `crs`: Cluster Ready Services<br>• `ctss`: Cluster Time Synchronization Service<br>• `evm`: Event Manager<br>• `gipc`: Grid Interprocess Communication |
| `-filesize ``file_size`             | Specify the size of a single trace file in kilobytes (`K|k`), megabytes (`M|m`), or gigabytes (`G|g`).                                                                                                                                                                                                                                                                                         |
| `-numsegments ``number_of_segments` | Specify the number of trace files to save before Oracle Clusterware rotates the older files out.                                                                                                                                                                                                                                                                                               |

#### crsctl add type

Creates a resource type in Oracle Clusterware.

##### Syntax

    crsctl add type type_name -basetype base_type_name {-attr "ATTRIBUTE=attribute_name
     | -file file_path,TYPE={string | int} [,DEFAULT_VALUE=default_value][,FLAGS=typeFlags"} [-i]

##### Parameters

Table E-36 crsctl add type Command Parameters

| Parameter                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type_name`                         | Specify a name for the resource type in the form of `xxx.yyy``.type`. Resource type names must be unique and cannot be changed after the resource type is registered.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-basetype ``base_type_name`        | The name of an existing base type. Any resource type that you create must either have `local_resource` or `cluster_resource` as its base resource type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-attr "ATTRIBUTE=``attribute_name` | You can specify the resource type attributes using the `-attr` argument. Each type attribute definition can contain up to four type attribute keywords that must be displayed in the order shown. Enter a comma-delimited description of one or more resource type attributes enclosed in double quotation marks (`""`). The keywords for an attribute include:<br>1. `ATTRIBUTE`: Specify a name for the attribute. The name is case-sensitive and cannot contain spaces.<br>2. `TYPE`: Specify whether the attribute type is `integer` or `string`.<br>3. `DEFAULT_VALUE`: (Optional) If the attribute is required, then a default value is not required. For attributes that are not required, you must specify a default value that Oracle Clusterware uses when you create resources based on this resource type.<br>4. `FLAGS`: (Optional) Specify one or more of the following types, separated by a vertical bar (`|`):<br>4. `CONFIG`: After you register a resource with this resource type, you can configure the attribute.<br>4. `READONLY`: After you register a resource with this resource type, you cannot modify this attribute.<br>4. `REQUIRED`: You must specify the name and value of this attribute when you create a resource that is based on this resource type. If you specify that this attribute is not required, then Oracle Clusterware uses the default value of this attribute that you specify.<br>4. `HOTMOD`: If you change the value of an attribute for resources of this type, then the changes are applied immediately with the need to restart the resource.<br>You cannot use multiple `-attr` arguments to define multiple arguments for the resource type. Instead, you can specify multiple types within the double quotation marks after the `-attr` flag. For example:<br>`"ATTRIBUTE=FOO,TYPE=integer,DEFAULT_VALUE=0,`<br>`FLAGS=REQUIRED|HOTMOD,ATTRIBUTE=BAR,TYPE=string"`<br>The preceding example defines two type attributes, `FOO` and `BAR`. When you specify the `ATTRIBUTE` keyword, it ends the previous type attribute (if any) and begins a new type attribute. |
| `-file ``file_path`                 | Path name (either absolute or relative) for a text file containing line-delimited resource type keyword-value pairs that define the resource type. An example of the contents of the file is:<br>`ATTRIBUTE=FOO`<br>`TYPE=integer`<br>`DEFAULT_VALUE=0`<br>`FLAGS=REQUIRED`<br>`ATTRIBUTE=BAR`<br>`TYPE=string`<br>Note: The keywords must be in the following order: `ATTRIBUTE`, `TYPE`, `DEFAULT_VALUE`, and `FLAGS`. When you specify the `ATTRIBUTE` keyword, it ends the previous type attribute (if any) and begins a new type attribute.<br>The preceding example defines two type attributes, `FOO` and `BAR`.<br>Note: All operators must be surrounded by spaces.<br>See Also: "Filters" for more information about operators                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `–i`                                | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

**See Also:**

"[Oracle Clusterware Resource Types](making-applications-highly-available-using-oracle-clusterware.md)" for more information about resource types

##### Usage Notes

- Both the `type_name` and `base_type_name` parameters are required

- You can either specify a file containing the type information or you can specify the type information on the command line

- Do not use this command for any resource types with names that begin with ora because these resource types are Oracle resource types

- You must have read permissions on the base type

##### Example

To create a resource type for `demoActionScript`:

    # crsctl add type test_type1 -basetype cluster_resource -attr
      "ATTRIBUTE=FOO,TYPE=integer,DEFAULT_VALUE=0"

#### crsctl delete type

Removes resource types from the Oracle Clusterware configuration.

##### Syntax

    crsctl delete type type_name [-i]

##### Usage Notes

- The `type_name` parameter is required. You can specify more than one type by separating each type by a space.

- If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.

- Do not use this command for any resource types with names that begin with ora because these resource types are Oracle resource types.

##### Example

To delete two resource types, run the following command as a user who has write permissions on the resource type:

    $ crsctl delete type test_type1 test_type2

#### crsctl getperm type

Obtains permissions for a particular resource type.

##### Syntax

    crsctl getperm type resource_type  [-u user_name] | [-g group_name]

##### Parameters

Table E-37 crsctl getperm type Command Parameters

| Parameter         | Description                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------|
| `resource_type`   | Specify the resource type for which you want to obtain permissions.                      |
| `-u ``user_name`  | If you specify `-u`, then Oracle Clusterware obtains permissions for a particular user.  |
| `-g ``group_name` | If you specify `-g`, then Oracle Clusterware obtains permissions for a particular group. |

##### Usage Notes

- The `resource_type` parameter is required

- Do not use this command for any resource types with names that begin with ora because these resource types are Oracle resource types

**See Also:**

"[Oracle Clusterware Resource Types](making-applications-highly-available-using-oracle-clusterware.md)" for more information about resource types

##### Example

This command returns output similar to the following:

    $ crsctl getperm type app.appvip.type

    Name: app.appvip.type
    owner:root:rwx,pgrp:oinstall:rwx,other::r--

#### crsctl modify type

Modifies an existing resource type.

##### Syntax

    crsctl modify type type_name -attr "ATTRIBUTE=attribute_name,TYPE={string | int}
      [,DEFAULT_VALUE=default_value [,FLAGS=[READONLY][| REQUIRED]]" [-i] [-f]]

##### Parameters

Table E-38 crsctl modify type Command Parameters

| Parameter   | Description                                                                                                                                                                                                                                            |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type_name` | Specify the name of the resource type you want to modify. You cannot modify resource type names.                                                                                                                                                       |
| `–attr`     | You can modify the following resource type keywords:<br>• `TYPE`<br>• `DEFAULT_VALUE`<br>• `FLAGS`<br>Note: Although you must specify the `ATTRIBUTE` keyword, you cannot modify it.<br>See Also: `crsctl add type` for descriptions of these keywords |
| `–i`        | If you specify the `-i` parameter, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                |

##### Usage Notes

- The `type_name` parameter is required

- Do not use this command for any resource types with names that begin with ora because these resource types are Oracle resource types

**See Also:**

"[Oracle Clusterware Resource Types](making-applications-highly-available-using-oracle-clusterware.md)" for more information about resource types

##### Example

The following example modifies the two type attributes `FOO` and `BAR`:

    $ crsctl modify type myType.type -attr "ATTRIBUTE=FOO,DEFAULT_VALUE=0
    ATTRIBUTE=BAR,DEFAULT_VALUE=baz"

#### crsctl setperm type

Sets permissions for resources of a particular resource type.

##### Syntax

    crsctl setperm type resource_type_name {-u acl_string | -x acl_string |
    -o user_name | -g group_name}

##### Parameters

Table E-39 crsctl setperm type Command Parameters

| Parameter            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_type_name` | Specify the name of the resource type for which you want to set permissions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-u | -x | -o | -g`  | You can specify only one of the following parameters for a resource type:<br>• `-u ``acl_string`: You can update the access control list (ACL) for a resource type<br>• `-x ``acl_string`: You can delete the ACL for a resource type<br>• `-o ``user_name`: You can change the owner of a resource type by entering a user name<br>• `-g ``group_name`: You can change the primary group of a resource type by entering a group name<br>Specify a user, group, or other ACL string, as follows:<br>`user:user_name[:readPermwritePermexecPerm] |`<br>`group:group_name[:readPermwritePermexecPerm] |`<br>`other[::readPermwritePermexecPerm]`<br>• `user`: User ACL<br>• `group`: Group ACL<br>• `other`: Other ACL<br>• `readPerm`: Read permission for the resource type; the letter `r` grants a user, group, or other read permission, the minus sign (`-`) denies read permission<br>• `writePerm`: Write permission for the resource type; the letter `w` grants a user, group, or other write permission, the minus sign (`-`) denies write permission<br>• `execPerm`: Execute permission for the resource type; the letter `x` grants a user, group, or other execute permission, the minus sign (`-`) denies execute permission |

##### Usage Notes

- The `resource_type_name` parameter is required

- You must have read and write permissions on the specified resources to set their permissions

- Do not use this command for any resource types with names that begin with ora because these resource types are Oracle resource types

##### Example

To grant read, write, and execute permissions on a resource type for user Scott:

    $ crsctl setperm type resType -u user:scott:rwx

#### crsctl status type

Obtains the configuration information of one or more particular resource types.

##### Syntax

    crsctl status type [resource_type_name [...] | -w "filter"] [-g] [-p] [-f] [-r]

##### Parameters

Table E-40 crsctl status type Command Parameters

| Parameter                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_type_name`` [...] | -w "``filter``"` | Specify one or more space-delimited resource type names of which you want to check the status.<br>Alternatively, you can specify a resource type filter surrounded by double quotation marks (`""`) that CRSCTL uses to match resource types. For example, `-w "TYPE = ora.database.type"`.<br>See Also: "Filters" for more information                                                                                                              |
| `[-g] [-p] [-f] [-r]`                          | You can specify the following parameters as options when CRSCTL checks the status of specific resource types:<br>• `-g`: Use this parameter to check if the specified resource types are registered<br>• `-p`: Use this parameter to display static configuration of the specified resource types<br>• `-f`: Use this parameter to display the full configuration of the resource types<br>• `–r`: Use this parameter to print all of the base types |

##### Usage Notes

The `resource_type_name` parameter or a filter is required.

##### Example

The `crsctl status type` command returns output similar to the following:

    $ crsctl status type ora.network.type

    TYPE_NAME=ora.network.type
    BASE_TYPE=ora.local_resource.type

### Oracle RAC Environment CRSCTL Commands

You can use the following commands only in an Oracle RAC environment.

The commands listed in this section manage the Oracle Clusterware stack in an Oracle RAC environment, which consists of the following:

- Oracle Clusterware, the member nodes and server pools

- Oracle ASM (if installed)

- Cluster Synchronization Services

- Cluster Time Synchronization Services

#### crsctl request action

Performs a specific action on specific resource.

##### Syntax

    crsctl request action action_name {-r resource_name [...] | -w "filter"}
      [-env "env1=val1,env2=val2,..."] [-i]

##### Parameters

Table E-41 crsctl request action Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `action_name`                                    | Specify the name of the action you want perform. Actions supported by a particular resource are listed in the `ACTIONS` resource attribute of that resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-r ``resource_name`` [...]`                     | Specify a particular resource. Multiple resource names must be separated by a space.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-w "``filter``"`                                | Alternative to specifying resource names, you can specify a resource filter that Oracle Clusterware uses to limit the number of resources on which actions are performed. Examples of resource filters include:<br>• `TYPE == cluster_resource`: This filter limits Oracle Clusterware to perform actions on only resources of `cluster_resource` type<br>• `CHECK_INTERVAL > 10`: This filter limits Oracle Clusterware to perform actions on only resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `(CHECK_INTERVAL > 10) AND (NAME co 2)`: This filter limits Oracle Clusterware to perform actions on only resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: "Filters" for more information |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values with the `-env` command parameter. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `–i`                                             | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

##### Usage Notes

The `action_name` must be a supported action, defined both in the agent and in the `ACTIONS` resource attribute, and the user must have permission to run the action. You can set permissions in the `ACTIONS` resource attribute.

##### Example

To initiate the specified action inside the application specific agent of a particular resource:

    $ crsctl request action action1 -r res1

#### crsctl add category

Adds a server category.

##### Syntax

    crsctl add category category_name [-attr "attr_name=attr_value
       [,attr_name=attr_value[,...]]"] [-i]

##### Parameters

Table E-42 crsctl add category Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `category_name`                              | Specify a name for the server category you want to add.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-attr "``attr_name``=``attr_value``[,...]"` | Specify the name-value pair of a category attribute you want to add preceded by the `-attr` flag.<br>Note: The `attr_name` and `attr_value` parameters must be enclosed in double quotation marks (`""`), and separate multiple name-value pairs with commas. For example:<br>`-attr "EXPRESSION='(CPU_COUNT > 2) AND (MEMORY_SIZE > 2048)'"`<br>See Also:<br>• [Table 3-4](policy-based-cluster-and-capacity-management.md) for a list of attributes you can use with this command<br>• "Filters" for information about operators |
| `–i`                                         | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                          |

##### Usage Notes

If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

    "START_DEPENDENCIES='hard(res1,res2,res3)'"

##### Example

To add a server category:

    $ crsctl add category cat1 -attr "EXPRESSION='(CPU_COUNT > 2) AND (MEMORY_SIZE > 2048)'"

#### crsctl delete category

Deletes a server category.

##### Syntax

    crsctl delete category category_name [category_name [...]] [-i]

##### Usage Notes

- Specify the name of the server category or a space-delimited list of server categories that you want to delete.

- If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.

##### Example

To delete a server category:

    $ crsctl delete category blue_server -i

#### crsctl modify category

Modifies an existing server category.

##### Syntax

    crsctl modify category category_name [-attr "attr_name=attr_value
       [,attr_name=attr_value[,...]]"] [-i] [-f]

##### Parameters

Table E-43 crsctl modify category Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:---------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `category_name`                              | Specify the name of the server category you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-attr "``attr_name``=``attr_value``[,...]"` | Specify the name-value pair of a category attribute you want to modify preceded by the `-attr` flag.<br>Note: The `attr_name` and `attr_value` parameters must be enclosed in double quotation marks (`""`), and separate multiple name-value pairs with commas. For example:<br>`"ACL='owner:st-cdc\cdctest:rwx,pgrp::---',`<br>`ACTIVE_CSS_ROLE=hub"`<br>See Also:<br>• [Table 3-4](policy-based-cluster-and-capacity-management.md) for a list of attributes you can use with this command<br>• "Filters" for information about operators |
| `–i`                                         | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `–f`                                         | Use this parameter to force the operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

##### Usage Notes

If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

    "START_DEPENDENCIESs=s'hard(res1,res2,res3)'"

##### Example

To modify a server category:

    $ crsctl modify category blue_server -attr  "EXPRESSION=(LOCATION=hub)"

#### crsctl status category

Obtains information about a server category.

##### Syntax

    crsctl status category {category_name [category_name [...]] | [-w "filter" |
       -server server_name]}

##### Parameters

Table E-44 crsctl status category Command Parameters

| Parameter               | Description                                                                                                                     |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `category_name`` [...]` | Specify the name of the server category or a space-delimited list of server categories for which you want to obtain the status. |
| `-w "``filter``"`       | Alternatively, you can specify a category filter preceded by the `-w` flag.<br>See Also: "Filters" for more information         |
| `-server ``server_name` | Alternatively, you can specify a particular server to list all of the categories that the server matches.                       |

##### Examples

To obtain the status of a server category using filters:

    $ crsctl stat category -w "ACTIVE_CSS_ROLE = hub"

    NAME=my_category_i
    ACL=owner:scott:rwx,pgrp:svrtech:rwx,other::r--
    ACTIVE_CSS_ROLE = hub
    EXPRESSION=(CPU_COUNT > 3)

To obtain the status of a server category by server:

    $ crsctl stat category -server node1

    NAME=my_category
    ACL=owner:scott:rwx,pgrp:svrtech:rwx,other::r--
    ACTIVE_CSS_ROLE = hub
    EXPRESSION=

To print all resources containing `ASM`:

    $ crsctl stat res -w "NAME co asm" -t
    --------------------------------------------------------------------------------
    Name   Target   State   Server            State details
    --------------------------------------------------------------------------------
    Cluster Resources
    --------------------------------------------------------------------------------
    ora.asm(ora.asmgroup)
    1      ONLINE   ONLINE   stbm000042-vm1   Started,STABLE
    2      ONLINE   ONLINE   stbm000042-vm2   Started,STABLE
    3      ONLINE   ONLINE   stbm000042-vm3   Started,STABLE
    ora.asmnet1.asmnetwork(ora.asmgroup)
    1      ONLINE  ONLINE    stbm000042-vm1   STABLE
    2      ONLINE  ONLINE    stbm000042-vm2   STABLE
    3      ONLINE  ONLINE    stbm000042-vm3   STABLE
    --------------------------------------------------------------------------------

To print all resources containing `db`:

    $ crsctl stat res -w "NAME co db" -t
    --------------------------------------------------------------------------------
    Name   Target   State   Server             State details
    --------------------------------------------------------------------------------
    Cluster Resources
    --------------------------------------------------------------------------------
    ora.cdb19.db
    1      ONLINE   ONLINE   stbm000042-vm1    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    2      ONLINE   ONLINE   stbm000042-vm2    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    3      ONLINE   ONLINE   stbm000042-vm3    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    4      ONLINE   ONLINE   stbm000042-vm4    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    --------------------------------------------------------------------------------

To print all resources containing `db` and their state is `ONLINE`:

    crsctl stat res -w "(NAME en db) AND (STATE = ONLINE)" -t
    --------------------------------------------------------------------------------
    Name   Target   State   Server             State details
    --------------------------------------------------------------------------------
    Cluster Resources
    --------------------------------------------------------------------------------
    ora.cdb19.db
    1      ONLINE   ONLINE   stbm000042-vm1    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    2      ONLINE   ONLINE   stbm000042-vm2    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    3      ONLINE   ONLINE   stbm000042-vm3    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE
    4      ONLINE   ONLINE   stbm000042-vm4    Open,HOME=/u01/app/oracle/product/19c/dbhome,STABLE

#### crsctl check cluster

Checks the status of the Oracle Clusterware stack from any node in the cluster.

##### Syntax

    crsctl check cluster [-all | [-n server_name [...]]

##### Usage Notes

- You can check the status of the Oracle Clusterware stack on all nodes in the cluster with the `-all` parameter or you can specify one or more space-delimited nodes. If you do not specify either parameter, then Oracle Clusterware checks the status of the Oracle Clusterware stack on the local server.

- You can use this cluster-aware command on any node in the cluster.

##### Example

The `crsctl check cluster` command returns output similar to the following:

    $ crsctl check cluster -all
    *****************************************************************
    node1:
    CRS-4537: Cluster Ready Services is online
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online
    *****************************************************************
    node2:
    CRS-4537: Cluster Ready Services is online
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online
    *****************************************************************

#### crsctl start cluster

Starts the Oracle Clusterware stack when run on any node in the cluster.

##### Syntax

    crsctl start cluster [[-all] | [-n server [...]] | -hub | -w "filter"]

##### Parameters

Table E-45 crsctl start cluster Command Parameters

| Parameter             | Description                                                                                                                                                                         |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-all`                | Use this parameter to start the Oracle Clusterware stack on all servers in the cluster.                                                                                             |
| `-n ``server`` [...]` | Optionally, you can specify one or more named servers in the cluster (separate multiple server names by a space), or the local server, if you do not specify either `-all` or `-n`. |
| `-hub`                | Optionally, you can specify `-hub` to start the Oracle Clusterware stack on Hub Nodes in the cluster.                                                                               |
| `-w "``filter``"`     | Optionally, you can use this parameter to start only servers that match a filter, such as `"ACTIVE_CSS_ROLE = hub"`.<br>See Also: Filters for more information about filters.       |

#### crsctl stop cluster

Stops the Oracle Clusterware stack on all servers in the cluster or specific servers when you run the command on any node in the cluster.

##### Syntax

    crsctl stop cluster [[-all] | [-n server [...]] | -hub | -w "filter"] [-f]

##### Parameters

Table E-46 crsctl stop cluster Command Parameters

| Parameter             | Description                                                                                                                                                                         |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-all`                | Use this parameter to start the Oracle Clusterware stack on all servers in the cluster.                                                                                             |
| `-n ``server`` [...]` | Optionally, you can specify one or more named servers in the cluster (separate multiple server names by a space), or the local server, if you do not specify either `-all` or `-n`. |
| `-hub`                | Optionally, you can specify `-hub` to stop the Oracle Clusterware stack on a specific Hub Node in the cluster.                                                                      |
| `-w "``filter``"`     | Optionally, you can use this parameter to stop only servers that match a filter, such as `"ACTIVE_CSS_ROLE = hub"`.<br>See Also: Filters for more information about filters.        |

##### Usage Notes

- You must run this command as `root`.

- If you do not specify `-all` or one or more space-delimited server names, then Oracle Clusterware stops the Oracle Clusterware stack on the local server.

- You can use this cluster-aware command on any node in the cluster.

- This command attempts to gracefully stop resources managed by Oracle Clusterware while attempting to stop the Oracle Clusterware stack.

  If any resources that Oracle Clusterware manages are still running after you run the `crsctl stop cluster` command, then the command fails. Use the `-f` parameter to unconditionally stop all resources and stop the Oracle Clusterware stack.

- If you intend to stop Oracle Clusterware on all or a list of nodes, then use the `crsctl stop cluster` command, because it prevents certain resources from being relocated to other servers in the cluster before the Oracle Clusterware stack is stopped on a particular server. If you must stop the Oracle High Availability Services on one or more nodes, then wait until the `crsctl stop cluster` command completes and then run the `crsctl stop crs` command on any particular nodes, as necessary.

##### Example

To stop the Oracle Clusterware stack on a particular server:

    # crsctl stop cluster -n node1

#### crsctl get cluster class

Obtains cluster class information.

##### Syntax

    crsctl get cluster class

##### Usage Notes

This command has no parameters.

#### crsctl get cluster configuration

Displays the cluster configuration information.

##### Syntax

    crsctl get cluster configuration

##### Usage Notes

This command has no parameters.

#### crsctl set cluster disabledtlsciphersuite

Adds a cipher suite to or removes a cipher suite from a list of disabled cipher suites used to secure inter-node communication.

##### Syntax

    crsctl set cluster disabledtlsciphersuite add | delete cipher_suite_name

##### Usage Notes

Use the `add` or `delete` verb to perform the operation you want and specify the name of the cipher suite you want to add or remove.

#### crsctl get cluster extended

Determines whether the cluster is an extended cluster.

##### Syntax

    crsctl get cluster extended

##### Usage Notes

This command has no parameters.

##### Example

This command returns output similar to the following:

    $ crsctl get cluster extended
    CRS-XXXX: The cluster is 'EXTENDED'
    $ crsctl get cluster extended
    CRS-XXXX: The cluster is 'NOT EXTENDED'

#### crsctl get cluster hubsize

Obtains the value of Hub Nodes in an Oracle Flex Cluster.

##### Syntax

    crsctl get cluster hubsize

##### Example

This command returns output similar to the following:

    CRS-4950: Current hubsize parameter value is 32

#### crsctl set cluster hubsize

Sets the maximum number of Hub Nodes for an Oracle Flex Cluster.

##### Syntax

    crsctl set cluster hubsize

##### Example

The following command example sets the maximum number of Hub Nodes to 32:

    $ crsctl set cluster hubsize 32

#### crsctl get cluster mode

Ascertains whether the cluster is configured for Oracle Flex Clusters or obtains the current status.

##### Syntax

    crsctl get cluster mode [config | status]

##### Usage Notes

- Specify the `config` option to obtain the mode in which the cluster is configured.

- Specify the `status` option to obtain the current status of the cluster.

#### crsctl set cluster mode

Changes a standard cluster to an Oracle Flex Cluster.

##### Syntax

    crsctl set cluster mode flex

##### Usage Notes

This command takes only the `flex` parameter, which is required.

#### crsctl get cluster name

Displays the current cluster name.

##### Syntax

    crsctl get cluster name

##### Usage Notes

This command has no parameters.

#### crsctl add cluster site

Use the `crsctl add cluster site` command to add a site to an extended cluster.

##### Syntax

    $ crsctl add cluster site site_name [-guid site_guid]

##### Usage Notes

- You must specify a name for the site you are adding. Optionally, you can provide a GUID for the site.

- An extended cluster can have a maximum of five sites.

- You cannot run this command in a cluster that is not extended.

##### Examples

The following command example adds a site called `SiteA` to an extended cluster:

    $ crsctl add cluster site SiteA

#### crsctl delete cluster site

Use the `crsctl delete cluster site` command to delete a specific site from an extended cluster.

##### Syntax

    $ crsctl delete cluster site site_name

##### Usage Notes

- You must specify the name of the site that you want to delete.

- You cannot run this command in a cluster that is not extended.

- You cannot delete a site that has nodes or disks. You must delete the nodes and drop the disks before you can delete the site.

##### Examples

The following command deletes a site named `SiteA` from an extended cluster:

    $ crsctl delete cluster site SiteA

#### crsctl modify cluster site

Modifies the configuration of a site in an extended cluster.

##### Syntax

    crsctl modify cluster site site_name {–n node1, node2, ... | -s {rejuvenate | quarantine} | [-local]}

##### Parameters

Table E-47 crsctl modify cluster site Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `site_name`                    | Specify the name of the site you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `–n ``node1, node2, ...`       | Specify this parameter to make a global change in Oracle Cluster Registry (OCR) and also push the changes to the Oracle Local Registry (OLR) on all the nodes.                                                                                                                                                                                                                                                                                                                                                        |
| `-s {rejuvenate | quarantine}` | Specify a state for the site.<br>• `rejuvenate`: Use this option to enable a previously quarantined site.<br>• A site is typically quarantined by Oracle Clusterware and Oracle ASM when it detects a storage split.<br>• `quarantine`: Use this option if you want to explicitly quarantine a site. Oracle Clusterware will not start any database instances nor Oracle ASM on a quarantined site. In the event of a storage split, Oracle Clusterware detects the condition and sets the site to quarantine status. |
| `-local`                       | Optionally, you can specify this parameter to make changes only to the Oracle Local Registry on the local node. Oracle provides this command for certain scripts that can run this when OCR is not available or for a user, if the node goes down when a global change is performed.                                                                                                                                                                                                                                  |

##### Examples

The following command example adds a node called `node11` to the SiteA:

    $ crsctl modify cluster site SiteA –n node1, node2,node11

#### crsctl query cluster site

Displays site information in an extended cluster.

##### Syntax

    $ crsctl query cluster site {site_name | -all}

##### Usage Notes

- You can specify a particular site by name or you use `-all` to get the information for all the sites in the extended cluster.

- The command returns the names of the sites, the site GUID, the site state, and the components of the site.

- The Oracle Clusterware technology stack must be active and up to run this command.

- An extended cluster can have up to five sites.

##### Examples

This command returns output similar to the following:

    $ crsctl query cluster site –all
    Site 'SiteA' identified by GUID '7b7b3bef4c1f5ff9ff8765bceb45433a' in state 'ONLINE' contains nodes 'node1,node2,node3', and disks 'disk1, disk2, disk3'.
    Site 'SiteB' identified by GUID '23453bef4c1f5ff9ff8765bceb45433a' in state 'QUARANTINED' contains nodes 'node4, node5, node6', and disks 'disk4, disk5, disk6'.
    Site 'SiteQ' identified by GUID '98763bef4c1f5ff9ff8765bceb45433a' in state 'ONLINE' contains no nodes and disk 'disk7'.
    Site 'SiteD' identified by GUID '4abcd453c6bc6fc1ffd3a58849d5ba41' in state 'ONLINE' contains nodes 'cuj1234' and no disk.

#### crsctl get cluster tlsciphersuite

Lists available cipher suites used by transport layer security for securing inter-node communication.

##### Syntax

    crsctl get cluster tlsciphersuite [disabled|all]

##### Usage Notes

Optionally, you can specify `disabled` to list only those cipher suites disabled for use, or you can specify `all` to list all cipher suites.

#### crsctl get cluster type

Use the `crsctl get cluster type` command to determine whether the cluster is an Oracle Flex Cluster or an application cluster.

##### Syntax

    crsctl get cluster type

This command returns the cluster type, either `flex` or `application`.

#### crsctl set cluster type

Sets the type of the cluster.

##### Syntax

    crsctl Set cluster type flex | application

##### Usage Notes

Specify either `flex` or `application` to choose which type of cluster you want to set.

#### crsctl get cpu equivalency

The `crsctl get cpu equivalency` command obtains the value of the `CPU_EQUIVALENCY` server configuration attribute.

##### Syntax

    crsctl get cpu equivalency

##### Example

This command returns output similar to the following:

    $ crsctl get cpu equivalency

    CRS-4963: Current cpu equivalency parameter value is 1000

**Related Topics**

- [Server Configuration and Server State Attributes](policy-based-cluster-and-capacity-management.md)

#### crsctl set cpu equivalency

The `crsctl set cpu equivalency` command sets a value for the `CPU_EQUIVALENCY` server configuration attribute.

##### Syntax

    crsctl set cpu equivalency number

##### Usage Notes

This command takes only a numerical value to set the `CPU_EQUIVALENCY` server configuration attribute.

##### Example

The following example sets the value of the `CPU_EQUIVALENCY` server configuration attribute to 2000:

    $ crsctl set cpu equivalency 2000

    CRS-4416: Server attribute 'CPU_EQUIVALENCY' successfully changed.
     Restart Oracle High Availability Services for new value to take effect.

**Related Topics**

- [Server Configuration and Server State Attributes](policy-based-cluster-and-capacity-management.md)

#### crsctl check crs

Checks the status of Oracle High Availability Services and the Oracle Clusterware stack on the local server.

##### Syntax

    crsctl check crs

##### Example

This command returns output similar to the following:

    CRS-4638: Oracle High Availablity Services is online
    CRS-4537: Cluster Ready Services is onlin
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online

#### crsctl config crs

Displays Oracle High Availability Services automatic startup configuration.

##### Syntax

    crsctl config crs

##### Example

This command returns output similar to the following:

    CRS-4622: Oracle High Availability Services autostart is enabled.

#### crsctl disable crs

Prevents the automatic startup of Oracle High Availability Services when the server boots.

##### Syntax

    crsctl disable crs

##### Usage Notes

- This command only affects the local server

- If you disable Oracle High Availability Services automatic startup, you must use the `crsctl start crs` command to start Oracle High Availability Services

##### Example

This command returns output similar to the following:

    CRS-4621: Oracle High Availability Services autostart is disabled.

#### crsctl enable crs

Enables automatic startup of Oracle High Availability Services when the server boots.

##### Syntax

    crsctl enable crs

##### Usage Notes

This command only affects the local server

##### Example

This command returns output similar to the following:

    CRS-4622: Oracle High Availability Services autostart is enabled.

#### crsctl start crs

Starts Oracle High Availability Services on the local server.

##### Syntax

    crsctl start crs [-excl [-nocrs] [-cssonly]] | [-wait | -waithas | -nowait] | [-noautostart]

##### Parameters

Table E-48 crsctl start crs Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                       |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-excl [-nocrs] [-cssonly]`  | Starts Oracle Clusterware in exclusive mode with two options:<br>• Specify the `-nocrs` parameter to start Oracle Clusterware in exclusive mode without starting CRSD.<br>• Specify the `-cssonly` parameter to start CSSD, only.                                                                 |
| `-wait | -waithas | -nowait` | Choose one of the following:<br>• Specify `-wait` to wait until startup is complete and display all progress and status messages.<br>• Specify `-waithas` to wait until startup is complete and display OHASD progress and status messages.<br>• Specify `-nowait` to not wait for OHASD to start |
| `-noautostart`               | Start only OHASD.                                                                                                                                                                                                                                                                                 |

##### Usage Notes

- You must run this command as `root`

- This command starts Oracle High Availability Services only on the local server

##### Example

To start Oracle High Availability Services on the local server:

    # crsctl start crs

#### crsctl stop crs

Stops Oracle High Availability Services on the local server.

##### Syntax

    crsctl stop crs [-f]

##### Usage Notes

- You must run this command as `root`.

- This command attempts to gracefully stop resources managed by Oracle Clusterware while attempting to stop Oracle High Availability Services on the local server.

  If any resources that Oracle Clusterware manages are still running after you run the `crsctl stop crs` command, then the command fails. Use the `-f` parameter to unconditionally stop all resources and stop Oracle High Availability Services on the local server.

- If you intend to stop Oracle Clusterware on all or a list of nodes, then use the `crsctl stop cluster` command, because it prevents certain resources from being relocated to other servers in the cluster before the Oracle Clusterware stack is stopped on a particular server. If you must stop the Oracle High Availability Services on one or more nodes, then wait until the `crsctl stop cluster` command completes and then run the `crsctl stop crs` command on any particular nodes, as necessary.

- Before attempting to shut down the Oracle Clusterware technology stack on all nodes with an Oracle ASM instance running in parallel in an Oracle Clusterware standard Cluster with Oracle Flex ASM enabled, you must first relocate at least one Oracle ASM instance to another node where Oracle ASM is not running.

- CRSCTL uses a `shutdown abort` stop option when running this command to improve high availability and failover times.

- If you shut down the database with SRVCTL, before you run `crsctl stop crs`, then you must restart the resources after Oracle Clusterware comes up.

- In Oracle Clusterware 11g release 2 (11.2.0.3), when you run this command in Solaris Sparc and Solaris X64 environments, drivers remain loaded on shutdown and subsequent startup. This does not happen in Linux environments.

##### Example

To stop Oracle High Availability Services on the local server:

    # crsctl stop crs

#### crsctl query crs activeversion

Displays the active version and the configured patch level of the Oracle Clusterware software running in the cluster.

During a rolling upgrade, however, the active version is not advanced until the upgrade is finished across the cluster, until which time the cluster operates at the pre-upgrade version. Additionally, during a rolling patch, the active patch level is not advanced until the patching is finished across the cluster, until which time the cluster operates at the pre-upgrade patch level.

##### Syntax

    crsctl query crs activeversion [-f]

##### Usage Notes

If you specify the `-f` parameter, then this command also prints the patch level for each configured node in the cluster.

##### Example

This command returns output similar to the following:

    Oracle Clusterware active version on the cluster is [12.2.0.1.0]. The cluster
    upgrade state is [NORMAL]. The cluster active patch level is [456789126].

#### crsctl add crs administrator

Adds a user to the list of cluster administrators.

##### Syntax

    crsctl add crs administrator -u user_name [-f]

##### Parameters

Table E-49 crsctl add crs administrator Command Parameters

| Parameter        | Description                                                                                 |
|:-----------------|:--------------------------------------------------------------------------------------------|
| `-u ``user_name` | The name of the user to whom you want to give Oracle Clusterware administrative privileges. |
| `-f`             | Use this parameter to override the user name validity check.                                |

##### Usage Notes

- This command is deprecated in Oracle Clusterware 12c and later releases.

- You must run this command as `root` or a cluster administrator, or an administrator on Windows systems

- By default, `root`, the user who installed Oracle Clusterware, and the `*` wildcard are members of the list of users who have Oracle Clusterware administrative privileges. Run the `crsctl delete crs administrator` command to remove the wildcard and enable role-separated management of Oracle Clusterware.

##### Example

To add a user to the list of Oracle Clusterware administrators:

    # crsctl add crs administrator -u scott

**Related Topics**

- [Role-Separated Management](oracle-clusterware-administration.md)

#### crsctl delete crs administrator

Removes a user from the list of Oracle Clusterware administrators.

##### Syntax

    crsctl delete crs administrator -u user_name [-f]

##### Parameters

Table E-50 crsctl delete crs administrator Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-u ``user_name` | The name of the user whose Oracle Clusterware administrative privileges you want to remove.<br>By default, the list of users with Oracle Clusterware administrative privileges consists of the user who installed Oracle Clusterware, `root`, and `*`. The user who installed Oracle Clusterware and `root` are permanent members this list. The `*` value gives Oracle Clusterware administrative privileges to all users and must be removed to enable role-separated management. |
| `-f`             | Use this parameter to override the user name validity check.                                                                                                                                                                                                                                                                                                                                                                                                                        |

##### Usage Notes

- The `user_name` parameter is required

- You must run this command as `root` or a cluster administrator, or an administrator on Windows systems

- To enable role-separated management, you must remove the `*` value enclosed in double quotation marks (`""`)

##### Example

To remove a user from the list of cluster administrators:

    # crsctl delete crs administrator -u scott

**See Also:**

"[Role-Separated Management](oracle-clusterware-administration.md)"

#### crsctl query crs administrator

Displays the list of users with Oracle Clusterware administrative privileges.

##### Syntax

    crsctl query crs administrator

##### Usage Notes

Add additional information about the command here.

##### Example

This command returns output similar to the following:

    CRS Administrator List: scott

#### crsctl query crs autostart

Obtains the values of the Oracle Clusterware automatic resource start criteria.

##### Syntax

    crsctl query crs autostart

##### Example

This command returns output similar to the following:

    'Autostart delay':       60
    'Autostart servercount': 2

#### crsctl set crs autostart

Sets the Oracle Clusterware automatic resource start criteria.

The autostart delay and minimum server count criteria delay Oracle Clusterware resource autostart until one of the two conditions are met.

##### Syntax

    crsctl set crs autostart [delay delay_time] [servercount count]

##### Parameters

Table E-51 crsctl set crs autostart Command Parameters

| Parameter             | Description                                                                      |
|:----------------------|:---------------------------------------------------------------------------------|
| `delay ``delay_time`  | Specify the number of seconds to delay Oracle Clusterware autostart.             |
| `servercount ``count` | Specify the minimum number of servers required for Oracle Clusterware autostart. |

##### Example

To ensure that Oracle Clusterware delays resource autostart for 60 seconds after the first server in the cluster is ONLINE:

    $ crsctl set crs autostart delay 60

To ensure that Oracle Clusterware waits for there to be at least two servers ONLINE before it initiates resource autostart:

    $ crsctl set crs autostart servercount 2

To ensure that Oracle Clusterware delays resource autostart until either of the previous two conditions are met (in no particular order):

    $ crsctl set crs autostart delay 60 servercount 2

#### crsctl query crs releasepatch

Displays the patch level which is updated in the Grid home patch repository while patching a node.

The patch level corresponds to only the local node on which you run the command. You can run this command while the Oracle Clusterware stack is not running.

##### Syntax

    crsctl query crs releasepatch

##### Example

This command returns output similar to the following for a node which has no patches applied:

    Oracle Clusterware release patch level is [3180840333] and the complete list of
    patches is [13559647] on the local node.

#### crsctl query crs releaseversion

Displays the version of the Oracle Clusterware software stored in the binaries on the local node.

##### Syntax

    crsctl query crs releaseversion

##### Example

This command returns output similar to the following:

    Oracle High Availablity Services release version on the local node is [12.2.0.1.0]

#### crsctl query crs site

Use the `crsctl query crs site` command to determine to which site a specific host or disk belongs.

##### Syntax

    crsctl query crs site {-n host_name | -d disk_name}

##### Usage Notes

- You must specify either a host name or a disk name.

- The Oracle Clusterware technology stack must be active to run this command.

##### Examples

This command returns output similar to the following:

    $ crsctl query crs site –n hostA
    Host 'hostA' is a part of site 'SiteA'

#### crsctl query crs softwarepatch

Displays the configured patch level of the installed Oracle Clusterware.

##### Syntax

    crsctl query crs softwarepatch [host_name]

##### Usage Notes

You can optionally specify a host name to display the patch level of Oracle Clusterware installed on that particular host. Otherwise, CRSCTL displays the patch level of Oracle Clusterware installed on the local host.

##### Example

This command returns output similar to the following:

    Oracle Clusterware patch level on node [node1] is [456789126]

#### crsctl query crs softwareversion

Displays the latest version of the software that has been successfully started on the specified node.

##### Syntax

    crsctl query crs softwareversion [node_name]

##### Usage Notes

If you do not provide a node name, then Oracle Clusterware displays the version of Oracle Clusterware running on the local server.

##### Example

This command returns output similar to the following:

    Oracle Clusterware version on node [node1] is [12.2.0.1.0]

#### crsctl get css

Obtains the value of a specific Cluster Synchronization Services parameter.

##### Syntax

    crsctl get css parameter

##### Usage Notes

- Cluster Synchronization Services parameters and their default values include:

      clusterguid
      diagwait
      disktimeout (200 (seconds))
      misscount (30 (seconds))
      reboottime (3 (seconds))
      priority (4 (UNIX), 3 (Windows))
      logfilesize (50 (MB))

- This command does not display default values.

- This command only affects the local server.

##### Example

This command returns output similar to the following:

    $ crsctl get css disktimeout
    CRS-4678: Successful get disktimeout 200 for Cluster Synchronization Services.

#### crsctl pin css

Pins many specific nodes.

Pinning a node means that the association of a node name with a node number is fixed. If a node is not pinned, its node number may change if the lease expires while it is down. The lease of a pinned node never expires.

##### Syntax

    crsctl pin css -n node_name [ node_name [...]]

##### Usage Notes

- You can specify a space-delimited list of servers

- Any pre-12c release 1 (12.1) Oracle software must reside on a pinned server.

- A node may be unpinned with `crsctl unpin css`.

- Deleting a node with the `crsctl delete node` command implicitly unpins the node.

##### Example

To pin the node named `node2`:

    # crsctl pin css -n node2

#### crsctl set css

Sets the value of a Cluster Synchronization Services parameter.

##### Syntax

    crsctl set css parameter value

##### Usage Notes

- Do not use the `crsctl set css` command to set the following parameters unless instructed to do so by My Oracle Support.

- Cluster Synchronization Services parameters include:

      diagwait
      disktimeout
      logfilesize
      misscount
      priority
      reboottime

#### crsctl unpin css

Unpins many servers.

If a node is not pinned, its node number may change if the lease expires while it is down.

##### Syntax

    crsctl unpin css -n node_name [node_name [...exit]]

##### Usage Notes

- You can specify a space-delimited list of nodes.

- Unpinned servers that stop for longer than a week are no longer reported by `olsnodes`. These servers are dynamic when they leave the cluster, so you do not need to explicitly remove them from the cluster.

- Deleting a node with the `crsctl delete node` command implicitly unpins the node.

- During upgrade of Oracle Clusterware, all servers are pinned, whereas after a fresh installation of Oracle Clusterware 12c or a later release, all servers you add to the cluster are unpinned.

- You cannot unpin a server that has an instance of Oracle RAC that is older than 12c release 1 (12.1) if you installed Oracle Clusterware 12c or a later release on that server.

##### Example

To unpin two nodes:

    $ crsctl unpin css -n node1 node4

#### crsctl unset css

Unsets the value of a Cluster Synchronization Services parameter and restores it to its default value.

##### Syntax

    crsctl unset css parameter

##### Usage Notes

- You can specify the following Cluster Synchronization Services parameters:

  - `diagwait`

  - `disktimeout`

  - `misscount`

  - `reboottime`

  - `priority`

  - `logfilesize`

##### Example

To restore the `reboottime` Cluster Synchronization Services parameter to its default value:

    $ crsctl unset css reboottime

#### crsctl get css ipmiaddr

Retrieves the address stored in the Oracle Local Registry of the local Intelligent Platform Management Interface (IPMI) device.

##### Syntax

    crsctl get css ipmiaddr

##### Usage Notes

- Run the command under the user account used to install Oracle Clusterware.

- This command only obtains the IP address stored in the Oracle Local Registry. It may not be the IP address actually used by IPMI.

  Use either `ipmiutil` or `ipmitool` as `root` on the local server to obtain the IP address used by the IPMI device.

#### crsctl set css ipmiaddr

Stores the address of the local Intelligent Platform Management Interface (IPMI) device in the Oracle Local Registry.

##### Syntax

    crsctl set css ipmiaddr ip_address

##### Usage Notes

- Run the command under the user account used to install Oracle Clusterware

- Obtain the IP address used by the IPMI device using either `ipmiutil` or `ipmitool` as `root` on the local server

- Oracle Clusterware stores the IP address for IPMI in the configuration store, and distributes the address as required

- This command only stores the IPMI IP address on the server from which you run it

- This command fails if another server cannot access IPMI at the supplied address

##### Example

To store the IPMI IP address on a local server and distribute it to other cluster nodes:

    $ crsctl set css ipmiaddr 192.0.2.244

#### crsctl set css ipmiadmin

Stores the login credentials of an Intelligent Platform Management Interface (IPMI) administrator in the Oracle Local Registry.

##### Syntax

    crsctl set css ipmiadmin ipmi_administrator_name

##### Usage Notes

- This command must be run under the user account that installed Oracle Clusterware.

- When prompted, provide the new password to associate with the new administrator account name. Oracle Clusterware stores the name and password for the local IPMI in the configuration store, and distributes the new credentials as required.

- This command only modifies the IPMI administrator on the server from which you run it.

- This command fails if another server cannot access the local IPMI at the supplied address.

##### Example

To modify the IPMI administrator `scott`:

    $ crsctl set css ipmiadmin scott

#### crsctl query css ipmiconfig

Determines whether Oracle Clusterware on the local server has been configured to use IPMI for failure isolation.

Note that this command detects the presence of configuration data, but cannot not validate its correctness.

##### Syntax

    crsctl query css ipmiconfig

##### Usage Notes

- This command attempts to locate and access the IPMI configuration stored in the Oracle Cluster Registry (OCR) and should be run under the account used to install Oracle Clusterware, or an authorization failure may be reported.

- An authorization failure may not result when run under another account, if the registry contains no IPMI configuration data.

##### Example

This command returns output similar to the following:

    CRS-4236: Oracle Clusterware configured to use IPMI

Or:

    CRS-4237: Oracle Clusterware is not fully configured to use IPMI

#### crsctl unset css ipmiconfig

Clears all previously stored IPMI configuration (login credentials and IP address) from the Oracle Local Registry.

##### Prerequisites

This is appropriate when deconfiguring IPMI in your cluster or if IPMI configuration was previously stored by the wrong user.

##### Syntax

    crsctl unset css ipmiconfig

##### Usage Notes

- This command must be run under the user account originally used to configure IPMI or by a privileged user.

- This command only clears the IPMI configuration on the server on which you run it.

- If Oracle Clusterware was able to access and use the configuration data to be deleted by this command, then it will continue to do so until you restart Oracle Clusterware.

##### Example

To clear the IPMI configuration data from the Oracle Local Registry and restart Oracle Clusterware to prevent further use of IPMI, log in as `root` or a member of the Administrator's group on Windows and run the following commands:

    # crsctl unset css ipmiconfig
    # crsctl stop crs
    # crsctl start crs

#### crsctl query css ipmidevice

Determines the presence of the Intelligent Platform Management Interface (IPMI) driver on the local system.

##### Syntax

    crsctl query css ipmidevice

##### Usage Notes

- This command performs a pre-check during IPMI installation, and is normally issued only by the installer.

- This command performs a perfunctory check and a success return does not guarantee that the IPMI hardware is fully configured for use.

- There are no special privileges required to run this command.

##### Example

This command returns output similar to the following:

    CRS-4231: IPMI device and/or driver found

Or:

    CRS-4218: Unable to access an IPMI device on this system

#### crsctl get css noautorestart

Lists the problems for which automatic restart of Cluster Synchronization Services is disabled.

##### Syntax

    crsctl get css noautorestart

##### Usage Notes

- This command has no parameters.

- CRSCTL returns one of three possible values:
  - `all`: Auto restart is disabled for any problem.
  - `interconnect`: Auto restart is disabled when an interconnect problem occurs.
  - `vf`: Auto restart is disabled when a voting files problem occurs.

#### crsctl set css noautorestart

Stops the automatic restart of Cluster Synchronization Services when a specific problem occurs.

##### Syntax

    crsctl set css noautorestart {all | interconnect | vf | none}

##### Usage Notes

Specify one of the following values:

- `all`: Disables automatic restart when any problem occurs.
- `interconnect`: Disables automatic restart when an interconnect problem occurs.
- `vf`: Disables automatic restart when a voting files problem occurs.
- `none`: Enables Cluster Synchronization Services automatic restart.

#### crsctl add css votedisk

Use the `crsctl add css votedisk` command to add one or more voting files to the cluster on storage devices other than an Oracle ASM disk group.

##### Syntax

    crsctl add css votedisk vdisk [...] [-purge]

##### Parameters

Table E-52 crsctl add css votedisk Command Parameters

| Parameter       | Description                                                                                                                                 |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `vdisk`` [...]` | Specify a fully qualified path of the voting file you want to add. Specify multiple voting file paths in a space-delimited list.            |
| `-purge`        | Specify the `-purge` option to remove all existing voting files at once. You can replace the existing set of voting files in one operation. |

##### Usage Notes

- You should have at least three voting files, unless you have a storage device, such as a disk array, that provides external redundancy. Oracle recommends that you do not use more than 5 voting files. The maximum number of voting files that is supported is 15.

##### Example

To add a voting file to the cluster:

    $ crsctl add css votedisk /stor/grid/ -purge

#### crsctl delete css votedisk

Removes a voting file from the Oracle Clusterware configuration.

##### Syntax

    crsctl delete css votedisk {voting_disk_GUID [...] | vdisk [...] | +diskgroup}

##### Parameters

Table E-53 crsctl delete css votedisk Command Parameters

| Parameter                  | Description                                                                                                                                                                         |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `voting_disk_GUID`` [...]` | Specify the file universal identifier (GUID) of the voting file you want to remove. Specify multiple GUIDs in a space-delimited list.                                               |
| `vdisk`` [...]`            | Alternatively, specify the path of the voting file you want to remove. Specify multiple voting file paths in a space-delimited list.                                                |
| `+``diskgroup`             | Alternatively, specify the name of an Oracle ASM disk group that contains voting files you want to remove. You can only use parameter when Oracle Clusterware is in exclusive mode. |

##### Usage Notes

- You can specify one or more GUIDs of voting files you want to remove, one or more paths to voting files you want to remove, or the name of an Oracle ASM disk group that contains voting files you want to remove.

- You can obtain the GUIDs of each current voting file by running the `crsctl query css votedisk` command

##### Example

To remove a voting file using a GUID:

    $ crsctl delete css votedisk 26f7271ca8b34fd0bfcdc2031805581e

#### crsctl query css votedisk

Displays the voting files used by Cluster Synchronization Services, the status of the voting files, and the location of the disks, whether they are stored in Oracle ASM or elsewhere.

##### Syntax

    crsctl query css votedisk

##### Example

This command returns output similar to the following:

    ##  STATE    File Universal Id                File Name Disk group
    --  -----    -----------------                --------- ---------
    1. ONLINE   296641fd201f4f3fbf3452156d3b5881 (/ocfs2/host09_vd3) []
    2. ONLINE   8c4a552bdd9a4fd9bf93e444223146f2 (/netapp/ocrvf/newvd) []
    3. ONLINE   8afeee6ae3ed4fe6bfbb556996ca4da5 (/ocfs2/host09_vd1) []
    Located 3 voting file(s).

#### crsctl check ctss

Checks the status of the Cluster Time Synchronization services.

**Note:**

Cluster Time Synchronization Service (CTSS) is deprecated in Oracle Database 19c. 

##### Syntax

    crsctl check ctss

##### Example

This command returns output similar to the following:

    CRS-4700: The Cluster Time Synchronization Service is in Observer mode.

Or:

    CRS-4701: The Cluster Time Synchronization Service is in Active mode.
    CRS-4702: Offset from the reference node (in msec): 100

#### crsctl discover dhcp

Sends DHCP discover packets on the network at the specified port. If DHCP servers are present on the network, then they respond to the discovery message and the command succeeds.

##### Syntax

    crsctl discover dhcp -clientid clientid [-port port] [-subnet subnet]

##### Parameters

Table E-54 crsctl discover dhcp Command Parameters

| Parameter              | Description                                                                                                                            |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `-clientid ``clientid` | Specify the client ID for which you want to attempt discovery. Obtain the client ID by running the `crsctl get clientid dhcp` command. |
| `-port ``port`         | Specify the port to which CRSCTL sends the discovery packets.                                                                          |
| `-subnet ``subnet`     | Optionally, you can specify the subnet on which DHCP discover packets are sent.                                                        |

##### Usage Notes

You must run this command as `root`.

##### Example

This command returns output similar to the following:

    CRS-10009: DHCP server returned server: 192.168.53.232,
     loan address : 192.168.29.221/255.255.252.0, lease time: 43200

#### crsctl get clientid dhcp

Displays the client ID that the Oracle Clusterware agent uses to obtain the IP addresses from the DHCP server for configured cluster resources. The VIP type is required.

##### Syntax

    crsctl get clientid dhcp -cluname cluster_name -viptype vip_type
    [-vip vip_res_name] [-n node_name]

##### Parameters

Table E-55 crsctl get clientid dhcp Command Parameters

| Parameter                 | Description                                                                                                                                |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `-cluname ``cluster_name` | Specify the name of the cluster where the cluster resources are configured.                                                                |
| `-viptype ``vip_type`     | Specify the type of the VIP resource for which you want to display client IDs: `HOSTVIP`, `SCANVIP`, or `APPVIP`.                          |
| `-vip ``vip_res_name`     | Specify the name of the VIP resource. This parameter is required if you specify the `APPVIP` VIP type.                                     |
| `-n ``node_name`          | Specify the name of the node for which you want to obtain the client ID. This parameter is required if you specify the `HOSTVIP` VIP type. |

##### Example

This command returns output similar to the following:

    CRS-10007: stmjk0462clr-stmjk01-vip

#### crsctl release dhcp

Sends a DHCP lease release request to a specific client ID, and sends release packets on the network to a specific port.

##### Syntax

    crsctl release dhcp -clientid clientid [-port port]

##### Parameters

Table E-56 crsctl release dhcp Command Parameters

| Parameter              | Description                                                                                                                     |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `-clientid ``clientid` | Specify the client ID for which you want to attempt release. Obtain the client ID by running the `crsctl get clientid` command. |
| `-port ``port`         | The port to which CRSCTL sends the release packets. If you do not specify a port, then CRSCTL uses the default value 67.        |

##### Example

This command returns output similar to the following:

    CRS-10012: released DHCP server lease for client ID stmjk0462clr-stmjk01-vip
    on port 67

#### crsctl request dhcp

Sends DHCP request packets on the network to the specified port.

If the DHCP server has an IP address it can provide, then it responds with the IP address for the client ID.

##### Syntax

    crsctl request dhcp -clientid clientid [-port port]

##### Parameters

Table E-57 crsctl request dhcp Command Parameters

| Parameter              | Description                                                                                                                                          |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `-clientid ``clientid` | Specify the client ID for which you want to attempt request. Obtain the client ID by running the `crsctl get clientid` command.                      |
| `-port ``port`         | Optionally, you can specify the port to which CRSCTL sends the request packets. If you do not specify a port, then CRSCTL uses the default value 67. |

##### Example

This command returns output similar to the following:

    CRS-10009: DHCP server returned server: 192.168.53.232,
    loan address : 192.168.29.228/255.255.252.0, lease time: 43200

#### crsctl replace discoverystring

Replaces the existing discovery string used to locate voting files.

##### Syntax

    crsctl replace discoverystring "absolute_path[,...]"

##### Usage Notes

- Specify one or more comma-delimited absolute paths that match one or more voting file locations. You can use wild cards and a list of paths must be enclosed in double quotation marks (`""`).

- You must be `root`, the Oracle Clusterware installation owner, or a member of the Administrators group to run this command.

- You can run this command on any node in the cluster.

- If you store voting files in an Oracle ASM disk group, then you cannot change the discovery string.

##### Example

Assume the current discovery string is `/oracle/css1/*`. To also use voting files in the `/oracle/css2/` directory, replace the current discovery string using the following command:

    # crsctl replace discoverystring "/oracle/css1/*,/oracle/css2/*"

#### crsctl query dns

Obtains a list of addresses returned by DNS lookup of the name with the specified DNS server.

##### Syntax

    crsctl query dns -name name [-dnsserver DNS_server_address] [-type query_type]
    [-port port] [-attempts number_of_attempts] [-timeout timeout_in_seconds] [-v]

##### Parameters

Table E-58 crsctl query dns Command Parameters

| Parameter                         | Description                                                                                                                      |
|:----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `-name ``name`                    | Specify the fully-qualified domain name that you want to query.                                                                  |
| `-dnsserver ``DNS_server_address` | Optionally, you can specify the address of the DNS server on which you want the domain name to be queried.                       |
| `-type ``query_type`              | Optionally, you can select either IPv4 or IPv6 by specifying either `A` or `AAAA`, respectively, as a query type.                |
| `-port ``port`                    | Optionally, you can specify the port on which the DNS server listens. If you do not specify a port, then it defaults to port 53. |
| `-attempts ``number_of_attempts`  | Optionally, you can specify the number of retry attempts.                                                                        |
| `-timeout ``timeout_in_seconds`   | Optionally, you can specify the timeout length in seconds.                                                                       |
| `–v`                              | Verbose output.                                                                                                                  |

##### Example

The `crsctl query dns` command returns output similar to the following for a DNS server named `stmjk07-vip.stmjk0462.foo.com`:

    CRS-10024: DNS server returned 192.168.29.250 for name
    stmjk07-vip.stmjk0462.foo.com

#### crsctl start ip

Starts a given IP name or IP address on a specified interface with a specified subnet mask.

Run this command on the server on which you want to start the IP.

##### Syntax

    crsctl start ip -A {IP_name | IP_address}/netmask/interface_name

##### Parameters

Table E-59 crsctl start ip Command Parameters

| Parameter                       | Description                                                                                                                                                   |
|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IP_name`` | ``IP_address`      | Specify either a domain name or an IP address preceded by `-A`. If you do not specify a fully-qualified domain name, then CRSCTL uses a standard name search. |
| `/``netmask``/``interface_name` | Specify a subnet mask and an interface name for the IP to start, separated by a forward slash (`/`). This pair must also be preceded by a forward slash.      |

##### Example

To start an IP on the local server, run the command similar to the following:

    $ crsctl start ip -A 192.168.29.220/255.255.252.0/eth0

#### crsctl status ip

Checks if a given IP address is up on the network.

##### Syntax

    crsctl status ip -A {IP_name | IP_address}

##### Usage Notes

Specify either a domain name or an IP address preceded by `–A`. If you do not specify a fully-qualified domain name, then CRSCTL uses a standard name search.

##### Example

This command returns output similar to the following:

    CRS-10003: IP address 192.168.29.220 could be reached from current node

#### crsctl stop ip

Stops a given IP name or IP address on a specified interface with a specified subnet mask.

Run this command on the server on which you want to stop the IP.

##### Syntax

    crsctl stop ip -A {IP_name | IP_address}/interface_name

##### Parameters

Table E-60 crsctl stop ip Command Parameters

| Parameter                  | Description                                                                                                                                                   |
|:---------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IP_name`` | ``IP_address` | Specify either a domain name or an IP address preceded by `-A`. If you do not specify a fully-qualified domain name, then CRSCTL uses a standard name search. |
| `interface_name`           | Specify an interface on which to stop the IP.                                                                                                                 |

##### Example

To stop an IP on the local server, run the command similar to the following:

    $ crsctl stop ip -A MyIP.domain.com/eth0

#### crsctl lsmodules

Lists the components of the modules that you can debug.

##### Syntax

    crsctl lsmodules {mdns | gpnp | css | crf | crs | ctss | evm | gipc}

##### Usage Notes

You can obtain a list of components for any of the following modules:

- `mdns`: Multicast domain name server
- `gpnp`: Grid Plug and Play service
- `css`: Cluster Synchronization Services
- `crf`: Cluster Health Monitor
- `crs`: Cluster Ready Services
- `ctss`: Cluster Time Synchronization Service
- `evm`: Event Manager
- `gipc`: Grid Interprocess Communication

##### Example

This command returns output similar to the following:

    $ crsctl lsmodules evm
    List EVMD Debug Module: CLSVER
    List EVMD Debug Module: CLUCLS
    List EVMD Debug Module: COMMCRS
    List EVMD Debug Module: COMMNS
    List EVMD Debug Module: CRSOCR
    List EVMD Debug Module: CSSCLNT
    List EVMD Debug Module: EVMAGENT
    List EVMD Debug Module: EVMAPP
    ...

**Related Topics**

- Dynamic Debugging Using crsctl set log

#### crsctl create member_cluster_configuration

Creates the configuration deployment file for a new member cluster.

##### Syntax

    crsctl create member_cluster_configuration member_cluster_name
       -file cluster_manifest_file -member_type database | application
       [-version member_cluster_version] [-domain_services [asm_storage local
       | direct | indirect] [rhp] [acfs]

##### Parameters

Table E-61 crsctl create member_cluster_configuration Command Parameters

| Parameter                                                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `member_cluster_name`                                                   | Specify the name of the new member cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-file ``cluster_manifest_file`                                         | Specify the path of the cluster manifest file (including the `.xml` extension) you want to create.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-member_type database | application`                                   | Specify the type of member cluster you want to create. If you choose `database`, then you can use the cluster to deploy Oracle databases. If you choose `application`, then you can use the cluster to only deploy applications.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-version ``member_cluster_version`                                     | Optionally, you can specify the five-digit version of Oracle Grid Infrastructure (such as `12.2.0.1.0`) on the new member cluster, if is different from that of the domain services cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-domain_services [asm_storage local | direct | indirect] [rhp] [acfs]` | Optionally, you can specify services to be initially configured for this member cluster. If you do not use the `-domain_services` parameter, then CRSCTL only configures the Grid Infrastructure Management Repository and TFA services.<br>Additionally, you can optionally specify the Oracle ASM storage access path for the database member clusters.<br>• `local`: Storage is local to the cluster<br>• `direct` or `indirect`: Choose direct or indirect access to storage provided on the domain services cluster<br>Optionally, you can choose `rhp` to generate credentials and configuration for a Fleet Patching and Provisioning Client cluster.<br>Optionally, you can choose `acfs` for an indirect-access Member Cluster to utilize Oracle ACFS Remote to provide storage to the Member Cluster. |

#### crsctl delete member_cluster_configuration

Deletes a member cluster configuration.

##### Syntax

    crsctl delete member_cluster_configuration member_cluster_name [-f]

##### Usage Notes

You must specify the name of the member cluster you want to delete and you can optionally use `-f` to force the delete operation.

#### crsctl query member_cluster_configuration

Displays the configuration for a member cluster.

##### Syntax

    crsctl query member_cluster_configuration [member_cluster_name]

##### Usage Notes

If you choose not to specify a particular member cluster by name, then CRSCTL displays the details of all the member clusters.

##### Example

This command returns output similar to the following:

    $ crsctl query member_cluster_configuration

    indirect-mc0     12.2.0.1.0 66cdb4efd2f77f7affe559cc56003a14 ASM,GIMR,TFA
    indirect-mc1     12.2.0.1.0 2b85c6ac63434f30bfa6d074bb337621 ASM,GIMR,TFA
    indirect-mc2     12.2.0.1.0 d883e65af9ffff1fbf67e922e99bd6e4 ASM,GIMR,TFA
    indirect-mc3     12.2.0.1.0 60dcca80166aff0cffaf8e33213bfacb ASM,GIMR,TFA
    indirect-mc4     12.2.0.1.0 78d64e1454505f3effda0136738f325e ASM,GIMR,TFA

#### crsctl delete node

Removes a node from the cluster.

##### Syntax

    crsctl delete node -n node_name

##### Usage Notes

- You must be `root` to run this command

- The `node_name` parameter is required

##### Example

To delete the node named `node06` from the cluster, run the following command as `root`:

    # crsctl delete node -n node06

#### crsctl get nodename

Obtains the name of the local node.

##### Syntax

    crsctl get nodename

##### Example

This command returns output similar to the following:

    node2

#### crsctl get node role

Obtains the configured node role of nodes in the cluster.

##### Syntax

    crsctl get node role {config | status} [node node_name | -all]

##### Usage Notes

- Specify the `config` option to obtain the configured node role for a specific node.

- Specify the `status` option to obtain the current status of a specific node.

- You can specify a particular node for which to obtain role information or you can use `-all` to obtain information for all nodes in the cluster. If you do not specify a particular node, then CRSCTL returns information about the local node.

##### Examples

This command returns output similar to the following:

    $ crsctl get node role config -all
    Node 'mjkeenan_node5_0' configured role is 'hub'
    Node 'mjkeenan_node5_1' configured role is 'hub'
    Node 'mjkeenan_node5_2' configured role is 'hub'
    Node 'mjkeenan_node5_3' configured role is 'hub'

    $ crsctl get node role status -all
    Node 'mjkeenan_node5_0' active role is 'hub'
    Node 'mjkeenan_node5_2' active role is 'hub'
    Node 'mjkeenan_node5_3' active role is 'hub'

    $ crsctl get node role config -node mjkeenan_node5_1
    Node 'mjkeenan_node5_1' configured role is 'hub'

#### crsctl add policy

Adds a configuration policy to the policy set.

##### Syntax

    crsctl add policy policy_name -attr "attr_name=attr_value[,attr_name=attr_value[, ...]]"

##### Parameters

Table E-62 crsctl add policy Command Parameters

| Parameter     | Description                                                                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specify a name for the policy you want to add.                                                                                                                                                                                                          |
| `attr_name`   | Specify a description for the policy using the `DESCRIPTION` policy attribute preceded by the `-attr` flag.                                                                                                                                             |
| `attr_value`  | A value for the `DESCRIPTION` policy attribute that describes the policy.<br>Note: The `attr_name` and `attr_value` parameters must be enclosed in double quotation marks (`""`) and separated by commas. For example:<br>`-attr "DESCRIPTION=daytime"` |

##### Usage Notes

- Adding a policy does not activate the policy

- The `policy_name` parameter is required

- Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set

##### Example

To add a policy:

    $ crsctl add policy nightTime -attr "DESCRIPTION=nighttime"

#### crsctl delete policy

Deletes a configuration policy from the policy set.

##### Syntax

    crsctl delete policy policy_name [policy_name [...]] [-i]

##### Usage Notes

- Specify a name for the policy or a space-delimited list of policy names you want to delete. The `policy_name` parameter is required.

- If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.

- Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set.

##### Example

To delete a policy, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl delete policy nightTime

#### crsctl eval activate policy

Predicts the effects of activating a specific policy without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval activate policy policy_name [-f] [-admin [-l serverpools | resources
      | all] [-x] [-a]] [-explain]

##### Parameters

Table E-63 crsctl eval activate policy Command Paramaters

| Parameter                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-f`                                                  | Specify this parameter to evaluate what happens if you try to forcibly activate a policy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-admin [-l serverpools | resources | all] [-x] [-a]` | You must specify `-admin` if you specify any combination of `-l`, `-x`, and `-a`.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources. |
| `-explain`                                            | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

##### Example

This command returns output similar to the following:

    $ crsctl eval activate policy p2 -explain

    Stage Group 1:
    ---------------------------------------------------------------------------
    Stage   Required   Action
    ---------------------------------------------------------------------------
    1       E  Starting to evaluate activation of policy 'p2' with server pools
               (MIN_SIZE, MAX_SIZE) 'Free(0,-1),sp1(2,-1),sp2(4,-1)'.
            E  Looking at other server pools to see whether MIN_SIZE value 4 of
               server pool 'sp2' can be met.
            E  Scanning server pools with MIN_SIZE or fewer servers in
               ascending order of IMPORTANCE.
            E  Considering server pools (IMPORTANCE): sp1(0) for suitable
               servers.
            E  Considering server pool 'sp1' because its MIN_SIZE is 2 and it
               has 0 servers above MIN_SIZE.
            E  Relocating server 'mjkeenan_node1_0' to server pool 'sp2'.
            E  Scanning server pools with MIN_SIZE or fewer servers in
               ascending order of IMPORTANCE.
            E  Considering server pools (IMPORTANCE): sp1(0) for suitable
               servers.
            E  Considering server pool 'sp1' because its MIN_SIZE is 2 and it
               has 0 servers above MIN_SIZE.
            E  Relocating server 'mjkeenan_node1_1' to server pool 'sp2'.
    2       Y  Resource 'cs2' (3/1) will be in state 'ONLINE|INTERMEDIATE' on
               server 'mjkeenan_node1_0'.
            Y  Resource 'cs2' (4/1) will be in state 'ONLINE|INTERMEDIATE' on
               server 'mjkeenan_node1_1'.
    3       Y  Server 'mjkeenan_node1_0' will be moved from pool 'sp1' to pool
               'sp2'.
            Y  Server 'csivanan_node1_1' will be moved from pool 'sp1' to pool
               'sp2'.
    ---------------------------------------------------------------------------

**Related Topics**

- [How Server Pools Work](policy-based-cluster-and-capacity-management.md)

#### crsctl modify policy

Modifies an existing configuration policy.

##### Syntax

    crsctl modify policy policy_name -attr "attr_name=attr_value"

##### Parameters

Table E-64 crsctl modify policy Command Parameters

| Parameter     | Description                                                                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specify the name of the policy you want to modify.                                                                                                                                                                                                      |
| `attr_name`   | Specify a description for the policy using the `DESCRIPTION` policy attribute following the `-attr` flag.                                                                                                                                               |
| `attr_value`  | A value for the `DESCRIPTION` policy attribute that describes the policy.<br>Note: The `attr_name` and `attr_value` parameters must be enclosed in double quotation marks (`""`) and separated by commas. For example:<br>`-attr "DESCRIPTION=daytime"` |

##### Usage Notes

- The `policy_name` parameter is required

- Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set

##### Example

To modify an existing policy, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl modify policy p1 -attr "DESCRIPTION=daytime"

#### crsctl status policy

Obtains the status and definition of a configuration policy.

##### Syntax

    crsctl status policy [policy_name [...]] | -w "filter" | -active]

##### Parameters

Table E-65 crsctl status policy Command Parameters

| Parameter             | Description                                                                                                           |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------|
| `policy_name`` [...]` | Specify the name of the policy or a space-delimited list of policy names for which you want to view the status.       |
| `-w "``filter``"`     | Alternatively, you can specify a policy filter preceded by the `-w` flag.<br>See Also: "Filters" for more information |
| `-active`             | Alternatively, you can specify this parameter to display the status of the active policy.                             |

##### Usage Notes

Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set.

#### crsctl create policyset

Creates a single policy set, in the form of a text file, that reflects the server pool configuration.

After you create a policy set, you can copy the contents of the text file to create other policy sets.

##### Syntax

    crsctl create policyset -file path_to_file

##### Usage Notes

Specify a path to where CRSCTL creates a file that you can edit and then send back using `crsctl modify policyset` to add, delete, or update policies.

##### Example

To create a policy set:

    $ crsctl create policyset -file /tmp/ps

#### crsctl modify policyset

Modifies an existing policy set.

##### Syntax

    crsctl modify policyset {-attr "attr_name=attr_value[,attr_name=attr_value[, ...]]"
       | -file file_name} [-ksp] [-f]

##### Parameters

Table E-66 crsctl modify policyset Command Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                           |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `attr_name`         | The name of a policy attribute you want to modify following the `-attr` flag. With this command, you can specify any of the following attributes:<br>• `ACL`<br>• `LAST_ACTIVATED_POLICY`<br>• `SERVER_POOL_NAMES`                                                                    |
| `attr_value`        | A value for the policy attribute.<br>Note: The `attr_name` and `attr_value` parameters must be enclosed in double quotation marks (`""`) and separated by commas. For example:<br>`-attr "ACL='owner:mjkeenan:rwx,pgrp:svrtech:rwx,other::r--',`<br>`SERVER_POOL_NAMES=sp1 sp2 Free"` |
| `-file ``file_name` | If you specify this parameter instead of `-attr`, then enter a name of a file that contains policy set definitions.                                                                                                                                                                   |
| `-ksp`              | If you specify this parameter, then CRSCTL keeps the server pools in the system, which means that they are independent and not managed by the policy set.                                                                                                                             |
| `–f`                | Specify this parameter to force enable policy set modifications.                                                                                                                                                                                                                      |

##### Usage Notes

- Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set

- You can only specify policy definitions using the `-file` parameter or by running the `crsctl modify policy` command

##### Example

To modify an existing policy set, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl modify policyset –file my_policy_set.def

#### crsctl status policyset

Obtains the current policies in the policy set, including the access control list, which governs who can modify the set, the last activated policy, and the configuration which is now in effect, which is known as the Current policy.

##### Syntax

    crsctl status policyset [-file file_name]

##### Usage Notes

- You can specify this parameter to create a file that you can edit and then send back using `crsctl modify policyset` to add, delete, or update multiple policies. If you do not specify this optional parameter, then CRSCTL displays the Current configuration.

- Privileges necessary to run this command depend on the value of the `ACL` attribute of the policy set.

##### Example

This command returns output similar to the following:

    ACL=owner:'mjkeenan:rwx,pgrp:g900:rwx,other::r--'
    LAST_ACTIVATED_POLICY=DayTime
    SERVER_POOL_NAMES=Free pool1 pool2 pool3
    POLICY
    NAME=DayTime
    DESCRIPTION=Test policy
    SERVERPOOL
      NAME=pool1
      IMPORTANCE=0
      MAX_SIZE=2
      MIN_SIZE=2
      SERVER_CATEGORY=
      SERVER_NAMES=
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
    DESCRIPTION=Test policy
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
    DESCRIPTION=Test policy
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

#### crsctl check resource

Initiates the check action inside the application-specific agent of a particular resource.

Oracle Clusterware only provides output if something prevents the system from issuing the check request, such as a bad resource name.

##### Syntax

    crsctl check resource {resource_name [...] | -w "filter"} [-n node_name]
       [-k cardinality_id] [-d degree_id]

##### Parameters

Table E-67 crsctl check resource Command Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [...]` | Specify a particular resource. You can check multiple resources by entering a space-delimited list of resource names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-w "``filter``"`       | Specify a resource filter that Oracle Clusterware uses to limit the number of resources checked. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to check only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to check resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to check resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: "Filters" for more information |
| `-n ``node_name`        | Check the resource instance on a specific node. If you do not specify the `-n` parameter, then Oracle Clusterware checks the resource instances only on the local server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-k ``cardinality_id`   | Specify the resource cardinality ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-d ``degree_id`        | Specify the resource degree ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

##### Usage Notes

- You must have read and execute permissions on the specified resources to check them.

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources.

- If this command is successful, it only means that a check was issued; it does not mean the CHECK action was completed.

##### Example

To initiate the check action inside the application-specific agent of a particular resource:

    $ crsctl check resource appsvip

#### crsctl relocate resource

Relocates resources to another server in the cluster.

##### Syntax

    crsctl relocate resource {resource_name [-k cid] | {resource_name | -all}
       -s source_server | -w "filter"} [-n destination_server] [-env "env1=val1,env2=val2,..."]
       [-i] [-f]

##### Parameters

Table E-68 crsctl relocate resource Command Parameters

| Parameter                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resource_name`` [-k ``cid``]`                   | Specify the name of a resource you want to relocate.<br>Optionally, you can also specify the resource cardinality ID. If you specify this parameter, then Oracle Clusterware relocates the resource instance that have the cardinality you specify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `resource_name`` | -all -s ``source_server`      | Alternatively, you can specify one particular resource or all resources located on a particular server that you specify from which you want to relocate those resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-w "``filter``"`                                | Alternatively, you can specify a resource filter that Oracle Clusterware uses to limit the number of resources relocated. The filter must be enclosed in double quotation marks (`""`). Examples of resource filters include:<br>• `"TYPE == cluster_resource"`: This filter limits Oracle Clusterware to relocate only resources of `cluster_resource` type<br>• `"CHECK_INTERVAL > 10"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute<br>• `"(CHECK_INTERVAL > 10) AND (NAME co 2)"`: This filter limits Oracle Clusterware to relocate resources that have a value greater than 10 for the `CHECK_INTERVAL` resource attribute and the name of the resource contains the number `2`<br>See Also: "Filters" for more information |
| `-n ``destination_server`                        | Specify the name of the server to which you want relocate resources. If you do not specify a destination server, then Oracle Clusterware relocates the resources to the best server according to the attribute profile of each resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-env "``env1``=``val1``,``env2``=``val2``,..."` | You can optionally override one or more resource profile attribute values for this command. If you specify multiple environment name-value pairs, then you must separate each pair with a comma and enclose the entire list in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `–i`                                             | If you specify `-i`, then the command returns an error if processing this command requires waiting for Oracle Clusterware to unlock the resource or its dependents. Sometimes, Oracle Clusterware locks resources or other objects to prevent commands from interfering with each other.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `–f`                                             | Specify the `-f` parameter to force the relocating of the resource when it has other resources running that depend on it. Dependent resources are relocated or stopped when you use this parameter.<br>Note: When you are relocating resources that have cardinality greater than 1, you must use either `-k` or `-s` to narrow down which resource instances are to be relocated.                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- Any one of the three following options is required to specify which resources you want to relocate:

  - You can specify one particular resource to relocate.

  - Or you can specify one particular or all the resources to relocate from a particular source server.

  - Thirdly, you can specify a resource filter that Oracle Clusterware uses to match resources to relocate.

- If a resource has a degree ID greater than 1, then Oracle Clusterware relocates all instances of the resource.

- You must have read and execute permissions on the specified resources to relocate them.

- Do not use this command for any resources with names that begin with ora because these resources are Oracle resources.

##### Example

To relocate one particular resource from one server to another:

    # crsctl relocate resource myResource1 -s node1 -n node3

#### crsctl get resource use

Checks the current setting value of the `RESOURCE_USE_ENABLED` server configuration parameter.

##### Syntax

    crsctl get resource use

##### Usage Notes

The possible values are 1 or 0. If the value for this attribute is 1, which is the default, then the server can be used for resource placement. If the value is 0, then Oracle Clusterware disallows starting server pool resources on the server. The server remains in the Free server pool.

##### Example

This command returns output similar to the following:

    CRS-4966: Current resource use parameter value is 1

#### crsctl set resource use

Sets the value of the `RESOURCE_USE_ENABLED` server configuration parameter for the server on which you run this command.

##### Syntax

    crsctl set resource use [1 | 0]

##### Usage Notes

- The possible values are 1 or 0. If you set the value for this attribute to 1, which is the default, then the server can be used for resource placement. If you set the value to 0, then Oracle Clusterware disallows starting server pool resources on the server. The server remains in the Free server pool.

- You must run this command as `root` or a cluster administrator, or an administrator on Windows systems.

##### Example

To set the value of the `RESOURCE_USE_ENABLED` server configuration parameter:

    # crsctl set resource use 1

#### crsctl start rollingpatch

Transitions Oracle Clusterware and Oracle ASM into rolling patch mode.

**Note:**

`crsctl` `start` `rollingpatch` and `crsctl` `stop` `rollingpatch` should not be run directly except under the direction of Oracle Support. These commands are invoked as part of `rootcrs.pl` `-prepatch`/`-postpatch` which orchestrates patching on each node.

In this mode, the software tolerates nodes having different patch levels.

##### Syntax

    crsctl start rollingpatch

##### Usage Notes

- This command queries the Oracle Clusterware rolling patch state and Oracle ASM cluster state. If either one is not in rolling patch mode, then it will use the appropriate method to transition Oracle Clusterware or Oracle ASM to rolling patch mode.

- If Oracle Clusterware and Oracle ASM are both in rolling patch mode when you run this command, then this command does nothing.

- The rolling patch mode is not persistent. If all the nodes in a cluster are shut down and restarted, then the cluster transitions out of rolling patch mode when it is restarted. Similarly, if Oracle Clusterware is stopped and then restarted on all nodes in the cluster, then the rolling patch mode is lost.

- This command does not transition Oracle ASM to rolling patch mode if issued within an Oracle ASM Client Cluster.

#### crsctl stop rollingpatch

Transitions Oracle Clusterware and Oracle ASM out of rolling patch mode.

**Note:**

`crsctl` `start` `rollingpatch` and `crsctl` `stop` `rollingpatch` should not be run directly except under the direction of Oracle Support. These commands are invoked as part of `rootcrs.pl` `-prepatch`/`-postpatch` which orchestrates patching on each node.

After the software transitions out of rolling patch mode, it does not tolerate nodes having different patch levels.

##### Syntax

    crsctl stop rollingpatch

##### Usage Notes

- This command queries the Oracle Clusterware rolling patch state and Oracle ASM cluster state. If either one is in rolling patch mode, then it will use the appropriate method to transition Oracle Clusterware or Oracle ASM out of rolling patch mode.

- This command verifies that all the nodes in the cluster have a consistent patch level, and returns an error otherwise.

- If neither Oracle Clusterware or Oracle ASM are in rolling patch mode when you issue this command, then this command does nothing.

- This command does not transition Oracle ASM out of rolling patch mode if issued within an Oracle ASM Client Cluster.

#### crsctl start rollingupgrade

Transitions Oracle Clusterware and Oracle ASM into rolling upgrade mode.

**Note:**

This command should not be invoked directly except under the direction of Oracle Support. It is invoked by the `rootupgrade` scripts as part of the upgrade.

##### Syntax

    crsctl start rollingupgrade version

##### Usage Notes

- This command queries the Oracle Clusterware rolling upgrade state and Oracle ASM cluster state. If either one is not in rolling upgrade mode, then it will use the appropriate method to transition Oracle Clusterware or Oracle ASM to rolling upgrade mode.

- If Oracle Clusterware and Oracle ASM are both in rolling upgrade mode when you run this command, then this command does nothing.

- This command does not transition Oracle ASM to rolling upgrade mode if run within an Oracle ASM Client Cluster.

#### crsctl eval add server

Simulates the addition of a server without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval add server server_name [-file file_path] | [-attr "attr_name=attr_value[,...]"]
        [-admin [-l level [-x] [-a]] [-explain]

##### Parameters

Table E-69 crsctl eval add server Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:---------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`                                | The name of the server you want to add.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-file ``file_path`                          | Fully-qualified path to a file containing server attributes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-attr "``attr_name``=``attr_value``[,...]"` | Alternatively, you can specify the name of a server attribute you want to modify preceded by the `-attr` flag, followed by a value for the server attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "MAX_SIZE=30,IMPORTANCE=25"`                                                                                                                                                                                                                                                                                                                         |
| `-admin [-l ``level``] [-x] [-a]`            | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note: To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |
| `-explain`                                   | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

##### Example

This command returns output similar to the following:

    $ crsctl eval add server scott_node5_0

    Stage Group 1:
    ---------------------------------------------------------------------------
    Stage   Required   Action
    ---------------------------------------------------------------------------
    1       E  Looking for a suitable server pool for server 'scott_node5_0'.
            E  Scanning server pools with MIN_SIZE or more servers in
               descending order of IMPORTANCE.
            E  Considering server pools (IMPORTANCE): Free(0) for relocating
               servers.
            E  Relocating server 'scott_node5_0' to server pool 'Free'.
            Y  Server 'scott_node5_0' will be added to pools 'Free'.
    ---------------------------------------------------------------------------

**Related Topics**

- [Server Category Attributes](policy-based-cluster-and-capacity-management.md)

#### crsctl eval delete server

Predicts the effects of deleting a server without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval delete server server_name [-admin [-l level] [-x] [-a]] [-f] [-explain]

##### Parameters

Table E-70 crsctl eval delete server Command Parameters

| Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`                     | Specify the name of the server you want to evaluate before deleting.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-admin [-l ``level``] [-x] [-a]` | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note:To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |
| `-explain`                        | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

##### Examples

This command returns output similar to the following:

    $ crsctl eval delete server scott_node1_0 -explain

    Stage Group 1:
    ---------------------------------------------------------------------------
    Stage Number    Required              Action
    ---------------------------------------------------------------------------
    1      Y   Resource 'cs1' (1/1) will be in state 'OFFLINE'.
           E   Server 'scott_node1_0' is removed from server pool 'sp1'.
           E   Server pool 'sp1' is below the MIN_SIZE value of 2 with 1
               servers.
           E   Looking at other server pools to see whether MIN_SIZE value 2 of
               server pool 'sp1' can be met.
           E   Scanning server pools with more than MIN_SIZE servers in
               ascending order of IMPORTANCE.
           E   Considering server pools (IMPORTANCE): sp2(4) for suitable
               servers.
           E   Considering server pool 'sp2' because its MIN_SIZE is 1 and it
               has 1 servers above MIN_SIZE.
           E   Relocating server 'scott_node1_2' to server pool 'sp1'.
           Y   Server 'scott_node1_2' will be moved from pool 'sp2' to pool
               'sp1'.
           Y   Server 'scott_node1_0' will be removed from pools 'sp1'.
           Y   Resource 'cs2' (1/1) will be in state 'OFFLINE'.
    2      Y   Resource 'cs1' (1/1) will be in state 'ONLINE|INTERMEDIATE' on
               server 'scott_node1_2'.
    ---------------------------------------------------------------------------

**Related Topics**

- [How Server Pools Work](policy-based-cluster-and-capacity-management.md)

#### crsctl eval relocate server

Predicts the effects of relocating a server to a different server pool without making changes to the system.

This command might be useful for a cluster administrator.

##### Syntax

    crsctl eval relocate server server_name -to server_pool_name [-f]
       [-admin [-l level] [-x] [-a]]

##### Parameters

Table E-71 crsctl eval relocate server Parameters

| Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`                     | The name of the server you want to relocate. You can provide a space-delimited list of servers to evaluate relocating multiple servers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-to`                             | Specify the name of the server pool to which you want relocate the server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-f`                              | If you specify this parameter, then CRSCTL predicts the effects of forcibly relocating a server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-admin [-l ``level``] [-x] [-a]` | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note: To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |

##### Example

This command returns output similar to the following:

    $ crsctl eval relocate server scott-node4-0 -to sp2

    Stage Group 1:
    -------------------------------------------------------------------------------
    Stage  Required Action
    -------------------------------------------------------------------------------
        1      Y Server 'scott-node4-0' will be moved from pool 'sp1' to pool 'sp2'.
        2      Y Resource 'cs2' (2/1) will be in state 'ONLINE|INTERMEDIATE' on
                 server 'scott-node4-0'.
               Y Resource 'cs1' (2/1) will be in state 'ONLINE|INTERMEDIATE' on
                 server 'scott-node4-0'.
    --------------------------------------------------------------------------------

#### crsctl modify server

Modifies the configuration of a particular server.

##### Syntax

    crsctl modify server server_name -attr "attr_name=attr_value[,...]"

##### Parameters

Table E-72 crsctl modify server Command Parameters

| Parameter                           | Description                                                                                                                                                                                                                                                                                                                                                           |
|:------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`                       | Specify the name of the server you want to modify.                                                                                                                                                                                                                                                                                                                    |
| `-attr "``attr_name``=``attr_value` | Specify the name of a server attribute you want to modify preceded by the `-attr` flag, followed by a value for the server attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "CHECK_INTERVAL=30,START_TIMEOUT=25"` |

##### Usage Notes

If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

    "START_DEPENDENCIES='hard(res1,res2,res3)'"

##### Example

To modify the configuration of a specific server, enter a command similar to the following:

    $ crsctl modify server email_server_2 -attr  "WORKLOAD_VALUE=1"

#### crsctl relocate server

Relocates a server to a different server pool.

##### Syntax

    crsctl relocate server server_name [...] -c server_pool_name [-i] [-f]

##### Parameters

Table E-73 crsctl relocate server Command Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`` [...]`   | Specify the name of the server you want to relocate. You can provide a space-delimited list of servers to relocate multiple servers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-c ``server_pool_name` | Specify the name of the server pool to which you want relocate the servers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `–i`                    | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `–f`                    | If you specify the `-f` parameter, then Oracle Clusterware stops resources running on the servers in another server pool and relocates that server into the server pool you specified.<br>If you do not specify the `-f` parameter, then Oracle Clusterware checks for resources that must be stopped on the servers that are being relocated. If it finds any, then Oracle Clusterware rejects the `crsctl relocate server` command.<br>Note: If the number of servers in the server pool is not above the value of the `MIN_SIZE` server pool attribute, then the force parameter will have no affect because CRSCTL will not violate the configuration. |

##### Usage Notes

The `server_name` and `-c ``server_pool_name` parameters are required.

##### Example

To move the `node6` and `node7` servers into the `sp1` server pool without disrupting any active resources on those nodes, use the following command:

    $ crsctl relocate server node6 node7 -c sp1

#### crsctl status server

Obtains the status and configuration information of one or more particular servers.

##### Syntax

    crsctl status server {server_name [...] | -w "filter"} [-g | -p | -v | -f] |
        [-category category_name | -w "filter"]

##### Parameters

Table E-74 crsctl status server Command Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_name`` [...]`       | Specify one or more space-delimited server names.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-w "``filter``"`           | Alternatively, specify a filter to determine which servers are displayed. The filter must be enclosed in double quotation marks (`""`). Values that contain parentheses or spaces must be enclosed in single quotation marks (`''`). For example, `"STATE = ONLINE"` limits the display to servers that are online.<br>See Also: "Filters" for more information                                                                                                            |
| `-g | -p | -v | -f`         | You can specify one of the following parameters when Oracle Clusterware checks the status of specific servers:<br>• `-g`: Use this parameter to check if the specified servers are registered<br>• `-p`: Use this parameter to display static configuration of the specified servers<br>• `-v`: Use this parameter to display the run-time configuration of the specified servers<br>• `-f`: Use this parameter to display the full configuration of the specified servers |
| `-category ``category_name` | Optionally, you can specify a particular category of servers for which to obtain status.                                                                                                                                                                                                                                                                                                                                                                                   |
| `-w "``filter``"`           | Alternatively, specify a filter to determine which categories are displayed. The filter must be enclosed in double quotation marks (`""`). Values that contain parentheses or spaces must be enclosed in single quotation marks (`''`). For example, `"STATE = ONLINE"` limits the display to servers that are online.<br>See Also: "Filters" for more information                                                                                                         |

##### Examples

Example E-7 Example 1

This command returns output similar to the following:

    NAME=node1
    STATE=ONLINE

    NAME=node2
    STATE=ONLINE

Example E-8 Example 2

The full configuration of a specific server is similar to the following:

    NAME=node2
    MEMORY_SIZE=72626
    CPU_COUNT=12
    CPU_CLOCK_RATE=1711
    CPU_HYPERTHREADING=0
    CPU_EQUIVALENCY=1000
    DEPLOYMENT=other
    CONFIGURED_CSS_ROLE=hub
    RESOURCE_USE_ENABLED=1
    SERVER_LABEL=
    PHYSICAL_HOSTNAME=
    STATE=ONLINE
    ACTIVE_POOLS=ora.pool1
    STATE_DETAILS=
    ACTIVE_CSS_ROLE=hub

#### crsctl get server css_critical

Obtains the current configured value for the `CSS_CRITICAL` server attribute

##### Syntax

    crsctl get server css_critical

##### Usage Notes

This command has no parameters.

#### crsctl set server css_critical

Sets the configuration value for the CSS_CRITICAL server attribute.

##### Syntax

    crsctl set server css_critical {yes | no}

##### Usage Notes

Choose `yes` to set the server as CSS_CRITICAL.

#### crsctl get server label

Checks the current setting value of the `SERVER_LABEL` server attribute.

##### Syntax

    crsctl get server label

##### Example

This command returns output similar to the following:

    CRS-4972: Current SERVER_LABEL parameter value is hubserver

#### crsctl set server label

Sets the configuration value of the `SERVER_LABEL` server configuration attribute for the server on which you run this command.

##### Syntax

    crsctl set server label value

##### Usage Notes

- Specify a value for the server. This value can reflect a physical location, such as `building_A`, or some other identifying characteristic of the server, such as `hubserver`.

- You must restart the Oracle Clusterware technology stack on the node before any changes you make take effect.

#### crsctl add serverpool

Adds a server pool that is for hosting non-database resources (such as application servers) to Oracle Clusterware.

##### Syntax

    crsctl add serverpool server_pool_name {-file file_path |
    -attr "attr_name=attr_value[,...]"} [-i] [-f]

##### Parameters

Table E-75 crsctl add serverpool Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`                           | A short, descriptive name for the server pool. A server pool name has a 254 character limit and can contain any platform-supported characters except the exclamation point (!), the tilde (~), and spaces. A server pool name cannot begin with a period nor with ora.                                                                                                                                                                                                                                                                                                                            |
| `-file ``file_path`                          | Fully-qualified path to an attribute file to define the server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-attr "``attr_name``=``attr_value``[,...]"` | Alternatively, specify the name of a server pool attribute for the server pool you are adding preceded by the `-attr` flag, followed by a value for the server pool attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "MAX_SIZE=30,IMPORTANCE=3"`<br>The available attribute names include:<br>• `IMPORTANCE`<br>• `MIN_SIZE`<br>• `MAX_SIZE`<br>• `SERVER_NAMES`<br>• `PARENT_POOLS`<br>• `EXCLUSIVE_POOLS`<br>• `ACL`<br>• `SERVER_CATEGORY` |
| `-i`                                         | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-f`                                         | If you specify the `-f` parameter, then Oracle Clusterware stops resources running on a server in another server pool and relocates that server into the server pool you are adding. If you do not specify the `-f` parameter, then Oracle Clusterware checks whether the creation of the server pool results in stopping any resources on a server in another server pool that is going to give up a server to the server pool you are adding. If so, then Oracle Clusterware rejects the `crsctl add serverpool` command.                                                                       |

##### Usage Notes

- The `server_pool_name` parameter is required.

- If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`).

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools.

- Running this command may result in Oracle Clusterware relocating other servers between server pools to comply with the new configuration.

- You must run this command as `root` or a cluster administrator.

- Use the `crsctl add serverpool` command to create server pools that host non-database resources. To create server pools that host Oracle databases, use the SRVCTL command utility.

  **See Also:**

  [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for information about using the SRVCTL command utility to create server pools

##### Examples

To add a server pool named `testsp` with a maximum size of 5 servers, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl add serverpool testsp -attr "MAX_SIZE=5"

Create the `sp1_attr` file with the attribute values for the `sp1` server pool, each on its own line, as shown in the following example:

    IMPORTANCE=1
    MIN_SIZE=1
    MAX_SIZE=2
    SERVER_NAMES=node3 node4 node5
    PARENT_POOLS=Generic
    EXCLUSIVE_POOLS=testsp
    ACL=owner:oracle:rwx,pgrp:oinstall:rwx,other::r--

Use the following command to create the `sp1` server pool using the `sp1_attr` file as input:

    $ crsctl add serverpool sp1 -file /tmp/sp1_attr

#### crsctl delete serverpool

Removes a server pool from the Oracle Clusterware configuration.

##### Syntax

    crsctl delete serverpool server_pool_name [server_pool_name [...]] [-i]

**See Also:**

"[How Server Pools Work](policy-based-cluster-and-capacity-management.md)" for more information about server pools and server pool attributes

##### Usage Notes

- The `server_pool_name` parameter is required

  . Use spaces to delimit multiple server pool names.

- If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools.

- While you can use this command in either environment, it is only useful in the Oracle RAC environment.

##### Example

To delete a server pool, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl delete serverpool sp1

#### crsctl eval add serverpool

Predicts the effects of adding a server pool without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval add serverpool server_pool_name [-file file_path | -attr "attr_name=attr_value[,...]"]
        [-admin [-l level [-x] [-a]] [-explain] [-f]

##### Parameters

Table E-76 crsctl eval add serverpool Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`                           | Specify a short, descriptive name for the server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-file ``file_path`                          | Specify a fully-qualified path to an attribute file to define the server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-attr "``attr_name``=``attr_value``[,...]"` | Alternatively, specify the name of a server pool attribute for the server pool you are adding preceded by the `-attr` flag, followed by a value for the server pool attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "MAX_SIZE=30,IMPORTANCE=3"`<br>Server pool attributes include:<br>• `IMPORTANCE`<br>• `MIN_SIZE`<br>• `MAX_SIZE`<br>• `SERVER_NAMES`<br>• `PARENT_POOLS`<br>• `EXCLUSIVE_POOLS`<br>• `ACL`                                                                                                                                        |
| `-admin [-l ``level``] [-x] [-a]`            | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note:To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |
| `-explain`                                   | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-f`                                         | If you specify this parameter, then CRSCTL predicts the effects of forcibly adding a server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

##### Example

The following example evaluates adding a server pool named `sp1`:

    $ crsctl eval add serverpool sp1 -explain

    Stage Group 1:
    ----------------------------------------------------------------------------
    Stage Required Action
    ----------------------------------------------------------------------------

    1       E   Starting to look for server pools that will donate servers to be
                reallocated to the new pool 'sp1'.
            E   Scanning server pools with more than MIN_SIZE servers in
                ascending order of IMPORTANCE.
            E   Considering server pools (IMPORTANCE): Free(0) for suitable
                servers.
            E   Considering server pool 'Free' because its MIN_SIZE is 0 and it
                has 4 servers above MIN_SIZE.
            E   Relocating server 'scott_node1_0' to server pool 'sp1'.
            E   Scanning server pools with more than MIN_SIZE servers in
                ascending order of IMPORTANCE.
            E   Considering server pools (IMPORTANCE): Free(0) for suitable
                servers.
            E   Considering server pool 'Free' because its MIN_SIZE is 0 and it
                has 3 servers above MIN_SIZE.
            E   Relocating server 'scott_node1_1' to server pool 'sp1'.
            E   Scanning server pools with more than MIN_SIZE servers in
                ascending order of IMPORTANCE.
            E   Considering server pools (IMPORTANCE): Free(0) for suitable
                servers.
            E   Considering server pool 'Free' because its MIN_SIZE is 0 and it
                has 2 servers above MIN_SIZE.
            E   Relocating server 'scott_node1_2' to server pool 'sp1'.
            E   Scanning server pools with more than MIN_SIZE servers in
                ascending order of IMPORTANCE.
            E   Considering server pools (IMPORTANCE): Free(0) for suitable
                servers.
            E   Considering server pool 'Free' because its MIN_SIZE is 0 and it
                has 1 servers above MIN_SIZE.
            E   Relocating server 'scott_node1_3' to server pool 'sp1'.
            E   Scanning server pools with MIN_SIZE or fewer servers in
                ascending order of IMPORTANCE.
            Y   Server 'scott_node1_2' will be moved from pool 'Free' to pool
                'sp1'.
            Y   Server 'scott_node1_0' will be moved from pool 'Free' to pool
                'sp1'.
            Y   Server 'scott_node1_1' will be moved from pool 'Free' to pool
                'sp1'.
            Y   Server 'scott_node1_3' will be moved from pool 'Free' to pool
                'sp1'.

    -------------------------------------------------------------------------------

**Related Topics**

- [How Server Pools Work](policy-based-cluster-and-capacity-management.md)

#### crsctl eval delete serverpool

Simulates the deletion of a server pool without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval delete serverpool server_pool_name [-admin [-l level] [-x] [-a]] [-explain]

##### Parameters

Table E-77 crsctl eval delete serverpool Paramaters

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`            | The name of the server pool you want to delete.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-admin [-l level] [-x] [-a]` | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note:To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |
| `-explain`                    | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

##### Examples

Consider the following server pool configuration:

    NAME=Free
    ACTIVE_SERVERS=

    NAME=Generic
    ACTIVE_SERVERS=

    NAME=sp1
    ACTIVE_SERVERS=scott-node2-0 scott-node2-3

    NAME=sp2
    ACTIVE_SERVERS=scott-node2-1

The following command evaluates the effect of deleting server pool `sp1`:

    $ crsctl eval delete sp sp1

    Stage Group 1:
    --------------------------------------------------------------------------------
    Stage Required Action
    --------------------------------------------------------------------------------

        1 Y Server 'scott-node2-0' will be moved from pool 'sp1' to pool
                    'sp2'.
               Y Server 'scott-node2-3' will be moved from pool 'sp1' to pool
                    'sp2'.

    --------------------------------------------------------------------------------

Adding the `-explain` parameter to the preceding command returns reasoned command evaluation similar to the following:

    $ crsctl eval delete sp sp1 -explain

    Stage Group 1:
    --------------------------------------------------------------------------------
    Stage Required Action
    --------------------------------------------------------------------------------

        1 E Starting to look for server pools to reallocate servers from
                    pool 'sp1'.
               E Looking for a suitable server pool for server
                    'scott-node2-0'.
               E Scanning server pools with fewer than MIN_SIZE servers in
                    descending order of IMPORTANCE.
               E Considering server pools (IMPORTANCE): sp2(1) for relocating
                    servers.
               E Relocating server 'scott-node2-0' to server pool 'sp2'.
               E Looking for a suitable server pool for server
                    'scott-node2-3'.
               E Scanning server pools with fewer than MIN_SIZE servers in
                    descending order of IMPORTANCE.
               E Considering server pools (IMPORTANCE): sp2(1) for relocating
                    servers.
               E Relocating server 'scott-node2-3' to server pool 'sp2'.
        2 Y Server 'scott-node2-0' will be moved from pool 'sp1' to pool
                    'sp2'.
               Y Server 'scott-node2-3' will be moved from pool 'sp1' to pool
                    'sp2'.

    --------------------------------------------------------------------------------

**Related Topics**

- [How Server Pools Work](policy-based-cluster-and-capacity-management.md)

#### crsctl eval modify serverpool

Predicts the effects of modifying a server pool without making changes to the system.

This command may be useful to cluster administrators.

##### Syntax

    crsctl eval modify serverpool server_pool_name {-file file_path
       | -attr "attr_name=attr_value[,...]]"}
       [-f] [-admin [-l level [-x] [-a]] [-explain]

##### Parameters

Table E-78 crsctl eval modify serverpool Parameters

| Parameter                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`                            | The name of the server pool you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-file ``file_path`                           | Fully-qualified path to an attribute file to define the server pool you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-attr "``attr_name``=``attr_value``[,...]]"` | Alternatively, specify the name of a server pool attribute for the server pool you are adding preceded by the `-attr` flag, followed by a value for the server pool attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "MAX_SIZE=30,IMPORTANCE=3"`<br>Server pool attributes include:<br>• `IMPORTANCE`<br>• `MIN_SIZE`<br>• `MAX_SIZE`<br>• `SERVER_NAMES`<br>• `PARENT_POOLS`<br>• `EXCLUSIVE_POOLS`<br>• `ACL`                                                                                                                                         |
| `-f`                                          | If you specify this parameter, then CRSCTL predicts the effects of forcibly modifying a server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-admin [-l ``level``] [-x] [-a]`             | If you specify this parameter, then CRSCTL displays output for the cluster administrator.<br>If you specify the `-l` parameter, then you can choose one of the following three output levels:<br>• `serverpools`: Restricts the output to servers running in a server pool<br>• `resources`: Restricts the output to resources running on servers in a server pool<br>• `all`: Displays all available output<br>If you specify the `-x` parameter, then CRSCTL displays the differences.<br>If you specify the `-a` parameter, then CRSCTL displays all resources.<br>Note: To specify either the `-l`, `-x`, or `-a` parameters, or any combination of the three, you must specify the `-admin` parameter. |
| `-explain`                                    | Specify this parameter to display reasoned command evaluation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

##### Usage Notes

- The `server_pool_name` parameter is required

- If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

      "START_DEPENDENCIES='hard(res1,res2,res3)'"

- Running this command may result in Oracle Clusterware relocating other servers between server pools to comply with the new configuration

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools

- While you can use this command in either environment, it is only useful in the Oracle RAC environment

##### Example

For the following examples, consider two server pools, `sp1` and `sp2`. Server pool `sp1` is configured, as follows:

    ACTIVE_SERVERS=mjkeenan-node2-0 mjkeenan-node2-3

Server pool `sp2` is configured, as follows:

    ACTIVE_SERVERS=mjkeenan-node2-1

Currently, `sp1` has more importance than `sp2`. The following command evaluates what would happen if you modified the `IMPORTANCE` and `MAX_SIZE` attributes for `sp2`:

    $ crsctl eval modify serverpool sp2 -attr "MAX_SIZE=3,IMPORTANCE=5"

    Stage Group 1:
    --------------------------------------------------------------------------------
    Stage Required Action
    --------------------------------------------------------------------------------

        1 Y Server 'scott-node2-0' will be moved from pool 'sp1' to pool
                    'sp2'.
               Y Server 'scott-node2-3' will be moved from pool 'sp1' to pool
                    'sp2'.

    --------------------------------------------------------------------------------

Adding the `-explain` parameter to the preceding command returns reasoned command evaluation similar to the following:

    $ crsctl eval modify serverpool sp2 -attr "MAX_SIZE=3,IMPORTANCE=5" -explain

    Stage Group 1:
    --------------------------------------------------------------------------------
    Stage Required Action
    --------------------------------------------------------------------------------

        1 E Starting to look at server pools due to a configuration change
                    in the pool 'sp2'.
               E Looking at other server pools to see whether MIN_SIZE value 3 of
                    server pool 'sp2' can be met.
               E Scanning server pools with MIN_SIZE or fewer servers in
                    ascending order of IMPORTANCE.
               E Considering server pools (IMPORTANCE): sp1(3) for suitable
                    servers.
               E Considering server pool 'sp1' because its MIN_SIZE is 2 and it
                    has 0 servers above MIN_SIZE.
               E Relocating server 'scott-node2-0' to server pool 'sp2'.
               E Scanning server pools with MIN_SIZE or fewer servers in
                    ascending order of IMPORTANCE.
               E Considering server pools (IMPORTANCE): sp1(3) for suitable
                    servers.

               E Considering server pool 'sp1' because its MIN_SIZE is 2 and it
                    has 0 servers above MIN_SIZE.
               E Relocating server 'scott-node2-3' to server pool 'sp2'.
               Y Server 'scott-node2-0' will be moved from pool 'sp1' to pool
                    'sp2'.
               Y Server 'scott-node2-3' will be moved from pool 'sp1' to pool
                    'sp2'.

    --------------------------------------------------------------------------------

**Related Topics**

- [How Server Pools Work](policy-based-cluster-and-capacity-management.md)

#### crsctl getperm serverpool

Retrieves permissions for a particular server pool.

##### Syntax

    crsctl getperm serverpool server_pool_name [-u user_name | -g group_name]

**See Also:**

"[How Server Pools Work](policy-based-cluster-and-capacity-management.md)" for more information about server pools and server pool attributes

##### Parameters

Table E-79 crsctl getperm serverpool Command Parameters

| Parameter          | Description                                                                                |
|:-------------------|:-------------------------------------------------------------------------------------------|
| `server_pool_name` | Specify the name of the server pool for which you want to retrieve permissions.            |
| `-u ``user_name`   | If you specify `-u`, then Oracle Clusterware retrieves permissions for a particular user.  |
| `-g ``group_name`  | If you specify `-g`, then Oracle Clusterware retrieves permissions for a particular group. |

##### Usage Notes

- The `server_pool_name` parameter is required

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools

- While you can use this command in either environment, it is only useful in the Oracle RAC environment

##### Example

This command returns output similar to the following:

    $ crsctl getperm serverpool sp1

    NAME: sp1
    owner:root:rwx,pgrp:root:r-x,other::r--

#### crsctl modify serverpool

Modifies an existing server pool.

##### Syntax

    crsctl modify serverpool server_pool_name -attr "attr_name=attr_value[, ...]"
       [-policy policyName | -all_policies] [-i] [-f]

##### Parameters

Table E-80 crsctl modify serverpool Command Parameters

| Parameter                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`                            | Specify the name of the server pool you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-attr "``attr_name``=``attr_value``[, ...]"` | Specify the name of a server pool attribute that you want to modify preceded by the `-attr` flag, followed by a value for the server pool attribute.<br>Note: The `attr_name``=``attr_value` name-value pairs must be enclosed in double quotation marks (`""`). Multiple name-value pairs must be separated by commas. For example:<br>`-attr "MAX_SIZE=30,IMPORTANCE=3"`<br>The available attribute names include:<br>• `IMPORTANCE`<br>• `MIN_SIZE`<br>• `MAX_SIZE`<br>• `SERVER_NAMES`<br>• `PARENT_POOLS`<br>• `EXCLUSIVE_POOLS`<br>• `ACL`<br>• `SERVER_CATEGORY` |
| `-policy ``policyName`` | -all_policies`      | Specify a particular policy or all policies for which you want to modify the server pool definition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `–i`                                          | If you specify `-i`, then the command fails if Oracle Clusterware cannot process the request immediately.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `–f`                                          | If you specify the `-f` parameter, then Oracle Clusterware stops resources running on a server in another server pool and relocates that server into the server pool you are modifying.<br>If you do not specify the `-f` parameter, then Oracle Clusterware checks whether the creation of the server pool results in stopping any resources on a server in another server pool that is going to give up a server to the server pool you are modifying. If so, then Oracle Clusterware rejects the `crsctl modify serverpool` command.                                 |

**See Also:**

"[How Server Pools Work](policy-based-cluster-and-capacity-management.md)" for more information about server pools and server pool attributes

##### Usage Notes

- The `server_pool_name` parameter is required.

- If an attribute value for an attribute name-value pair contains commas, then the value must be enclosed in single quotation marks (`''`). For example:

      "START_DEPENDENCIES='hard(res1,res2,res3)'"

- Running this command may result in Oracle Clusterware relocating other servers between server pools to comply with the new configuration.

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools.

- While you can use this command in either environment, it is only useful in the Oracle RAC environment.

##### Example

To modify an existing server pool, run the following command as `root` or the Oracle Clusterware installation owner:

    # crsctl modify serverpool sp1 -attr "MAX_SIZE=7"

#### crsctl setperm serverpool

Sets permissions for a particular server pool.

##### Syntax

    crsctl setperm serverpool server_pool_name {-u acl_string | -x acl_string |
       -o user_name | -g group_name}

##### Parameters

Table E-81 crsctl setperm serverpool Command Parameters

| Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`    | Specify the name of the server pool for which you want to set permissions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `{-u | -x | -o | -g}` | You can specify only one of the following parameters for a server pool:<br>• `-u ``acl_string`: You can update the access control list (ACL) for a server pool<br>• `-x ``acl_string`: You can delete the ACL for a server pool<br>• `-o ``user_name`: You can change the owner of a server pool by entering a user name<br>• `-g ``group_name`: You can change the primary group of a server pool by entering a group name<br>Specify a user, group, or other ACL string, as follows:<br>`user:user_name[:readPermwritePermexecPerm] |`<br>`group:group_name[:readPermwritePermexecPerm] |`<br>`other[::readPermwritePermexecPerm]`<br>• `user`: User ACL<br>• `group`: Group ACL<br>• `other`: Other ACL<br>• `readPerm`: Read permission for the server pool; the letter `r` grants a user, group, or other read permission, the minus sign (`-`) denies read permission<br>• `writePerm`: Write permission for the server pool; the letter `w` grants a user, group, or other write permission, the minus sign (`-`) denies write permission<br>• `execPerm`: Execute permission for the server pool; the letter `x` grants a user, group, or other execute permission, the minus sign (`-`) denies execute permission |

##### Usage Notes

- The `server_pool_name` parameter is required

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools

- While you can use this command in either environment, it is only useful in the Oracle RAC environment

##### Example

To grant read, write, and execute permissions on a server pool for user Jane Doe:

    $ crsctl setperm serverpool sp3 -u user:jane.doe:rwx

#### crsctl status serverpool

Retrieves the status and configuration information of one or more particular server pools.

##### Syntax

    crsctl status serverpool [server_pool_name [...] | -w "filter"] [-p | -v | -f]

    crsctl status serverpool {[server_pool_name [...]} -g

##### Parameters

Table E-82 crsctl status serverpool Command Parameters

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                             |
|:------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `server_pool_name`` [...] —g` | Specify one or more space-delimited server pool names to identify specific server pools.<br>`-g`: Use this parameter to check if the specified server pools are registered<br>Note: You cannot use the `-g` parameter with any other parameters after you specify the server pool names.                                                                |
| `-w "``filter``"`             | Alternative to specifying a server pool by name, you can use this parameter to specify a filter, such as `MIN_SIZE > 3`, surrounded by double quotation marks (`""`). Use this parameter to identify server pools by a particular characteristic.<br>See Also: "Filters" for more information                                                           |
| `-p | -v | -f`                | You can optionally specify one of the following parameters:<br>• `-p`: Use this parameter to display static configuration of the specified server pools<br>• `-v`: Use this parameter to display the run-time configuration of the specified server pools<br>• `-f`: Use this parameter to display the full configuration of the specified server pools |

##### Usage Notes

- The `server_pool_name` parameter or a filter is required

- Do not use this command for any server pools with names that begin with ora because these server pools are Oracle server pools

- While you can use this command in either environment, it is only useful in the Oracle RAC environment

##### Examples

Example E-9 Example 1

To display the full configuration of the server pool `sp1`:

    $ crsctl status serverpool sp1 -f

    NAME=spl
    IMPORTANCE=1
    MIN_SIZE=0
    MAX_SIZE=-1
    SERVER_NAMES=node3 node4 node5
    PARENT_POOLS=Generic
    EXCLUSIVE_POOLS=
    ACL=owner:oracle:rwx,pgrp:oinstall:rwx,other::r--
    SERVER_CATEGORY=ora.hub.category
    ACTIVE_SERVERS=node3 node4

Example E-10 Example 2

To display all the server pools and the servers associated with them, use the following command:

    $ crsctl status serverpool

    NAME=Free
    ACTIVE_SERVERS=

    NAME=Generic
    ACTIVE_SERVERS=node1 node2

    NAME=ora.orcl
    ACTIVE_SERVERS=node1 node2

    NAME=sp1
    ACTIVE_SERVERS=node3 node4

Example E-11 Example 3

To find a server pool that meets certain criteria, use the following command:

    $ crsctl status serverpool -w "MAX_SIZE > 1"

    NAME=sp2
    ACTIVE_SERVERS=node3 node4

#### crsctl query socket udp

Verifies that a daemon can listen on a specified address and port.

##### Syntax

    crsctl query socket udp [-address address] [-port port]

##### Parameters

Table E-83 crsctl query socket udp Command Parameters

| Parameter            | Description                                                                                                                                       |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `-address ``address` | Specify the IP address on which the socket is to be created. If you do not specify an address, then CRSCTL assumes the local host as the default. |
| `-port ``port`       | Specify the port on which the socket is to be created. If you do not specify a port, then CRSCTL assumes 53 as the default.                       |

##### Usage Notes

You must run this command as `root` to verify port numbers less than 1024.

##### Examples

The command returns output similar to the following:

    $ crsctl query socket udp

    CRS-10030: could not verify if port 53 on local node is in use

    # crsctl query socket udp

    CRS-10026: successfully created socket on port 53 on local node

The first of the preceding two commands was not run as `root`, and in both commands no port was specified, so CRSCTL assumed the default, 53, which is less than 1024. This condition necessitates running the command as `root`.

    $ crsctl query socket udp -port 1023

    CRS-10030: could not verify if port 1023 on local node is in use

    # crsctl query socket udp -port 1023

    CRS-10026: successfully created socket on port 1023 on local node

Similar to the first two examples, the first of the preceding two commands was not run as `root`, and, although a port number was specified, it is still less than 1024, which requires `root` privileges to run the command.

In this last example, a port number greater than 1024 is specified, so there is no need to run the command as `root`:

    $ crsctl query socket udp -port 1028

    CRS-10026: successfully created socket on port 1028 on local node

#### crsctl start testdns

Starts a test DNS server that will listen on a specified IP address and port.

The test DNS server does not respond to incoming packets but does display the packets it receives. Typically, use this command to check if domain forwarding is set up correctly for the GNS domain.

##### Syntax

    crsctl start testdns [-address address [-port port]] [-once] [-v]

##### Parameters

Table E-84 crsctl start testdns Command Parameters

| Parameter            | Description                                                                                                |
|:---------------------|:-----------------------------------------------------------------------------------------------------------|
| `-address ``address` | Specify a server address in the form `IP_address``/``netmask``[/``interface_name``]`.                      |
| `-port ``port`       | The port on which the server listens. If you do not specify a port, then it defaults to port 53.           |
| `–once`              | Specify this parameter to indicate that the DNS server should exit after it receives one DNS query packet. |
| `–v`                 | Verbose output.                                                                                            |

##### Example

To start a test DNS server on the local server, run the command similar to the following:

    $ crsctl start testdns -address 192.168.29.218 -port 63 -v

#### crsctl status testdns

Queries the test DNS server running on a specified address and local host name.

##### Syntax

    crsctl status testdns [-server DNS_server_address] [-port port] [-v]

##### Parameters

Table E-85 crsctl status testdns Command Parameters

| Parameter                      | Description                                                                                                                      |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `-server ``DNS_server_address` | Optionally, you can specify the DNS server address for which you want to check the status.                                       |
| `-port ``port`                 | Optionally, you can specify the port on which the DNS server listens. If you do not specify a port, then it defaults to port 53. |
| `–v`                           | Verbose output.                                                                                                                  |

##### Example

This command returns output similar to the following:

    CRS-10024: DNS server returned 192.168.28.74 for name
    stmjk07-vip.stmjk0462.foo.com

#### crsctl stop testdns

Stops a test DNS server.

##### Syntax

    crsctl stop testdns [-address address] [-port port] [-v]

##### Parameters

Table E-86 crsctl stop testdns Command Parameters

| Parameter            | Description                                                                                                                                           |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-address ``address` | Optionally, you can specify the server address for which you started the test DNS server in the form `IP_address``/``netmask``[/``interface_name``]`. |
| `-port ``port`       | Optionally, you can specify the port on which the DNS server listens. If you do not specify a port, then it defaults to port 53.                      |
| `–v`                 | Verbose output.                                                                                                                                       |

##### Example

This command returns output similar to the following:

    CRS-10032: successfully stopped the DNS listening daemon running on port 53 on
    local node

#### crsctl replace votedisk

Moves or replaces the existing voting files.

This command creates voting files in the specified locations, either in Oracle ASM or some other storage option. Oracle Clusterware copies existing voting file information into the new locations and removes the voting files from the former locations.

##### Syntax

    crsctl replace votedisk [+asm_disk_group | path_to_voting_disk [...]]

##### Parameters

Table E-87 crsctl replace votedisk Command Parameters

| Parameter                     | Description                                                                                                                    |
|:------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `+``asm_disk_group`           | Specify the Oracle ASM disk group (preceded by a plus sign (`+`))where you want to locate the voting file.                     |
| `path_to_voting_disk`` [...]` | Alternatively, you can specify a space-delimited list of voting file paths for voting files that reside outside of Oracle ASM. |

##### Usage Notes

- You must be `root`, the Oracle Clusterware installation owner, or a member of the Administrators group to run this command.

- Specify to replace a voting file in either an Oracle ASM disk group or in some other storage device.

- You can run this command on any node in the cluster.

##### Examples

Example E-12 Example 1

To replace a voting file that is located within Oracle ASM:

    # crsctl replace votedisk +diskgroup1

Example E-13 Example 2

To replace a voting file that is located on a shared file system:

    # crsctl replace votedisk /mnt/nfs/disk1 /mnt/nfs/disk2

#### crsctl add wallet

Creates and adds users to a wallet.

##### Syntax

    crsctl add wallet -type wallet_type [-name name] [-user user_name -passwd]

##### Parameters

Table E-88 crsctl add wallet Command Parameters

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-type ``wallet_type`         | Speicfy the type of wallet you want to create, such as APPQOSADMIN, APPQOSUSER, APPQOSDB, MGMTDB, OSUSER, or CVUDB.<br>• OSUSER: This wallet type stores a low-privileged Windows user's user name and password that the agent uses when you create a Windows service on a policy-managed database or in general to update the Windows service's password.<br>• CVUDB: This wallet type stores a database user name and password that the health check component of CVU uses to connect to the database and perform database checks. |
| `-name ``name`                | You must specify a name for the wallet to create APPQOSDB and CVUDB wallets.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-user ``user_name`` -passwd` | Specify the user name you want to add to the wallet and provide the password through standard input. The user name is required to create an OSUSER wallet.                                                                                                                                                                                                                                                                                                                                                                           |

##### Usage Notes

If you are using a policy-managed database, then you must have a wallet. Otherwise, wallets are optional.

##### Example

To add a wallet:

    $ crsctl add wallet -type OSUSER -user lp_oracle_home_user -passwd

In the preceding example, `lp_oracle_home_user` is a low-privileged Oracle home user who owns the home where the policy-managed database was created.

#### crsctl delete wallet

Removes wallets or users from a wallet.

##### Syntax

    crsctl delete wallet -type wallet_type [-name name] [-user user_name]

##### Parameters

Table E-89 crsctl delete wallet Command Parameters

| Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-type ``wallet_type` | Type of wallet you want to remove, such as APPQOSADMIN, APPQOSUSER, APPQOSDB, MGMTDB, OSUSER, or CVUDB.<br>• OSUSER: This wallet type stores a low-privileged Windows user's user name and password that the agent uses when you create a Windows service on a policy-managed database or in general to update the Windows service's password.<br>• CVUDB: This wallet type stores a database user name and password that the health check component of CVU uses to connect to the database and perform database checks. |
| `-name ``name`        | You must specify the name of the wallet to remove an APPQOSDB wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-user ``user_name`   | You must specify a user name to remove a user from an OSUSER wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

##### Example

To delete a user from the OSUSER wallet:

    $ crsctl delete wallet -type OSUSER -user lp_oracle_home_user

In the preceding example, `lp_oracle_home_user` is a low-privileged Oracle home user who owns the home where the policy-managed database was created. Additionally, the command does not delete the wallet if it contains other users.

#### crsctl modify wallet

Modifies the password for a specific user in a specific wallet.

##### Syntax

    crsctl modify wallet -type wallet_type [-name name] [-user user_name -passwd]

##### Parameters

Table E-90 crsctl modify wallet Command Parameters

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-type ``wallet_type`         | Specify the type of wallet you want to modify, such as APPQOSADMIN, APPQOSUSER, APPQOSDB, MGMTDB, OSUSER, or CVUDB.<br>• OSUSER: This wallet type stores a low-privileged Windows user's user name and password that the agent uses when you create a Windows service on a policy-managed database or in general to update the Windows service's password.<br>• CVUDB: This wallet type stores a database user name and password that the health check component of CVU uses to connect to the database and perform database checks. |
| `-name ``name`                | You must specify the wallet name to modify an APPQOSDB wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-user ``user_name`` -passwd` | You must specify the user name for whom you want to modify the password. Modify the password through standard input.                                                                                                                                                                                                                                                                                                                                                                                                                 |

##### Usage Notes

You cannot use this command to change a user name.

##### Example

To modify the password of a low-privileged Oracle home user:

    $ crsctl modify wallet -type OSUSER -user lp_oracle_home_user -passwd

#### crsctl query wallet

Queries low-privileged users from a wallet.

##### Syntax

    crsctl query wallet -type wallet_type [-name name] [-user user_name] [-all]

##### Parameters

Table E-91 crsctl query wallet Command Parameters

| Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-type ``wallet_type` | Type of wallet you want to query, such as APPQOSADMIN, APPQOSUSER, APPQOSDB, MGMTDB, OSUSER, or CVUDB.<br>• OSUSER: This wallet type stores a low-privileged Windows user's user name and password that the agent uses when you create a Windows service on a policy-managed database or in general to update the Windows service's password.<br>• CVUDB: This wallet type stores a database user name and password that the health check component of CVU uses to connect to the database and perform database checks. |
| `-name ``name`        | You must specify the name of the wallet to query an APPQOSDB wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-user ``user_name`   | You must specify a user name to query a user from an OSUSER wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `–all`                | Specify `-all` to list all of the users in a specific wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

##### Example

To list all of the users in the OSUSER wallet:

    $ crsctl query wallet -type OSUSER -all

### Oracle Restart Environment CRSCTL Commands

You can only use these commands in the Oracle Restart environment.

The commands listed in this section control Oracle High Availability Services. These commands manage the Oracle High Availability Services stack in the Oracle Restart environment, which consists of the Oracle High Availability Services daemon (`ohasd`), Oracle ASM (if installed), and Cluster Synchronization Services (if Oracle ASM is installed). These commands only affect the local server on which you run them.

**Note:**

Oracle does not support using `crs_*` commands in an Oracle Restart environment.

Each server in the cluster is in one of two possible states:

- The whole stack is up, which means that Oracle High Availability Services is active

- The whole stack is down, which means that Oracle High Availability Services is inactive

#### crsctl check has

Checks the status of `ohasd`.

##### Syntax

    crsctl check has

##### Example

This command returns output similar to the following:

    CRS-4638: Oracle High Availability Services is online

#### crsctl config has

Displays the automatic startup configuration of the Oracle High Availability Services stack on the server.

##### Syntax

    crsctl config has

##### Usage Notes

This command has no parameters.

##### Example

This command returns output similar to the following:

    CRS-4622 Oracle High Availability Services autostart is enabled.

#### crsctl disable has

Disables automatic startup of the Oracle High Availability Services stack when the server boots up.

##### Syntax

    crsctl disable has

##### Example

This command returns output similar to the following:

    CRS-4621 Oracle High Availability Services autostart is disabled.

#### crsctl enable has

Enables automatic startup of the Oracle High Availability Services stack when the server boots up.

##### Syntax

    crsctl enable has

##### Example

This command returns output similar to the following:

    CRS-4622 Oracle High Availability Services autostart is enabled.

#### crsctl query has releaseversion

Displays the release version of the Oracle Clusterware software that is stored in the binaries on the local node.

##### Syntax

    crsctl query has releaseversion

##### Example

This command returns output similar to the following:

    Oracle High Availability Services release version on the local node is [12.2.0.1.0]

#### crsctl query has softwareversion

Displays the software version on the local node.

##### Syntax

    crsctl query has softwareversion [server_name]

##### Usage Notes

If you do not provide a server name, then Oracle Clusterware displays the version of Oracle Clusterware running on the local server.

##### Example

This command returns output similar to the following:

    Oracle High Availability Services version on the local node is [12.2.0.1.0]

#### crsctl start has

Starts Oracle High Availability Services on the local server.

##### Syntax

    crsctl start has [-nowait] [-noautostart] [-wait]

##### Usage Notes

- Use the `-nowait` parameter to skip waiting for Oracle High Availability Services to start.
- Use the `-noautorestart` parameter to start only Oracle High Availability Services.
- Use the `-wait` parameter to wait for Oracle High Availability Services to start.

##### Example

To start Oracle High Availability Services on the local server:

    # crsctl start has

#### crsctl stop has

Stops Oracle High Availability Services on the local server.

This command attempts to gracefully stop resources managed by Oracle Clusterware while attempting to stop Oracle High Availability Services.

##### Syntax

    crsctl stop has [-f]

##### Usage Notes

If any resources that Oracle Clusterware manages are still running after you run the `crsctl stop has` command, then the command fails. Use the `-f` parameter to unconditionally stop all resources and stop Oracle High Availability Services.

##### Example

To stop Oracle High Availability Services on the local server:

    # crsctl stop has

### Troubleshooting and Diagnostic Output

You can use `crsctl set log` commands as the `root` user to enable dynamic debugging for Cluster Ready Services (CRS), Cluster Synchronization Services (CSS), and the Event Manager (EVM), and the clusterware subcomponents.

You can dynamically change debugging levels using `crsctl debug` commands. Debugging information remains in the Oracle Cluster Registry (OCR) for use during the next startup. You can also enable debugging for resources.

This section includes the following topics:

- Dynamic Debugging Using crsctl set log

- Component Level Debugging

#### Dynamic Debugging Using crsctl set log

Setting log levels for Oracle Clusterware.

##### Syntax

    crsctl set log module_name "component1=level1,..."

##### Usage Notes

- You can set log levels for various components of the following modules:

  - `mdns`: Multicast domain name server
  - `gpnp`: Grid Plug and Play service
  - `css`: Cluster Synchronization Services
  - `crf`: Cluster Health Monitor
  - `crs`: Cluster Ready Services
  - `ctss`: Cluster Time Synchronization Service
  - `evm`: Event Manager
  - `gipc`: Grid Interprocess Communication

  Use the `crsctl lsmodules` command to obtain a list of components for each module.

- You can specify multiple component name/log level pairs in a comma-delimited list enclosed in double quotation marks ("").

- Separate component name/log level pairs with an equals sign (=) in Oracle Clusterware 11g release 2 (11.2.0.3), and later. Previous Oracle Clusterware versions used a colon (:).

- The `log_level` is a number from `1` to `5` that sets the log level for the component or resource, where 1 is the least amount of log output and 5 provides the most detailed log output. The default log level is 2.

##### Example

To set log levels for the CRSRTI and CRSCOMM components of the CRS module:

    $ crsctl set log crs "CRSRTI=1,CRSCOMM=2"

#### Component Level Debugging

You can use `crsctl set log` and `crsctl set trace` commands as the `root` user to enable dynamic debugging for the various Oracle Clusterware modules.

##### Enabling Debugging for Oracle Clusterware Modules

You can enable debugging for Oracle Clusterware modules and their components, and for resources, by setting environment variables or by running the `crsctl set log` command.

Use the following syntax to enable debugging for various Oracle Clusterware modules:

    crsctl set {log | trace} module_name "component:debugging_level[,...]"

Run the `crsctl set` command as the `root` user, and supply the following information:

- `module_name`: Specify the name of one of the following modules:

  - `mdns`: Multicast domain name server
  - `gpnp`: Grid Plug and Play service
  - `css`: Cluster Synchronization Services
  - `crf`: Cluster Health Monitor
  - `crs`: Cluster Ready Services
  - `ctss`: Cluster Time Synchronization Service
  - `evm`: Event Manager
  - `gipc`: Grid Interprocess Communication

- `component`: Specify the name of a component for one of the modules. See Table E-92 for a list of all of the components.

- `debugging_level`: Specify a number from 1 to 5 to indicate the level of detail you want the debug command to return, where 1 is the least amount of debugging output and 5 provides the most detailed debugging output. The default debugging level is 2.

The following examples show how to enable debugging for the various modules:

- To enable debugging for Oracle Clusterware:

      # crsctl set log crs "CRSRTI:1,CRSCOMM:2"

- To enable debugging for OCR:

      # crsctl set log crs "CRSRTI:1,CRSCOMM:2,OCRSRV:4"

- To enable debugging for EVM:

      # crsctl set log evm "EVMCOMM:1"

- To enable debugging for resources

      # crsctl set log res "resname:1"

To obtain a list of components that can be used for debugging, run the `crsctl lsmodules` command, with the following syntax:

    $ crsctl lsmodules {mdns | gpnp | css | crf | crs | ctss | evm | gipc}

**Note:**

You do not have to be the `root` user to run the `crsctl lsmodulues` command.

Table E-92 shows the components for the CRS, CSS, and EVM modules, respectively. Note that some component names are common between the CRS, EVM, and CSS daemons and may be enabled on that specific daemon. For example, `COMMNS` is the NS layer and because each daemon uses the NS layer, you can enable this specific module component on any of the daemons to get specific debugging information.

Table E-92 Components for the CRS, CSS, and EVM Modules

| CRS Components(1)                                                                                                                                                                                  | CSS Components(2)               | EVM Components(3)                                                                                                                     |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `CRSUI`<br>`CRSCOMM`<br>`CRSRTI`<br>`CRSMAIN`<br>`CRSPLACE`<br>`CRSAPP`<br>`CRSRES`<br>`CRSCOMM`<br>`CRSOCR`<br>`CRSTIMER`<br>`CRSEVT`<br>`CRSD`<br>`CLUCLS`<br>`CSSCLNT`<br>`COMMCRS`<br>`COMMNS` | `CSSD`<br>`COMMCRS`<br>`COMMNS` | `EVMD`<br>`EVMDMAIN`<br>`EVMCOMM`<br>`EVMEVT`<br>`EVMAPP`<br>`EVMAGENT`<br>`CRSOCR`<br>`CLUCLS`<br>`CSSCLNT`<br>`COMMCRS`<br>`COMMNS` |

<sup>Footnote 1</sup> Obtain the list of CRS components using the crsctl lsmodules crs command.

<sup>Footnote 2</sup> Obtain the list of CSS components using the crsctl lsmodules css command.

<sup>Footnote 3</sup> Obtain the list of EVM components using the crsctl lsmodules evm command.

For example, use the following command to set debugging levels on specific cluster nodes, include the `-nodelist` keyword and the names of the nodes, as follows:

    crsctl set log crs "CRSRTI:1,CRSCOMM:2" -nodelist node1,node2

Table E-93 describes the Cluster Synchronization Services modules.

Table E-93 Cluster Synchronization Services (CSS) Modules and Functions

| Module | Description          |
|:-------|:---------------------|
| CSS    | CSS client component |
| CSSD   | CSS daemon component |

Table E-94 describes the function of each communication (COMM) module.

Table E-94 Communication (COMM) Modules and Functions

| Module  | Description                     |
|:--------|:--------------------------------|
| COMMCRS | Clusterware communication layer |
| COMMNS  | NS communication layer          |

Table E-95 describes the functions performed by each CRS module.

Table E-95 Oracle Clusterware (CRS) Modules and Functions

| Module   | Descriptions                      |
|:---------|:----------------------------------|
| CRSUI    | User interface module             |
| CRSCOMM  | Communication module              |
| CRSRTI   | Resource management module        |
| CRSMAIN  | Main module/driver                |
| CRSPLACE | CRS placement module              |
| CRSAPP   | CRS application                   |
| CRSRES   | CRS resources                     |
| CRSOCR   | Oracle Cluster Registry interface |
| CRSTIMER | Various timers related to CRS     |
| CRSEVT   | CRS EVM/event interface module    |
| CRSD     | CRS daemon                        |

Using the `crsctl set log crs` command, you can debug the OCR components listed in Table E-96. The components listed in Table E-96 can also be used for the Oracle Local Registry (OLR) except for OCRMAS and OCRASM. You can also use them for OCR and OLR clients, except for OCRMAS and OCRSRV. Some OCR and OLR clients are OCRCONFIG, OCRDUMP, and so on.

Table E-96 Oracle Cluster Registry (OCR) Component Names

| Module | Description                                |
|:-------|:-------------------------------------------|
| OCRAPI | OCR abstraction component                  |
| OCRCLI | OCR client component                       |
| OCRSRV | OCR server component                       |
| OCRMAS | OCR master thread component                |
| OCRMSG | OCR message component                      |
| OCRCAC | OCR cache component                        |
| OCRRAW | OCR raw device component                   |
| OCRUTL | OCR util component                         |
| OCROSD | OCR operating system dependent (OSD) layer |
| OCRASM | OCR ASM component                          |

Table E-97 describes the OCR tool modules.

Table E-97 OCRCONFIG Modules and Functions

| Module    | Description                                                       |
|:----------|:------------------------------------------------------------------|
| OCRCONFIG | OCRCONFIG component for configuring OCR                           |
| OCRDUMP   | OCRDUMP component that lists the Oracle Cluster Registry contents |
| OCRCHECK  | OCRCHECK component that verifies all of the configured OCRs       |

##### Enabling Debugging for Oracle Clusterware Resources

You can enable debugging for Oracle Clusterware resources by running the `crsctl set log` command, using the following syntax:

    crsctl set log res "resource_name=debugging_level"

Run the `crsctl set log` command as the `root` user, and supply the following information:

- `resource_name`: The name of the resource to debug.

- `debugging_level`: A number from `1` to `5` to indicate the level of detail you want the debug command to return, where 1 is the least amount of debugging output and 5 provides the most detailed debugging output.
  **Note:**

  After you resolve an issue that required additional debugging, you can reset the debug level to default, as follows:
      # crsctl set log crs resource_name=default

To obtain a list of resources that can be used for debugging, run the `crsctl status resource` command.

Example

To generate a debugging log for the VIP resource on `node1`, issue the following command:

    # crsctl set log res "ora.node1.vip:1"
