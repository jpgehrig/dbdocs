Use the Server Control (SRVCTL) utility to manage various components and applications in your cluster.

This appendix contains reference information for Server Control commands, including utility usage information and a comprehensive listing of the SRVCTL commands.

**Note:**

SRVCTL commands specific to Oracle RAC administration operations are documented in [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)

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

Table F-1 String Restrictions for SRVCTL Object Names

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

The command reference in this appendix shows the keywords for each SRVCTL command. Table F-2 lists the deprecated single-character parameters.

Table F-2 Deprecated Single-Character Parameters for SRVCTL Commands

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

Table F-3 Deprecated Commands and Parameters for SRVCTL

| Command                  | Deprecated Parameters                                                                                                                                                                                                                 |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `srvctl modify asm`      | `-node` `node_name`                                                                                                                                                                                                                   |
| `srvctl modify instance` | `-z`<br>Instead, use the `-node` option with the value set to `""`                                                                                                                                                                    |
| `srvctl modify gns`      | `[-ip ``ip_address``] [-advertise ``host_name`` -address ``address``] [-delete ``host_name`` -address ``address``] [-createalias ``name`` -alias ``alias``] [-deletealias ``alias``]`<br>Use the `srvctl update gns` command instead. |
| `srvctl * oc4j`          | The `oc4j` noun has been deprecated and replaced with `qosmserver`. SRVCTL still accepts the `oc4j` noun until it is desupported.                                                                                                     |
| `srvctl add service`     | The `PRECONNECT`option with the `-tafpolicy` parameter is deprecated.                                                                                                                                                                 |
| `srvctl modify service`  | The `-failovermethod {NONE | BASIC}` is deprecated.<br>The `PRECONNECT`option with the `-tafpolicy` parameter is deprecated.                                                                                                          |

### SRVCTL Command Reference

A comprehensive list of SRVCTL commands to use in Oracle Grid Infrastructure environments.

SRVCTL uses the following command syntax:

    srvctl command object [parameters]

In SRVCTL syntax:

- `command` is a verb such as `start`, `stop`, or `remove`

- `object` (also known as a noun) is the target or object on which SRVCTL performs the command, such as Oracle Automatic Storage Management (Oracle ASM) or a file system. You can also use object abbreviations.

- `parameters` extend the use of a preceding command combination to include additional parameters for the command. Some parameters are required while others are optional.

**Note:**

If specifying a comma-delimited list in a command parameter on Windows, then you must enclose the list within double quotation marks (`""`).

Table F-4 lists the keywords that can be used for the `object` portion of SRVCTL commands. You can use either the full name or the abbreviation for each object keyword. The Purpose column describes the object and the actions that can be performed on that object.

Table F-4 Object Keywords and Abbreviations

| Object                                                  | Keyword             | Purpose                                                                                                                                                                                                          |
|:--------------------------------------------------------|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle ASM                                              | `asm`               | To add, modify, manage environment variables for, list the configuration of, enable, disable, start, stop, and obtain the status of Oracle ASM                                                                   |
| Oracle ASM Network                                      | `asmnetwork`        | To add, configure, modify and remove an Oracle ASM network configuration                                                                                                                                         |
| Cluster Verification Utility                            | `cvu`               | To add, modify, enable, disable, remove, relocate, start, stop, and obtain the status of the Cluster Verification Utility                                                                                        |
| Cross-cluster dependency                                | `cdp`               | To add, modify, enable, disable, remove, relocate, start, stop, and obtain the status of cross-cluster dependency services.                                                                                      |
| Cross-cluster dependency proxies                        | `cdpproxy`          | To add, modify, enable, disable, remove, relocate, start, stop, and obtain the status of cross-cluster dependency proxy resources.                                                                               |
| Export file system                                      | `exportfs`          | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, and remove export file systems                                                                                    |
| Oracle Automatic Storage Management Cluster File System | `filesystem`        | To add, modify, list the configuration of, remove, start, stop, and obtain the status of Oracle ACFS                                                                                                             |
| Grid Naming Service                                     | `gns`               | To add, modify, list the configuration of, import, export, enable, disable, start, stop, obtain the status of, relocate, remove, and update the Grid Naming Service                                              |
| Highly available VIP                                    | `havip`             | To add, list the configuration of, enable, start, obtain the status of, stop, disable, relocate, and remove highly available VIPs                                                                                |
| Oracle ASM IOServer                                     | `ioserver`          | To add, list the configuration of, modify, enable, disable, start, stop, relocate, obtain the status of, manage environment variables for, and remove Oracle ASM IOServer                                        |
| Management database                                     | `mgmtdb`            | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, manage environment variables for, and remove management databases (Cluster Health Monitor repositories) |
| Management listener                                     | `mgmtlsnr`          | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, manage environment variables for, and remove management listener resources for Cluster Health Monitor   |
| Network Attached Storage (NAS)                          | `mountfs`           | To add, list the configuration of, enable, start, obtain the status of, stop, disable, relocate, and remove NAS                                                                                                  |
| Network Storage Service Resource                        | `netstorageservice` | To add, list the configuration of, enable, start, obtain the status of, stop, disable, and remove NetStorageService Resource                                                                                     |
| Virtual machine manager                                 | `ovmm`              | To add, list the configuration of, enable, modify, and remove a virtual machine manager                                                                                                                          |
| Oracle Database Quality of Service Management Server    | `qosmserver`        | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, and remove Oracle Database Quality of Service Management Server                                         |
| Fleet Patching and Provisioning Client                  | `rhpclient`         | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, and remove Fleet Patching and Provisioning Clients                                                      |
| Fleet Patching and Provisioning Server                  | `rhpserver`         | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, and remove Fleet Patching and Provisioning Servers                                                      |
| Virtual machine                                         | `vm`                | To add, modify, list the configuration of, enable, disable, start, stop, obtain the status of, relocate, and remove virtual machines                                                                             |

**Note:**

SRVCTL commands specific to Oracle RAC administration operations are documented in [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)

#### srvctl config all

Displays the configuration details of the cluster and database components.

##### Syntax

    srvctl config all [-help]

##### Example

This command returns output similar to the following:

    $ srvctl config all

    Oracle Clusterware configuration details
    ========================================
    Oracle Clusterware basic information
    ------------------------------------
    Operating system       Linux
    Name                   stbm000025-rac3
    Class                  STANDALONE
    Cluster nodes          stbm000025-vm11, stbm000025-vm10, stbm000025-vm9,
                           stbm000025-vm12
    Version                19.0.0.0.0
    Groups                 SYSOPER:oinstall SYSASM:oinstall SYSRAC:oinstall
                           SYSDBA:oinstall
    OCR locations          +DATA2
    Voting disk locations  DATA2
    Voting disk file paths AFD:DATA21

    Cluster network configuration details
    -------------------------------------
    Interface name  Type  Subnet          Classification
    ens3            IPV4  100.70.0.0/20   PUBLIC
    ens4            IPV4  192.168.1.0/24  PRIVATE, ASM

    SCAN configuration details
    --------------------------
    SCAN "stbm000025-scan3" details
    +++++++++++++++++++++++++++++++
    Name                stbm000025-scan3
    IPv4 subnet         100.70.0.0/20
    DHCP server type    static
    End points          TCP:1521

    SCAN listeners
    --------------
    Name              VIP address
    LISTENER_SCAN1    100.70.5.26
    LISTENER_SCAN2    100.70.5.20
    LISTENER_SCAN3    100.70.5.22

    ASM configuration details
    -------------------------
    Mode             remote
    Password file    +DATA2
    SPFILE           +DATA2

    ASM disk group details
    ++++++++++++++++++++++
    Name   Redundancy
    DATA2  EXTERN

    Database configuration details
    ==============================
    Database "ora.orcl.db" details
    ------------------------------
    Name                 ora.orcl.db
    Type                 RAC
    Version              19.0.0.0.0
    Role                 PRIMARY
    Management policy    AUTOMATIC
    SPFILE               +DATA2
    Password             +DATA2
    file Groups          OSDBA:oinstall OSOPER:oinstall OSBACKUP:oinstall OSDG:oinstall
                         OSKM:oinstall OSRAC:oinstall
    Oracle home          /scratch/app/19c/220523/dbhome


#### srvctl add asm

Adds a record for an Oracle ASM instance to the entire cluster.

This command must be run only one time from the Oracle Grid Infrastructure home.

##### Syntax

    srvctl add asm [-listener listener_name] [-pwfile password_file_path
        [-flex [-count {number_of_instances | ALL}] | -proxy [-spfile server_parameter_file_path]]

##### Parameters

Table F-5 srvctl add asm Command Parameters

| Parameter                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener listener_name`                                                                        | Enter the name of a listener. If you do not specify this parameter, then the listener name defaults to `LISTENER`.                                                                                                                                                                                                                                                                                                                |
| `-pwfile password_file_path`                                                                     | Enter the full path to the location of the password file on Oracle ASM.                                                                                                                                                                                                                                                                                                                                                           |
| `-flex [-count {number_of_instances | ALL}] | `<br>`-proxy [-spfile server_parameter_file_path]` | Specify that the Oracle ASM instances are configured as Oracle Flex ASM instances. You can optionally specify the number of Oracle ASM instances to create or that an Oracle ASM instance should be created on all nodes.<br>Alternatively, you can specify the `-proxy` parameter to configure the Oracle ASM Dynamic Volume Manager proxy instance resource. Optionally, you can specify the path to the server parameter file. |

##### Usage Notes

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Example

To add a clusterware resource for Oracle ASM to every node in the cluster, use the following command:

    $ srvctl add asm

#### srvctl config asm

Displays the configuration for all Oracle ASM instances.

##### Syntax

    srvctl config asm [-proxy] [-detail]

##### Parameters

Table F-6 srvctl config asm Command Parameters

| Parameter | Description                                                                                                            |
|:----------|:-----------------------------------------------------------------------------------------------------------------------|
| `-proxy`  | Optionally, you can use this parameter to specify whether the Oracle ASM configuration to display is a proxy instance. |
| `-detail` | Optionally, you can use this parameter to print detailed configuration information.                                    |

##### Usage Notes

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Example

This command returns output similar to the following:

    $ srvctl config asm

    ASM Home: /u01/app/19.0.0/grid
    ASM Listener: LISTENER
    ASM instance count: 3
    Password file:

#### srvctl disable asm

Disables the Oracle ASM proxy resource.

Oracle ASM will restart if it contains Oracle Clusterware data or if the node restarts and it was running before the node failed. The `srvctl disable asm` command also prevents the `srvctl start asm` command from starting Oracle ASM instances.

Disabling the Oracle ASM proxy resource prevents the databases and disk groups from starting because they depend on the Oracle ASM proxy resource.

##### Syntax

    srvctl disable asm [-proxy] [-node node_name]

##### Parameters

Table F-7 srvctl disable asm Command Parameters

| Parameter           | Description                                                                                                   |
|:--------------------|:--------------------------------------------------------------------------------------------------------------|
| `-proxy`            | Optionally, you can use this parameter to specify whether you are disabling a proxy Oracle ASM configuration. |
| `-node ``node_name` | Optionally, you can specify a particular node on which you want to disable Oracle ASM.                        |

##### Usage Notes

- To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

- Oracle ASM is part of the Oracle Clusterware stack and when OCR and voting files are stored on Oracle ASM, then Oracle ASM starts when OHASD starts the Oracle Clusterware stack. The `srvctl disable asm` command does not prevent the Oracle ASM instance managed by OHASD from starting. Oracle ASM, therefore, starts as needed by the Oracle Clusterware stack.

  The `srvctl disable asm` command prevents the Oracle ASM Oracle Clusterware proxy resource, and any resources that depend on it, from starting. So, the command prevents Oracle Clusterware-managed objects, such as databases, disk groups, and file systems that depend on Oracle ASM, from starting. For example, the `srvctl start database | diskgroup | filesystem` command fails to start any of those objects on nodes where the Oracle ASM Oracle Clusterware proxy resource is disabled. The command also prevents the `srvctl start asm` command from starting Oracle ASM on remote nodes.

##### Example

The following example disables Oracle ASM on a node named `crmnode1`:

    $ srvctl disable asm -node crmnode1

#### srvctl enable asm

Enables an Oracle ASM instance.

##### Syntax

    srvctl enable asm [-proxy] [-node node_name]

##### Parameters

Table F-8 srvctl enable asm Command Parameters

| Parameter           | Description                                                                                                  |
|:--------------------|:-------------------------------------------------------------------------------------------------------------|
| `-proxy`            | Optionally, you can use this parameter to specify whether you are enabling a proxy Oracle ASM configuration. |
| `-node ``node_name` | Optionally, you can specify a particular node on which you want to enable Oracle ASM.                        |

##### Usage Notes

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Example

An example of this command is:

    $ srvctl enable asm -node crmnode1

#### srvctl getenv asm

Displays the values for environment variables associated with Oracle ASM.

##### Syntax

    srvctl getenv asm [-envs "name_list"]

##### Usage Notes

- If you choose not use the `-env` parameter, then the values of all environment variables associated with Oracle ASM are displayed.

- You can specify a comma-delimited list of the names of environment variables for which you want to retrieve the values.

##### Example

The following example displays the current values for all the environment variables used by Oracle ASM:

    $ srvctl getenv asm

#### srvctl modify asm

Modifies the listener used by Oracle ASM, the disk group discovery string used by Oracle ASM, or the SPFILE used by Oracle ASM for a noncluster database or a cluster database.

**Note:**

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Syntax

    srvctl modify asm [-listener listener_name] [-pwfile password_file_path]
      [-pwfilebackup backup_password_file_path] [-count {number_of_instances | ALL}] [-diskstring asm_diskstring]
      [-spfile spfile_path_name [-proxy] [-force]]

##### Parameters

| Parameter                                   | Description                                                                                                                                                  |
|:--------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-listener ``listener_name`                 | Specify the name of the listener with which Oracle ASM registers.                                                                                            |
| `-pwfile ``password_file_path`              | Specify the full path to the location of the password file for Oracle ASM.                                                                                   |
| `-pwfilebackup ``backup_password_file_path` | Specify this option to update the location of the Oracle ASM password backup file.<br>**Note:**<br>This option does not backup the Oracle ASM password file. |
| `-count {``number_of_instances`` | ALL}`    | Specify the number of Oracle ASM instances to create, or that an Oracle ASM instance should be created on all nodes.                                         |
| `-diskstring ``asm_diskstring`              | Specify a new Oracle ASM disk group discovery string.                                                                                                        |
| `-spfile ``spfile_path_name`                | Specify the path to the new spfile to be used by Oracle ASM.                                                                                                 |
| `-proxy`                                    | Use this parameter to specify an Oracle ASM proxy instance.                                                                                                  |
| `–force`                                    | Use this parameter to force modification of Oracle ASM.                                                                                                      |

##### Example

An example of this command to modify the configuration of Oracle ASM is:

    $ srvctl modify asm -listener lsnr1

#### srvctl predict asm

Predicts the consequences of Oracle ASM failure.

##### Syntax

    srvctl predict asm [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify a particular node on which you want to predict the consequences of an Oracle ASM failure.

- You can choose verbose output.

##### Example

An example of this command to predict the consequences of an Oracle ASM failure on a particular node:

    $ srvctl predict asm -node crmnode2

#### srvctl relocate asm

Relocates an Oracle Flex ASM instance from one Hub Node of an Oracle Flex Cluster to another.

##### Syntax

    srvctl relocate asm -currentnode current_node [-targetnode target_node] [-force]

##### Parameters

Table F-9 srvctl relocate asm Parameters

| Parameter                     | Description                                                                  |
|:------------------------------|:-----------------------------------------------------------------------------|
| `-currentnode ``current_node` | Name of the node on which the Oracle Flex ASM instance currently resides.    |
| `-targetnode ``target_node`   | Name of the node to which you want to relocate the Oracle Flex ASM instance. |
| `-force`                      | Force the relocation of the Oracle Flex ASM instance.                        |

##### Usage Notes

- You cannot use this command if there is only one Oracle Flex ASM instance running.

- Because of bootstrap issues between Oracle ASM and Oracle Clusterware, on the node where Oracle Clusterware uses Oracle ASM run either `crsctl stop crs` or `crsctl stop cluster` to stop Cluster Ready Services on the node before you relocate the Oracle ASM instance.

##### Example

An example of this command to relocate an Oracle Flex ASM instance from the current node to a node named `hubnode2` is:

    $ srvctl relocate asm -currentnode hubnode1 -targetnode hubnode2

#### srvctl remove asm

Removes the Oracle ASM resource from Oracle Clusterware management.

**Note:**

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Syntax

    srvctl remove asm [-proxy] [-force]

##### Parameters

Table F-10 srvctl remove asm Command Parameters

| Parameter | Description                                                                                                  |
|:----------|:-------------------------------------------------------------------------------------------------------------|
| `-proxy`  | Optionally, you can use this parameter to specify whether you are removing a proxy Oracle ASM configuration. |
| `-force`  | Forcefully removes an Oracle ASM resource (ignores any dependencies).                                        |

##### Example

An example of this command is:

    $ srvctl remove asm -force

#### srvctl setenv asm

Sets Oracle ASM environment configurations.

##### Syntax

Use this command with one of the following syntaxes:

    srvctl setenv asm -envs "name=value,[...]"

    srvctl setenv asm -env "name=value"

##### Parameters

Table F-11 srvctl setenv asm Command Parameters

| Parameter                          | Description                                                                                                                                                                              |
|:-----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name``=``value``,[...]"` | Use this parameter to specify either a single name-value pair or a comma-delimited list of multiple name-value pairs of environment variables enclosed in double quotation marks (`""`). |
| `-env "``name``=``value``"`        | Use this parameter to enable a single environment variable to be set to a value that contains commas or other special characters, enclosed in double quotation marks (`""`).             |

##### Example

The following example sets the language environment configuration for Oracle ASM:

    $ srvctl setenv asm -envs "LANG=en"

#### srvctl start asm

Starts an Oracle ASM instance.

**Note:**

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Syntax

    srvctl start asm [-proxy] [-node node_name [-startoption start_options]]

##### Parameters

Table F-12 srvctl start asm Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-proxy`                       | Optionally, you can use this parameter to specify whether you are starting a proxy Oracle ASM configuration.                                                                                                                                                                                                                                                                                                   |
| `-node ``node_name`            | Optionally, you can specify a particular node on which you want to start Oracle ASM.<br>Note: You can use this parameter only with Oracle Clusterware.                                                                                                                                                                                                                                                         |
| `-startoption ``start_options` | Optionally, you can specify options to the startup command, such as `OPEN`, `MOUNT`, or `NOMOUNT`<br>Note: For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/STARTUP.md) for more information about startup options |

##### Examples

An example of this command to start an Oracle ASM instance on a single node of a cluster is:

    $ srvctl start asm -node crmnode1

An example to start an Oracle ASM instance on all nodes in the cluster, or for a noncluster database, is:

    $ srvctl start asm

#### srvctl status asm

Displays the status of an Oracle ASM instance.

**Note:**

To manage Oracle ASM on Oracle Database 12c and later installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ASM.

##### Syntax

    srvctl status asm [-proxy] [-node node_name] [-detail] [-verbose]

##### Parameters

Table F-13 srvctl status asm Command Parameters

| Parameter         | Description                                                                                                                                       |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `-proxy`          | Optionally, you can use this parameter to display the status for an Oracle ASM proxy instance.                                                    |
| `-node node_name` | Optionally, you can specify a particular node. If you do not specify this parameter, then SRVCTL displays the status of all Oracle ASM instances. |
| `-detail`         | Print detailed status information.                                                                                                                |
| `-verbose`        | Displays verbose output.                                                                                                                          |

##### Example

This command returns output similar to the following:

    $ srvctl status asm -verbose

    ASM is running on node2, node3, node4
    Detailed state on node node2: Started
    Detailed state on node node3: Started
    Detailed state on node node4: Started

#### srvctl stop asm

Stops an Oracle ASM instance.

##### Syntax

    srvctl stop asm [-proxy] [-node node_name] [-stopoption stop_options] [-force]

##### Parameters

Table F-14 srvctl stop asm Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                   |
|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-proxy`                     | Optionally, you can use this parameter to specify whether you are stopping a proxy Oracle ASM configuration.                                                                                                                                                                  |
| `-node ``node_name`          | Optionally, you can specify a particular node on which you want to stop Oracle ASM.<br>If you do not specify this parameter, then SRVCTL stops the Oracle ASM instance on every active node in the cluster.<br>Note: You can use this parameter only with Oracle Clusterware. |
| `-stopoption ``stop_options` | Optionally, you can specify options to the shutdown command, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, or `ABORT`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/SHUTDOWN.md) for more information about shutdown options                                |
| `-force`                     | Optionally, you can use this parameter to stop disk groups, file systems, and databases that depend on Oracle ASM.                                                                                                                                                            |

##### Usage Notes

- To manage Oracle ASM on Oracle Database 12c and later installations, use SRVCTL in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use SRVCTL in the database home to manage Oracle ASM.

- You cannot use this command when OCR is stored in Oracle ASM because it will not stop Oracle ASM. To stop Oracle ASM you must shut down Oracle Clusterware.

##### Example

An example of this command is:

    $ srvctl stop asm -node crmnode1 -stopoption IMMEDIATE

#### srvctl unsetenv asm

Unsets the Oracle ASM environment configurations.

##### Syntax

    srvctl unsetenv asm -envs "name_list"

##### Usage Notes

Use the `-envs` parameter to specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).

