After installing the gateway and the ODBC driver for the non-Oracle system, perform the following tasks to configure Oracle Database Gateway for ODBC:

1.  Configure the Gateway Initialization Parameter File

2.  Configure Oracle Net for the Gateway

3.  Configure the Oracle Database for Gateway Access

4.  Create Database Links

5.  Encrypt Gateway Initialization Parameter Values

6.  Configure the Gateway to Access Multiple ODBC Data Sources

### 11.1 Configure the Gateway Initialization Parameter File

Perform the following tasks to configure the gateway initialization file:

1.  Create the Initialization Parameter File
2.  Set the Initialization Parameter Values

#### 11.1.1 Create the Initialization Parameter File

You must create an initialization file for your Oracle Database Gateway for ODBC. Oracle supplies a sample initialization file, `initdg4odbc.ora`. The sample file is stored in the `$ORACLE_HOME/hs/admin` directory.

To create an initialization file for the ODBC gateway, copy the sample initialization file and rename it to `init``sid``.ora`, where `sid` is the system identifier (SID) you want to use for the instance of the non-Oracle system to which the gateway connects.

The gateway system identifier (SID) is an alphanumeric character string that identifies a gateway instance. You need one gateway instance, and therefore one gateway SID, for each ODBC source you are accessing.

If you want to access two ODBC sources, you need two gateway SIDs, one for each instance of the gateway. If you have only one ODBC source but want to access it sometimes with one set of gateway parameter settings, and other times with different gateway parameter settings, then you will need multiple gateway SIDs for the single ODBC source. The SID is used as part of the file name for the initialization parameter file.

#### 11.1.2 Set the Initialization Parameter Values

After the initialization file has been created, you must set the initialization parameter values. A number of initialization parameters can be used to modify the gateway behavior. You must set the `HS_FDS_CONNECT_INFO and ``the HS_FDS_SHAREABLE_NAME` initialization parameters. Other initialization parameters have defaults or are optional. You can use the default values and omit the optional parameters, or you can specify the parameters with values tailored for your installation. Refer to [Initialization Parameters](initialization-parameters-for-gateways.md) for the complete list of initialization parameters that can be set. Changes made to the initialization parameters only take effect in the next gateway session.

The `HS_FDS_CONNECT_INFO` initialization parameter specifies the information required for connecting to the non-Oracle system. Set the `HS_FDS_CONNECT_INFO` as follows:

    HS_FDS_CONNECT_INFO=dsn_value

where dsn_value is the data source name configured in the `odbc.ini `file

The `HS_FDS_SHAREABLE_NAME` initialization parameter specifies the full path of the ODBC driver manager. Set the `HS_FDS_SHAREABLE_NAME` as follows:

    HS_FDS_SHAREABLE_NAME=full_path_of_odbc_driver

where `full_path_of_odbc_driver` is the full path to the ODBC driver manager

**Note:**

Before deciding whether to accept the default values or to change them, see [Initialization Parameters](initialization-parameters-for-gateways.md) for detailed information about all the initialization parameters.

##### 11.1.2.1 Example: Setting Initialization Parameter Values

The following is an example of an `odbc.ini` file that uses DataDirect Technologies SQLServer ODBC driver. The ODBC driver is installed in `$ODBCHOME`, which is the `/opt/odbc520` directory.

    [ODBC Data Sources]
    SQLServerWP=DataDirect 5.20 SQL Server Wire Protocol

    [SQLServerWP]
    Driver=/opt/odbc520/lib/ivmsss18.so
    Description=DataDirect 5.20 SQL Server Wire Protocol
    Database=oratst
    LogonID=TKHOUSER
    Password=TKHOUSER
    Address=sqlserver-pc,1433
    QuotedId=Yes
    AnsiNPW=No

    [ODBC]
    Trace=0
    TraceFile=/opt/odbc520/odbctrace.out
    TraceDll=/opt/odbc520/lib/odbctrac.so
    InstallDir=/opt/odb520
    ConversionTableLocation=/opt/odbc520/tables
    UseCursorLib=0

To configure the Gateway for ODBC to use this driver, the following lines are required in `init``sid``.ora`:

    HS_FDS_CONNECT_INFO=SQLServerWP
    HS_FDS_SHAREABLE_NAME=/opt/odbc520/lib/libodbc.so
    set ODBCINI=/opt/odbc/odbc.ini

If the ODBC driver you are using requires you to set some environment variables then you can either set them in the initizlization file or in the environment.

The `HS_FDS_CONNECT_INFO` initialization parameter value must match the ODBC data source name in the `odbc.ini` file.

**Note:**

