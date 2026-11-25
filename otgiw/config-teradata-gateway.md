After installing the gateway, perform the following tasks to configure Oracle Database Gateway for Teradata:

1.  Configure the Gateway Initialization Parameter File

2.  Configure Oracle Net for the Gateway

3.  Configure the Oracle Database for Gateway Access

4.  Create Database Links

5.  Configure Two-Phase Commit

6.  Encrypt Gateway Initialization Parameter Values

7.  Configure the Gateway to Access Multiple Teradata Databases

### Configure the Gateway Initialization Parameter File

Perform the following tasks to configure the gateway initialization parameter file:

1.  Choose a System Identifier for the Gateway
2.  Customize the Initialization Parameter File

#### Choose a System Identifier for the Gateway

The gateway system identifier (SID) is an alphanumeric character string that identifies a gateway instance. You need one gateway instance, and therefore one gateway SID, for each Teradata database you are accessing. The SID is used as part of the file name for the initialization parameter file. The default SID is `dg4tera`.

You can define a gateway SID, but using the default of `dg4tera` is easier because you do not need to change the initialization parameter file name. However, if you want to access two Teradata databases, you need two gateway SIDs, one for each instance of the gateway. If you have only one Teradata database and want to access it sometimes with one set of gateway parameter settings, and other times with different gateway parameter settings, then you will need multiple gateway SIDs for the single Teradata database.

#### Customize the Initialization Parameter File

The initialization parameter file must be available when the gateway is started. During installation, the following default initialization parameter file is created:

    ORACLE_HOME\dg4tera\admin\initdg4tera.ora

Where `ORACLE_HOME` is the directory under which the gateway is installed.

This initialization file is for the default gateway SID. If you are not using `dg4tera` as the gateway SID, you must rename the initialization parameter file using the SID you chose in the preceding Step Choose a System Identifier for the Gateway. This default initialization parameter file is sufficient for starting the gateway, verifying a successful installation, and running the demonstration scripts.

A number of initialization parameters can be used to modify the gateway behavior. Refer to [Initialization Parameters](init-param-gateway.md) for the complete list of initialization parameters that can be set. Changes made to the initialization parameters only take effect in the next gateway session. The most important parameter is the `HS_FDS_CONNECT_INFO`, which describes the connection to the non-Oracle system.

The default initialization parameter file already has an entry for this parameter. The syntax for `HS_FDS_CONNECT_INFO` is as follows:

    HS_FDS_CONNECT_INFO=ip_address:port_number[/database_name]

Where:

| Variable        | Description                                                             |
|:----------------|:------------------------------------------------------------------------|
| `ip_address`    | is the IP address of the machine hosting the Teradata database.         |
| `port_number`   | is the port number of the Teradata database server.                     |
| `database_name` | is the Teradata database name. The `database_name` variable is optional |

**See Also:**

[Initialization Parameters](init-param-gateway.md) and the [Oracle Database Heterogeneous Connectivity User's Guide](../heter/initialization-parameters.md) for more information about customizing the initialization parameter file.

### Configure Oracle Net for the Gateway

The gateway requires Oracle Net to communicate with the Oracle database. After configuring the gateway, perform the following tasks to configure Oracle Net to work with the gateway:

1.  Configure Oracle Net Listener for the Gateway
2.  Stop and Start the Oracle Net Listener for the Gateway

#### Configure Oracle Net Listener for the Gateway

The Oracle Net Listener listens for incoming requests from the Oracle database. For the Oracle Net Listener to listen for the gateway, information about the gateway must be added to the Oracle Net Listener configuration file, `listener.ora`. This file by default is located in `ORACLE_HOME``\network\admin`, where `ORACLE_HOME` is the directory under which the gateway is installed.

The following entries must be added to the `listener.ora` file:

- A list of Oracle Net addresses on which the Oracle Net Listener listens

- The executable name of the gateway that the Oracle Net Listener starts in response to incoming connection requests

A sample of the `listener.ora` entry (`listener.ora.sample`) is available in the `ORACLE_HOME``\dg4tera\admin` directory where `ORACLE_HOME` is the directory under which the gateway is installed.

##### Syntax of listener.ora File Entries

The Oracle database communicates with the gateway using Oracle Net and any supported protocol adapters. The following is the syntax of the address on which the Oracle Net Listener listens using the TCP/IP protocol adapter:

    LISTENER=
            (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name)
              (PORT=port_number))

