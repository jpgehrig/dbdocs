This chapter describes how to administer Oracle Real Application Clusters (Oracle RAC) databases and database instances.

The topics in this chapter include:

- Overview of Oracle RAC Database Administration

- Starting and Stopping Instances and Oracle RAC Databases

- Starting and Stopping PDBs in Oracle RAC

- Verifying That Instances are Running

- Terminating Sessions On a Specific Cluster Instance

- Overview of Initialization Parameter Files in Oracle RAC

- Initialization Parameter Use in Oracle RAC

- Converting an Administrator-Managed Database to a Policy-Managed Database

- Managing Memory Pressure for Database Servers

- Quiescing Oracle RAC Databases

- Administering Multiple Cluster Interconnects on Linux and UNIX Platforms

- Customizing How Oracle Clusterware Manages Oracle RAC Databases

- Advanced Oracle Enterprise Manager Administration

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for more information about Oracle Enterprise Manager Cloud Control

### Overview of Oracle RAC Database Administration

Oracle RAC database administration requires certain privileges and involves either a policy-managed or administrator-managed deployment model.

#### Required Privileges for Oracle RAC Database Administration

To increase security and further separate administrative duties, Oracle RAC database administrators manage Oracle RAC databases with the SYSRAC administrative privilege, and no longer require the SYSDBA administrative privilege. The SYSRAC administrative privilege is the default mode of connecting to the database by the Oracle Clusterware agent on behalf of Oracle RAC utilities, such as SRVCTL, meaning that no SYSDBA connections to the database are necessary for everyday administration of Oracle RAC database clusters.

#### Oracle RAC Database Depolyment Models

Oracle RAC databases support two different management styles and deployment models:

- Administrator-managed deployment is based on the Oracle RAC deployment types that existed before Oracle Database 11g release 2 (11.2) and requires that you statically configure each database instance to run on a specific node in the cluster, and that you configure database services to run on specific instances belonging to a certain database using the `preferred` and `available` designation.

- Policy-managed deployment is based on server pools, where database services run within a server pool as singleton or uniform across all of the servers in the server pool. Databases are deployed in one or more server pools and the size of the server pools determine the number of database instances in the deployment.

You can manage databases with either the administrator-managed or policy-managed deployment model using the same commands or methods (such as DBCA or Oracle Enterprise Manager). All commands and utilities maintain backward compatibility to support the management of Oracle databases that only support administrator-based management (Oracle databases before Oracle Database 11g release 2 (11.2)).

In general, a database is defined as a resource in Oracle Clusterware. The database resource is automatically created when you create your database with DBCA or provision a database using Rapid Home Provisioning, or you can manually create the database resource by adding your database with SRVCTL. The database resource contains the Oracle home, the SPFILE, one or more server pools, and one or more Oracle ASM disk groups required for the database to start. You can specify the Oracle ASM disk groups using either the `srvctl add database` or `srvctl modify database` commands, or, when the database opens a data file on a disk group that is not on this list, the disk group gets added to the list.

The database resource also has a weak start dependency on the listener type, which means that the resource tries to start all listeners for the node when the database instance starts. Oracle Clusterware tries to start listeners on the node where the database instance starts. Starting the listeners in turn starts the VIP for the node.

When you review the database resource for an administrator-managed database, you see a server pool defined with the same name as the Oracle database. This server pool is part of a special Oracle-defined server pool called Generic. Oracle RAC manages the Generic server pool to support administrator-managed databases. When you add or remove an administrator-managed database using either SRVCTL or DBCA, Oracle RAC creates or removes the server pools that are members of Generic. You cannot use SRVCTL or CRSCTL commands to modify the Generic server pool.

Use [policy-managed database](glossary.md)s to simplify management of dynamic systems. Policy management allows clusters and databases to expand or shrink as requirements change. If you use policy-managed databases, then you must install the Oracle home software on every node in your cluster. Policy-managed databases must use Oracle Database 11g release 2 (11.2) or higher software and cannot coexist on the same servers as administrator-managed databases.

**Note:**

You cannot run more than one instance of the same database on the same node.

A policy-managed database is defined by [cardinality](glossary.md), which is the number of database instances you want running during normal operations. A policy-managed database runs in one or more database server pools that the cluster administrator creates in the cluster, and it can run on different servers at different times. Every server pool of a policy-managed database should have at least one database service. A database instance starts on a server that is in the server pools defined for the database. If you are using Oracle Automatic Storage Management (Oracle ASM) with Oracle Managed Files for your database storage, then, when an instance starts and there is no redo thread available, Oracle RAC automatically enables one and creates the required redo log files and undo tablespace. Clients can connect to a policy-managed database using the same SCAN-based connect string no matter which servers they happen to be running on at the time.

Policy-managed database instances are named `db_unique_name``_``cardinality`, where `cardinality` is the cardinality ID of the server in the server pool. Use the `srvctl status database -sid` command to retrieve the instance name on the local node. You can also create a fixed mapping of nodes-to-instance name using the `srvctl modify instance` command.

#### Using the Same Cluster for Administrator-Managed and Policy-Managed Databases

If you want to create an administrator-managed database on a cluster that already hosts policy-managed databases, then you must carefully select the nodes for the administrator-managed database. This is because the nodes that you select for an administrator-managed database that are in policy-managed server pools will be moved into the Generic server pool as part of this process.

If you select nodes that already run other policy-managed database instances, then DBCA prompts you with a message that lists the instances and services that will be shut down when DBCA creates the administrator-managed database. If you select the Yes button on the dialog box when DBCA asks "Do you want to continue?", then your policy-managed database instances and services will be shut down because of the administrator-managed database creation process.

**Note:**

This is also true if you use the `srvctl add instance` command, which returns a similar error message indicating that the databases would be shut down. If you also use the force option (`-f`) with the `srvctl add instance` command, then this is the same as choosing Yes on the DBCA dialog. Doing this shuts down any policy-managed databases that are running on the node before moving the node into the Generic server pool.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/making-applications-highly-available-using-oracle-clusterware.md)
- Converting an Administrator-Managed Database to a Policy-Managed Database

#### Tools for Administering Oracle RAC

The following sections introduce Oracle RAC administration using the three tools that you commonly use to manage Oracle RAC databases and instances: the SRVCTL utility, Oracle Enterprise Manager, and SQL\*Plus. In many cases, you use these tools the same way to manage Oracle RAC environments as you would use them manage noncluster Oracle databases:

- Administering Oracle RAC with SRVCTL

- Administering Oracle RAC with Oracle Enterprise Manager

- Administering Oracle RAC with SQL\*Plus

##### Administering Oracle RAC with SRVCTL

The Server Control Utility (SRVCTL) is a command-line interface that you can use to manage Oracle Databases in a centralized manner.

Oracle made centralized, SRVCTL-based database management available in Oracle Database 11g release 2 (11.2) for single-instance Oracle Databases, using Oracle ASM in the Oracle Grid Infrastructure, for both a noncluster environment and Oracle RAC databases, based on Oracle Grid Infrastructure for a cluster. This enables homogeneous management of all Oracle Database types using SRVCTL. You can use SRVCTL to start and stop the database and instances, and to delete or move instances and services. You can also use SRVCTL to add services and manage configuration information, in addition to other resources in the cluster.

When you use SRVCTL to perform configuration operations on your cluster, SRVCTL stores configuration data in the Oracle Cluster Registry (OCR) in a cluster or Oracle Local Registry (OLR) in Oracle Restart environments. SRVCTL performs other operations, such as starting and stopping instances, by configuring and managing Oracle Clusterware resources, which define agents that perform database startup and shutdown operations using Oracle Call Interface APIs.

**Note:**

If you require your database (or database instance) to start using certain environment variables, then use the `srvctl setenv` command to set those variables for the database profile that is maintained for the database using SRVCTL. You do not need to set the `ORACLE_HOME` and `ORACLE_SID` environment variables, because SRVCTL maintains and sets those parameters, automatically.

**Related Topics**

- [Server Control Utility Reference](server-control-utility-reference.md)

##### Administering Oracle RAC with Oracle Enterprise Manager

Oracle Enterprise Manager provides a central point of control for the Oracle RAC environment, allowing you to perform administrative tasks simultaneously on multiple cluster databases.

Based on the Oracle Enterprise Manager Cloud Control (Grid Control in Oracle Enterprise Manager 11g) graphical user interface (GUI), you can manage both non-clustered and Oracle RAC environments.

In Oracle Enterprise Manager, Oracle RAC-specific administrative tasks generally focus on two levels: tasks that affect an entire cluster database and tasks that affect specific instances. For example, you can use Oracle Enterprise Manager to start, stop, and monitor databases, cluster database instances, and their listeners, and to schedule jobs or set up alert thresholds for metrics. Or you can perform instance-specific commands such as setting parameters or creating resource plans. You can also use Oracle Enterprise Manager to manage schemas, security, and cluster database storage features.

**Related Topics**

- Advanced Oracle Enterprise Manager Administration