##### Example

The following example unsets the environment configuration for an Oracle ASM environment variable:

    $ srvctl unsetenv asm -envs "CLASSPATH"

#### srvctl add asmnetwork

Adds an Oracle ASM network configuration to Oracle Clusterware.

##### Syntax

    srvctl add asmnetwork [-netnum asm_network_number] [-deptype {optional |
      mandatory}] -subnet subnet[/netmask/if1[|if2...]]

##### Parameters

Table F-15 srvctl add asmnetwork Command Parameters

| Parameter                                               | Description                                                                                                                                                                                                             |
|:--------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``asm_network_number`                          | Optionally, you can specify an Oracle ASM network number (default number is 1) that you want to add.                                                                                                                    |
| `-deptype {optional | mandatory}`                       | Specify whether the Oracle ASM dependency type is optional or mandatory. The default is `optional`.                                                                                                                     |
| `-subnet ``subnet``[/``netmask``/``if1``[|``if2``...]]` | Specify a subnet for the Oracle ASM network you want to add. If you do not specify any interface names, then the network uses any interface on the given subnet.<br>For IPv6, `netmask` is a prefix length, such as 64. |

#### srvctl config asmnetwork

Displays the configuration information for Oracle ASM networks registered with Oracle Clusterware.

##### Syntax

    srvctl config asmnetwork [-netnum asm_network_number]

##### Usage Notes

Optionally, you can specify an Oracle ASM network number (default number is 1) for which you want to view configuration information.

#### srvctl modify asmnetwork

Modifies an Oracle ASM network configuration in Oracle Clusterware.

##### Syntax

    srvctl modify asmnetwork [-netnum asm_network_number] [-deptype {optional | mandatory}]

##### Parameters

Table F-16 srvctl modify asmnetwork Command Parameter

| Parameter                         | Description                                                                                             |
|:----------------------------------|:--------------------------------------------------------------------------------------------------------|
| `-netnum ``asm_network_number`    | Optionally, you can specify an Oracle ASM network number (default number is 1) that you want to modify. |
| `-deptype {optional | mandatory}` | Specify whether the Oracle ASM dependency type is optional or mandatory.                                |

#### srvctl remove asmnetwork

Removes an Oracle ASM network configuration from Oracle Clusterware.

##### Syntax

    srvctl remove asmnetwork {-netnum asm_network_number | -all} [-force]

##### Parameters

Table F-17 srvctl remove asmnetwork Command Parameters

| Parameter                               | Description                                                                                                                                                                     |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-netnum ``asm_network_number`` | —all` | Specify an Oracle ASM network number (default number is 1) that you want to remove or specify `–all` to remove all Oracle ASM network numbers configured on Oracle Clusterware. |
| `-force`                                | Use this parameter to forcibly remove an Oracle ASM network regardless of any dependencies.                                                                                     |

#### srvctl add cdp

Adds a cross-cluster dependency proxy resource to a cluster (only on the first public network).

##### Syntax

    srvctl add cdp [-port port_number] [–passfile_admin afile] [-passfile_readonly rfile]

##### Parameters

Table F-18 srvctl add cdp Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                             |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-port ``port_number`        | Optionally, you can specify a port on which all cross-cluster dependency proxy resources in the cluster listen. If you do not specify a port, then SRVCTL chooses a port that is available on all nodes of the Domain Services Cluster. |
| `–passfile_admin ``afile`    | If you have a password file for administrators, then you can specify it using this parameter. If no password file exists, then SRVCTL randomly generates a password.                                                                    |
| `-passfile_readonly ``rfile` | If you have a password file for read-only users, then you can specify it using this parameter. If no password file exists, then SRVCTL writes a randomly-generated password to a file.                                                  |

#### srvctl disable cdp

Disables a cross-cluster dependency proxy resource.

##### Syntax

    srvctl disable cdp [-cdpnumber cdp_ordinal_number]

##### Usage Notes

You can optionally specify the ordinal number of a specific cross-cluster dependency proxy resource that you want to disable. If you choose not to do so, then SRVCTL disables all cross-cluster dependency proxy resources in a cluster.

#### srvctl enable cdp

Enables a cross-cluster dependency proxy resource.

##### Syntax

    srvctl enable cdp [-cdpnumber cdp_ordinal_number]

##### Usage Notes

You can optionally specify the ordinal number of a specific cross-cluster dependency proxy resource that you want to enable. If you choose not to do so, then SRVCTL enables all cross-cluster dependency proxy resources in cluster.

#### srvctl modify cdp

Modifies ports and passwords for a cross-cluster dependency proxy resource.

##### Syntax

    srvctl modify cdp [-port port_number] [–passfile_admin afile] [-passfile_readonly rfile]

##### Parameters

Table F-19 srvctl modify cdp Command Parameters

| Parameter                    | Description                                                                                                      |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------|
| `-port ``port_number`        | Optionally, you can modify the port on which all cross-cluster dependency proxy resources in the cluster listen. |
| `–passfile_admin ``afile`    | Optionally, you can modify the password information for administrators.                                          |
| `-passfile_readonly ``rfile` | Optionally, you can modify the password information for read-only users.                                         |

##### Usage Notes

You must stop the cross-cluster dependency proxy resource before you make any changes.

#### srvctl relocate cdp

Relocates a cross-cluster dependency proxy resource in a cluster.

##### Syntax

    srvctl relocate cdp -cdpnumber cdp_ordinal_number [-node node_name] [-force]

##### Parameters

Table F-20 srvctl relocate cdp Command Parameters

| Parameter                         | Description                                                                                                                                                                                                                                                |
|:----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-cdpnumber ``cdp_ordinal_number` | Specify a cross-cluster dependency proxy resource that you want to relocate by specifying its identifying ordinal number.                                                                                                                                  |
| `-node ``node_name`               | Optionally, you can specify the name of a node on which a cross-cluster dependency proxy resource resides that you want to relocate.                                                                                                                       |
| `–force`                          | Optionally, you can use this parameter to relocate a cross-cluster dependency proxy resource with a running VIP. If you try to relocate a cross-cluster dependency proxy resource with a running VIP without using this parameter, then the command fails. |

#### srvctl remove cdp

Removes a cross-cluster dependency proxy resource from a cluster without removing cross-cluster dependency proxy resources.

##### Syntax

    srvctl remove cdp [-force]

##### Usage Notes

- Use the `–force` parameter to remove a running cross-cluster dependency proxy resource.

- This command completely removes all cross-cluster dependency proxy configuration. If you use `-force` while proxies exist, then the proxies will no longer function until they are re-created.

#### srvctl start cdp

Starts a cross-cluster dependency proxy resource on a cluster.

##### Syntax

    srvctl start cdp [-cdpnumber cdp_ordinal_number] [-node node_name]

##### Parameters

Table F-21 srvctl start cdp Command Parameters

| Parameter                         | Description                                                                                                                                      |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `-cdpnumber ``cdp_ordinal_number` | Optionally, you can use this parameter to start a specific cross-cluster dependency proxy resource by specifying its identifying ordinal number. |
| `-node ``node_name`               | Optionally, you can specify the name of a node on which a cross-cluster dependency proxy resource resides that you want to start.                |

#### srvctl status cdp

Obtains the status of cross-cluster dependency proxy resources.

##### Syntax

    srvctl status cdp [-cdpnumber cdp_ordinal_number]

##### Usage Notes

You can optionally specify the ordinal number of a specific cross-cluster dependency proxy resource. If you choose not to do so, then SRVCTL returns the status of all cross-cluster dependency proxy resources in the cluster.

#### srvctl stop cdp

Stops a cross-cluster dependency proxy resource on a cluster.

##### Syntax

    srvctl stop cdp [-cdpnumber cdp_ordinal_number]

##### Usage Notes

Optionally, you can stop a specific cross-cluster dependency proxy resource by specifying its identifying ordinal number.

#### srvctl add cdpproxy

Adds a cross-cluster dependency proxy resource to a cluster (credentials must exist or be imported, first).

##### Syntax

    srvctl add cdpproxy -client_type client_type -client_name client_name
      [-remote_start {YES|NO}]

##### Parameters

Table F-22 srvctl add cdpproxy Command Parameters

| Parameter                    | Description                                                                  |
|:-----------------------------|:-----------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type that you want to proxy.                    |
| `-client_name ``client_name` | Specify a name for the cluster resource that you want to proxy.              |
| `-remote_start {YES|NO}`     | Specify whether to start the proxy resource when the remote resource starts. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl config cdpproxy

Displays configuration information for a cross-cluster dependency proxy resource.

##### Syntax

    srvctl config cdpproxy -client_type client_type [-client_name client_name]

##### Parameters

Table F-23 srvctl config cdpproxy Command Parameters

| Parameter                    | Description                                                                                           |
|:-----------------------------|:------------------------------------------------------------------------------------------------------|
| `-client_type ``client_type` | The cluster resource type of the proxy for which you want to display the configuration information.   |
| `-client_name ``client_name` | Specify a name for the cluster resource proxy that you want to display the configuration information. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl disable cdpproxy

Disables a cross-cluster dependency proxy resource.

##### Syntax

    srvctl disable cdpproxy -client_type client_type -client_name client_name

##### Parameters

Table F-24 srvctl disable cdpproxy Command Parameters

| Parameter                    | Description                                                             |
|:-----------------------------|:------------------------------------------------------------------------|
| `-client_type ``client_type` | The cluster resource type of the proxy you want to disable.             |
| `-client_name ``client_name` | Specify a name for the cluster resource proxy that you want to disable. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl enable cdpproxy

Enables a cross-cluster dependency proxy resource.

##### Syntax

    srvctl enable cdpproxy -client_type client_type -client_name client_name

##### Parameters

Table F-25 srvctl enable cdpproxy Command Parameters

| Parameter                    | Description                                                            |
|:-----------------------------|:-----------------------------------------------------------------------|
| `-client_type ``client_type` | The cluster resource type of the proxy you want to enable.             |
| `-client_name ``client_name` | Specify a name for the cluster resource proxy that you want to enable. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl modify cdpproxy

Modifies the configuration of a cross-cluster dependency proxy resource.

##### Syntax

    srvctl modify cdpproxy -client_type client_type -client_name client_name
      [-remote_start {YES|NO}]

##### Parameters

Table F-26 srvctl modify cdpproxy Command Parameters

| Parameter                    | Description                                                                  |
|:-----------------------------|:-----------------------------------------------------------------------------|
| `-client_type ``client_type` | The cluster resource type that you want to proxy.                            |
| `-client_name ``client_name` | Specify a name for the cluster resource that you want to proxy.              |
| `-remote_start {YES|NO}`     | Specify whether to start the proxy resource when the remote resource starts. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl relocate cdpproxy

Relocates a cross-cluster dependency proxy from one node of a cluster to another.

##### Syntax

    srvctl relocate cdpproxy -client_type client_type -client_name client_name
      [-node node_name] [-force]

##### Parameters

Table F-27 srvctl relocate cdpproxy Command Parameters

| Parameter                    | Description                                                                                                      |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type of the proxy that you want to relocate.                                        |
| `-client_name ``client_name` | Specify the name of the cluster resource proxy that you want to relocate.                                        |
| `-node ``node_name`          | Optionally, you can specify the name of a node to which you want to relocate the cross-cluster dependency proxy. |
| `–force`                     | You must use this parameter if resources dependent on the cross-cluster dependency proxy are running.            |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl remove cdpproxy

Removes a cross-cluster dependency proxy resource.

##### Syntax

    srvctl remove cdpproxy -client_type client_type [-client_name client_name]
      [-force]

##### Parameters

Table F-28 srvctl remove cdpproxy Command Parameters

| Parameter                    | Description                                                                                               |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type of the proxy that you want to remove.                                   |
| `-client_name ``client_name` | Optionally, you can specify the name of a cluster resource proxy that you want to remove.                 |
| `–force`                     | You must use this parameter if the cross-cluster dependency proxy resource you want to remove is running. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl start cdpproxy

Starts a cross-cluster dependency proxy resource.

##### Syntax

    srvctl start cdpproxy -client_type client_type -client_name client_name
      [-node node_name]

##### Parameters

Table F-29 srvctl start cdpproxy Command Parameters

| Parameter                    | Description                                                                                                   |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type of the proxy that you want to start.                                        |
| `-client_name ``client_name` | Specify a name for the cluster resource proxy that you want to start.                                         |
| `-node ``node_name`          | Optionally, you can specify the name of a node on which you want to start the cross-cluster dependency proxy. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl status cdpproxy

Retrieves the status of a cross-cluster dependency proxy resource.

##### Syntax

    srvctl status cdpproxy -client_type client_type -client_name client_name]

##### Parameters

Table F-30 srvctl status cdpproxy Command Parameters

| Parameter                    | Description                                                                           |
|:-----------------------------|:--------------------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type of the proxy of which you want to check the status. |
| `-client_name ``client_name` | Specify the name of the cluster resource proxy of which you want to check the status. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl stop cdpproxy

Stops a cross-cluster dependency proxy resource.

##### Syntax

    srvctl stop cdpproxy -client_type client_type -client_name client_name
      [-node node_name]

##### Parameters

Table F-31 srvctl stop cdpproxy Command Parameters

| Parameter                    | Description                                                                                                           |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------|
| `-client_type ``client_type` | Specify the cluster resource type of the proxy that you want to stop.                                                 |
| `-client_name ``client_name` | Specify a name for the cluster resource proxy that you want to stop.                                                  |
| `-node ``node_name`          | Optionally, you can specify the name of a node on which you want to stop the cross-cluster dependency proxy resource. |

##### Usage Notes

- For Oracle Clusterware 18c, the client type is always `diskgroup`.

- For Oracle Clusterware 18c, the client name is the name of a remote disk group.

#### srvctl add cvu

Adds the Cluster Verification Utility (CVU) to an Oracle Clusterware configuration.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax and Parameters

Use the `srvctl add cvu` command with the following syntax:

    srvctl add cvu [-checkinterval time_in_minutes]

##### Usage Notes

- Optionally, you can change the interval between checks. By default, CVU runs once every 6 hours and verifies the health of the cluster. The shortest interval you can specify for CVU check is 10 minutes.

- Run this command while logged in as the Grid home user.

##### Example

To add CVU with a check interval of 6 hours, use the following command:

    $ srvctl add cvu -checkinterval 360

#### srvctl config cvu

Displays the time interval, in minutes, between CVU checks.

##### Syntax and Parameters

Use the `srvctl config cvu` command with the following syntax:

    srvctl config cvu

This command has no parameters.

##### Example

This command returns output similar to the following:

    CVU is configured to run once every 360 minutes

#### srvctl disable cvu

Disables the Cluster Verification Utility (CVU) for Oracle Clusterware management (if enabled).

##### Syntax

    srvctl disable cvu [-node node_name]

##### Parameters

Optionally, you can specify the name of a particular node on which you want to disable CVU. Otherwise, SRVCTL disables CVU on all nodes.

##### Example

An example of this command to disable CVU on a node named `crmnode1` is:

    $ srvctl disable cvu -node crmnode1

#### srvctl enable cvu

Enables the Cluster Verification Utility (CVU) for Oracle Clusterware management (if disabled).

##### Syntax

    srvctl enable cvu [-node node_name]

##### Parameters

Optionally, you can specify the name of a particular node on which you want to enable CVU. Otherwise, SRVCTL enables CVU on all nodes.

