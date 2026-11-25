After installing the gateway, perform the following tasks to configure Oracle Database Gateway for DRDA:

1.  Configure the Gateway Initialization Parameter File

2.  Configure Oracle Net for the Gateway

3.  Configure Two-Phase Commit

4.  Create Tables and Views for Data Dictionary Support

5.  Configure the Oracle Database for Gateway Access

6.  Create Database Links

7.  Configure the Gateway to Access Multiple DRDA Databases

SQL scripts are provided to perform steps such as creating the `HS_TRANSACTION_LOG` table, removing obsolete tables and views, and creating tables and views to provide data dictionary support.

These scripts must be run on the DRDA Server platform using a database native tool (such as SPUFI on DB2 UDB for z/OS), because no tool is provided with the gateway to execute these scripts. Note that when running these scripts, the user ID used must be suitably authorized.

SQL scripts are located in the `dg4db2/admin` directory. Appropriate platform scripts are designated by having the DB2 platform identifiers (eg: "zos", "as400" and "luw") and version specific numbers (eg: vw7, vw8) in their file names.

### 14.1 Configure the Gateway Initialization Parameter File

Perform the following tasks to configure the gateway initialization parameter file:

1.  Choose a System Identifier for the Gateway
2.  Customize the Initialization Parameter File

#### 14.1.1 Choose a System Identifier for the Gateway

The gateway system identifier (SID) is an alphanumeric character string that identifies a gateway instance. You need one gateway instance, and therefore one gateway SID, for each DRDA database you are accessing. However, if you want to access two DRDA databases, you need two gateway SIDs, one for each instance of the gateway. If you have one DRDA database and want to access it sometimes with one set of gateway parameter settings, and other times with different gateway parameter settings, you can do that by having multiple gateway SIDs for the single DRDA database. The SID is used as part of the file name for the initialization parameter file.

#### 14.1.2 Customize the Initialization Parameter File

Tailor the parameter file with additional parameters as needed. Refer to [Initialization Parameters](initialization-parameters-for-gateways.md) for a list of supported initialization parameters. Also refer to [Security Considerations](drda-gateway-security-consideration.md) for security aspects to tailoring the parameter file.

### 14.2 Configure Oracle Net for the Gateway

The gateway requires Oracle Net to communicate with the Oracle database. After configuring the gateway, perform the following tasks to configure Oracle Net to work with the gateway:

1.  Configure Oracle Net Listener for the Gateway
2.  Stop and Start the Oracle Net Listener for the Gateway

#### 14.2.1 Configure Oracle Net Listener for the Gateway

The Oracle Net Listener listens for incoming requests from the Oracle database. For the Oracle Net Listener to listen for the gateway, information about the gateway must be added to the Oracle Net Listener configuration file, `listener.ora`. This file by default is located in `$ORACLE_HOME/network/admin`, where `$ORACLE_HOME` is the directory under which the gateway is installed.

The following entries must be added to the `listener.ora` file:

- A list of Oracle Net addresses on which the Oracle Net Listener listens

- The executable name of the gateway that the Oracle Net Listener starts in response to incoming connection requests

A sample of the `listener.ora` entry (`listener.ora.sample`) is available in the `$ORACLE_HOME/dg4db2/admin` directory where `$``ORACLE_HOME` is the directory under which the gateway is installed.

##### 14.2.1.1 Syntax of listener.ora File Entries

The Oracle database communicates with the gateway using Oracle Net and any supported protocol adapters. The syntax of the address on which the Oracle Net Listener listens using the TCP/IP protocol adapter is as follows:

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

You must use the same SID value in the `listener.ora` file and the `tnsnames.ora` file that will be configured in the next step.

    SID_LIST_LISTENER=
       (SID_LIST=
          (SID_DESC=
             (SID_NAME=gateway_sid)
             (ORACLE_HOME=oracle_home_directory)
             (PROGRAM=dg4db2)
          )
       )

where:

| Variable                | Description                                                                                                                        |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `gateway_sid`           | specifies the SID of the gateway and matches the gateway SID specified in the connect descriptor entry in the `tnsnames.ora `file. |
| `oracle_home_directory` | specifies the Oracle home directory where the gateway resides.                                                                     |
| `dg4db2`                | specifies the executable name of the Oracle Database Gateway for DRDA.                                                             |