Where:

| Variable      | Description                                                                                                                                                                                                   |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `host_name`   | is the name of the machine on which the gateway is installed.                                                                                                                                                 |
| `port_number` | specifies the port number used by the Oracle Net Listener. If you have other listeners running on the same machine, then the value of `port_number` must be different from the other listeners' port numbers. |

To direct the Oracle Net Listener to start the gateway in response to incoming connection requests, add an entry to the `listener.ora` file.

**Note:**

You must use the same SID value in the listener.ora file and the `tnsnames.ora` file that will be configured in the next step.

    SID_LIST_LISTENER=
       (SID_LIST=
          (SID_DESC=
             (SID_NAME=gateway_sid)
             (ORACLE_HOME=oracle_home_directory)
             (PROGRAM=dg4tera)
             (ENVS=PATH=oracle_home_directory\bin;teradata_client_directory\lib;Windows_system_paths)
          )
       )

Where:

| Variable                    | Description                                                                                                                                                                                                                          |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `gateway_sid`               | specifies the SID of the gateway and matches the gateway SID specified in the connect descriptor entry in the `tnsnames.ora` file.                                                                                                   |
| `oracle_home_directory`     | specifies the Oracle home directory where the gateway resides.                                                                                                                                                                       |
| `dg4tera`                   | specifies the executable name of the Oracle Database Gateway for Teradata.                                                                                                                                                           |
| `teradata_client_directory` | specifies the directory where the Teradata client resides.                                                                                                                                                                           |
| `Windows_system_paths`      | specifies the Microsoft Windows system paths.<br>For example, C:\gtwyhome\tg11\bin;C:\Program Files\NCR\Teradata Client\cliv2;C:\Program Files\NCR\Common Files\Shared ICU Libraries for Teradata\lib;C:\WINDOWS\system32;C:\WINDOWS |

If you already have an existing Oracle Net Listener, then add the following syntax to `SID_LIST` in the existing `listener.ora` file:

    SID_LIST_LISTENER=
    (SID_LIST=
       (SID_DESC=.
         .
       )
       (SID_DESC=.
         .
       )
       (SID_DESC=
          (SID_NAME=gateway_sid)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4tera)
          (ENVS=PATH=oracle_home_directory\bin;teradata_client_directory\lib;Windows_system_paths)
       )
    )

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for information about changing the `listener.ora` file.

#### Stop and Start the Oracle Net Listener for the Gateway

You must stop and restart the Oracle Net Listener to initiate the new settings, as follows:

1.  From the Start menu, select Settings, Control Panel and then select Services.
2.  Select the Oracle Net Listener service for the gateway.
3.  If the service is already running, click Stop to stop it.
4.  Click Start to start or restart the service.

### Configure the Oracle Database for Gateway Access

Before you use the gateway to access Teradata data you must configure the Oracle database to enable communication with the gateway over Oracle Net.

To configure the Oracle database you must add connect descriptors to the `tnsnames.ora` file. By default, this file is in `ORACLE_HOME``\network\admin`, where `ORACLE_HOME` is the directory in which the Oracle database is installed. You cannot use the Oracle Net Assistant or the Oracle Net Easy Config tools to configure the `tnsnames.ora` file. You must edit the file manually.

A sample of the `tnsnames.ora` entry (`tnsnames.ora.sample`) is available in the `ORACLE_HOME``\dg4tera\admin` directory where `ORACLE_HOME` is the directory under which the gateway is installed.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for information about editing the `tnsnames.ora` file.

#### Configuring tnsnames.ora

Edit the `tnsnames.ora` file to add a connect descriptor for the gateway. The following is a syntax of the Oracle Net entry using the TCP/IP protocol:

    connect_descriptor=
       (DESCRIPTION=
          (ADDRESS=
             (PROTOCOL=TCP)
             (HOST=host_name)
             (PORT=port_number)
          )
          (CONNECT_DATA=
             (SID=gateway_sid))
          (HS=OK))