##### Example

An example of this command to enable CVU on a node named `crmnode1` is:

    $ srvctl enable cvu -node crmnode1

#### srvctl modify cvu

Modifies the check interval for CVU.

##### Syntax

    srvctl modify cvu [-checkinterval time_in_minutes]

##### Parameters

By default, CVU runs once every 360 minutes (six hours) and verifies the health of cluster. If you change the interval, then the shortest interval you can specify for CVU check is 10 minutes.

##### Example

An example of this command to modify CVU to have a check interval of 4 hours is:

    $ srvctl modify cvu -checkinterval 240

#### srvctl relocate cvu

Temporarily relocates the CVU to another node in a cluster.

##### Syntax

    srvctl relocate cvu [-node node_name]

##### Usage Notes

Optionally, you can specify a particular node to which you want to relocate CVU.

##### Example

An example of this command to temporarily relocate CVU from the local node to the cluster node named `crmnode2` is:

    $ srvctl relocate cvu -node crmnode2

#### srvctl remove cvu

Removes CVU from an Oracle Clusterware configuration.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove cvu [-force]

##### Usage Notes

Use the `-force` parameter to remove a CVU resource that is running or starting.

#### srvctl start cvu

Starts the CVU resource on one node in a cluster. If you specify a node name, then CVU starts on that node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start cvu [-node node_name]

##### Usage Notes

Optionally, you can specify a particular node to which you want to start CVU. Otherwise, SRVCTL starts CVU on all nodes.

##### Example

An example of this command to start CVU on a single node of a cluster is:

    $ srvctl start cvu -node crmnode1

#### srvctl status cvu

Displays the current state of the CVU resource on one node in a cluster. If you specify a node name, then the command checks CVU status on that node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status cvu [-node node_name]

##### Usage Notes

Optionally, you can specify a particular node where the CVU resource is running, if it is not the local node.

**Note:**

The local and global status can be different, if CVU is enabled or disabled on selected nodes. Do not use the `-node` parameter to change CVU status globally.

##### Example

An example of this command to check the status of CVU on the node in the cluster named `crmnode1` is:

    $ srvctl status cvu -node crmnode1

#### srvctl stop cvu

Stops the Cluster Verification Utility (CVU) that is either in the running or starting state.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop cvu [-force]

##### Usage Notes

Optionally, you can specify the `-force` parameter to stop CVU if it is a dependant resource.

##### Example

An example of this command to stop CVU:

    $ srvctl stop cvu

#### srvctl add exportfs

Creates an export file system configuration in Oracle Clusterware.

##### Syntax

    srvctl add exportfs -name unique_name -id havip_name -path path_to_export
        [-clients export_clients] [-options export_options] [-type NFS | SMB]

##### Parameters

Table F-32 svrctl add exportfs Command Parameters

| Parameter                                               | Description                                                                                                                                                                                                                                                                                                                                                     |
|:--------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name`                                   | Enter a unique name for the export file system that you are creating. This parameter is required.                                                                                                                                                                                                                                                               |
| `-id ``havip_name`                                      | Enter the number or name that identifies an existing HAVIP, that you specified in the `srvctl add havip` command. This parameter is required.                                                                                                                                                                                                                   |
| `-path ``path_to_export`                                | Enter the path to the Oracle Automatic Storage Management Cluster File System (Oracle ACFS) that you want to export. This parameter is required.                                                                                                                                                                                                                |
| `-clients ``export_clients`` -options ``export_options` | Optionally, enter a comma-delimited list of clients to which you want the file system exported. You can enter net groups and wildcards. For example:<br>`-clients @netgroup1,`<br>`*.us.domain.com,`<br>`16.140.0.0, hostname1`<br>Note: You can use the `-clients` parameter only for Linux systems. Use the `-options` parameter for Solaris and AIX systems. |
| `-type NFS | SMB`                                       | Specify the export type (`NFS` for a network file system or `SMB` for Oracle ACFS server message block). The default is `NFS` for Linux and UNIX platforms, and `SMB` for Windows.                                                                                                                                                                              |

##### Usage Notes

- You cannot use the `–clients` parameter with `—type SMB`.

- You must run this command as `root` on Linux and UNIX platforms.

##### Example

To export with operating system defaults:

    # srvctl add exportfs -name cifsExport -path "/acfs1" -options "browsable = yes,read only = no,comment = acfs1"

To export read-only to certain clients:

    # srvctl add exportfs -name export1 -id havip1 -path /u01/db1 -clients node1 -options ro

#### srvctl config exportfs

Displays the configuration information for the export file system in Oracle Clusterware.

##### Syntax

    srvctl config exportfs [-name unique_name | -id havip_name]

##### Parameters

Table F-33 srvctl config exportfs Command Parameters

| Parameter             | Description                                                                                                   |
|:----------------------|:--------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Enter the unique name of the NFS export for which you want to display the configuration.                      |
| `-id ``havip_name`    | Enter the name of a HAVIP to display the configuration of all the NFS exports attached to the specific HAVIP. |

##### Example

If you specify the `-name` parameter, then this command returns output similar to the following, whether you specify `-name` or `-id`:

    $ srvctl config exportfs -id havip1

    export file system kep1 is configured
    Exported path: /scratch/ghnew/base/mymount3
    Export options:
    Export Type:
    Exported clients:
    export file system kexp2 is configured
    Exported path: /scratch/ghnew/base/mymount3
    Export options:
    Export Type:
    Exported clients:

#### srvctl disable exportfs

Disables an export file system managed by Oracle Clusterware.

##### Syntax

    srvctl disable exportfs -name filesystem_name

##### Usage Notes

- This command takes only the unique name of the file system you want to disable.

- You must run this command as `root` user on Linux and UNIX platforms.

##### Example

The following example disables an export file system called `export1`:

    # srvctl disable exportfs -name export1

#### srvctl enable exportfs

Enables an export file system configuration in Oracle Clusterware.

##### Syntax

    srvctl enable exportfs -name filesystem_name

This command takes only the name of the file system you want to enable, which is a required parameter.

##### Usage Notes

You must run this command as the `root` user on Linux and UNIX platforms.

##### Example

The following command example enables a file system named `export1`:

    # srvctl enable exportfs -name export1

#### srvctl modify exportfs

Modifies an export file system configuration in Oracle Clusterware.

##### Syntax

    srvctl modify exportfs -name unique_name [-path path_to_export]
        [-clients node_list] [-options nfs_options_string]

##### Parameters

Table F-34 srvctl modify exportfs Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                                          |
|:-------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name`          | Enter the unique name of the NFS export file system to modify. This parameter is required.                                                                                                                                                                                                                                                           |
| `-path ``path_to_export`       | You can modify the path to the Oracle Automatic Storage Management Cluster File System (Oracle ACFS) where the export is located.                                                                                                                                                                                                                    |
| `-clients ``node_list`         | You can modify the comma-delimited list of clients (hosts) to where the file system is exported. You can enter net groups and wildcards. For example:<br>`-clients @netgroup1,*.us.domain.com,16.140.0.0, hostname1`<br>Note: You can use the `-clients` parameter only for Linux systems. Use the `-options` parameter for Solaris and AIX systems. |
| `-options ``nfs_client_string` | Use this parameter to modify the export options for the export file system.                                                                                                                                                                                                                                                                          |

##### Usage Notes

- You must run this command as root user on Linux and UNIX platforms.

- You must start and stop the NFS export before any changes you make take effect.

##### Example

The following command example modifies the path of an export file system named `exportfs1`:

    # srvctl modify exportfs -name exportfs1 -path /mnt/racdb1

#### srvctl remove exportfs

Removes the specified export file system configuration.

##### Syntax

    srvctl remove exportfs -name exportfs_name [-force]

##### Parameters

Table F-35 srvctl remove exportfs Command Parameters

| Parameter               | Description                                                                               |
|:------------------------|:------------------------------------------------------------------------------------------|
| `-name ``exportfs_name` | Enter the unique name of the export file system you want to remove.                       |
| `-force`                | Use this parameter to ignore any dependencies and forcibly remove the export file system. |

##### Usage Notes

- You must run this command as `root` user on Linux and UNIX platforms.

- If you do not use the `-force` parameter, then you must first stop the export file system you want to remove before you remove it.

- If you use the `-force` parameter, then the resulting configuration can cause errors when attempting to shut down the Oracle Clusterware stack.

##### Examples

To remove the stopped export file system named `export1`:

    # srvctl remove exportfs -name export1

To remove a running export file system, leaving it exported:

    # srvctl remove exportfs -name export1 -force

#### srvctl start exportfs

Starts an export file system configuration in Oracle Clusterware.

##### Syntax

    srvctl start exportfs {-name unique_name | -id havip_name}

##### Parameters

Table F-36 srvctl start exportfs Command Parameters

| Parameter             | Description                                                |
|:----------------------|:-----------------------------------------------------------|
| `-name ``unique_name` | Enter the unique name of the NFS export you want to start. |
| `-id ``havip_name`    | The unique ID associated with the HAVIP resource.          |

##### Example

To start an export file system:

    $ srvctl start exportfs -name export1

#### srvctl status exportfs

Displays the status of an export file system configuration.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status exportfs [-name unique_name | -id havip_name]

##### Parameters

Table F-37 srvctl status exportfs Command Parameters

| Parameter             | Description                                                                                                                                                 |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Optionally, you can specify the unique name of the NFS export for which you want to display the status.                                                     |
| `-id ``havip_name`    | Alternatively, you can specify the name of an HAVIP resource and display the status of all of the NFS exports associated with the specified HAVIP resource. |

##### Usage Notes

If you do not specify any parameters, then SRVCTL displays the status for all NFS exports in the cluster.

##### Example

This command returns output similar to the following:

    $ srvctl status exportfs

    export file system export1 is enabled
    export file system export1 is not exported
    export file system export2 is enabled
    export file system export2 is exported on node node1

#### srvctl stop exportfs

Stops an export file system configuration managed by Oracle Clusterware.

##### Syntax

    srvctl stop exportfs {-name unique_name | -id havip_name} [-force]

##### Parameters

Table F-38 srvctl stop exportfs Command Parameters

| Parameter             | Description                                                                                                                                                                  |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Enter the unique name of the NFS export you want to stop.                                                                                                                    |
| `-id ``havip_name`    | Alternatively, you can specify the name of an HAVIP. If you specify this parameter, then SRVCTL stops all of the NFS exports associated with the HAVIP resource you specify. |
| `–force`              | Stop the NFS export, ignoring errors.                                                                                                                                        |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Example

An example of this command is:

    # srvctl stop exportfs -name export1

#### srvctl add filesystem

Adds a device containing a file system (Oracle Automatic Storage Management Cluster File System (Oracle ACFS) or other) to the Oracle Clusterware stack for automount and high availability.

An Oracle ACFS file system resource is typically created for use with application resource dependency lists. For example, if an Oracle ACFS file system is configured for use as an Oracle Database home, then a resource created for the file system can be included in the resource dependency list of the Oracle Database application. This will cause the file system and stack to be automatically mounted because of the start action of the database application.

##### Syntax

    srvctl add filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name}
        -path mountpoint_path [-node "node_list" | -serverpool "server_pool_list"]
        [-user "user_list"] [-mountowner user_name] [-mountgroup group_name] [-mountperm octal_permission]
        [-fstype {ACFS | EXT3 | EXT4}] [-fsoptions options] [-description description]
        [-appid application_id] [-autostart {ALWAYS | NEVER | RESTORE}] [-acceleratorvols volume_name]

**Note:**

Oracle supports the `EXT3` and `EXT4` values for the `-fstype` parameter only for Linux.

##### Parameters

Table F-39 srvctl add filesystem Command Parameters

| Parameter                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-device ``volume_device`                              | Specify the path to the file system volume device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-volume ``volume_name`                                | Specify the name of the volume.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-diskgroup ``disk_group_name`                         | Specify the name of the disk group on which the `-volume` is located.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-path ``mountpoint_path`                              | Specify the mount point path that is used to set up dependencies on other resources for nested mounts. This must be an absolute path.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-node ``node_list`` | -serverpool ``server_pool_list` | Optionally, you can specify a comma-delimited list of nodes on which to mount the file system device. If you specify a list of nodes or a server pool, then SRVCTL creates a single-node file system resource. Without any nodes or server pools, SRVCTL creates a file system resource that runs on every cluster node.<br>Alternatively, you can specify a comma-delimited list of server pools in which a file system will run. If you specify a list of server pools, then you dynamically limit the number or type of nodes on which a file system will run. This does not count as a cluster-wide file system for later usage that may require a cluster-wide Oracle ACFS resource, such as HANFS.<br>Note: Nodes and server pools are mutually exclusive. |
| `-user ``user_list`                                    | Optionally, you can specify a comma-delimited list of users authorized to mount and unmount the file system.<br>If the file system is for Oracle Database software, then specify the name of the Oracle home owner.<br>If you specify no users, then only `root` can mount and unmount the file system, or run `srvctl` `start` `filesystem` on the file system.                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-mountowner ``user_name`                              | Optionally, you can specify the user that is the mount point owner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-mountgroup ``group_name`                             | Optionally, you can specify the group that includes the mount point owners.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-mountperm ``octal_permission`                        | Optionally, you can specify the permissions (OCTAL format) for the mount point.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-fstype {ACFS | EXT3 | EXT4}`                         | Optionally, you can specify the type of file system to be mounted. The default value is `ACFS`.<br>If the type of file system to be mounted is not `ACFS`, then it must be a single-node file system, and you must specify `-node` or `-serverpool`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-fsoptions ``options`                                 | Optionally, you can specify options used to mount the file system. The options are file system and operating system dependent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-description ``description`                           | Optionally, you can specify a description of the file system. This is stored as an attribute for later viewing by an administrator.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-appid ``application_id`                              | Optionally, you can specify an application ID, which is a unique identifier used to group file systems into logical groupings. You can use this method to group file systems that may be different on different nodes but are used by an application that must have a dependency on the resource type, which is `ora.id.fs.type`.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-autostart {ALWAYS | NEVER | RESTORE}`                | Optionally, you can specify the file system resource `autostart` policy.<br>• `ALWAYS`: The file system resource always automatically starts.<br>• `NEVER`: The file system does not automatically start.<br>• `RESTORE`: The file system is restored to its last state. This is the default option.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-acceleratorvols ``volume_name`                       | Optionally, you can specify the accelerator volume. An accelerator volume is a secondary Oracle ACFS volume that is used by Oracle ACFS to store critical metadata.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to add, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- You must run this command as `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms.

- This command must be run only one time from the Oracle Grid Infrastructure home.

- To manage Oracle ACFS on Oracle Database installations, use the SRVCTL binary in the Oracle Grid Infrastructure home for a cluster (Grid home). If you have Oracle RAC or Oracle Database installed, then you cannot use the SRVCTL binary in the database home to manage Oracle ACFS.

- Standard Edition High Availability (SEHA) databases are supported only on Oracle Database 19c (19.7) release or later.

- This command is only available with Oracle Clusterware.

##### Examples

To add the `d1volume1-295` disk device in the disk group `RAC_DATA` as the Oracle ACFS volume `VOLUME1` with a mount point of `/oracle/cluster1/acfs`:

    # srvctl add filesystem -device /dev/asm/d1volume1-295
      -path /oracle/cluster1/acfs1

To add an Oracle ACFS file system on the dynamic volume device `asm-test-55`, with this file system mounted on one of the specified nodes at a time:

    # srvctl add filesystem -fstype ACFS -device asm-test-55 -path myacfs
     -node node1,node2,node3

To add an Oracle ACFS file system for configuring Standard Edition High Availability (SEHA) on the `sehome` volume of the `DATA` disk group with a mount point of `/u01/app/oracle`:

    # srvctl add filesystem -volume sehome -diskgroup DATA -path /u01/app/oracle -fstype ACFS
      -autostart ALWAYS -user oracle

#### srvctl config filesystem

Displays the configuration for a specific file system resource.

##### Syntax

    srvctl config filesystem [-device volume_device | -volume volume_name -diskgroup disk_group_name]

##### Parameters

Table F-40 srvctl config filesystem Command Parameters

| Parameter                      | Description                                                           |
|:-------------------------------|:----------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                    |
| `-volume ``volume_name`        | Specify the name of the volume.                                       |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located. |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to display the configuration or specify `-volume` volume_name `-diskgroup` disk_group_name.

- This command is only available with Oracle Clusterware.

##### Examples

The following example lists the configuration of all file systems:

    $ srvctl config filesystem

The following example displays the configuration for a specific device:

    $ srvctl config filesystem -device /dev/asm/d1volume1-295

#### srvctl disable filesystem

Disables a specific Oracle Clusterware-managed file system volume.

##### Syntax

    srvctl disable filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name}

##### Parameters

Table F-41 srvctl disable filesystem Command Parameters

| Parameter                      | Description                                                           |
|:-------------------------------|:----------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                    |
| `-volume ``volume_name`        | Specify the name of the volume.                                       |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located. |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to disable, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl disable filesystem -device /dev/asm/racvol1

#### srvctl enable filesystem

Enables an Oracle ACFS volume or generic file system in Oracle Clusterware.

##### Syntax

    srvctl enable filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name}

##### Parameters

Table F-42 srvctl enable filesystem Command Parameters

| Parameter                      | Description                                                           |
|:-------------------------------|:----------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                    |
| `-volume ``volume_name`        | Specify the name of the volume.                                       |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located. |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to enable, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl enable filesystem -device /dev/asm/racvol1

#### srvctl modify filesystem

Modifies the configuration of the file system resource.

##### Syntax

    srvctl modify filesystem
        {-device volume_device | -volume volume_name -diskgroup disk_group_name}
        [-user {/+|/-}user_name | "user_list"]
        [-mountowner user_name] [-mountgroup group_name] [-mountperm octal_permission]
        [-path mountpoint_path] [-node "node_list" | -serverpool "server_pool_list"]
        [-fsoptions options] [-description description]
        [-autostart {ALWAYS | NEVER | RESTORE}] [-force]

##### Parameters

Table F-43 srvctl modify filesystem Command Parameters

| Parameter                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-device ``volume_device`                                    | Specify the path to the file system volume device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-volume ``volume_name`                                      | Specify the name of the volume.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-diskgroup ``disk_group_name`                               | Specify the name of the disk group on which the `-volume` is located.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-user ``user_name`` | "``user_list``"`                      | Specify the user(s) who is authorized to mount and unmount the file system. You can add (/+) or remove (/-) single a user, or replace the entire set of users with a comma-delimited list. If you do not specify this parameter, then SRVCTL defaults to the user running the command.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-mountowner ``user_name`                                    | Modify the owner of the mount point with the specified value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-mountgroup ``group_name`                                   | Modify the group of the mount point with the specified value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-mountperm ``octal_permission`                              | Modify the permissions of the user, group, and others with the specified value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-path ``mountpoint_path`                                    | Modify the mount point path that is used to set up dependencies on other resources for nested mounts. This must be an absolute path.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-node "``node_list``" | -serverpool "``server_pool_list``"` | Modify a comma-delimited list of nodes on which to mount the file system device. If you specify a list of nodes or a server pool, then SRVCTL creates a single-node file system resource. Without any nodes or server pools, SRVCTL creates a file system resource that runs on every cluster node.<br>Alternatively, you can modify a comma-delimited list of server pools in which a file system will run. If you specify a list of server pools, then you dynamically limit the number or type of nodes on which a file system will run. This does not count as a cluster-wide file system for later usage that may require a cluster-wide Oracle ACFS resource, such as HANFS.<br>Note: Nodes and server pools are mutually exclusive. |
| `-fsoptions ``options`                                       | Modify options used to mount the file system. The options (comma-delimited list) are file system and operating system dependent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-description ``description`                                 | Modify the description of the file system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-autostart {ALWAYS | NEVER | RESTORE}`                      | Modify the file system resource autostart policy.<br>• `ALWAYS`: The file system resource always automatically starts<br>• `NEVER`: The file system does not automatically start<br>• `RESTORE`: The file system is restored to its last state. This is the default option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-force `                                                    | Force modification. This option ignores dependencies.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to modify, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- When performing online changes to the file system resource, the changes take effect only after the resource is next (re)started.

- You must run this command as `root` user on Linux and UNIX platforms.

- This command is only available with Oracle Clusterware.

##### Example

The following example changes the authorized user to `sysad` for the `RACVOL1` volume:

    # srvctl modify filesystem -device /dev/asm/racvol1 -user /+sysad

#### srvctl predict filesystem

Predicts the consequences of file system failure.

##### Syntax

    srvctl predict filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name} [-verbose]

##### Parameters

Table F-44 srvctl predict filesystem Command Parameters

| Parameter                      | Description                                                                  |
|:-------------------------------|:-----------------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                           |
| `-volume ``volume_name`        | Specify the name of the volume.                                              |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located.        |
| `-verbose`                     | Optionally, you can use the `-verbose` parameter to display detailed output. |

##### Usage Notes

- Specify the `-device` parameter to specify the path to the file system resource for which you want to predict the consequences of file system failure, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- Optionally, you can choose verbose output.

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    $ srvctl predict filesystem -device /dev/asm/volume1-123

#### srvctl remove filesystem

Removes a specific file system resource from the cluster.

##### Syntax

    srvctl remove filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name} [-force]

##### Parameters

Table F-45 srvctl remove filesystem Command Parameters

| Parameter                      | Description                                                                                      |
|:-------------------------------|:-------------------------------------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                                               |
| `-volume ``volume_name`        | Specify the name of the volume.                                                                  |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located.                            |
| `-force`                       | Optionally, you can use the `-force` parameter to forcibly remove the resource from the cluster. |

##### Usage Notes

- Specify the `-device` parameter to specify the path to the file system resource for which you want to remove, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- Optionally, you can use the `-force` parameter to ignore any resource dependencies and forcibly remove the resource from the cluster.

- You must run this command as `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms.

