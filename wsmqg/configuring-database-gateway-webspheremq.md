After installing Oracle Database Gateway for WebSphere MQ, follow the instructions in the following topics to configure the gateway.

### Configuration Overview

The gateway works with several components and products to communicate between the Oracle database and WebSphere MQ queues.

For example:

- Oracle Net

  The gateway and the Oracle database communicate using Oracle Net in a server-to-server manner. You must configure both, the gateway and Oracle database to have Oracle Net communication enabled, by configuring the `tnsnames.ora` and `listener.ora` files.

- Gateway initialization files and parameters

  The gateway has initialization files and parameters that you must customize for your installation. For example, you must choose your gateway system identifier (SID), and provide other information, such as the gateway log file destination.

### Configuring the Gateway

The gateway is installed and preconfigured using default values for the gateway SID, directory names, file names, and gateway parameter settings.

The default SID values are:

- `dg4mqs`

  This is the default SID that is used when the gateway resides on the same system as the WebSphere MQ software.

- `dg4mqc`

  This is the default SID that is used when the gateway resides on a different system than the WebSphere MQ software. In this case, the gateway functions as a remote WebSphere MQ client.

A basic gateway initialization file is also installed, and values in this file are set based on the information you entered during the installation phase.

#### Using the Gateway with the Default Values

If you are configuring one gateway instance, and if you have no need to change any of the default values, then most of the gateway configuration process is completed by Oracle Universal Installer.

In this case, perform the following actions:

1.  Skip all steps under "Changing Default Values".

2.  Skip "Step 1: Configure the Oracle Net Oracle Net Listener for the Gateway"

3.  Begin with "Step 2: Stop and Start the Oracle Net Listener for the Gateway", and continue to the end of the chapter.

#### Using the Gateway Without the Default Values

This topic explains how to modify the default values.

If multiple instances of the gateway are being configured, or to modify the default values set during the installation phases, then begin with the steps under "Changing Default Values" and continue to the end of the chapter.

#### Changing Default Values

When changing default values, choose a gateway SID and customize the gateway initialization file.

##### Step 1: Choose a System ID for the Gateway

The gateway SID is a string of 1 to 64 alphanumeric characters that identifies a gateway instance. The SID is used in the gateway boot file and as part of the file name for the gateway parameter file.

Choose a SID different from the default SID and different from `dg4mqs` and `dg4mqc`.

You need a distinct gateway instance, and SID, for each queue manager you want to access. If you want to access two different queue managers, then you need two gateway SIDs, one for each instance of the gateway. If you have one queue manager and want to access it sometimes with one set of gateway parameter settings and at other times with different gateway parameter settings, then you can do this by having multiple gateway SIDs for one queue manager.

##### Step 2: Customize the Gateway Initialization File

This topic explains how to customize the gateway initialization file.

The gateway initialization file (`init``sid``.ora`) supports all database gateway initialization parameters described in [Gateway Initialization Parameters](database-gateway-webspheremq-initialization-parameters.md). The initialization file must be available when the gateway is started.

During installation, a default initialization file is created in `ORACLE_HOME\dg4mq\admin\init``sid``.ora` on Microsoft Windows and ` $``ORACLE_HOME/dg4mq/admin/init``sid.``ora`, on UNIX based systems where `sid` is the default SID of `dg4mqs` or `dg4mqc`. If you chose an SID other than the default, then rename this file using the SID you chose in Step 1: Choose a System ID for the Gateway. Customize the default initialization file as necessary.

The following entries might appear in an initialization file:

    LOG_DESTINATION=log_file
    QUEUE_MANAGER=manager_name
    AUTHORIZATION_MODEL=auth_model
    TRANSACTION_MODEL=tx_model
    TRANSACTION_LOG_QUEUE=tx_queue_name
    TRANSACTION_RECOVERY_USER=rec_user
    TRANSACTION_RECOVERY_PASSWORD=rec_password
    TRACE_LEVEL=0
    MQSERVER=channel
    MQCCSID=character_set

In this file:

- `log_file` specifies the full path name of the gateway log file.

- `manager_name` is the name of the WebSphere MQ queue manager to access.

- `auth_model` is the authorization model to use. The default value is `RELAXED`.

- `tx_model` is the transaction model to use. The default is `SINGLE_SITE`.

- `tx_queue_name` is the name of the queue for logging transaction IDs for distributed transactions. This is used only when `tx_model` is set to `COMMIT_CONFIRM`.

- `rec_user` specifies the user name that the gateway uses to start recovery of a distributed transaction. This is used only when `auth_model` is set to `STRICT` and `tx_model` is set to `COMMIT_CONFIRM`.

- `rec_password` specifies the password of the user name that the gateway uses to start recovery of a distributed transaction.

- `channel` specifies the location of the WebSphere MQ server and the communication method to use. The channel format is:

  `channel_name/connection_type/hostname [(port_number)]`.

  For example:

      MQSERVER=CHAN9/TCP/dolphin(1425)