If you are already running a Oracle Net Listener that listens on multiple database SIDs, add only the following syntax to `SID_LIST` in the existing `listener.ora` file:

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
          (PROGRAM=dg4db2)
       )
    )

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for information about changing the `listener.ora` file.

#### 14.2.2 Stop and Start the Oracle Net Listener for the Gateway

You must stop and restart the Oracle Net Listener to initiate the new settings, as follows:

1.  Set the `PATH` environment variable to `$ORACLE_HOME/bin` where `$ORACLE_HOME` is the directory in which the gateway is installed. If you have the Bourne or Korn Shell, enter the following:
        $ PATH=$ORACLE_HOME/bin:$PATH;export PATH
        $ LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH; export LD_LIBRARY_PATH

    If you have the C Shell, enter the following:

        $ setenv PATH $ORACLE_HOME/bin:$PATH
        $ setenv LD_LIBRARY_PATH $ORACLE_HOME/lib:$LD_LIBRARY_PATH

    Table 14-1 specifies which parameter value to use for the different platforms:

    Table 14-1 Oracle Database Gateway for DRDA Parameter Values for UNIX Based Platforms

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

    The following is a partial output from a `lsnrctl` status check:

<!-- -->

    .
    .
    .
    Listening Endpoints Summary...
      (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=204.179.99.15)(PORT=1551)))
    Services Summary...
    Service "dg4db2" has 1 instance(s).
      Instance "dg4db2", status UNKNOWN, has 1 handler(s) for this service...
    The command completed successfully

In this example, the service name is `dg4db2`, which is the default SID value assigned during installation.

**Note:**

You must use the same SID value in the `tnsnames.ora` file and the `listener.ora` file.

### 14.3 Configure Two-Phase Commit

Support for Two-Phase Commit requires running the `$ORACLE_HOME/dg4db2/admin/dg4db2_tx.sql` script on the DB2 server. This script will create objects used by the gateway for Two-Phase Commit. Edit the script and replace the default recover account schema (`RECOVER`) with the account name specified for the `HS_FDS_RECOVERY_ACCOUNT` initialization parameter. Refer to [Initialization Parameters](initialization-parameters-for-gateways.md) for more details..

### 14.4 Create Tables and Views for Data Dictionary Support

To enable data dictionary translation support, data dictionary tables and views have to be created on each non-Oracle system that you want to access through the gateway.

Perform the following steps to create the data dictionary tables and views using database native tools:

1.  Upgrade from a previous gateway release
    If you are upgrading from a previous version of the gateway then run the appropriate script to drop the old data dictionary definitions.

    - If connecting to DB2 UDB for Linux, Unix, and Windows, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_luw_drop.sql

    - If connecting to DB2 UDB for z/OS, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_drop.sql

    - If connecting to DB2 UDB for iSeries, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_as400_drop.sql
2.  Create the data dictionary tables
    Run the appropriate script to create the data dictionary tables.

    - If connecting to DB2 UDB for Linux, Unix, and Windows, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_luw_tab.sql

    - If connecting to DB2 UDB for z/OS, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_tab.sql

    - If connecting to DB2 UDB for iSeries, then run

          $ORACLE_HOME/dg4db2/admin/dg4db2_as400_tab.sql
3.  Create the data dictionary views
    Run the appropriate script to create the data dictionary views.

    - If connecting to DB2 UDB for Linux, Unix, and Windows, then run

      For DB2 UDB for Linux, Unix, and Windows V7:

          $ORACLE_HOME/dg4db2/admin/dg4db2_luw_vw7.sql

      For DB2 UDB for Linux, Unix, and Windows V8 and V9:

          $ORACLE_HOME/dg4db2/admin/dg4db2_luw_vw8.sql

    - If connecting to DB2 UDB for z/OS then run

      For DB2 UDB for z/OS V7 (RACF security):

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_vw7r.sql

      For DB2 UDB for z/OS V7 (DB2 security):

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_vw7s.sql

      For DB2 UDB for z/OS V8 and V9 (RACF security):

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_vw8r.sql

      For DB2 UDB for z/OS V8 and V9 (DB2 security):

          $ORACLE_HOME/dg4db2/admin/dg4db2_zos_vw8s.sql

    - If connecting to DB2 UDB for iSeries, then run

      For DB2 UDB for iSeries V5.1:

          $ORACLE_HOME/dg4db2/admin/dg4db2_as400_vw51.sql

      For DB2 UDB for iSeries V5.2:

          $ORACLE_HOME/dg4db2/admin/dg4db2_as400_vw52.sql

      For DB2 UDB for iSeries V5.3 or higher:

          $ORACLE_HOME/dg4db2/admin/dg4db2_as400_vw53.sql

