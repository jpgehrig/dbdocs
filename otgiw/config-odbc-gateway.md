After installing the gateway and the ODBC driver for the non-Oracle system, perform the following tasks to configure Oracle Database Gateway for ODBC:

1.  Configure the Gateway Initialization Parameter File

2.  Configure Oracle Net for the Gateway

3.  Configure the Oracle Database for Gateway Access

4.  Create Database Links

5.  Encrypt Gateway Initialization Parameter Values

6.  Configure the Gateway to Access Multiple ODBC Data Sources

### Configure the Gateway Initialization Parameter File

Perform the following tasks to configure the gateway initialization file:

1.  Create the Initialization Parameter File
2.  Set the Initialization Parameter Values

#### Create the Initialization Parameter File

You must create an initialization file for your Oracle Database Gateway for ODBC. Oracle supplies a sample initialization file, `initdg4odbc.ora`. The sample file is stored in the `ORACLE_HOME``\hs\admin` directory.

To create an initialization file for the ODBC gateway, copy the sample initialization file and rename it to `init``sid``.ora`, where `sid` is the system identifier(SID) you want to use for the instance of the non-Oracle system to which the gateway connects.

The gateway system identifier (SID) is an alphanumeric character string that identifies a gateway instance. You need one gateway instance, and therefore one gateway SID, for each ODBC source you are accessing.

If you want to access two ODBC sources, you need two gateway SIDs, one for each instance of the gateway. If you have only one ODBC source but want to access it sometimes with one set of gateway parameter settings, and other times with different gateway parameter settings, then you will need multiple gateway SIDs for the single ODBC source. The SID is used as part of the file name for the initialization parameter file.

#### Set the Initialization Parameter Values

After the initialization file has been created, you must set the initialization parameter values. A number of initialization parameters can be used to modify the gateway behavior. You must set the `HS_FDS_CONNECT_INFO `initialization parameter. Other initialization parameters have defaults or are optional. You can use the default values and omit the optional parameters, or you can specify the parameters with values tailored for your installation. Refer to [Initialization Parameters](init-param-gateway.md) for the complete list of initialization parameters that can be set. Changes made to the initialization parameters only take effect in the next gateway session.

The `HS_FDS_CONNECT_INFO` initialization parameter specifies the information required for connecting to the non-Oracle system. Set the `HS_FDS_CONNECT_INFO` as follows:

    HS_FDS_CONNECT_INFO=dsn_value

    where dsn_value is the name of the system DSN defined in the Microsoft Windows ODBC Data Source Administrator.

**Note:**

Before deciding whether to accept the default values or to change them, see [Initialization Parameters](init-param-gateway.md) for detailed information about all the initialization parameters.

##### Example: Setting Initialization Parameter Values

Assume that a system DSN has been defined in the Microsoft Windows ODBC Data Source Administrator. In order to connect to this SQL Server database through the gateway, the following line is required in the `init``sid``.ora` file:

    HS_FDS_CONNECT_INFO=sqlserver7

`sqlserver7` is the name of the system DSN defined in the Microsoft Windows ODBC Data Source Administrator.

The following procedure enables you to define a system DSN in the Microsoft Windows ODBC Data Source Administrator, version 3.5:

1.  From the Start menu, choose Settings \> Control Panel and select ODBC.
2.  Select the System DSN tab page to display the system data sources.
3.  Click Add.
4.  From the list of installed ODBC drivers, select the name of the driver that the data source will use. For example, select SQL Server.
5.  Click Finish.
6.  Enter a name for the DSN and an optional description. Enter other information depending on the ODBC driver. For example, for SQL Server enter the SQL Server machine name.
    **Note:**

    The name entered for the DSN must match the value of the initialization parameter `HS_FDS_CONNECT_INFO` that is specified in `init``sid``.ora`.
7.  Refer to your ODBC driver documentation and follow the prompts to complete configuration of the DSN.
8.  After creating the system DSN, click OK to exit the ODBC Data Source Administrator.

**Note:**

If the ODBC driver supports Quoted Identifiers or Delimited Identifiers it should be turned on.

### Configure Oracle Net for the Gateway

The gateway requires Oracle Net to communicate with the Oracle database. After configuring the gateway, perform the following tasks to configure Oracle Net to work with the gateway:

1.  Configure Oracle Net Listener for the Gateway
2.  Stop and Start the Oracle Net Listener for the Gateway

#### Configure Oracle Net Listener for the Gateway

The Oracle Net Listener listens for incoming requests from the Oracle database. For the Oracle Net Listener to listen for the gateway, information about the gateway must be added to the Oracle Net Listener configuration file, `listener.ora`. This file by default is located in `ORACLE_HOME``\network\admin`, where `ORACLE_HOME` is the directory under which the gateway is installed.