If the ODBC driver supports Quoted Identifiers or Delimited Identifiers it should be turned on.

### 11.2 Configure Oracle Net for the Gateway

The gateway requires Oracle Net to communicate with the Oracle database. After configuring the gateway, perform the following tasks to configure Oracle Net to work with the gateway:

1.  Configure Oracle Net Listener for the Gateway
2.  Stop and Start the Oracle Net Listener for the Gateway

#### 11.2.1 Configure Oracle Net Listener for the Gateway

The Oracle Net Listener listens for incoming requests from the Oracle database. For the Oracle Net Listener to listen for the gateway, information about the gateway must be added to the Oracle Net Listener configuration file, `listener.ora`. This file by default is located in `$ORACLE_HOME``/network/admin`, where `$ORACLE_HOME` is the directory under which the gateway is installed.

The following entries must be added to the `listener.ora` file:

- A list of Oracle Net addresses on which the Oracle Net Listener listens

- The executable name of the gateway that the Oracle Net Listener starts in response to incoming connection requests

A sample of the `listener.ora` entry (`listener.ora.sample`) is available in the `$ORACLE_HOME/hs/admin` directory where `$``ORACLE_HOME` is the directory under which the gateway is installed.

##### 11.2.1.1 Syntax of listener.ora File Entries

The Oracle database communicates with the gateway using Oracle Net and any supported protocol adapters. The following is the syntax of the address on which the Oracle Net Listener listens using the TCP/IP protocol adapter:

    LISTENER=
            (ADDRESS=
              (PROTOCOL=TCP)
              (HOST=host_name)
              (PORT=port_number))

where:

| Variable      | Description                                                                                                                                                                                                 |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `host_name`   | is the name of the machine on which the gateway is installed. IPv6 format is supported with this release. Refer to [Oracle Database Net Services Reference](../netrf/index.md) for detail.                  |
| `port_number` | specifies the port number used by the Oracle Net Listener. If you have other listeners running on the same machine, then the value of port_number must be different from the other listeners' port numbers. |

To direct the Oracle Net Listener to start the gateway in response to incoming connection requests, add an entry to the `listener.ora` file.

**Note:**

You must use the same SID value in the `tnsnames.ora` file and the `listener.ora` file.

For Linux:

    SID_LIST_LISTENER=
       (SID_LIST=
          (SID_DESC=
             (SID_NAME=gateway_sid)
             (ORACLE_HOME=oracle_home_directory)
             (PROGRAM=dg4odbc)
             (ENVS=LD_LIBRARY_PATH=odbc_library_dir:oracle_home_directory/lib)
          )
       )

where:

| Variable                | Description                                                                                                                        |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `gateway_sid`           | specifies the SID of the gateway and matches the gateway SID specified in the connect descriptor entry in the `tnsnames.ora `file. |
| `oracle_home_directory` | specifies the Oracle home directory where the gateway resides.                                                                     |
| `odbc_library_dir`      | specifies the ODBC driver library path                                                                                             |
| `dg4odbc`               | specifies the executable name of the Oracle Database Gateway for ODBC.                                                             |

If you already have an existing Oracle Net Listener, then add the following syntax to `SID_LIST` in the existing `listener.ora` file:

For Linux:

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
    (ENVS=LD_LIBRARY_PATH=odbc_library_dir:oracle_home_directory/lib)
       )
    )

**See Also:**