- This command is only available with Oracle Clusterware.

##### Examples

An example of this command is:

    # srvctl remove filesystem -device /dev/asm/racvol1

#### srvctl start filesystem

Starts (mounts) the file system resource.

##### Syntax

    srvctl start filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name} [-node node_name]

##### Parameters

Table F-46 srvctl start filesystem Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                           |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path of the file system resource device that you want to start.                                                                                                                                                           |
| `-volume ``volume_name`        | Specify the name of the volume.                                                                                                                                                                                                       |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located.                                                                                                                                                                 |
| `-node ``node_name`            | Optionally, you can specify the name of the node on which the file system resource should be started.<br>If you do not specify this parameter, then SRVCTL starts the file system resource on all the available nodes in the cluster. |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to start, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- You must run this command as `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms, or as a configured file system user.

  If `srvctl add filesystem` was run with the `-user` parameter to identify users authorized to mount and unmount the file system, then you can run `srvctl` `start` `filesystem` as one of the configured file system users.

  **See Also:**

  `srvctl add filesystem` for more information about configuring file system users

- This command is only available with Oracle Clusterware.

##### Examples

To start a file system on all configured nodes in the cluster:

    $ srvctl start filesystem -device /dev/asm/data_db1-68

To start the file system on `node1`:

    $ srvctl start filesystem -device /dev/asm/data_db1-68 -node node1

#### srvctl status filesystem

Displays the status of the file system resource.

##### Syntax

    srvctl status filesystem [-device volume_device | -volume volume_name -diskgroup disk_group_name] [-verbose]

##### Parameters

Table F-47 srvctl status filesystem Command Parameters

| Parameter                      | Description                                                                  |
|:-------------------------------|:-----------------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device.                           |
| `-volume ``volume_name`        | Specify the name of the volume.                                              |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located.        |
| `-verbose`                     | Optionally, you can use the `-verbose` parameter to display detailed output. |

##### Usage Notes

- Optionally, you can use the `-device` parameter to specify the path to the file system resource for which you want to obtain status, or specify `-volume` volume_name `-diskgroup` disk_group_name. If you do not specify `-device` or `-volume` `-diskgroup`, then SRVCTL displays the status of all file systems.

- This command is only available with Oracle Clusterware.

##### Examples

You can specify a device, or volume and disk group.

For example, if you specify a device name:

    $ srvctl status filesystem -d /dev/asm/fs1vol-358
    ACFS file system /acfs/fs1 is not mounted

    $ srvctl start filesystem -d /dev/asm/fs1vol-358
    ...
    $ srvctl status filesystem -d /dev/asm/fs1vol-358
    ACFS file system /acfs/fs1 is mounted on nodes nd1-4n-01,nd1-4n-02,nd1-4n-03,nd1-4n-04

For example, if you specify a volume and disk group:

    $ srvctl status filesystem -volume fs1vol -diskgroup DATA
    ACFS file system /acfs/fs1 is mounted on nodes nd1-4n-01,nd1-4n-02,nd1-4n-03,nd1-4n-04

If you do not specify a device, or volume and disk group:

    $ srvctl status filesystem
    ACFS file system /acfs/fs1 is mounted on nodes nd1-4n-01,nd1-4n-02,nd1-4n-03,nd1-4n-04

**Note:**

In the preceding examples, the file system is Oracle ACFS. If you are using other file systems, then the file systems display as EXT3 or EXT4.

#### srvctl stop filesystem

Stops (unmounts) the Oracle ACFS file system or generic file system.

##### Syntax

    srvctl stop filesystem {-device volume_device | -volume volume_name -diskgroup disk_group_name} [-node node_name] [-force]

##### Parameters

Table F-48 srvctl stop filesystem Command Parameters

| Parameter                      | Description                                                                                                                                                     |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-device ``volume_device`      | Specify the path to the file system volume device that you want to stop.                                                                                        |
| `-volume ``volume_name`        | Specify the name of the volume.                                                                                                                                 |
| `-diskgroup ``disk_group_name` | Specify the name of the disk group on which the `-volume` is located.                                                                                           |
| `-node ``node_name`            | Optionally, you can specify the name of a node. If you do not specify this parameter, then SRVCTL stops the volume resource on all active nodes in the cluster. |
| `-force`                       | Optionally, you can use `-force` to stop the file system and also stop any databases or other resources that depend on this file system.                        |

##### Usage Notes

- Use the `-device` parameter to specify the path to the file system resource for which you want to stop, or specify `-volume` volume_name `-diskgroup` disk_group_name.

- You must run this command as `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms, or as a configured file system user.

  If `srvctl` `add` `filesystem` was executed with the `-user` parameter to identify users authorized to mount and unmount the file system, then you can run `srvctl` `stop` `filesystem` as one of the configured file system users.

  **See Also:**

  `srvctl add filesystem` for more information about configuring file system users

- This command is only available with Oracle Clusterware.

##### Example

An example of this command is:

    # srvctl stop filesystem -device /dev/asm/racvol_1 -force

#### srvctl add gns

Adds the Grid Naming Service (GNS) to a cluster when you are using a DHCP public network or creating a client cluster.

##### Syntax

Use the `srvctl add gns` command with one of the following syntax models:

To add GNS to a cluster that is not currently running GNS:

    srvctl add gns [-domain domain_name] -vip {vip_name | ip_address} [-skip] [-verbose]

To change a cluster that is not running GNS to be a client cluster of another cluster that is running GNS:

    srvctl add gns -clientdata file_name

To add a secondary GNS to a cluster:

    srvctl add gns -vip vip_name | ip_address -clientdata file_name

##### Parameters

Table F-49 srvctl add gns Command Parameters

| Parameter                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-domain ``domain_name`                | The network subdomain that is used for Forward DNS Lookup of cluster IP addresses. You can only use this parameter if you specify `-vip`, and you must use this parameter if the cluster to which you are adding GNS has a GNS zone delegation and you are using DHCP. The cluster to which you add GNS using `-vip` with the `-domain` parameters becomes a server cluster.<br>If you do not specify `-domain`, then SRVCTL adds GNS without a domain.  |
| `-vip {``vip_name`` | ``ip_address``}` | Specify either the virtual IP (VIP) name or IP address on which GNS listens for DNS requests. You cannot use `-vip` with `-clientdata`.<br>Use the `-domain` parameter with `-vip` to make the cluster to which you are adding GNS a server cluster.                                                                                                                                                                                                     |
| `-skip`                                | Specify this parameter to skip the reachability check of the VIP address.                                                                                                                                                                                                                                                                                                                                                                                |
| `-clientdata ``path_to_file`           | Specify the path to the file you created with the `srvctl export gns` command that contains the GNS credentials. You must copy this file to a node in the cluster you are adding before running the `srvctl add gns` command.<br>The cluster to which you add GNS using `-clientdata` becomes either a client cluster or a secondary GNS.<br>You can only use the `-clientdata` parameter with the `-vip` parameter when you are adding a secondary GNS. |
| `-verbose`                             | Verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                          |

##### Usage Notes

- You must run this command as `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms.

- When you are adding GNS to a cluster for the first time, use the `-vip` parameter with the `-domain` parameter.

- When you are adding GNS to a cluster using the `-clientdata` parameter, you must first export the GNS data to a file and manually copy the file to a node in the cluster you are adding. Use the `-clientdata` parameter and run this command on any node in the cluster.

- You can only specify the `-vip` and `-clientdata` parameters at the same time when you are adding a secondary GNS.

##### Examples

To add GNS to a cluster, making it a server cluster:

    # srvctl add gns -vip 192.168.16.17 -domain cluster.mycompany.com

To add GNS to a cluster, making it a client cluster:

    # srvctl add gns -clientdata /tmp/gnsdata

#### srvctl config gns

Displays the configuration for the grid naming service (GNS).

##### Syntax

    srvctl config gns [-detail] [-subdomain] [-multicastport] [-node node_name] [-port] [-status]
      [-version] [-query name] [-list] [-clusterguid] [-clustername] [-clustertype] [-loglevel]
      [-network] [-role] [-instances]

##### Parameters

Table F-50 srvctl config gns Command Parameters

| Parameter           | Description                                                                   |
|:--------------------|:------------------------------------------------------------------------------|
| `-detail`           | Print detailed configuration information about the GNS.                       |
| `-subdomain`        | Display the subdomain served by GNS.                                          |
| `-multicastport`    | Display the port on which the GNS daemon is listening for multicast requests. |
| `-node ``node_name` | Display the configuration information for GNS on the specified node.          |
| `-port`             | Display the port that the GNS daemon uses to communicate with the DNS server. |
| `-status`           | Display the status of GNS.                                                    |
| `-version`          | Display the version of GNS.                                                   |
| `-query ``name`     | Query GNS for the records belonging to a specific name.                       |
| `-list`             | List all records in GNS.                                                      |
| `-clusterguid`      | Display the globally unique identifier of the cluster where GNS is running.   |
| `-clustername`      | Display the name of the cluster where GNS is running.                         |
| `-clustertype`      | Display the type of configuration of GNS on this cluster.                     |
| `-loglevel`         | Print the log level of the GNS.                                               |
| `-network`          | Display network on which GNS is listening.                                    |
| `-role`             | Display the role of the GNS instance.                                         |
| `-instances`        | Display the instance list.                                                    |

#### srvctl disable gns

Disables GNS for a specific node, or all available nodes in the cluster.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable gns [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a node in the cluster on which you want to disable GNS. If you do not specify this parameter, then SRVCTL disables GNS for the entire cluster.

- Optionally, you can use the `-verbose` parameter to display detailed output.

##### Example

An example of this command to disable GNS on the node named `crm7` is:

    $ srvctl disable gns -node crm7

#### srvctl enable gns

Enables GNS on all nodes or a specific node.

**Note:**

This command can be used only with Oracle Clusterware.

##### Syntax

    srvctl enable gns [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a node on which you want to enable GNS. If you do not specify this parameter, then SRVCTL enables GNS on all nodes in the cluster.

- Optionally, you can use the `-verbose` parameter to print detailed output.

##### Example

An example of this command is:

    $ srvctl enable gns -node node1

#### srvctl export gns

Exports Grid Naming Service (GNS) instance data to a file that you can use when you are either moving GNS from one server cluster to another or when you are creating a client cluster.

SRVCTL extracts the data from OCR. Exported data includes:

- The credentials used to authorize users, which includes the VIP address on which the server listens

- The names and DNS records kept in GNS

##### Syntax

    srvctl export gns {-instance path_to_file | {-clientdata path_to_file -role {CLIENT|SECONDARY} [-version]}}

##### Parameters

Table F-51 srvctl export gns Command Parameters

| Parameter                                               | Description                                                                                                                                                                                                                                                                                                                                                             |
|:--------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-instance ``path_to_file`                              | Use this parameter to specify the file to which GNS instance data is written, when you are moving GNS from one server cluster to another.                                                                                                                                                                                                                               |
| `-clientdata ``path_to_file`` -role {CLIENT|SECONDARY}` | Use this parameter to specify the file to which GNS credentials data is written, when you are adding a client cluster to create a file that contains credentials that the client cluster accesses to perform name management operations on the server cluster.<br>You must also use the `-role` parameter to specify a role for which the client data will be exported. |
| `-version`                                              | Optionally, you can use this parameter to specify the version for which the client data will be generated.                                                                                                                                                                                                                                                              |

##### Example

The following command exports the GNS credentials data to a file named `gns.txt`:

    $ srvctl export gns -clientdata /temp/gnsdata/gns.txt

#### srvctl import gns

The `srvctl import gns` command imports data from a file that you create when you run the `srvctl export gns` command. Use this command when you want to locate GNS to a different server cluster.

When you import GNS data, SRVCTL stores the credentials and places the record data into OCR. If another GNS instance is running or data for another instance is encountered during the import procedure, then an error occurs.

This command also makes the cluster in which you run it the server cluster.

**Note:**

This command is only available with Oracle Clusterware.

#### srvctl modify gns

Modifies the IP address, domain, or other configuration parameters used by the grid naming service (GNS).

##### Syntax

Use the `srvctl modify gns` command with one of the following syntax models:

    srvctl modify gns -loglevel log_level

or

    srvctl modify gns [-resolve name] [-verify name]
      [-parameter name:value[,name:value...]]
      [-vip {vip_name | ip} [-skip]] [-clientdata file_name]
      [-role {PRIMARY} [-force]] [-verbose]

##### Parameters

Table F-52 srvctl modify gns Command Parameters

| Parameter                                               | Description                                                                                                                                                                                                                                          |
|:--------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-loglevel ``log_level`                                 | Specify the GNS diagnostic logging level (acceptable values are 1-6).                                                                                                                                                                                |
| `-resolve ``name`                                       | Resolve the name you specify through GNS.                                                                                                                                                                                                            |
| `-verify ``name`                                        | Check to see if the specified name is advertised through GNS.                                                                                                                                                                                        |
| `-parameter ``name``:``value``[,``name``:``value``...]` | Set the value of one or more configuration parameters.                                                                                                                                                                                               |
| `-vip {``vip_name`` | ``ip``} [-skip]`                  | Specify a VIP name or IP address on which GNS is to listen.<br>Note: You can modify this attribute using Online Resource Attribute Modification.<br>Optionally, you can use the `-skip` parameter to skip the reachability check of the VIP address. |
| `-clientdata ``file_name`                               | Modifies the GNS client data with client data contained in the specified file.                                                                                                                                                                       |
| `-role {PRIMARY} [-force]`                              | Convert a secondary GNS instance to primary.<br>Use the `-force` parameter to forcibly convert the secondary GNS instance to primary.                                                                                                                |

##### Examples

An example of this command is:

    $ srvctl modify gns -vip 192.0.2.15

#### srvctl relocate gns

Relocates GNS from its current hosting node to another node within the cluster.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl relocate gns [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a node to which you want to move GNS.

- Optionally, you can use the `-verbose` parameter to display verbose output.

- On Linux and UNIX systems, you must be logged in as `root` and on Windows, you must be logged in as a user with Administrator privileges to run this command.

##### Example

An example of this command is:

    # srvctl relocate gns -node node1

#### srvctl remove gns

Removes GNS from the cluster.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove gns [-force] [-verbose]

##### Usage Notes

- Optionally, you can use the `-force` parameter to forcibly remove GNS from the cluster, regardless of any errors that might occur.

- Optionally, you can use the `-verbose` parameter to display verbose output.

##### Example

An example of this command is:

    $ srvctl remove gns

#### srvctl start gns

Starts GNS on a specific node.

##### Syntax

    srvctl start gns [-loglevel log_level] [-node node_name] [-verbose]

##### Parameters

Table F-53 srvctl start gns Command Parameters

| Parameter               | Description                                                                                                                                                              |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-loglevel ``log_level` | Optionally, you can specify the level of logging with which GNS should run. Log levels vary between 1 (minimal tracing) and 6 (traces everything and is time consuming). |
| `-node ``node_name`     | Optionally, you can specify the name of a node in the cluster where you want to start GNS.                                                                               |
| `-verbose`              | Optionally, you can use this parameter to display verbose output.                                                                                                        |