Where:

| Variable             | Description                                                                                                                                                                                                                                                                                                     |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `connect_descriptor` | is the description of the object to connect to as specified when creating the database link, such as `dg4tera`.<br>Check the sqlnet.ora file for the following parameter setting:<br>`names.directory_path` = `(TNSNAMES)`<br>Note: The `sqlnet.ora` file is typically stored in `ORACLE_HOME``\network\admin`. |
| TCP                  | is the TCP protocol used for TCP/IP connections.                                                                                                                                                                                                                                                                |
| `host_name`          | specifies the machine where the gateway is running.                                                                                                                                                                                                                                                             |
| `port_number`        | matches the port number used by the Oracle Net Listener that is listening for the gateway. The Oracle Net Listener's port number can be found in the `listener.ora` file used by the Oracle Net Listener. See Syntax of listener.ora File Entries .                                                             |
| `gateway_sid`        | specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that is listening for the gateway. See Configure Oracle Net Listener for the Gateway for more information.                                                                                 |
| `(HS=OK)`            | specifies that this connect descriptor connects to a non-Oracle system.                                                                                                                                                                                                                                         |

#### Configuring tnsnames.ora for Multiple Listeners

To ensure higher availability, you can specify multiple listeners within the connect descriptor.

     connect_descriptor=
        (DESCRIPTION=
           (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name_1)
              (PORT=port_number_1)
           )
           (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name_2)
              (PORT=port_number_2)
           )
           (CONNECT_DATA=
              (SID=gateway_sid))
           (HS=OK))

This indicates that, if the listener for `host_name_1` and `port_number_1` is not available, then the second listener for `host_name_2` and `port_number_2` will take over.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for information about editing the `tnsnames.ora` file.

### Create Database Links

Any Oracle client connected to the Oracle database can access Teradata data through the gateway. The Oracle client and the Oracle database can reside on different machines. The gateway accepts connections only from the Oracle database.

A connection to the gateway is established through a database link when it is first used in an Oracle session. In this context, a connection refers to the connection between the Oracle database and the gateway. The connection remains established until the Oracle session ends. Another session or user can access the same database link and get a distinct connection to the gateway and Teradata database.

Database links are active for the duration of a gateway session. If you want to close a database link during a session, you can do so with the `ALTER SESSION` statement.

To access the Teradata server, you must create a database link. A public database link is the most common of database links.

    SQL> CREATE PUBLIC DATABASE LINK dblink CONNECT TO
    2  "user" IDENTIFIED BY "password" USING 'tns_name_entry';

Where:

| Variable         | Description                                                                                                  |
|:-----------------|:-------------------------------------------------------------------------------------------------------------|
| `dblink`         | is the complete database link name.                                                                          |
| `tns_name_entry` | specifies the Oracle Net connect descriptor specified in the `tnsnames.ora` file that identifies the gateway |

After the database link is created you can verify the connection to the Teradata database, as follows:

    SQL> SELECT * FROM DUAL@dblink;

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for more information about using database links.

### Configure Two-Phase Commit

The gateway supports the following transaction capabilities:

- `COMMIT_CONFIRM`

- `READ_ONLY`

- `SINGLE_SITE`

The transaction model is set using the HS_TRANSACTION_MODEL initialization parameter. By default, the gateway runs in `COMMIT_CONFIRM` transaction mode. When the Teradata database is updated by a transaction, the gateway becomes the commit point site. The Oracle database commits the unit of work in the Teradata database after verifying that all Oracle databases in the transaction have successfully prepared the transaction. Only one gateway instance can participate in an Oracle two-phase commit transaction as the commit point site.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/two-phase-commit-protocol.md) for information about the two-phase commit process.

To enable the `COMMIT_CONFIRM` transaction mode, perform the following tasks:

1.  Create a Recovery Account and Password
2.  Create the Transaction Log Table

The log table, called `HS_TRANSACTION_LOG`, is where two-phase commit transactions are recorded.

#### Create a Recovery Account and Password