The following entries must be added to the `listener.ora` file:

- A list of Oracle Net addresses on which the Oracle Net Listener listens

- The executable name of the gateway that the Oracle Net Listener starts in response to incoming connection requests

A sample of the `listener.ora` entry (`listener.ora.sample`) is available in the `ORACLE_HOME``\dg4odbc\admin` directory where `ORACLE_HOME` is the directory under which the gateway is installed.

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
             (PROGRAM=dg4odbc)
          )
       )

Where:

| Variable                | Description                                                                                                                        |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `gateway_sid`           | specifies the SID of the gateway and matches the gateway SID specified in the connect descriptor entry in the `tnsnames.ora `file. |
| `oracle_home_directory` | specifies the Oracle home directory where the gateway resides.                                                                     |
| `dg4odbc`               | specifies the executable name of the Oracle Database Gateway for ODBC.                                                             |

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
          (PROGRAM=dg4odbc)
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

Before you use the gateway to access an ODBC data source you must configure the Oracle database to enable communication with the gateway over Oracle Net.

To configure the Oracle database you must add connect descriptors to the `tnsnames.ora` file. By default, this file is in `ORACLE_HOME``\network\admin`, where `ORACLE_HOME` is the directory in which the Oracle database is installed. You cannot use the Oracle Net Assistant or the Oracle Net Easy Config tools to configure the `tnsnames.ora` file. You must edit the file manually.

A sample of the `tnsnames.ora` entry (`tnsnames.ora.sample`) is available in the `ORACLE_HOME``\dg4odbc\admin` directory where `ORACLE_HOME` is the directory under which the gateway is installed.

**See Also:**

[Oracle Database Administrator's Guide](../admin/index.md) for information about editing the `tnsnames.ora` file.

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

Table 11-1 Oracle Database Gateway for ODBC Parameters for tnsnames.ora File

| Variable             | Description                                                                                                                                                                                                                                                                                                       |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `connect_descriptor` | is the description of the object to connect to as specified when creating the database link, such as `dg4odbc`.<br>Check the `sqlnet.ora` file for the following parameter setting:<br>`names.directory_path` = `(TNSNAMES)`<br>Note: The `sqlnet.ora` file is typically stored in `ORACLE_HOME``\network\admin`. |
| `TCP`                | is the TCP protocol used for TCP/IP connections.                                                                                                                                                                                                                                                                  |
| `host_name`          | specifies the machine where the gateway is running.                                                                                                                                                                                                                                                               |
| `port_number`        | matches the port number used by the Oracle Net Listener that is listening for the gateway. The Oracle Net Listener's port number can be found in the `listener.ora` file used by the Oracle Net Listener. See Syntax of listener.ora File Entries .                                                               |
| `gateway_sid`        | specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that is listening for the gateway. See Configure Oracle Net Listener for the Gateway for more information.                                                                                   |
| `(HS=OK)`            | specifies that this connect descriptor connects to a non-Oracle system.                                                                                                                                                                                                                                           |

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

Any Oracle client connected to the Oracle database can access an ODBC data source through the gateway. The Oracle client and the Oracle database can reside on different machines. The gateway accepts connections only from the Oracle database.

A connection to the gateway is established through a database link when it is first used in an Oracle session. In this context, a connection refers to the connection between the Oracle database and the gateway. The connection remains established until the Oracle session ends. Another session or user can access the same database link and get a distinct connection to the gateway and ODBC data source.

Database links are active for the duration of a gateway session. If you want to close a database link during a session, you can do so with the `ALTER SESSION` statement.

To access the ODBC data source, you must create a database link. A public database link is the most common of database links.

    SQL> CREATE PUBLIC DATABASE LINK dblink CONNECT TO
    2  "user" IDENTIFIED BY "password" USING 'tns_name_entry';

Where:

| Variable         | Description                                                                                                  |
|:-----------------|:-------------------------------------------------------------------------------------------------------------|
| `dblink`         | is the complete database link name.                                                                          |
| `tns_name_entry` | specifies the Oracle Net connect descriptor specified in the `tnsnames.ora` file that identifies the gateway |

After the database link is created you can verify the connection to the ODBC data source, as follows:

    SQL> SELECT * FROM DUAL@dblink;

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for more information about using database links.

### Encrypt Gateway Initialization Parameter Values

The gateway uses user IDs and passwords to access the information in the remote database. Some user IDs and passwords must be defined in the gateway initialization file to handle functions such as resource recovery. In the current security conscious environment, having plain-text passwords that are accessible in the initialization file is deemed insecure. The `dg4pwd` encryption utility has been added as part of Heterogeneous Services to help make this more secure. This utility is accessible by this gateway. The initialization parameters that contain sensitive values can be stored in an encrypted form.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/initialization-parameters.md) for more information about using this utility.