### 14.5 Configure the Oracle Database for Gateway Access

Before you use the gateway to access DB2 data you must configure the Oracle database to enable communication with the gateway over Oracle Net.

To configure the Oracle database you must add connect descriptors to the `tnsnames.ora` file. By default, this file is in `$ORACLE_HOME/network/admin`, where `$ORACLE_HOME` is the directory in which the Oracle database is installed. You cannot use the Oracle Net Assistant or the Oracle Net Easy Config tools to configure the `tnsnames.ora` file. You must edit the file manually.

A sample of the `tnsnames.ora` entry (`tnsnames.ora.sample`) is available in the `$ORACLE_HOME/dg4db2/admin` directory where `$``ORACLE_HOME` is the directory under which the gateway is installed.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for information about editing the `tnsnames.ora` file.

#### 14.5.1 Configuring tnsnames.ora

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

where:

| Variable             | Description                                                                                                                                                                                                                                                                                                |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `connect_descriptor` | is the description of the object to connect to as specified when creating the database link, such as `dg4db2`.<br>Check the sqlnet.orafile for the following parameter setting:<br>• `names.directory_path = (TNSNAMES)`<br>Note: The sqlnet.ora file is typically stored in `$ORACLE_HOME/network/admin`. |
| `TCP`                | is the TCP protocol used for TCP/IP connections.                                                                                                                                                                                                                                                           |
| `host_name`          | specifies the machine where the gateway is running.                                                                                                                                                                                                                                                        |
| `port_number`        | matches the port number used by the Oracle Net Listener that is listening for the gateway. The Oracle Net Listener's port number can be found in the `listener.ora` file used by the Oracle Net Listener. See Syntax of listener.ora File Entries.                                                         |
| `gateway_sid`        | specifies the SID of the gateway and matches the SID specified in the `listener.ora` file of the Oracle Net Listener that is listening for the gateway. See Configure Oracle Net Listener for the Gateway for more information.                                                                            |
| `(HS=OK)`            | specifies that this connect descriptor connects to a non-Oracle system.                                                                                                                                                                                                                                    |

#### 14.5.2 Configuring tnsnames.ora for Multiple Listeners

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

### 14.6 Create Database Links

Any Oracle client connected to the Oracle database can access DB2 data through the gateway. The Oracle client and the Oracle database can reside on different machines. The gateway accepts connections only from the Oracle database.

A connection to the gateway is established through a database link when it is first used in an Oracle session. In this context, a connection refers to the connection between the Oracle database and the gateway. The connection remains established until the Oracle session ends. Another session or user can access the same database link and get a distinct connection to the gateway and DRDA database.

Database links are active for the duration of a gateway session. If you want to close a database link during a session, you can do so with the `ALTER SESSION` statement.

To access the DRDA server, you must create a database link. A public database link is the most common of database links.

    SQL> CREATE PUBLIC DATABASE LINK dblink CONNECT TO
    2  "user" IDENTIFIED BY "password" USING 'tns_name_entry';

where:

| Variable         | Description                                                                                                  |
|:-----------------|:-------------------------------------------------------------------------------------------------------------|
| `dblink`         | is the complete database link name.                                                                          |
| `tns_name_entry` | specifies the Oracle Net connect descriptor specified in the `tnsnames.ora` file that identifies the gateway |

After the database link is created you can verify the connection to the DRDA database, as follows:

    SQL> SELECT * FROM DUAL@dblink;

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for more information about using database links.

### 14.7 Configure the Gateway to Access Multiple DRDA Databases

The tasks for configuring the gateway to access multiple DRDA databases are similar to the tasks for configuring the gateway for a single database. The configuration example assumes the following:

- The gateway is installed and configured with the default SID of `dg4db2`

- The `ORACLE_HOME` environment variable is set to the directory where the gateway is installed