For the gateway to recover distributed transactions, a recovery account and password must be set up in the Teradata database. By default, both the user name of the account and the password are `RECOVER`. The name of the account can be changed with the gateway initialization parameter `HS_FDS_RECOVERY_ACCOUNT`. The account password can be changed with the gateway initialization parameter `HS_FDS_RECOVERY_PWD`.

**Note:**

Oracle recommends that you do not use the default value `RECOVER` for the user name and password. Moreover, storing plain-text as user name and password in the initialization file is not a good security policy. There is a utility called `dg4pwd` that should be used for encryption. Refer to [Section 4.2.3, 'Encrypting Initialization parameters'](../heter/initialization-parameters.md) in the Oracle Database Heterogeneous Connectivity User's Guide for further details.

1.  Set up a user account in the Teradata database. Both the user name and password must be a valid Teradata user name and password.
2.  In the initialization parameter file, set the following gateway initialization parameters:
    - `HS_FDS_RECOVERY_ACCOUNT` to the user name of the Teradata user account you set up for recovery.

    - `HS_FDS_RECOVERY_PWD` to the password of the Teradata user account you set up for recovery.

      **See Also:**

      Customize the Initialization Parameter File for information about editing the initialization parameter file. For information about `HS_FDS_RECOVERY_ACCOUNT` and `HS_FDS_RECOVERY_PWD`, see [Initialization Parameters](init-param-gateway.md).

#### Create the Transaction Log Table

When configuring the gateway for two-phase commit, a table must be created in the Teradata database for logging transactions. The gateway uses the transaction log table to check the status of failed transactions that were started at the Teradata database by the gateway and registered in the table.

**Note:**

Updates to the transaction log table cannot be part of an Oracle distributed transaction.

The information in the transaction log table is required by the recovery process and must not be altered. The table must be used, accessed, or updated only by the gateway.

The table, called `HS_TRANSACTION_LOG`, consists of two columns, `GLOBAL_TRAN_ID`, data type `CHAR(64)` and `TRAN_COMMENT`, data type `CHAR(255)`.

You can use another name for the log table, other than `HS_TRANSACTION_LOG`, by specifying the other name using the `HS_FDS_TRANSACTION_LOG` initialization parameter.

**See Also:**

[Initialization Parameters](init-param-gateway.md) for information about the `HS_FDS_TRANSACTION_LOG` initialization parameter.

Create the transaction log table in the user account you created in Create a Recovery Account and Password. Because the transaction log table is used to record the status of a gateway transaction, the table must reside at the database where the Teradata update takes place. Also, the transaction log table must be created under the owner of the recovery account.

**Note:**

To utilize the transaction log table, users of the gateway must be granted privileges on the table.

To create a transaction log table use the `dg4tera_tx.sql` script, located in the directory `ORACLE_HOME``\dg4tera\admin` where `ORACLE_HOME` is the directory under which the gateway is installed.

### Encrypt Gateway Initialization Parameter Values

The gateway uses user IDs and passwords to access the information in the remote database. Some user IDs and passwords must be defined in the gateway initialization file to handle functions such as resource recovery. In the current security conscious environment, having plain-text passwords that are accessible in the initialization file is deemed insecure. The `dg4pwd` encryption utility has been added as part of Heterogeneous Services to help make this more secure. This utility is accessible by this gateway. The initialization parameters that contain sensitive values can be stored in an encrypted form.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/initialization-parameters.md) for more information about using this utility.

### Configure the Gateway to Access Multiple Teradata Databases

The tasks for configuring the gateway to access multiple Teradata databases are similar to the tasks for configuring the gateway for a single database. The configuration example assumes the following:

- The gateway is installed and configured with the default SID of `dg4tera`.

- The gateway is configured for one Teradata database named `db1`.

- Two Teradata databases named `db2` and `db3` on a host with IP Address 204.179.79.15 are being added.

#### Multiple Teradata Databases Example: Configuring the Gateway

##### Choose One System ID for Each Teradata Database

A separate instance of the gateway is needed for each Teradata database. Each instance needs its own gateway System ID (SID). For this example, the gateway SIDs are chosen for the instances that access the Teradata databases:

- `dg4tera2 `for the gateway accessing database `db2`