##### Usage Notes

You can only run this command in the [server cluster](glossary.md). If you attempt to run this command in a [client cluster](glossary.md), then an error occurs.

##### Example

An example of this command to start the GNS on the cluster node named `crmnode1` is:

    $ srvctl start gns -node crmnode1

#### srvctl status gns

Displays the current state of GNS.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status gns [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify a node on which GNS is running for which you want to display the state.

- Optionally, you can use the `-verbose` parameter to display detailed output.

#### srvctl stop gns

Stops GNS in the cluster.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop gns [-node node_name] [-force] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a node on which GNS is running that you want to stop.

- Optionally, you can use `-force` and `-verbose` to forcibly stop GNS and print detailed output, respectively.

##### Example

An example of this command to stop GNS on the local node is:

    $ srvctl stop gns

#### srvctl update gns

Modifies a Grid Naming Service (GNS) instance.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

Use the `srvctl update gns` command with one of these syntax models:

    srvctl update gns -advertise name -address ip_address [-timetolive time_to_live
    ]
      [-verbose]

    srvctl update gns -delete name [-address address] [-verbose]

    srvctl update gns -alias alias -name name [-timetolive time_to_live] [-verbose]

    srvctl update gns -deletealias alias [-verbose]

    srvctl update gns -createsrv service -target target -protocol protocol
      [-weight weight] [-priority priority] [-port port_number]
      [-timetolive time_to_live] [-instance instance_name] [-verbose]

    srvctl update gns -deletesrv service_name -target target -protocol protocol
       [-verbose]

    srvctl update gns -createtxt name -target target [-timetolive time_to_live]
       [-namettl name_ttl] [-verbose]

    srvctl update gns -deletetxt name -target target [-verbose]

    srvctl update gns -createptr name -target target [-timetolive time_to_live]
       [-namettl name_ttl] [-verbose]

    srvctl update gns -deleteptr name -target target [-verbose]

##### Parameters

Table F-54 srvctl update gns Command Parameters

| Parameter                    | Description                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------|
| `-advertise ``name`          | Use this parameter to advertise a name through GNS.                                                             |
| `-address ``ip_address`      | Specify the IP address for an advertised name.                                                                  |
| `-timetolive ``time_to_live` | Optionally, you can specify, in seconds, an amount of time for the record to live.                              |
| `-delete ``name`             | Use this parameter to remove the advertisement of a name from GNS.                                              |
| `-alias ``alias`             | Use this parameter to create an alias for an advertised name.                                                   |
| `-name ``name`               | You must specify a name to associate with the alias.                                                            |
| `-deletealias ``alias`       | Use this parameter to delete an alias.                                                                          |
| `-createsrv ``service`       | Use this parameter to create a service that is described by the record.                                         |
| `-target ``target`           | Use this parameter to associate a name with the service.                                                        |
| `-protocol ``protocol`       | Use this parameter to specify which protocol is used to connect to the service.                                 |
| `-weight ``weight`           | Optionally, you can specify the weight of the record.                                                           |
| `-priority ``priority`       | Optionally, you can specify a priority of the record, with a value ranging from 0 to 65535.                     |
| `-port ``port_number`        | Optionally, you can specify a port number used to connect to the service, with a value ranging from 0 to 65535. |
| `-instance ``instance_name`  | Optionally, you can specify an instance name for the service.                                                   |
| `-deletesrv ``service_name`  | Use this parameter to specify the name of the service record you want to delete.                                |
| `-createtxt ``name`          | Use this parameter to add a text (TXT) record using the specified name.                                         |
| `-namettl ``name_ttl`        | Optionally, you can specify the time, in seconds, to live for the name.                                         |
| `-deletetxt ``name`          | Use this parameter to delete a text (TXT) record for a specific name.                                           |
| `-createptr ``name`          | Use this parameter to add a pointer (PTR) record for a specific name.                                           |
| `-deleteptr ``name`          | Use this parameter to delete a pointer (PTR) record for a specific name.                                        |

##### Usage Notes

You must be logged in as the `root` user on Linux and UNIX platforms, or as an Administrator user on Windows platforms, to run this command.

##### Example

The following command advertises a name with GNS:

    # srvctl update gns -advertise myname -address 192.168.1.45

#### srvctl add havip

Adds highly available VIPs (HAVIPs) (used for highly available NFS and SMB exports) to a cluster.

##### Syntax

    srvctl add havip -id havip_name -address {host_name | ip_address}
        [-netnum network_number] [-description text] [-skip] [-homenode node_name]

##### Parameters

Table F-55 srvctl add havip Command Parameters

| Parameter                                   | Description                                                                                                                                                                           |
|:--------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-id ``havip_name`                          | Specify a unique ID for the HAVIP resource.                                                                                                                                           |
| `-address {``host_name`` | ``ip_address``}` | Specify either a host name or an IPv4 IP address for the HAVIP you are going to create.<br>Note: You must configure the IPv4 IP address with a non-DHCP, non-round robin DNS address. |
| `-netnum ``network_number`                  | Optionally, you can specify a network resource upon which the HAVIP depends. The default value for this parameter is 1.                                                               |
| `-description ``text`                       | Optionally, you can specify a text description of the HAVIP.                                                                                                                          |
| `-skip`                                     | Optionally, you can specify this parameter to skip the reachability check for the IP address.                                                                                         |
| `-homenode ``node_name`                     | Optionally, you can specify a preferred node or an empty string to clear the home node.                                                                                               |

##### Example

An example of this command is:

    # srvctl add havip -id myhavip -address 192.0.2.1 -netnum 2 -description
        "My HA VIP" -skip -homenode myNode2

#### srvctl config havip

Displays configuration information for a specific highly available VIP (HAVIP) (used for highly available NFS and SMB exports) or all HAVIP resources in a cluster.

##### Syntax

Use the `srvctl config havip` command with the following syntax:

    srvctl config havip [-id havip_name]

##### Parameters

Table F-56 srvctl config havip Command Parameters

| Parameter          | Description                                                                                                                                                                                             |
|:-------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-id ``havip_name` | Specify the unique name of the HAVIP resource you want to display. If you do not specify this parameter, then SRVCTL displays the configuration information for all HAVIPs known to Oracle Clusterware. |

##### Example

This command returns output similar to the following:

    $ srvctl config havip -id hrexports

    VIP: /mjk-vm3-vip/10.149.237.196/10.149.236.0/255.255.252.0/eth0
    Description: HR Exports

#### srvctl disable havip

Prevents a specific highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports) resource from running on a number of specified nodes.

##### Syntax

    srvctl disable havip -id havip_name [-node node1,node2,...,noden]

##### Parameters

Table F-57 srvctl disable havip Command Parameters

| Parameter                               | Description                                                                                                                                                                                                  |
|:----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-id ``havip_name`                      | Specify the unique name of the HAVIP resource you want to disable.                                                                                                                                           |
| `-node ``node1``,``node2``,...,``noden` | Specify the name of a node or a comma-delimited list of node names on which you do not want the HAVIP resource to run.<br>If you specify all but one node in the cluster, then the HAVIP will not fail over. |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Example

An example of this command is:

    # srvctl disable havip -id myhavip -node myNode1,myNode3

#### srvctl enable havip

Enables a specific highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports) to run on a number of specified nodes.

##### Syntax

    srvctl enable havip -id havip_name [-node node_name]

##### Parameters

Table F-58 srvctl enable havip Command Parameters

| Parameter           | Description                                                                        |
|:--------------------|:-----------------------------------------------------------------------------------|
| `-id ``havip_name`  | Specify the unique name of the HAVIP resource you want to enable.                  |
| `-node ``node_name` | Specify the name of a node on which you want the HAVIP resource to be able to run. |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Examples

An example of this command is:

    # srvctl enable havip -id myhavip -node myNode1

#### srvctl modify havip

Modifies a highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports).

##### Syntax

    srvctl modify havip -id havip_name [-address {host_name | ip_address}
        [-netnum network_number] [-skip]] [-description text] [-homenode node_name]

##### Parameters

Table F-59 srvctl modify havip Command Parameters

| Parameter                                | Description                                                                                                                                                                              |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-id ``havip_name`                       | Specify the unique name for the HAVIP resource you want to modify.                                                                                                                       |
| `-address {``host_name`` | ``ip_address` | Specify either a host name or an IPv4 IP or IPv6 address for the HAVIP you want to modify.<br>Note: You must configure the IPv4 IP address with a non-DHCP, non-round robin DNS address. |
| `-netnum ``network_number`               | Optionally, you can change the network resource upon which the HAVIP depends. The default value for this optional parameter is 1.                                                        |
| `-skip`                                  | Specify this parameter to skip checking the reachability of the IP address.                                                                                                              |
| `-description ``text`                    | Specify a text description for the HAVIP.                                                                                                                                                |
| `-homenode ``node_name`                  | Optionally, you can specify a preferred node or an empty string to clear the home node.                                                                                                  |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Example

An example of this command is:

    # srvctl modify havip -id myhavip -address 192.168.16.17 -netnum 2

#### srvctl relocate havip

Relocates a highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports) to another node in a cluster.

##### Syntax

    srvctl relocate havip -id havip_name [-node node_name] [-force]

##### Parameters

Table F-60 srvctl relocate havip Command Parameters

| Parameter           | Description                                                                    |
|:--------------------|:-------------------------------------------------------------------------------|
| `-id ``havip_name`  | Specify the unique name of the HAVIP resource you want to relocate.            |
| `-node ``node_name` | Specify the name of the node to which you want to relocate the HAVIP resource. |
| `-force`            | Optionally, you can force the relocation of the HAVIP resource.                |

##### Example

An example of this command is:

    $ srvctl relocate havip -id myhavip -node node3

#### srvctl remove havip

Removes a highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports).

##### Syntax

    srvctl remove havip -id havip_name [-force]

##### Parameters

Table F-61 srvctl remove havip Command Parameters

| Parameter          | Description                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------|
| `-id ``havip_name` | Specify the unique name of the HAVIP resource you want to remove.                                |
| `–force`           | Use this parameter to forcibly remove the resource from the cluster and ignore any dependencies. |

##### Usage Notes

- You must first stop the HAVIP resource before you attempt to remove it.

- You must run this command as `root` user on Linux and UNIX platforms.

##### Example

An example of this command is:

    # srvctl remove havip -id myhavip -force

#### srvctl start havip

Starts a specific highly-available VIP (HAVIP) (used for highly-available NFS and SMB exports) on a specific node.

##### Syntax

    srvctl start havip -id havip_name [-node node_name]

##### Parameters

Table F-62 srvctl start havip Command Parameters

| Parameter           | Description                                                                                                       |
|:--------------------|:------------------------------------------------------------------------------------------------------------------|
| `-id ``havip_name`  | Specify the unique name of the HAVIP resource you want to start.                                                  |
| `-node ``node_name` | Optionally, you can use the `-node` parameter to specify the name of the node on which the HAVIP resource starts. |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Example

An example of this command is:

    # srvctl start havip -id myhavip -node myNode1

#### srvctl status havip

Displays the status of all highly-available VIPs (HAVIPs) (used for highly-available NFS and SMB exports) in a cluster or one particular HAVIP.

##### Syntax

    srvctl status havip [-id havip_name]

##### Usage Notes

Specify the unique name of the HAVIP resource you want to display. If you do not specify this parameter, then SRVCTL displays the status of all HAVIPs known to Oracle Clusterware.

##### Example

This command returns output similar to the following:

    $ srvctl status havip

    HAVIP ora.ha1.havip is enabled
    HAVIP ora.ha1.havip is not running

#### srvctl stop havip

Stops the highly-available VIPs (HAVIPs) (used for highly-available NFS and SMB exports) on a specific node.

##### Syntax

    srvctl stop havip -id havip_name [-node node_name] [-force]

##### Parameters

Table F-63 srvctl stop havip Command Parameters

| Parameter           | Description                                                                                   |
|:--------------------|:----------------------------------------------------------------------------------------------|
| `-id ``havip_name`  | Specify the unique name of the HAVIP resource to stop.                                        |
| `-node ``node_name` | Optionally, you can specify the name of the node on which the HAVIP resource to stop resides. |
| `–force`            | Use this parameter to forcibly stop the HAVIP.                                                |

##### Usage Notes

You must run this command as `root` user on Linux and UNIX platforms.

##### Examples

An example of this command is:

    # srvctl stop havip -id myhavip -node myNode1 -force

#### srvctl add ioserver

Adds an Oracle ASM IOServer configuration to the cluster.

When you configure, upgrade, or convert from a standard cluster to an Oracle Flex Cluster you can create Oracle ASM IOServers on the Hub nodes in the cluster.

##### Syntax

    srvctl add ioserver [-spfile spfile] [-count number_of_ioserver_instances| ALL] [-listener listener_name]

##### Parameters

Table F-64 srvctl add ioserver Command Parameters

| Parameter                                  | Description                                                                                                 |
|:-------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| `-spfile spfile`                           | Specify the path to the server parameter file.                                                              |
| `-count number_of_ioserver_instances| ALL` | Specify the number of Oracle ASM IOServer instances you want to add or `ALL` to add instances to all nodes. |
| `-listener listener_name`                  | Specify the name of the listener.                                                                           |

##### Example

An example of this command is:

    # srvctl add ioserver -count 2

#### srvctl config ioserver

Displays the configuration details of Oracle ASM IOServers.

##### Syntax

    srvctl config ioserver

##### Usage Notes

This command has no parameters.

##### Example

This command displays output similar to the following:

    $ srvctl config ioserver
    ASM I/O Server instance count: 3
    ASM I/O Server is enabled.
    ASM I/O server is enabled on nodes:
    ASM I/O server is disabled on nodes:

#### srvctl disable ioserver

Disables an Oracle ASM IOServer.

##### Syntax

    srvctl disable ioserver -node node_name

##### Usage Notes

Use the `-node` parameter to specify the name of a Hub node on which you want to disable an Oracle ASM IOServer.

#### srvctl enable ioserver

Enable an Oracle ASM IOServer on a specific node.

##### Syntax

    srvctl enable ioserver [-node node_name]

##### Usage Notes

Use the `-node` parameter to specify the name of a Hub node on which you want to enable an Oracle ASM IOServer.

#### srvctl getenv ioserver

Displays the values for environment variables associated with an Oracle ASM IOServer.

##### Syntax

    srvctl getenv ioserver [-envs "name_list"]

##### Usage Notes

Specify a comma-delimited list of the names of environment variables. If you do not specify this parameter, then SRVCTL displays the values of all environment variables associated with the database.

#### srvctl modify ioserver

Modifies an Oracle ASM IOServer configuration on a cluster.

##### Syntax

    srvctl modify ioserver [-spfile spfile] [-count number_of_ioserver_instances | ALL]
      [-listener listener_name] [-force]

##### Parameters

Table F-65 srvctl modify ioserver Command Parameters

| Parameter                                       | Description                                                                                                                                                                                                                                                 |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-spfile ``spfile`                              | Optionally, specify the path to the server parameter file path.                                                                                                                                                                                             |
| `-count ``number_of_ioserver_instances`` | ALL` | Optionally, specify a number of instances or `ALL` (to modify instances on all nodes) that you want to modify. If you modify the count, then, because this results in a change in cardinality of the cluster resource, the changes take effect immediately. |
| `-listener ``listener_name`                     | Optionally, specify the name of the listener.                                                                                                                                                                                                               |
| `-force`                                        | Optionally, you can ignore any dependencies and force the modification of the Oracle ASM IOServer.                                                                                                                                                          |

#### srvctl relocate ioserver

Relocates an Oracle ASM IOServer instance from its current hosting node to another node within the cluster.

##### Syntax

    srvctl relocate ioserver -currentnode node_name [-targetnode node_name] [-force]

##### Parameters

Table F-66 srvctl relocate ioserver Command Parameters

| Parameter                  | Description                                                                      |
|:---------------------------|:---------------------------------------------------------------------------------|
| `-currentnode ``node_name` | The name of the node on which the Oracle ASM IOServer instance currently resides |
| `-targetnode ``node_name`  | The name of the node to which to relocate the IOServer instance                  |
| `-force`                   | Optionally, you can force the relocation of the Oracle ASM IOServer instance     |

##### Example

The following command relocates the Oracle ASM IOServer from a node called `crsNode2` to a node called `crsNode5`:

    $ srvctl relocate ioserver -currentnode crsNode2 -targetnode crsNode5

#### srvctl remove ioserver

Use this command to remove an Oracle ASM IOServer instance from the cluster.

##### Syntax

    srvctl remove ioserver [-force]

##### Usage Notes

Use the `-force` parameter to forcibly remove the Oracle ASM IOServer instance, ignoring any dependencies.

#### srvctl setenv ioserver

Administers the environment configuration for an Oracle ASM IOServer.

##### Syntax

    srvctl setenv ioserver {-envs "name=val[,name=val][...]" | -env "name=val"}

##### Parameters

Table F-67 srvctl setenv ioserver Command Parameters

| Parameter                      | Description                                                                                                                                                                    |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name``=``val``,..."` | Comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`).                                                                   |
| `-env "``name``=``val"`        | Alternatively, use this parameter to set a single environment variable to a value that contains commas or other special characters, enclosed in double quotation marks (`""`). |

#### srvctl start ioserver

Starts Oracle ASM IOServers in the cluster.

You can also start an Oracle ASM IOServer on a particular Hub Node by specifying the node name.

##### Syntax

    srvctl start ioserver [-node node_name]

##### Usage Notes

If you choose to start an Oracle ASM IOServer on a particular Hub Node, then use the `-node` parameter and specify the name of the node. If you do not specify a particular Hub Node, then SRVCTL starts all Oracle ASM IOServers in the cluster.

##### Example

The following command starts an Oracle ASM IOServer on a Hub node named `mjkhub46`:

    $ srvctl start ioserver -node mjkhub46

#### srvctl status ioserver

Displays the status of Oracle ASM IOServers running in the cluster.

You can display the status of all Oracle ASM IOServers running a cluster, the status of an Oracle ASM IOServer running on a particular Hub Node, or the information about clients from a specific database.

##### Syntax

    srvctl status ioserver [-node node_name] [-detail]

##### Parameters

Table F-68 srvctl status ioserver Parameters

| Parameter           | Description                                                                                                                                                                                                                                            |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `—node ``node_name` | Specify a particular Hub node to display the status of the Oracle ASM IOServer resource instance running there. If you do not specify a Hub node, then SRVCTL returns the status of all Oracle ASM IOServer resource instances running in the cluster. |
| `-detail`           | Use this parameter to display more detailed information about the status of the Oracle ASM IOServer.                                                                                                                                                   |

##### Example

If you run the command with the `-detail` parameter, then SRVCTL displays output similar to the following:

    $ srvctl status ioserver -detail
    ASM I/O Server is enabled
    ASM I/O Server is running on nodes: mjk376, mjk377

    ASM I/O Server instance +IOS1 running on node mjk376 is connected to ASM instance +ASM2:
    Number of clients connected: 2
    Names of clients: later14, alus16, later12, alus9, db0010

    ASM I/O Server instance +IOS2 running on node mjk377 is connected to ASM instance +ASM3:
    Number of clients connected: 3
    Number of requests completed per sec: 110
    Names of networks: eth1, eth2
    Names of clients: later11, later3, later14, later15, later16, alus19, alus17, alus13

#### srvctl stop ioserver

Stops an Oracle ASM IOServer in the cluster.

##### Syntax

    srvctl stop ioserver [-node node_name] [-force]

##### Usage Notes

- Use the `-node` parameter to stop an Oracle ASM IOServer on a particular Hub Node. If you do not specify a particular Hub Node, then SRVCTL stops all of the Oracle ASM IOServers in the cluster.

- Use the `-force` parameter to stop an Oracle ASM IOServer, regardless of any dependencies.

#### srvctl unsetenv ioserver

Unsets the Oracle ASM IOServer environment configurations.

##### Syntax

    srvctl unsetenv ioserver -envs "name_list"

##### Usage Notes

Use the `-envs` parameter to specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).

#### srvctl add mgmtdb

Adds a management database (CHM repository) resource to the cluster.

##### Syntax

    srvctl add mgmtdb [-domain domain]

##### Usage Notes

Optionally, you can specify the domain for the database. If you have the `DB_DOMAIN` database initialization parameter set, then you must provide a value for this parameter.

##### Example

To add a management database to the cluster:

    $ srvctl add mgmtdb -domain example.com

#### srvctl config mgmtdb

Displays configuration information for the management database (CHM repository) resource.

**Note:**

Use this command only with Oracle Clusterware.

##### Syntax

    srvctl config mgmtdb [-verbose] [-all]

##### Usage Notes

- Optionally, use the `-verbose` parameter to print detailed output.

- Optionally, use the `-all` parameter to print detailed configuration information.

#### srvctl disable mgmtdb

Disables the management database (CHM repository) resource on the specified node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable mgmtdb [-node node_name]

##### Usage Notes

Optionally, you can specify the name of a cluster node on which the management database you want to disable is running.

##### Example

An example of this command is:

    $ srvctl disable mgmtdb

#### srvctl enable mgmtdb

Enables a management database (CHM repository) resource.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl enable mgmtdb [-node node_name]

##### Usage Notes

Optionally, you can specify the name of a cluster node on which you want to enable a management database resource.

##### Example

To enable a management database on the node named `node5`, use the following command:

    $ srvctl enable mgmtdb -node node5

#### srvctl getenv mgmtdb

Gets the environment variables for the management database (CHM repository).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl getenv mgmtdb [-envs "name_list"]

##### Usage Notes

Specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`). If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the listener.