- `character_set` specifies the coded character set number used by the gateway when communicating with the WebSphere MQ queue manager. This is an optional parameter.

  This parameter is set only if the system that is running the WebSphere MQ queue manager uses a different encoding scheme than the system that runs the gateway. When set, the value of `character_set` is used by the WebSphere MQ client software on the gateway system to convert the data.

Refer to [Gateway Running Environment](database-gateway-webspheremq-running-environment.md) for more information on transaction and security models.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/index.md) and [Oracle Database Net Services Reference](../netrf/index.md)

### Configuring Oracle Net for the Gateway

The gateway requires Oracle Net to provide transparent data access to and from the Oracle database.

Oracle Net uses the Oracle Net Listener to receive incoming connections from an Oracle Net client. In the case of the gateway, the Oracle Net Listener listens for incoming requests from the Oracle database. For the Oracle Net Listener to listen for the gateway, information about the gateway must be added to the Oracle Net Listener configuration file (`listener.ora`). This file is located in the ` ORACLE_HOME``/network/admin` directory on Microsoft Windows and `ORACLE_HOME\network\admin` directory on UNIX based systems by default, where `ORACLE_HOME` is the directory under which the gateway is installed. The default values in this file are set for you during the installation process by Oracle Universal Installer.

#### Using Oracle Net with Default Gateway Values

If you are configuring one gateway instance, and if you do not need to change any of the default values, then no further configuration is necessary for Oracle Net.

Perform only "Step 2: Stop and Start the Oracle Net Listener for the Gateway".

#### Using Oracle Net When Changing the Default Gateway Values

If you intend to use the Oracle Net listener for multiple gateway instances, or if you need to modify some of the default values set during the installation phase, then perform Step 1 and Step 2 in this section.

In Step 1, you add gateway information or change default information in the `listener.ora` file in the gateway directory `ORACLE_HOME\network\admin` on Microsoft Windows and `ORACLE_HOME``/network/admin` on UNIX based systems.

##### Step 1: Configure the Oracle Net Oracle Net Listener for the Gateway

Configuring the `listener.ora` file.

Two entries must be added to the `listener.ora` file:

- A list of Oracle Net addresses for the Oracle Net Listener to listen on

- The gateway process that the Oracle Net Listener should start in response to incoming connection requests

  **Note:**

  The Oracle Net Listener and the gateway must reside on the same node. If you already have a Oracle Net Listener running on the node, then you must make the changes suggested in Step 1 and 2 to your existing `listener.ora` and `tnsnames.ora` files.

  After making the changes, you can reload the changes by running the `reload` subcommand in the `lsnrctl` utility without shutting down the Oracle Net Listener.

##### Specifying Oracle Net Addresses for the Oracle Net Listener

If you are using Oracle Net and the TCP/IP protocol adapter, then the syntax of an entry in the `listener.ora` file is:

    LISTENER=
      (ADDRESS_LIST=
          (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name)
              (PORT=port_number)
           )
      )

In this entry:

- `host_name` is the name of the system where the gateway is installed.

- `port_number` specifies the IP port number used by the Oracle Net Listener. If you have other listeners running on `host_name`, such as the listener of an Oracle database on the same system, then the value of `port_number` must be different from the other listener port numbers.

If you are using Oracle Net and the interprocess socket call (IPC) protocol adapter, the syntax of the entry in `listener.ora` file is:

    LISTENER=
      (ADDRESS_LIST=
         (ADDRESS=
             (PROTOCOL=IPC)
             (KEY=key_name)
         )
       )

In this entry:

- `IPC` specifies that the protocol used for connections is IPC.

- `key_name` is the unique user-defined service name.

##### Entry for the Gateway

To configure the Oracle Net Listener to listen for a gateway instance in incoming connection requests, add an entry to the `listener.ora` file using the following syntax:

    SID_LIST_LISTENER=
       (SID_LIST=
          (SID_DESC=
              (SID_NAME=gateway_sid)
              (ORACLE_HOME=gateway_directory)
              (PROGRAM=driver)
           )
        )

In this entry:

- `gateway_sid` specifies the SID of the gateway and matches the gateway SID specified in the connect descriptor entry in the `tnsnames.ora` file.

- `gateway_directory` specifies the gateway directory in which the gateway software resides.

- `driver` is the name of the gateway executable file. If the gateway uses a local WebSphere MQ server, then the file name is `dg4mqs`. The file name is `dg4mqc` if the gateway is run as a WebSphere MQ client to access a remote WebSphere MQ server.

When you add an entry for multiple gateway instances, add the entry to the existing `SID_LIST` syntax:

    SID_LIST_LISTENER=
     (SID_LIST=
          (SID_DESC=.
                    .
                    .
          )
          (SID_DESC=.
                    .
                    .
          )
          (SID_DESC=
              (SID_NAME=gateway_sid)
              (ORACLE_HOME=gateway_directory)
              (PROGRAM=driver)
           )
      )

