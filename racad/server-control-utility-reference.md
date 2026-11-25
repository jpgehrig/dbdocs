Use the Server Control Utility (SRVCTL) to manage Oracle Real Application Clusters (Oracle RAC) configuration information.

**Note:**

SRVCTL commands specific to Oracle Grid Infrastructure administration operations are documented in [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)

This appendix includes the following topics:

- SRVCTL Usage Information

- Specifying Command Parameters as Keywords Instead of Single Letters

- Character Set and Case Sensitivity of SRVCTL Object Values

- Summary of Tasks for Which SRVCTL Is Used

- Using SRVCTL Help

- SRVCTL Privileges and Security

- Additional SRVCTL Topics

- Deprecated SRVCTL Subprograms or Commands

- SRVCTL Command Reference

### SRVCTL Usage Information

SRVCTL is installed on each node in a cluster by default. To use SRVCTL, log in to the operating system of a node and enter the SRVCTL command and its parameters in case-sensitive syntax.

- Use the version of SRVCTL that is provided with the current Oracle Database release from the Oracle home of the database that you are managing. The version of SRVCTL must be the same as the version of the object (listeners, Oracle ASM instances, Oracle Database, Oracle Database instances, and Oracle Database services) being managed.

- SRVCTL does not support concurrent executions of commands on the same object. Therefore, run only one SRVCTL command at a time for each database, service, or other object.

- When specifying a comma-delimited list as part of a SRVCTL command, there should not be any spaces between the items in the list. For example:

      srvctl add database -serverpool "serverpool1,serverpool3"

  When you specify a comma-delimited list in a Windows environment, you must enclose the list in double quotation marks (`""`). You can enclose a comma-delimited list in double quotation marks in a Linux or UNIX environment but they will be ignored.