##### Administering Oracle RAC with SQL\*Plus

Unlike SRVCTL or Oracle Enterprise Manager, SQL\*Plus is an instance-oriented management tool.

SQL\*Plus commands operate on the current instance. The current instance can be either the local default instance on which you initiated your SQL\*Plus session, or it can be a remote instance to which you connect with Oracle Net Services. For an Oracle RAC environment that runs multiple instances on one database at the same time, this implies that you need to consider the extent to which SQL\*Plus can operate on this instance. Due to those restrictions, you should not use SQL\*Plus to manage policy-managed databases.

**Note:**

Starting with Oracle Grid Infrastructure 21c, policy-managed databases are deprecated.

For example, when using pluggable databases (PDBs)—regardless of whether those databases are managed in an administrator-managed or a policy-managed style—you must consider that any alteration performed on the PDB using a SQL\*Plus connection will, by default, only affect the current instance. To make changes affecting all instances that belong to the PDB, you must use the `ALTER PLUGGABLE DATABASE` command with `instance=all`. When using PDBs you must connect, using a dynamic database service (`net_service_name`), to an instance, as PDBs represent themselves as dynamic database services associated with one or more instances of an Oracle RAC database.

Because, by default, the SQL\*Plus prompt does not identify the current instance, you should direct your commands to the correct instance. Starting a SQL\*Plus session and connecting to the database without specifying an instance directs all SQL\*Plus commands to the local instance. In this case, the default instance is also the current instance.

Since the SQL\*Plus prompt does not identify the current instance by default, you should direct your commands to the correct instance. Starting a SQL\*Plus session and connecting to the database without specifying an instance directs all SQL\*Plus commands to the local instance. In this case, the default instance is also the current instance. To connect to a different instance in SQL\*Plus, issue a new `CONNECT` command and specify a remote instance net service name, as shown in the following example, where `password` is the password:

    CONNECT user_name@net_service_name
    Enter password: password

Connecting as `SYSOPER` or `SYSRAC` enables you to perform privileged operations, such as instance startup and shutdown. Multiple SQL\*Plus sessions can connect to the same instance at the same time. SQL\*Plus automatically disconnects you from the first instance whenever you connect to another one.

**Note:**

Use the `SYSASM` privilege instead of the `SYSRAC` privilege to connect to and administer an Oracle ASM instance. If you use the `SYSRAC` privilege to connect to an Oracle ASM instance, then Oracle Database writes warnings to the alert log files because commands that run using the `SYSRAC` privilege on an Oracle ASM instance are deprecated.

**Related Topics**

- [Authentication for Accessing Oracle ASM Instances](../ostmg/authenticate-access-asm-instance.md)
- [Configuring Naming Methods](../netag/configuring-naming-methods.md)
- [Modifying a PDB with the ALTER PLUGGABLE DATABASE Statement](../multi/administering-pdbs-with-sql-plus.md)

###### How SQL\*Plus Commands Affect Instances

You can use SQL\*Plus to start and stop instances in the Oracle RAC database.

Most SQL statements affect the current instance. You do not need to run SQL\*Plus commands as `root` on Linux and UNIX systems or as `Administrator` on Windows systems. You need only the proper database account with the privileges that you normally use for a noncluster Oracle database. Some examples of how SQL\*Plus commands affect instances are:

- `ALTER SYSTEM CHECKPOINT LOCAL` affects only the instance to which you are currently connected, rather than the default instance or all instances.

- `ALTER SYSTEM CHECKPOINT` or `ALTER SYSTEM CHECKPOINT GLOBAL` affects all instances in the cluster database.

- `ALTER SYSTEM SWITCH LOGFILE `affects only the current instance.

  - To force a global log switch, use the `ALTER SYSTEM ARCHIVE LOG CURRENT` statement.

  - The `INSTANCE` option of `ALTER SYSTEM ARCHIVE LOG` enables you to archive each online redo log file for a specific instance.

The following table describes how SQL\*Plus commands affect instances.

Table 3-1 How SQL\*Plus Commands Affect Instances