The following are examples of entry made to the `listener.ora` file:

For Microsoft Windows:

    (SID_DESC =
             (SID_NAME=dg4mqs)
             (ORACLE_HOME=gateway_directory)
             (PROGRAM=dg4mqs)
    )

For UNIX based systems:

    (SID_DESC =
             (SID_NAME=dg4mqs)
             (ORACLE_HOME=/oracle/app/oracle/product/dg4mq)
             (PROGRAM=dg4mqs)
    )

**Related Topics**

- Configuring Oracle Net for Oracle Database

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/index.md) and [Oracle Database Net Services Reference](../netrf/index.md) for additional information about changing `listener.ora`.

##### Step 2: Stop and Start the Oracle Net Listener for the Gateway

The Oracle Net Listener must be started or reloaded to initiate the new settings.

**Note:**

If you already have a Oracle Net Listener running on the Oracle database where the gateway is installed, then you must change your existing `listener.ora` and `tnsnames.ora` files. After making the changes, you can reload the changes by running the reload subcommand in the `lsnrctl` utility without shutting down the Oracle Net Listener.

Refer to the Note in Step 1: Configure the Oracle Net Oracle Net Listener for the Gateway.

- Set the gateway directory name:

  For Microsoft Windows:

      set TNS_ADMIN=c:\orant\network\admin

  If you are using the Bourne or Korn shell, then enter:

      $ ORACLE_HOME=gateway_directory;export ORACLE_HOME

  If you have the C shell, then enter:

      $ setenv ORACLE_HOME gateway_directory

  In this entry:

  `gateway_directory` specifies the directory where the gateway software is installed.

- If the listener is already running, then use the `lsnrctl` command to reload the listener with the new settings:

  For Microsoft Windows:

      c:\orant\bin> lsnrctl reload your_listener_name

  For UNIX based systems:

      $ cd $ORACLE_HOME/bin
      $ ./lsnrctl reload your_listener_name

  In this entry:

  `ORACLE_HOME `specifies the directory where the gateway software is installed.

- Check the status of the listener with the new settings:

  For Microsoft Windows:

      c:\orant\bin> lsnrctl status your_listener_name

  For UNIX based systems:

      $ ./lsnrctl status listener_name

  The following are examples of the output from a `lsnrctl` status check:

For Microsoft Windows:

    Connecting to (ADDRESS=(PROTOCOL=IPC)(KEY=ORAIPC))
    STATUS of the LISTENER
    ------------------------
    Alias                     LISTENER
    Version                   TNSLSNR for MS Windows: version 12.2.0.1.0 - Beta
    Start Date                14-Sep-16 18:16:10
    Uptime                    0 days 0 hr. 2 min. 19 sec
    Trace Level               off
    Security                  OFF
    SNMP                      OFF
    Listener Parameter File   \oracle\app\oracle\product\dg4mqs\network\admin\listener.ora
    Listener Log File         \oracle\app\oracle\product\dg4mqs\network\log\listener.log
    Services Summary...
      dg4mqs            has 1 service handler(s)
    The command completed successfully

For UNIX based systems:

    Connecting to (ADDRESS=(PROTOCOL=IPC)(KEY=ORAIPC))
    STATUS of the LISTENER
    ------------------------
    Alias                     LISTENER
    Version                   TNSLSNR for Solaris: version 12.2.0.1.0 - Production
    Start Date                14-Sep-16 10:16:10
    Uptime                    0 days 0 hr. 2 min. 19 sec
    Trace Level               off
    Security                  OFF
    SNMP                      OFF
    Listener Parameter File   /oracle/app/oracle/product/dg4mqs/network/admin/listener.ora
    Listener Log File         /oracle/app/oracle/product/dg4mqs/network/log/listener.log
    Services Summary...
      dg4mqs            has 1 service handler(s)
    The command completed successfully

In the example, `dg4mqs` is the default SID value that was assigned during installation. You can use any valid ID for the SID, or keep the default.

**Note:**

You must use the same SID value in the `tnsnames.ora` file, the `listener.ora` file, and the `GATEWAY_SID` environment variable in the gateway initialization file for each gateway instance being configured.

### Configuring Oracle Net for Oracle Database

You must configure the Oracle database so that it can communicate with the gateway by using Oracle Net.

Any Oracle application that has access to an Oracle database can also access WebSphere MQ through the gateway. Before you use the gateway to access WebSphere MQ, you must configure the Oracle database so that it can communicate with the gateway by using Oracle Net. To configure the server, add connect descriptors to the `tnsnames.ora` file.