##### Example

The following example lists all environment variables specified for the management database:

    $ srvctl getenv mgmtdb

#### srvctl modify mgmtdb

Modifies the configuration for the management database (CHM repository).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl modify mgmtdb [-pwfile password_file_path] [-spfile spfile_path]
      [-startoption start_option] [-stopoption stop_option] [-diskgroup "diskgroup_list"]

##### Parameters

Table F-69 srvctl modify mgmtdb Command Parameters

| Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-pwfile ``password_file_path`    | Modify the full path to the location of the password file for the management database.                                                                                                                                                                                                                                                                                                                      |
| `-spfile ``spfile_path`           | Modify the path name of the new spfile to be used by the management database.                                                                                                                                                                                                                                                                                                                               |
| `-startoption ``start_option`     | Modify the startup options for the management database, such as `OPEN`, `MOUNT`, or `NOMOUNT`.<br>Note: For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/STARTUP.md) for more information about startup options |
| `-stopoption ``stop_option`       | Modify the stop options for the management database, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, or `ABORT`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/SHUTDOWN.md) for more information about shutdown options                                                                                                                                                                      |
| `-diskgroup "``diskgroup_list``"` | Modify a comma-delimited list of Oracle ASM disk groups used by the management database, enclosed in double quotation marks (`""`).                                                                                                                                                                                                                                                                         |

##### Example

The following example directs the management database to use the `SYSFILES` Oracle ASM disk group:

    $ srvctl modify mgmtdb -diskgroup "SYSFILES"

#### srvctl relocate mgmtdb

Relocates the management database (CHM repository) resource from one node of the cluster to another.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl relocate mgmtdb [-node node_name]

##### Usage Notes

Specify a node to which you want to relocate the management database.

##### Example

An example of this command is:

    $ srvctl relocate mgmtdb -node crsNode2

#### srvctl remove mgmtdb

Removes the management database (CHM repository) from Oracle Clusterware management.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove mgmtdb [-force] [-noprompt] [-verbose]

##### Parameters

Table F-70 srvctl remove mgmtdb Command Parameters

| Parameter   | Description                                                                                                                                   |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `-force`    | Optionally, you can use this parameter to forcibly remove the management database from the cluster regardless of any errors that might occur. |
| `-noprompt` | Optionally, you can use this parameter to suppress prompts.                                                                                   |
| `-verbose`  | Optionally, you can use this parameter to display verbose output.                                                                             |

##### Usage Notes

You must first shut down the management database before you attempt to remove it.

##### Example

An example of this command is:

    $ srvctl remove mgmtdb -noprompt

#### srvctl setenv mgmtdb

Administers the environment configuration for the management database (CHM repository).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

Use this command with one of these syntax models:

    srvctl setenv mgmtdb -envs "name=val[,...]"

    srvctl setenv mgmtdb -env "name=val"

##### Parameters

Table F-71 srvctl setenv mgmtdb Command Parameters

| Parameter                        | Description                                                                                                                                                                 |
|:---------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name``=``val``[,...]"` | Specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`).                                                      |
| `-env "``name``=``val``"`        | Use this parameter to enable a single environment variable to be set to a value that contains commas or other special characters enclosed in double quotation marks (`""`). |

##### Example

The following example sets the language environment configuration for the management database:

    $ srvctl setenv mgmtdb -env LANG=en

#### srvctl start mgmtdb

Starts the management database (CHM repository) resource.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start mgmtdb [-startoption start_options] [-node node_name]

##### Parameters

Table F-72 srvctl start mgmtdb Command Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-startoption ``start_options` | Optionally, you can specify options to the startup command, such as `OPEN`, `MOUNT`, or `NOMOUNT`.<br>Note: For multi-word startup options, such as `read only` and `read write`, separate the words with a space and enclose in double quotation marks (`""`). For example, `"read only"`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/STARTUP.md) for more information about startup options |
| `-node ``node_name`            | Optionally, you can specify a particular node on which to start a management database resource.<br>Note: This parameter can be used only with Oracle Clusterware.                                                                                                                                                                                                                                               |

##### Example

An example of this command to start the management database on the `crmnode1` node of the cluster is:

    $ srvctl start mgmtdb -node crmnode1

#### srvctl status mgmtdb

Displays the current state of the management database (CHM repository) resource.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status mgmtdb [-verbose]

##### Usage Notes

Optionally, you can use the `-verbose` parameter to display detailed output.

##### Example

An example of this command to check the status of the management database is:

    $ srvctl status mgmtdb

#### srvctl stop mgmtdb

Stops the management database (CHM repository) resource.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop mgmtdb [-stopoption stop_options] [-force]

##### Parameters

Table F-73 srvctl stop mgmtdb Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-stopoption ``stop_options` | Optionally, you can use this parameter to specify `shutdown` command options, such as `NORMAL`, `TRANSACTIONAL`, `IMMEDIATE`, or `ABORT`.<br>See Also: [SQL\*Plus User's Guide and Reference](../sqpug/SHUTDOWN.md) for more information about shutdown options |
| `-force`                     | Use this parameter to forcibly stop the database and any associated services and any dependent resources.                                                                                                                                                       |

##### Example

An example of this command is:

    $ srvctl stop mgmtdb -stopoption NORMAL

#### srvctl unsetenv mgmtdb

Unsets the management database (CHM repository) environment configurations.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl unsetenv mgmtdb -envs "name_list"

##### Usage Notes

Use the `-envs` parameter to specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).

##### Example

The following example unsets the environment configuration for a management database environment variable:

    $ srvctl unsetenv mgmtdb -envs "LANG"

#### srvctl add mgmtlsnr

Adds a management listener resource (for Cluster Health Monitor) to the cluster.

##### Syntax

    srvctl add mgmtlsnr [-endpoints "[TCP:]port_list[/IPC:key][/NMP:pipe_name
      [/TCPS:s_port][/SDP:port][/EXADIRECT:port]"] [-skip]]

##### Parameters

Table F-74 srvctl add mgmtlsnr Command Parameters

| Parameter                                                                                                        | Description                                                                                                        |
|:-----------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| `-endpoints "[TCP:]port_list`<br>` [/IPC:key][/NMP:pipe_name`<br>` [/TCPS:s_port][/SDP:port][/EXADIRECT:port]"]` | Protocol specifications for the listener. `port_list` is a comma-delimited list of TCP ports or listener endpoints |
| `-skip`                                                                                                          | Indicates you want to skip the checking of ports.                                                                  |

##### Example

The following command adds a management listener that is listening on port 1341 to the cluster:

    $ srvctl add mgmtlsnr -endpoints "TCP:1341"

#### srvctl config mgmtlsnr

Displays configuration information for the management listener resource (for CHM).

**Note:**

Use this command only with Oracle Clusterware.

##### Syntax

    srvctl config mgmtlsnr [-all]

##### Usage Notes

Use the `-all` parameter to print detailed configuration information.

#### srvctl disable mgmtlsnr

Disables the management listener resource (for CHM) on the specified node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable mgmtlsnr [-node node_name]

##### Usage Notes

Optionally, you can specify the name of a cluster node on which the management listener you want to disable is running.

##### Example

An example of this command is:

    $ srvctl disable mgmtlsnr

#### srvctl enable mgmtlsnr

Enables a management database listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl enable mgmtlsnr [-node node_name]

##### Usage Notes

Optionally, you can specify the name of a cluster node on which you want to enable a management listener.

##### Example

To enable a management listener on a node named `node5`, use the following command:

    $ srvctl enable mgmtlsnr -node node5

#### srvctl getenv mgmtlsnr

Gets the environment variables for the management listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl getenv mgmtlsnr [-envs "name_list"]

##### Usage Notes

Optionally, you can specify a comma-delimited list of environment variable names. If you do not use this parameter, then SRVCTL displays the values of all environment variables associated with the listener.

##### Example

The following example lists all environment variables specified for the management listener:

    $ srvctl getenv mgmtlsnr

#### srvctl modify mgmtlsnr

Modifies the configuration for the management listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl modify mgmtlsnr [-endpoints "[TCP:]port_list[/IPC:key][/NMP:pipe_name]
       [/TCPS:s_port][/SDP:port]"]

##### Usage Notes

Optionally, you can specify protocol specifications for the management listener. `port_list` is comma-delimited list of port numbers. You can also modify this attribute using Online Resource Attribute Modification.

##### Example

The following example changes the TCP ports for the management listener:

    $ srvctl modify mgmtlsnr -endpoints "TCP:2521,2522"

#### srvctl remove mgmtlsnr

Removes the management listener resource (for CHM) from Oracle Clusterware.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove mgmtlsnr [-force]

##### Usage Notes

Use the `-force` parameter to forcibly remove the management listener, ignoring any dependencies.

##### Example

An example of this command is:

    $ srvctl remove mgmtlsnr

#### srvctl setenv mgmtlsnr

Administers the environment configuration for the management listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

Use this command with one of the following syntax models:

    srvctl setenv mgmtlsnr -envs "name=val[,...]"

    srvctl setenv mgmtlsnr -env "name=val"

##### Parameters

Table F-75 srvctl setenv mgmtlsnr Command Parameters

| Parameter                        | Description                                                                                                                                                                 |
|:---------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-envs "``name``=``val``[,...]"` | Specify a comma-delimited list of name-value pairs of environment variables enclosed in double quotation marks (`""`) that you want to set.                                 |
| `-env "``name``=``val``"`        | Use this parameter to enable a single environment variable to be set to a value that contains commas or other special characters enclosed in double quotation marks (`""`). |

##### Example

The following example sets the language environment configuration for the management listener:

    $ srvctl setenv mgmtlsnr -env LANG=en

#### srvctl start mgmtlsnr

Starts the management listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start mgmtlsnr [-node node_name]

##### Usage Notes

Specify the node on which you want to start the management listener.

##### Example

To start the management listener on the `crmnode1` node:

    $ srvctl start mgmtlsnr -node crmnode1

#### srvctl status mgmtlsnr