- The gateway is configured for one DRDA database named `db1`

- Two DRDA databases named `db2` and `db3` on a host with IP Address 204.179.79.15 are being added

#### 14.7.1 Multiple DRDA Databases Example: Configuring the Gateway

##### Choose One System ID for Each DRDA Database

A separate instance of the gateway is needed for each DRDA database. Each instance needs its own gateway System ID (SID). For this example, the gateway SIDs are chosen for the instances that access the DRDA databases:

- `dg4db22`for the gateway accessing database `db2`

- `dg4db23` for the gateway accessing database `db3`

##### Create Two Initialization Parameter Files

Create an initialization parameter file for each instance of the gateway by copying the original initialization parameter file, ` $ORACLE_HOME/dg4db2/admin/initdg4db2.ora`, twice, naming one with the gateway SID for `db2` and the other with the gateway SID for `db3`:

    $ cd $ORACLE_HOME/dg4db2/admin
    $ cp initdg4db2.ora initdg4db22.ora
    $ cp initdg4db2.ora initdg4db23.ora

**Note:**

If you have multiple gateway SIDs for the same DRDA database because you want to use different gateway parameter settings at different times, follow the same procedure. You create several initialization parameter files, each with different SIDs and different parameter settings.

#### 14.7.2 Multiple DRDA Databases Example: Configuring Oracle Net Listener

##### Add Entries to listener.ora

Add two new entries to the Oracle Net Listener configuration file,`listener.ora`. You must have an entry for each gateway instance, even when multiple gateway instances access the same database.

The following example shows the entry for the original installed gateway first, followed by the new entries:

    SID_LIST_LISTENER=
    (SID_LIST=
       (SID_DESC=
          (SID_NAME=dg4db2)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4db2)
       )
       (SID_DESC=
          (SID_NAME=dg4db22)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4db2)
       )
       (SID_DESC=
          (SID_NAME=dg4db23)
          (ORACLE_HOME=oracle_home_directory)
          (PROGRAM=dg4db2)
       )
    )

where, `oracle_home_directory` is the directory where the gateway resides.

#### 14.7.3 Multiple DRDA Databases Example: Stopping and Starting the Oracle Net Listener

If the listener is already running, use the `lsnrctl` command to stop the listener and then start it with the new settings, as follows:

    $ lsnrctl stop
    $ lsnrctl start

#### 14.7.4 Multiple Databases Example: Configuring Oracle Database for Gateway Access

Examples:

- Configuring Oracle Net for Multiple Gateway Instances

##### 14.7.4.1 Configuring Oracle Net for Multiple Gateway Instances

Add two connect descriptor entries to the `tnsnames.ora` file. You must have an entry for each gateway instance, even if the gateway instances access the same database.

The following DRDA example shows the entry for the original installed gateway first, followed by the two entries for the new gateway instances:

    old_db_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4db2))
                   (HS=OK))
    new_db2_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4db22))
                    (HS=OK))
    new_db3_using=(DESCRIPTION=
                  (ADDRESS=
                    (PROTOCOL=TCP)
                    (PORT=port_number)
                    (HOST=host_name))
                    (CONNECT_DATA=
                        (SID=dg4db23))
                    (HS=OK))

The value for `PORT` is the TCP/IP port number of the Oracle Net Listener that is listening for the gateway. The number can be found in the `listener.ora` file used by the Oracle Net Listener. The value for `HOST` is the name of the machine on which the gateway is running. The name also can be found in the `listener.ora` file used by the Oracle Net Listener.

#### 14.7.5 Multiple DRDA Databases Example: Accessing DB2 Data

Enter the following to create a database link for the `dg4db22` gateway:

    SQL> CREATE PUBLIC DATABASE LINK DRDA2 CONNECT TO
      2  "user2" IDENTIFIED BY "password2" USING 'new_db2_using';

Enter the following to create a database link for the `dg4db23` gateway:

    SQL> CREATE PUBLIC DATABASE LINK DRDA3 CONNECT TO
      2  "user3" IDENTIFIED BY "password3" USING 'new_db3_using';

After the database links are created, you can verify the connection to the new DRDA databases, as in the following:

    SQL> SELECT * FROM ALL_USERS@DRDA2;

    SQL> SELECT * FROM ALL_USERS@DRDA3;