Any Oracle database that accesses the gateway needs a service name entry or a connect descriptor name entry in the `tnsnames.ora` file on the server, to tell the Oracle database how to make connections. This file, by default, is located in the `ORACLE_HOME``\network\admin` directory on Microsoft Windows and `ORACLE_HOME/network/admin` directory on UNIX based systems, where `ORACLE_HOME` is the directory in which the Oracle database is installed. The `tnsnames.ora` file is required by the Oracle database that is accessing the gateway, and not by the gateway itself.

**Related Topics**

- Configuration Overview
- Configuring the Gateway

**See Also:**

Refer to [Oracle Database Net Services Administrator's Guide](../netag/index.md) and [Oracle Database Net Services Reference](../netrf/index.md) for more information about changing the `tnsnames.ora` file.

#### Using Default Gateway Values

Oracle Universal Installer creates and preconfigures a `tnsnames.ora` file where `ORACLE_HOME` is the directory in which the gateway software is installed.

Oracle Universal Installer creates and preconfigures a `tnsnames.ora` file in the `ORACLE_HOME/network/admin` directory on Microsoft Windows and `ORACLE_HOME/network/admin` directory on UNIX based systems, where `ORACLE_HOME` is the directory in which the gateway software is installed. If you use the default values, and if you do not need to configure additional gateway instances, then you can append the contents of this file to the `tnsnames.ora` file of each Oracle database that accesses the gateway.

#### Changing Default Gateway Values

If you need to change some of the default settings, use the examples in this section to guide you.

##### TCP/IP Example

This is an example of using the TCP/IP protocol adapter.

An Oracle database accesses the gateway using Oracle Net and the TCP/IP protocol adapter. The syntax of the connect descriptor entry in `tnsnames.ora` is:

    tns_name_entry=
      (DESCRIPTION=
         (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name)
              (PORT=port_number)
         )
         (CONNECT_DATA=
         (SID=gateway_sid)
         )
         (HS=OK)
    )

In this example:

- `tns_name_entry` is the `tns_name_entry` of the `CREATE DATABASE LINK` statement.

- `TCP` specifies that the protocol used for connections is TCP/IP.

- `port_number` is the port number used by the Oracle Net Oracle Net Listener that listens for the gateway. This port number can be found in the `listener.ora` file that is used by the Oracle Net Listener.

- `host_name` specifies the system on which the gateway is running. The Oracle Net Listener host name can be found in the `listener.ora` file used by the Oracle Net Listener that is listening for the gateway.

- `gateway_sid` specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that listens for the gateway.

**Related Topics**

- Creating Database Links
- Step 1: Configure the Oracle Net Oracle Net Listener for the Gateway

##### IPC Example

This is an example using the IPC protocol adapter.

An Oracle database accesses the gateway using Oracle Net and the IPC protocol adapter. The syntax of the connect descriptor entry in `tnsnames.ora` is:

    tns_name_entry=
        (DESCRIPTION=
            (ADDRESS=
            (PROTOCOL=IPC)
            (KEY=key_name)
        )
        (CONNECT_DATA=
            (SID=gateway_sid)
        )
         (HS=OK)
      )

where:

- `tns_name_entry` is the `tns_name_entry` of the `CREATE DATABASE LINK` statement.

- `IPC` specifies that the protocol used for connections is IPC.

- `key_name` is the service name.

- `gateway_sid` specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that is listening for the gateway.

**Related Topics**

- Creating Database Links

### Creating a Transaction Log Queue

When the `TRANSACTION_MODEL` parameter in the gateway initialization file is set to `COMMIT_CONFIRM` to allow for distributed transactions, an additional configuration step is required.

This step is required to:

- Create a WebSphere MQ queue

- Set the `TRANSACTION_LOG_QUEUE`, `TRANSACTION_RECOVERY_USER` and `TRANSACTION_RECOVERY_PASSWORD` parameters in the gateway initialization file

**See Also:**

Refer to IBM publications for information about creating and configuring a queue.

For the gateway to recover distributed transactions, a recovery account and queue must be set up in the queue manager by the WebSphere MQ system administrator. This account must be a valid WebSphere MQ user, and it must have authorization to access the recovery queue.

The gateway uses the recovery queue to check the status of failed transactions that were started at the queue manager by the gateway and were logged in this queue. The information in this queue is vital to the recovery process and must not be used, accessed, or updated except by the gateway.

**Related Topics**

- [Commit-Confirm Transactions](database-gateway-webspheremq-running-environment.md)
- [Oracle Database Gateway for WebSphere MQ Initialization Parameters](database-gateway-webspheremq-initialization-parameters.md)
- [Authorization for WebSphere MQ Objects](database-gateway-webspheremq-running-environment.md)

### Administering the Database Links Alias Library

A connection to the gateway is established through a database link when it is first used in an Oracle session.

In this context, connection refers to the connection between the Oracle database and the gateway. The connection persists until the Oracle session ends. Another session or user can access the same database link and get a distinct connection to the gateway and the queue manager.