Displays the status of the management listener resource (for CHM).

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status mgmtlsnr [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify the name of a cluster node.

- Optionally, use the `-verbose` parameter to display detailed output.

##### Examples

To display the status of the management listener on the node `node2`, use the following command:

    $ srvctl status mgmtlsnr -node node2

#### srvctl stop mgmtlsnr

Stops the management listener resource (for CHM) on all nodes or the specified node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop mgmtlsnr [-node node_name] [-force]

##### Usage Notes

- Optionally, you can specify the name of a single node on which the management listener runs.

- Optionally, you can use the `-force` parameter to forcibly stop the management listener.

##### Example

The following command stops the management listener on the node `mynode1`:

    $ srvctl stop mgmtlsnr -node mynode1

#### srvctl unsetenv mgmtlsnr

Unsets the management listener resource (for CHM) environment configurations.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl unsetenv mgmtlsnr -envs "name_list"

##### Usage Notes

Use the `-envs` parameter to specify a comma-delimited list of the names of environment variables enclosed in double quotation marks (`""`).

##### Example

The following example unsets the environment configuration for a management listener environment variable:

    $ srvctl unsetenv mgmtlsnr -envs "LANG"

#### srvctl add mountfs

Adds Network Attached Storage (NAS) configuration to Oracle Clusterware.

**Note:**

Use this command only with Oracle Clusterware.

##### Syntax

    srvctl add mountfs -name mountfs_name -path mount_path -exportserver server_name
       -exportpath path [-mountoptions mount_options] [-user user]

##### Parameters

Table F-76 srvctl add mountfs Command Parameters

| Parameter                       | Description                                                                  |
|:--------------------------------|:-----------------------------------------------------------------------------|
| `-name ``mountfs_name`          | Specify a unique name for the NAS.                                           |
| `-path ``mount_path`            | Specify a mount path for the NAS.                                            |
| `-exportserver ``server_name`   | Specify a name for the export server.                                        |
| `-exportpath ``path`            | Specify an export file path.                                                 |
| `-mountoptions ``mount_options` | Optionally, you can specify mount options for the NAS.                       |
| `-user ``user`                  | Optionally, you can specify a user authorized to mount and dismount the NAS. |

#### srvctl config mountfs

Displays the configuration information for a specific NAS.

**Note:**

Use this command only with Oracle Clusterware.

##### Syntax

    srvctl config mountfs [-name mountfs_name]

##### Usage Notes

Specify the unique name of the NAS for which you want to display configuration information.

#### srvctl disable mountfs

Disables the specified NAS from Oracle Clusterware management.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable mountfs -name mountfs_name [-node node_list]

##### Parameters

Table F-77 srvctl disable mountfs Command Parameters

| Parameter              | Description                                                                          |
|:-----------------------|:-------------------------------------------------------------------------------------|
| `-name ``mountfs_name` | Specify the unique name for the NAS you want to disable.                             |
| `-node ``node_list`    | Optionally, you can specify a comma-delimited list of nodes on which to disable NAS. |

#### srvctl enable mountfs

Enables the specified Network Attached Storage (NAS) for Oracle Clusterware management.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl enable mountfs -name mountfs_name [-node node_list]

##### Parameters

Table F-78 srvctl enable mountfs Command Parameters

| Parameter              | Description                                                                         |
|:-----------------------|:------------------------------------------------------------------------------------|
| `-name ``mountfs_name` | Specify the unique name for the NAS you want to enable.                             |
| `-node ``node_list`    | Optionally, you can specify a comma-delimited list of nodes on which to enable NAS. |

#### srvctl modify mountfs

Modifies Network Attached Storage (NAS) configuration in Oracle Clusterware.

**Note:**

This command is available only with Oracle Clusterware.

##### Syntax

    srvctl modify mountfs -name mountfs_name [-path mount_path] [-exportserver server_name]
       [-exportpath path] [-mountoptions mount_options] [-user user_name]

##### Parameters

Table F-79 srvctl modify mountfs Command Parameters

| Parameter                       | Description                                               |
|:--------------------------------|:----------------------------------------------------------|
| `-name ``mountfs_name`          | Specify a unique name for the NAS you want to modify.     |
| `-path ``mount_path`            | Modify the mount path for the NAS.                        |
| `-exportserver ``server_name`   | Modify the name of the export server.                     |
| `-exportpath ``path`            | Modify the export file path.                              |
| `-mountoptions ``mount_options` | Modify mount options for the NAS.                         |
| `-user ``user_name`             | Modify the user authorized to mount and dismount the NAS. |

#### srvctl remove mountfs

Removes a specific NAS configuration.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove mountfs -name mountfs_name [-force]

##### Usage Notes

- Specify the unique name for the NAS to mount.

- Optionally, you can use the `-force` parameter to ignore resource dependencies while removing the NAS.

#### srvctl start mountfs

Mounts a specific NAS.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start mountfs -name mountfs_name [-node node_list]

##### Parameters

Table F-80 srvctl start mountfs Command Parameters

| Parameter              | Description                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------|
| `-name ``mountfs_name` | Specify the unique name for the NAS to mount.                                      |
| `-node ``node_list`    | Optionally, you can specify a comma-delimited list of nodes on which to mount NAS. |

#### srvctl status mountfs

Displays the current state of a specific NAS.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status mountfs -name mountfs_name

##### Usage Notes

Specify the unique name of the NAS for which you want to display the status.

#### srvctl stop mountfs

Unmounts a specific NAS.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop mountfs -name mountfs_name [-node node_list] [-force]

##### Parameters

Table F-81 srvctl stop mountfs Command Parameters

| Parameter              | Description                                                                                        |
|:-----------------------|:---------------------------------------------------------------------------------------------------|
| `-name ``mountfs_name` | Specify the unique name for the NAS to unmount.                                                    |
| `-node ``node_list`    | Optionally, you can specify a comma-delimited list of nodes from which to unmount NAS.             |
| `-force`               | Optionally, you can use the `-force` parameter to ignore resource dependencies while stopping NAS. |

#### srvctl add ovmm

Adds manager credentials to the credentials store for managing a virtual machine.

##### Syntax

    srvctl add ovmm -wallet certificate_wallet_file -username user_name -ovmmhost host_name | ip_address
      -ovmmport port_number [-autologin]

##### Parameters

Table F-82 srvctl add ovmm Command Parameters

| Parameter                                | Description                                                                                                                                                                                                                  |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-wallet ``certificate_wallet_file`      | Specify the path to the certification wallet that contains the CA certificate used by the virtual machine manager.                                                                                                           |
| `-autologin`                             | Optionally, you can include this parameter to indicate automatic login for the wallet credentials. If you choose not to specify this parameter, then the user will always be prompted to provide the password of the wallet. |
| `-username ``user_name`                  | Specify a user name for whom you want to add manager credentials. You must provide a manager password when prompted.                                                                                                         |
| `-ovmmhost ``host_name`` | ``ip_address` | Specify the host name or the IP address of the host designated as the virtual machine manager.                                                                                                                               |
| `-ovmmport ``port_number`                | Specify the port number used by the virtual machine manager.                                                                                                                                                                 |

##### Usage Notes

You must run this command as `root` or equivalent user.

##### Example

An example of this command is:

    # srvctl add ovmm -username scott -wallet /tmp/ovmmcred/cwallet.sso -ovmmhost node1 -ovmmport 80

#### srvctl config ovmm

Lists the current configuration of the virtual machine manager.

##### Syntax

    srvctl config ovmm

##### Usage Notes

This command takes no parameters.

##### Example

This command returns output similar to the following:

    $ srvctl config ovmm

    OVMM Host: host1
    OVMM Port: 80

#### srvctl modify ovmm

Modifies the virtual machine manager configuration.

##### Syntax

    srvctl modify ovmm [-wallet certificate_wallet_file [-autologin]] [-username user_name]
       [-ovmmhost host_name | ip_address [-ovmmport port_number]

##### Parameters

Table F-83 srvctl modify ovmm Command Parameters

| Parameter                           | Description                                                                                                                                                                                                                  |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-wallet ``certificate_wallet_file` | Specify the path to the certification wallet that contains the CA certificate used by the virtual machine manager.                                                                                                           |
| `-autologin`                        | Optionally, you can include this parameter to indicate automatic login for the wallet credentials. If you choose not to specify this parameter, then the user will always be prompted to provide the password of the wallet. |
| `-username ``user_name`             | Specify a user name for whom you want to add manager credentials. You must provide a manager password when prompted.                                                                                                         |
| `-ovmmhost ``host_ip`               | Specify the host name or the IP address of the host designated as the virtual machine manager.                                                                                                                               |
| `-ovmmport ``port_number`           | Specify the port number used by the virtual machine manager.                                                                                                                                                                 |

##### Usage Notes

- You must run this command as `root` or equivalent user.

- The `srvctl modify ovmm` command deletes all credentials before writing new ones.

##### Example

An example of this command is:

    $ srvctl modify ovmm -username scott -ovmport 81

#### srvctl remove ovmm

Removes the current configuration of the virtual machine manager.

##### Syntax

    srvctl remove ovmm

##### Usage Notes

- You must run this command as `root` or equivalent user.

- This command takes no parameters.

##### Example

An example of this command is:

    # srvctl remove ovmm

#### srvctl add qosmserver

Adds an Oracle Database QoS Management Server instance to all the nodes in the cluster.

##### Syntax

    srvctl add qosmserver [-verbose]

##### Usage Notes

Optionally, you can use the `-verbose` parameter to display verbose output.

##### Example

The following command adds an Oracle Database QoS Management Server instance:

    $ srvctl add qosmserver

#### srvctl config qosmserver

Displays configuration information for the `qosmserver` resource.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl config qosmserver

##### Parameters

This command has no parameters.

##### Example

The following command displays the configuration information for the `qosmserver` resource.

    $ srvctl config qosmserver

#### srvctl disable qosmserver

Disables the Oracle Database QoS Management Server instance on all nodes or on a specific node.

##### Syntax

    srvctl disable qosmserver [-node node_name] [-verbose]

##### Usage Notes

With this command you can optionally specify a particular node on which to disable an Oracle Database QoS Management Server instance, and you can also choose verbose output.

##### Example

The following example disables the Oracle Database QoS Management Server on a node called `crsNode3`:

    $ srvctl disable qosmserver -node crsNode3

#### srvctl enable qosmserver

Enables an Oracle Database QoS Management Server instance on all nodes or on a specific node.

##### Syntax

    srvctl enable qosmserver [-node node_name] [-verbose]

##### Usage Notes

With this command you can optionally specify a particular node on which to enable an Oracle Database QoS Management Server instance, and you can also choose verbose output.

##### Example

The following command example enables an Oracle Database QoS Management Server instance on a node named `crsNode3`:

    $ srvctl enable qosmserver -node crsNode3

#### srvctl modify qosmserver

Modifies the RMI port for the Oracle Database QoS Management Server instances.

##### Syntax

    srvctl modify qosmserver
    [-rmiport qosmserver_rmi_port]
    [-httpport qosmserver_http_port]
    [-secure '{YES|NO}']
    [-enableHTTPS '{YES|NO}']
    [-verbose]
    [-force]

Table F-84 srvctl modify qosmserver Command Parameters

| Parameter                          | Description                                                                                                                                                                                   |
|:-----------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-rmiport ``qosmserver_rmi_port`   | Specify the QoS Management RMI port number that the Oracle Database QoS Management Server instance uses.<br>Note: You can modify this attribute using Online Resource Attribute Modification. |
| `-httpport ``qosmserver_http_port` | Specify the HTTP port number.                                                                                                                                                                 |
| `-secure {YES|NO}`                 | Specify whether to enable QoS Management Server security.                                                                                                                                     |
| `-enableHTTPS {YES|NO}`            | Specify whether to enable QoS Management Server Transport Layer Security.                                                                                                                     |
| `-force`                           | Stops and restarts the resource to affect a change                                                                                                                                            |
| `-verbose`                         | Verbose output                                                                                                                                                                                |

##### Example

The following command example sets the QoS Management RMI port number to 5385:

    $ srvctl modify qosmserver -rmiport 5385

#### srvctl predict qosmserver

The `srvctl predict qosmserver` command predicts the consequences of Oracle Database QoS Management Server failure.

##### Syntax

    srvctl predict qosmserver [-verbose]

This command has only one optional parameter to display verbose output.

##### Example

This command returns output similar to the following:

    $ srvctl predict qosmserver

    Resource ora.qosmserver will be started on node crsNodel

#### srvctl relocate qosmserver

Relocates an Oracle Database QoS Management Server instance from its current hosting node to another node within the cluster.

##### Syntax

    srvctl relocate qosmserver [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify a particular node to which you want to relocate an Oracle Database QoS Management Server instance.

- Optionally, you can use the `-verbose` parameter to display verbose output.

##### Example

The following command example relocates the Oracle Database QoS Management Server instance to node `crsNode1` and displays verbose output:

    $ srvctl relocate qosmserver -node crsNode1 -verbose

#### srvctl remove qosmserver

Removes the Oracle Database QoS Management Server instance from the Oracle Clusterware configuration.

##### Syntax

    srvctl remove qosmserver [-force] [-verbose]

##### Usage Notes

Optionally, you can use the `-force` and `-verbose` parameters that force the removal of the Oracle Database QoS Management Server instance and display verbose output, respectively.

##### Example

The following command forcibly removes the Oracle Database QoS Management Server instance:

    $ srvctl remove qosmserver -force

#### srvctl start qosmserver

Starts an Oracle Database QoS Management Server instance.

##### Syntax

    srvctl start qosmserver [-node node_name] [-verbose]

##### Usage Notes

- Optionally, you can specify a particular node on which to start an Oracle Database QoS Management Server instance.

- Optionally, you can use the `-verbose` parameter to display verbose output.

##### Example

The following command example starts an Oracle Database QoS Management Server instance on a node called `crsNode1`:

    $ srvctl start qosmserver -node crsNode1

#### srvctl status qosmserver

Determines which node is running the Oracle Database QoS Management Server instance.

##### Syntax

    srvctl status qosmserver [-node node_name] [-verbose]

You can optionally specify a particular about which you can obtain the status of the Oracle Database QoS Management Server instance, and you can also use the `-verbose` parameter to display verbose output.

##### Example

This command returns output similar to the following:

    $ srvctl status qosmserver

    QoS Management Server is enabled.
    QoS Management Server is running on node crsNode1.

#### srvctl stop qosmserver

Stops an Oracle Database QoS Management Server instance.

##### Syntax

    srvctl stop qosmserver [-force] [-verbose]

##### Usage Notes

- Optionally, you can specify a particular node on which to stop an Oracle Database QoS Management Server instance.

- Optionally, you can use the `-verbose` parameter to display verbose output.

##### Example

The following command example forcibly stops an Oracle Database QoS Management Server instance:

    $ srvctl stop qosmserver -force

#### srvctl add rhpclient

Adds a Fleet Patching and Provisioning Client configuration file to the Oracle Clusterware configuration.

##### Syntax

    srvctl add rhpclient -clientdata path_to_file [-diskgroup disk_group_name -storage base_path]
      [-email email_address -mailserver mail_server_address -mailserverport mail_server_port] [-verbose]

##### Parameters

Table F-85 srvctl add rhpclient Command Parameters

| Parameter                            | Description                                                                                                                                                                             |
|:-------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-clientdata ``path_to_file`         | Specify the path to the file that contains the Fleet Patching and Provisioning Client data.                                                                                             |
| `-diskgroup ``disk_group_name`       | Specify the Oracle ASM disk group from which to create the Oracle ACFS file system for image storage.                                                                                   |
| `-storage ``base_path`               | Specify a location that is available on all cluster nodes and that is used for mounting an Oracle ACFS that you create for image storage on the Fleet Patching and Provisioning Client. |
| `-email ``email_address`             | Specify an email address.                                                                                                                                                               |
| `-mailserver ``mail_server_address`  | Specify the mail server address.                                                                                                                                                        |
| `-mailserverport ``mail_server_port` | Specify the mail server port number.                                                                                                                                                    |
| `–verbose`                           | Displays verbose output.                                                                                                                                                                |

##### Usage Notes

- You cannot run this command on a Fleet Patching and Provisioning Server.

- You must run this command as `root` user on Linux and UNIX platforms.

- This command does not create an Oracle Clusterware resource.

- To store working copies in `RHP_MANAGED_STORAGE` on the client, you must specify the `-diskgroup` and `-storage` parameters with this command (or with ). An additional benefit of using these options applies to multi-node client clusters. When the Fleet Patching and Provisioning Server provisions a working copy to the client cluster, the image is transferred to one node, and the client distributes it, internally, to remaining nodes.

##### Example

The following command creates a Fleet Patching and Provisioning Client:

    # srvctl add rhpclient -clientdata /tmp/gnsdata

#### srvctl config rhpclient

Displays configuration information for a Fleet Patching and Provisioning Client instance.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl config rhpclient

##### Example

This command returns output similar to the following:

    $ srvctl config rhpclient

    Fleet Patching and Provisioning Client is configured
    Cluster name: mjk9394
    Storage base path: /scratch/aime/storage
    Disk group: MJKRHPCDG
    Fleet Patching and Provisioning Server (RHPS): mjk8990clust
    Fleet Patching and Provisioning Server discovery string: 198.51.100.191
    Port number: 8896
    Fleet Patching and Provisioning Client is enabled
    Fleet Patching and Provisioning Client is individually enabled on nodes:
    Fleet Patching and Provisioning Client is individually disabled on nodes:

#### srvctl disable rhpclient

Disables a Fleet Patching and Provisioning Client instance on a specific node from Oracle Clusterware management.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable rhpclient [-node node_name]

##### Usage Notes

Optionally, you can specify a particular node on which to disable a Fleet Patching and Provisioning Client.

##### Example

An example of this command is:

    $ srvctl disable rhpclient -node clusterNode01

#### srvctl enable rhpclient

Enables a Fleet Patching and Provisioning Client instance on a specific node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl enable rhpclient [-node node_name]

##### Usage Notes

Optionally, you can specify the node on which you want to enable the Fleet Patching and Provisioning Client instance. If you do not specify a node, then SRVCTL enables all of the Fleet Patching and Provisioning Clients in the Oracle Clusterware configuration.

##### Example

An example of this command is:

    $ srvctl enable rhpclient -node clusterNode03

#### srvctl modify rhpclient

Changes the locations of the client data and image storage for the Fleet Patching and Provisioning Client.

##### Syntax

    srvctl modify rhpclient [-clientdata path_to_client_data] [-port rmi_port] [-diskgroup dg_name -storage base_path] [-email email_address -mailserver mail_server_address
       -mailserverport mail_server_port]

##### Parameters

Table F-86 srvctl modify rhpclient Command Parameters

| Parameter                            | Description                                                                                                                                                                                                                                                                      |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-clientdata ``path_to_client_data`  | Modify the path to the Fleet Patching and Provisioning Client data.                                                                                                                                                                                                              |
| `-port ``rmi_port`                   | Modify the RMI port number used by the Fleet Patching and Provisioning Client.                                                                                                                                                                                                   |
| `-diskgroup ``dg_name`               | Modify the Oracle ASM disk group from which to create the Oracle ACFS file systems for image storage.                                                                                                                                                                            |
| `-storage ``base_path`               | Modify the location which is available on every cluster node but is not necessarily shared. It is not required that this location exist when you add a Fleet Patching and Provisioning Client. All images are mounted on `base_path``/images` for all local Oracle ACFS storage. |
| `-email ``email_address`             | Modify an email address.                                                                                                                                                                                                                                                         |
| `-mailserver ``mail_server_address`  | Modify the mail server address.                                                                                                                                                                                                                                                  |
| `-mailserverport ``mail_server_port` | Modify the mail server port number.                                                                                                                                                                                                                                              |

##### Usage Notes

- You must run this command as the `root` user on Linux and UNIX platforms.

- You run this command only on Fleet Patching and Provisioning Clients.

- After running this command, you must run `srvctl stop rhpclient` and `srvctl start rhpclient` on the Fleet Patching and Provisioning Client, so that it communicates the changes to the Fleet Patching and Provisioning Server.

#### srvctl relocate rhpclient

Relocates a Fleet Patching and Provisioning Client instance to a different node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl relocate rhpclient -node node_name

##### Usage Notes

Specify a node to which you want to relocate the Fleet Patching and Provisioning Client instance.

##### Example

An example of this command is:

    $ srvctl relocate rhpclient -node crsNode03

#### srvctl remove rhpclient

Removes a Fleet Patching and Provisioning Client instance.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl remove rhpclient [-force]

##### Usage Notes

Optionally, you can use the `-force` parameter to forcibly remove the Fleet Patching and Provisioning Client instance, ignoring any dependencies.

#### srvctl start rhpclient

Start a Fleet Patching and Provisioning Client instance on one or more nodes.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start rhpclient [-node node_name]

##### Usage Notes

Specify the node on which you want to start the Fleet Patching and Provisioning Client instance. If you do not specify a node, then Oracle Clusterware determines the node where the Fleet Patching and Provisioning Client is to be started. The Fleet Patching and Provisioning Client resource has cardinality of 1 and Oracle Clusterware decides the placement when the Fleet Patching and Provisioning Client resource is started.

##### Example

An example of this command to start the Fleet Patching and Provisioning Server on the node named `crs3`:

    $ srvctl start rhpclient -node crs3

#### srvctl status rhpclient

Displays the current state of a Fleet Patching and Provisioning Client instance.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status rhpclient

##### Usage Notes

This command does not accept any parameters except for `-help`.

##### Example

This command displays output similar to the following:

    $ srvctl status rhpclient

    Fleet Patching and Provisioning Client is enabled
    Fleet Patching and Provisioning Client is running on node mjk1270093

#### srvctl stop rhpclient

Stops a Fleet Patching and Provisioning Client instance that is in a running or starting state.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop rhpclient

##### Usage Notes

This command does not accept any parameter, except for `-help`.

#### srvctl add rhpserver

Adds a Fleet Patching and Provisioning Server to the Oracle Clusterware configuration.

##### Syntax

    srvctl add rhpserver -storage base_path -diskgroup disk_group_name
      [-email email_address -mailserver mail_server_address -mailserverport mail_server_port]
      [-pl_port RHP_progress_listener_port] [-clport RHP_copy_listener_port]
      [-enableTLS {YES|NO}] [-enableHTTPS '{YES|NO}'] [-port_range low_val-high_val] [-usegnsvip]

##### Parameters

Table F-87 srvctl add rhpserver Command Parameters

| Parameter                               | Description                                                                                                                                                                                                                          |
|:----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-storage ``base_path`                  | Specify a location that is available on all cluster nodes. It is not necessary that this location be shared. The catalog for the server is kept in this location and all the image file systems are mounted on `base_path``/images`. |
| `-diskgroup ``disk_group_name`          | Specify a particular Oracle ASM disk group from which to create the Oracle ACFS file system for storing images.                                                                                                                      |
| `-email ``email_address`                | Specify an email address.                                                                                                                                                                                                            |
| `-mailserver ``mail_server_address`     | Specify the mail server address.                                                                                                                                                                                                     |
| `-mailserverport ``mail_server_port`    | Specify the mail server port number.                                                                                                                                                                                                 |
| `-pl_port ``RHP_progress_listener_port` | Specify the Fleet Patching and Provisioning progress listener port number.                                                                                                                                                           |
| `-clport ``RHP_copy_listener_port`      | Specify the Fleet Patching and Provisioning copy listener port number.                                                                                                                                                               |
| `-enableTLS {YES|NO}`                   | Enable Fleet Patching and Provisioning transport level security                                                                                                                                                                      |
| `-enableHTTPS '{YES|NO}'`               | Enable Fleet Patching and Provisioning transport layer security for HTTP.                                                                                                                                                            |
| `-port_range ``low_val-high_val`        | Specify the lower and upper port values for the ports to use for file transfer.                                                                                                                                                      |
| `-usegnsvip`                            | Optionally, enable Oracle FPP server to communicate on a Virtual IP Address (VIP), if the GNS port 53 is already in use.                                                                                                             |

##### Usage Notes

- You must be `root` user on Linux and UNIX platforms to run this command.

- The default user is the user who installed Oracle Clusterware, and this user gets added to the user list for the Fleet Patching and Provisioning Server resource.

#### srvctl config rhpserver

Displays configuration information for a Fleet Patching and Provisioning Server.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl config rhpserver

##### Example

This command returns output similar to the following:

    $ srvctl config rhpserver

    Storage base path: /scratch/aime/storagedg
    Disk Groups: MJKRHPSDG
    Port number: 8896
    Fleet Patching and Provisioning Server is enabled
    Fleet Patching and Provisioning Server is individually enabled on nodes:
    Fleet Patching and Provisioning Server is individually disabled on nodes:

#### srvctl disable rhpserver

Disables a Fleet Patching and Provisioning Server on a specific node from Oracle Clusterware management.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl disable rhpserver [-node node_name]

##### Usage Notes

Optionally, you can specify a node on which you want to disable the Fleet Patching and Provisioning Server.

##### Example

An example of this command is:

    $ srvctl disable rhpserver -node clusterNode01

#### srvctl enable rhpserver

Use this command to enable a Fleet Patching and Provisioning Server on a specific node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl enable rhpserver [-node node_name]

##### Usage Notes

Optionally, you can specify a node on which you want to enable the Fleet Patching and Provisioning Server. If you do not specify a node, then SRVCTL enables all of the Fleet Patching and Provisioning Servers in the Oracle Clusterware configuration.

##### Example

An example of this command is:

    $ srvctl enable rhpserver -node clusterNode03

#### srvctl modify rhpserver

Modifies the storage for a Fleet Patching and Provisioning Server.

##### Syntax

    srvctl modify rhpserver [-port rmi_port [-force]] [-email email_address
       -mailserver mail_server_address -mailserverport mail_server_port]
       [-pl_port RHP_progress_listener_port] [-clport RHP_copy_listener_port] [-enableTLS {YES|NO}]
       [-p12certpath p12_file_path -certname cert_name] [-enableHTTPS '{YES|NO}']
       [-port_range low_val-high_val] [-tmploc temporary_location]
       [-httpport rhpserver_http_port] [-rhpsvip_address rhps_vip_address]

##### Parameters

Table F-88 srvctl modify rhpserver Command Parameters

| Parameter                               | Description                                                                    |
|:----------------------------------------|:-------------------------------------------------------------------------------|
| `-port ``rmi_port`                      | Modify the RMI port number used by the Fleet Patching and Provisioning Server. |
| `-force`                                | Specify this parameter to stop and restart the resource to effect a change.    |
| `-email ``email_address`                | Modify an email address.                                                       |
| `-mailserver ``mail_server_address`     | Modify the mail server address.                                                |
| `-mailserverport ``mail_server_port`    | Modify the mail server port number.                                            |
| `-pl_port ``RHP_progress_listener_port` | Modify the Fleet Patching and Provisioning progress listener port number.      |
| `-clport ``RHP_copy_listener_port`      | Modify the Fleet Patching and Provisioning copy listener port number.          |
| `-enableTLS {YES|NO}`                   | Enable Fleet Patching and Provisioning transport level security.               |
| `-p12certpath ``p12_file_path`          | Absolute path to the P12 certificate file.                                     |
| `-certname ``cert_name`                 | Modify the security certificate registered name.                               |
| `-enableHTTPS '{YES|NO}'`               | Enable Fleet Patching and Provisioning transport layer security for HTTP.      |
| `-port_range ``low_val-high_val`        | Modify the lower and upper port values for the ports to use for file transfer. |
| `-tmploc``temporary_location`           | Modify the temporary location for Oracle FPP Server installation processing.   |
| `-httpport ``rhpserver_http_port`       | Specify the HTTP port number.                                                  |
| `-rhpsvip_address ``rhps_vip_address`   | Specify the VIP address for the Oracle FPP Server.                             |

#### srvctl relocate rhpserver

Relocates a Fleet Patching and Provisioning Server to a different node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl relocate rhpserver [-node node_name]

##### Usage Notes

Optionally, you can specify a node to which you want to relocate the Fleet Patching and Provisioning Server.

##### Example

An example of this command is:

    $ srvctl relocate rhpserver -node crsNode03

#### srvctl remove rhpserver

Removes a Fleet Patching and Provisioning Server instance configured for the cluster.

##### Syntax

    srvctl remove rhpserver [-resource] [-force] [-verbose]

##### Parameters

Table F-89 srvctl remove rhpserver Command Parameters

| Parameter   | Description                                                                                                             |
|:------------|:------------------------------------------------------------------------------------------------------------------------|
| `-resource` | Optionally, you can remove the Fleet Patching and Provisioning Server resource only, leaving its repository unaffected. |
| `–force`    | Forcibly remove the Fleet Patching and Provisioning Server, ignoring any dependencies.                                  |
| `–verbose`  | Print verbose output.                                                                                                   |

#### srvctl start rhpserver

Starts a Fleet Patching and Provisioning Server on a specific node.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl start rhpserver [-node node_name]

##### Usage Notes

Optionally, you can specify a node on which you want to start the Fleet Patching and Provisioning Server.

##### Examples

The following example starts the Fleet Patching and Provisioning Server on a node named `clusterNode03`:

    $ srvctl start rhpserver -node clusterNode03

#### srvctl status rhpserver

Displays the current state of a Fleet Patching and Provisioning Server.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl status rhpserver

##### Usage Notes

This command does not accept any parameters except for `-help`.

##### Example

This command returns output similar to the following:

    $ srvctl status rhpserver

    Fleet Patching and Provisioning Server is enabled
    Fleet Patching and Provisioning Server is running on node mjk1270089

#### srvctl stop rhpserver

Stops a Fleet Patching and Provisioning Server that is in a running or starting state.

**Note:**

This command is only available with Oracle Clusterware.

##### Syntax

    srvctl stop rhpserver

##### Usage Notes

This command does not accept any parameter except for `-help`.

#### srvctl add vm

Adds a virtual machine resource to Oracle Clusterware management.

##### Syntax

    srvctl add vm -name resource_name -vm "list_of_vms" [-serverpool server_pool_name | -category server_category
       | -node "node_list"] [–stoptimeout stop_timeout] [-checkinterval check_interval]

##### Parameters

Table F-90 srvctl add vm Command Parameters

| Parameter                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``resource_name`                                                                    | Specify a unique name for the virtual machine resource. If the name is not unique, then the command results in an error.                                                                                                                                                                                                                                                 |
| `-vm "``list_of_vms``"`                                                                    | Specify a comma-delimited list of virtual machine names or virtual machine IDs that you want to add to the virtual machine resource. A list must be enclosed in double quotation marks (`""`).<br>Currently, Oracle Clusterware gives preference to virtual machines at the beginning of this list, so you should list your most important virtual machines first.       |
| `-serverpool ``server_pool_name`` | -category ``server_category`` | -node "``node_list``"` | Optionally, you can specify the name of a server pool, server category, or list of nodes to which to add the virtual machine resource.<br>A list of nodes must be enclosed in double quotation marks (`""`).<br>If you choose to specify a list of nodes, then the number of nodes must be greater than or equal to the number of virtual machine resources you specify. |
| `–stoptimeout ``stop_timeout`                                                              | Optionally, you can specify a stop timeout, in seconds. The default is 180 if you do not assign a value to the parameter.                                                                                                                                                                                                                                                |
| `-checkinterval ``check_interval`                                                          | Optionally, you can specify an interval between checks, in seconds. The default is 10 if you do not assign a value to the parameter.                                                                                                                                                                                                                                     |

##### Usage Notes

You must run `srvctl add ovmm` and add virtual machine manager credentials before you add a virtual machine resource.

##### Example

An example of this command is:

    $ srvctl add vm -name vmres -vm vm1 -node node1

#### srvctl check vm

Checks the status of a specific virtual machine or a virtual machine instance running on a specific node.

##### Syntax

    srvctl check vm -name resource_name [-vm vm_name | -node node_name]

##### Parameters

Table F-91 srvctl check vm Command Parameters

| Parameter               | Description                                                                              |
|:------------------------|:-----------------------------------------------------------------------------------------|
| `-name ``resource_name` | Specify the name of the virtual machine resource for which you want to check the status. |
| `-vm ``vm_name`         | Specify the name or ID of the virtual machine on which the named resource resides.       |
| `-node ``node_name`     | Alternatively, specify the name of the node on which the virtual machine resides.        |

#### srvctl config vm

Lists the current configuration of a particular virtual machine.

##### Syntax

    srvctl config vm [-name unique_name]

##### Usage Notes

Specify the unique name of the virtual machine resource for which you want to display the configuration information. If you do not specify a particular virtual machine resource, then the command displays all of the virtual machine resources in the cluster.

##### Example

This command displays output similar to the following, depending on the command syntax used:

    $ srvctl config vm -name vmres1

    VM resource name: vmres1
    VMs: vm1, y, vm3
    VM Names: x, y, z
    VM IDs: vm1, vm2, vm3
    Server pool: vmpool
    Server category:
    Nodes:
    Stop Timeout: 7
    Check Interval: 5
    VM resource "vmres1" is enabled.
    VM resource is individually enabled on nodes:
    VM resource is individually disabled on nodes:
    VM resource is individually disabed for VMs: vm2,vm3
    $

    $ srvctl config vm

    vmres1
    vmres2
    vmres3
    $

#### srvctl disable vm

Disables a virtual machine resource.

##### Syntax

    srvctl disable vm -name unique_name [-vm "vm_list" | -node node_name]

##### Parameters

Table F-92 srvctl disable vm Command Parameters

| Parameter             | Description                                                                                                                                                                                                                                                    |
|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Specify the unique name of the virtual machine resource you want to disable.                                                                                                                                                                                   |
| `-vm "``vm_list``"`   | Specify the name or ID, or a list of names or IDs enclosed in double quotation marks (`""`) of the virtual machines on which the named resource resides. If you specify this parameter, then SRVCTL enables the cardinality instance matching that name or ID. |
| `-node ``node_name`   | Alternatively, specify the name of the node on which the virtual machine resides. If you specify this parameter, then SRVCTL does not allow any instances of the specified resource to run on that node.                                                       |

##### Usage Notes

If you do not specify any of the optional parameters, then SRVCTL disables the virtual machine resource, and the enabled or disabled states of all the nodes are purged, but the state of the virtual machines within the resource remains unchanged.

##### Example

An example of this command is:

    $ srvctl disable vm -name vmres -vm "vm1,vm2,vm3"

#### srvctl enable vm

Enables a virtual machine resource.

##### Syntax

    srvctl enable vm -name unique_name [-vm "vm_list" | -node node_name]

##### Parameters

Table F-93 srvctl enable vm Command Parameters

| Parameter             | Description                                                                                                                                                                                                                                                     |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Specify the name of the virtual machine resource you want to enable.                                                                                                                                                                                            |
| `-vm ``vm_list`       | Specify the name or ID, or a list of names or IDs enclosed in double quotation marks (`""`) of the virtual machines on which the named resource resides. If you specify this parameter, then SRVCTL disables the cardinality instance matching that name or ID. |
| `-node ``node_name`   | Alternatively, specify the name of the node on which the virtual machine resides. If you specify this parameter, then SRVCTL does not allow any instances of the specified resource to run on that node.                                                        |

##### Usage Notes

If you do not specify any of the optional parameters, then SRVCTL enables the virtual machine resource, and the enabled or disabled states of all the nodes are purged, but the state of the virtual machines within the resource remains unchanged.

##### Example

An example of this command is:

    $ srvctl enable -name vmres -node node3

#### srvctl modify vm

Modifies the virtual machine resource configuration.

##### Syntax

    srvctl modify vm -name uniquee_name [-addvm "list_of_vms" | -removevm "list_of_vms"
       [-serverpool server_pool_name | -category server_category | -node "node_list"]
       [–stoptimeout stop_timeout] [-checkinterval check_interval]

##### Parameters

Table F-94 srvctl modify vm Command Parameters

| Parameter                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                          |
|:-------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name`                                                                      | Specify the unique name of the virtual machine resource you want to modify.                                                                                                                                                                                                                                                                                                          |
| `-addvm "``list_of_vms``"`                                                                 | Specify a comma-delimited list of virtual machine names or virtual machine IDs, enclosed in double quotation marks (`""`), that you want to add to the virtual machine resource. You can add virtual machines to a virtual machine resource at any time regardless of whether the virtual machine resource instance is running. Adding virtual machines creates new cardinality IDs. |
| `-removevms "``list_of_vms``"`                                                             | Specify a comma-delimited list of virtual machine names or virtual machine IDs that you want to remove from the virtual machine resource. You cannot remove a virtual machine if there are existing instances of the virtual machine resource still running. An attempt to do so results in an error.                                                                                |
| `-serverpool ``server_pool_name`` | -category ``server_category`` | -node "``node_list``"` | You can modify the server pool, server category, or list of nodes to which the virtual machine resource belongs.<br>A list of nodes must be enclosed in double quotation marks (`""`).<br>If you choose to specify a list of nodes, then the number of nodes must be greater than or equal to the number of virtual machine resources you specify.                                   |
| `–stoptimeout ``stop_timeout`                                                              | You can modify the stop timeout, in seconds. The default is 180 if you do not assign a value to the parameter.                                                                                                                                                                                                                                                                       |
| `-checkinterval ``check_interval`                                                          | You can modify the interval between checks, in seconds. The default is 10 if you do not assign a value to the parameter.                                                                                                                                                                                                                                                             |

##### Example

An example of this command is:

    $ srvctl modify vm -name vmres -addvm vm2 -removevm vm1 -stoptimeout 93

#### srvctl relocate vm

Relocates a running virtual machine resource to another node, or relocates the virtual machine resource running on the specified node to another node.

##### Syntax

    srvctl relocate vm -name unique_name {-vm vm_name | -srcnode source_node_name}
       -node destination_node_name]