- `dg4tera3` for the gateway accessing database `db3`

##### Create Two Initialization Parameter Files

Create an initialization parameter file for each instance of the gateway by copying the original initialization parameter file:` ORACLE_HOME``\dg4tera\admin\initdg4tera.ora`, twice, naming one with the gateway SID for `db2` and the other with the gateway SID for `db3`:

    > cd ORACLE_HOME\dg4tera\admin
    > copy initdg4tera.ora initdg4tera2.ora
    > copy initdg4tera.ora initdg4tera3.ora

Change the value of the `HS_FDS_CONNECT_INFO` parameter in the new files.

For `initdg4tera2.ora`, enter the following:

    HS_FDS_CONNECT_INFO=204.179.79.15:1025/db2

For `initdg4tera3.ora`, enter the following:

    HS_FDS_CONNECT_INFO=204.179.79.15:1025/db3

**Note:**

If you have multiple gateway SIDs for the same Teradata database because you want to use different gateway parameter settings at different times, follow the same procedure. You create several initialization parameter files, each with different SIDs and different parameter settings.

#### Multiple Teradata Databases Example: Configuring Oracle Net Listener

##### Add Entries to listener.ora

Add two new entries to the Oracle Net Listener configuration file,`listener.ora`. You must have an entry for each gateway instance, even when multiple gateway instances access the same database.

The following example shows the entry for the original installed gateway first, followed by the new entries:

    SID_LIST_LISTENER=
    (SID_LIST=
       (SID_DESC=
          (SID_NAME=dg4tera)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4tera)
          (ENVS=PATH=oracle_home_directory\bin;teradata_client_directory\lib;Windows_system_paths)
       )
       (SID_DESC=
          (SID_NAME=dg4tera2)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4tera)
          (ENVS=PATH=oracle_home_directory\bin;teradata_client_directory\lib;Windows_system_paths)
       )
       (SID_DESC=
          (SID_NAME=dg4tera3)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4tera)
          (ENVS=PATH=oracle_home_directory\bin;teradata_client_directory\lib;Windows_system_paths)
       )
    )

where, `oracle_home_directory` is the directory where the gateway resides, `teradata_client_directory` specifies the directory where the Teradata client resides, and `Windows_system_paths` specifies the Microsoft Windows system paths.

#### Multiple Teardata Databases Example: Stopping and Starting the Oracle Net Listener

Perform the following steps:

1.  From the Start menu, select Settings, Control Panel and then select Services.
2.  Select the Oracle Net Listener service for the gateway.
3.  Click Stop.
4.  Click Start.

#### Multiple Teradata Databases Example: Configuring Oracle Database for Gateway Access

Add two connect descriptor entries to the `tnsnames.ora` file. You must have an entry for each gateway instance, even if the gateway instances access the same database.

This example describes how to configure Oracle Net on the Oracle database for multiple gateway instances. It shows the entry for the original installed gateway first, followed by the two entries for the new gateway instances:

    old_db_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4tera))
                   (HS=OK))
    new_db2_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4tera2))
                    (HS=OK))
    new_db3_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4tera3))
                    (HS=OK))

The value for `PORT` is the TCP/IP port number of the Oracle Net Listener that is listening for the gateway. The number can be found in the `listener.ora` file used by the Oracle Net Listener. The value for `HOST` is the name of the machine on which the gateway is running. The name also can be found in the `listener.ora` file used by the Oracle Net Listener.

#### Multiple Teradata Databases Example: Accessing Teradata Data

Enter the following to create a database link for the `dg4tera2` gateway:

    SQL> CREATE PUBLIC DATABASE LINK TERA2 CONNECT TO
      2  "user2" IDENTIFIED BY "password2" USING 'new_db2_using';

Enter the following to create a database link for the `dg4tera3` gateway:

    SQL> CREATE PUBLIC DATABASE LINK TERA3 CONNECT TO
      2  "user3" IDENTIFIED BY "password3" USING 'new_db3_using';

After the database links are created, you can verify the connection to the new Teradata databases, as in the following:

    SQL> SELECT * FROM ALL_USERS@TERA2;

    SQL> SELECT * FROM ALL_USERS@TERA3;