| SQL\*Plus Command                     | Associated Instance                                                                                                                                                |
|:--------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ARCHIVE LOG`                         | Always affects the current instance.                                                                                                                               |
| `CONNECT`                             | Affects the default instance if no instance is specified in the `CONNECT` command.                                                                                 |
| `HOST`                                | Affects the node running the SQL\*Plus session, regardless of the location of the current and default instances.                                                   |
| `RECOVER`                             | Does not affect any particular instance, but rather the database.                                                                                                  |
| `SHOW INSTANCE`                       | Displays information about the current instance, which can be different from the default local instance if you have redirected your commands to a remote instance. |
| `SHOW PARAMETER`<br>and<br>`SHOW SGA` | Displays parameter and SGA information from the current instance.                                                                                                  |
| `STARTUP`<br>and<br>`SHUTDOWN`        | Always affects the current instance. These are privileged SQL\*Plus commands.                                                                                      |

### Starting and Stopping Instances and Oracle RAC Databases

You can start and stop instances with Oracle Enterprise Manager, SQL\*Plus, or SRVCTL.

Both Oracle Enterprise Manager and SRVCTL provide options to start and stop all of the instances in an Oracle RAC database with a single step.

Using any tool, you can choose the startup state to which you want to start the database. The state of the database and database instance will determine what operations you can perform. You can perform certain operations only when the database is in the MOUNT (NOMOUNT) state. Performing other operations requires that the database be in the OPEN state.

**Note:**

Oracle does not support running more than one instance of the same database on the same node.

To start an Oracle RAC database instance on a node in the cluster, you must first start the Oracle Grid Infrastructure stack on the node. An Oracle RAC database instance will not start on a server on which the Oracle Grid Infrastructure stack is not running.

#### Oracle Database QoS Management Policy Workload Criticality Determines Database Startup Order

If a user-created Oracle Database Quality of Service Management (Oracle Database QoS Management) policy is active, then the ranked order of the performance classes determines the order in which the associated Oracle RAC databases start or request real-time LMS process slots. Using the performance class rankings ensures that mission-critical databases running in a consolidated environment have their LMS processes run in real time, thus eliminating a resource bottleneck within inter-node communication. Because the Oracle Database QoS Management policy specifies the rank of each workload, using the value of `Max(Ranks)` for each database provides a consistent expression of the expressed business criticality of each database.

The procedures in the following sections discuss starting and stopping Oracle RAC database instances:

- Starting One or More Instances and Oracle RAC Databases Using SRVCTL

- Stopping One or More Instances and Oracle RAC Databases Using SRVCTL

- Stopping All Databases and Instances Using CRSCTL

- Starting and Stopping Individual Instances Using SQL\*Plus

**Related Topics**

- [Oracle Database Concepts](../cncpt/oracle-database-instance.md)

#### Starting One or More Instances and Oracle RAC Databases Using SRVCTL

Use SRVCTL start Oracle RAC databases and instances.

**Note:**

This section assumes that you are using an SPFILE for your database.

Enter the following SRVCTL syntax from the command line, providing the required database name and instance name, or include multiple instance names to start multiple specific instances:

- To start or stop your entire cluster database, that is, all of the instances and its enabled services, enter the following SRVCTL commands:

      $ srvctl start database -db db_unique_name [-startoption start_options]

      $ srvctl stop database -db db_unique_name [-o stop_options]

  The following SRVCTL command, for example, mounts all of the non-running instances of an Oracle RAC database:

      $ srvctl start database -db orcl -startoption mount

- To start administrator-managed databases, enter a comma-delimited list of instance names:

      $ srvctl start instance -db db_unique_name -instance instance_name_list
        [-startoption start_options]

  In Windows you must enclose a comma-delimited list in double quotation marks (`""`).

- To start policy-managed databases, enter a single node name:

      $ srvctl start instance -db db_unique_name -node node_name
        [-startoption start_options]

  Note that this command also starts all enabled and non-running services that have `AUTOMATIC` management policy, and for which the database role matches one of the service's roles.

- To stop one or more instances, enter the following SRVCTL syntax from the command line:

      $ srvctl stop instance -db db_unique_name [-instance "instance_name_list" |
        -node node_name] [-stopoption stop_options]

  You can enter either a comma-delimited list of instance names to stop several instances or you can enter a node name to stop one instance. In Windows you must enclose a comma-delimited list in double quotation marks (`""`).

This command also stops the services related to the terminated instances on the nodes where the instances were running. As an example, the following command shuts down the two instances, `orcl3` and `orcl4`, on the `orcl` database using the `immediate` stop option:

    $ srvctl stop instance -db orcl -instance "orcl3,orcl4" -stopoption immediate

**Related Topics**

- [Server Control Utility Reference](server-control-utility-reference.md)

#### Stopping One or More Instances and Oracle RAC Databases Using SRVCTL

Use SRVCTL to stop instances and Oracle RAC databases.

The procedure for shutting down Oracle RAC instances is identical to shutting down instances in noncluster Oracle databases, with the following exceptions:

- In Oracle RAC, shutting down one instance does not interfere with the operation of other running instances.

- To shut down an Oracle RAC database completely, shut down every instance that has the database open or mounted.

- After a `NORMAL` or `IMMEDIATE` shutdown, instance recovery is not required. Recovery is required, however, after you issue the `SHUTDOWN ABORT` command or after an instance terminates unusually. An instance that is still running performs instance recovery for the instance that shut down. If no other instances are running, the next instance to open the database performs instance recovery for any instances needing it.

- Using the `SHUTDOWN TRANSACTIONAL` command with the `LOCAL` option is useful to shut down a particular Oracle RAC database instance. Transactions on other instances do not block this operation. If you omit the `LOCAL` option, then this operation waits until transactions on all other instances that started before you ran the `SHUTDOWN` command either commit or rollback, which is a valid approach, if you intend to shut down all instances of an Oracle RAC database.

  **Note:**

  `SHUTDOWN TRANSACTIONAL` and `SHUTDOWN TRANSACTIONAL LOCAL` both perform the same action on a nonclustered database but the two commands are different on an Oracle RAC database.

Enter the following SRVCTL syntax from the command line, providing the required database name and instance name, or include multiple instance names to stop multiple specific instances:

- To stop your entire cluster database, that is, all of the instances and its enabled services, enter the following SRVCTL command:

      $ srvctl stop database -db db_unique_name [-stopoption stop_options]

  Use the `TRANSACTIONAL` stop option with the `srvctl stop database` command and the `TRANSACTIONAL LOCAL` stop option with the `srvctl stop instance` command.

- To stop all instances and their enabled services that are managed by Oracle Clusterware on one or more nodes, enter the following SRVCTL command:

      $ srvctl stop instance -node "node_list" [-stopoption stop_options]

- To stop one or more instances, enter the following SRVCTL syntax from the command line:

      $ srvctl stop instance -db db_unique_name {-node "node_list" | -instance "inst_name_list"}
         [-stopoption stop_options]

  You can enter either a comma-delimited list of instance names to stop several instances or you can enter a node name to stop one instance. In Windows you must enclose a comma-delimited list in double quotation marks (`""`).

  This command also stops the services related to the terminated instances on the nodes where the instances were running. As an example, the following command shuts down the two instances, `orcl3` and `orcl4`, on the `orcl` database using the `failover` option for CRS to find another node to run the services from it and the `immediate` stop option:

      $ srvctl stop instance -db orcl -instance "orcl3,orcl4" -failover -stopoption immediate

**Related Topics**

- [srvctl stop database](server-control-utility-reference.md)
- [srvctl stop instance](server-control-utility-reference.md)
- [Overview of Database and Instance Shutdown](../cncpt/oracle-database-instance.md)
- [Shutting Down a Database](../admin/starting-up-and-shutting-down.md)

#### Stopping All Databases and Instances Using CRSCTL

You can use the `crsctl stop crs` command on the node or the `crsctl stop cluster -all` command to stop all instances on a node or the entire cluster.

When you want to stop an entire node or cluster (for maintenance purposes, for example), you run either the `crsctl stop crs` command on the node or the `crsctl stop cluster -all` command, provided you have the required cluster privileges. These commands stop all database instances running on a server or in the cluster and ensure that their state is recovered after you restart the cluster. Using CRSCTL also enables Oracle Clusterware to relocate services and other resources that can run elsewhere.

Using either of these CRSCTL commands to stop all database instances on a server or in the cluster can lead to the database instances being stopped similar to shutdown abort, which requires an instance recovery on startup. If you use SRVCTL to stop the database instances manually before stopping the cluster, then you can prevent a shutdown abort, but this requires that you manually restart the database instances after restarting Oracle Clusterware.

#### Starting and Stopping Individual Instances Using SQL\*Plus

If you want to start or stop only one instance and you are connected to your local node, then you must first ensure that your current environment includes the SID for the local instance.

Note that any subsequent commands in your session, whether inside or outside a SQL\*Plus session, are associated with that same SID.

**Note:**

This section assumes you are using an SPFILE.

To start or shutdown your local instance, initiate a SQL\*Plus session and connect with the SYSRAC or SYSOPER privilege and then issue the required command. For example to start and mount an instance on your local node, run the following commands in your SQL\*Plus session:

       CONNECT / AS SYSRAC
       STARTUP MOUNT

**Note:**

If you use Oracle ASM disk groups, then use the SYSASM privilege instead of the SYSRAC privilege to connect to and administer the Oracle ASM instances.

Oracle recommends that you do not use SQL\*Plus to manage Oracle ASM instances in an Oracle RAC environment. Oracle Clusterware automatically manages Oracle ASM instances, as required. If manual intervention is necessary, then use respective SRVCTL commands.

You can start multiple instances from a single SQL\*Plus session on one node using Oracle Net Services. Connect to each instance in turn by using a Net Services connection string, typically an instance-specific alias from your `tnsnames.ora` file.

For example, you can use a SQL\*Plus session on a local node to perform a transactional shutdown for two instances on remote nodes by connecting to each in turn using the instance's individual alias name. Assume the alias name for the first instance is `db1` and that the alias for the second instance is `db2`. Connect to the first instance and shut it down as follows:

       CONNECT /@db1 AS SYSRAC
       SHUTDOWN TRANSACTIONAL

**Note:**

To ensure that you connect to the correct instance, you must use an alias in the connect string that is associated with only one instance. If you use a connect string that uses a TNS alias that connects to a service or an Oracle Net address that lists multiple IP addresses, then you might not be connected to the specific instance you want to shut down.

Then connect to and shutdown the second instance by entering the following from your SQL\*Plus session:

       CONNECT /@db2 AS SYSRAC
       SHUTDOWN TRANSACTIONAL

It is not possible to start or stop multiple instances, simultaneously, with SQL\*Plus, so you cannot start or stop all of the instances for a cluster database with a single SQL\*Plus command. You may want to create a script that connects to each instance in turn and start it up and shut it down. However, you must maintain this script manually if you add or drop instances.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md)
- [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-reference.md)

### Starting and Stopping PDBs in Oracle RAC

Administering a pluggable database (PDB) involves a small subset of the tasks required to administer a non-CDB.

Administering an Oracle RAC-based multitenant container database (CDB) is similar to administering a non-CDB. The differences are that some administrative tasks apply to the entire CDB, some to the CDB root, and some to specific PDBs. In this subset of tasks, most are the same for a PDB and a non-CDB. There are some differences, however, such as when you modify the open mode of a PDB. Also, a PDB administrator is limited to managing a single PDB and is not affected by other PDBs in the CDB.

You manage PDBs in an Oracle RAC CDB by managing services. This is true regardless of whether the PDBs are policy managed or administrator managed. Assign one dynamic database service to each PDB to coordinate start, stop, and placement of PDBs across instances in a clustered container database.

For example, if you have a CDB called `raccont` with a policy-managed PDB called `spark` in a server pool called `prod`, then assign a service called `plug` to this database using the following command:

    srvctl add service –db raccont –pdb spark –service plug –serverpool prod

The service `plug` is uniformly managed across all nodes in the server pool. If you want to have this service running as a singleton service in the same server pool, then use the `-cardinality singleton` parameter with the preceding command.

To open the PDB `spark`, you must start the service `plug` as follows:

    srvctl start service -db raccont -service plug

To stop the service `plug`:

    srvctl stop service -db raccont -service plug

The PDB `spark` remains open until you close the PDB using the SQL command `ALTER PLUGGABLE DATABASE ``PDB_NAME`` CLOSE IMMEDIATE`. You can check the status of the database using the `srvctl status service` command.

Because PDBs are managed using dynamic database services, typical Oracle RAC-based management practices apply. For this reason, if the service `plug` is in the online state when Oracle Clusterware is shut down on a server hosting this service, then the service is restored to its original state after the restart of Oracle Clusterware on this server. Thus, starting PDBs is automated as with any other Oracle RAC database.

**Note:**

Unlike SQL\*Plus, SRVCTL operates on an entire cluster database. Starting a PDB using services therefore applies to multiple instances of the clustered CDB at the same time when the service is defined to run on multiple servers simultaneously and the current status of the cluster allows for this placement.

**Related Topics**

- [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md)

### Verifying That Instances are Running

To verify that a database instance is available, use Oracle Enterprise Manager, SRVCTL, or SQL\*Plus.

- Using SRVCTL to Verify That Instances are Running

- Using SQL\*Plus to Verify That Instances are Running

#### Using SRVCTL to Verify That Instances are Running

You can use SRVCTL to verify that instances are running on a particular database.

The following command provides an example of using SRVCTL to check the status of the database instances for the Oracle RAC database named mail:

    $ srvctl status database -db mail

This command returns output similar to the following:

    Instance mail1 is running on node betal011Instance mail2 is running on node betal010

Additionally, you can check whether PDBs are running in the cluster by checking the availability of their assigned services, as follows:

    $ srvctl status service -db db_unique_name -service service_name

#### Using SQL\*Plus to Verify That Instances are Running

You can use SQL\*Plus to verify that database instances are running.

1.  On any node, from a SQL\*Plus prompt, connect to a database instance by using a Net Services connection string, typically an instance-specific alias from your `tnsnames.ora` file.

        CONNECT /@db1 as SYSRAC

2.  Query the V\$ACTIVE_INSTANCES view, using the following statement:

        CONNECT SYS/as SYSRAC
        Enter password: password
        SELECT * FROM V$ACTIVE_INSTANCES;

    This query returns output similar to the following:

        INST_NUMBER INST_NAME
        -----------  -----------------
        1            db1-sun:db1
        2            db2-sun:db2
        3            db3-sun:db3

The output columns for this example are shown in the following table.

Table 3-2 Descriptions of V\$ACTIVE_INSTANCES Columns

| Column        | Description                                                                |
|:--------------|:---------------------------------------------------------------------------|
| `INST_NUMBER` | Identifies the instance number.                                            |
| `INST_NAME`   | Identifies the host name and instance name as `host_name`:`instance_name`. |

### Terminating Sessions On a Specific Cluster Instance

You can use the `ALTER SYSTEM KILL SESSION` statement to terminate a session on a specific instance.

When a session is terminated, any session active transactions are rolled back, and resources held by the session (such as locks and memory areas) are immediately released and available to other sessions.

Using the `ALTER SYSTEM KILL SESSION` statement enables you to maintain strict application service-level agreements in Oracle RAC environments. Often, the goal of a service-level agreement is to carry out a transaction in a specified time limit. In an Oracle RAC environment, this may require terminating a transaction on an instance, and retrying the transaction on another instance within a specified time frame.

**Note:**

You can use Application Continuity to hide the cancellation of a transaction from the user, if the application initially used an Application Continuity-enabled dynamic database service to connect to the database instance.

For a more granular approach to service-level management, Oracle recommends that you use Oracle Database Quality of Service Management (Oracle Database QoS Management) for all Oracle RAC-based databases.

To terminate sessions, follow these steps:

1.  Query the value of the `INST_ID` column in the `GV$SESSION` dynamic performance view to identify which session to terminate.

2.  Issue the `ALTER SYSTEM KILL SESSION` and specify the session index number (SID) and serial number of a session that you identified with the `GV$SESSION` dynamic performance view.

        KILL SESSION 'integer1, integer2[, @integer3]'

    - For `integer1`, specify the value of the SID column.

    - For `integer2`, specify the value of the `SERIAL#` column.

    - For the optional `integer3`, specify the ID of the instance where the session to be terminated exists. You can find the instance ID by querying the `GV$` tables.

    To use this statement, your instance must have the database open, and your session and the session to be terminated must be on the same instance unless you specify `integer3`.