- If you are entering a SRVCTL command, and you want to continue the input on a new line, then you can use the operating system continuation character. In Linux, this is the backslash (\\ symbol.

- A SRVCTL command that produces no output is a successful command. Not all SRVCTL commands return a message when it completes, successfully. However, if a SRVCTL command fails, then it always returns an error message.

- SRVCTL returns `0` on success, `1` on failure, and `2` on warnings. Some commands, such as `start`, `stop`, `enable`, and `disable`, can return 2 for a warning when the request would not change anything. In other words, the object of the command is already started, already stopped, already disabled, and so on. In warning cases, SRVCTL also prints a message about what was already done.

- You can use the `-eval` parameter with several SRVCTL commands. This parameter, when you use it, enables you to simulate running a command without making any changes to the system. SRVCTL returns output that informs you what will happen if you run a particular command. For example, to know what might happen if you relocate a server:

      $ srvctl relocate server –servers "rac1" –eval –serverpool pool2

      Database db1
           will stop on node rac1
           will start on node rac7
           Service mySrv1
                will stop on node rac1, it will not run on any node
           Service myServ2
                will stop on node rac1
                will start on node rac6
      Server rac1
           will be moved from pool myPoolX to pool pool2

  The `-eval` parameter is available with the following commands:

  - `srvctl add database`

  - `srvctl add service`

  - `srvctl add srvpool`

  - `srvctl modify database`

  - `srvctl modify service`

  - `srvctl modify srvpool`

  - `srvctl relocate server`

  - `srvctl relocate service`

  - `srvctl remove srvpool`

  - `srvctl start database`

  - `srvctl start service`

  - `srvctl stop database`

  - `srvctl stop service`

### Specifying Command Parameters as Keywords Instead of Single Letters

Before Oracle Database 12c, the SRVCTL command-line interface used single letter parameters. However, this imposes a limit on the number of unique parameters available for use with SRVCTL commands. SRVCTL command parameters introduced in Oracle Database 12c are full words instead of single letters, such as `-multicastport` and `-subdomain`.

To support backward compatibility, you can use a mix of single-letter parameters and new keyword parameters. New parameters introduced with keywords can be used with single letter parameters.

**Note:**

Starting with Oracle Database 12c, the single letter parameters are deprecated in favor of the keyword parameters to avoid using the same letter to implement different functionality depending on the command.

You can obtain the single-letter equivalents, where applicable, by adding the `-compatible` parameter after the `-help` parameter.

### Character Set and Case Sensitivity of SRVCTL Object Values

SRVCTL interacts with many different types of objects. The character set and name length limitations, and whether the object name is case sensitive, can vary between object types.

Table A-1 String Restrictions for SRVCTL Object Names

| Object Type      | Character Set Limitations                                                                                                                                                                                                                                                            | Case Sensitive?                           | Maximum Length                                                                                             |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| `db_domain`      | Alpha-numeric characters, underscore (\_), and number sign (#)                                                                                                                                                                                                                       |                                           | 128 characters                                                                                             |
| `db_unique_name` | Alpha-numeric characters, underscore (\_), number sign (#), and dollar sign (\$); the first 8 characters must be unique because those characters are used to form instance names for policy-managed databases                                                                        | No                                        | 30 characters but the first 8 characters must be unique relative to any other database in the same cluster |
| `diskgroup_name` | Naming disk groups have the same limitations as naming other database objects.<br>See Also: [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md) for more information about database object naming rules                                       | No (all names are converted to uppercase) |                                                                                                            |
| `instance_name`  | Alpha-numeric characters                                                                                                                                                                                                                                                             | Depends on the platform                   | 15 characters                                                                                              |
| `listener_name`  |                                                                                                                                                                                                                                                                                      |                                           |                                                                                                            |
| `node_name`      |                                                                                                                                                                                                                                                                                      | No                                        |                                                                                                            |
| `scan_name`      | The first character must be an alphabetic character                                                                                                                                                                                                                                  | No                                        |                                                                                                            |
| `server_pool`    | Alpha-numeric characters, underscore (\_), number sign (#), period (.), and dollar sign (\$); the name cannot begin with a period, contain single quotation marks (`''`), nor can the name be "Generic" or "Free" because those two names are reserved for the built-in server pools |                                           | 250 characters                                                                                             |
| `service_name`   |                                                                                                                                                                                                                                                                                      |                                           | 250 characters                                                                                             |
| `volume_name`    | Alphanumeric characters; dashes (-) are not allowed and the first character must be an alphabetic character.                                                                                                                                                                         | No                                        | 11 characters                                                                                              |

### Summary of Tasks for Which SRVCTL Is Used

Use SRVCTL to manage databases, instances, cluster databases, cluster database instances, Oracle ASM instances and disk groups, services, listeners, or other clusterware resources.

- Database Configuration Tasks

  | Tasks                                                                                     | Commands                                                                                                       |
  |:------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------|
  | Add, modify, and delete database configuration information                                | `srvctl add database`<br>`srvctl modify database`<br>`srvctl remove database`                                  |
  | Add an instance to or delete an instance from the configuration of an Oracle RAC database | `srvctl add instance`<br>`srvctl remove instance`                                                              |
  | Add a service to or delete a service from the configuration of a database                 | `srvctl add service`<br>`srvctl remove service`                                                                |
  | Move instances and services in a database configuration and modify service configurations | `srvctl relocate database`<br>`srvctl relocate service`<br>`srvctl modify instance`<br>`srvctl modify service` |
  | Set and unset the environment for an instance or service in a database configuration      | `srvctl modify instance`<br>`srvctl modify service`                                                            |
  | Set and unset the environment for an entire cluster database in a database configuration  | `srvctl setenv database`<br>`srvctl unsetenv database`                                                         |

- General Database Administration Tasks

  | Tasks                                                                  | Commands                                                                        |
  |:-----------------------------------------------------------------------|:--------------------------------------------------------------------------------|
  | Start and stop databases                                               | `srvctl start database`<br>`srvctl stop database`                               |
  | Start and stop database instances                                      | `srvctl start instance`<br>`srvctl stop instance`                               |
  | Start, stop, and relocate database services                            | `srvctl start service`<br>`srvctl stop service`<br>`srvctl relocate service`    |
  | Obtain statuses of databases, database instances, or database services | `srvctl status database`<br>`srvctl status instance`<br>`srvctl status service` |

- Node-Level Tasks

  | Tasks                           | Commands                                                                                                                                                                                                                                                                                               |
  |:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Administering VIPs              | `srvctl add vip`<br>`srvctl config vip`<br>`srvctl disable vip`<br>`srvctl enable vip`<br>`srvctl getenv vip`<br>`srvctl modify vip`<br>`srvctl relocate vip`<br>`srvctl remove vip`<br>`srvctl setenv vip`<br>`srvctl start vip`<br>`srvctl status vip`<br>`srvctl stop vip`<br>`srvctl unsetenv vip` |
  | Administering node applications | `srvctl add nodeapps`<br>`srvctl disable nodeapps`<br>`srvctl enable nodeapps`<br>`srvctl getenv nodeapps`<br>`srvctl modify nodeapps`<br>`srvctl remove nodeapps`<br>`srvctl setenv nodeapps`<br>`srvctl unsetenv nodeapps`                                                                           |

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)

### Using SRVCTL Help

This section includes information about using context sensitive help with SRVCTL.

To see help for all SRVCTL commands, from the command line enter:

    srvctl -help

To see the command syntax and a list of parameters for each SRVCTL command, from the command line enter:

    srvctl command (or verb) object (or noun) -help

When you request online help for a command using `-help`, SRVCTL prints the full words for each parameter. You can obtain the single-letter equivalents, where applicable, by adding the `-compatible` parameter after the `-help` parameter. For example:

    $ srvctl config database -help -compatible

The preceding command prints usage information for the `srvctl config database` command, listing all parameters as full words followed by their single-letter equivalents in parentheses, where applicable.

To see the SRVCTL version number enter:

    $ srvctl -version

### SRVCTL Privileges and Security

To use SRVCTL to change your database configuration, log in to the operating system as the software owner of the home that you want to manage.

For example, if different users installed Oracle Database and the Oracle Grid Infrastructure, then log in as the database software owner (for example, `ora_db`) to manage databases and log in as the Oracle Grid Infrastructure software owner (for example, `ora_asm`) to manage the Oracle ASM instances.

Users who are members of the OSDBA operating system group can start and stop the database. To stop and start an Oracle ASM instance, you must be a member of the OSASM operating system group.

To create or register objects such as listeners, Oracle Notification Services, and services, you must be logged in to the operating system as the software owner of the Oracle home. The objects you create or register for that Oracle home will run under the user account of the owner of the Oracle home. Databases run as the database installation owner of the home from which they run.

To perform `srvctl add` operations on any object, you must be logged in as the Oracle account owner of the home on which the object runs.

For some SRVCTL commands, on Linux and UNIX systems, you must be logged in as `root`, and on Windows systems, you must be logged in as a user with Administrator privileges to run them. In this appendix, those commands are preceded by the root prompt (#) in the command examples.

### Additional SRVCTL Topics

- Use SRVCTL to manage Oracle-supplied resources such as listener, instances, disk groups, and networks, and CRSCTL for managing Oracle Clusterware and its resources.

  **Note:**

  Oracle strongly discourages directly manipulating Oracle-supplied resources (resources whose names begin with ora) using CRSCTL. This could adversely impact the cluster configuration.

- Although you may be able to cancel running SRVCTL commands by pressing the Control-C keys, you may corrupt your configuration data by doing this.

  You are strongly advised not to attempt to terminate SRVCTL in this manner.

### Deprecated SRVCTL Subprograms or Commands

A number of SRVCTL commands and parameters have been deprecated in this release.

#### Single Character Parameters for all SRVCTL Commands

Single-character parameters have been deprecated in Oracle Database 12c.

Use the full keyword for each parameter instead. To support older tools and scripts that still use single-character parameters, the current version of SRVCTL supports both single-character parameters and full keyword parameters.

The command reference in this appendix shows the keywords for each SRVCTL command. Table A-2 lists the deprecated single-character parameters.

Table A-2 Deprecated Single-Character Parameters for SRVCTL Commands

| Single Letter | Long Form          | Values                                                                                                  | Description                                                                                                                                                                  | Related Commands                                                                                                                                         |
|:--------------|:-------------------|:--------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `A`           | `address`          | `{``VIP_name`` | ``IP``}/``netmask``/ [``if1``[|``if2``...]]`                                           | VIP address specification for node applications                                                                                                                              | Node applications, VIP, network, Listener, SCAN VIP, and SCAN listener commands                                                                          |
| `a`           | `all`              |                                                                                                         | All resources of that kind                                                                                                                                                   | `srvctl config database`<br>Common                                                                                                                       |
| `a`           | `diskgroup`        | `diskgroup_list`                                                                                        | Comma-delimited list of Oracle ASM disk groups                                                                                                                               | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `a`           | `detail`           |                                                                                                         | Print detailed configuration information                                                                                                                                     | Common                                                                                                                                                   |
| `a`           | `available`        | `available_list`                                                                                        | A comma-delimited list of available instances                                                                                                                                | Service and server pool commands                                                                                                                         |
| `a`           | `abort`            |                                                                                                         | Stop failed online relocation                                                                                                                                                | Relocate database                                                                                                                                        |
| `a`           | `viponly`          |                                                                                                         | Display VIP configuration                                                                                                                                                    | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `B`           | `rlbgoal`          | `{NONE| SERVICE_TIME| THROUGHPUT}`                                                                      | The runtime load balancing goal of a service                                                                                                                                 | Service and server pool commands                                                                                                                         |
| `c`           | `currentnode`      | `current_node`                                                                                          | Node name from which to relocate the service                                                                                                                                 | Service and server pool commands                                                                                                                         |
| `c`           | `cardinality`      | `{UNIFORM| SINGLETON}`                                                                                  | Whether the service should run on every active server in the server pool (UNIFORM) or only one server (SINGLETON)                                                            | Service and server pool commands                                                                                                                         |
| `c`           | `dbtype`           | `type`                                                                                                  | Type of database: Oracle RAC One Node, Oracle RAC, or single instance                                                                                                        | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `d`           | `db` or `database` | `db_unique_name`                                                                                        | Database unique name                                                                                                                                                         | Common                                                                                                                                                   |
| `d`           | `device`           | `volume_device`                                                                                         | Volume device path                                                                                                                                                           | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `d`           | `domain`           |                                                                                                         | Display subdomain served by GNS                                                                                                                                              | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `e`           | `emport`           | `em_port_number`                                                                                        | Local listen port for Oracle Enterprise Manager                                                                                                                              | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `e`           | `failovertype`     | `{NONE|SESSION BASIC|TRANSACTION}`                                                                      | The failover type for a service                                                                                                                                              | Service and server pool commands                                                                                                                         |
| `e`           | `server`           | `server_list`                                                                                           | Candidate server list for Oracle RAC One Node database                                                                                                                       | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `f`           | `force`            |                                                                                                         | Force remove                                                                                                                                                                 | Common                                                                                                                                                   |
| `g`           | `diskgroup`        | `diskgroup_name`                                                                                        | Disk group name                                                                                                                                                              | File system, Diskgroup commands                                                                                                                          |
| `g`           | `gsdonly`          |                                                                                                         | Display GSD configuration                                                                                                                                                    | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `g`           | `serverpool`       | `server_pool_name`` ``server_pool_list`                                                                 | A server pool name<br>Comma-delimited list of database server pool names                                                                                                     | Service and server pool commands<br>Database, instance, Oracle ASM, disk group, and file system commands                                                 |
| `h`           | `help`             |                                                                                                         |                                                                                                                                                                              | Common                                                                                                                                                   |
| `i`           | `importance`       | `number`                                                                                                | A number that represents the importance of the server pool                                                                                                                   | Service and server pool commands                                                                                                                         |
| `i`           | `instance`         | `instance_name`` ``instance_list`                                                                       | Instance name prefix for administrator-managed Oracle RAC One Node database<br>A comma-delimited list of instance names                                                      | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `I`           | `ip`               | `ip_address`                                                                                            | VIP address on which GNS is to listen                                                                                                                                        | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `i`           | `oldinst`          | `instance_name`                                                                                         | The old instance name                                                                                                                                                        | Service and server pool commands                                                                                                                         |
| `i`           | `scannumber`       | `scan_ordinal`` ``_number`                                                                              | Ordinal number of the IP address for the SCAN                                                                                                                                | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `i`           | `vip`              | `vip_name`` or "``vip_name``_list``"`                                                                   | VIP names                                                                                                                                                                    | Node applications, GNS, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                     |
| `j`           | `acfspath`         | `acfs_path_list`                                                                                        | Comma-delimited list of Oracle ACFS paths where the dependency on the database will be set                                                                                   | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `j`           | `clbgoal`          | `{SHORT|LONG}`                                                                                          | The connection load balancing goal for a service                                                                                                                             | Service and server pool commands                                                                                                                         |
| `k`           | `netnum`           | `network_number`                                                                                        | The network number                                                                                                                                                           | Service and server pool commands<br>Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands<br>OC4J, home, CVU, and GNS commands |
| `l`           | `list`             |                                                                                                         | List all records in GNS                                                                                                                                                      | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `l`           | `listener`         | `listener_name`                                                                                         | The name of a listener                                                                                                                                                       | ASM commands                                                                                                                                             |
| `l`           | `loglevel`         | `log_level`                                                                                             | Specify the level (0-6) of logging that GNS should run with                                                                                                                  | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `l`           | `min`              | `number`                                                                                                | The minimum size of the server pool                                                                                                                                          | Service and server pool commands                                                                                                                         |
| `l`           | `onslocalport`     | `port_number`                                                                                           | Oracle Notification Service listening port for local client connections                                                                                                      | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `l`           | `role`             | `service_role`                                                                                          | Comma-delimited list of server roles within double quotation marks (`""`), where each role is one of `PRIMARY`, `PHYSICAL_STANDBY`, `LOGICAL_STANDBY`, or `SNAPSHOT_STANDBY` | Service and server pool commands                                                                                                                         |
| `m`           | `domain`           | `domain_name`                                                                                           | The domain for the database                                                                                                                                                  | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `m`           | `failovermethod`   | `{NONE|BASIC}`                                                                                          | The failover method of a service                                                                                                                                             | Service and server pool commands                                                                                                                         |
| `m`           | `multicastpost`    |                                                                                                         | The port on which the GNS daemon is listening for multicast requests                                                                                                         | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `m`           | `path`             | `mountpoint_path`                                                                                       | Mountpoint path                                                                                                                                                              | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `n`           | `name`             |                                                                                                         | Advertise a name through GNS using the given address                                                                                                                         | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `n`           | `node`             | `node_name`                                                                                             | The name of a specific node                                                                                                                                                  | Common                                                                                                                                                   |
| `n`           | `nodes`            | `node_list`                                                                                             | A comma-delimited list of node names                                                                                                                                         | File system commands                                                                                                                                     |
| `n`           | `dbname`           | `database_name`                                                                                         | The database name (DB_NAME), if different from the unique name specified by the `-db` parameter                                                                              | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `n`           | `scanname`         | `scan_name`                                                                                             | Fully-qualified SCAN name (includes the domain)                                                                                                                              | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `n`           | `servers`          | `server_list`                                                                                           | A comma-delimited list of candidate server names                                                                                                                             | Service and server pool commands                                                                                                                         |
| `n`           | `targetnode`       | `node_name`                                                                                             | Node name to which to relocate the service                                                                                                                                   | Service and server pool commands                                                                                                                         |
| `o`           | `oraclehome`       | `oracle_home`                                                                                           | `$ORACLE_HOME` path                                                                                                                                                          | Database commands                                                                                                                                        |
| `p`           | `endpoints`        | `[TCP:]``port`` ``_number``[/IPC: ``key``][/NMP:``pipe`` ``_name``][/TCPS: ``s_port``][/SDP: ``port``]` | SCAN listener endpoints                                                                                                                                                      | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `p`           | `port`             |                                                                                                         | The port which the GNS daemon uses to communicate with the DNS server                                                                                                        | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `p`           | `rmiport`          | `port_number`                                                                                           | OC4J RMI port number                                                                                                                                                         | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `P`           | `tafpolicy`        | `{NONE|BASIC}`                                                                                          | TAF policy specification                                                                                                                                                     | Service and server pool commands                                                                                                                         |
| `p`           | `spfile`           | `spfile_location`                                                                                       | Server parameter file path                                                                                                                                                   | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `q`           | `notification`     | `{TRUE|FALSE}`                                                                                          | Whether FAN is enabled for OCI connections                                                                                                                                   | Service commands                                                                                                                                         |
| `q`           | `query`            |                                                                                                         | Query GNS for the records belonging to a name                                                                                                                                | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `r`           | `preferred`        | `preferred_list`                                                                                        | A comma-delimited list of preferred instances                                                                                                                                | Service and server pool commands                                                                                                                         |
| `r`           | `onsremoteport`    | `port_number`                                                                                           | Oracle Notification Service listening port for connections from remote hosts                                                                                                 | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `r`           | `relocate`         |                                                                                                         | Relocate the VIP                                                                                                                                                             | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `r`           | `revert`           |                                                                                                         | Remove target node of failed online relocation request from the candidate server list of administrator-managed Oracle RAC One Node database                                  | Relocate database                                                                                                                                        |
| `r`           | `role`             | `role_type`                                                                                             | Role of the standby database: `PRIMARY`, `PHYSICAL_STANDBY`, `LOGICAL_STANDBY`, or `SNAPSHOT_STANDBY`                                                                        | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `s`           | `onsonly`          |                                                                                                         | Display Oracle Notification Service daemon configuration                                                                                                                     | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `s`           | `skip`             |                                                                                                         | Skip checking the ports                                                                                                                                                      | Listener, SCAN, and SCAN listener.                                                                                                                       |
| `s`           | `statfile`         | `file_name`                                                                                             | The file path of the `state_file` created by a previously run `srvctl stop home` command                                                                                     | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `s`           | `status`           |                                                                                                         | Display the status of GNS                                                                                                                                                    | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `S`           | `subnet`           | `subnet``/``net`` ``_mask``/[``if1``[| ``if2``...]]`                                                    | Network address specification for a network                                                                                                                                  | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `s`           | `service`          | `service_name`` ``service_name``_list`                                                                  | The name of a service<br>A comma-delimited list of service names                                                                                                             | Service and server pool commands                                                                                                                         |
| `s`           | `startoption`      | `start_options`                                                                                         | Startup options for the database (mount, open, read only)                                                                                                                    | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `t`           | `checkinterval`    | `time_interval`                                                                                         | Interval in minutes between checks                                                                                                                                           | OC4J, home, CVU, and GNS commands                                                                                                                        |
| `t`           | `edition`          | `edition_name`                                                                                          | The initial session edition of a service                                                                                                                                     | Service and server pool commands                                                                                                                         |
| `t`           | `envs`             | `"``name_list``"`                                                                                       | A list of environment variables                                                                                                                                              | Common                                                                                                                                                   |
| `t`           | `namevals`         | `"``name``= ``value``,..."`                                                                             | Names and values of environment variables                                                                                                                                    | Common                                                                                                                                                   |
| `T`           | `nameval`          | `"``name``=``value``"`                                                                                  | Name and value of a single environment variable                                                                                                                              | Common                                                                                                                                                   |
| `t`           | `update`           | `instance_name`                                                                                         | The new instance name                                                                                                                                                        | Service and server pool commands                                                                                                                         |
| `t`           | `remoteservers`    | `host_name``[: ``port_number``] [,``host_name``[: ``port_number``]...]`                                 | List of remote host name and port number pairs for Oracle Notification Service daemons outside this cluster                                                                  | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `t`           | `stopoption`       | `stop_options`                                                                                          | Stop options for the database (`NORMAL`, `TRANSACTIONAL`, `IMMEDITATE`, or `ABORT`)                                                                                          | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `t`           | `toversion`        | `target_version`                                                                                        | Version to which you are downgrading                                                                                                                                         | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `u`           | `max`              | `number`                                                                                                | Maximum size of the server pool                                                                                                                                              | Service and server pool commands                                                                                                                         |
| `u`           | `nettype`          | `network_type`                                                                                          | The network server type, which can be `STATIC`, `DHCP`, or `MIXED`                                                                                                           | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `u`           | `newinst`          |                                                                                                         | Add a new instance to the service configuration                                                                                                                              | Service commands                                                                                                                                         |
| `u`           | `update`           |                                                                                                         | Update SCAN listeners to match the number of SCAN VIPs                                                                                                                       | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `u`           | `user`             | `oracle_user`                                                                                           | Oracle user or other authorized user to mount and unmount file systems                                                                                                       | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `v`           | `verbose`          |                                                                                                         | Verbose output                                                                                                                                                               | Common                                                                                                                                                   |
| `v`           | `volume`           | `volume_name`                                                                                           | Name of a volume                                                                                                                                                             | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `V`           | `versions`         |                                                                                                         |                                                                                                                                                                              | Common                                                                                                                                                   |
| `w`           | `failoverdelay`    | `number`                                                                                                | Failover delay                                                                                                                                                               | Service and server pool commands                                                                                                                         |
| `w`           | `nettype`          | `network_type`                                                                                          | The network server type, which can be `STATIC`, `DHCP`, or `MIXED`                                                                                                           | Node applications, VIP, network, listener, SCAN VIP, and SCAN listener commands                                                                          |
| `w`           | `timeout`          | `timeout`                                                                                               | Online relocation timeout in minutes                                                                                                                                         | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |
| `x`           | `dtp`              | `{TRUE | FALSE}`                                                                                        | Whether to enable distributed transaction processing                                                                                                                         | Service and server pool commands                                                                                                                         |
| `x`           | `node`             | `node_name`                                                                                             | Node name (use this parameter only with noncluster databases)                                                                                                                | Common                                                                                                                                                   |
| `y`           | `noprompt`         |                                                                                                         | Suppress the confirmation prompt                                                                                                                                             | Common                                                                                                                                                   |
| `y`           | `policy`           | `{AUTOMATIC | MANUAL}`                                                                                  | Management policy for the resource                                                                                                                                           | Database, instance, Oracle ASM, disk group, file system, service and server pool commands                                                                |
| `z`           | `failoverretry`    | `number`                                                                                                | Number of failover retries                                                                                                                                                   | Service and server pool commands                                                                                                                         |
| `z`           | `rmdepondisk`      |                                                                                                         | To remove a database's dependency upon disk groups                                                                                                                           | Database, instance, Oracle ASM, disk group, and file system commands                                                                                     |

#### Miscellaneous SRVCTL Commands and Parameters

The following command parameters have been deprecated in this release:

Table A-3 Deprecated Commands and Parameters for SRVCTL

| Command                  | Deprecated Parameters                                                                                                                                                                                                                 |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `srvctl modify asm`      | `-node` `node_name`                                                                                                                                                                                                                   |
| `srvctl modify instance` | `-z`<br>Instead, use the `-node` option with the value set to `""`                                                                                                                                                                    |
| `srvctl modify gns`      | `[-ip ``ip_address``] [-advertise ``host_name`` -address ``address``] [-delete ``host_name`` -address ``address``] [-createalias ``name`` -alias ``alias``] [-deletealias ``alias``]`<br>Use the `srvctl update gns` command instead. |
| `srvctl * oc4j`          | The `oc4j` noun has been deprecated and replaced with `qosmserver`. SRVCTL still accepts the `oc4j` noun until it is desupported.                                                                                                     |
| `srvctl add service`     | The `PRECONNECT`option with the `-tafpolicy` parameter is deprecated.                                                                                                                                                                 |
| `srvctl modify service`  | The `-failovermethod {NONE | BASIC}` is deprecated.<br>The `PRECONNECT`option with the `-tafpolicy` parameter is deprecated.                                                                                                          |

### SRVCTL Command Reference

A comprehensive list of SRVCTL commands to use in Oracle RAC environments.

SRVCTL commands, object names, and parameters are case sensitive. Database, instance, listener, and service names are case insensitive and case preserving. You cannot create listener names that differ only in case, such as LISTENER and listener. SRVCTL uses the following command syntax:

    srvctl command object [parameters]

In SRVCTL syntax:

- `command` is a verb such as `start`, `stop`, or `remove`

- `object` (also known as a noun) is the target or object on which SRVCTL performs the command, such as database or instance. You can also use object abbreviations.

- `parameters` extend the use of a preceding command combination to include additional parameters for the command. For example, the `-instances` parameter indicates that a comma-delimited list of preferred instance names follows; the `-instance` parameter only permits one value and not a list of names. Do not use spaces between the items in a comma-delimited list.

**Note:**

If specifying a comma-delimited list in Windows, then you must enclose the list within double quotation marks (`""`).

Table A-4 lists the keywords that can be used for the `object` portion of SRVCTL commands. You can use either the full name or the abbreviation for each object keyword. The Purpose column describes the object and the actions that can be performed on that object.

Table A-4 Object Keywords and Abbreviations

| Object                           | Keyword              | Purpose                                                                                                                                                                                                                                       |
|:---------------------------------|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Database                         | `database`           | To add, modify, manage environment variables for, list the configuration of, enable, disable, start, stop, and obtain the status of databases, and also to upgrade, downgrade, and remove database configuration information about databases. |
| Instance                         | `instance`<br>`inst` | To add, modify, enable, disable, start, stop, obtain the status of, and remove database instances.                                                                                                                                            |
| Listener                         | `listener`<br>`lsnr` | To add, modify, manage environment variables for, list the configuration of, enable, disable, start, stop, obtain the status of, and remove listeners                                                                                         |
| Network                          | `network`            | To add, modify, list the configuration of, and remove a non-default Network<br>Note: The node applications object, and the `config` and `modify` commands also manage the default network.                                                    |
| Node applications                | `nodeapps`           | To add, modify, manage environment variables for, list the configuration of, enable, disable, start, stop, obtain the status of, and remove node applications                                                                                 |
| Oracle Notification Service      | `ons`                | To add, configure, enable, start, obtain the status of, stop, disable, and remove Oracle Notification Service instances only for Oracle Restart                                                                                               |
| Single client access name (SCAN) | `scan`               | To add, list the configuration of, modify, enable, disable, start, stop, relocate, obtain the status of, and remove SCAN VIPs                                                                                                                 |
| SCAN listener                    | `scan_listener`      | To add, list the configuration of, modify, enable, disable, start, stop, relocate, obtain the status of, and remove SCAN listeners                                                                                                            |
| Service                          | `service`            | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, and remove services                                                                                                                  |
| Virtual IP                       | `vip`                | To add, manage environment variables for, list the configuration of, enable, disable, start, stop, obtain the status of, and remove a VIP                                                                                                     |

**Note:**

SRVCTL commands specific to Oracle Grid Infrastructure administration operations are documented in [CWADD SRVCTL Command Reference](../cwadd/server-control-command-reference.md)

#### srvctl add database

Adds a database configuration to Oracle Clusterware.

##### Syntax

    srvctl add database -db db_unique_name [-eval]
         -oraclehome oracle_home [-node node_list] [-domain domain_name]
         [-spfile spfile] [-pwfile password_file_path]
         [-dbtype  {RACONENODE | RAC | SINGLE} [-server "server_list"]]
         [-instance instance_name] [-timeout timeout]]
         [-role {PRIMARY | PHYSICAL_STANDBY | LOGICAL_STANDBY | SNAPSHOT_STANDBY"]
         [-startoption start_options] [-stopoption stop_options] [-dbname db_name]
         [-acfspath "acfs_path_list"] [-policy {AUTOMATIC | MANUAL | NORESTART}]
         [-serverpool "server_pool_list" [-pqpool "pq_pool_list"]]
         [-diskgroup "disk_group_list"] [-css_critical {yes | no}] [-cpucount cpu_count]
         [-memorytarget memory_target] [-maxmemory max_memory] [-cpucap cpu_cap] [-defaultnetnum network_number] [-verbose]

##### Parameters

Table A-5 srvctl add database Command Parameters

| Parameter                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                                    | Specify the unique name of the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-eval`                                                                   | Use this parameter to hypothetically evaluate the impact of the command on the system.<br>Note: You can only use this parameter with a policy-managed database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-oraclehome ``oracle_home`                                               | Specify the path for the Oracle database home directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-node ``node_list`                                                       | Specify a single node name or a comma-delimited list of node names on which you want to register a noncluster, or single instance, Oracle database. Starting with Oracle Database 19c Release Update (19.7), you can register a Standard Edition High Availability database on multiple cluster nodes.<br>Note: While creating a policy-managed single instance database, this parameter can be used only with Oracle Clusterware and can be used with the `-serverpool` parameter.                                                                                                                                                                                                                              |
| `-domain ``db_domain`                                                     | Specify the domain for the database.<br>Note: You must use this parameter if you set the `DB_DOMAIN` initialization parameter for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-spfile ``spfile`                                                        | Specify the path name of the database server parameter file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-pwfile ``password_file_path`                                            | Enter the full path to the location of the password file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-dbtype {RACONENODE | RAC | SINGLE}`                                     | Specify the type of database you are adding: Oracle RAC One Node, Oracle RAC, or single instance. The default is `RAC` unless you specify the `-node ``node_name` parameter, and the `-type` parameter defaults to `SINGLE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-server ``server_list`                                                   | List candidate servers for Oracle RAC One Node databases.<br>Note: You can use this parameter only with administrator-managed Oracle RAC One Node databases. If your Oracle RAC One Node database is policy managed, then you cannot use this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-instance ``instance_name`                                               | Specify the instance name prefix for Oracle RAC One Node databases. The default value for this parameter is the first 12 characters of the global unique name of the database.<br>Note: You can use this parameter only with administrator-managed Oracle RAC One Node databases. If your Oracle RAC One Node database is policy managed, then you cannot use this parameter.                                                                                                                                                                                                                                                                                                                                    |
| `-timeout ``timeout`                                                      | Specify the online database relocation timeout, in minutes, for Oracle RAC One Node databases. The default is `30`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-role {PRIMARY | PHYSICAL_STANDBY | LOGICAL_STANDBY | SNAPSHOT_STANDBY}` | Specify the role of the database in an Oracle Data Guard configuration. The default is `PRIMARY`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-startoption ``start_options`                                            | Startup options for the database, such as `OPEN`, `MOUNT`, and `NOMOUNT`. The default value is `OPEN`.<br>Notes:<br>• For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>• When performing a switchover in an Oracle Data Guard configuration, the `-startoption` for a standby database that becomes a primary database is always set to `OPEN` after the switchover.                                                                                                                                                                                                           |
| `-stoption ``stop_options`                                                | Specify stop options for the database, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, and `ABORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-dbname ``db_name`                                                       | Specify the name of the database, if it is different from the unique name given by the `-db` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-acfspath "``acfs_path_list``"`                                          | A single Oracle ACFS path or a comma-delimited list of Oracle ACFS paths enclosed in double quotation marks (`""`) where the database's dependency is set.<br>Use this parameter to create dependencies on Oracle ACFS file systems other than `ORACLE_HOME`, such as for when the database uses `ORACLE_BASE` on a file system that is different from the `ORACLE_HOME` file system.                                                                                                                                                                                                                                                                                                                            |
| `-policy {AUTOMATIC | MANUAL | NORESTART}`                                | Specify the management policy for the database.<br>• `AUTOMATIC` (default): The database is automatically restored to its previous running condition (started or stopped) upon restart of the database host computer.<br>• `MANUAL`: The database is never automatically restarted upon restart of the database host computer. A `MANUAL` setting does not prevent Oracle Clusterware from monitoring the database while it is running and restarting it if a failure occurs.<br>• `NORESTART`: Similar to the `MANUAL` setting, the database is never automatically restarted upon restart of the database host computer. A `NORESTART` setting, however, never restarts the database even if a failure occurs. |
| `-serverpool "``server_pool_name``" [-pqpool "``pq_pool_name``"]`         | Specify the name of a server pool used to control database placement. If you do not specify this parameter, then it defaults to the Generic server pool.<br>You can optionally also specify the name of a parallel query server pool to be used by the database.<br>Notes:<br>• This parameter can only be used with Oracle Clusterware. You can use this parameter with the `-node` parameter but the server pool must have `MAX_SIZE=1` and exactly one configured server (the one you specify in `-node`).<br>• After you add server pools, you can assign services to them using the `srvctl add service` command.                                                                                           |
| `-diskgroup "``disk_group_list``"`                                        | Specify a comma-delimited list of Oracle ASM disk groups if database uses Oracle ASM storage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-css_critical {YES | NO}`                                                | You can add weight to a service by setting this parameter to `YES`. In the event of a node failure within the cluster, Oracle Clusterware will evict the node with the least amount of weight, ensuring that critical services remain available.<br>Note: You can use this parameter only on an administrator-managed node. Should the node become policy managed, at some point, this parameter will no longer apply.                                                                                                                                                                                                                                                                                           |
| `-cpucount ``cpu_count`                                                   | Specify the number of CPUs. The default value is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-memorytarget ``memory_target`                                           | Specify the target memory, in MB, to be allocated for the database. The default is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-maxmemory ``max_memory`                                                 | Specify the maximum memory, in MB, to be allocated for the resource. If you specify `-memorytarget` but not `-maxmemory`, then `-maxmemory` will be the default value of 0. Both `-maxmemory` and `-memorytarget` are validated as long as `-memorytarget` is less than or equal to `-maxmemory`.                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-cpucap ``cpu_cap`                                                       | Specify a percentage from 1 to 100 that is the maximum utilization of the workload CPUs the database requires. The default is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-defaultnetnum ``network_number`                                         | Specify a network number (an integer) to which services will default in the event you do not specify a network number when you add the service. The number must match the value of the `-netnum` parameter you specified when you added the network.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

##### Examples

An example of this command to add a policy-managed Oracle RAC database is:

    $ srvctl add database -db crm -oraclehome /u01/oracle/product/12c/mydb
        -domain example.com -spfile +diskgroup1/crm/spfilecrm.ora
        -role PHYSICAL_STANDBY -startoption MOUNT -dbtype RAC -dbname crm_psd
        -policy MANUAL -serverpool "svrpool1,svrpool2" -diskgroup "dgrp1,dgrp2"

An example of this command to add an administrator-managed database is:

    $ srvctl add database -db crm -oraclehome /u01/oracle/product/12c/mydb
    -domain example.com

#### srvctl config database

Displays the configuration for an Oracle RAC database or lists all configured databases that are registered with Oracle Clusterware.

##### Syntax

    srvctl config database [-db db_unique_name] [-all] [-verbose]

##### Parameters

Table A-6 srvctl config database Command Parameters

| Parameter            | Description                                                                                                                                |
|:---------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `-db db_unique_name` | Unique name for the database. If you do not specify this parameter, then the utility displays the configuration of all database resources. |
| `-all`               | Print detailed configuration information.                                                                                                  |
| `-verbose`           | Display verbose output.                                                                                                                    |

##### Example

This command returns output similar to the following:

    $ srvctl config database -d main4

    Database unique name: main
    Database name:
    Oracle home: /ade/mjkeenan_main4/oracle
    Oracle user: mjkeenan
    Spfile:
    Password file:
    Domain:
    Start options: open
    Stop options: immediate
    Database role: PRIMARY
    Management policy: AUTOMATIC
    Server pools:
    Disk Groups:
    Mount point paths:
    Services: test
    Type: RAC
    Start concurrency:
    Stop concurrency:
    OSDBA group: dba
    OSOPER group: oper
    Database instances: main41,main42
    Configured nodes: mjkeenan_main4_0,mjkeenan_main4_1
    CSS critical: no
    CPU count: 0
    Memory target : 0
    Maximum memory: 0
    CPU cap: 0
    Database is administrator managed

#### srvctl convert database

Converts a database either to or from an Oracle RAC One Node database.

##### Syntax

Use this command with one of the following syntax models:

    srvctl convert database -db db_unique_name -dbtype RACONENODE
       [-instance instance_name] [-timeout timeout]

    srvctl convert database -db db_unique_name -dbtype RAC [-node node_name]

##### Parameters

Table A-7 srvctl convert database Command Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`      | Specify the unique name for the database.<br>Note: If you specify a noncluster database, then command returns an error instructing you to use `rconfig` to convert the noncluster database to Oracle RAC or Oracle RAC One Node.                                                                                                                                                                                                                                         |
| `-dbtype RACONENODE | RAC`  | Specify the type of database to which you are converting, either Oracle RAC One Node or Oracle RAC.<br>Note: If there is an ongoing or failed online database relocation, then the command returns an error instructing you to first complete or abort the online database relocation and then rerun the command.                                                                                                                                                        |
| `-instance ``instance_name` | Optionally, you can specify an instance name prefix for Oracle RAC One Node databases. The default value for this parameter is the first 12 characters of the global unique name of the database.<br>Notes:<br>• You can use this parameter only when converting from an Oracle RAC database to an Oracle RAC One Node database.<br>• In order for the converted instance to come online, you must restart the database using the `srvctl stop/start database` commands. |
| `-timeout ``timeout`        | Optionally, you can specify online database relocation timeout, in minutes, for Oracle RAC One Node databases. The default is `30`.                                                                                                                                                                                                                                                                                                                                      |
| `-node ``node_name`         | Optionally, you can specify the name of the node for an administrator-managed Oracle RAC database. The default is the first candidate.<br>Note: If you do not specify a node name or you specify a node name where the database is not running, then the command returns an error instructing you specify the correct node.                                                                                                                                              |

##### Example

An example of this command is:

    $ srvctl convert database -db myDB -dbtype RACONENODE -instance myDB3

#### srvctl disable database

Disables a running database.

If the database is a cluster database, then its instances are also disabled.

##### Syntax

    srvctl disable database -db db_unique_name [-node node_name]

##### Parameters

Table A-8 srvctl disable database Command Parameters

| Parameter              | Description                                                                                                                                          |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name` | Specify the name of the database you want to disable.                                                                                                |
| `-node ``node_name`    | Optionally, you can specify a node on which you want to disable the database.<br>Note: You can only use this parameter only with Oracle Clusterware. |

##### Example

The following example disables the database `mydb1`:

    $ srvctl disable database -db mydb1

#### srvctl downgrade database

Downgrades the configuration of a database and its services from its current version to a specific lower version.

##### Syntax

    srvctl downgrade database -db db_unique_name -oraclehome Oracle_home
      -targetversion to_version

##### Parameters

Table A-9 srvctl downgrade database Command Parameters

| Parameter                     | Description                                                    |
|:------------------------------|:---------------------------------------------------------------|
| `-db ``db_unique_name`        | Specify the unique name of the database you want to downgrade. |
| `-oraclehome ``Oracle_home`   | Specify the path to the Oracle home.                           |
| `-targetversion ``to_version` | Specify the database version to which you want to downgrade.   |

#### srvctl enable database

Enables a cluster database and its instances.

##### Syntax

    srvctl enable database -db db_unique_name [-node node_name]

##### Parameters

Table A-10 srvctl enable database Command Parameters

| Parameter              | Description                                                                                                                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name` | Specify the unique name of the database you want to enable.                                                                                                                        |
| `-node ``node_name`    | Optionally, you can specify the name of the node on which the database resource resides that you want to enable.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Example

The following example enables a database named `mydb1`:

    $ srvctl enable database -db mydb1

#### srvctl getenv database

Displays the values for environment variables associated with a database.

##### Syntax

    srvctl getenv database -db db_unique_name [-envs "name_list"]

##### Parameters

Table A-11 srvctl getenv database Command Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                           |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`  | Specify the unique name of the database for which you want to display the environment variable values.                                                                                                                                                                                                                |
| `-envs "``name_list``"` | Optionally, you can specify a comma-delimited list of the names of specific environment variables enclosed in double quotation marks (`""`) for which you want to display the values.<br>If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the database. |

##### Example

The following example displays the environment configuration for a database named `crm`:

    $ srvctl getenv database -db crm

#### srvctl modify database

Modifies the configuration for a database.

##### Syntax

    srvctl modify database -db db_unique_name [-dbname db_name]
         [-instance instance_name] [-oraclehome oracle_home] [-user user_name]
         [-server "server_list"] [-timeout timeout] [-domain db_domain]
         [-spfile spfile] [-pwfile password_file_path]
         [-role {PRIMARY|PHYSICAL_STANDBY|LOGICAL_STANDBY|SNAPSHOT_STANDBY}]
         [-startoption start_options] [-stopoption stop_options]
         [-startconcurrency start_concurrency] [-stopconcurrency stop_concurrency]
         [-policy {AUTOMATIC | MANUAL | NORESTART | USERONLY}]
         [-serverpool "server_pool_name"] [-node node_list]
         [-pqpool pq_server_pool] [{-diskgroup "diskgroup_list" | -nodiskgroup}]
         [-acfspath "acfs_path_list"] [-css_critical {yes | no}]
         [-cpucount cpu_count [-overridepools overridepool_list]]
         [-memorytarget memory_target] [-maxmemory max_memory]
         [-defaultnetnum network_number] [-disabledreason {DECOMMISSIONED}]
         [-force] [-eval] [-verbose]

##### Parameters

Table A-12 srvctl modify database Command Parameters

| Parameter                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:--------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                                    | Unique name for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-dbname ``db_name`                                                       | The name of the database, if it is different from the unique name given by the `-db` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-instance ``instance_name`                                               | Instance name prefix; this parameter is required for administrator-managed Oracle RAC One Node databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-oraclehome ``oracle_home`                                               | The path for the Oracle database home directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-user ``user_name`                                                       | The name of the user that owns the Oracle home directory.<br>Note: If you specify the `-user`parameter, then you must run this command in privileged mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-server ``server_list`                                                   | List candidate servers for Oracle RAC One Node databases.<br>Note: You can use this parameter only with administrator-managed Oracle RAC One Node databases. If your Oracle RAC One Node database is policy managed, you cannot use this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-timeout ``timeout`                                                      | Online database relocation timeout, in minutes, for Oracle RAC One Node databases. The default is `30`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-domain ``db_domain`                                                     | The domain for the database.<br>Note: You must use this parameter if you set the `DB_DOMAIN` initialization parameter for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-spfile ``spfile`                                                        | The path name of the database server parameter file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-pwfile ``password_file_path`                                            | Enter the full path to the location of the password file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-role {PRIMARY | PHYSICAL_STANDBY | LOGICAL_STANDBY | SNAPSHOT_STANDBY}` | The role of the database in an Oracle Data Guard configuration. The default is `PRIMARY`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-startoption ``start_options`                                            | Startup options for the database, such as `OPEN`, `MOUNT`, and `NOMOUNT`. The default value is `OPEN`.<br>Notes:<br>• For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>• When performing a switch-over in an Oracle Data Guard configuration, the `-startoption` for a standby database that becomes a primary database is always set to `OPEN` after the switchover.                                                                                                                                                                                                                                                                                                                                                                   |
| `-stopoption ``stop_options`                                              | Stop options for the database, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, and `ABORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-startconcurrency ``start_concurrency`                                   | Number of instances to be started simultaneously, or 0 to disable this option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-stopconcurrency ``stop_concurrency`                                     | Number of instances to be stopped simultaneously, or 0 to disable this option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-policy {AUTOMATIC | MANUAL | NORESTART | USERONLY}`                     | Management policy for the database.<br>• `AUTOMATIC` (default): The database is automatically restored to its previous running condition (started or stopped) upon restart of the database host computer.<br>• `MANUAL`: The database is never automatically restarted upon restart of the database host computer. A `MANUAL` setting does not prevent Oracle Clusterware from monitoring the database while it is running and restarting it if a failure occurs.<br>• `NORESTART`: Similar to the `MANUAL` setting, the database is never automatically restarted upon restart of the database host computer. A `NORESTART` setting, however, never restarts the database even if a failure occurs.<br>• `USERONLY`: The database can only be restarted by user command, not as a result of any other reason (auto-start, start by dependency, node failure, and so on.) |
| `-serverpool "``server_pool_name``"`                                      | Specify the name of a server pool used to control database placement. If you do not specify this parameter, then it defaults to the Generic server pool.<br>Notes:<br>• This parameter can only be used with Oracle Clusterware. You can use this parameter with the `-node` parameter but the server pool must have `MAX_SIZE=1` and exactly one configured server (the one you specify in `-node`).<br>• After you add server pools, you can assign services to them using the `srvctl add service` command.                                                                                                                                                                                                                                                                                                                                                            |
| `-node ``node_list`                                                       | Specify a single node name or a comma-delimited list of node names on which you want to modify configuration of a noncluster, or single instance, Oracle database. Starting with Oracle Database 19c Release Update (19.7), you can modify a Standard Edition High Availability database configuration on multiple cluster nodes.<br>Note: While modifying an Oracle RAC One Node database, this parameter can be used only with the `-serverpool` parameter.                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-pqpool "``pq_pool_list``"`                                              | Comma separated list of parallel query server pool names<br>Note: This parameter can be used only with Oracle Clusterware and with the policy-managed databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-diskgroup "``disk_group_list``"`                                        | Comma-delimited list of Oracle ASM disk groups if database uses Oracle ASM storage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-acfspath "``acfs_path_list``"`                                          | A single Oracle ACFS path or a comma-delimited list of Oracle ACFS paths enclosed in double quotation marks (`""`) where the database's dependency is set.<br>Use this parameter to create dependencies on Oracle ACFS file systems other than `ORACLE_HOME`, such as for when the database uses `ORACLE_BASE` on a file system that is different from the `ORACLE_HOME` file system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-css_critical {YES | NO}`                                                | You can add weight to a service by setting this parameter to `YES`. In the event of a node failure within the cluster, Oracle Clusterware will evict the node with the least amount of weight, ensuring that critical services remain available.<br>Note: You can use this parameter only on an administrator-managed node. Should the node become policy managed, at some point, this parameter will no longer apply.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-cpucount ``cpu_count`` [-overridepools ``overridepool_list``]`          | Specify the number of CPUs. The default value is 0. Use the `-overridepools` option to specify the CPU count for specific server pools.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-memorytarget ``memory_target`                                           | Specify the target memory, in MB, to be allocated for the database. The default is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-maxmemory ``max_memory`                                                 | Specify the maximum memory, in MB, to be allocated for the resource. If you specify `-memorytarget` but not `-maxmemory`, then `-maxmemory` will be the default value of 0. Both `-maxmemory` and `-memorytarget` are validated as long as `-memorytarget` is less than or equal to `-maxmemory`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-defaultnetnum ``network_number`                                         | Specify a network number to which services will default in the event you do not specify a network number when you add a service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-disabledreason {DECOMMISSIONED}`                                        | Marks the database as being decommissioned, which means it cannot be started again and is not being used. This is intended for databases that will be deleted at a future date.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-eval`                                                                   | Use this parameter to hypothetically evaluate the impact of the command on the system.<br>Note: You can only use this parameter with a policy-managed database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

##### Usage Notes

- The `srvctl modify database` command can convert administrator-managed databases to policy-managed databases. For a running administrator-managed database, if the server list is supplied, then the node where the database is running must be on that list. The instance name prefix cannot be modified after running the `srvctl add database` command.

- You cannot change the management policy from `AUTOMATIC` (using the `-policy` parameter) for Oracle RAC One Node databases. Any attempt to do so results in an error message. The same is true for the `-node` parameter, which is used to change the node on which a non-cluster database runs.

- For policy-managed Oracle RAC One Node databases, you can use the `-serverpool` parameter to move an Oracle RAC One Node database between server pools but you can only specify one server pool. Specifying a list of server pools returns an error.

##### Examples

The following example changes the role of a database to a logical standby:

    $ srvctl modify database -db crm -role logical_standby

The following example directs the `racTest` database to use the `SYSFILES`, `LOGS`, and `OLTP` Oracle ASM disk groups:

    $ srvctl modify database -db racTest -diskgroup "SYSFILES,LOGS,OLTP"

**Related Topics**

- [Oracle Data Guard Configurations](../sbydb/introduction-to-oracle-data-guard-concepts.md)
- [Database Startup](../sqpug/database-administration-with-SQL-Plus.md)
- [Database Shutdown](../sqpug/database-administration-with-SQL-Plus.md)

#### srvctl predict database

Predicts the consequences of the failure of a specific database.

##### Syntax

    srvctl predict database -db db_unique_name [-verbose]

##### Usage Notes

- Specify the unique name of the database you want to check.

- Optionally, you can use the `–verbose` parameter to display detailed output.

#### srvctl relocate database

Initiates the relocation of an Oracle RAC One Node database from one node to another node.

This command also cleans up after a failed relocation, and you can only use it for relocating Oracle RAC One Node databases.

##### Syntax

Use this command with one of the following syntax models:

To initiate the online relocation of an Oracle RAC One Node database:

    srvctl relocate database -db db_unique_name [-node target_node] [-timeout timeout]
       [-stopoption NORMAL] [-drain_timeout drain_timeout] [-verbose]

To abort the failed online relocation of an Oracle RAC One Node database:

    srvctl relocate database -db db_unique_name -abort [-revert]
       [-drain_timeout drain_timeout] [-verbose]

##### Parameters

Table A-13 srvctl relocate database Command Parameters

| Parameter                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`     | Specify the unique name of the database you want to relocate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-node ``target_node`      | Optionally, you can specify a target node to which to relocate the Oracle RAC One Node database.<br>Note: You must use this parameter if you are relocating an administrator-managed Oracle RAC One Node database.                                                                                                                                                                                                                                                                                                                                             |
| `-timeout ``timeout`       | Optionally, you can specify an online database relocation timeout, in minutes, for Oracle RAC One Node databases. The default is `30`.                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-stopoption NORMAL`       | Use this parameter to override the default shutdown option for a running instance, such as the default of `SHUTDOWN TRANSACTIONAL LOCAL` for a primary database or `SHUTDOWN IMMEDIATE` for a standby database. The only value accepted for `-stopoption` is `NORMAL`.                                                                                                                                                                                                                                                                                         |
| `–abort`                   | Use this parameter to abort a failed online database relocation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `–revert`                  | Use this parameter to remove the target node of a failed online relocation request from the candidate server list of an administrator-managed Oracle RAC One Node database.                                                                                                                                                                                                                                                                                                                                                                                    |
| `-drain_timeout ``timeout` | Specify the time, in seconds, allowed for resource draining to be completed. Accepted values are an empty string (""), 0, or any positive integer. The default value is an empty string, which means that this parameter is not set. If it is set to 0, then draining occurs, immediately.<br>The draining period is intended for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. When set on the service this value is used when the command line value is not set. |
| `–verbose`                 | Use this parameter to display verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

##### Usage Notes

- If the Oracle RAC One Node database you want to relocate is not running, then the command returns an error.

- If another online database relocation is active for this Oracle RAC One Node database, then the command returns an error.

- If an online database relocation for this Oracle RAC One Node database has failed and the target nodes are not the same for either relocation, then the command returns an error instructing you to abort the failed online database relocation and then initiate a new one.

- If an online database relocation for this Oracle RAC One Node database has failed and the target nodes are the same (or you do not specify the target), then the command attempts to relocate the database.

##### Example

The following example relocates an administrator-managed Oracle RAC One Node database named `rac1` to a server called `node7`.

    $ srvctl relocate database -db rac1 -node node7

#### srvctl remove database

Removes database configurations.

After running this command, ensure that the password file is in the default location if you want to connect to the database as the SYS user with the SYS user's password.

##### Syntax

    srvctl remove database -db db_unique_name [-force] [-noprompt] [-verbose]

##### Parameters

Table A-14 srvctl remove database Command Parameters

| Parameter                    | Description                                               |
|:-----------------------------|:----------------------------------------------------------|
| `-database ``db_unique_name` | Unique name for the database.                             |
| `-force`                     | Forcibly remove the database and ignore any dependencies. |
| `-noprompt`                  | Suppress prompts.                                         |
| `-verbose`                   | Display verbose output.                                   |

##### Example

To remove a database named `crm`:

    $ srvctl remove database -db crm

#### srvctl setenv database

Administers cluster database environment configurations.

##### Syntax

Use this command with one of the following syntax models:

    srvctl setenv database -db db_unique_name -envs "name=val[,...]"

    srvctl setenv database -db db_unique_name -env "name=val"

##### Parameters

Table A-15 srvctl setenv database Command Parameters

| Parameter                        | Description                                                                                                                                                       |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`           | Specify a unique name for the database for which you want to set environment variables.                                                                           |
| `-envs "``name``=``val``[,...]"` | Specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`) that you want to set.                       |
| `-env "``name``=``val``"`        | Specify a single environment variable that you want to set to a value that contains commas or other special characters enclosed in double quotation marks (`""`). |

##### Usage Notes

Add additional information about the command here.

##### Example

The following example sets the language environment variable for a cluster database:

    $ srvctl setenv database -db crm -env LANG=en

#### srvctl start database

Starts a database and its enabled instances, and all listeners on nodes with database instances.

You can disable listeners that you do not want to start.

##### Syntax

    srvctl start database -db db_unique_name [-eval] [-startoption start_options]
      [-startconcurrency number_of_instances] [-node node_name]

##### Parameters

Table A-16 srvctl start database Command Parameters

| Parameter                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                    | Specify the unique name of the database you want to start.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `–eval`                                   | Optionally, use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-startoption ``start_options`            | Optionally, you can set options for the startup command (for example: `OPEN`, `MOUNT`, or `NOMOUNT`).<br>Notes:<br>• This command parameter supports all database startup options.<br>• For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>• See Also: [SQL\*Plus User's Guide and Reference](../sqpug/STARTUP.md) for more information about startup options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-startconcurrency ``number_of_instances` | Optionally, you can specify a number of database instances to start simultaneously, or specify `0` for an empty start concurrency value. When you use this parameter with the `srvctl start database` command, it overrides any `-startconcurrency` value configured using the `srvctl add | modify database` commands.<br>**Note:**<br>If the value for the `-startconcurrency` parameter is greater than the number of total instances, then this parameter does not have any effect, same as `0`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-node ``node_name`                       | Optionally, you can specify the name of a node on which you want to start the database.<br>Notes:<br>• This command only applies to Oracle RAC One Node and Standard Edition High Availability databases.<br>• The node you specify must be in the candidate list for an administrator-managed Oracle RAC One Node or Standard Edition High Availability database. The node must be in the server pool for a policy-managed Oracle RAC One Node database.<br>• If the database is already running on a node than the one you specify, then the command returns an error.<br>• If you do not specify a node, then Oracle Clusterware chooses which node on which to start the Oracle RAC One Node or Standard Edition High Availability database according to its policies, such as dispersion, number of resources, and order of candidate nodes.<br>• If there is an active online database relocation for the Oracle RAC One Node database you are attempting to start, then both instances will already be running and the command returns an error message. Only during an online database relocation are two instances of an Oracle RAC One Node database in existence.<br>• If the online database relocation failed for the Oracle RAC One Node database and you do not specify a node, then the command attempts to start both database instances.<br>• If the online database relocation failed for the Oracle RAC One Node database and you specify a node, then the command attempts to stop the failed relocation and start the instance on that node. |

##### Examples

The following example starts the `crm` database and sets the startup option to read only:

    $ srvctl start database -db crm -startoption "read only"

#### srvctl status database

This command displays the current state of the of the database.

##### Syntax

    srvctl status database {-db db_unique_name {[-serverpool serverpool_name]
       | [-sid] [-home]} | -serverpool serverpool_name | -thisversion | -thishome}
       [-force] [-detail] [-verbose]

##### Parameters

Table A-17 srvctl status database Parameters

| Parameter                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`          | Specify a unique name for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-serverpool ``serverpool_name` | Optionally, you can specify a server pool that SRVCTL will display information on nodes contained within.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `–sid`                          | Use this parameter to display the SID of the Oracle instance running on this node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `–home`                         | Use this parameter to display the Oracle home of the specified database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-thisversion`                  | Use this parameter to display the status of databases that are of the same Oracle product version as SRVCTL.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-thishome`                     | Use this parameter to display the status of databases that are configured in this Oracle home.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-force`                        | Include disabled applications                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `–detail`                       | Use this parameter to display detailed database status information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-verbose`                      | Displays `STATE_DETAILS` and `INTERNAL_STATE` attributes, which include `STABLE`, `STARTING`, `STOPPING`, and `CLEANING`.<br>If the `INTERNAL_STATE` is `STABLE`, then SRVCTL displays no additional information. If the `INTERNAL_STATE` is `STARTING`, then SRVCTL displays:<br>`Instance instance_name is being started`<br>If the `INTERNAL_STATE` is `CLEANING`, then SRVCTL displays:<br>`Instance instance_name is being cleaned up`<br>If the `INTERNAL_STATE` is `STOPPING`, then SRVCTL displays:<br>`Instance instance_name is being stopped` |

##### Usage Notes

The output of this command includes information on the Oracle ASM or Oracle ASM IOServer instance for each running instance of the database.

##### Examples

This command displays output similar to the following:

    $ srvctl status database -db db00 -detail

    Instance db00_1 is connected to ASM instance +ASM3
    Instance db00_2 is connected to ASM I/O server instance +IOS1

#### srvctl stop database

Stops a database, its instances, and its services.

##### Syntax

    srvctl stop database -db db_unique_name [-stopoption stop_options]
      [-stopconcurrency number_of_instances] [-drain_timeout timeout] [-eval]
      [-force] [-verbose]

##### Parameters

Table A-18 srvctl stop database Command Parameters

| Parameter                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                   | Specify the unique name for the database that you want to stop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-stopoption ``stop_options`             | Optionally, you can specify options for the shutdown command, such as `NORMAL`, `TRANSACTIONAL LOCAL`, `IMMEDIATE`, or `ABORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-stopconcurrency ``number_of_instances` | Optionally, you can specify a number of database instances to stop simultaneously, or specify `0` for an empty stop concurrency value. When you use this parameter with the `srvctl stop database` command, it overrides any `-stopconcurrency` value configured using the `srvctl add | modify database` commands.<br>**Note:**<br>If the value for the `-stopconcurrency` parameter is greater than the number of total instances, then this parameter does not have any effect, same as `0`.                                                                                                                                                                                                                                                                                          |
| `-drain_timeout ``timeout`               | Optionally, you can specify the time, in seconds, allowed to complete the resource draining action. By default, this parameter is not set. You can specify 0 or any positive integer. An empty string unsets the parameter. If you specify zero, then the agent will perform the actions related to service draining, immediately.<br>Drain timeout is the maximum time the service waits before exiting (in case of `srvctl stop service` or `srvctl stop instance`) or proceeding to stop database (`srvctl stop database`), until the draining of sessions is completed. If session draining completes in 10 seconds and the drain timeout value (on CLI or resource attribute) is 100 seconds, then SRVCTL moves on after 10 seconds. It does not wait for the remaining 90 seconds. |
| `-eval`                                  | Optionally, you can use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-force`                                 | Optionally, you can use this parameter to stop the database, its instances, its services, and any resources that depend on those services.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `—verbose`                               | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

##### Example

The following command example stops a database and includes detailed output:

    $ srvctl stop database -db db1 -drain_timeout 50 -verbose
    Draining in progress on services svc1,svc2.
    Drain complete on services svc1.
    Draining in progress on services svc2.
    Draining in progress on services svc2.
    Drain complete on services svc2.

#### srvctl unsetenv database

Unsets the cluster database environment configurations.

##### Syntax

    srvctl unsetenv database -db db_unique_name -envs "name_list"

##### Parameters

Table A-19 srvctl unsetenv database Command Parameters

| Parameter               | Description                                                                                             |
|:------------------------|:--------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`  | Specify the unique name of the database for which you want to unset environment variables.              |
| `-envs "``name_list``"` | Specify a comma-delimited list of environment variable names enclosed in double quotation marks (`""`). |

##### Example

The following example unsets two cluster database environment variables:

    $ srvctl unsetenv database -db crm -envs "CLASSPATH,LANG"

#### srvctl update database

Updates the specified database to use the new listener endpoints.

##### Syntax

    srvctl update database -db db_unique_name

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Specify the unique name of the database you want to update.

#### srvctl upgrade database

Upgrades the configuration of a database and all of its services to the version of the database home from where this command is run.

##### Syntax

    srvctl upgrade database -db db_unique_name -oraclehome Oracle_home

##### Parameters

Table A-20 srvctl upgrade database Command Parameters

| Parameter                   | Description                                                  |
|:----------------------------|:-------------------------------------------------------------|
| `-db ``db_unique_name`      | Specify the unique name of the database you want to upgrade. |
| `-oraclehome ``Oracle_home` | Specify the path to the upgraded `ORACLE_HOME`.              |

#### srvctl disable diskgroup

Disables a specific disk group on a number of specified nodes.

##### Syntax

    srvctl disable diskgroup -diskgroup diskgroup_name [-node "node_list"]

##### Parameters

Table A-21 srvctl disable diskgroup Command Parameters

| Parameter                     | Description                                                                                                                                                                                                      |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-diskgroup ``diskgroup_name` | Specify the name of the Oracle ASM disk group you want to disable.                                                                                                                                               |
| `-node "``node_list``"`       | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) on which to disable the disk group.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Example

The following example disables the Oracle ASM disk group, `dgroup1`, on two nodes in a cluster, `mynode1` and `mynode2`:

    $ srvctl disable diskgroup -diskgroup dgroup1 -node "mynode1,mynode2"

#### srvctl enable diskgroup

Enables a specific disk group on a number of specified nodes.

##### Syntax

    srvctl enable diskgroup -diskgroup diskgroup_name [-node "node_list"]

##### Parameters

Table A-22 srvctl enable diskgroup Command Parameters

| Parameter                     | Description                                                                                                                                                                                                     |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-diskgroup ``diskgroup_name` | Specify the name of the Oracle ASM disk group you want to enable.                                                                                                                                               |
| `-node "``node_list``"`       | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) on which to enable the disk group.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Example

The following example enables the `diskgroup1` Oracle ASM disk group on nodes `mynode1` and `mynode2`:

    $ srvctl enable diskgroup -diskgroup diskgroup1 -node "mynode1,mynode2"

#### srvctl predict diskgroup

Predicts the consequences of an Oracle ASM disk group failure.

##### Syntax

    srvctl predict diskgroup -diskgroup diskgroup_name [-verbose]

##### Usage Notes

Specify the name of the Oracle ASM disk group for which you want to evaluate a failure. Optionally, you can use the `–verbose` parameter top print detailed output.

#### srvctl remove diskgroup

Removes a specific Oracle ASM disk group resource from Oracle Clusterware or Oracle Restart.

##### Syntax

    srvctl remove diskgroup -diskgroup diskgroup_name [-force]

##### Usage Notes

Specify the name of the Oracle ASM disk group you want to remove. Optionally, you can use the `–force` parameter to ignore any dependencies and forcibly remove the disk group.

##### Example

The following example forcibly removes the `DG1` Oracle ASM disk group:

    $ srvctl remove diskgroup -diskgroup DG1 -force

#### srvctl start diskgroup

Starts a specific Oracle ASM disk group resource on a number of specified nodes.

##### Syntax

    srvctl start diskgroup -diskgroup diskgroup_name [-node "node_list"]

##### Parameters

Table A-23 srvctl start diskgroup Command Parameters

| Parameter                     | Description                                                                                                                                                                                                             |
|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-diskgroup ``diskgroup_name` | Specify the name of the Oracle ASM disk group you want to start.                                                                                                                                                        |
| `-node "``node_list``"`       | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) on which to start the disk group resource.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Example

The following example starts the `diskgroup1` Oracle ASM disk group on the nodes `mynode1` and `mynode2`:

    $ srvctl start diskgroup -diskgroup diskgroup1 -node "mynode1,mynode2"

#### srvctl status diskgroup

Displays the status of a specific disk group on a number of specified nodes.

##### Syntax

    srvctl status diskgroup -diskgroup diskgroup_name [-node "node_list"]
      [-detail] [-verbose]

##### Parameters

Table A-24 srvctl status diskgroup Command Parameters

| Parameter                     | Description                                                                                                                                                                              |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-diskgroup ``diskgroup_name` | Specify the name of the Oracle ASM disk group for which you want to display the status.                                                                                                  |
| `-node "``node_list``"`       | Optionally, you can specify a comma-delimited list of node names on which to check status of an Oracle ASM disk group.<br>Note: You can only use this parameter with Oracle Clusterware. |
| `-detail`                     | Optionally, you can use this parameter to display detailed status information for the Oracle ASM disk group.                                                                             |
| `-verbose`                    | Optionally, you can use this parameter to display verbose output.                                                                                                                        |

##### Examples

The following example displays the status of the `dgrp1` Oracle ASM disk group:

    $ srvctl status diskgroup -diskgroup dgrp1 -node "mynode1,mynode2" -detail

#### srvctl stop diskgroup

Stops a specific Oracle ASM disk group resource on a number of specified nodes.

##### Syntax

    srvctl stop diskgroup -diskgroup diskgroup_name [-node "node_list"] [-force]

##### Parameters

Table A-25 srvctl stop diskgroup Command Parameters

| Parameter                     | Description                                                                                                                                                                                                                       |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-diskgroup ``diskgroup_name` | Specify the name of the Oracle ASM disk group you want to stop.                                                                                                                                                                   |
| `-node "``node_list``"`       | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) on which to stop the Oracle ASM disk group resource.<br>Note: You can only use this parameter with Oracle Clusterware. |
| `-force`                      | Optionally, you can use this parameter to perform a forceful dismount. While this parameter does not stop the databases that depend on the disk group you are stopping, it still may cause those databases to fail.               |

##### Example

The following command stops the `diskgroup1` Oracle ASM disk group on the two nodes `mynode1` and `mynode2`:

    $ srvctl stop diskgroup -diskgroup diskgroup1 -node "mynode1,mynode2" -force

#### srvctl start home

Starts all the Oracle Restart-managed or Oracle Clusterware-managed resources on the specified Oracle home.

##### Syntax

    srvctl start home -oraclehome Oracle_home -statefile state_file -node node_name

##### Parameters

Table A-26 srvctl start home Command Parameters

| Parameter                   | Description                                                                                                                      |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `-oraclehome ``Oracle_home` | Specify the path to the Oracle home for which you want to start the Oracle Restart or Oracle Clusterware-managed resources.      |
| `-statefile ``state_file`   | Specify the path to the directory where you want SRVCTL to write the state file.                                                 |
| `-node ``node_name`         | Specify the name of the node on which the Oracle home resides.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Example

The following command starts an Oracle home:

    $ srvctl start home -oraclehome /u01/app/oracle/product/12.2.0/db_1
      -statefile ~/state.txt -node node1

#### srvctl status home

Displays the status of all the Oracle Restart-managed or Oracle Clusterware-managed resources for the specified Oracle home.

##### Syntax

    srvctl status home -oraclehome Oracle_home -statefile state_file -node node_name

##### Parameters

Table A-27 srvctl status home Command Parameters

| Parameter                   | Description                                                                                                                                         |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `-oraclehome ``Oracle_home` | Specify the path to the Oracle home for which you want to start the Oracle Restart or Oracle Clusterware-managed resources.                         |
| `-statefile ``state_file`   | Specify the path to the directory that contains the text file that holds the state information generated by this command.                           |
| `-node ``node_name`         | Specify the name of the node on which the Oracle home resides.<br>Note: This parameter is required and you can only use it with Oracle Clusterware. |

##### Example

The following example obtains the status of a particular Oracle home:

    $ srvctl status home -oraclehome /u01/app/oracle/product/12.1/dbhome_1 -statefile
     ~/state.txt -node stvm12

The preceding command returns output similar to the following:

    Database cdb1 is running on node stvm12

#### srvctl stop home

Stops all the Oracle Restart-managed or Oracle Clusterware-managed resources that run from the specified Oracle home.

##### Syntax

    srvctl stop home -oraclehome Oracle_home -statefile state_file -node node_name
      [-stopoption stop_options] [-force]

##### Parameters

Table A-28 srvctl stop home Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                      |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-oraclehome ``Oracle_home`  | Specify the directory path to the Oracle home for which you want to start the Oracle Restart or Oracle Clusterware-managed resources.<br>Note: The path to the Oracle home you specify must be the same version as the Oracle home from which you invoke SRVCTL. |
| `-statefile ``state_file`    | Specify the path to the directory where you want SRVCTL to write the state file.                                                                                                                                                                                 |
| `-node ``node_name`          | Specify the name of the node on which the Oracle home resides.<br>Note: You can only use this parameter with Oracle Clusterware.                                                                                                                                 |
| `-stopoption ``stop_options` | Optionally, you can specify shutdown options for the database, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, or `ABORT`<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/SHUTDOWN.md) for more information about shutdown options                  |
| `-force`                     | Optionally, you can use this parameter to stop the resources even if errors are reported.                                                                                                                                                                        |

##### Example

The following example stops the Oracle home:

    $ srvctl stop home -oraclehome /u01/app/oracle/product/12.1.0/db_1 -statefile
     ~/state.txt

#### srvctl add instance

Adds a configuration for an instance to your cluster database configuration.

You can only use this command for administrator-managed databases. If you have a policy-managed database, then use the `srvctl modify srvpool` command to add an instance to increase either the maximum size, minimum size, or both, of the server pool used by the database.

##### Syntax

    srvctl add instance -db db_unique_name -instance instance_name
         -node node_name [-force]

##### Parameters

Table A-29 srvctl add instance Command Parameters

| Parameter                   | Description                                                                              |
|:----------------------------|:-----------------------------------------------------------------------------------------|
| `-db ``db_unique_name`      | The unique name of the database you are adding the instance to                           |
| `-instance ``instance_name` | The name of the instance you are adding                                                  |
| `-node ``node_name`         | The name of the node on which you are creating the instance                              |
| `-force`                    | Optionally, you can force the add operation, even though some resources will be stopped. |

##### Usage Notes

- You can only use this command with Oracle Clusterware and Oracle RAC.

- This command increments the `CARDINALITY` resource attribute.

- If you attempt to use this command on an Oracle RAC One Node database, then the command returns an error stating you must convert the database to Oracle RAC.

##### Examples

Examples of this command are:

    $ srvctl add instance -db crm -instance crm01 -node gm01
    $ srvctl add instance -db crm -instance crm02 -node gm02
    $ srvctl add instance -db crm -instance crm03 -node gm03

#### srvctl disable instance

Disables a database instance.

If the database instance that you disable with this command is the last enabled database instance, then this operation also disables the database.

**Note:**

- This command is only available with Oracle Clusterware and Oracle RAC.

- If you run this command on an Oracle RAC One Node database, then the command returns an error instructing you to use the `database` noun, instead.

##### Syntax

    srvctl disable instance -db db_unique_name -instance "instance_name_list"

##### Parameters

Table A-30 srvctl disable instance Command Parameters

| Parameter                            | Description                                                                                                                         |
|:-------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`               | Specify the unique name for the database for which you want to disable the instance.                                                |
| `-instance "``instance_name_list``"` | Specify an instance name or a comma-delimited list of instance names enclosed in double quotation marks (`""`) you want to disable. |

##### Example

The following example disables two instances of the `crm` database, named `crm1` and `crm2`:

    $ srvctl disable instance -db crm -instance "crm1,crm3"

#### srvctl enable instance

Enables an instance of an Oracle RAC database.

If you use this command to enable all instances, then the database is also enabled.

**Note:**

- You can only use this command with Oracle Clusterware and Oracle RAC.

- If you run this command on an Oracle RAC One Node database, then the command returns an error instructing you to use the `database` noun, instead.

##### Syntax

    srvctl enable instance -db db_unique_name -instance "instance_name_list"

##### Parameters

Table A-31 srvctl enable instance Command Parameters

| Parameter                            | Description                                                                                                         |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`               | Specify the unique name of the database for which you want to enable instances.                                     |
| `-instance "``instance_name_list``"` | Specify a comma-delimited list of instance names enclosed in double quotation marks (`""`) that you want to enable. |

##### Example

The following example enables two instances of the `crm` database:

    $ srvctl enable instance -db crm -instance "crm1,crm2"

#### srvctl modify instance

For an administrator-managed database, this command modifies the configuration for a database instance from its current node to another node. For a policy-managed database, this command defines an instance name to use when the database runs on the specified node.

##### Syntax

    srvctl modify instance -db db_unique_name -instance instance_name
         -node node_name

##### Parameters

Table A-32 srvctl modify instance Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_unique_name` | Specify the unique name for the database.                                                                                                                                                                                                                                                                                                                                              |
| `-instance ``instance_name`  | Specify the database instance name.<br>Notes:<br>• If you are modifying a policy-managed database instance, then the instance name must contain an underscore (`_`), such as `pmdb1_1`.<br>• If you specify an instance name that has never been started before, and is not of the form `prefix_number`, then you may have to assign an instance number, undo, and redo in the SPFILE. |
| `-node ``node_name`          | Name of the node on which to run the instance. You can set the value of this parameter to `""` only for a policy-managed database.                                                                                                                                                                                                                                                     |

##### Usage Notes

You cannot use this command to rename or relocate a running instance.

##### Examples

The following example to changes the configuration of an administrator-managed database, `amdb`, so that the database instance, `amdb1`, runs on the specified node, `mynode`:

    $ srvctl modify instance -db amdb -instance amdb1 -node mynode

The following example causes the policy-managed database `pmdb`, when and if it runs on `mynode`, to use the instance name `pmdb1`:

    $ srvctl modify instance -db pmdb -instance pmdb1_1 -node mynode

The following example removes the directive established by the previous example:

    $ srvctl modify instance -db pmdb -instance pmdb1_1 -node ""

#### srvctl remove instance

Removes the configurations for an instance of an administrator-managed database.

To remove the configurations of a policy-managed database, you must shrink the size of the server pool with the `srvctl modify srvpool` command.

##### Syntax

    srvctl remove instance -db db_unique_name -instance instance_name
      [-noprompt] [-force]

##### Parameters

Table A-33 srvctl remove instance Command Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                             |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`      | Specify the unique name of the administrator-managed database.                                                                                                                                                                                                          |
| `-instance ``instance_name` | Specify the name of the Instance you want to remove.                                                                                                                                                                                                                    |
| `-noprompt`                 | Use this parameter to suppress prompts.                                                                                                                                                                                                                                 |
| `–force`                    | Use this parameter to skip checking that the instance is not running, and remove it even though it is running. This parameter also skips checking that the instance has no running services using it, and causes those services to stop before the instance is removed. |

##### Usage Notes

- You can use this command only with Oracle Clusterware and Oracle RAC.

- If you use the `-force` parameter, then any services running on the instance stop. Oracle recommends that you reconfigure services to not use the instance you want to removed as a preferred or available instance before removing the instance.

- If you attempt to use this command on an Oracle RAC One Node database, then the command returns an error stating that cannot remove the instance except by removing the database.

##### Example

The following example removes the `crm01` database instance from the `crm` database.

    $ srvctl remove instance -db crm -instance crm01

#### srvctl start instance

Starts instances in the cluster database.

Use the `srvctl start instance` command to start database instances, and all listeners on nodes with database instances

##### Syntax

Use the `srvctl start instance` command with one of these syntax models:

    srvctl start instance -db db_unique_name -node node_name
       [-instance "instance_name"] [-startoption start_options]

    srvctl start instance -db db_unique_name -instance "inst_name_list"
        [-startoption start_options]

##### Parameters

Table A-34 srvctl start instance Parameters

| Parameter                                                  | Description                                                                                                                                                                                                                                                  |
|:-----------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                     | Unique name for the database.                                                                                                                                                                                                                                |
| `-node ``node_name`                                        | The name of a single node.<br>Note: Use this parameter for policy-managed databases.                                                                                                                                                                         |
| `-instance { "``instance_name``" | "``inst_name``_list" }` | The name of a single instance or a comma-delimited list of instance names<br>Note: Use this parameter for administrator-managed databases.                                                                                                                   |
| `-startoption ``start_options`                             | Options for startup command, such as `OPEN`, `MOUNT`, or `NOMOUNT`)<br>Note: For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`. |

##### Usage Notes

- This command is only available with Oracle Clusterware and Oracle RAC.

- If you run this command on an Oracle RAC One Node database, then the command returns an error instructing you to use the `database` noun, instead.

**Related Topics**

- [SQL\*Plus User's Guide and Reference](../sqpug/STARTUP.md)

#### srvctl status instance

Displays the status of instances.

**Note:**

This command is only available with Oracle Clusterware and Oracle RAC.

#### srvctl stop instance

The `srvctl stop instance` command stops instances and stops any services running on specified instances.

##### Syntax

Use this command with one of the following syntax models.

To stop all instances on one or more nodes:

    srvctl stop instance -node "node_list" [-stopoption stop_options]
        [-drain_timeout timeout] [-force] [-failover] [-verbose]

To stop instances for a database that are running on specific nodes:

    srvctl stop instance -db db_unique_name -node "node_list"
        [-stopoption stop_options] [-drain_timeout timeout] [-force] [-failover] [-verbose]

To stop one or more instances by name for a database:

    srvctl stop instance -db db_unique_name -instance "instance_name_list"
        [-stopoption stop_options] [-drain_timeout timeout] [-force] [-failover] [-verbose]

##### Parameters

Table A-35 srvctl stop instance Command Parameters

| Parameter                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`               | Specify the unique name for the database for which you want to stop an instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-node "``node_list``"`              | Specify a comma-delimited list of node names enclosed in double quotation marks (`""`).<br>If you specify `-node` without specifying a value for `-db`, then all instances running on a node are stopped, regardless of which databases they are associated with.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-instance "``instance_name_list``"` | Specify a comma-delimited list of instance names enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-stopoption ``stop_options`         | Specify options for the shutdown command, such as `NORMAL`, `TRANSACTIONAL LOCAL`, `IMMEDIATE`, or `ABORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-drain_timeout ``timeout`           | The time, in seconds, allowed to complete the resource draining action. By default, this parameter is not set. You can specify 0 or any positive integer. An empty string unsets the parameter. If you specify zero, then the agent will perform the actions related to service draining, immediately.<br>Drain timeout is the maximum time the service waits before exiting (in case of `srvctl stop service` or `srvctl stop instance`) or proceeding to stop database (`srvctl stop database`), until the draining of sessions is completed. If session draining completes in 10 seconds and the drain timeout value (on CLI or resource attribute) is 100 seconds, then SRVCTL moves on after 10 seconds. It does not wait for the remaining 90 seconds. |
| `-force`                             | Use this parameter to forcibly stop the instance and any running services if the `srvctl stop instance` command fails with an error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `–failover`                          | If you specify `-failover`, then the services fail over to an available instance when the instance stops.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-verbose`                           | Display verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

If you run this command on an Oracle RAC One Node database, then the command returns an error instructing you to use the `srvctl stop database` command instead.

##### Example

The following command example stops the instance of the `db1` database running on the node `server1`, and includes verbose output:

    $ srvctl stop instance -db db1 -node server1 -drain_timeout 50 -verbose
    Draining in progress on services svc1
    Draining in progress on services svc1
    Drain complete on services svc1

**Related Topics**

- [Database Shutdown](../sqpug/database-administration-with-SQL-Plus.md)

#### srvctl update instance

The `srvctl update instance` command changes the open mode or the target Oracle ASM instance of the database instances.

##### Syntax

    srvctl update instance -db db_unique_name [-instance "instance_name_list"
        | -node "node_list"] [-startoption start_options] [-targetinstance instance_name]

##### Parameters

| Parameter                                                    | Description                                                                                                                                                                             |
|:-------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                       | The unique name of the database                                                                                                                                                         |
| `-instance "``instance_name_list``" | -node "``node_list``"` | A comma-delimited list of instance names or node names that you want to update. If you specify a list of node names, then SRVCTL udpates the instances running on those specific nodes. |
| `-startoption ``start_options`                               | The specify startup options for the database, such as `OPEN`, `MOUNT`, or `"READ ONLY"`                                                                                                 |
| `-targetinstance ``instance_name`                            | The target Oracle ASM or Oracle ASM IOServer instance. Use double quotation marks (`""`) with no space in-between to specify the default target instance.                               |

##### Examples

An example of this command is:

    $ srvctl update instance -db db00 -instance db00_3 -targetinstance +ASM2

#### srvctl add listener

Adds a listener to every node in a cluster.

##### Syntax

Use this command with one of the following syntax models.

To create an Oracle Database listener:

    srvctl add listener [-listener listener_name] [-netnum network_number] [-oraclehome Oracle_home]
      [-user user_name] [-endpoints "[TCP:]port_list[:FIREWALL={ON|OFF}][/IPC:key][/NMP:pipe_name]
      [/{TCPS|SDP|EXADIRECT}port_list[:FIREWALL={ON|OFF}]]" [-group group_name]] [-invitednodes "node_list"]
      [-invitedsubnets "subnet_list"] [-skip]

To create an Oracle ASM listener:

    srvctl add listener [-listener listener_name] -asmlistener [-subnet subnet]
      [-endpoints "[TCP:]port_list[:FIREWALL={ON|OFF}][/IPC:key][/NMP:pipe_name]
      [/{TCPS|SDP|EXADIRECT}port_list[:FIREWALL={ON|OFF}]]" [-group group_name]] [-invitednodes "node_list"]
      [-invitedsubnets "subnet_list"] [-skip]

To create a SCAN listener, use the `srvctl add scan_listener` command.

##### Parameters

Table A-36 srvctl add listener Command Parameters

| Parameter                                                                                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:---------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name`                                                                                                                        | Specify a listener name. This parameter is optional.<br>If you do not specify this parameter, then the name of the listener defaults to `LISTENER` for a database listener or `LISTENER_ASM` for an Oracle ASM listener.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-netnum ``network_number`                                                                                                                         | The optional network number from which VIPs are obtained. If not specified, the VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained.<br>Note: Use this parameter when you add an Oracle Database listener.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-oraclehome ``oracle_home`                                                                                                                        | Specify an Oracle home for the cluster database. If you do not include this parameter, then SRVCTL uses the Grid home by default.<br>Note: Use this parameter when you add an Oracle Database listener.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-user ``user_name`                                                                                                                                | Use this parameter to set the user that will run the listener to a less privileged user. Oracle recommends using this parameter to increase security.<br>Notes:<br>• You must be logged in as `root` to run this command and specify the `-user` parameter.<br>• Use this parameter when you add an Oracle Database listener.<br>• When you use the `-user` parameter, ensure the following:<br>• The listener log directory in the Oracle Base directory and the `Grid_home``/network/admin/``user_name` directory must both exist on each node before you can use this parameter. Additionally, `user_name` must have read, write, and execute permission in the directory.<br>• The `Oracle_Base``/diag/tnslsnr/``host_name``/``lower_case_listener_name` directory exists and `user_name` has read, write, and execute permission on it.<br>• Before you can use LSNRCTL to manage a listener, you must set `TNS_ADMIN` to `Grid_home``/network/admin/``user_name`. |
| `-endpoints "[TCP:]``port_list``[:FIREWALL={ON|OFF}][/IPC:``key``] [/NMP:``pipe_name``][/{TCPS|SDP|EXADIRECT}``port_list``[:FIREWALL={ON|OFF}]]"]` | Protocol specifications for the listener. Use `port_list` to specify a comma-delimited list of TCP ports or listener endpoints.<br>If you do not specify the `-endpoints` parameter for an Oracle Database listener, then SRVCTL searches for a free port between 1521 and 1540.<br>You can also specify endpoints for TCPS, SDP, and EXADIRECT ports.<br>Note: You can modify this attribute using Online Resource Attribute Modification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-group ``group_name`                                                                                                                              | Optionally, you can use the `-group` parameter with `-endpoints` to specify a group for the secure endpoint. This parameter is used for the EXADIRECT protocol on Exadata and Exalogic systems.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-invitednodes "``node_list``"`                                                                                                                    | Specify a comma-delimited list of node names allowed to register with the listener.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-invitedsubnets "``subnet_list``"`                                                                                                                | Specify a comma-delimited list of subnets allowed to register with the listener.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-skip`                                                                                                                                            | Indicates you want to skip the checking of ports.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-asmlistener`                                                                                                                                     | Specifies the listener type as an Oracle ASM listener. If you do not specify the `-listener` parameter, then the name of the Oracle ASM listener defaults to `LISTENER_ASM`.<br>Note: You can only use this parameter with Oracle Clusterware.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-subnet ``subnet`                                                                                                                                 | Specifies the subnet to use for an Oracle ASM listener.<br>Note: You can only use this parameter with Oracle Clusterware.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms when you specify the `-user` parameter.

##### Example

The following command adds a listener named `listener112` that is listening on ports 1341, 1342, and 1345 and runs from the Oracle home directory on every node in the cluster.

    $ srvctl add listener -listener listener112 -endpoints "1341,1342,1345"
    -oraclehome /u01/app/oracle/product/12.2.0/db1

When a listener is configured in the Oracle RAC home instead of the Grid home, then the `listener.ora` file is created under the location returned by the `$ORACLE_HOME/bin/orabasehome` utility, in the subdirectory `network/admin`, for example, `/u02/racbase/homes/OraDB20Home1/network/admin`.

#### srvctl config listener

Displays configuration information of a specific listener that is registered with Oracle Clusterware.

##### Syntax

    srvctl config listener [-listener listener_name | -asmlistener] [-all]

##### Parameters

Table A-37 srvctl config listener Command Parameters

| Parameter                                    | Description                                                                                                                                                                                   |
|:---------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name`` | -asmlistener` | The name of a specific listener name or the type of listener (Oracle ASM).<br>If you do not specify this parameter, then SRVCTL displays the configuration for the default database listener. |
| `-all`                                       | Print detailed configuration information.                                                                                                                                                     |

##### Example

This command returns output similar to the following:

    Name: LISTENER
    Subnet: 10.100.200.195
    Type: type
    Owner: scott
    Home: Grid_home
    End points: TCP:1521

#### srvctl disable listener

Disables a listener resource.

##### Syntax

    srvctl disable listener [-listener listener_name] [-node node_name]

##### Parameters

Table A-38 srvctl disable listener Command Parameters

| Parameter                   | Description                                                                                                                                                                              |
|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify the name of a particular listener resource. If you do not specify this parameter, then the name of the listener defaults to `LISTENER`.                      |
| `-node ``node_name`         | Optionally, you can specify the name of a cluster node on which the listener resource you want to disable is running.<br>Note: This parameter is only available with Oracle Clusterware. |

##### Example

The following example disables a listener resource named `listener_crm` on the node `node5`:

    $ srvctl disable listener -listener listener_crm -node node5

#### srvctl enable listener

Enables a listener resource.

##### Syntax

    srvctl enable listener [-listener listener_name] [-node node_name]

##### Parameters

Table A-39 srvctl enable listener Command Parameters

| Parameter                   | Description                                                                                                                                               |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify the name of a listener resource. If you do not use this parameter, then the name of the listener defaults to `LISTENER`.      |
| `-node ``node_name`         | Optionally, you can specify the name of a cluster node on which to enable the listener.<br>Note: You can only use this parameter with Oracle Clusterware. |

##### Examples

The following example enables the listener named `listener_crm` on the node named `node5`:

    $ srvctl enable listener -listener listener_crm -node node5

#### srvctl getenv listener

Displays the environment variables for the specified listener.

##### Syntax

    srvctl getenv listener [-listener listener_name] [-envs "name_list"]

##### Parameters

Table A-40 srvctl getenv listener Command Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                         |
|:----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify a listener name for which you want to obtain the environment variables.<br>If you do not use this parameter, then the name of the listener defaults to `LISTENER`.                                                                      |
| `-envs "``name_list``"`     | Optionally, you can specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).<br>If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the listener. |

##### Example

The following example lists all environment variables specified for the default listener:

    $ srvctl getenv listener

#### srvctl modify listener

Changes several aspects of the listener

Changes the Oracle home directory from which the listener runs, the name of the operating system user who owns Oracle home directory from which the listener runs, the listener endpoints, or the public subnet on which the listener listens, either for the default listener, or a specific listener, that is registered with Oracle Restart or with Oracle Clusterware.

If you want to change the name of a listener, then use the `srvctl remove listener` and `srvctl add listener` commands.

##### Syntax

    srvctl modify listener [-listener listener_name] [-oraclehome oracle_home]
     [-endpoints "[TCP:]port_list[:FIREWALL={ON|OFF}][/IPC:key][/NMP:pipe_name]
     [/{TCPS|SDP|EXADIRECT}port_list[:FIREWALL={ON|OFF}]]"] [-group <group>]
     [-user user_name] [-netnum network_number]

##### Parameters

Table A-41 srvctl modify listener Command Parameters

| Parameter                                                                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name`                                                                                                                      | Optionally, you can enter the name of the listener you want to modify.<br>If you do not use this parameter, then SRVCTL uses the default name, `LISTENER`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-oraclehome ``oracle_home`                                                                                                                      | If you choose to use this parameter, then SRVCTL moves the listener to run from the Oracle home you specify.<br>Note: When you use this parameter, run the command as a privileged user to enable SRVCTL to update resource ownership corresponding to the new `ORACLE_HOME` owner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-endpoints "[TCP:]``port_list``[:FIREWALL={ON|OFF}][/IPC:``key``][/NMP:``pipe_name``][/{TCPS|SDP|EXADIRECT}``port_list``[:FIREWALL={ON|OFF}]]"` | Optionally, you can use this parameter to modify protocol specifications for the listener. You must enclose the string of protocols in double quotation marks (`""`).<br>`port_list` is comma-delimited list of port numbers.<br>You can also modify endpoints for TCPS, SDP, and EXADIRECT ports.<br>Note: You can modify this attribute using Online Resource Attribute Modification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-group ``group_name`                                                                                                                            | Optionally, you can use the `-group` parameter with `-endpoints` to specify a group for the secure endpoint. This parameter is used for the EXADIRECT protocol on Exadata and Exalogic systems.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-user ``user_name`                                                                                                                              | Optionally, you can specify the name of the operating system user who will own the specified Oracle listener<br>Notes:<br>• You can only use this parameter with Oracle Clusterware.<br>• You must be logged in as `root` to run this command and specify the `-user` parameter.<br>• When you use the `-user` parameter, ensure the following:<br>• The listener log directory in `ORACLE_BASE` and the `Grid_home``/network/admin/``user_name` directory must both exist on each node before you can use this parameter. Additionally, `user_name` must have read, write, and execute permission in the directory.<br>• The `$ORACLE_BASE/diag/tnslsnr/``host_name``/``lower_case_listener_name` directory exists and `user_name` has read, write, and execute permission on it.<br>• Before you can use LSNRCTL to manage a listener, you must set `TNS_ADMIN` to `Grid_home``/network/admin/``user_name`. |
| `-netnum ``network_number`                                                                                                                       | Optionally, you can use this parameter to change the public subnet on which the listener listens.<br>Note: Oracle recommends that you always have at least one listener on the default network. Do not use this parameter to change the network of the only listener that listens on the default network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

##### Example

The following example changes the TCP ports for the default listener:

    $ srvctl modify listener -endpoints "TCP:1521,1522"

#### srvctl predict listener

Predicts the consequences of a listener failure.

##### Syntax

    srvctl predict listener listener_name [-verbose]

##### Usage Notes

Specify the name of the listener for which you want to predict the consequences of a failure. Optionally, you can use the `–verbose parameter` for detailed output.

#### srvctl remove listener

Removes the configuration of a specific listener, or all listeners, from Oracle Clusterware or Oracle Restart.

##### Syntax

    srvctl remove listener [-listener listener_name | -all] [-force]

##### Usage Notes

- Optionally, you can specify the name of a listener that you want to remove or use the `–all` parameter to remove all listeners. If you do not specify a listener name, then the listener name defaults to `LISTENER` for a database listener or `LISTENER_ASM` for an Oracle ASM listener.

- Optionally, you can use the `–force` parameter to skip checking whether there are other resources that depend on this listener, such as databases, and remove the listener anyway.

##### Example

The following example removes the configuration for the listener named `lsnr01`:

    $ srvctl remove listener -listener lsnr01

#### srvctl setenv listener

Administers listener environment configurations.

##### Syntax

Use this command with one of the following syntax models:

    srvctl setenv listener [-listener listener_name] -envs "name=val[,...]"

    srvctl setenv listener [-listener listener_name] -env "name=val"

##### Parameters

Table A-42 srvctl setenv listener Command Parameters

| Parameter                   | Description                                                                                                                                                               |
|:----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify the name of a listener.<br>If you do not use this parameter, then the listener name defaults to `LISTENER`.                                   |
| `-envs "name=val[,...]"`    | Specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`).                                                    |
| `-env "``name``=``val``"`   | Use this parameter to enable single environment variable to be set to a value that contains commas or other special characters enclosed in double quotation marks (`""`). |

##### Examples

The following example sets the language environment configuration for the default listener:

    $ srvctl setenv listener -env "LANG=en"

#### srvctl start listener

Starts the default listener on specific node, or starts the specified listener on all nodes that are registered with Oracle Clusterware or on the given node.

##### Syntax

    srvctl start listener [-node node_name] [-listener listener_name]

##### Parameters

Table A-43 srvctl start listener Command Parameters

| Parameter                   | Description                                                                                                                                                                                                              |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`         | Specify a particular node name to start the listener on that node.<br>Note: You can only use this parameter with Oracle Clusterware.                                                                                     |
| `-listener ``listener_name` | Specify a particular listener name. Use the `srvctl config listener` command to obtain the name of a listener.<br>If you do not assign a value to this parameter, then SRVCTL starts all known listeners in the cluster. |

##### Examples

The following command starts all listeners managed by Oracle Clusterware on the node named `server3`.

    $ srvctl start listener -node server3

#### srvctl status listener

Displays the status of listener resources.

##### Syntax

    srvctl status listener [-listener listener_name] [-node node_name] [-verbose]

##### Parameters

Table A-44 srvctl status listener Command Parameters

| Parameter                   | Description                                                                                                                             |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify the name of a listener.<br>If you do not use this parameter, then the listener name defaults to `LISTENER`. |
| `-node ``node_name`         | Optionally, you can specify the name of a cluster node.<br>Note: You can only use this parameter with Oracle Clusterware.               |
| `–verbose`                  | Optionally, you can use this parameter to display verbose output.                                                                       |

##### Examples

The following example displays the status of the default listener on the node `node2`:

    $ srvctl status listener -node node2

#### srvctl stop listener

Stops the default listener or a specific listener on all nodes or the specified node.

You can also use this command to stop a listener on a non-cluster database from the non-cluster database home. However, SRVCTL does not accept the `-node` parameter when run from a non-cluster database home.

##### Syntax

    srvctl stop listener [-listener listener_name] [-node node_name] [-force]

##### Parameters

Table A-45 srvctl stop listener Command Parameters

| Parameter                   | Description                                                                                                                                                  |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Specify the name of the listener you want to stop.<br>If you do not assign a value to this parameter, then SRVCTL stops all known listeners in the cluster.  |
| `-node ``node_name`         | Optionally, you can specify the name of a single node on which a particular listener runs.<br>Note: You can only use this parameter with Oracle Clusterware. |
| `–force`                    | Forcibly stop the listener.                                                                                                                                  |

##### Examples

The following command stops all listeners on the node `mynode1`:

    $ srvctl stop listener -node mynode1

#### srvctl unsetenv listener

Unsets the environment configuration for a listener.

##### Syntax

    srvctl unsetenv listener [-listener listener_name] -envs "name_list"

##### Parameters

Table A-46 srvctl unsetenv listener Command Parameters

| Parameter                   | Description                                                                                                                                                                                              |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name` | Optionally, you can specify the name of a listener for which you want to unset the environment configuration.<br>If you do not use this parameter, then the name of the listener defaults to `LISTENER`. |
| `-envs "``name_list``"`     | Specify a comma-delimited list of environment variable names enclosed in double quotation marks (`""`) that you want to unset.                                                                           |

##### Examples

The following example unsets the environment variable `TNS_ADMIN` for the default listener:

    $ srvctl unsetenv listener -envs "TNS_ADMIN"

#### srvctl update listener

Updates the listener to listen on the new endpoints.

##### Syntax

    srvctl update listener

##### Usage Notes

- This command does not accept any additional parameters, except for `-help`.

- You can only use this command with Oracle Clusterware.

#### srvctl add network

Adds a static or dynamic network.

If your server connects to more than one network, then you can use this command to configure an additional network interface for Oracle RAC, allowing you to create VIPs on multiple public networks.

##### Syntax

    srvctl add network [-netnum net_number] -subnet subnet/netmask[/if1[|if2...]]
       [-nettype {STATIC | DHCP | AUTOCONFIG | MIXED}] [-pingtarget "ping_target_list"]
       [-skip] [-verbose]

##### Parameters

Table A-47 srvctl add network Command Parameters

| Parameter                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``net_number`                                    | The network number. The default is 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-subnet ``subnet``/``netmask`` [/``if1``[|``if2``|...]]` | Defines a subnet. If you do not specify any interface names, then the network uses any interface on the given subnet.<br>For IPv6, `netmask` is a prefix length, such as 64.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-nettype {STATIC|DHCP|AUTOCONFIG|MIXED}`                 | Specify the network type: `STATIC`, `DHCP`, `AUTOCONFIG`, or `MIXED`.<br>If you specify `STATIC` for the network type, then you must provide the virtual IP address using the `srvctl add vip` command.<br>If you specify `DHCP` for the network type, then the VIP agent obtains the IP address from a DHCP server.<br>If you specify `AUTOCONFIG` for the network type, then the VIP agent generates a stateless IPv6 address for the network. You can only use `AUTOCONFIG` for IPv6 networks. If the subnet/netmask specification is not for an IPv6 address, then SRVCTL returns an error.<br>If you specify `MIXED` for the network type, then the VIP resource uses both a static IP address and an IP address obtained dynamically, either from a DHCP server for IPv4 or using stateless auto-configuration for IPv6. |
| `-pingtarget "``ping_target_list``"`                      | A comma-delimited list of IP addresses or host names to ping.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-skip`                                                   | Use this parameter to skip the checking of subnet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-verbose`                                                | Verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

##### Usage Notes

- On Linux and UNIX systems, you must be logged in as the `root` user and on Windows, you must be logged in as a user with Administrator privileges to run this command.

- This command is only available with Oracle Clusterware.

- Oracle only supports DHCP-assigned networks for the default network, not for subsequent networks.

- You can also use the `LISTENER_NETWORKS` database initialization parameter to control client redirects to the appropriate network.

##### Example

An example of this command is:

    # srvctl add network -netnum 3 -subnet 192.168.3.0/255.255.255.0

#### srvctl config network

Displays the network configuration for the cluster.

##### Syntax

    srvctl config network [-netnum network_number]

##### Usage Notes

- Specify the network for which you want to display configuration information.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    $ srvctl config network -netnum 2

#### srvctl modify network

Modifies the subnet, network type, or IP address type for a network.

##### Syntax

    srvctl modify network [-netnum network_number] [-subnet subnet/netmask
      [/if1[|if2|...]]] [-nettype network_type | -iptype {ipv4 | ipv6 | both}]
      [-pingtarget "ping_target_list"] [-verbose]

##### Parameters

Table A-48 srvctl modify network Command Parameters

| Parameter                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`                                | Optionally, you can specify a network number that you want to modify. The default is 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-subnet ``subnet``/``netmask`` [/``if1``[|``if2``|...]]` | Optionally, you can specify a subnet number for the public network. The netmask and interfaces you specify, if any, change those of the network you are modifying. If you specify an IPv6 subnet, then enter a prefix length, such as 64, in place of `netmask`. If you do not specify any interface names, then the VIPs use any interface on the given subnet.<br>If you are changing the network type using the `-nettype` parameter, then you must specify either an existing IPv4 or IPv6 network using the `-subnet` parameter. Additionally, the subnet and netmask you specify in the `-subnet` parameter do not change those of the network you are modifying. |
| `-nettype ``network_type`                                 | Optionally, you can modify the network type using this parameter, to `static`, `dhcp`, `autoconfig`, or `mixed`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-iptype {ipv4 | ipv6 | both}`                            | Alternative to modifying the network type, you can modify the type of IP address to `ipv4`, `ipv6`, or `both`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-pingtarget "``ping_target_list``"`                      | Optionally, you can specify a comma-delimited list of IP addresses or host names to ping enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-verbose`                                                | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- On Linux and UNIX systems, you must be logged in as `root` and on Windows, you must be logged in as a user with Administrator privileges to run this command.

- You can modify the IP address type for a network from IPv4 to IPv6, or from IPv6 to IPv4.

- If you specify `static` for the network type, then you must provide the virtual IP address using the `srvctl add vip` command.

- If you specify `dhcp` for the network type, then the VIP agent obtains the IP address from a DHCP server.

- If you specify `autoconfig` for the network type, then the VIP agent generates a stateless IPv6 address for the network. You can only use this parameter for IPv6 networks. If the subnet/netmask specification is not for an IPv6 address, then SRVCTL returns an error.

- If you change a network from `static` to `mixed`, then you must first configure GNS, so that the dynamic addresses obtained can have names registered for them.

- If you specify `mixed` for the network type, then the VIP resource uses both a static IP address and an IP address obtained dynamically, either DHCP or autoconfig.

- If you specify `mixed_autoconfig` for the network type, then the VIP resource retains the static IP configuration and either obtains an IP address from a DHCP server for an IPv4 network specification or generates a stateless auto-configured IP address for an IPv6 network specification.

##### Examples

The following example changes the subnet number, netmask, and interface list:

    # srvctl modify network -subnet 192.168.2.0/255.255.255.0/eth0

The following example changes the second network to DHCP:

    # srvctl modify network -netnum 2 -nettype dhcp

The following example adds an IPv6 subnet and netmask to the default network:

    # srvctl modify network -subnet 2606:b400:400:18c0::/64

The following example removes the IPv4 configuration from a network:

    # srvctl modify network -iptype ipv6

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

#### srvctl predict network

Predicts the consequences of network failure.

##### Syntax

    srvctl predict network [-netnum network_number] [-verbose]

##### Usage Notes

Optionally, you can specify a network for which you want to evaluate a failure. The default value is 1. You can also use the `–verbose` parameter to print detailed output.

##### Example

The following example predicts the consequences of a failure on network number 2:

    $ srvctl predict network -netnum 2

#### srvctl remove network

Removes the network configuration.

##### Syntax

    srvctl remove network {-netnum network_number | -all} [-force] [-verbose]

##### Parameters

Table A-49 srvctl remove network Command Parameters

| Parameter                           | Description                                                                                                                                        |
|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`` | -all` | Specify which network number you want to remove. Alternatively, you can use the `–all` parameter to indicate that you want to remove all networks. |
| `-force`                            | Optionally, you can use this parameter to remove the specified network regardless of any dependencies.                                             |
| `-verbose`                          | Optionally, you can use this parameter to display detailed output.                                                                                 |

##### Usage Notes

- You can only use the command with Oracle Clusterware.

- You must have full administrative privileges to run this command. On Linux and UNIX systems, you must be logged in as `root` and on Windows systems, you must be logged in as a user with Administrator privileges.

##### Example

The following example removes a network:

    # srvctl remove network -netnum 3

#### srvctl add nodeapps

Adds a node application configuration to the specified node.

##### Syntax

Use this command with one the following syntax models, specifying either a specific node and VIP or a specific subnet and netmask:

    srvctl add nodeapps
        {-node node_name -address {vip_name | ip_address}/netmask[/if1[|if2|..]] [-skip]}
        [-emport em_port] [-onslocalport ons_local_port]
        [-onsremoteport ons_remote_port] [-onshostport hostname_port_list]
        [-remoteservers hostname_port_list [-verbose]

    srvctl add nodeapps -subnet subnet/netmask[/if1[|if2|...]] [-emport em_port]
        [-onslocalport ons_local_port] [-onsremoteport ons_remote_port]
        [-onshostport hostname_port_list] [-remoteservers hostname_port_list]
        [-verbose]

##### Parameters

Table A-50 srvctl add nodeapps Command Parameters

| Parameter                                                                      | Description                                                                                                                                                                                                                                                        |
|:-------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`                                                            | The name of the node on which you want to create the node application. Node name is optional and unnecessary if you run the command on the local node.                                                                                                             |
| `-address {``vip_name`` | ``ip_address``}/``netmask``[/``if1``[|``if2``|..]]}` | This specification creates a traditional VIP node application on the specified node.<br>Note: You must use this parameter for upgrade configurations and new, non-DHCP configurations.                                                                             |
| `-skip`                                                                        | Specify this parameter to skip checking the reachability of the VIP address.                                                                                                                                                                                       |
| `-subnet ``subnet``/``netmask`` [/``if1``[|``if2 ``|...]]`                     | Creates a DHCP subnet. If you do not specify any interface names, then the VIPs use any interface on the given subnet.                                                                                                                                             |
| `-emport ``em_port`                                                            | Local port on which Oracle Enterprise Manager listens. The default port is 2016.                                                                                                                                                                                   |
| `-onslocalport ``ons_local_port`                                               | The Oracle Notification Service daemon listener port on its node.<br>If you do not specify this value, the Oracle Notification Service daemon listener port defaults to 6100.<br>Note: The local port and remote port must each be unique.                         |
| `-onsremoteport ``ons_remote_port`                                             | The port number for remote Oracle Notification Service daemon connections.<br>If you do not specify a port number, the default value of 6200 is used for the Oracle Notification Service remote port.<br>Note: The local port and remote port must each be unique. |
| `-onshostport ``host_port_list`                                                | A list of `host``[:``port``]` pairs of remote hosts that are part of the Oracle Notification Service network but are not part of the Oracle Clusterware cluster<br>Note: If `port` is not specified for a remote host, then `ons_remote_port` is used.             |
| `-remoteservers ``host_port_list`                                              | A list of `host``[:``port``]` pairs for Oracle Notification Service daemons on servers that are not in the cluster.                                                                                                                                                |
| `-verbose`                                                                     | Verbose output                                                                                                                                                                                                                                                     |

##### Usage Notes

- On Linux and UNIX systems, you must be logged in as `root` and on Windows, you must be logged in as a user with Administrator privileges to run this command.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl add nodeapps -node crmnode1 -address 1.2.3.4/255.255.255.0

#### srvctl config nodeapps

Displays the VIP configuration for each node in the cluster.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl config nodeapps [-viponly] [-onsonly]

##### Usage Notes

Use `-viponly` to display the VIP address configuration. Use `-onsonly` to display the Oracle Notification Service configuration.

##### Example

An example of this command is:

    $ srvctl config nodeapps -viponly -onsonly

#### srvctl disable nodeapps

Disables node applications on all nodes in the cluster.

##### Syntax

    srvctl disable nodeapps [-gsdonly] [-adminhelper] [-verbose]

##### Parameters

Table A-51 srvctl disable nodeapps Command Parameters

| Parameter      | Description                                                                              |
|:---------------|:-----------------------------------------------------------------------------------------|
| `-gsdonly`     | Optionally, you can use this parameter to disable only the global services daemon (GSD). |
| `-adminhelper` | Optionally, you can use this parameter to disable the Administrator helper only.         |
| `–verbose`     | Optionally, you can use this parameter to display detailed output.                       |

##### Usage Notes

You can only use this parameter with Oracle Clusterware.

##### Example

The following example disables GSD:

    $ srvctl disable nodeapps -gsdonly -verbose

#### srvctl enable nodeapps

Enables the node applications on all nodes in the cluster.

##### Syntax

    srvctl enable nodeapps [-gsdonly] [-adminhelper] [-verbose]

##### Parameters

Table A-52 srvctl enable nodeapps Command Parameters

| Parameter      | Description                                                                             |
|:---------------|:----------------------------------------------------------------------------------------|
| `-gsdonly`     | Optionally, you can use this parameter to enable only the global services daemon (GSD). |
| `-adminhelper` | Optionally, you can use this parameter to enable the Administrator helper only.         |
| `–verbose`     | Optionally, you can use this parameter to display detailed output.                      |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example enables GSD:

    $ srvctl enable nodeapps -gsdonly -verbose

#### srvctl getenv nodeapps

Displays the environment variables for the node application configurations.

##### Syntax

    srvctl getenv nodeapps [-viponly] [-onsonly] [-envs "name_list"]

##### Parameters

Table A-53 srvctl getenv nodeapps Command Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                  |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-viponly`              | Optionally, you can use this parameter to display the VIP address configuration.                                                                                                                                                                                             |
| `-onsonly`              | Optionally, you can use this parameter to isplay the Oracle Notification Service configuration.                                                                                                                                                                              |
| `-envs "``name_list``"` | Optionally, you can specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).<br>If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the node applications. |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example lists all environment variables for the node applications:

    $ srvctl getenv nodeapps -viponly

#### srvctl modify nodeapps

Modifies the configuration for a node application.

##### Syntax

Use this command with one of the following syntax models, specifying either a specific node and VIP or a specific subnet and netmask:

    srvctl modify nodeapps {[-node node_name -address {vip_name|vip_address}/
      netmask[/if1[|if2|...]] [-skip]} [-nettype network_type] [-emport em_port]
        [-onslocalport ons_local_port] [-onsremoteport ons_remote_port]
        [-remoteservers host:[port][,...]] [-verbose]
        [-clientdata file] [-pingtarget "ping_target_list"]

    srvctl modify nodeapps [-subnet subnet/netmask[/if1[|if2|...]]]
        [-nettype network_type] [-emport em_port]
        [-onslocalport ons_local_port] [-onsremoteport ons_remote_port]
        [-remoteservers host:[port][,host:port,...]] [-verbose]
        [-clientdata file] [-pingtarget "ping_target_list"]

##### Parameters

Table A-54 srvctl modify nodeapps Command Parameters

| Parameter                                                                      | Description                                                                                                                                                                                                                                                                                                                      |
|:-------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`                                                            | Specify the name of the node on which the node application you want to modify resides.                                                                                                                                                                                                                                           |
| `-address {``vip_name``|``vip_address``}/ ``netmask``[/``if1``[|``if2``|...]]` | Specify a node-level virtual IP name or address. The address specified by name or IP must match the subnet number of the default network.<br>Note: You must use this parameter for upgrade configurations and new non-DHCP configurations                                                                                        |
| `–skip`                                                                        | Optionally, you can use this parameter to skip checking the reachability of the VIP address.                                                                                                                                                                                                                                     |
| `-subnet ``subnet``/``netmask``[/``if1``[|``if2``|...]]`                       | Alternative to specifying a node name and address, you can specify a subnet number for the public network. The netmask and interfaces you specify, if any, change those of the default network. Additionally, if you specify a value for the `netmask` option, then you need only specify it for the first node on each network. |
| `-nettype ``network_type`                                                      | Optionally, you can change the network server type to `static`, `dhcp`, or `mixed`.                                                                                                                                                                                                                                              |
| `-emport ``em_port`                                                            | Optionally, you can change the local port on which Oracle Enterprise Manager listens.<br>Note: You can also modify this attribute using Online Resource Attribute Modification.                                                                                                                                                  |
| `-onslocalport ``ons_local_port`                                               | Optionally, you can change the port on which the Oracle Notification Service daemon listens for local client connections.<br>Notes:<br>• The local port and remote port must each be unique.<br>• You can modify the local port while the resource remains online, without restarting the resource.                              |
| `-onsremoteport ``ons_remote_port`                                             | Optionally, you can change the port on which the Oracle Notification Service daemon listens for connections from remote hosts.<br>Notes:<br>• The local port and remote port must each be unique.<br>• You can modify the remote port while the resource remains online, without restarting the resource.                        |
| `-remoteservers ``host``:[``port``][,...]`                                     | Optionally, you can modify the comma-delimited list of `host``:[``port` pairs of remote hosts that are part of the Oracle Notification Service network but are not part of the cluster. If you do not specify a port for a remote host, then the utility uses the value you specified for `ons_remote_port`.                     |
| `-clientdata ``file`                                                           | Optionally, you can specify the file with a wallet to import, or an empty string to delete a wallet used for SSL to secure Oracle Notification Service communication.                                                                                                                                                            |
| `-pingtarget "``ping_target_list``"`                                           | Optionally, you can specify a comma-delimited list of IPs or host names enclosed in double quotation marks (`""`) to ping.                                                                                                                                                                                                       |
| `-verbose`                                                                     | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                                                                                               |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example changes the nodeapps resource on `mynode1` to use the application VIP of 100.200.300.40 with a subnet mask of 255.255.255.0 on the network interface `eth0`:

    $ srvctl modify nodeapps -node mynode1 -addr 100.200.300.40/255.255.255.0/eth0

#### srvctl remove nodeapps

Removes the node application configuration.

##### Syntax

    srvctl remove nodeapps [-force] [-noprompt] [-verbose]

##### Parameters

Table A-55 srvctl remove nodeapps Command Parameters

| Parameter   | Description                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------|
| `-force`    | Optionally, you can use this parameter to forcibly remove node application configurations, regardless of any dependencies. |
| `-noprompt` | Optionally, you can use this parameter to suppress prompts.                                                                |
| `-verbose`  | Optionally, you can use this parameter to display detailed output.                                                         |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- You must have full administrative privileges to run this command. On Linux and UNIX systems, you must be logged in as `root` and on Windows systems, you must be logged in as a user with Administrator privileges.

#### srvctl setenv nodeapps

Sets the environment variables for the node application configurations.

##### Syntax

    srvctl setenv nodeapps {-envs "name=val[,...]" | -env "name=val"}
       [-viponly] [-gsdonly] [-onsonly] [-verbose]

##### Parameters

Table A-56 srvctl setenv nodeapps Command Parameters

| Parameter                        | Description                                                                                                                                                                                            |
|:---------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name``=``val``[,...]"` | Use this parameter to specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`).                                                           |
| `-env "``name``=``val``"`        | Alternatively, you can use this parameter to enable a single environment variable that is set to a value which contains commas or other special characters, enclosed in double quotation marks (`""`). |
| `-viponly`                       | Optionally, you can use this parameter to modify only the VIP configuration.                                                                                                                           |
| `-gsdonly`                       | Optionally, you can use this parameter to modify only the GSD configuration.                                                                                                                           |
| `-onsonly`                       | Optionally, you can use this parameter to modify only the ONS daemon configuration.                                                                                                                    |
| `-verbose`                       | Optionally, you can use this parameter to display detailed output.                                                                                                                                     |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example sets the `CLASSPATH` environment variable for all node applications:

    $ srvctl setenv nodeapps -env "CLASSPATH=/usr/local/jdk/jre/rt.jar" -verbose

#### srvctl start nodeapps

Starts node-level applications on a node or all nodes in the cluster.

##### Syntax

    srvctl start nodeapps [-node node_name] [-gsdonly] [-adminhelper] [-verbose]

##### Parameters

Table A-57 srvctl start nodeapps Command Parameters

| Parameter           | Description                                                                                                                                                                                     |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name` | Optionally, you can specify a node on which to start node-level applications.<br>If you do not use this parameter, then SRVCTL starts the node applications on all active nodes in the cluster. |
| `-gsdonly`          | Optionally, you can use this parameter to start only GSD, instead of all node applications.                                                                                                     |
| `-adminhelper`      | Optionally, you can use this parameter to start only an Administrator helper instead of all node applications.                                                                                  |
| `-verbose`          | Optionally, you can use this parameter to display detailed output.                                                                                                                              |

##### Usage Notes

You can only use this command with Oracle Clusterware.

#### srvctl status nodeapps

Displays the status of node applications.

##### Syntax

    srvctl status nodeapps [-node node_name]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can specify a node for which to display the status of the node applications.

#### srvctl stop nodeapps

Stops node-level applications on a node in the cluster.

##### Syntax

    srvctl stop nodeapps [-node node_name] [-gsdonly] [-adminhelper] [-force]
       [-relocate] [-verbose]

##### Parameters

Table A-58 srvctl stop nodeapps Command Parameters

| Parameter           | Description                                                                                                                                                                                                                 |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name` | Optionally, you can use this parameter to specify a node on which you want to stop node applications.<br>If you do not use this parameter, then the utility stops the node applications on all active nodes in the cluster. |
| `-gsdonly`          | Optionally, you can use this parameter to stop only the GSD, instead of all node applications.                                                                                                                              |
| `-adminhelper`      | Optionally, you can use this parameter to stop only the Administrator helper instead of all node applications.                                                                                                              |
| `-force`            | Optionally, you can use this parameter to stop node applications regardless of any dependencies.                                                                                                                            |
| `-relocate`         | Optionally, you can use this parameter to relocate the VIP and possibly-dependent services.<br>Note: If you use this parameter, then you must also specify the `-node ``node_name` parameter.                               |
| `-verbose`          | Optionally, you can use this parameter to display detailed output.                                                                                                                                                          |

##### Usage Notes

You can only use this command with Oracle Clusterware.

#### srvctl unsetenv nodeapps

Unsets the environment configuration for the node applications.

##### Syntax

    srvctl unsetenv nodeapps -envs "name_list" [-viponly] [-gsdonly] [-onsonly]
       [-verbose]

##### Parameters

Table A-59 srvctl unsetenv nodeapps Command Parameters

| Parameter               | Description                                                                                                                            |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name_list``"` | Specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`) that you want to unset. |
| `-viponly`              | Optionally, you can use this parameter to unset only the VIP configuration.                                                            |
| `-gsdonly`              | Optionally, you can use this parameter to unset only the GSD configuration.                                                            |
| `-onsonly`              | Optionally, you can use this parameter to unset only the ONS daemon configuration.                                                     |
| `-verbose`              | Optionally, you can use this parameter to display detailed output.                                                                     |

##### Example

The following example unsets the environment configuration for the specified node applications:

    $ srvctl unsetenv nodeapps -envs "test_var1,test_var2"

#### srvctl add ons

Adds an Oracle Notification Service daemon to an Oracle Restart configuration.

##### Syntax

    srvctl add ons [-emport em_port] [-onslocalport ons_local_port] [-onsremoteport ons_remote_port]
       [-remoteservers host[:port][,host[:port]...]]
       [-clientcluster cluster_name] [-clientdata filename]

##### Parameters

Table A-60 srvctl add ons Command Parameters

| Parameter                                                    | Description                                                                                                                                                                                                                                                                                     |
|:-------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-emport ``em_port`                                          | Local listen port for Oracle Enterprise Manager. The default port number is 2016.                                                                                                                                                                                                               |
| `-onslocalport ``ons_local_port`                             | Optionally, you can specify the Oracle Notification Service daemon listening port for local client connections.<br>Note: The local port and remote port must each be unique.                                                                                                                    |
| `-onsremoteport ``ons_remote_port`                           | Optionally, you can specify the Oracle Notification Service daemon listening port for connections from remote hosts.<br>Note: The local port and remote port must each be unique.                                                                                                               |
| `-remoteservers ``host``[:``port``][``host``[:``port``]...]` | Optionally, you can specify a comma-delimited list of `host``:``port` pairs of remote hosts that are part of the Oracle Notification Service network but are not part of the Oracle Clusterware cluster.<br>Note: If `port` is not specified for a remote host, then `ons_remote_port` is used. |
| `-clientcluster ``cluster_name`                              | The name of the cluster that is running the shared SCAN listener.                                                                                                                                                                                                                               |
| `-clientdata ``filename`                                     | Specify the path to the file to which credentials data will be written.                                                                                                                                                                                                                         |

##### Usage Notes

You can only use this command with Oracle Restart.

##### Example

An example of this command is:

    $ srvctl add ons -onslocalprt 6200

#### srvctl config ons

Displays configuration information for the Oracle Notification Service daemon.

##### Syntax

    srvctl config ons [-all] [-clientcluster cluster_name]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can display the configuration for all ONS daemons, or those for a specific client cluster.

#### srvctl disable ons

Disables the Oracle Notification Service (ONS) daemon for Oracle Restart installations.

##### Syntax

    srvctl disable ons [-clientcluster cluster_name] [-verbose]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can disable all ONS daemons, or those for a specific client cluster.

- Optionally, you can use the `-verbose` parameter to display detailed output.

#### srvctl enable ons

Enables the Oracle Notification Service daemon.

##### Syntax

    srvctl enable ons [-clientcluster cluster_name] [-verbose]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can enable all ONS daemons, or those for a specific client cluster.

- Optionally, you can use the `-verbose` parameter to display detailed output.

#### srvctl modify ons

Modifies the ports used by the Oracle Notification Service daemon that is registered with Oracle Restart.

##### Syntax

    srvctl modify ons [-emport em_port] [-onslocalprt ons_local_port] [-onsremoteport ons_remote_port]
      [-remoteservers host[:port][,host[:port],...]]
      [-clientcluster cluster_name] [-verbose]

##### Parameters

Table A-61 srvctl modify ons Command Parameters

| Parameter                                                      | Description                                                                                                                                                                                                                                                                                         |
|:---------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-emport ``em_port`                                            | Optionally, you can specify the local port on which Oracle Enterprise Manager listens. The default port is 2016.                                                                                                                                                                                    |
| `-onslocalprt ``ons_local_port`                                | Optionally, you can modify the Oracle Notification Service daemon listening port for local client connections.<br>Note: The local port and remote port must each be unique.                                                                                                                         |
| `-onsremoteport ``ons_remote_port`                             | Optionally, you can modify the Oracle Notification Service daemon listening port for connections from remote hosts.<br>Note: The local port and remote port must each be unique.                                                                                                                    |
| `-remoteservers ``host``[:``port``][,``host``[:``port``],...]` | Optionally, you can specify a list of `host``:``port` pairs of remote hosts that are part of the Oracle Notification Service network but are not part of the Oracle Clusterware cluster.<br>Note: If you do not specify `port` for a remote host, then SRVCTL uses the value for `ons_remote_port`. |
| `-clientcluster ``cluster_name`                                | The name of the cluster that is running the shared SCAN listener.                                                                                                                                                                                                                                   |
| `-verbose`                                                     | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                                                                  |

##### Usage Notes

You can only use this command with Oracle Restart.

##### Example

An example of this command is:

    $ srvctl modify ons -onslocalprt 6203

#### srvctl remove ons

Removes Oracle Notification Service from the Oracle Grid Infrastructure home.

##### Syntax

    srvctl remove ons [-clientcluster cluster_name] [-force] [-verbose]

##### Usage Notes

- You can only use this command with Oracle Restart.

- If using the shared SCAN feature, then use the `-clientcluster` parameter to specify the name of the cluster that is running the shared SCAN listener.

- Optionally, you can use the `–force` parameter to remove Oracle Notification Service regardless of dependencies.

- Optionally, you can use the `–verbose` parameter to display detailed output.

#### srvctl start ons

Starts the Oracle Notification Service daemon.

##### Syntax

    srvctl start ons [-clientcluster cluster_name] [-verbose]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can enable all ONS daemons, or those for a specific client cluster.

- Optionally, you can use the `-verbose` parameter to display detailed output.

#### srvctl status ons

Displays the current state of the Oracle Notification Service daemon.

##### Syntax

    srvctl status ons [-clientcluster cluster_name]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can display the status for all ONS daemons, or those for a specific client cluster.

#### srvctl stop ons

Stops the Oracle Notification Service daemon.

##### Syntax

    srvctl stop ons [-clientcluster cluster_name] [-force]

##### Usage Notes

- You can only use this command with Oracle Restart.

- You can stop all ONS daemons, or those for a specific client cluster.

- Optionally, you can use the `–force` parameter to stop the ONS daemons regardless of any dependencies.

#### srvctl add scan

Adds Oracle Clusterware resources for the given SCAN.

##### Syntax

    srvctl add scan -scanname scan_name [-netnum network_number]

##### Parameters

Table A-62 srvctl add scan Command Parameters

| Parameter                  | Description                                                                                                                                                                                                                                                                                                |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-scanname ``scan_name`    | A fully-qualified host name, which includes the domain name. If the network is dynamic, then you do not have to use fully-qualified host name but, if you choose to do so, then the domain must be the GNS subdomain.<br>Note: You can modify this attribute using Online Resource Attribute Modification. |
| `-netnum ``network_number` | The optional network number from which SCAN VIPs are obtained. If you do not specify this parameter, then the SCAN VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained.                                                                                              |

##### Usage Notes

- This command creates the same number of SCAN VIP resources as the number of IP addresses that SCAN resolves to, or 3 when `network_number` identifies a dynamic network and Oracle GNS configuration.

- For static networks, the addresses to which the SCAN resolves in DNS must match the address type of the subnet.

- For an IPv4 network, the SCAN must resolve to IPv4 addresses.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl add scan -scanname scan.mycluster.example.com

#### srvctl config scan

Displays the configuration information for all SCAN VIPs, by default, or a specific SCAN VIP identified by ordinal_number.

##### Syntax

    srvctl config scan [[-netnum network_number] [-scannumber ordinal_number] | -all]

##### Parameters

Table A-63 srvctl config scan Command Parameters

| Parameter                      | Description                                                                                                                           |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`     | Use this parameter to view the configuration of a specific SCAN VIP.                                                                  |
| `-scannumber ``ordinal_number` | Use this parameter to specify any one of the three SCAN VIPs, using values from 1 to 3, for which you want to view the configuration. |
| `-all`                         | Alternative to specifying network or ordinal numbers, you can use this parameter to view the configuration for all of the SCAN VIPs.  |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

This command returns output similar to the following:

    $ srvctl config scan -scannumber 1

    SCAN name: mjk12700890090-r, Network: 1
    Subnet IPv4: 198.51.100.1/203.0.113.46/eth0, static
    Subnet IPv6:
    SCAN 1 IPv4 VIP: 198.51.100.195
    SCAN VIP is enabled.
    SCAN VIP is individually enabled on nodes:
    SCAN VIP is individually disabled on nodes:

#### srvctl disable scan

Disables all SCAN VIPs, by default, or a specific SCAN VIP identified by `ordinal_number`.

##### Syntax

    srvctl disable scan [-scannumber ordinal_number]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can use the `-scannumber` parameter to specify any one of the three SCAN VIPs you want to disable. The parameter takes a range of values from 1 to 3.

##### Example

The following example disables the first SCAN VIP:

    $ srvctl disable scan -scannumber 1

#### srvctl enable scan

Enables all SCAN VIPs, by default, or a specific SCAN VIP identified by its ordinal number.

##### Syntax

    srvctl enable scan [-scannumber ordinal_number]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can use the `-scannumber` parameter to specify any one of the three SCAN VIPs you want to enable. The parameter takes a range of values from 1 to 3.

##### Example

The following example enables the first SCAN VIP:

    $ srvctl enable scan -scannumber 1

#### srvctl modify scan

Modifies the number of SCAN VIPs to match the number of IP addresses returned by looking up the `scan_name` you specify in DNS.

You use this command when DNS was modified to add, change, or remove IP addresses, and now you must adjust the Oracle Clusterware resource configuration to match.

##### Syntax

    srvctl modify scan -scanname scan_name [-netnum network_number]

##### Parameters

Table A-64 srvctl modify scan Command Parameters

| Parameter                  | Description                                                                                                                                                                |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-scanname ``scan_name`    | Identifies the SCAN name that resolves to the SCAN VIPs that you want to modify.<br>Note: You can modify this attribute using Online Resource Attribute Modification.      |
| `-netnum ``network_number` | The optional network number from which VIPs are obtained. If not specified, the VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained. |

##### Example

Assume your system currently has a SCAN named `scan_name1`, and it resolves to a single IP address in DNS. If you modify the SCAN `scan_name1` in DNS to resolve to three IP addresses, then use the following command to create the additional SCAN VIP resources:

    $ srvctl modify scan -scanname scan_name1

#### srvctl predict scan

Predicts the consequences of SCAN failure.

##### Syntax

    srvctl predict scan -scannumber ordinal_number [-verbose]

##### Usage Notes

- Specify an ordinal number that identifies the SCAN VIP for which you want to simulate failure. The range of values you can specify for this parameter is 1 to 3.

- Optionally, you can use the `–verbose` parameter to display detailed output.

Add additional information about the command here.

#### srvctl relocate scan

Relocates a specific SCAN VIP from its current hosting node to another node within the cluster.

##### Syntax

    srvctl relocate scan -scannumber ordinal_number [-node node_name]

##### Parameters

Table A-65 srvctl relocate scan Command Parameters

| Parameter                      | Description                                                                                                                                                                                         |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-scannumber ``ordinal_number` | Specify an ordinal number that identifies which SCAN VIP you want to relocate. The range of values you can specify for this parameter is 1 to 3.                                                    |
| `-node ``node_name`            | Optionally, you can specify the name of a single node to which SRVCTL relocates the SCAN VIP.<br>If you do not use this parameter, then SRVCTL chooses the node to which the SCAN VIP is relocated. |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example relocates the first SCAN VIP to `node1`:

    $ srvctl relocate scan -scannumber 1 -node node1

#### srvctl remove scan

Removes Oracle Clusterware resources from all SCAN VIPs.

##### Syntax

    srvctl remove scan [-netnum network_number] [-force] [-noprompt]

##### Parameters

Table A-66 srvctl remove scan Command Parameters

| Parameter                  | Description                                                                                                                                                                |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number` | The optional network number from which VIPs are obtained. If not specified, the VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained. |
| `–force`                   | Removes the SCAN VIPs even though there are SCAN listeners running that are dependent on the SCAN VIPs.                                                                    |
| `–noprompt`                | Use this parameter to suppress all prompts.                                                                                                                                |

##### Usage Notes

If you use the `-force` option, then SCAN VIPs that are running are not stopped before the dependent resources are removed, which may require manual cleanup.

##### Examples

An example of this command is:

    $ srvctl remove scan -force

#### srvctl start scan

Starts all SCAN VIPs, by default, or a specific SCAN VIP, on all nodes or a specific node in the cluster.

##### Syntax

    srvctl start scan [-scannumber ordinal_number] [-node node_name]

##### Parameters

Table A-67 srvctl start scan Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                                  |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-scannumber ``ordinal_number` | Optionally, you can specify an ordinal number that identifies which SCAN VIP you want to start. The range of values you can specify for this parameter is 1 to 3.<br>If you do not use this parameter, then SRVCTL starts all the SCAN VIPs. |
| `-node ``node_name`            | Optionally, you can specify the name of a single node on which the SCAN VIP resides that you want to start.<br>If you do not specify this parameter, then SRVCTL starts the SCAN VIPs on all nodes in the cluster.                           |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example starts the SCAN VIP identified by the ordinal number 1 on the `crm1` node:

    $ srvctl start scan -scannumber 1 -node crm1

#### srvctl status scan

Displays the status for all SCAN VIPs, by default, or a specific SCAN VIP.

##### Syntax

    srvctl status scan [-scannumber ordinal_number] [-verbose]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can specify an ordinal number that identifies a specific SCAN VIP for which you want to display the status. The range of values you can specify for this parameter is 1 to 3. If you do not use this parameter, then SRVCTL displays the status of all SCAN VIPs in the cluster.

- Optionally, you can use the `–verbose` parameter to display detailed output.

#### srvctl stop scan

Stops all SCAN VIPs, by default, that are running or in starting state, or stops a specific SCAN VIP identified by an ordinal number.

##### Syntax

    srvctl stop scan [-scannumber ordinal_number] [-force]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can specify an ordinal number that identifies which SCAN VIP you want to stop. The range of values you can specify for this parameter is 1 to 3. If you do not use this parameter, then SRVCTL stops all the SCAN VIPs.

- Optionally, you can use the `–force` parameter to stop the SCAN VIPs regardless of any dependencies.

##### Example

The following example stops the SCAN VIP identified by the ordinal number 1:

    $ srvctl stop scan -scannumber 1

#### srvctl add scan_listener

Adds Oracle Clusterware resources for the SCAN listeners.

##### Syntax

    srvctl add scan_listener [-netnum network_number] [-listener lsnr_name_prefix] [-skip]
      [-endpoints "[TCP:]port_list[/IPC:key][/NMP:pipe_name]
      [/{TCPS|SDP|EXADIRECT}port_list]"]
      [-invitednodes "node_list"] [-invitedsubnets "subnet_list"]
      [-clientcluster cluster_name] [-clientdata <filename>]

##### Parameters

Table A-68 srvctl add scan_listener Command Parameters

| Parameter                                                                                                 | Description                                                                                                                                                                                                                                                                                          |
|:----------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`                                                                                | The optional network number from which SCAN VIPs are obtained. If you do not specify this parameter, then the SCAN VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained.                                                                                        |
| `-listener ``lsnr_name_prefix`                                                                            | The SCAN listener name prefix.                                                                                                                                                                                                                                                                       |
| `-skip`                                                                                                   | Skip checking of the ports.                                                                                                                                                                                                                                                                          |
| `-endpoints "[TCP:]``port_list``[/IPC:``key``] [/NMP:``pipe_name``][/{TCPS|SDP|EXADIRECT}``port_list``]"` | Protocol specifications for the SCAN listener. Use `port_list` to specify a comma-delimited list of TCP ports or SCAN listener endpoints.<br>You can also specify endpoints for TCPS, SDP, and EXADIRECT ports.<br>Note: You can modify this attribute using Online Resource Attribute Modification. |
| `-invitednodes "``node_list``"`                                                                           | A comma-delimited list of host names from outside the cluster that are allowed to register with the SCAN listener.                                                                                                                                                                                   |
| `-invitedsubnets "``subnet_list``"`                                                                       | A comma-delimited list of subnets from outside the cluster that are allowed to register with the SCAN listener. You can specify the subnets using either CIDR notation or wildcards (such as 192.168.\*).                                                                                            |
| `-clientcluster ``cluster_name`                                                                           | The name of the cluster that is running the SCAN listener you want to share.                                                                                                                                                                                                                         |
| `-clientdata ``file_name`                                                                                 | The name of the cluster that is running the shared SCAN listener.                                                                                                                                                                                                                                    |

##### Usage Notes

- The number of SCAN listener resources created is the same as the number of SCAN VIP resources.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl add scan_listener -listener myscanlistener

#### srvctl config scan_listener

Displays the configuration information for all SCAN listeners, by default, or a specific listener identified by network number or ordinal_number.

##### Syntax

    srvctl config scan_listener [[-netnum network_number] [-scannumber ordinal_number]
     [-clientcluster cluster_name] | -all]

##### Parameters

Table A-69 srvctl config scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                           |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | Use this parameter to view the configuration of the listener for a specific SCAN VIP.                                                                 |
| `-scannumber ``ordinal_number`  | Use this parameter to specify any one of the three SCAN VIPs, using values from 1 to 3, for which you want to view the configuration of the listener. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                     |
| `–all`                          | Alternative to specifying network or ordinal numbers, you can use this parameter to view the configuration of the listeners for all of the SCAN VIPs. |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

This command returns output similar to the following:

    $ srvctl config scan_listener -scannumber 1

    SCAN Listener LISTENER_SCAN1 exists. Port: TCP:1529
    Registration invited nodes:
    Registration invited subnets:
    SCAN Listener is enabled.
    SCAN Listener is individually enabled on nodes:
    SCAN Listener is individually disabled on nodes:

#### srvctl disable scan_listener

Disables all SCAN listeners, by default, or a specific listener identified by an ordinal number or client cluster.

##### Syntax

    srvctl disable scan_listener [-netnum network_number] [-scannumber ordinal_number]
      [-clientcluster cluster_name]

##### Parameters

Table A-70 srvctl disable scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                        |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | Use this parameter to disable SCAN listeners for a specific network number.                                                                                        |
| `-scannumber ``ordinal_number`  | Use this parameter to disable any one of the three SCAN VIPs, using values from 1 to 3. If you do not use this parameter, then SRVCTL disables all SCAN listeners. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                                  |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

The following example disables the SCAN listener identified as 1:

    $ srvctl disable scan_listener -scannumber 1

#### srvctl enable scan_listener

Enables all SCAN listeners, by default, or a specific listener identified by its ordinal number.

##### Syntax

    srvctl enable scan_listener [-netnum network_number] [-scannumber ordinal_number]
      [-clientcluster <cluster_name>]

##### Parameters

Table A-71 srvctl enable scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                      |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | Use this parameter to enable the listener for a specific SCAN VIP.                                                                                               |
| `-scannumber ``ordinal_number`  | Use this parameter to enable any one of the three SCAN VIPs, using values from 1 to 3. If you do not use this parameter, then SRVCTL enables all SCAN listeners. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                                |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

The following example enables the SCAN listener identified as 1:

    $ srvctl enable scan_listener -scannumber 1

#### srvctl modify scan_listener

Modifies the SCAN listener to match that of the SCAN VIP, or modifies the SCAN listener endpoints or service registration restrictions.

##### Syntax

    srvctl modify scan_listener {-update | -endpoints [TCP:]port_list[/IPC:key]
         [/NMP:pipe_name][/{TCPS|SDP|EXADIRECT}port_list]"} [-invitednodes "node_list"]
         [-invitedsubnets "subnet_list"] [-clientcluster cluster_name]

##### Parameters

Table A-72 srvctl modify scan_listener Command Parameters

| Parameter                                                                                                  | Description                                                                                                                                                                                                                             |
|:-----------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-update`                                                                                                  | Use this parameter to update SCAN listener configuration to match the current SCAN VIP configuration. This parameter adds new resources or removes existing SCAN listener resources to match the number of SCAN VIP resources.          |
| `-endpoints "[TCP:]``port_list``[/IPC:``key``] [/NMP:``pipe_name``][/{TCPS|SDP|EXADIRECT}``port_list``]"]` | Protocol specifications for the SCAN listener. Use `port_list` to specify a comma-delimited list of TCP ports or listener endpoints.<br>You can also specify endpoints for TCPS, SDP, and EXADIRECT ports.                              |
| `-invitednodes "``node_list``"`                                                                            | Use this parameter to specify a comma-delimited list of host names from outside the cluster that are allowed to register with the SCAN listener.                                                                                        |
| `-invitedsubnets "``subnet_list``"`                                                                        | Use this parameter to specify a comma-delimited list of subnets from outside the cluster that are allowed to register with the SCAN listener. You can specify the subnets using either CIDR notation or wildcards (such as 192.168.\*). |
| `-clientcluster ``cluster_name`                                                                            | The name of the cluster that is running the shared SCAN listener.                                                                                                                                                                       |

##### Example

Assume your system currently has a SCAN named `scan_name1`, and you recently modified the DNS entry to resolve to three IP addresses instead of one. After running the `srvctl modify scan` command to create additional SCAN VIP resources, use the following command to create Oracle Clusterware resources for the additional two SCAN listeners to go with the two additional SCAN VIPs:

    $ srvctl modify scan_listener -update

#### srvctl predict scan_listener

Predicts the consequences of SCAN listener failure.

##### Syntax

    srvctl predict scan_listener -scannumber ordinal_number [-verbose]

##### Usage Notes

- Use the `-scannumber` parameter to specify any one of the three SCAN listeners for which you want to predict the consequences of a failure. The range of values you can specify for this parameter is 1 to 3.

- Optionally, you can use the `–verbose` parameter to display detailed output.

#### srvctl relocate scan_listener

Relocates a specific SCAN listener from its current hosting node to another node within the cluster.

##### Syntax

    srvctl relocate scan_listener -scannumber ordinal_number [-node node_name]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Specify an ordinal number that identifies which SCAN listener you want to relocate. The range of values you can specify for this parameter is 1 to 3.

- Optionally, you can specify the name of a single node to which you want to relocate the SCAN listener. If you do not specify this parameter, then SRVCTL chooses the node to which the SCAN listener is relocated.

##### Example

The following example relocates the SCAN listener identified as 3 to `node2` of the cluster:

    $ srvctl relocate scan_listener -scannumber 3 -node node2

#### srvctl remove scan_listener

Removes Oracle Clusterware resources from all SCAN listeners.

##### Syntax

    srvctl remove scan_listener [-netnum network_number] [-clientcluster cluster_name]
      [-force] [-noprompt]

##### Parameters

Table A-73 srvctl remove scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                                                                   |
|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | The optional network number from which SCAN VIPs are obtained. If you do not specify this parameter, then the SCAN VIPs are obtained from the same default network from which the `nodeapps` VIP is obtained. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                                                                             |
| `-force`                        | Removes the SCAN listener without stopping the SCAN listener if it is running.                                                                                                                                |
| `–noprompt`                     | Use this parameter to suppress all prompts.                                                                                                                                                                   |

##### Example

An example of this command is:

    $ srvctl remove scan_listener -force

#### srvctl start scan_listener

Starts all SCAN listeners, by default, or a specific listener on all nodes or a specific node in the cluster.

##### Syntax

    srvctl start scan_listener [-netnum network_number] [-scannumber ordinal_number]
      [-node node_name] [-clientcluster cluster_name]

##### Parameters

Table A-74 srvctl start scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                                        |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | Use this parameter to start SCAN listeners for a specific network number.                                                                                                          |
| `-scannumber ``ordinal_number`  | Use this parameter to start one of the three SCAN VIPs, using values from 1 to 3. If you do not use this parameter, then SRVCTL starts all SCAN listeners.                         |
| `-node ``node_name`             | Specify the name of a single node on which you want to start a SCAN listener. If you do not use this parameter, then SRVCTL starts the SCAN listeners on all nodes in the cluster. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                                                  |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

The following example starts the SCAN listener identified as 1:

    $ srvctl start scan_listener -scannumber 1

#### srvctl status scan_listener

Displays the status for all SCAN listeners, by default, or a specific listener.

##### Syntax

    srvctl status scan_listener [[-netnum network_number] [-scannumber ordinal_number]
       | [-clientcluster cluster_name] | -all] [-verbose]

##### Parameters

Table A-75 srvctl status scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | The network number. The default network number is 1.                                                                                                                                                                                       |
| `-scannumber ``ordinal_number`  | An ordinal number that identifies a specific SCAN listener. The range of values you can specify for this parameter is 1 to 3. If you do not use this parameter, then the utility displays the status of all SCAN listeners in the cluster. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                                                                                                          |
| `-all`                          | Display the status for SCAN listeners for all networks.                                                                                                                                                                                    |
| `-verbose`                      | Display detailed information.                                                                                                                                                                                                              |

##### Usage Notes

This command is only available with Oracle Clusterware.

#### srvctl stop scan_listener

Stops all SCAN listeners, by default, that are in a running or starting state, or a specific listener identified by an ordinal number.

##### Syntax

    srvctl stop scan_listener [-netnum network_number] [-scannumber ordinal_number]
      [-clientcluster cluster_name] [-force]

##### Parameters

Table A-76 srvctl stop scan_listener Command Parameters

| Parameter                       | Description                                                                                                                                                  |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``network_number`      | Use this parameter to stop SCAN listeners for a specific network number.                                                                                     |
| `-scannumber ``ordinal_number`  | Use this parameter to stop any one of the three SCAN VIPs, using values from 1 to 3. If you do not use this parameter, then SRVCTL stops all SCAN listeners. |
| `-clientcluster ``cluster_name` | The name of the cluster that is running the shared SCAN listener.                                                                                            |
| `-force`                        | Stops the SCAN listener regardless of any dependencies.                                                                                                      |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

The following example stops the SCAN listener identified as 1:

    $ srvctl stop scan_listener -scannumber 1

#### srvctl update scan_listener

Updates the SCAN listeners to listen on the new endpoints.

##### Syntax

    srvctl update scan_listener

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- This command does not accept any additional parameters, except for `-help`.

#### srvctl relocate server

Relocates servers to a server pool in the cluster.

##### Syntax

    srvctl relocate server -servers "server_name_list" -serverpool pool_name
       [-eval] [-force]

##### Parameters

Table A-77 srvctl relocate server Command Parameters

| Parameter                         | Description                                                                                                                                                                   |
|:----------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-servers "``server_name_list``"` | Specify either a single server name or a comma-delimited list of server names enclosed in double quotation marks (`""`) that you want to relocate to a different server pool. |
| `-serverpool ``pool_name`         | Specify the name of the server pool to which you want to move servers.                                                                                                        |
| `–eval`                           | Optionally, you can use this parameter to hypothetically evaluate the impact of the command on the system.                                                                    |
| `–force`                          | Optionally, you can use this parameter to force the relocation of servers even if it means stopping some resources.                                                           |

##### Example

The following example relocates two servers to a different server pool:

    $ srvctl relocate server -servers "server1, server2" -serverpool sp3

#### srvctl status server

Displays the current state of specific servers.

##### Syntax

    srvctl status server -server "server_name_list" [-detail]

##### Usage Notes

- Use the `–server` parameter to specify a single server name or a comma-delimited list of server names enclosed in double quotation marks (`""`) for which you want to check the status.

- Optionally, you can use the `–detail` parameter to print detailed status information.

#### srvctl add service

Adds services to a database and assigns them to instances.

##### Syntax

Use this command with one of the following syntax models.

To add a service to a policy-managed database:

    srvctl add service -db db_unique_name -service service_name_list [-eval]
       -serverpool server_pool [-pdb pluggable_database]
       [-cardinality {UNIFORM | SINGLETON}] [-edition edition_name]
       [-netnum network_number] [-role "[PRIMARY][,PHYSICAL_STANDBY][,LOGICAL_STANDBY][,SNAPSHOT_STANDBY]"]
       [-policy {AUTOMATIC | MANUAL}] [-notification {TRUE | FALSE}] [-rfpool pool_name]
       [-clbgoal {SHORT | LONG}] [-failovertype {NONE|SESSION|SELECT|TRANSACTION|AUTO}]
       [-rlbgoal {NONE | SERVICE_TIME | THROUGHPUT}] [-dtp {TRUE | FALSE}]
       [-failovermethod {NONE | BASIC}] [-failoverretry failover_retries]
       [-drain_timeout timeout] [-stopoption {NONE|IMMEDIATE|TRANSACTIONAL}]
       [-failover_restore {NONE|LEVEL1|AUTO}] [-failoverdelay failover_delay]
       [-gsmflags gsm_flags] [-sql_translation_profile sql_translation_profile]
       [-global {TRUE | FALSE}] [-maxlag max_lag_time] [-commit_outcome {TRUE|FALSE}]
       [-retention retention_time] [-replay_init_time replay_initiation_time]
       [-session_state {STATIC | DYNAMIC | AUTO}] [-pqservice pq_service]
       [-pqpool pq_pool] [-css_critical {yes | no}] [-force]

To add a service to an administrator-managed database:

    srvctl add service -database db_unique_name -service service_name_list
       [-pdb pluggable_database] [-eval]
       [-preferred preferred_list] [-available available_list] [-failback {YES | NO}]
       [-netnum network_number] [-tafpolicy {BASIC | NONE}]
       [-edition edition_name]
       [-role "[PRIMARY][,PHYSICAL_STANDBY][,LOGICAL_STANDBY][,SNAPSHOT_STANDBY]"
       [-policy {AUTOMATIC | MANUAL}] [-notification {TRUE | FALSE}]
       [-clbgoal {SHORT | LONG}] [-failovertype {NONE|SESSION|SELECT|TRANSACTION|AUTO}]
       [-rlbgoal {NONE | SERVICE_TIME | THROUGHPUT}] [-dtp {TRUE | FALSE}]
       [-failovermethod {NONE | BASIC}] [-failoverretry failover_retries]
       [-drain_timeout timeout] [-stopoption {NONE|IMMEDIATE|TRANSACTIONAL}]
       [-failover_restore {NONE|LEVEL1|AUTO}] [-failoverdelay failover_delay]
       [-sql_translation_profile sql_translation_profile]
       [-global {TRUE | FALSE}] [-maxlag max_lag_time] [-commit_outcome {TRUE|FALSE}]
       [-retention retention_time] [-replay_init_time replay_initiation_time]
       [-session_state {STATIC|DYNAMIC|AUTO}] [-force] [-verbose]

To update the preferred and available lists of an existing service:

    srvctl add service -db db_unique_name -service service_name_list
       -update {-prefered preferred_list | -available available_list} [-force]
       [-verbose]

##### Parameters

The following table lists and describes all the `srvctl add service` parameters and whether they can be used when adding a service to either an Oracle RAC database or non-cluster database.

Table A-78 srvctl add service Command Parameters

| Parameter                                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:--------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                                                            | Unique name for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-service ``service_name_list`                                                                    | The `service_name``.``service_domain` should be unique within the cluster unless you want to spread connections across multiple databases that offer the same service. If you do not specify the service domain as part of the service name (such as `sales.example.com`), then the `DB_DOMAIN` database attribute is appended to the service name. You can specify one service or several services in a comma-delimited list.<br>Note: The `-service` parameter has a 4 kilobyte (KB) limit for its value. Therefore, the total length of the names of all services assigned to an instance cannot exceed 4 KB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-eval`                                                                                           | Use this parameter to hypothetically evaluate the impact of the command on the system.<br>Note: You can only use this parameter with a policy-managed service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-edition ``edition_name`                                                                         | The initial session edition of the service.<br>When an edition is specified for a service, all subsequent connections that specify the service use this edition as the initial session edition. However, if a session connection specifies a different edition, then the edition specified in the session connection is used for the initial session edition.<br>SRVCTL does not validate the specified edition name. During connection, the connect user must have `USE` privilege on the specified edition. If the edition does not exist or if the connect user does not have `USE` privilege on the specified edition, then an error is raised.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-sql_translation_profile ``profile_name`                                                         | Use this parameter to specify a [SQL translation profile](glossary.md) for a service that you are adding after you have migrated applications from a non-Oracle database to an Oracle database.<br>This parameter corresponds to the SQL translation profile parameter in the `DBMS_SERVICE` service attribute.<br>Notes:<br>• Before using the SQL translation feature, you must migrate all server-side application objects and data to the Oracle database.<br>• Use the `srvctl config service` command to display the SQL translation profile.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-preferred ``preferred_list`                                                                     | A list of preferred instances on which the service runs when the database is administrator managed.<br>The list of preferred instances must be mutually exclusive with the list of available instances.<br>Note: This parameter can be used only with Oracle RAC and only for administrator-managed databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-available ``available_list`                                                                     | A list of available instances to which the service fails over when the database is administrator managed.<br>The list of available instances must be mutually exclusive with the list of preferred instances.<br>Note: This parameter can be used only with Oracle RAC and only for administrator-managed databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-failback {YES | NO}`                                                                            | If a service fails over to an available instance after the list of preferred instances was exhausted, then, if this parameter is set to `YES`, the service automatically fails back to a preferred instance when one becomes available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-serverpool ``server_pool`                                                                       | The name of a server pool used when the database is policy managed.<br>Note: This parameter can be used only with Oracle RAC and only for policy-managed databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-cardinality {UNIFORM | SINGLETON}`                                                              | The cardinality of the service, either `UNIFORM` (offered on all instances in the server pool) or `SINGLETON` (runs on only one instance at a time).<br>Notes:<br>• This parameter can be used only with Oracle RAC and only for policy-managed databases.<br>• For policy-managed Oracle RAC One Node databases, all services must be `SINGLETON`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-netnum ``network_number`                                                                        | Use this parameter to determine on which network this service is offered. The service is configured to depend on VIPs from the specified network.<br>Notes:<br>• If you omit this parameter, then the default is taken from the database configuration, which you specify using `srvctl add database` or `srvctl modify database`, with the `-defaultnetwork` parameter to specify the default network for that database's services.<br>• This parameter can be used only with Oracle RAC and Oracle RAC One Node database configurations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-tafpolicy {BASIC | NONE}`                                                                       | TAF policy specification (for administrator-managed databases only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-role "[PRIMARY][,PHYSICAL_STANDBY] [,LOGICAL_STANDBY][,SNAPSHOT_STANDBY]"`                      | The service role. You can specify one or more roles in a comma-delimited list.<br>Use this option to indicate that the service should only be automatically started upon database open when the Oracle Data Guard database role matches one of the specified service roles.<br>Using SRVCTL to manually start a service is not affected by the service role.<br>Note: The `-role` parameter is only used at database startup and by the Oracle Data Guard Broker. All manual service startup must specify the name of the service to be started by the user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-policy {AUTOMATIC | MANUAL}`                                                                    | Service management policy.<br>If `AUTOMATIC` (the default), then the service is automatically started upon restart of the database, either by a planned restart (with SRVCTL) or after a failure. Automatic restart is also subject to the service role, however (the `-role` parameter).<br>If `MANUAL`, then the service is never automatically restarted upon planned restart of the database (with SRVCTL). A `MANUAL` setting does not prevent Oracle Clusterware from monitoring the service when it is running and restarting it if a failure occurs.<br>Note: Using CRSCTL to stop and start the Oracle Clusterware restarts the service in the same way that a failure does.                                                                                                                                                                                                                                                                                                                                                                                                |
| `-notification {TRUE | FALSE}`                                                                    | Enable Fast Application Notification (FAN) for OCI connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-rfpool ``pool_name`                                                                             | Specify the name of the reader farm server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-dtp {TRUE | FALSE}`                                                                             | Indicates whether Distributed Transaction Processing should be enabled for this service. This service will either be a singleton service in a policy-managed database or a preferred service on a single node in an administrator-managed database.<br>Note: This parameter can be used only with Oracle RAC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-clbgoal {SHORT | LONG}`                                                                         | Connection Load Balancing Goal. Use a value of `SHORT` for this parameter for run-time load balancing, or if using an integrated connection pool. Use a value of `LONG` for this parameter for long running connections, such as batch jobs, that you want balanced by the number of sessions per node for the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-rlbgoal {NONE | SERVICE_TIME | THROUGHPUT}`                                                     | Runtime Load Balancing Goal (for the Load Balancing Advisory). Set this parameter to `SERVICE_TIME` to balance connections by response time. Set this parameter to `THROUGHPUT` to balance connections by throughput.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-failovertype {NONE | SESSION | SELECT | TRANSACTION | AUTO}`                                    | Set the failover type.<br>To enable Application Continuity for Java, set this parameter to `TRANSACTION`. To enable Transparent Application Continuity, set this parameter to `AUTO`.<br>To enable TAF for OCI, set this parameter to `SELECT` or `SESSION`.<br>Note: If you set `-failovertype` to `TRANSACTION`, then you must set `-commit_outcome` to `TRUE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-failovermethod {NONE | BASIC}`                                                                  | TAF failover method (for backward compatibility only).<br>If the failover type (`-failovertype`) is set to a value other than `NONE`, then you should choose `BASIC` for this parameter.<br>Note: This parameter can be used only with Oracle RAC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-failoverretry ``failover_retries`                                                               | For Application Continuity and TAF, this parameter determines the number of attempts to connect after an incident.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-drain_timeout ``timeout`                                                                        | Specify the time, in seconds, allowed for resource draining to be completed. Accepted values are an empty string (""), 0, or any positive integer. The default value is an empty string, which means that this parameter is not set. If it is set to 0, then draining occurs, immediately.<br>The draining period is intended for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. When set on the service this value is used when the command line value is not set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-stopoption {NONE|IMMEDIATE|TRANSACTIONAL}`                                                      | Specify the mode in which the service is stopped. When set on the service, this value is used if you do not set the value on the command line.<br>`IMMEDIATE` permits sessions to drain before the service is stopped.<br>`TRANSACTIONAL` permits sessions to drain for the amount of time specified in the `-drain_timeout` parameter. The service is stopped when the time limit is reached and any remaining sessions are terminated.<br>If you specify `NONE`, then no sessions are terminated.<br>The default is taken from the service setting, when specified on the service. Otherwise the default is `NONE`.<br>Note: You must use the `-stopoption` parameter with the `-force` parameter.                                                                                                                                                                                                                                                                                                                                                                                 |
| `-failover_restore {NONE|LEVEL1|AUTO}`                                                            | For Application Continuity, when you set the `-failover_restore` parameter, session states are restored before replaying. Use `LEVEL1` for ODP.NET and Java with Application Continuity to restore the initial state.<br>Set this parameter to `AUTO` to enable Transparent Application Continuity to restore session states.<br>For OCI applications using TAF or Application Continuity, setting `-failover_restore` to `LEVEL1` restores the current state. If the current state differs from the initial state, then a TAF callback is required. This restriction applies only to OCI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-failoverdelay ``failover_delay`                                                                 | For Application Continuity and TAF, this parameter specifies the time delay (in seconds) between reconnect attempts per incident at failover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-gsmflags ``gsm_flags`                                                                           | Set locality and region failover values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-pdb ``pluggable_database`                                                                       | The name of the pluggable database (PDB).<br>Note: You can specify a PDB property when you create or modify a service. The PDB property associates the service with the specified PDB. You can view the PDB property for a service by querying the ALL_SERVICES data dictionary view or, when using the SRVCTL utility, by running the `srvctl config service` command.<br>When you create or modify a service with the specified PDB, SRVCTL does not check if the PDB exists. Before running this command, you must ensure that the PDB exists.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-global {TRUE | FALSE}`                                                                          | Indicates whether this is a Global Data Services service.<br>Note: This parameter can only be used with Global Data Services.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-maxlag ``maximum_lag_time`                                                                      | Maximum replication lag time in seconds. Must be a non-negative integer. The default value is `ANY`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-commit_outcome {TRUE | FALSE}`                                                                  | Enable Transaction Guard; when set to `TRUE`, the commit outcome for a transaction is accessible after the transaction's session fails due to a recoverable outage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-retention ``retention_time`                                                                     | If `-commit_outcome` is set to `TRUE`, then this parameter determines the amount of time (in seconds) that the commit outcome is retained in the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-replay_init_time ``replay_initialization_time`                                                  | For Application Continuity, this parameter specifies the difference between the time, in seconds, of original execution of the first operation of a request and the time that the replay is ready to start after a successful reconnect. Application Continuity will not replay after the specified amount of time has passed. This parameter is intended to avoid the unintentional execution of a transaction when a system is recovered after a long period. The default is 5 minutes (`300`). The maximum value is 24 hours (`86400`). If the `-failover_type` parameter is not set to `TRANSACTION`, then you cannot use this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-session_state {STATIC | DYNAMIC | AUTO}`                                                        | For Application Continuity; this parameter describes how the non-transactional session state is changed by the application within a request. Examples of session state are NLS settings, optimizer preferences, event settings, PL/SQL global variables, and temporary tables. For Transparent Application Continuity `session_state` is always set to `AUTO`. Session state is tracked automatically.<br>This parameter is considered only if `-failovertype` is set to `TRANSACTION` for Application Continuity or `AUTO` for Transparent Application Continuity.<br>• If `failover_type` is set to `TRANSACTION`, then Oracle recommends a value of `DYNAMIC` for `session_state`.<br>• If `failover_type` is set to `AUTO`, then `session_state` defaults to `AUTO`.<br>• If `failover_type` is set to any value other than `TRANSACTION` or `AUTO`, then the value of `session_state` is not set.<br>If non-transactional values change after the request starts, then set this parameter to either `DYNAMIC` or `AUTO`. Most applications should use `DYNAMIC` or `AUTO` mode. |
| `-pqservice ``pq_service`                                                                         | Specify a parallel query service name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-pqpool ``pq_pool`                                                                               | Specify a parallel query server pool.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-update {``-preferred`` ``new_preferred_instance`` | ``-available`` ``new_available_instance``}` | Add a new preferred or available instance to the service configuration. `-preferred` specifies the name of the instance to add to the list of preferred instances for the service. `-available` specifies the name of the instance to add to the list of available instances for the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-css_critical {yes | no}`                                                                        | You can add weight to a service by setting this parameter to `YES`. In the event of a node failure within the cluster, Oracle Clusterware will evict the node with the least amount of weight, ensuring that critical services remain available.<br>Note: You can use this parameter only on an administrator-managed node. Should the node become policy managed, at some point, this parameter will no longer apply.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-verbose`                                                                                        | Display verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-force`                                                                                          | Force the add operation even though a listener is not configured for a network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

This command does not accept placement parameters for Oracle RAC One Node and Standard Edition High Availability databases.

##### Examples

Use this example syntax to add the `gl.example.com` service to the `my_rac` database with Fast Application Notification enabled for OCI connections, a failover method of `BASIC`, a Connection Load Balancing Goal of `LONG`, a failover type of `SELECT`, and 180 failover retries with a failover delay of 5 seconds:

    $ srvctl add service -db my_rac -service gl.example.com -notification TRUE -failovermethod BASIC -failovertype SELECT -failoverretry 180 -failoverdelay 5 -clbgoal LONG

Use this example syntax to add a named service to a database with preferred instances and available instances and enabled for TAF:

    $ srvctl add service -db crm -service sales -preferred crm01,crm02 -available crm03 -tafpolicy BASIC

#### srvctl config service

Displays the configuration for a service.

##### Syntax

    srvctl config service {-db db_unique_name [-service service_name]
       | -serverpool pool_name [-db db_unique_name]} [-verbose]

##### Parameters

Table A-79 srvctl config service Command Parameters

| Parameter                 | Description                                                                                                                                                                                                                   |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`    | Unique name for the database.                                                                                                                                                                                                 |
| `-service ``service_name` | Optionally, you can specify the name of a service.<br>If you do not use this parameter, then SRVCTL displays the configuration information for all services configured for the database.                                      |
| `-serverpool ``pool_name` | Alternatively, you can use this parameter to specify the name of a server pool for which you want to view the service configuration. Optionally, you can also specify a particular database on which the server pool resides. |
| `-verbose`                | Displays verbose output.                                                                                                                                                                                                      |

##### Usage Notes

The `srvctl config service` command shows exactly the string value you specified for the edition using the `srvctl add | modify service` commands. If you specified the edition in upper case, then `srvctl config service` displays upper case. If it is surrounded by double quotation marks (`""`), then the command displays the double quotation marks. Otherwise, the command displays an empty string.

##### Examples

This command returns information similar to the following for a policy-managed database:

    $ srvctl config service -db crm -service webapps

    Service name: webapps
    Service is enabled
    Server pool: sales
    Cardinality: SINGLETON
    Disconnect: false
    Service role: PRIMARY
    Management policy: AUTOMATIC
    DTP transaction: false
    AQ HA notifications: false
    Failover type: NONE
    Failover method: NONE
    TAF failover retries: 0
    TAF failover delay: 0
    Connection Load Balancing Goal: LONG
    Runtime Load Balancing Goal: NONE
    TAF policy specification: NONE
    Service is enabled on nodes:
    Service is disabled on nodes:
    Edition: "my Edition"

This command returns information similar to the following for a administrator-managed database:

    $ srvctl config service -db crm -service webapps

    Service name: webapps
    Service is enabled
    Server pool: sales
    Cardinality: 1
    Disconnect: false
    Service role: PRIMARY
    Management policy: AUTOMATIC
    DTP transaction: false
    AQ HA notifications: false
    Failover type: NONE
    Failover method: NONE
    TAF failover retries: 0
    TAF failover delay: 0
    Connection Load Balancing Goal: LONG
    Runtime Load Balancing Goal: NONE
    TAF policy specification: NONE
    Preferred instances: crm_1
    Available instances:
    Edition: "my Edition"

Service configuration for administrator-managed Oracle RAC One Node databases displays the one instance as preferred.

#### srvctl disable service

Disables a service.

Disabling an entire service affects all of the instances, disabling each one. If the entire service is already disabled, then running this command on the entire service returns an error. This means that you cannot always use the entire set of service operations to manipulate the service indicators for each instance.

##### Syntax

    srvctl disable service -db db_unique_name -services "service_name_list"
       [-instance instance_name | -node node_name]

##### Parameters

Table A-80 srvctl disable service Command Parameters

| Parameter                           | Description                                                                                                                                                                                                                                                                               |
|:------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`              | Specify a unique name for the database for which you want to disable the service.                                                                                                                                                                                                         |
| `-services "``service_name_list``"` | Specify a comma-delimited list of service names enclosed in double quotation marks (`""`), or a single service name, that you want to disable.                                                                                                                                            |
| `-instance ``instance_name`         | Optionally, you can specify the name of the instance for which you want to disable the service.<br>Notes:<br>• Use this parameter with administrator-managed databases.<br>• You can only use this parameter with Oracle Clusterware and Oracle RAC.                                      |
| `-node ``node_name`                 | Alternative to using the `–instance` parameter, you can use this parameter to specify the name of the node on which to disable the service.<br>Notes:<br>• Use this parameter with policy-managed databases.<br>• You can only use this parameter with Oracle Clusterware and Oracle RAC. |

##### Examples

The following example globally disables two services for the `CRM` database:

    $ srvctl disable service -db crm -service "crm,marketing"

The following example disables a service for the `CRM` database that is running on the `CRM1` instance, resulting in the service still being available for the database, but on one less instance:

    $ srvctl disable service -db crm -service crm -instance crm1

#### srvctl enable service

Enables a service for Oracle Clusterware.

Enabling an entire service also affects the enabling of the service over all of the instances by enabling the service on each one. If the entire service is already enabled, then running this command does not affect all of the instances and enable them but, instead, returns an error. Therefore, you cannot always use the entire set of service operations to manipulate the service indicators for each instance.

##### Syntax

    srvctl enable service -db db_unique_name -service "service_name_list"
       [-instance instance_name | -node node_name]

##### Parameters

Table A-81 srvctl enable service Command Parameters

| Parameter                          | Description                                                                                                                                                                                                                                                                              |
|:-----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`             | Specify a unique name for the database for which you want to enable the service.                                                                                                                                                                                                         |
| `-service "``service_name_list``"` | Specify a single service name or a comma-delimited list of service names enclosed in double quotation marks (`""`) that you want to enable.                                                                                                                                              |
| `-instance ``instance_name`        | Optionally, you can use this parameter to specify the name of the database instance where you want the service to run.<br>Notes:<br>• Use this parameter for administrator-managed databases.<br>• You can only use this parameter with Oracle Clusterware and Oracle RAC.               |
| `-node ``node_name`                | Alternative to using the `–instance` parameter, you can use this parameter to specify the name of the node on which to enable the service.<br>Notes:<br>• Use this parameter with policy-managed databases.<br>• You can only use this parameter with Oracle Clusterware and Oracle RAC. |

##### Examples

The following example globally enables a service:

    $ srvctl enable service -db crm -service crm

The following example enables a service to use a preferred instance:

    $srvctl enable service -db crm -service crm -instance crm1

#### srvctl modify service

Modifies service configurations.

This command supports some online modifications to the service, such as:

- Moving a service member from one instance to another

- Performing online changes to service attributes from `DBMS_SERVICE` (for example, failover delay, runtime load balancing goal, and so on)

- Adding a new preferred or available instance

- Removing preferred or available instances for a service

**Caution:**

Oracle recommends that you limit configuration changes to the minimum requirement and that you not perform other service operations while the online service modification is in progress.

##### Syntax and Parameters

Use one of the following forms of the `srvctl modify service` command, depending on the task you want to perform, with the specified syntax:

To move a service from one instance to another:

    srvctl modify service -db db_unique_name -service service_name
          -oldinst old_instance_name -newinst new_instance_name [-force]

**Note:**

This form of the command is only available with Oracle Clusterware.

Table A-82 srvctl modify service Parameters for Moving a Service

| Parameter                      | Description                                                                                   |
|:-------------------------------|:----------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`         | Specify the unique name for the database.                                                     |
| `-service ``service_name`      | Specify a service name. If you do not specify a service name, then SRVCTL moves all services. |
| `-oldinst ``old_instance_name` | Specify the name of the instance from which you want to move the service.                     |
| `-newinst ``new_instance_name` | Specify the name of the instance to which you want to move the service.                       |
| `-force`                       | Force the modify operation, stopping the service on some nodes, as necessary.                 |

To change an available instance to a preferred instance for a service:

    srvctl modify service -db db_unique_name -service service_name
          -available avail_inst_name [-failback {YES|NO}] -toprefer [-force]

**Note:**

This form of the command is only available with Oracle Clusterware and does not accept placement parameters for Oracle RAC One Node databases. This command also does not move or otherwise disconnect the service but only modifies the service attributes.

Table A-83 srvctl modify service Parameters for Changing to a Preferred Instance

| Parameter                          | Description                                                                                                                                                                                                                                                                      |
|:-----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`             | Specify the unique name for the database.                                                                                                                                                                                                                                        |
| `-service ``service_name`          | Specify the name of the service you want to modify.                                                                                                                                                                                                                              |
| `-available ``available_inst_name` | Specify the name of the available instance you want to change.                                                                                                                                                                                                                   |
| `-failback {YES|NO}`               | If a service fails over to an available instance after the list of preferred instances was exhausted, then, if this parameter is set to `YES`, then the service automatically fails back to a preferred instance when one becomes available.                                     |
| `-toprefer`                        | Specify this parameter to change the instance status to preferred.                                                                                                                                                                                                               |
| `-force`                           | Force the modify operation. For planned operations, it is best to use an Oracle Connection Pool with FAN. The FAN planned event causes the Oracle pool to drain the requests with no interruption to the users. Sessions that are connected to an instance are not disconnected. |

To change the available and preferred status for multiple instances:

    srvctl modify service -db db_unique_name -service service_name
         -modifyconfig -preferred "preferred_list" [-available "available_list"]
         [-force]

**Note:**

This form of the command is only available with Oracle Clusterware and does not accept placement parameters for Oracle RAC One Node databases. This command also does not move or otherwise disconnect the service but only modifies the service attributes. Sessions connected to instances are not disconnected.

Table A-84 srvctl modify service Parameters for Changing the Statuses of Multiple Instances

| Parameter                                  | Description                                                                                                                                                                                                         |
|:-------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                     | Specify the unique name for the database.                                                                                                                                                                           |
| `-service ``service_name`                  | Specify the name of the service that you want to modify.                                                                                                                                                            |
| `-modifyconfig`                            | This parameter directs SRVCTL to use only the instances named for this service (unnamed instances already assigned to the service are removed).                                                                     |
| `-preferred "``preferred_instance_list``"` | Specify a comma-delimited list of preferred instances enclosed within double quotation marks ("").                                                                                                                  |
| `-available "``available_instance_list``"` | Specify a comma-delimited list of available instances enclosed within double quotation marks ("").                                                                                                                  |
| `-force`                                   | Force the modify operation. For planned operations, it is best to use an Oracle Connection Pool with FAN. The FAN planned event causes the connection pool to drain the requests with no interruption to the users. |

To modify other service attributes or to modify a service for Oracle Clusterware:

    srvctl modify service -db db_unique_name -service service_name [-eval]
     [-serverpool pool_name] [-cardinality {UNIFORM|SINGLETON}]
     [-drain_timeout timeout] [-stopoption {NONE|IMMEDIATE|TRANSACTIONAL}]
     [-pqservice pqsvc_name] [-pqpool pq_pool_list]
     [-pdb pluggable_database] [-tafpolicy {BASIC|NONE}]
     [-edition edition_name] [-role "[PRIMARY][,PHYSICAL_STANDBY]
     [,LOGICAL_STANDBY][,SNAPSHOT_STANDBY]"] [-notification {TRUE|FALSE}]
     [-dtp {TRUE|FALSE}] [-clbgoal {SHORT|LONG}] [-rlbgoal {NONE|SERVICE_TIME|THROUGHPUT}]
     [-failovertype {NONE|SESSION|SELECT|TRANSACTION|AUTO}] [-failovermethod {NONE|BASIC}]
     [-failover_restore [NONE|LEVEL1|AUTO]] [-failoverretry failover_retries]
     [-failoverdelay failover_delay] [-policy {AUTOMATIC|MANUAL}]
     [-sql_translation_profile profile_name] [-commit_outcome {TRUE|FALSE}]
     [-retention retention_time] [-replay_init_time replay_initiation_time]
     [-session_state {STATIC|DYNAMIC|AUTO}] [-global_override] [-verbose] [-force]

Table A-85 srvctl modify service Parameters

| Parameter                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`                                                       | Specify the unique name for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-service ``service_name`                                                    | Specify the name of the service you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-eval`                                                                      | Use this parameter to hypothetically evaluate the impact of the command on the system.<br>Note: You can only use this parameter with a policy-managed service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-serverpool ``pool_name`                                                    | The name of a server pool used when the database is policy managed.<br>Note: This parameter can be used only with Oracle RAC and only for policy-managed databases.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-cardinality {UNIFORM|SINGLETON}`                                           | Specify the cardinality of the service, either `UNIFORM` (offered on all instances in the server pool) or `SINGLETON` (runs on only one instance at a time).<br>Note: This parameter can be used only with Oracle Clusterware.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-drain_timeout ``timeout`                                                   | Specify the time, in seconds, allowed for resource draining to be completed. Accepted values are an empty string (""), 0, or any positive integer. The default value is an empty string, which means that this parameter is not set. If it is set to 0, then draining occurs, immediately.<br>The draining period is intended for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. When set on the service this value is used when the command line value is not set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-stopoption {NONE|IMMEDIATE|TRANSACTIONAL}`                                 | Specify the mode in which the service is stopped. If you set this parameter on the service, then this value is used if you do not set the value on the command line.<br>`IMMEDIATE` permits sessions to drain before the service is stopped.<br>`TRANSACTIONAL` permits sessions to drain for the amount of time specified in the `-drain_timeout` parameter. The service is stopped when the time limit is reached and any remaining sessions are terminated.<br>If you specify `NONE`, then no sessions are terminated.<br>The default is taken from the service setting, when specified on the service. Otherwise the default is `NONE`.<br>Note: You must use the `-stopoption` parameter with the `-force` parameter.                                                                                                                                                                                                                                                                                                                                                           |
| `-pqservice ``pqsvc_name`                                                    | Specify a comma-delimited list of parallel query service names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-pqpool ``pq_pool_list`                                                     | Specify a comma-delimited list of parallel query server pool names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-pdb ``pluggable_database`                                                  | Specify the name of a pluggable database (PDB).<br>Note: You can specify a PDB property when you create or modify a service. The PDB property associates the service with the specified PDB. You can view the PDB property for a service by querying the ALL_SERVICES data dictionary view or, when using the SRVCTL utility, by running the `srvctl config service` command.<br>When create or modify a service with the specified PDB, SRVCTL does not check if the PDB exists. Before running this command, you must ensure that the PDB exists.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-tafpolicy {BASIC|NONE}`                                                    | Specify the transaction failover (TAF) policy (for administrator-managed databases only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-edition ``edition_name`                                                    | The initial session edition of the service.<br>When an edition is specified for a service, all subsequent connections that specify the service use this edition as the initial session edition. However, if a session connection specifies a different edition, then the edition specified in the session connection is used for the initial session edition.<br>SRVCTL does not validate the specified edition name. During connection, the connect user must have `USE` privilege on the specified edition. If the edition does not exist or if the connect user does not have `USE` privilege on the specified edition, then an error is raised.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-role "[PRIMARY][,PHYSICAL_STANDBY] [,LOGICAL_STANDBY][,SNAPSHOT_STANDBY]"` | The database modes for which the service should be started automatically. You can specify one or more roles in a comma-delimited list.<br>Note: The `-role` parameter is only used at database startup and by the Oracle Data Guard Broker. All manual service startup must specify the name of the service to be started by the user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-notification {TRUE|FALSE}`                                                 | Specify a value of `TRUE` to enable Fast Application Notification (FAN) for Oracle Call Interface (OCI) connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-dtp {TRUE|FALSE}`                                                          | Specify `TRUE` to enable Distributed Transaction Processing for this service. This ensures that the service is offered at exactly one instance at a time for XA affinity.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-clbgoal {SHORT|LONG}`                                                      | Use this parameter to set a connection load balancing goal: set to `SHORT` if using runtime load balancing, set to `LONG` for long running connections, such as batch jobs or older SQL\*Forms style.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-rlbgoal {NONE|SERVICE_TIME|THROUGHPUT}`                                    | Use this parameter to set a runtime load balancing goal. Set this parameter to `SERVICE_TIME` to balance connections by response time. Set this parameter to `THROUGHPUT` to balance connections by throughput.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-failovertype {NONE|SESSION|SELECT|TRANSACTION|AUTO}`                       | Use this parameter to set the failover type.<br>To enable Application Continuity, set this parameter to `TRANSACTION`. To enable Transparent Application Continuity, set this parameter to `AUTO`.<br>To enable TAF, set this parameter to `SELECT` or `SESSION`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-failovermethod {NONE|BASIC}`                                               | Specify the TAF failover method (for backward compatibility only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-failover_restore [NONE|LEVEL1|AUTO]`                                       | For Application Continuity, when you set the `-failover_restore` parameter, session states are restored before replaying. Use `LEVEL1` for ODP.NET and Java with Application Continuity to restore the initial state.<br>Set this parameter to `AUTO` to enable Transparent Application Continuity to restore session states.<br>For OCI applications using TAF or Application Continuity, setting `-failover_restore` to `LEVEL1` restores the current state. If the current state differs from the initial state, then a TAF callback is required. This restriction applies only to OCI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-failoverretry ``failover_retries`                                          | For Application Continuity and TAF, specify the number of attempts to connect after an incident.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-failoverdelay ``failover_delay`                                            | For Application Continuity and TAF, specify the time delay (in seconds) between reconnect attempts per incident at failover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-policy {AUTOMATIC|MANUAL}`                                                 | Specify the service management policy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-sql_translation_profile ``profile_name`                                    | Use this parameter to specify a SQL translation profile for a service that you are modifying after you have migrated applications from a non-Oracle database to an Oracle database.<br>If you want to set the SQL translation profile to a NULL value, then you must enter an empty string after the `-p` flag.<br>Note: Before using the SQL translation feature, you must migrate all server-side application objects and data to the Oracle database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-commit_outcome {TRUE|FALSE}`                                               | Enable Transaction Guard; when set to `TRUE`, the commit outcome for a transaction is accessible after the transaction's session fails due to a recoverable outage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-retention ``retention_time`                                                | For Transaction Guard (with the `-commit_outcome` parameter set to `TRUE`); this parameter determines the amount of time (in seconds) that the commit outcome is retained in the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-replay_init_time ``replay_initiation_time`                                 | For Application Continuity; this parameter specifies the time, in seconds, from when the original request started. Application Continuity will not replay after the specified amount of time has passed. This attribute avoids the unintentional replay of a request when a system is recovered after a long period. The default value is 300 (5 minutes).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-session_state {STATIC|DYNAMIC|AUTO}`                                       | For Application Continuity; this parameter describes how the non-transactional session state is changed by the application within a request. Examples of session state are NLS settings, optimizer preferences, event settings, PL/SQL global variables, and temporary tables. For Transparent Application Continuity `session_state` is always set to `AUTO`. Session state is tracked automatically.<br>This parameter is considered only if `-failovertype` is set to `TRANSACTION` for Application Continuity or `AUTO` for Transparent Application Continuity.<br>• If `failover_type` is set to `TRANSACTION`, then Oracle recommends a value of `DYNAMIC` for `session_state`.<br>• If `failover_type` is set to `AUTO`, then `session_state` defaults to `AUTO`.<br>• If `failover_type` is set to any value other than `TRANSACTION` or `AUTO`, then the value of `session_state` is not set.<br>Oracle recommends a value of `AUTO` or `DYNAMIC` for most applications. If you are unsure which value to use, or if you can customize the application, then use `DYNAMIC`. |
| `-global_override`                                                           | Override value to modify the global service attributes.<br>Use this parameter with the `-role`, `-policy`, `-notification`, `-failovertype`, `-failovermethod`, `-failoverdelay`, `-failoverretry` and `-edition` parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `–verbose`                                                                   | Display verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-force`                                                                     | Force the modify operation, stopping the service on some nodes as necessary.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

##### Usage Notes

- When performing online changes to service attributes (for example, failover delay, Runtime Load Balancing Goal, and so on), the changes take effect only when the service is next (re)started.

- When a service configuration is modified so that a new preferred or available instance is added, the running state of the existing service is not affected. However, the newly added instances will not automatically provide the service, until a `srvctl start service` command is issued.

- When there are available instances for the service, and the service configuration is modified so that a preferred or available instance is removed, the running state of the service may change unpredictably:

  - The service is stopped and then removed on some instances according to the new service configuration.

  - The service may be running on some instances that are being removed from the service configuration.

  - These services will be relocated to the next free instance in the new service configuration.

Because of these considerations, when the online service is being modified, users may experience a brief service outage on some instances even if the instances are not being removed. Or users may experience a brief service outage on instances that are being removed from the service.

##### Examples

An example of moving a service member from one instance to another is:

    $ srvctl modify service -db crm -service crm -oldinst crm1 -newinst crm2

An example of changing an available instance to a preferred instance is:

    $ srvctl modify service -db crm -service crm -available crm1 -toprefer

The following command exchanges a preferred and available instance:

    $ srvctl modify service -db crm -service crm -modifyconfig -preferred "crm1" \
    -available "crm2"

**Related Topics**

- [Oracle Data Guard Broker](../dgbkr/using-data-guard-broker-to-manage-switchovers-failovers.md)
- [Oracle Database SQL Translation and Migration Guide](../drdaa/SQL-translation-framework-overview.md)

#### srvctl predict service

Predicts the consequences of service failure.

##### Syntax

    srvctl predict service -db db_unique_name -service service_name [-verbose]

##### Parameters

Table A-86 srvctl predict service Command Parameters

| Parameter                 | Description                                                                                                                                |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`    | Specify the unique name for the database on which the service operates that you want to check.                                             |
| `-service ``service_name` | Specify a single service name or a comma-delimited list of service names enclosed in double quotation marks (`""`) that you want to check. |
| `–verbose`                | Optionally, you can use this parameter to display detailed output.                                                                         |

#### srvctl relocate service

Temporarily relocates the specified service names from one specified instance to another specified instance.

This command works on only one source instance and one target instance at a time, relocating a service or all services from a single source instance to a single target instance.

##### Syntax

    srvctl relocate service -db db_unique_name [-service service_name
      | -pdb pluggable_database] {-oldinst old_inst_name
      [-newinst new_inst_name] | -currentnode source_node [-targetnode target_node]} [-drain_timeout timeout]
      [-wait YES | NO] [-pq] [-force [-noreplay]] [-eval] [-verbose]

##### Parameters

Table A-87 srvctl relocate service Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`       | Specify a unique name for the database on which the service operates that you want to relocate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-service ``service_name`    | Specify the name of the service you want to relocate. If you do not specify any services, then all services that can be relocated, are relocated. Those that cannot be relocated remain in place.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-pdb ``pluggable_database`  | Use this parameter to relocate services running on a specific pluggable database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-oldinst ``old_inst_name`   | Specify the name of the instance from which you are relocating the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-newinst ``new_inst_name`   | Specify the name of the instance to which you are relocating the service. This parameter is optional. If you do not specify an instance, then Oracle Clusterware chooses a new one.<br>Note: If you are using an administrator-managed database, then you must use the `-oldinst` and `-newinst` parameters and the target instance must be on the preferred or available list for the service.                                                                                                                                                                                                                                                                                                      |
| `-currentnode ``source_node` | Name of the node where the service is currently running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-targetnode ``target_node`  | Name of node where the service is to be relocated. If you do not specify a target node, then Oracle Clusterware chooses a new location.<br>Note: If you are using a policy-managed database, then you must use the `-currentnode` and `-targetnode` parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-drain_timeout ``timeout`   | Specify the time, in seconds, allowed for resource draining to be completed. Accepted values are an empty string (""), 0, or any positive integer. The default value is an empty string, which means that this parameter is not set. If it is set to 0, then draining occurs, immediately.<br>The draining period is intended for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. When set on the service this value is used when the command line value is not set.                                                                                                                                       |
| `-wait YES | NO`             | Choose `YES` to wait until service draining is completed on the node from which you are relocating the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-stopoption ``option`       | Specify the mode in which the service is stopped. When set on the service, this value is used if you do not set the value on the command line.<br>`IMMEDIATE` permits sessions to drain before the service is stopped.<br>`TRANSACTIONAL` permits sessions to drain for the amount of time specified in the `-drain_timeout` parameter. The service is stopped when the time limit is reached and any remaining sessions are terminated.<br>If you specify `NONE`, then no sessions are terminated.<br>The default is taken from the service setting, when specified on the service. Otherwise the default is `NONE`.<br>Note: You must use the `-stopoption` parameter with the `-force` parameter. |
| `–pq`                        | Performs the action on a parallel query service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `–force [-noreplay]`         | Disconnect all sessions during stop or relocate service operations.<br>Optionally, you can specify the `-noreplay` parameter if you do not want Application Continuity to replay in-flight transactions after a session is terminated during stop or relocate service operations.<br>The `-noreplay` parameter is not limited to use with `-force` but `-force` does require `-noreplay` if you do not want to replay in-flight transactions after you force the service to disconnect all sessions.                                                                                                                                                                                                 |
| `–eval`                      | Use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `–verbose`                   | Verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Example

To temporarily relocate a named service member for the `crm` service from the database instance `crm1` to the database instance `crm3`:

    $ srvctl relocate service -db crm -service crm -oldinst crm1 -newinst crm3

**Related Topics**

- [SQL\*Plus User's Guide and Reference](../sqpug/database-administration-with-SQL-Plus.md)

#### srvctl remove service

Removes the configuration for a service.

##### Syntax

    srvctl remove service -db db_unique_name -service service_name
       [-instance instance_name] [-global_override]

##### Parameters

Table A-88 srvctl remove service Command Parameters

| Parameter                   | Description                                                                                                                                           |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`      | Specify the unique name of the database on which the service that you want to remove operates.                                                        |
| `-service ``service_name`   | Specify the name of the service you want to remove.                                                                                                   |
| `-instance ``instance_name` | Optionally, you can specify the instance name of an administrator-managed database.<br>Note: You can only use this parameter with Oracle Clusterware. |
| `-global_override`          | Optionally, you can use this parameter to override value to operate on a global service. SRVCTL ignores this parameter a non-global service.          |

##### Examples

This following example removes the `sales` service from all instances of the clustered database named `crm`:

    $ srvctl remove service -db crm -service sales

The following example removes the `sales` service from a specific instance of the `crm` clustered database:

    $ srvctl remove service -db crm -service sales -instance crm02

#### srvctl start service

Starts a service or multiple services on a database, pluggable database, or instance.

##### Syntax

    srvctl start service [-db db_unique_name] [-service "services_list"
      [-pq] | -pdb pluggable_database | -serverpool pool_name]
      [-node node_name | -instance instance_name]
      [-global_override] [-startoption start_options] [-eval] [-verbose]

##### Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                       |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`         | Specify a unique name for the database.                                                                                                                                                                                                                                                                                           |
| `-service "``service_list``"`  | Specify a service name or a comma-delimited list of service names enclosed in double quotation marks ("").<br>If you do not include this parameter, then SRVCTL starts all of the services for the specified database.<br>Note: All manual service startup must specify the name of the service to be started by the user.        |
| `-pq`                          | Specify this parameter to restrict the start action to a parallel query service.                                                                                                                                                                                                                                                  |
| `-pdb ``pluggable_database`    | Specify the name of a pluggable database. Optionally, you can specify either the name of a node or the name of an instance to restrict the starting of services to that particular object on the pluggable database.                                                                                                              |
| `-serverpool ``pool_name`      | Alternative to using the `-pq` parameter, you can specify the name of a server pool that contains the services you want to start. Use this parameter for policy-managed databases.                                                                                                                                                |
| `-node ``node_name`            | Specify the name of a node where the services reside that you want to start. Use this parameter for policy-managed databases.                                                                                                                                                                                                     |
| `-instance ``instance_name`    | Specify the name of an instance where the services reside that you want to start. Use this parameter for administrator-managed databases.                                                                                                                                                                                         |
| `-global_override`             | Override value to operate on a global service. Use this parameter only with global services; this parameter is ignored if specified for a non-global service.                                                                                                                                                                     |
| `-startoption ``start_options` | Specify startup options used when service startup requires starting a database instance. Options include `OPEN`, `MOUNT`, and `NOMOUNT`.<br>Note: For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`. |
| `–verbose`                     | Display verbose output.                                                                                                                                                                                                                                                                                                           |

##### Usage Notes

- The `srvctl start service` command will fail if you attempt to start a service that is already running.

- The `srvctl start service` command will fail if you attempt to start a service on an instance, if that service is already running on its maximum number of instances, that is, its number of preferred instances.

- You can move a service or change the status of a service on an instance with the `srvctl modify service` and `srvctl relocate service` commands.

##### Examples

The following example starts all services on a specific database:

    $ srvctl start database -db myDB

The following examples start a list of services (optionally restricted to a parallel query services in the latter example) regardless of the pluggable database on which they may reside:

    $ srvctl start database -db myDB -service "myServ01,myServ02"
    $ srvctl start database -db myDB -service "myServ01,myServ02" -pq

The following example starts all services in a given server pool:

    $ srvctl start database -db myDB -serverpool myServerPool

The following examples start all services on a given pluggable database, optionally restricted to a single node or a single instance in the latter two examples, repectively:

    $ srvctl start service -db myDB -pdb myPDB1
    $ srvctl start service -db myDB -pdb myPDB1 -node myRACNode01
    $ srvctl start service -db myDB -pdb myPDB1 -instance myDB01

The following example starts all services, for a given database, on a given instance (for all pluggable databases):

    $ srvctl start service -db myDB -instance myDB01

The following example start all services for a given database on a given node (for all pluggable databases):

    $ srvctl start service -db myDB -node myRACNode01

The following examples start a list of services on a given node or given instance:

    $ srvctl start service -db myDB -service "myService01,myService02" -node myRACNode01
    $ srvctl start service -db myDB -service "myService01,myService02" -instance myDB01

#### srvctl status service

Displays the status of a service.

For Oracle RAC One Node databases, if there is an online database relocation in process, then this command displays the source and destination nodes and the status of the relocation, whether it is active or failed.

##### Syntax

    srvctl status service -db db_unique_name [-service "service_name_list"]
       [-force] [-verbose]

##### Parameters

Optionally, you can use this parameter to include disabled applications.

Table A-89 srvctl status service Command Parameters

| Parameter                          | Description                                                                                                                                                                                                           |
|:-----------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-db ``db_unique_name`             | Specify the unique name of the database on which the service operates for which you want to check the status.                                                                                                         |
| `-service "``service_name_list``"` | Optionally, you can specify a comma-delimited list of service names for which you want to check status.<br>If you do not use this parameter, then SRVCTL lists the status of all services for the specified database. |
| `–force`                           | Optionally, you can use this parameter to include disabled applications.                                                                                                                                              |
| `–verbose`                         | Optionally, you can use this parameter to display detailed output.                                                                                                                                                    |

#### srvctl stop service

Stops one or more services globally across the cluster database, or on the specified instance.

##### Syntax

To stop services for a particular node in the cluster:

    srvctl stop service -node node_name [-stopoption IMMEDIATE|TRANSACTIONAL|NONE]
       [-drain_timeout timeout] [-wait {YES | NO}] [-force] [-noreplay]
       [-global_override] [-verbose]

To stop services for a database:

    srvctl stop service -db db_unique_name [-pq] [-rf] [-pdb pluggable_database |
        -service "service_list" [-eval]] [-node node_name | -instance instance_name |
        -serverpool pool_name] [-stopoption IMMEDIATE|TRANSACTIONAL|NONE]
       [-drain_timeout timeout] [-wait {YES | NO}] [-force [-noreplay]
       [-global_override] [-verbose]

##### Parameters

**Note:**

Starting with Oracle Grid Infrastructure 21c, policy-managed databases are deprecated.

Table A-90 srvctl stop service Command Parameters

| Parameter                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:-------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`                        | Optionally, you can specify the name of the node on which you want to stop services. Use this parameter without the `–db` parameter to stop all services on a specific node. If you use the `–db` parameter, then only the services on the specified node for that database are stopped.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-db ``db_unique_name`                     | Specify a unique name for the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-pdb ``pluggable_database`                | Alternatively, use this parameter to stop services running on a specific pluggable database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-service "``service_list``"`              | Specify a particular service or a comma-delimited list of service names enclosed in double quotation marks (`""`) you want to stop.<br>If you do not provide a service name list, then SRVCTL stops all services on the database or on a specific instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-pq`                                      | Specify this parameter to restrict the stop action to a parallel query service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-instance ``instance_name`                | Optionally, you can specify the name of the instance for which you want to stop services.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-serverpool ``pool_name`                  | Optionally, you can specify the name of the server pool that contains the service you want to stop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `—eval`                                    | Use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-stopoption IMMEDIATE|TRANSACTIONAL|NONE` | Specify the method of stopping the service. If this attribute was previously set for the service, then that value is used as the default value if you do not include the `-stopoption` parameter in your command. Otherwise, the default is `NONE`.<br>• `IMMEDIATE` permits sessions to drain before the service is stopped. Sessions that do not drain are terminated when the time limit specified by `-drain_timeout` is reached.<br>• If you specify `TRANSACTIONAL`, then sessions are terminated as soon as they commit. The service is stopped when the time limit specified by `-drain_timeout` is reached and any remaining sessions are terminated.<br>• If you specify `NONE`, then no sessions are terminated.<br>Note: You must use the `-stopoption` parameter with the `-force` parameter.                |
| `-drain_timeout ``timeout`                 | Specify the time, in seconds, allowed for resource draining to be completed. Accepted values are an empty string (""), 0, or any positive integer. The default value is an empty string, which means that this parameter is not set. If it is set to 0, then draining occurs, immediately.<br>The draining period is intended for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. When set on the service this value is used when the command line value is not set.                                                                                                                                                                                                                                                            |
| `-wait {YES | NO}`                         | Choose `YES` to wait until service draining is completed on the node to stop the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-force [-noreplay]`                       | Force SRVCTL to stop the service; this causes SRVCTL to disconnect all of the sessions using the stop option you specify (`IMMEDIATE` or `TRANSACTIONAL`), requiring the sessions using the service to reconnect and then connect to another instance.<br>Notes:<br>• If you do not specify the `-force` parameter, then sessions already connected to this service stay connected, but new sessions cannot be established to the service.<br>• Optionally, you can specify the `-noreplay` parameter if you do not want Application Continuity to replay in-flight transactions after a session is terminated.<br>• The `-noreplay` parameter is not limited to use with `-force`. However, if you do not want to replay in-flight transactions after you force the service to stop, then `-force` requires `-noreplay`. |
| `-global_override`                         | Override value to operate on a global service. SRVCTL ignores this parameter if the service is not a global service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-verbose`                                 | Use this parameter to display verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

##### Examples

The following example command stops services running on the `crmeast` PDB in the `crm` database on instance `crm1` using the `IMMEDIATE` method, allowing 60 seconds for services to transfer to another node:

    $ srvctl stop service -db crm -pdb crmeast -instance crm1 -drain_timeout 60 -force
    - stopoption immediate -verbose

The following example command stops all services running on the node `node1` that are managed by Oracle Clusterware using the default stop option specified for each service and waiting until all sessions have drained from that node.

    $ srvctl stop service -node node1 -wait yes

#### srvctl add srvpool

Adds a server pool that is configured to host Oracle databases to a cluster.

##### Syntax

    srvctl add srvpool -serverpool server_pool_name [-eval]
        [-importance importance] [-min min_size] [-max max_size]
        [-servers "node_list" | -category server_category] [-force] [-verbose]

##### Parameters

Table A-91 srvctl add srvpool Command Parameters

| Parameter                        | Description                                                                                                                                                                                                                                                                                                                                                         |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-serverpool ``server_pool_name` | The name of the server pool.                                                                                                                                                                                                                                                                                                                                        |
| `-eval`                          | Use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                                                                                                                                                              |
| `-importance ``importance`       | The importance of the server pool (default value is `0`).                                                                                                                                                                                                                                                                                                           |
| `-min ``min_size`                | The minimum size of the server pool (default value is `0`).                                                                                                                                                                                                                                                                                                         |
| `-max ``max_size`                | The maximum size of the server pool. The default value is `-1`, which indicates that the size is unlimited.                                                                                                                                                                                                                                                         |
| `-servers "``node_list``"`       | A comma-delimited list of candidate node names enclosed in double quotation marks (`""`). The server pool will only include nodes on the candidate list, but not all nodes on the candidate list will necessarily be in the server pool.<br>Note: In Oracle Database 12c, servers are assigned to server pools according to the value of the `-category` parameter. |
| `-category ``server_category`    | The category of servers to use for the server pool, or `""` for the empty category value.                                                                                                                                                                                                                                                                           |
| `-force`                         | Add the server pool, even if it requires stopping resources in other server pools.                                                                                                                                                                                                                                                                                  |
| `-verbose`                       | Display verbose output.                                                                                                                                                                                                                                                                                                                                             |

##### Usage Notes

- SRVCTL prepends “`ora.`” to the name of the server pool.

- This command is only available with Oracle Clusterware.

##### Example

The following command adds a server pool named SP1, with importance set to 1, the minimum number of nodes in the server pool set to 3 and the maximum number of nodes in the server pool set to 7:

    srvctl add srvpool -serverpool SP1 -importance 1 -min 3 -max 7

#### srvctl config srvpool

Displays configuration information including name, minimum size, maximum size, importance, and a list of server names, if applicable, for a specific server pool in a cluster.

##### Syntax

    srvctl config srvpool [-serverpool pool_name]

##### Parameters

The only parameter available for this command is `-serverpool ``pool_name`, which is the name of the server pool for which you want to display the configuration information.

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    $ srvctl config srvpool -serverpool dbpool

#### srvctl modify srvpool

Modifies a server pool in a cluster.

If minimum size, maximum size, and importance are numerically increased, then the CRS daemon may attempt to reassign servers to this server pool, if by resizing, other server pools have comparatively lower minimum size and importance, to satisfy new sizes of this server pool.

##### Syntax

    srvctl modify srvpool -serverpool pool_name [-eval] [-importance importance]
       [-min min_size] [-max max_size] [-servers "server_list"]
       [-category "server_category"] [-verbose] [-force]

##### Parameters

Table A-92 srvctl modify srvpool Command Parameters

| Parameter                         | Description                                                                                                                                                                                                                                        |
|:----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-serverpool ``pool_name`         | Specify the name of the server pool you want to modify.                                                                                                                                                                                            |
| `–eval`                           | Optionally, you can use this parameter to hypothetically evaluate the impact of the command on the system.                                                                                                                                         |
| `-importance ``importance`        | Optionally, you can modify the importance of the server pool.                                                                                                                                                                                      |
| `-min ``min_size`                 | Optionally, you can modify the minimum size of the server pool. The default value is 0.                                                                                                                                                            |
| `-max ``max_size`                 | Optionally, you can modify the maximum size of the server pool. A value of `-1` sets the server pool maximum size to `UNLIMITED`.                                                                                                                  |
| `-servers "``server_list``"`      | Optionally, you can specify a comma-delimited list of candidate server names enclosed in double quotation marks (`""`).<br>Note: In Oracle Database 12c, servers are assigned to server pools according to the value of the `-category` parameter. |
| `-category "``server_category``"` | Optionally, you can modify the server category enclosed in double quotation marks (`""`) or `""` for empty category value.                                                                                                                         |
| `-verbose`                        | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                 |
| `–force`                          | Optionally, you can use this parameter to force the operation even though SRVCTL may stop some resources.                                                                                                                                          |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example changes the importance rank to 0, the minimum size to 2, and the maximum size to 4 for the server pool `srvpool1`:

    $ srvctl modify srvpool -serverpool srvpool1 -importance 0 -min 2 -max 4

#### srvctl remove srvpool

Removes a specific server pool.

If there are databases or services that depend upon this server pool, then those resources are removed from the server pool first so that the remove server pool operation succeeds.

##### Syntax

    srvctl remove srvpool -serverpool pool_name [-eval] [-verbose]

##### Parameters

Table A-93 srvctl remove srvpool Command Parameters

| Parameter                 | Description                                                                                                                        |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `-serverpool ``pool_name` | Specify the name of the server pool you want to remove.                                                                            |
| `-eval`                   | Optionally, you can use this parameter to evaluate the effects of removing a server pool without making any changes to the system. |
| `–verbose`                | Optionally, you can use this parameter to display detailed output.                                                                 |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- If you successfully remove the specified server pool, then the CRS daemon may assign its servers to other server pools depending upon their minimum size, maximum size, and importance. The CRS daemon may also return these servers to its Free server pool.

##### Example

The following example removes a server pool from the system:

    $ srvctl remove srvpool -serverpool srvpool1

#### srvctl status srvpool

Displays server pool names, number of servers in server pools, and, optionally, the names of the servers in the server pools.

##### Syntax

    srvctl status srvpool [-serverpool pool_name] [-detail]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Optionally, you can specify the name of a server pool for which you want to check the status. If you use this parameter, then the output includes the server pool name and number of servers in the server pool (and, optionally, the server names) for the specified server pool.

- If you choose to use the `-detail` parameter but do not specify a specific server pool with the `-serverpool` parameter, then the output of this command includes the names of servers that are currently assigned to each server pool.

#### srvctl add vip

Adds a virtual IP address (VIP) to a node.

##### Syntax

    srvctl add vip -node node_name -address {VIP_name|ip}/netmask[/if1[|if2|...]]
          -netnum network_number [-skip] [-verbose]

##### Parameters

Table A-94 srvctl add vip Command Parameters

| Parameter                                                             | Description                                                                                                                                                                          |
|:----------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`                                                   | The name of the node on which you are adding the VIP.                                                                                                                                |
| `-address {``VIP_name``|``ip``}/``netmask`` [/``if1``[|``if2``|...]]` | This specification creates a traditional VIP node application on the specified node.<br>You can specify one `VIP_name` or address, along with an IPv4 netmask or IPv6 prefix length. |
| `-netnum ``network_number`                                            | The network number from which VIPs are obtained. The default network number is 1.                                                                                                    |
| `-skip`                                                               | Specify this parameter to skip checking the reachability of the VIP address.                                                                                                         |
| `-verbose`                                                            | Verbose output                                                                                                                                                                       |

**Note:**

##### Usage Notes

- You cannot have multiple VIPs on the same net number (subnet or interface pair) on the same node.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl add network -netnum 2 -subnet 192.168.16.0/255.255.255.0
    # srvctl add vip -node node7 -address 192.168.16.17/255.255.255.0 -netnum 2

The first command creates a network number, `2`, and the second command adds a VIP to this network. You can specify the network number after the `-netnum` parameter in other SRVCTL commands.

#### srvctl config vip

Displays all VIPs on all networks in the cluster except for user VIPs.

##### Syntax

    srvctl config vip {-node node_name | -vip vip_name}

##### Parameters

Table A-95 srvctl config vip Command Parameters

| Parameter           | Description                                  |
|:--------------------|:---------------------------------------------|
| `-node ``node_name` | Specify the node name.                       |
| `-vip ``vip_name`   | Alternatively, you can specify the VIP name. |

##### Usage Notes

This command is only available with Oracle Clusterware.

##### Example

This command returns output similar to the following:

    $ srvctl config vip -node crmnode1

    VIP exists: ipv4, ipv6, network number 1, hosting node adc2100252

#### srvctl disable vip

Disables a specific VIP.

##### Syntax

    srvctl disable vip -vip vip_name [-verbose]

##### Usage Notes

- This command is only available with Oracle Clusterware.

- Specify the name of the VIP you want to disable.

- Optionally, you can use the `–verbose` parameter to display detailed output.

##### Example

The following command disables a VIP:

    $ srvctl disable vip -vip vip1 -verbose

#### srvctl enable vip

Enables a specific VIP.

##### Syntax

    srvctl enable vip -vip vip_name [-verbose]

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- Specify the name of the VIP you want to enable.

- Optionally, you can use the `–verbose` parameter to display detailed output.

##### Example

The following example enables a VIP named `crm1-vip`:

    $ srvctl enable vip -vip crm1-vip -verbose

#### srvctl getenv vip

Obtains the values of environment variables for a specific VIP.

##### Syntax

    srvctl getenv vip -vip vip_name [-envs "name_list"] [-verbose]

##### Parameters

Table A-96 srvctl getenv vip Command Parameters

| Parameter               | Description                                                                                                                                                                                                                |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-vip ``vip_name`       | Specify the name of the VIP for which you want to obtain the values of the environment variables.                                                                                                                          |
| `-envs "``name_list``"` | Optionally, you can specify a comma-delimited list of the names of specific environment variables. If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the VIP. |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example lists all environment variables for the specified VIP:

    $ srvctl getenv vip -vip node1-vip

#### srvctl modify vip

Modifies IP address type but you can also use it to modify only the IP address.

##### Syntax

    srvctl modify vip -node node_name -address {VIP_name|ip}/netmask[/if1[|if2|...]]
       [-netnum network_number] [-verbose]

##### Parameters

Table A-97 srvctl modify vip Command Parameters

| Parameter                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
|:---------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name`                                                  | Specify the name of the node on which you are changing the VIP.                                                                                                                                                                                                                                                                                                                                              |
| `-address {``VIP_name``|``ip``}/``netmask``[/``if1``[|``if2``|...]]` | Use this parameter to change the configuration of an existing VIP. If the VIP has an IPv4 address and the address you specify is IPv6, and the IP address type is set to `both` and the network type is set to `static`, then SRVCTL adds the IPv6 address to the existing IPv4 address of that resource.<br>You can specify one `VIP_name` or IP address, along with an IPv4 netmask or IPv6 prefix length. |
| `-netnum ``network_number`                                           | Optionally, you can specify the network number from which VIPs are obtained. If you do not use this parameter, then SRVCTL obtains the VIPs from the same default network from which the `nodeapps` VIP is obtained.                                                                                                                                                                                         |
| `–verbose`                                                           | Optionally, you can use this parameter to display detailed output.                                                                                                                                                                                                                                                                                                                                           |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- You cannot have multiple VIPs on the same net number (subnet or interface pair) on the same node.

##### Example

The following example adds an IPv4 address to a VIP, if one does not already exist. If the VIP has an IPv4 address, then it is replaced with the new network specification.

    # srvctl modify vip -node node7 -address 192.168.16.17/255.255.255.0 -netnum 2

#### srvctl predict vip

Predicts the consequences of VIP failure.

##### Syntax

    srvctl predict vip [-vip vip_name] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a VIP for which you want to evaluate the consequences of failure.

- Optionally, you can use the `–verbose` parameter to display detailed output.

#### srvctl relocate vip

Relocates a specific VIP from its current hosting node to another node within the cluster.

##### Syntax

    srvctl relocate vip -vip vip_name [-node node_name] [-force] [-verbose]

##### Parameters

Table A-98 srvctl relocate vip Command Parameters

| Parameter           | Description                                                                                               |
|:--------------------|:----------------------------------------------------------------------------------------------------------|
| `-vip ``vip_name`   | Specify the name of the VIP you want to relocate.                                                         |
| `-node ``node_name` | Optionally, you can specify the name of the target node where you want to relocate the VIP.               |
| `–force`            | Optionally, you can use this parameter to force the relocation of the VIP regardless of any dependencies. |
| `–verbose`          | Optionally, you can use this parameter to display detailed output.                                        |

##### Example

The following example relocates a VIP to a different node in the cluster:

    $ srvctl relocate vip -vip vip1 -node node3

#### srvctl remove vip

Removes specific VIPs.

##### Syntax

    srvctl remove vip -vip "vip_name_list" [-force] [-noprompt] [-verbose]

##### Parameters

Table A-99 srvctl remove vip Command Parameters

| Parameter                  | Description                                                                                                      |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------|
| `-vip "``vip_name_list``"` | Specify a comma-delimited list of VIP names that you want to remove surrounded by double quotation marks (`""`). |
| `–force`                   | Optionally, you can use this parameter to remove a VIP regardless of any dependencies.                           |
| `-noprompt`                | Optionally, you can use this parameter to suppress prompts.                                                      |
| `-verbose`                 | Optionally, you can use this parameter to display detailed output.                                               |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example removes several VIPs from the system:

    $ srvctl remove vip -vip "vip1,vip2,vip3" -force -noprompt -verbose

#### srvctl setenv vip

Administers cluster VIP environment configurations.

##### Syntax

    srvctl setenv vip -vip vip_name {-envs "name=val[,...]" | -env "name=val"}
       [-verbose]

##### Parameters

Table A-100 srvctl setenv vip Command Parameters

| Parameter                        | Description                                                                                                                                                                                                            |
|:---------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-vip ``vip_name`                | Specify the name of the VIP for which you want to set environment variables.                                                                                                                                           |
| `-envs "``name``=``val``[,...]"` | Specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`) that you want to set.                                                                            |
| `-env "``name``=``val"`          | Alternative to a list of environment variables, you can use this parameter to set a single environment variable to a value that contains commas or other special characters enclosed in double quotation marks (`""`). |
| `–verbose`                       | Optionally, you can use this parameter to display detailed output.                                                                                                                                                     |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example sets the language environment configuration for a cluster VIP:

    $ srvctl setenv vip -vip crm1-vip -env "LANG=en"

#### srvctl start vip

Starts a specific VIP or a VIP on a specific node.

##### Syntax

    srvctl start vip {-node node_name | -vip vip_name} [-verbose]

##### Parameters

Table A-101 srvctl start vip Command Parameters

| Parameter           | Description                                                                     |
|:--------------------|:--------------------------------------------------------------------------------|
| `-node ``node_name` | Specify the name of the node on which the VIP resides that you want to start.   |
| `-vip ``vip_name`   | Alternative to specifying a node, you can specify a VIP that you want to start. |
| `-verbose`          | Optionally, you can use this parameter to display detailed ouptut.              |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example starts a specific VIP:

    $ srvctl start vip -vip crm1-vip -verbose

#### srvctl status vip

Displays status for a specific VIP or a VIP on a specific node.

##### Syntax

    srvctl status vip {-node node_name | -vip vip_name} [-verbose]

##### Parameters

Table A-102 srvctl status vip Command Parameters

| Parameter           | Description                                                                                |
|:--------------------|:-------------------------------------------------------------------------------------------|
| `-node ``node_name` | Specify the name of the node on which the VIP resides that you want to check the status.   |
| `-vip ``vip_name`   | Alternative to specifying a node, you can specify a VIP that you want to check the status. |
| `-verbose`          | Optionally, you can use this parameter to display detailed output.                         |

##### Usage Notes

You can only use this command with Oracle Clusterware.

#### srvctl stop vip

Stops a specific VIP or all VIPs on a specific node, including any VIPs that were relocated due to a failover.

##### Syntax

    srvctl stop vip {-node node_name | -vip vip_name} [-force] [-relocate] [-verbose]

##### Parameters

Table A-103 srvctl stop vip Command Parameters

| Parameter           | Description                                                                                                                                                                      |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-node ``node_name` | Specify the name of a node on which a VIP resides that you want to stop. If you use this parameter, then SRVCTL stops all VIPs on the specific node, including failed-over VIPs. |
| `-vip ``vip_name`   | Alternative to specifying a node, you can specify a VIP that you want to stop.                                                                                                   |
| `-force`            | Optionally, you can use this parameter to stop the VIP regardless of any dependencies.                                                                                           |
| `-relocate`         | Optionally, you can use this parameter to relocate the VIP.<br>Note: You must use the `-node ``node_name` parameter with the `-relocate` parameter.                              |
| `–verbose`          | Optionally, you can use this parameter to display detailed output.                                                                                                               |

##### Usage Notes

You can only use this command with Oracle Clusterware.

##### Example

The following example stops all the VIPs on `mynode1`, including any failed-over VIPs:

    $ srvctl stop vip -node mynode1 -verbose

#### srvctl unsetenv vip

Unsets the environment configuration for the specified cluster VIP.

##### Syntax

    srvctl unsetenv vip -vip "vip_name_list" -envs "name_list" [-verbose]

##### Parameters

Table A-104 srvctl unsetenv vip Command Parameters

| Parameter                  | Description                                                                                                                    |
|:---------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `-vip "``vip_name_list``"` | Specify a comma-delimited list of VIP names enclosed in double quotation marks (`""`).                                         |
| `-envs "``name_list``"`    | Specify a comma-delimited list of environment variable names enclosed in double quotation marks (`""`) that you want to unset. |
| `–verbose`                 | Optionally, you can use this parameter to display detailed output.                                                             |

##### Example

The following example unsets the `CLASSPATH` environment variable for a cluster VIP:

    $ srvctl unsetenv vip -vip "crm2-vip" -envs "CLASSPATH"

#### srvctl config volume

Displays the configuration for a specific volume or all volumes.

##### Syntax

    srvctl config volume [-volume volume_name] [-diskgroup disk_group_name]
       [-device volume_device]

##### Parameters

Table A-105 srvctl config volume Command Parameters

| Parameter                      | Description                                                                                                     |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume for which you want to view the configuration.                                    |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume resides for which you want to display the configuration. |
| `-device ``volume_device`      | Specify the path to the volume device for which you want to display the configuration.                          |

##### Usage Notes

- If you do not specify any of the optional parameters, then SRVCTL displays the configuration information for all volumes.

- If you specify only the `-volume` parameter, then SRVCTL displays the configuration for all volumes with that name, regardless of the diskgroup.

- If you specify only the `-diskgroup` parameter, then SRVCTL displays the configuration information for the volumes that reside in the disk group that you specify.

- If you specify only the `-device` parameter, then SRVCTL displays the configuration information for the volume matching that device specifier.

- If you specify the `-diskgroup` and `-device` parameters, then SRVCTL displays the configuration information for the volume device that resides in the disk group that you specify.

- This command is only available with Oracle Clusterware.

##### Examples

This command returns information similar to the following:

    $ srvctl config volume -device /dev/asm/volume1-123

    Diskgroup Name: DG1
    Volume Name   : VOL1
    Volume Device : /dev/asm/volume1-123
    Volume is enabled.
    Volume is enabled on nodes:
    Volume is disabled on nodes:

If you do not specify any parameters, then SRVCTL returns configuration information for all volumes, similar to the following:

    $ srvctl config volume

    Diskgroup name: DG1
    Volume name: VOL1
    Volume device: /dev/asm/volume1-123
    Volume is enabled.
    Volume is enabled on nodes:
    Volume is disabled on nodes:
    Diskgroup name: DG1
    Volume name: VOL2
    Volume device: /dev/asm/volume2-456
    Volume is enabled.
    Volume is enabled on nodes:
    Volume is disabled on nodes:

#### srvctl disable volume

Disables Oracle Clusterware management for a specific volume or all volumes.

This command allows a volume device to be stopped by operating on the Oracle Clusterware resource for the volume. This command does not stop volume device.

##### Syntax

    srvctl disable volume {-volume volume_name -diskgroup disk_group_name |
        -device volume_device}

##### Parameters

Table A-106 srvctl disable volume Command Parameters

| Parameter                      | Description                                                                                                              |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume that you want to disable.                                                                 |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume that you want to disable resides.                                 |
| `-device ``volume_device`      | Alternative to using the `–diskgroup` parameter, you can specify the path to the volume device that you want to disable. |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- You must specify a particular volume that you want to disable. You can specify a volume that resides in either a particular disk group or on a particular volume device.

##### Example

The following example disables a volume named `VOLUME1` that resides in a disk group named `DATA`:

    $ srvctl disable volume -volume VOLUME1 -diskgroup DATA

#### srvctl enable volume

Enables Oracle Clusterware management for a specific volume or all volumes.

This command allows a volume device to be started by operating on the Oracle Clusterware resource for the volume. This command does not start the volume device, and is different from the SQL command `ALTER DISKGROUP ENABLE VOLUME` or the ASMCMD command `volenable`, because these two commands bring the volume device online, in a running state, making the volume device accessible.

##### Syntax

    srvctl enable volume {-volume volume_name -diskgroup disk_group_name |
       -device volume_device}

##### Parameters

Table A-107 srvctl enable volume Command Parameters

| Parameter                      | Description                                                                                                             |
|:-------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume that you want to enable.                                                                 |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume that you want to enable resides.                                 |
| `-device ``volume_device`      | Alternative to using the `–diskgroup` parameter, you can specify the path to the volume device that you want to enable. |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- You must specify a particular volume that you want to enable. You can specify a volume that resides in either a particular disk group or on a particular volume device.

##### Example

The following example enables a volume named `VOLUME1` that resides in a disk group named `DATA`:

    $ srvctl enable volume -volume VOLUME1 -diskgroup DATA

#### srvctl remove volume

Removes a specific volume.

##### Syntax

Use this command with one of the following syntax models:

    srvctl remove volume -volume volume_name -diskgroup disk_group_name [-force]

    srvctl remove volume -device volume_device [-force]

##### Parameters

Table A-108 srvctl remove volume Command Parameters

| Parameter                      | Description                                                                                       |
|:-------------------------------|:--------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume that you want to remove.                                           |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume that you want to remove resides.           |
| `-device ``volume_device`      | Specify the path to the file system resource in which the volume that you want to remove resides. |
| `–force`                       | You can use this parameter to remove the volume even if it is running.                            |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- The volume gets created when you create volumes in Oracle ASM.

- You must specify a particular volume that you want to remove. You can specify a volume that resides in either a particular disk group or on a particular volume device.

##### Example

The following example removes a volume named `VOLUME1` that resides in a disk group named `DATA`:

    $ srvctl remove volume -volume VOLUME1 -diskgroup DATA

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-advm-asmcmd.md)

#### srvctl start volume

Starts a specific, enabled volume.

##### Syntax

    srvctl start volume {-volume volume_name -diskgroup disk_group_name |
        -device volume_device} [-node node_list]

##### Parameters

Table A-109 srvctl start volume Command Parameters

| Parameter                      | Description                                                                                                                                             |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume that you want to start.                                                                                                  |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume that you want to start resides.                                                                  |
| `-device ``volume_device`      | Alternative to using the `–diskgroup` parameter, you can specify the path to the volume device that you want to start.                                  |
| `-node ``node_list`            | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) where volumes that you want to start reside. |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- The `srvctl start volume` command does not create a volume service. Provided that the volume already exists and the volume resource is enabled, SRVCTL attempts to start it. If the volume exists but the resource is disabled, then `srvctl start volume` returns an error.

##### Example

The following example starts a volume named `VOLUME1` that resides in a disk group named `DATA`:

    $ srvctl start volume -volume VOLUME1 -diskgroup DATA

#### srvctl status volume

Displays the status of a specific volume or all volumes.

##### Syntax

    srvctl status volume [-device volume_device] [-volume volume_name]
       [-diskgroup disk_group_name] [-node "node_list"]

##### Parameters

Table A-110 srvctl status volume Command Parameters

| Parameter                      | Description                                                                                                                                                            |
|:-------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-device ``volume_device`      | Optionally, you can specify the path to the volume device for which you want to display the status.                                                                    |
| `-volume ``volume_name`        | Optionally, you can specify the name of the volume for which you want to view the status.                                                                              |
| `-diskgroup ``disk_group_name` | Optionally, you can specify the name of the disk group in which the volume resides for which you want to display the status.                                           |
| `-node "``node_list``"`        | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) where volumes for which you want to view the status reside. |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- If you do not specify any of the optional parameters, then SRVCTL displays the status for all volumes.

- If you specify only the `-volume` parameter, then SRVCTL displays the status for the volume that you specify.

- If you specify only the `-diskgroup` parameter, then SRVCTL displays the status for the volumes that reside in the disk group that you specify.

- If you specify only the `-device` parameter, then SRVCTL displays the status for the volume device that you specify.

- If you specify the `-diskgroup` and `-device` parameters, then SRVCTL displays the status for the volume device in the disk group that you specify.

- If you specify the `-node` parameter, then SRVCTL displays the status of the volumes that reside on the nodes you list.

##### Examples

This command displays information similar to the following:

    $ srvctl status volume –volume vol1
    Volume vol1 of diskgroup diskgrp1 for device volume_device_path1 is enabled
    Volume vol1 of diskgroup diskgrp1 for device volume_device_path1 is running

In the preceding example, SRVCTL performs a status query on all nodes because the `-node` parameter is not specified.

    $ srvctl status volume
    Volume vol1 of diskgroup diskgrp for device volume_device_path1 is enabled
    Volume vol1 of diskgroup diskgrp for device volume_device_path1 is running
    Volume vol2 of diskgroup diskgrp for device volume_device_path2 is enabled
    Volume vol2 of diskgroup diskgrp for device volume_device_path2 is running

In the preceding example, SRVCTL displays the status of all registered volumes because the no parameter is specified.

#### srvctl stop volume

Stops a specific, running volume.

##### Syntax

    srvctl stop volume {-volume volume_name -diskgroup disk_group_name |
        -device volume_device} [-node "node_list"]

##### Parameters

Table A-111 srvctl stop volume Command Parameters

| Parameter                      | Description                                                                                                                                            |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-volume ``volume_name`        | Specify the name of the volume you want to stop.                                                                                                       |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group in which the volume you want to stop resides.                                                                       |
| `-device ``volume_device`      | Alternative to using the `–diskgroup` parameter, you can specify the path to the volume device that you want to stop.                                  |
| `-node "``node_list``"`        | Optionally, you can specify a comma-delimited list of node names enclosed in double quotation marks (`""`) where volumes that you want to stop reside. |

##### Usage Notes

- You can only use this command with Oracle Clusterware.

- The `srvctl stop volume` command attempts to stop (disable) the volume but it does not disable the resource or remove the volume from Oracle ASM.

##### Example

The following example stops a volume named `VOLUME1` that resides in a disk group named `DATA`:

    $ srvctl stop volume -volume VOLUME1 -diskgroup DATA