Database links are active for the duration of a gateway session. To close a database link during a session, use the `ALTER SESSION` statement.

**See Also:**

For more information about using database links, refer to the [Oracle Database Administrator's Guide](../admin/distributed-database-concepts.md).

#### Using Database Links

Oracle Database Gateway for WebSphere MQ uses an alias library to access the shared library installed with Oracle Database Gateway for WebSphere MQ.

An alias library is a schema object that represents a library in PL/SQL. To create the alias library, you must have the `CREATE LIBRARY PRIVILEGE`. The alias library used by Oracle Database Gateway for WebSphere MQ is `libdg4mq` and is defined in the `pgmobj.sql` script, which is created when the Oracle Database Gateway for WebSphere MQ deployment scripts are executed.

#### Creating Database Links

To create a database link, use the `CREATE DATABASE LINK` statement.

The `USING` clause points to a connect descriptor in the `tnsnames.ora` file. The `CONNECT TO` clause specifies the WebSphere MQ user ID and password when the security model is defined as `STRICT` with the `AUTHORIZATION_MODEL` parameter. If you do not include the `CONNECT TO` clause, then the current user ID and password are used.

When the `AUTHORIZATION_MODEL` parameter is set to `RELAXED`, you need not specify an user ID and password because the Oracle database uses the user ID and password of the user account that started the Oracle Net Listener for the gateway. If you specify an user ID and password with the `CONNECT TO` clause, then the Oracle database and gateway ignore those values.

The syntax of `CREATE DATABASE LINK` is as follows:

    CREATE [PUBLIC] DATABASE LINK dblink [CONNECT TO userid IDENTIFIED
                  BY password] USING 'tns_name_entry';

where:

- `dblink` is the database link name.

- `userid` is the user ID used to establish a session at the queue manager. It is only used when `AUTHORIZATION_MODEL` is set to `STRICT` in the `init``sid`.`ora` file. The user ID must be authorized to access all WebSphere MQ objects, and use any database object referenced in the PL/SQL commands.

  The `userid` must be in the password file on the computer on which WebSphere MQ and the gateway are installed. Otherwise, the `userid `must be published in the UNIX Network Information Service (NIS) when WebSphere MQ and the gateway are installed on different systems. If `userid` contains lowercase letters or non-alphanumeric characters, then you must surround `userid` with quotation marks ("). Refer to your WebSphere MQ documentation for more information about `userid`. 

- `password` is the password used to establish a session at the queue manager. It is used only when `AUTHORIZATION_MODEL` is set to `STRICT` in the `init``sid`.`ora` file.

  The `password` must be in the password file on the system on which WebSphere MQ and the gateway are installed. Otherwise, the `password` must be published in the Windows or UNIX Network Information Service (NIS), as the case may be when WebSphere MQ and the gateway are installed on different systems.

  If `password` contains lowercase letters or non alphanumeric characters, then surround `password` with quotation marks (").

- `tns_name_entry` is the Oracle Net TNS connect descriptor name specified in the `tnsnames.ora` file.

**Related Topics**

- [Security Models](database-gateway-webspheremq-running-environment.md)

#### Dropping Database Links

You can drop a database link with the `DROP DATABASE LINK` statement.

For example, to drop the database link named `dblink`, enter:

    DROP [PUBLIC] DATABASE LINK dblink;

A database link should not be dropped if it is required to resolve a distributed transaction that is in doubt.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/DROP-DATABASE-LINK.md) for more information about dropping database links.

#### Examining Available Database Links

The data dictionary of each database stores the definitions of all the database links in that database.

The `USER_DB_LINKS` view shows the database links that are defined for a user. The `ALL_DB_LINKS` data dictionary views show all the defined database links.

#### Limiting the Number of Active Database Links

You can limit the number of connections from a user process to remote databases with the `OPEN_LINKS` parameter.

This parameter controls the number of remote connections that any single user process can use with a single user session.

**See Also:**

[Oracle Database Administrator's Guide](../admin/distributed-database-concepts.md) for more information about limiting the number of active database links.

#### Creating Alias Library

Create the Oracle Database Gateway for WebSphere MQ alias library, `libdg4mq,` using the Oracle Database Gateway for WebSphere MQ deployment scripts.

During installation, the appropriate shared library name is defined in ` ORACLE_HOME\dg4mq\admin\deploy\pgmobj.sql on Microsoft Windows and ` `ORACLE_HOME``/dg4mq/admin/deploy/pgmobj.sql` on UXIX based systems based on the DG4MQ model you choose.

For a remote model, the `libdg4mqc.so` shared library is used. For example:

    CREATE OR REPLACE LIBRARY libdg4mq AS 'ORACLE_HOME/lib/libdg4mqc.so' TRANSACTIONAL;

For a local model, the `libdg4mqs.so` shared library is used. For example:

    CREATE OR REPLACE LIBRARY libdg4mq AS 'ORACLE_HOME/lib/libdg4mqs.so' TRANSACTIONAL;

**Note:**

The file extension of shared libraries on HP-UX is` .sl` . For example, `libdg4mqc.sl`

#### Dropping Alias Library

Use the undeploy scripts to drop the `libdg4mq` Oracle Database Gateway for WebSphere MQ alias library.

### Installing the Oracle Visual Workbench Repository

Install the Oracle Visual Workbench repository following the steps in this section.

You can skip the installation of the Oracle Visual Workbench repository if you do not plan to use Oracle Visual Workbench, or if you are preparing your production Oracle database, where you do not need a Visual Workbench repository, but instead need a Oracle Database Gateway for WebSphere MQ deployment.

**Related Topics**

- Preparing the Production Oracle Database

#### Preinstallation Tasks

These steps describe the preinstallation tasks.

##### Step 1: Choose a Repository Server

This step explains how to choose a repository server.

A repository server is an Oracle database on which the Visual Workbench repository is installed.

##### Step 2: Locate the Installation Scripts

This step explains how to locate the installation scripts.

The Visual Workbench repository installation scripts are installed with the Visual Workbench. If the repository is to be installed on the same system as Oracle Visual Workbench, then your repository server already has all the required installation scripts. Proceed to Step 3.

1.  Create a directory on the repository server to be the script directory. For example:
    For Microsoft Windows:

        > md %ORACLE_HOME%\dg4mqadmin\repo

    For UNIX based systems:

        $ mkdir $ORACLE_HOME/dg4mq/admin/repo
        $ chmod 777 $ORACLE_HOME/dg4mq/admin/repo
2.  Use a file transfer program to transfer the repository zip file (`repos``XXX.``zip`, where `XXX` is the release number), or move all script files with the `.sql` suffix from the script file directory `(ORACLE_HOME\dg4mqvwb\server\admin` on Windows) on the Visual Workbench system to the script file directory on the repository server system.

##### Step 3: Upgrade the Visual Workbench Repository

This step explains how to upgrade your Visual Workbench repository installation scripts.

Upgrade your existing Visual Workbench repository installation scripts by copying the `pgm``xxx`.`sql` files installed with the Oracle Database Gateway for WebSphere MQ in the `ORACLE_HOME\dg4mq\admin\deploy` directory on Microsoft Windows and `ORACLE_HOME/dg4mq/admin/deploy` directory on UNIX based systems to the script file directory on the repository server system.

##### Step 4: Ensure that the UTL_RAW Package is Installed

The step explains how to ensure that the `UTL_RAW` package is installed.

All data mapping packages generated by the Visual Workbench use the `UTL_RAW` package, which provides routines for manipulating raw data.

From SQL\*Plus, as the `SYS` user, issue the following statement:

    SQL> DESCRIBE UTL_RAW

If the `DESCRIBE` statement is successful, then your repository server already has `UTL_RAW` installed, and you can proceed to Step 4.

If the `DESCRIBE` statement fails, then install `UTL_RAW`:

From SQL\*Plus, as the `SYS` user, run the `utlraw.sql` and `prvtrawb.plb` scripts that are in the `ORACLE_HOME\rdbms\admin` directory on Microsoft Windows and `ORACLE_HOME``/rdbms/admin` directory on UNIX based systems. You must run the `utlraw.sql` script first.

    SQL> @utlraw.sql
    SQL> @prvtrawb.plb

##### Step 5: Ensure that the DBMS_OUTPUT Package is Enabled

This step explains how to ensure that the `DBMS_OUTPUT` package is enabled.

The sample programs and installation verification programs on the distribution CD-ROM use the standard `DBMS_OUTPUT` package.

From SQL\*Plus, as `SYS` user, issue the following statement:

    SQL> DESCRIBE DBMS_OUTPUT

If the `DESCRIBE` statement is successful, then your repository server has `DBMS_OUTPUT` installed, and you can proceed to Step 6.

If the `DESCRIBE` statement fails, then install `DBMS_OUTPUT`.

**See Also:**

[Oracle Database Administrator's Guide](../admin/index.md) for more information.

##### Step 6: Create a Database Link

This step explains how to create a database link.

Create a database link on your Oracle Production System Server to access the Oracle Database Gateway for WebSphere MQ.

If you do not already have a database link, then refer to "Administering the Database Links Alias Library" for more information about creating database links.

#### Visual Workbench Repository Installation Tasks

Use `pgvwbrepos.sql` to install the Visual Workbench Repository.

Use `pgvwbrepos.sql` to install the Visual Workbench Repository on Oracle10g or later. To run `pgvwbrepos.sql`, ensure that you are currently in the` ORACLE_HOME\dg4mq\admin\repo` directory on Microsoft Windows and `ORACLE_HOME``/dg4mq/admin/repo` directory on UNIX based systems, and then enter the following command:

    sqlplus /nolog @pgvwbrepos.sql

**Note:**

If you are installing the Visual Workbench repository on Oracle8i or earlier, then you must use `pgvwbrepos8.sql`. All of the examples in this section are provided with the assumption that you are installing on Oracle9i and later.

The script takes you through the following steps:

##### Step 1: Enter the Database Connection Information

This step explains how to enter the database connection information.

Use the default vale of `LOCAL` by pressing Enter. Next, you are prompted to enter the passwords for the `SYSTEM` and `SYS` accounts of the Oracle database. Press Enter after entering each password.

The script stops if any information is incorrect. Verify the information before rerunning the script.

##### Step 2: Check for Existing Workbench Repository

This step explains how to check for an existing Visual Workbench repository.

The script checks for an existing Visual Workbench repository and for the data dictionary. If neither is found, then the script proceeds to Step 3 below.

If the data dictionary exists, then the script stops. Choose another Oracle database and rerun the script, starting at "Step 1: Choose a Repository Server ".

If a Visual Workbench repository exists, then the script gives you the following options:

- Upgrade the existing private repository to public status and proceed to Step 3.

- Replace the existing repository with the new private repository and proceed to Step 3.

- Stop the script.

##### Step 3: Check for The Required PL/SQL Packages

This step explains how to check for the required PL/SQL packages.

The script checks for the existence of `UTL_RAW`, `DBMS_OUTPUT`, and `DBMS_PIPE` in the Oracle database. If this software exists, then the script proceeds to Step 4.

The script stops if this software does not exist. Refer to [Oracle Database Administrator's Guide](../admin/index.md) about the missing software. After the software is installed, rerun the script.

##### Step 4: Install the UTL_PG Package

This step explains how to install the `UTL_PG` package.

The script checks for the existence of the `UTL_PG` package. If it does not exist, then the `UTL_PG` package is installed. The script then proceeds to Step 5.

If `UTL_PG` exists, then you are prompted to reinstall it. Press Return to reinstall `UTL_PG`.

##### Step 5: Create the Administrative User and All Repository Tables

This step explains how to create the administrative user for the Visual Workbench repository as `PGMADMIN` with the initial password of `PGMADMIN`.

This user owns all objects in the repository.

After this step, a private Visual Workbench repository that includes the `PGM_SUP`,  `PGM_BQM`, and `PGM_UTL8` packages, is created in the Oracle database, which only the `PGMADMIN` user can access.

##### Step 6: Create Public Synonyms and Development Roles

This optional step explains how to change the private access privileges of the Visual Workbench repository.

The private status enables only the `PGMADMIN` user to have access to the repository. If you enter `N` and press Enter, then the repository retains its private status.

A public status enables the granting of access privileges to other users besides `PGMADMIN`. If you want to give the repository public status, then enter Y and press Enter.

#### After the Repository is Created

After creating the Visual Workbench repository, there is one optional step, granting development privileges for the Visual Workbench repository to users.

To allow users, other than the `PGMADMIN` user, to perform development operations on the Visual Workbench repository, `PGMADMIN` must grant them the necessary privileges. To do this, perform the following:

1.  Ensure that the repository has a public status. It has this status if you created it by using Steps 1 to 6 of the `pgvwbrepos.sql` script. If you did not use Step 6, then rerun the script. When you get to Step 2 of the script, enter A at the prompt to upgrade the private repository to public status.
2.  Use SQL\*Plus to connect to the repository as the `PGMADMIN` user and grant the `PGMDEV` role to each user. For example:
        SQL> GRANT PGMDEV TO SCOTT;

#### Deinstall the Visual Workbench Repository

Use the repository script `pgvwbremove.sql` to deinstall a Visual Workbench.

To deinstall a Visual Workbench repository on Oracle10g, use the repository script `pgvwbremove.sql`. To run this script, ensure that you are currently under the Oracle database `ORACLE_HOME\dg4mq\admin\repo directory on Microsoft Windows and ``ORACLE_HOME``/dg4mq/admin/repo` directory on UNIX based systems (where you copied the scripts), and then enter the following command:

    sqlplus /nolog @pgvwbremove.sql

**Note:**

If you are deinstalling the Visual Workbench Repository on Oracle8i or earlier, then you must use `pgvwbremove8.sql`. All the examples in this section are provided with the assumption that you are installing on Oracle9i and later.

The script takes you through the following steps:

##### Step 1: Enter the Database Connection Information

This step explains how to enter the database connection information.

Use the default value of `LOCAL` by pressing Enter.

Next, you are prompted to enter the passwords for the `SYSTEM`, `SYS`, and `PGMADMIN` accounts of the Oracle database. Press Enter after entering each password.

The script stops if any of the information is incorrect. Verify the information before rerunning the script.

##### Step 2: Check for the Existing Workbench Repository

This step explains how to check for the existing Workbench repository.

Enter Y and press Enter for the prompt to remove public synonyms and development roles. This returns the repository to private status. You can exit the script now by entering N and pressing Enter, or you can proceed to the next prompt.

If you are certain you want to remove the private repository, then enter Y and press Enter. The script removes all repository tables and related packages.

### Preparing the Production Oracle Database

These preparations include preparing, installing, and removing PL/SQL packages on the production database.

#### Introduction

This section describes how to run the `pgmdeploy.sql` and `pgmundeploy.sql` scripts.

Before you can compile MIPs on a production Oracle database, the following PL/SQL packages must be present on the production Oracle database:

- `DBMS_PIPE`, `DBMS_OUTPUT`, and `UTL_RAW`

  These packages are shipped with each Oracle database and are typically preinstalled.

- `PGM`, `PGM_BQM`, `PGM_SUP`, and `UTL_PG`

  These packages are shipped with your Oracle Database Gateway for WebSphere MQ. They are installed during the creation process of the Visual Workbench repository. Do not execute deployment script on the Oracle database with an installed Visual Workbench repository. If the Oracle database used for the repository is different from the Oracle database used in the production environment, you must install these packages on the production Oracle database.

This section describes how to run the following scripts:

- `pgmdeploy.sql`,

  A deployment script that is used to verify the existence of the required PL/SQL packages and install them if they do not exist on the production Oracle database.

- `pgmundeploy.sql`

  A script to remove the PL/SQL packages from a production Oracle database.

#### Verifying and Installing PL/SQL Packages

This topic describes verifying and installing PL/SQL packages.

1.  Locate the following scripts:
    - `pgm.sql`

    - `pgmbqm.sql`

    - `pgmdeploy.sql`

    - `pgmsup.sql`

    - `pgmundeploy.sql`

    - `prvtpg.sql`

    - `utlpg.sql`

    These scripts are installed with the gateway, in the `ORACLE_HOME\dg4mq\admin\deploy` directory on Microsoft Windows and `ORACLE_HOME``/dg4mq/admin/deploy` directory on UNIX based systems, where `ORACLE_HOME` is the gateway home directory.
2.  If your production Oracle database is on a system that is different from the gateway, then use a file transfer method, such as FTP, to transfer files in the `ORACLE_HOME\dg4mq\admin\deploy` directory on Microsoft Windows and` ORACLE_HOME/dg4mq/admin/deploy` directory on UNIX based systems, where `ORACLE_HOME` is the gateway home directory on your gateway system. On your production Oracle database system, change directory to the directory containing the deployment scripts that you just transferred and skip to Step 4.
3.  If your production Oracle database is on the same system as the gateway, then change the directory to `ORACLE_HOME\dg4mq\admin\deploy` directory on Microsoft Windows and `ORACLE_HOME/dg4mq/admin/deploy` on UNIX based systems, where `ORACLE_HOME` is the gateway home directory.
4.  Run the `pgmdeploy.sql` script by as follows:
        $ sqlplus /nolog @pgmdeploy.sql
5.  At the script prompt: `Enter the connect string for the Oracle database... [LOCAL]`, press Enter to use the default value of `LOCAL`.
6.  At the script prompt `Enter the following required Oracle database password`, enter the password of the `SYS` account.

After the script verifies the `SYS` account password, it connects to the production Oracle database. The script verifies and reports the PL/SQL packages that are installed there:

- If any of the Oracle database packages, `DBMS_OUTPUT`, `DBMS_PIPE` or `UTL_RAW` are missing, then the script stops. Have your DBA install the missing packages and re-run the deployment script.

- If any of the Oracle packages, `PGM`, `PGM_BQM`, `PGM_SUP`, and `UTL_PG` are missing, then the script installs them on the production Oracle database.

#### Removing the PL/SQL Packages

This topic describes removing PL/SQL packages.

You can remove the PL/SQL packages that were installed by the `pgmdeploy.sql` script if, for example, none of your applications in the production environment uses a MIP. To remove these packages, perform the following steps:

1.  On your production Oracle database, change to the directory containing the deployment scripts by entering the following command:
    For Microsoft Windows:

        > cd ORACLE_HOME\dg4mq\admin\deploy

    For UNIX based systems:

        $ cd $ORACLE_HOME/dg4mq/admin/deploy
2.  Run the `pgmundeploy.sql` as follows:
        $ sqlplus /nolog @pgmundeploy.sql
3.  At the script prompt: `Enter the connect string for the Oracle database... [LOCAL]`, press \[`Return`\] to use the default of `LOCAL`.
4.  At the script prompt, `enter the required Oracle database passwords`, enter the password of the `SYS` account.

After the script verifies the `SYS` account password, it connects to the production Oracle database and removes the packages installed by the `pgmdeploy.sql` script.

After the `pgmundeploy.sql` script completes successfully, applications on the production Oracle database fail if they attempt to reference any of the MIPs that are compiled there.