If the session is performing some activity that must be completed, such as waiting for a reply from a remote database or rolling back a transaction, then Oracle Database waits for this activity to complete, marks the session as terminated, and then returns control to you. If the waiting lasts a minute, then Oracle Database marks the session to be terminated and returns control to you with a message that the session is marked to be terminated. The PMON background process then marks the session as terminated when the activity is complete.

#### Examples of Identifying and Terminating Sessions

The following examples provide three scenarios in which a user identifies and terminates a specific session. In each example, the SYSDBA first queries the `GV$SESSION` view for the `SCOTT` user's session to identify the session to terminate, and then runs the `ALTER SYSTEM KILL SESSION` statement to terminate the session on the instance.

Example 3-1 Identify and terminate the session on an busy instance

In this example, assume that the running session is `SYSDBA` on the instance `INST_ID=1`. The `ORA-00031` message is returned because some activity must be completed before the session can be terminated.

    SQL> SELECT SID, SERIAL#, INST_ID FROM GV$SESSION WHERE USERNAME='SCOTT';

           SID    SERIAL#    INST_ID
    ---------- ---------- ----------
            80          4          2

    SQL> ALTER SYSTEM KILL SESSION '80, 4, @2';
    alter system kill session '80, 4, @2'
    *
    ERROR at line 1:
    ORA-00031: session marked for kill
    SQL>

Example 3-2 Identify and terminate the session on an idle instance

In this example, assume that the running session is `SYSDBA` on the instance `INST_ID=1`. The session on instance `INST_ID=2` is terminated immediately when Oracle Database runs the statement within 60 seconds.

    SQL> SELECT SID, SERIAL#, INST_ID FROM GV$SESSION WHERE USERNAME='SCOTT';

           SID    SERIAL#    INST_ID
    ---------- ---------- ----------
            80          6          2

    SQL> ALTER SYSTEM KILL SESSION '80, 6, @2';

    System altered.

    SQL>

Example 3-3 Using the IMMEDIATE parameter

The following example includes the optional `IMMEDIATE` clause to immediately terminate the session without waiting for outstanding activity to complete.

    SQL> SELECT SID, SERIAL#, INST_ID FROM GV$SESSION WHERE USERNAME='SCOTT';

           SID    SERIAL#    INST_ID
    ---------- ---------- ----------
            80          8          2

    SQL> ALTER SYSTEM KILL SESSION '80, 8, @2' IMMEDIATE;

    System altered.

    SQL>

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md)
- [Oracle Database 2 Day + Performance Tuning Guide](../tdppt/monitoring-real-time-database-performance.md)
- [About Application Continuity](ensuring-application-continuity.md)

### Overview of Initialization Parameter Files in Oracle RAC

The initialization parameters for an Oracle RAC database are stored in a SPFILE.

When you create the database, Oracle Database creates an SPFILE in the file location that you specify. This location can be either an Oracle Automatic Storage Management (Oracle ASM) disk group or a [cluster file system](glossary.md). If you manually create your database, then Oracle recommends that you create an SPFILE from an initialization parameter file (PFILE).

**Note:**

Oracle RAC uses a traditional PFILE only if an SPFILE does not exist or if you specify `PFILE` in your `STARTUP` command. Oracle recommends that you use an SPFILE to simplify administration, to maintain parameter setting consistency, and to guarantee parameter setting persistence across database shutdown and startup events. In addition, you can configure Oracle Recovery Manager (RMAN) to back up your SPFILE.

All instances in the cluster database use the same SPFILE at startup. Because the SPFILE is a binary file, do not directly edit the SPFILE with an editor. Instead, change SPFILE parameter settings using Oracle Enterprise Manager or `ALTER SYSTEM` SQL statements.

#### Setting SPFILE Parameter Values for Oracle RAC

You can change SPFILE settings with Oracle Enterprise Manager or by using the `SET` clause of the `ALTER SYSTEM` statement.

**Note:**

Modifying the SPFILE using tools other than Oracle Enterprise Manager or SQL\*Plus can corrupt the file and prevent database startup. To repair the file, you might be required to create a PFILE and then regenerate the SPFILE.

The examples in this section appear in ASCII text although the SPFILE is a binary file. Assume that you start an instance with an SPFILE containing the following entries:

    *.OPEN_CURSORS=500
    prod1.OPEN_CURSORS=1000

The value before the period (.) in an SPFILE entry identifies the instance to which the particular parameter value belongs. When an asterisk (\*) precedes the period, the value is applied to all instances that do not have a subsequent, individual value listed in the SPFILE.

For the instance with the Oracle system identifier (SID) `prod1`, the `OPEN_CURSORS` parameter is set to `1000` even though it has a database-wide setting of `500`. Parameter file entries that have the asterisk (\*) wildcard character only affect the instances without an instance-specific entry. This gives you control over parameter settings for instance `prod1`. These two types of settings can appear in any order in the parameter file.

If another DBA runs the following statement, then Oracle Database updates the setting on all instances except the instance with SID `prod1`:

    ALTER SYSTEM SET OPEN_CURSORS=1500 sid='*' SCOPE=SPFILE;

The SPFILE now has the following entries for `OPEN_CURSORS`:

    *.OPEN_CURSORS=1500
    prod1.OPEN_CURSORS=1000

Run the following statement to reset `OPEN_CURSORS` to its default value for all instances except `prod1`:

    ALTER SYSTEM RESET OPEN_CURSORS SCOPE=SPFILE;

The SPFILE now has only the following entry for `prod1`:

    prod1.OPEN_CURSORS=1000

Run the following statement to reset the `OPEN_CURSORS` parameter to its default value for instance `prod1` only:

    ALTER SYSTEM RESET OPEN_CURSORS SCOPE=SPFILE SID='prod1';

#### Parameter File Search Order in Oracle RAC

Oracle Database searches for your parameter file in a particular order depending on your platform. For Oracle RAC databases, you can easily determine the location of the parameter file by using the `srvctl config database` command.

On Linux and UNIX platforms, the search order is as follows:

1.  `$ORACLE_HOME/dbs/spfile``sid``.ora`

2.  `$ORACLE_HOME/dbs/spfile.ora`

3.  `$ORACLE_HOME/dbs/init``sid``.ora`

On Windows platforms, the search order is as follows:

1.  `%ORACLE_HOME%\database\spfile``sid``.ora`