### Configure the Gateway to Access Multiple ODBC Data Sources

The tasks for configuring the gateway to access multiple ODBC data sources are similar to the tasks for configuring the gateway for a single data source. The configuration example assumes the following:

- The gateway is installed and configured with the SID of `dg4odbc`.

- The gateway is configured to access one ODBC data source named `dsn1`.

- Two ODBC data sources named dsn2 and dsn3 where dsn2 and dsn3 are the names of the system DSN defined in the Microsoft Windows ODBC Data Source Administrator, are being added.

#### Multiple ODBC Data Sources Example: Configuring the Gateway

##### Choose One System ID for Each ODBC Data Source

A separate instance of the gateway is needed for each ODBC data source. Each instance needs its own gateway System ID (SID). For this example, the gateway SIDs are chosen for the instances that access the ODBC data source:

- `dg4odbc2` for the gateway accessing data source `dsn2`.

- `dg4odbc3` for the gateway accessing data source `dsn3`.

##### Create Two Initialization Parameter Files

Create an initialization parameter file for each instance of the gateway by copying the original initialization parameter file:` ORACLE_HOME``\hs\admin\initdg4odbc.ora`, twice, naming one with the gateway SID for `dsn2` and the other with the gateway SID for `dsn3`:

    > cd ORACLE_HOME\hs\admin
    > copy initdg4odbc.ora initdg4odbc2.ora
    > copy initdg4odbc.ora initdg4odbc3.ora

Change the value of the `HS_FDS_CONNECT_INFO` parameter in the new files as follows:

For `initdg4odbc2.ora`, enter the following:

    HS_FDS_CONNECT_INFO=dsn2

For `initdg4odbc3.ora`, enter the following:

    HS_FDS_CONNECT_INFO=dsn3

**Note:**

If you have multiple gateway SIDs for the same ODBC data source because you want to use different gateway parameter settings at different times, follow the same procedure. You create several initialization parameter files, each with different SIDs and different parameter settings.

#### Multiple ODBC Data Sources Example: Configuring Oracle Net Listener

##### Add Entries to listener.ora

Add two new entries to the Oracle Net Listener configuration file,`listener.ora`. You must have an entry for each gateway instance, even when multiple gateway instances access the same database.

The following example shows the entry for the original installed gateway first, followed by the new entries:

    SID_LIST_LISTENER=
    (SID_LIST=
       (SID_DESC=
          (SID_NAME=dg4odbc)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
       )
       (SID_DESC=
          (SID_NAME=dg4odbc2)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
       )
       (SID_DESC=
          (SID_NAME=dg4odbc3)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
       )
    )

where, `oracle_home_directory` is the directory where the gateway resides.

#### Multiple ODBC Data Sources Example: Stopping and Starting the Oracle Net Listener

Perform the following steps:

1.  From the Start menu, select Settings, Control Panel and then select Services.
2.  Select the Oracle Net Listener service for the gateway.
3.  Click Stop.
4.  Click Start.

#### Multiple ODBC Data Sources Example: Configuring Oracle Database for Gateway Access

Add two connect descriptor entries to the `tnsnames.ora` file. You must have an entry for each gateway instance, even if the gateway instances access the same database.

The following example shows the entry for the original installed gateway first, followed by the two entries for the new gateway instances:

    old_dsn_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4odbc))
                   (HS=OK))
    new_dsn2_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4odbc2))
                    (HS=OK))
    new_dsn3_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4odbc3))
                    (HS=OK))

The value for `PORT` is the TCP/IP port number of the Oracle Net Listener that is listening for the gateway. The number can be found in the `listener.ora` file used by the Oracle Net Listener. The value for `HOST` is the name of the machine on which the gateway is running. The name also can be found in the `listener.ora` file used by the Oracle Net Listener.

#### Multiple ODBC Data Sources Example: Accessing ODBC Data

Enter the following to create a database link for the `dg4odbc2` gateway:

    SQL> CREATE PUBLIC DATABASE LINK ODBC2 CONNECT TO
      2  "user2" IDENTIFIED BY "password2" USING 'new_dsn2_using';

Enter the following to create a database link for the `dg4odbc3` gateway:

    SQL> CREATE PUBLIC DATABASE LINK ODBC3 CONNECT TO
      2  "user3" IDENTIFIED BY "password3" USING 'new_dsn3_using';

After the database links are created, you can verify the connection to the new ODBC data sources, as in the following:

    SQL> SELECT * FROM ALL_USERS@ODBC2;

    SQL> SELECT * FROM ALL_USERS@ODBC3;