[Oracle Net Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for information about changing the `listener.ora` file.

#### 11.2.2 Stop and Start the Oracle Net Listener for the Gateway

You must stop and restart the Oracle Net Listener to initiate the new settings, as follows:

1.  Set the `PATH` environment variable to `$ORACLE_HOME/bin` where `$ORACLE_HOME` is the directory in which the gateway is installed.
    For example on the Linux platform, if you have the Bourne or Korn Shell, enter the following:

        $ PATH=$ORACLE_HOME/bin:$PATH;export PATH
        $ LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH; export LD_LIBRARY_PATH

    If you have the C Shell, enter the following:

        $ setenv PATH $ORACLE_HOME/bin:$PATH
        $ setenv LD_LIBRARY_PATH $ORACLE_HOME/lib:$LD_LIBRARY_PATH

    Table 11-1 specifies which parameter value to use for the different platforms:

    Table 11-1 Oracle Database Gateway for ODBC Parameter Values for UNIX Based Platforms

    | Platform                                                            | Parameter Value                       |
    |:--------------------------------------------------------------------|:--------------------------------------|
    | Oracle Solaris (SPARC) 64 bit and Oracle Solaris on x86-64 (64-Bit) | `LD_LIBRARY_PATH_64=$ORACLE_HOME/lib` |
    | HP-UX Itanium                                                       | `LD_LIBRARY_PATH=$ORACLE_HOME/lib`    |
    | Linux x86 64 bit                                                    | `LD_LIBRARY_PATH=$ORACLE_HOME/lib`    |
    | IBM AIX on POWER Systems (64-Bit)                                   | `LIBPATH=$ORACLE_HOME/lib`            |
2.  If the listener is already running, use the `lsnrctl` command to stop the listener and then start it with the new settings, as follows:
        $ lsnrctl stop
        $ lsnrctl start
3.  Check the status of the listener with the new settings, as follows:
        $ lsnrctl status

    The following is a partial output from a `lsnrctl` status check. In this example `dg4odbc` is the SID.

<!-- -->

    .
    .
    .
    Services Summary...
    Service "dg4odbc" has 1 instance(s).
      Instance "dg4odbc", status UNKNOWN, has 1 handler(s) for this service...
    The command completed successfully

### 11.3 Configure the Oracle Database for Gateway Access

Before you use the gateway to access an ODBC data source you must configure the Oracle database to enable communication with the gateway over Oracle Net.

To configure the Oracle database you must add connect descriptors to the `tnsnames.ora` file. By default, this file is in `$ORACLE_HOME/network/admin`, where `$ORACLE_HOME` is the directory in which the Oracle database is installed. You cannot use the Oracle Net Assistant or the Oracle Net Easy Config tools to configure the `tnsnames.ora` file. You must edit the file manually.

A sample of the `tnsmanes.ora` entry (`tnsnames.ora.sample`) is available in the `$ORACLE_HOME/dg4odbc/admin` directory where `$``ORACLE_HOME` is the directory under which the gateway is installed.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for information about editing the `tnsnames.ora` file.

#### 11.3.1 Configuring tnsnames.ora

Edit the `tnsnames.ora` file to add a connect descriptor for the gateway. The following is the syntax of the Oracle Net entry using the TCP/IP protocol:

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

| Variable             | Description                                                                                                                                                                                                                                                                                                      |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `connect_descriptor` | is the description of the object to connect to as specified when creating the database link, such as `dg4odbc`.<br>Check the sqlnet.ora file for the following parameter setting:<br>`names.directory_path` = `(TNSNAMES)`<br>Note: The `sqlnet.ora` file is typically stored in `$ORACLE_HOME``/network/admin`. |
| `TCP`                | is the TCP protocol used for TCP/IP connections.                                                                                                                                                                                                                                                                 |
| `host_name`          | specifies the machine where the gateway is running.                                                                                                                                                                                                                                                              |
| `port_number`        | matches the port number used by the Oracle Net Listener that is listening for the gateway. The Oracle Net Listener's port number can be found in the `listener.ora` file used by the Oracle Net Listener. See Syntax of listener.ora File Entries .                                                              |
| `gateway_sid`        | specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that is listening for the gateway. See Configure Oracle Net Listener for the Gateway for more information.                                                                                  |
| `(HS=OK)`            | specifies that this connect descriptor connects to a non-Oracle system.                                                                                                                                                                                                                                          |

#### 11.3.2 Configuring tnsnames.ora for Multiple Listeners

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

### 11.4 Create Database Links

Any Oracle client connected to the Oracle database can access an ODBC data source through the gateway. The Oracle client and the Oracle database can reside on different machines. The gateway accepts connections only from the Oracle database.

A connection to the gateway is established through a database link when it is first used in an Oracle session. In this context, a connection refers to the connection between the Oracle database and the gateway. The connection remains established until the Oracle session ends. Another session or user can access the same database link and get a distinct connection to the gateway and ODBC data source.

Database links are active for the duration of a gateway session. If you want to close a database link during a session, you can do so with the `ALTER SESSION` statement.

To access the ODBC data source, you must create a database link. A public database link is the most common of database links.

    SQL> CREATE PUBLIC DATABASE LINK dblink CONNECT TO
    2  "user" IDENTIFIED BY "password" USING 'tns_name_entry';

where:

| Variable         | Description                                                                                                  |
|:-----------------|:-------------------------------------------------------------------------------------------------------------|
| `dblink`         | is the complete database link name.                                                                          |
| `tns_name_entry` | specifies the Oracle Net connect descriptor specified in the `tnsnames.ora` file that identifies the gateway |

After the database link is created you can verify the connection to the ODBC data source, as follows:

    SQL> SELECT * FROM DUAL@dblink;

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for more information about using database links.

### 11.5 Encrypt Gateway Initialization Parameter Values

The gateway uses user IDs and passwords to access the information in the remote database. Some user IDs and passwords must be defined in the gateway initialization file to handle functions such as resource recovery. In the current security conscious environment, having plain-text passwords that are accessible in the initialization file is deemed insecure. The `dg4pwd` encryption utility has been added as part of Heterogeneous Services to help make this more secure. This utility is accessible by this gateway. The initialization parameters that contain sensitive values can be stored in an encrypted form.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/initialization-parameters.md) for more information about using this utility.