2.  `%ORACLE_HOME%\database\spfile.ora`

3.  `%ORACLE_HOME%\database\init``sid``.ora`

**Note:**

Oracle recommends that you do not use the default SPFILE names because all instances must use the same file and they all have different SIDs. Instead, store the SPFILE on Oracle ASM. If you store the SPFILE on a cluster file system, then use the following naming convention for the SPFILE: `$ORACLE_HOME/dbs/spfile``db_unique_name``.ora`. Create a PFILE named `$ORACLE_HOME/dbs/init``sid``.ora` that contains the name `SPFILE=``ORACLE_HOME``/dbs/spfile``db_unique_name``.ora`.

**Related Topics**

- [srvctl config database](server-control-utility-reference.md)

#### Backing Up the Server Parameter File

Oracle recommends that you regularly back up the server parameter file for recovery purposes.

Do this using Oracle Enterprise Manager or use the `CREATE PFILE` statement. For example:

    CREATE PFILE='/u01/oracle/dbs/test_init.ora'
    FROM SPFILE='/u01/oracle/dbs/test_spfile.ora';

You can use Recovery Manager (RMAN) to create backups of the server parameter file. You can also recover an SPFILE by starting an instance using a client-side initialization parameter file. Then re-create the server parameter file using the `CREATE SPFILE` statement. Note that if the parameter file that you use for this operation was for a single instance, then the parameter file does not contain instance-specific values, even those that must be unique in Oracle RAC instances. Therefore, ensure that your parameter file contains the appropriate settings as described earlier in this chapter.

To ensure that your SPFILE (and control files) are automatically backed up by RMAN during typical backup operations, use Oracle Enterprise Manager or the RMAN `CONTROLFILE AUTOBACKUP` statement to enable the RMAN autobackup feature

**Related Topics**

- [CREATE SPFILE](../sqlrf/CREATE-SPFILE.md)
- [Oracle Database Backup and Recovery Reference](../rcmrf/rman-commands-at-sign-to-quit.md)

### Initialization Parameter Use in Oracle RAC

By default, most parameters are set to a default value and this value is the same across all instances.

However, many initialization parameters can also have different values on different instances as described in Table 3-3. Other parameters must either be unique or identical as described in the following sections

- Parameters That Must Have Identical Settings on All Instances

- Parameters That Have Unique Settings on All Instances

- Parameters That Should Have Identical Settings on All Instances

Table 3-3 summarizes the initialization parameters used specifically for Oracle RAC databases.

Table 3-3 Initialization Parameters Specific to Oracle RAC

| Parameter                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [`ACTIVE_INSTANCE_COUNT`](../refrn/ACTIVE_INSTANCE_COUNT.md)                         | This initialization parameter was deprecated in Oracle RAC 11g release 2 (11.2). Instead, use a service with one preferred and one available instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [`ASM_PREFERRED_READ_FAILURE_GROUPS`](../refrn/ASM_PREFERRED_READ_FAILURE_GROUPS.md) | Specifies a set of disks to be the preferred disks from which to read mirror data copies. The values you set for this parameter are instance specific and need not be the same on all instances.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [`CLUSTER_DATABASE`](../refrn/CLUSTER_DATABASE.md)                                   | Enables a database to be started in cluster mode. Set this parameter to `TRUE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [`CLUSTER_DATABASE_INSTANCES`](../refrn/CLUSTER_DATABASE_INSTANCES.md)               | Oracle RAC uses this parameter to allocate adequate memory resources. It must be set to the same value on all instances.<br>• For policy-managed databases, Oracle internally sets this parameter to 16<br>• For administrator-managed databases, Oracle internally sets it to the number of configured Oracle RAC instances<br>You can set this parameter to a value that is greater than the current number of instances, if you are planning to add instances. For policy-managed databases, you should set this parameter to a higher value only if you intend to run a database with more than 16 instances. In this case, set the parameter to the expected maximum number of instances on which this database will run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [`CLUSTER_INTERCONNECTS`](../refrn/CLUSTER_INTERCONNECTS.md)                         | Specifies an alternative cluster interconnect for the private network when there are multiple interconnects.<br>Notes:<br>• Oracle recommends that all Oracle databases and Oracle Clusterware use the same interconnect network.<br>• Oracle does not recommend setting the `CLUSTER_INTERCONNECTS` parameter except in certain situations. See "Administering Multiple Cluster Interconnects on Linux and UNIX Platforms" for more details.<br>• This parameter is stored in the Grid Plug and Play profile in a Grid Plug and Play environment.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [`DB_NAME`](../refrn/DB_NAME.md)                                                     | If you set a value for `DB_NAME` in instance-specific parameter files, the setting must be identical for all instances.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [`DISPATCHERS`](../refrn/DISPATCHERS.md)                                             | Set the `DISPATCHERS` parameter to enable a shared server configuration, that is a server that is configured to enable many user processes to share very few server processes. With shared server configurations, many user processes connect to a dispatcher. The `DISPATCHERS` parameter may contain many attributes.<br>Oracle recommends that you configure at least the `PROTOCOL` and `LISTENER` attributes. `PROTOCOL` specifies the network protocol for which the dispatcher process generates a listening end point. `LISTENER` specifies an alias name for the Oracle Net Services listeners. Set the alias to a name that is resolved through a naming method such as a `tnsnames.ora` file. The `tnsnames.ora` file contains net service names. Clients, nodes, and the Oracle Performance Manager node need this file. Oracle Enterprise Manager does not require `tnsnames.ora` entries on the client for Cloud Control.<br>See Also: [Oracle Database Net Services Administrator's Guide](../netag/configuring-shared-server-architecture.md) for complete information about configuring the `DISPATCHERS` parameter and its attributes and for configuring the shared server                                                                              |
| [`GCS_SERVER_PROCESSES`](../refrn/GCS_SERVER_PROCESSES.md)                           | This static parameter specifies the initial number of server processes for an Oracle RAC instance's Global Cache Service (GCS). The GCS processes manage the routing of inter-instance traffic among Oracle RAC instances. The default number of GCS server processes is calculated based on system resources with a minimum setting of 2. For systems with one CPU, there is one GCS server process. For systems with two to eight CPUs, there are two GCS server processes. For systems with more than eight CPUs, the number of GCS server processes equals the number of CPUs divided by 4, dropping any fractions. For example, if you have 10 CPUs, then 10 divided by 4 means that your system has 2 GCS processes. You can set this parameter to different values on different instances.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [`INSTANCE_NAME`](../refrn/INSTANCE_NAME.md)                                         | Specifies the unique name of an instance. Clients can use this name to force their session to be connected to a specific instance in the cluster. The format of the `INSTANCE_NAME` parameter is generally `db_unique_name_instance_number`, such as `orcldb_2`.<br>Note: In Grid Plug and Play environments, the `INSTANCE_NAME` parameter is not required and defaults to `db_unique_name_instance_number` if not specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [`RESULT_CACHE_MAX_SIZE`](../refrn/RESULT_CACHE_MAX_SIZE.md)                         | In a clustered database, you can either set `RESULT_CACHE_MAX_SIZE=0` on every instance to disable the [result cache](glossary.md), or use a nonzero value on every instance to enable the result cache. To switch between enabled and disabled result cache requires that you restart every instance:<br>• Enabling the result cache: Set `RESULT_CACHE_MAX_SIZE` to a value greater than `0`, or leave the parameter unset. You can size the cache differently on individual instances.<br>• Disabling the result cache: Set `RESULT_CACHE_MAX_SIZE=0` on all instances to disable the result cache. If you set `RESULT_CACHE_MAX_SIZE=0` upon startup of any one instance, then you must set the parameter to zero on all instance startups because disabling the result cache must done clusterwide. Disabling the result cache on some instances may lead to incorrect results.<br>If you do not set the `RESULT_CACHE_MAX_SIZE` parameter, the parameter resolves to a default, nonzero value.                                                                                                                                                                                                                                                                       |
| [`SERVICE_NAMES`](../refrn/SERVICE_NAMES.md)                                         | When you use services, Oracle recommends that you do not set a value for the `SERVICE_NAMES` parameter but instead you should create cluster managed services through the Cluster Managed Services page in Oracle Enterprise Manager Cloud Control. This is because Oracle Clusterware controls the setting for this parameter for the services that you create and for the default database service. The service features described in [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md) are not directly related to the features that Oracle provides when you set `SERVICE_NAMES`. In addition, setting a value for this parameter may override some benefits of using services.<br>Note: Oracle recommends that client connections use services rather than instance names. Entries in the `SERVICE_NAMES` parameter may be used by client connections rather than the `INSTANCE_NAME` parameter value. The `SERVICE_NAMES` parameter may include one or more names and different instances may share one or more names with other instances, enabling a client to connect to either a specific instance or to any one of a set of instances, depending on the service name chosen in the connection string. |
| [`SPFILE`](../refrn/SPFILE.md)                                                       | When you use an SPFILE, all Oracle RAC database instances must use the SPFILE and the file must be on shared storage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [`THREAD`](../refrn/THREAD.md)                                                       | Specifies the number of the redo threads to be used by an instance. You can specify any available redo thread number if that thread number is enabled and is not used. If specified, this parameter must have unique values on all instances. The best practice is to use the `INSTANCE_NAME` parameter to specify redo log groups.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

**Related Topics**

- [Oracle Database Reference](../refrn/initialization-parameters-2.md)

#### Parameters That Must Have Identical Settings on All Instances

Certain parameters that are critical at database creation or that affect certain database operations must have the same value for every instance in an Oracle RAC database.

Specify these initialization parameter values in the SPFILE or in the individual PFILEs for each instance. The following list contains the parameters that must be identical on every instance:

- [`COMPATIBLE`](../refrn/COMPATIBLE.md)
- [`CLUSTER_DATABASE`](../refrn/CLUSTER_DATABASE.md)
- [`CONTROL_FILES`](../refrn/CONTROL_FILES.md)
- [`DB_BLOCK_SIZE`](../refrn/DB_BLOCK_SIZE.md)
- [`DB_DOMAIN`](../refrn/DB_DOMAIN.md)
- [`DB_FILES`](../refrn/DB_FILES.md)
- [`DB_NAME`](../refrn/DB_NAME.md)
- [`DB_RECOVERY_FILE_DEST`](../refrn/DB_RECOVERY_FILE_DEST.md)
- [`DB_RECOVERY_FILE_DEST_SIZE`](../refrn/DB_RECOVERY_FILE_DEST_SIZE.md)
- [`DB_UNIQUE_NAME`](../refrn/DB_UNIQUE_NAME.md)
- [`INSTANCE_TYPE`](../refrn/INSTANCE_TYPE.md) (RDBMS or ASM)
- [`PARALLEL_EXECUTION_MESSAGE_SIZE`](../refrn/PARALLEL_EXECUTION_MESSAGE_SIZE.md)
- [`REMOTE_LOGIN_PASSWORDFILE`](../refrn/REMOTE_LOGIN_PASSWORDFILE.md)
- [`UNDO_MANAGEMENT`](../refrn/UNDO_MANAGEMENT.md)

The following parameters must be identical on every instance only if the parameter value is set to zero:

- `DML_LOCKS`
- `RESULT_CACHE_MAX_SIZE`

#### Parameters That Have Unique Settings on All Instances

Certain parameters are unique to each instance, such as the `INSTANCE_NUMBER` parameter.

Starting with Oracle Grid Infrastructure 21c, policy-managed databases are deprecated.

When it is necessary to set parameters that have unique settings on a policy-managed database, you can ensure that instances always use the same name on particular nodes by running the `srvctl modify instance -n ``node_name`` -i ``instance_name` command for each server that can be assigned to the database's server pool. Then a unique value of the parameter can be specified for `instance_name` that is used whenever the database runs on `node_name`.

Specify the `ORACLE_SID` environment variable, which consists of the database name and the number of the `INSTANCE_NAME` assigned to the instance.

Use the `CLUSTER_INTERCONNECTS` initialization parameter to specify an alternative interconnect to the one Oracle Clusterware is using for the private network. Each instance of the Oracle RAC database gets a unique value when setting the `CLUSTER_INTERCONNECTS` initialization parameter.

Oracle Database uses the `INSTANCE_NUMBER` parameter to distinguish among instances at startup and the `INSTANCE_NAME` parameter to assign redo log groups to specific instances. The instance name can take the form `db_unique_name_instance_number` and when it has this form of name and number separated by an underscore, the number after the underscore is used as the `INSTANCE_NUMBER`. With Oracle Database 11.2 using Grid Plug and Play, you no longer have to explicitly assign instance numbers for policy-managed databases and the instance name defaults to `db_unique_name_instance_number`, where Oracle Database assigns the instance number.

When you specify `UNDO_TABLESPACE` with automatic undo management enabled, then set this parameter to a unique undo tablespace name for each instance.

If you use the `ROLLBACK_SEGMENTS` parameters, then Oracle recommends setting unique values for it by using the `SID` identifier in the SPFILE. However, you must set a unique value for `INSTANCE_NUMBER` for each instance and you cannot use a default value.

Using the `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter, you can specify a list of preferred read failure group names. The disks in those failure groups become the preferred read disks. Thus, every node can read from its local disks. This results in higher efficiency and performance and reduced network traffic. The setting for this parameter is instance-specific, and the values need not be the same on all instances.