##### Parameters

Table F-95 srvctl relocate vm Command Parameters

| Parameter                       | Description                                                                                                                                                                                                                                  |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name`           | Specify the unique name of the virtual machine resource you want to relocate.                                                                                                                                                                |
| `-vm ``vm_name`                 | Specify the name or ID of the virtual machine on which the named resource resides to which you want to relocate the virtual machine resource, together with the name of the node to which you want to relocate the virtual machine resource. |
| `-srcnode ``source_node_name`   | Alternatively, you can specify a node from which you want to relocate a virtual machine resource.                                                                                                                                            |
| `-node ``destination_node_name` | Optionally, you can specify the name of a destination node to which you want to relocate the virtual machine resource.                                                                                                                       |

##### Example

An example of this command is:

    $ srvctl relocate -name vmres -vm vm1 -node node3

#### srvctl remove vm

Removes a specific virtual machine resource.

##### Syntax

    srvctl remove vm -name unique_name [-force]

##### Usage Notes

Specify the unique name of the virtual machine resource you want to remove and, optionally, you can forcibly remove a running virtual machine resource.

#### srvctl start vm

Starts a specific virtual machine resource on a node.

##### Syntax

    srvctl start vm -name unique_name [-vm vm_name -node node_name]

##### Parameters

Table F-96 srvctl start vm Command Parameters

| Parameter               | Description                                                                                                                                     |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``resource_name` | Specify the unique name of the virtual machine resource you want to start.                                                                      |
| `-vm ``vm_name`         | Optionally, you can specify the virtual machine on which the virtual machine resource resides that you want to start.                           |
| `-node ``node_name`     | Optionally, you can specify the name of a node on which a virtual machine resides that contains the virtual machine resource you want to start. |

##### Usage Notes

You can use the `-vm` and `-node` parameters, together, to start a particular virtual machine resource on a particular node. You can also use either the `-vm` parameter or the `-node` parameter to start a particular virtual machine resource or the virtual machine resource that resides on a particular node, respectively.

##### Example

An example of this command is:

    $ srvctl start vm -name vmres -vm vm3 -node node3

#### srvctl status vm

Displays the currently known state of the virtual machine resource.

##### Syntax

    srvctl status vm -name unique_name [-vm vm_name | -node node_name]

##### Parameters

Table F-97 srvctl status vm Command Parameters

| Parameter             | Description                                                                                                                                                  |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Specify the unique name of the virtual machine resource for which you want to display the status.                                                            |
| `-vm ``vm_name`       | Optionally, you can specify the virtual machine on which the virtual machine resource resides that you want to display the status.                           |
| `-node ``node_name`   | Optionally, you can specify the name of a node on which a virtual machine resides that contains the virtual machine resource you want to display the status. |

##### Examples

This command returns output similar to following, depending on which parameters you specify:

    $ srvctl status vm -name vmres1 -vm vm1

    Virtual machine "vm1" of VM resource "vmres1" is running on node aime1.
    $

    $ srvctl status vm -name vmres1

    Virtual machine "vm1" of VM resource “vmres1” is running on node aime1.
    Virtual machine "vm2" of VM resource “vmres1” is not running.
    Virtual machine "vm3" of VM resource “vmres1” is running on node aime3
    $

    $ srvctl status vm -name vmres1 -vm vm1 -S 1

    result: vm_resource={vmres1} inst_name={vm1} node_name={aime1} up={true}
    $

#### srvctl stop vm

Stops a specific virtual machine resource, or one on a specific virtual machine or node.

##### Syntax

    srvctl stop vm -name unique_name [-vm vm_name | -node node_name]

##### Parameters

Table F-98 srvctl stop vm Command Parameters

| Parameter             | Description                                                                                                                                    |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `-name ``unique_name` | Specify the unique name of the virtual machine resource you want to stop.                                                                      |
| `-vm ``vm_name`       | Optionally, you can specify the virtual machine on which the virtual machine resource resides that you want to stop.                           |
| `-node ``node_name`   | Optionally, you can specify the name of a node on which a virtual machine resides that contains the virtual machine resource you want to stop. |

##### Example

An example of this command is:

    $ srvctl stop vm -name vmres1 -node node1