### 11.6 Configure the Gateway to Access Multiple ODBC Data Sources

The tasks for configuring the gateway to access multiple ODBC data sources are similar to the tasks for configuring the gateway for a single data source. The configuration example assumes the following:

- The gateway is installed and configured with the SID of `dg4odbc`.

- The gateway is configured to access one ODBC data source named `dsn1`.

- Two ODBC data sources named dsn2 and dsn3 where dsn2 and dsn3 are the data source names configured in the odbc.ini file, are being added.

#### 11.6.1 Multiple ODBC Data Sources Example: Configuring the Gateway

##### Choose One System ID for Each ODBC Data Source

A separate instance of the gateway is needed for each ODBC data source. Each instance needs its own gateway System ID (SID). For this example, the gateway SIDs are chosen for the instances that access the ODBC data source:

- `dg4odbc2` for the gateway accessing data source `dsn2`.

- `dg4odbc3` for the gateway accessing data source `dsn3`.

##### Create Two Initialization Parameter Files

Create an initialization parameter file for each instance of the gateway by copying the original initialization parameter file `$ORACLE_HOME``/hs/admin/initdg4odbc.ora`, twice, naming one with the gateway SID for `dsn2` and the other with the gateway SID for `dsn3`:

    $ cd ORACLE_HOME/hs/admin
    $ cp initdg4odbc.ora initdg4odbc2.ora
    $ cp initdg4odbc.ora initdg4odbc3.ora

Change the value of the `HS_FDS_CONNECT_INFO` parameter in the new files, as follows:

For `initdg4odbc2.ora`, enter the following:

    HS_FDS_CONNECT_INFO=dsn2

For `initdg4odbc3.ora`, enter the following:

    HS_FDS_CONNECT_INFO=dsn3

**Note:**

If you have multiple gateway SIDs for the same ODBC data source because you want to use different gateway parameter settings at different times, follow the same procedure. You create several initialization parameter files, each with different SIDs and different parameter settings.

#### 11.6.2 Multiple ODBC Data Sources Example: Configuring Oracle Net Listener

##### Add Entries to listener.ora

Add two new entries to the Oracle Net Listener configuration file,`listener.ora`. You must have an entry for each gateway instance, even when multiple gateway instances access the same database.

The following example shows the entry for the original installed gateway first, followed by the new entries.

    SID_LIST_LISTENER=
    (SID_LIST=
       (SID_DESC=
          (SID_NAME=dg4odbc)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
    (ENVS=LD_LIBRARY_PATH=odbc_library_dir:oracle_home_directory/lib)
       )
       (SID_DESC=
          (SID_NAME=dg4odbc2)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
    (ENVS=LD_LIBRARY_PATH=odbc_library_dir:oracle_home_directory/lib)
       )
       (SID_DESC=
          (SID_NAME=dg4odbc3)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4odbc)
    (ENVS=LD_LIBRARY_PATH=odbc_library_dir:oracle_home_directory/lib)
       )
    )

where, `oracle_home_directory` is the directory where the gateway resides.

#### 11.6.3 Multiple ODBC Data Sources Example: Stopping and Starting the Oracle Net Listener

If the listener is already running, use the `lsnrctl` command to stop the listener and then start it with the new settings, as follows:

    $ lsnrctl stop
    $ lsnrctl start

#### 11.6.4 Multiple ODBC Data Sources Example: Configuring Oracle Database for Gateway Access

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

#### 11.6.5 Multiple ODBC Data Sources Example: Accessing ODBC Data

Enter the following to create a database link for the `dg4odbc2` gateway:

    SQL> CREATE PUBLIC DATABASE LINK ODBC2 CONNECT TO
      2  "user2" IDENTIFIED BY "password2" USING 'new_dsn2_using';

Enter the following to create a database link for the `dg4odbc3` gateway:

    SQL> CREATE PUBLIC DATABASE LINK ODBC3 CONNECT TO
      2  "user3" IDENTIFIED BY "password3" USING 'new_dsn3_using';

After the database links are created, you can verify the connection to the new ODBC data sources, as in the following:

    SQL> SELECT * FROM ALL_USERS@ODBC2;

    SQL> SELECT * FROM ALL_USERS@ODBC3;