**Related Topics**

- Administering Multiple Cluster Interconnects on Linux and UNIX Platforms

#### Parameters That Should Have Identical Settings on All Instances

Oracle recommends that the parameters listed here have identical settings on all instances.

Oracle recommends that you set the values for the parameters in Table 3-4 to the same value on all instances. Although you can have different settings for these parameters on different instances, setting each parameter to the same value on all instances simplifies administration.

Table 3-4 Parameters That Should Have Identical Settings on All Instances

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ARCHIVE_LAG_TARGET`         | Different values for instances in your Oracle RAC database are likely to increase overhead because of additional automatic synchronization performed by the database processing.<br>When using either Oracle GoldenGate downstream capture or Oracle GoldenGate integrated capture mode in a downstream capture configuration with your Oracle RAC database, the value must be greater than zero.                                                                                                                                                                                                                                |
| `CLUSTER_DATABASE_INSTANCES` | While it is preferable for this parameter to have identical settings across all Oracle RAC database instances, it is not required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `LICENSE_MAX_USERS`          | Because this parameter determines a database-wide limit on the number of users defined in the database, it is useful to have the same value on all instances of your database so you can see the current value no matter which instance you are using. Setting different values may cause Oracle Database to generate additional warning messages during instance startup, or cause commands related to database user management to fail on some instances.                                                                                                                                                                      |
| `LOG_ARCHIVE_FORMAT`         | If you do not use the same value for all your instances, then you unnecessarily complicate media recovery. The recovering instance expects the required archive log file names to have the format defined by its own value of `LOG_ARCHIVE_FORMAT`, regardless of which instance created the archive log files.<br>Databases that support Oracle Data Guard, either to send or receive archived redo log files, must use the same value of `LOG_ARCHIVE_FORMAT` for all instances.                                                                                                                                               |
| `SPFILE`                     | If this parameter does not identify the same file to all instances, then each instance may behave differently and unpredictably in fail over, load-balancing, and during normal operations. Additionally, a change you make to the SPFILE with an `ALTER SYSTEM SET` or `ALTER SYSTEM RESET` command is saved only in the SPFILE used by the instance where you run the command. Your change is not reflected in instances using different SPFILEs.<br>If the SPFILE values are different in instances for which the values were set by the server, then you should restart the instances that are not using the default SPFILE. |
| `TRACE_ENABLED`              | If you want diagnostic trace information to be always available for your Oracle RAC database, you must set `TRACE_ENABLED` to `TRUE` on all of your database instances. If you trace on only some of your instances, then diagnostic information might not be available when required should the only accessible instances be those with `TRACE_ENABLED` set to `FALSE`.                                                                                                                                                                                                                                                         |
| `UNDO_RETENTION`             | By setting different values for `UNDO_RETENTION` in each instance, you are likely to reduce scalability and encounter unpredictable behavior following a failover. Therefore, you should carefully consider whether there are any benefits before you assign different values for this parameter to the instances in your Oracle RAC database.                                                                                                                                                                                                                                                                                   |

### Converting an Administrator-Managed Database to a Policy-Managed Database

You can convert an administrator-managed database to a policy-managed database.

**Note:**

If the administrator-managed database is configured for a low-privileged user and you attempt to convert the database to a policy-managed database, then you must manually add a wallet (if one does not already exist) for this low privileged user, so that a Windows service for Oracle Database can be created.

To convert an administrator-managed database:

1.  Check the current configuration of all services and the database (if you make a mistake and need to recover, then you can know what the configuration looked like when you began), as follows:

        srvctl config database -db db_unique_name
        srvctl config service -db db_unique_name

2.  Create a server pool for the policy-managed database (you must be a cluster administrator to do this), as follows:

        srvctl add srvpool -serverpool server_pool -min 0 -max n

    In the preceding command, 0 is the minimum number of servers you want in the server pool and `n` is the maximum.

    **Note:**

    This step does not necessarily place servers in the newly-created server pool. If there are no servers in the Free pool from which the new server pool can allocate servers, for example, then you may have to use the `srvctl relocate server` command to relocate a server from another server pool once the conversion is complete.

3.  Stop the database using Oracle Enterprise Manager or SRVCTL, as follows:

        srvctl stop database -db db_unique_name

4.  Modify the database to be in the new server pool, as follows:

        srvctl modify database -db db_unique_name -serverpool server_pool

5.  Add a service user to the wallet, as follows:

        crsctl add wallet -type OSUSER -user user_name -passwd

6.  Check the status of the database to confirm that it is now policy managed by repeating the commands in step 1.

Configure Oracle Enterprise Manager to recognize the change you made in the previous procedure, as follows:

1.  In order for Oracle Enterprise Manager Cloud Control to recognize the new database instances, you must change the instance name from `db_unique_name#` to `db_unique_name_#` (notice the additional underscore (\_) before the number sign (#) character).

2.  Rename the `orapwd` file in the `dbs/database` directory (or create a new `orapwd` file by running the `orapwd` command).

    By default, there is an `orapwd` file with the instance name appended to it, such as `orapwdORCL1`. You must change the name of the file to correspond to the instance name you changed in the previous step. For example, you must change `orapwdORCL1` to `orapwdORCL_1` or create a new `orapwd` file.

You cannot directly convert a policy-managed database to an administrator-managed database. Instead, you can remove the policy-managed configuration using the `srvctl remove database` and `srvctl remove service` commands, and then register the same database as an administrator-managed database using the `srvctl add database` and `srvctl add instance` commands. Once you register the database and instance, you must use the `srvctl add service` command to add back the services as you removed them.

Services for administrator-managed databases continue to be defined by the `PREFERRED` and `AVAILABLE` definitions. For policy-managed databases, a service is defined to a database server pool and can either be uniform (running on all instances in the server pool) or singleton (running on only one instance in the server pool). If you change the management policy of the database, then you must recreate the database services to be either uniform/singleton or `PREFERRED`/`AVAILABLE`, depending upon which database management policy you choose.

**Related Topics**

- [Server Control Utility Reference](server-control-utility-reference.md)
- [Service Deployment Options](workload-management-with-dynamic-database-services.md)

### Managing Memory Pressure for Database Servers

Memory Guard detects memory pressure on a server in real time and redirects new sessions to other servers to prevent using all available memory on the stressed server.

Enterprise database servers can use all available memory due to too many open sessions or runaway workloads. Running out of memory can result in failed transactions or, in extreme cases, a restart of the server and the loss of a valuable resource for your applications. Memory Guard detects memory pressure on a server in real time and redirects new sessions to other servers to prevent using all available memory on the stressed server.

Rerouting new sessions to different servers protects the existing workloads on the memory-stressed server and enables the server to remain available. Memory Guard is a feature of Oracle RAC that manages the memory pressure for servers, adding a new resource protection capability in managing service levels for applications hosted on Oracle RAC databases.

When Oracle Database Oracle Database Quality of Service Management is enabled, Cluster Health Monitor sends a metrics stream that provides real-time information about memory resources for the cluster servers to Memory Guard. This information includes the following:

- Amount of available memory
- Amount of memory currently in use

If Memory Guard determines that a node is experiencing memory pressure, then the database services managed by Oracle Clusterware are stopped on that node, preventing new connections from being created. After the memory stress is relieved, the services on that node are restarted automatically, and the listener starts sending new connections to that server. The memory pressure can be relieved in several ways (for example, by closing existing sessions or by user intervention).

### Quiescing Oracle RAC Databases

The procedure for quiescing Oracle RAC databases is identical to quiescing a noncluster database.

You use the `ALTER SYSTEM QUIESCE RESTRICTED` statement from one instance. You cannot open the database from any instance while the database is in the process of being quiesced. When all non-DBA sessions become inactive, the `ALTER SYSTEM QUIESCE RESTRICTED` statement finishes, and the database is considered as in a quiesced state. In an Oracle RAC environment, this statement affects all instances, not only the one from which the statement is issued.

To successfully issue the `ALTER SYSTEM QUIESCE RESTRICTED` statement in an Oracle RAC environment, you must have the Database Resource Manager feature activated, and it must have been activated since instance startup for all instances in the cluster database. It is through the facilities of the Database Resource Manager that non-DBA sessions are prevented from becoming active. Also, while this statement is in effect, any attempt to change the current resource plan is queued until after the system is unquiesced.

These conditions apply to Oracle RAC:

- If you issued the `ALTER SYSTEM QUIESCE RESTRICTED` statement but Oracle Database has not finished processing it, you cannot open the database.

- You cannot open the database if it is in a quiesced state.

- The `ALTER SYSTEM QUIESCE RESTRICTED` and `ALTER SYSTEM UNQUIESCE` statements affect all instances in an Oracle RAC environment, not only the instance that issues the command.

**Note:**

You cannot use the quiesced state to take a cold backup. This is because Oracle Database background processes may still perform updates for Oracle Database internal purposes even while the database is in quiesced state. In addition, the file headers of online data files continue to look like they are being accessed. They do not look the same as if a clean shutdown were done. You can still take online backups while the database is in a quiesced state.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md)
- [ALTER SYSTEM](../sqlrf/ALTER-SYSTEM.md)

### Administering Multiple Cluster Interconnects on Linux and UNIX Platforms

In Oracle RAC environments that run on Linux and UNIX platforms, you can use the `CLUSTER_INTERCONNECTS` initialization parameter to specify an alternative interconnect to the one Oracle Clusterware is using for the private network.

**Note:**

The `CLUSTER_INTERCONNECTS` initialization parameter should not be set to highly available IP (HAIP) addresses provided by Redundant Interconnect Usage. HAIP addresses are recognized automatically.

If you set multiple values for `CLUSTER_INTERCONNECTS`, then Oracle Database uses all of the network interfaces that you specify for the interconnect, providing load balancing if all of the listed interconnects remain operational. You must use identical values, including the order in which the interconnects are listed, on all instances of your database when defining multiple interconnects with this parameter.

**Note:**

Oracle does not recommend setting the `CLUSTER_INTERCONNECTS` initialization parameter, which overrides the default interconnect settings at the operating system level.

Instead, the best practice is to use Redundant Interconnect Usage, available with Oracle Grid Infrastructure 11g release 2 (11.2) for Oracle RAC and Oracle Real Application Clusters One Node 11g release 2 (11.2) databases, and later. For databases that precede Oracle Database 11g release 2 (11.2), use operating system-based network bonding technologies to enable high availability (and load balancing) for network interface cards meant to be used as the cluster interconnect. If you want to use multiple database versions in one cluster, you can combine both techniques. Redundant Interconnect Usage will use the interfaces as presented on the operating system level, regardless of bonding. For more information regarding bonding technologies contact your operating system vendor.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

#### Use Cases for Setting the CLUSTER_INTERCONNECTS Parameter

The `CLUSTER_INTERCONNECTS` initialization parameter requires an IP address. It enables you to specify multiple IP addresses, separated by colons. Oracle RAC network traffic is distributed between the specified IP addresses.

**Note:**

- Oracle does not recommend setting the `CLUSTER_INTERCONNECTS` parameter when using a policy-managed database.

- Oracle recommends that all databases and Oracle Clusterware use the same interconnect network.

Typically, you set the `CLUSTER_INTERCONNECTS` parameter only in the following situations:

- The cluster is running multiple databases and you need the interconnect traffic to be separated and you do not use Redundant Interconnect Usage.

- You have a single IP address that is made highly available by the operating system, and it does not have a stable interface name (for example, the name can change when you restart).

Do not set the `CLUSTER_INTERCONNECTS` parameter for the following common configurations:

- If you want to use Redundant Interconnect Usage.

- If you have only one cluster interconnect.

- If the default cluster interconnect meets the bandwidth requirements of your Oracle RAC database, which is typically the case.

Consider the following important points when specifying the `CLUSTER_INTERCONNECTS` initialization parameter:

- The `CLUSTER_INTERCONNECTS` initialization parameter is useful only in Linux and UNIX environments where UDP IPC is enabled.

- Specify a different value for each instance of the Oracle RAC database when setting the `CLUSTER_INTERCONNECTS` initialization parameter in the parameter file.

- The IP addresses you specify for the different instances of the same database on different nodes must belong to network adapters that connect to the same interconnect network.

- If you specify multiple IP addresses for this parameter, then list them in the same order for all instances of the same database. For example, if the parameter for the first instance on `node1` lists the IP addresses of the `alt0:`, `fta0:`, and `ics0:` devices in that order, then the parameter for the second instance on `node2` must list the IP addresses of the equivalent network adapters in the same order.

- If an operating system error occurs while Oracle Database is writing to the interconnect that you specify with the `CLUSTER_INTERCONNECTS` parameter, then Oracle Database returns an error even if some other interfaces are available. This is because the communication protocols between Oracle Database and the interconnect can vary greatly depending on your platform. See your Oracle Database platform-specific documentation for more information.

##### Example

Consider setting `CLUSTER_INTERCONNECTS` when a single cluster interconnect cannot meet your bandwidth requirements. You may need to set this parameter in data warehouse environments with high interconnect bandwidth demands from one or more databases that cannot use Redundant Interconnect Usage.

For example, if you have two databases with high interconnect bandwidth requirements, then you can override the default interconnect provided by your operating system and nominate a different interconnect for each database using the following syntax in each server parameter file where `ip``n` is an IP address in standard dot-decimal format, for example: `144.25.16.214`:

    Database One: crm1.CLUSTER_INTERCONNECTS = ip1
    Database Two: ext1.CLUSTER_INTERCONNECTS = ip2

If you have one database with high bandwidth demands, then you can nominate multiple interconnects using the following syntax:

    CLUSTER_INTERCONNECTS = ip1:ip2:...:ipn

**Related Topics**

- [Oracle Database Reference](../refrn/CLUSTER_INTERCONNECTS.md)

### Customizing How Oracle Clusterware Manages Oracle RAC Databases

Use these examples to minimize Oracle Clusterware control over Oracle RAC databases, which you may need to do during upgrades.

By default, Oracle Clusterware controls database restarts in Oracle RAC environments. In some cases, you may need to minimize the level of control that Oracle Clusterware has over your Oracle RAC database, for example, during database upgrades.

**Note:**

When using third-party clusterware, Oracle recommends that you use Oracle Clusterware to manage the Oracle RAC instances. If you set the instance to manual and start it with third-party clusterware, then do not use the third-party clusterware to monitor and restart database instances because Oracle Clusterware must do that.

To prevent Oracle Clusterware from restarting your Oracle RAC database when you restart your system, or to avoid restarting failed instances more than once, configure a management policy to define the degree of control. There are two management policies: AUTOMATIC, which is the default, and MANUAL. If the management policy is set to AUTOMATIC, the database is automatically restored to its previous running condition (started or stopped) upon restart of the database host computer. If MANUAL, the database is never automatically restarted upon restart of the database host computer. A MANUAL setting does not prevent Oracle Restart from monitoring the database while it is running and restarting it if a failure occurs.

Use SRVCTL commands to display and change the Oracle Clusterware management policies, as shown in the following examples:

#### Example 1: Display the Current Management Policy

Use the following command syntax to display the current management policy where `db_unique_name` is the name of the database for which you want to change management policies:

    srvctl config database -db db_unique_name -all

#### Example 2: Change the Current Management Policy to Another Management Policy

Use the following SRVCTL command syntax to change the current management policy to either AUTOMATIC, MANUAL, or NORESTART:

    srvctl modify database -db db_unique_name -policy [AUTOMATIC | MANUAL | NORESTART]

This command syntax sets the resource attribute of the database resource.

#### Example 3: Specify a Management Policy for a New Database

When you add a new database using the `srvctl add database` command, you can use the `-policy` parameter to specify the management policy as either `AUTOMATIC`, `MANUAL`, or `NORESTART`, as shown in the following example where `db_unique_name` is the name of the database:

    srvctl add database -db db_unique_name -policy [AUTOMATIC | MANUAL | NORESTART]
       -oraclehome $ORACLE_HOME -dbname DATA

This command syntax places the new database under the control of Oracle Clusterware. If you do not provide a management policy option, then Oracle Database uses the default value of `automatic`. After you change the management policy, the Oracle Clusterware resource records the new value for the affected database.

**Related Topics**

- [srvctl config database](server-control-utility-reference.md)
- [srvctl modify database](server-control-utility-reference.md)
- [srvctl add database](server-control-utility-reference.md)

### Advanced Oracle Enterprise Manager Administration

You can install, configure, and monitor an Oracle RAC database from a single location using Oracle Enterprise Manager Cloud Control.

This section provides advanced administration tasks that are not covered inOracle Database 2 Day + Real Application Clusters Guide or in "Overview of Monitoring and Tuning Oracle RAC Databases".

This section includes the following topics:

- Using Oracle Enterprise Manager Cloud Control to Discover Nodes and Instances

- Other Oracle Enterprise Manager Capabilities

- Administering Jobs and Alerts in Oracle RAC

#### Using Oracle Enterprise Manager Cloud Control to Discover Nodes and Instances

Discovering Oracle RAC database and instance targets in Oracle Enterprise Manager enables monitoring and administration.

Oracle Enterprise Manager Cloud Control enables you to use the Oracle Enterprise Manager console interface to discover Oracle Real Application Clusters (Oracle RAC) database and instance targets.

If the Oracle Enterprise Manager Cloud Control agents are installed on a cluster that has an Oracle RAC database, then Oracle RAC database targets are discovered at install time. You can use the console interface to discover targets if a database is created after agents are installed or if a database is not automatically discovered at agent install time.

To discover nodes and instances, use Oracle Enterprise Manager Cloud Control as follows:

1.  Log in to Oracle Enterprise Manager and click the Targets tab.

2.  Click the Database tab to view all of the available targets. The column labeled Types shows the Oracle RAC databases using the entry Cluster Database.

3.  Add the database target by selecting the target name, then clicking Add. The Add Database Target: Specify Host page appears, which enables you to add databases, listeners, and Oracle Automatic Storage Management (Oracle ASM) as monitored targets.

4.  Click the flashlight icon to display the available host names, select a host, then click Continue. The Add Database: Specify Source page appears.

5.  Either request Oracle Enterprise Managerr to discover only noncluster databases and listeners, or to discover all cluster databases, noncluster databases, and listeners on the cluster, then click Continue.

6.  If this procedure did not discover your reconfigured cluster database and all of its instances, you can use the Targets Discovered on Cluster page to manually configure your cluster database and noncluster databases.

#### Other Oracle Enterprise Manager Capabilities

Oracle Enterprise Manager provides a variety of administrative capabilities starting with Oracle Enterprise Manager 12c.

- The Oracle Grid Infrastructure/Oracle RAC Provisioning deployment procedure provisions Oracle RAC 12c and Oracle Grid Infrastructure. This procedure also has a feature called Profiles, which enables you to record the inputs and subsequently use them for repeated deployments.

- Dynamic prerequisites for the new procedures enable Oracle Enterprise Manager, when connected to My Oracle Support, to download the latest prerequisites and tools for Oracle RAC provisioning.

- The existing One-Click Extend Cluster Database capability now supports Oracle RAC 12c stack.

- The existing Delete/Scale down Oracle Real Application Clusters capability is certified with Oracle RAC 12c clusters.

- The existing Oracle Database Provisioning procedure now supports provisioning of single instances of Oracle Database 12c.

- A new deployment procedure—Oracle Grid Infrastructure Provisioning for Standalone Servers—has been introduced to provision Oracle Grid Infrastructure 12c for noncluster databases.

#### Administering Jobs and Alerts in Oracle RAC

You can use the Administration tab in Oracle Enterprise Manager for an Oracle RAC database.

The Cluster Database Home page shows all of the instances in the Oracle Real Application Clusters (Oracle RAC) database and provides an aggregate collection of several statistics specific to Oracle RAC that are collected by the Automatic Workload Repository (AWR) for server manageability.

You do not need to navigate to an instance-specific page to see these details. However, on the Cluster Database Home page, if an instance is down that should be operating, or if an instance has a high number of alerts, then you can drill down to the instance-specific page for each alert.

To perform specific administrative tasks as described in the remainder of this section, log in to the target Oracle RAC database, navigate to the Cluster Database Home page, and click the Administration tab.

##### Administering Jobs in Oracle RAC

You can administer Oracle Enterprise Manager jobs at both the database and instance levels.

For example, you can create a job at the cluster database level to run on any active instance of the target Oracle Real Application Clusters (Oracle RAC) database. Or you can create a job at the instance level to run on the specific instance for which you created it. If there is a failure, then recurring jobs can run on a remaining instance.

Because you can create jobs at the instance level, cluster level, or cluster database level, jobs can run on any available host in the cluster database. This applies to scheduled jobs as well. Oracle Enterprise Manager also displays job activity in several categories, including, `Active`, `History`, and `Library`.

Use the Jobs tab to submit operating system scripts and SQL scripts and to examine scheduled jobs. For example, to create a backup job for a specific Oracle RAC database:

1.  Click Targets and click the database for which you want to create the job.

2.  Log in to the target database.

3.  When Oracle Enterprise Manager displays the Database Home page, click Maintenance.

4.  Complete the Enterprise Manage Job Wizard pages to create the job.

##### Administering Alerts in Oracle RAC with Oracle Enterprise Manager

You can use Oracle Enterprise Manager to configure Oracle RAC environment alerts.

You can also configure special Oracle RAC database tests, such as global cache converts, consistent read requests, and so on.

Oracle Enterprise Manager distinguishes between database- and instance-level alerts in Oracle RAC environments. Alert thresholds for instance-level alerts, such as archive log alerts, can be set at the instance target level. This function enables you to receive alerts for the specific instance if performance exceeds your threshold. You can also configure alerts at the database level, such as setting alerts for tablespaces, to avoid receiving duplicate alerts at each instance.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md)

**See Also:**

Oracle Technology Network for an example of configuring alerts in Oracle RAC, and Oracle Database PL/SQL Packages and Types Reference for information about using packages to configure thresholds

##### Using Defined Suspensions in Oracle Enterprise Manager

You can define suspensions (which are time periods in which database monitoring is suspended so that maintenance operations do not skew monitoring data or generate needless alerts) for all managed targets of an Oracle Real Application Clusters (Oracle RAC) database.

Defining suspensions prevents alerts from occurring while performing maintenance. You can define suspensions for an entire cluster database or for specific cluster database instances.
