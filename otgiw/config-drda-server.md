This section describes tasks you must perform to configure the DRDA server. Each supported operating system is addressed separately. Experience with the given operating system and database is required.

The steps for configuring your remote DRDA server apply to the following DRDA servers:

- DB2 UDB for z/OS

- DB2 UDB for iSeries

- DB2 UDB for Linux, UNIX, and Windows

Configuring a DRDA database to enable access by the gateway requires actions on the DRDA database and on certain components of the host operating system. Although no Oracle software is installed on the host system, access to, and some knowledge of the host system and DRDA database are required during the configuration. Refer to the vendor documentation for complete information about your host system and DRDA database.

Topics:

- Configuring the DRDA Server for DB2 UDB for z/OS

- Configuring the DRDA Server for DB2 UDB for iSeries

- Configuring the DRDA Server for DB2 UDB for Linux\_ UNIX\_ and Windows

- Manual Binding of DRDA Gateway Packages

### Configuring the DRDA Server for DB2 UDB for z/OS

Perform the following tasks to configure the DRDA server with DB2 on a z/OS system:

1.  Define the user ID that owns the package
    During first gateway usage for a particular DRDA server, Oracle supplied packages will be automatically bound to the DRDA server. The user ID and password that are used (either implied as the current Oracle user or explicitly defined in the `CREATE DATABASE LINK` command) must have proper authority on the DRDA Server to create the packages. The followings are minimum authorities needed by this user:

    - Package privileges of `BIND`, `COPY`, and `EXECUTE`, for example:

          GRANT BIND    ON PACKAGE oraclegtw.* TO userid
          GRANT COPY    ON PACKAGE oraclegtw.* TO userid
          GRANT EXECUTE ON PACKAGE oraclegtw.* TO PUBLIC

    - Collection privilege of `CREATE` `IN`, for example:

          GRANT CREATE IN COLLECTION oraclegtw TO USER userid

    - System privileges of `BINDADD` and `BINDAGENT`, for example:

          GRANT BINDADD   TO USER userid
          GRANT BINDAGENT TO USER userid

    - Database privilege of `CREATETAB`, for example:

          GRANT CREATETAB ON DATABASE database TO USER userid

    Optionally, you can choose manual binding of the DRDA Gateway packages. See Manual Binding of DRDA Gateway Packagesfor instruction on how to manually bind packages for DB2 UDB for Linux, Unix, and Windows.

    Choose a user ID that will own the packages and the `HS_TRANSACTION_LOG` table. Ensure that this user ID is defined to both DB2 and OS/390 (MVS).

    The user ID must be granted `SELECT` privilege on the table `SYSIBM.SYSPACKSTMT`.
2.  Define the recovery user ID
    During gateway configuration, the recovery user ID and password are specified in the gateway initialization file using the `HS_FDS_RECOVERY_ACCOUNT` and `HS_FDS_RECOVERY_PWD` parameters. If a distributed transaction fails, then the recovery process connects to the remote database using the user ID and password that are defined in these parameters. This user ID must have execute privileges on the packages and must be defined in the DRDA database. If the user ID is not specified in `HS_FDS_RECOVERY_ACCOUNT`, then the gateway attempts to connect to a user ID of `RECOVER` when a distributed transaction is in doubt.

    Determine the user ID and password that you will use for recovery.

    The `HS_TRANSACTION_LOG` table must be created under the same schema as the recovery user.

    The recovery user ID must be granted `SELECT` privilege on the table `SYSIBM.SYSPACKSTMT`.
3.  Determine DRDA location name for DB2 instance
    The DRDA location name is required as a gateway parameter. To determine the location name, run the following SQL query from a DB2 SPUFI session:

        SELECT CURRENT SERVER FROM any_table

    where `any_table` is a valid table with one or more rows.

    If the value returned by this query is blank or null, then the DRDA location name has not been established. Contact the system administrator to arrange to set a location name for the instance.
4.  Configure DB2 Distributed Data Facility for Gateway
    DB2 Distributed Data Facility (DDF) is the component of DB2 that manages all distributed database operations, both DRDA and non‐DRDA.

    If your site uses DB2 distributed operations, then DDF is probably operational on the DB2 instance that you plan to access through the gateway. If DDF is not operational, then you must configure it and start it as described in the appropriate DB2 documentation.

    Even if DDF is operational on the DB2 instance, it might be necessary to make changes to the DDF Communication Database (CDB) tables to specify the authorization conduct of DRDA sessions from the gateway. Properly authorized users can do this with a utility such as the DB2 SPUFI utility. If you make changes to CDB tables, then you must stop and restart DDF for the changes to take effect. Refer to [Security Considerations](security-consideration-drda-gateway.md), for additional CDB tables and security information.

### Configuring the DRDA Server for DB2 UDB for iSeries

Experience with DB2 UDB for iSeries and AS/400 is required to perform the following steps:

1.  Define the user ID that owns the package
    During the first gateway usage for a particular DRDA server, Oracle supplied packages will be automatically bound to the DRDA server. The user ID and password that are used (either implied as the current Oracle user or explicitly defined in the `CREATE DATABASE LINK` command) must have proper authority on the DRDA server to create packages. The following are minimum authorities needed by this user:

    - Use authority on the `CRTSQLPKG` command

    - Change authority on the library in which the packages will be created

    Choose a user ID now that will own the packages and the `HS_TRANSACTION_LOG` table. Ensure that this user ID is defined in DB2 UDB for iSeries and AS/400.

    The user ID must be granted `SELECT` privilege on the table `QSYS2.SYSPACKAGE`.
2.  Define the recovery user ID
    During gateway configuration, the recovery user ID and password are specified in the gateway initialization file using the `HS_FDS_RECOVERY_ACCOUNT` and `HS_FDS_RECOVERY_PWD` parameters. If a distributed transaction fails, then the recovery process connects to the remote database using the user ID and password that are defined in these parameters. This user ID must have execute privileges on the packages and must be defined to the DRDA database. If the user ID is not specified in `HS_FDS_RECOVERY_ACCOUNT`, then the gateway attempts to connect to a user ID of `RECOVER` when a distributed transaction is in doubt.

    Determine the user ID and password that you will use for recovery.

    The `HS_TRANSACTION_LOG` table must be created under the same schema as the recovery user.

    The recovery user ID must be granted `SELECT` privilege on the table `QSYS2.SYSPACKAGE`.
3.  Determine DRDA location name for DB2 UDB for iSeries instance
    The DRDA location name is required as a gateway parameter. To determine the location name, run the following SQL query from a STRSQL session. If SQL is unavailable on the system, then use the AS/400 command `DSPRDBDIRE` to identify your `LOCAL` DRDA Server.

        SELECT CURRENT SERVER FROM any_table

    where` any_table `is a valid table with one or more rows.

    If the value returned by this query is blank or null, then the DRDA location name has not been established. Contact the system administrator to arrange to set a location name for the instance.

### Configuring the DRDA Server for DB2 UDB for Linux, UNIX, and Windows

Experience with DB2/UDB, configuring the communication subsystem of DB2 UDB for Linux, UNIX, and Windows, and the host System Administration tools is required to perform the following steps.

1.  Define the user ID that owns the package
    During first gateway usage for a particular DRDA server, Oracle supplied packages will be automatically bound to the DRDA server. The user ID and password that are used (either implied as the current Oracle user or explicitly defined in the CREATE DATABASE LINK command) must have proper authority on the DRDA Server to create the packages. The followings are minimum authorities needed by this user:

    - Package privileges of `BIND` and `EXECUTE`, for example:

          GRANT BIND    ON PACKAGE oraclegtw.* TO userid
          GRANT EXECUTE ON PACKAGE oraclegtw.* TO PUBLIC

    - Schema privilege of `CREATEIN`, for example:

          GRANT CREATEIN ON SCHEMA otgdb2 TO USER userid
          GRANT CREATEIN ON SCHEMA oraclegtw TO USER userid

    - Database authorities of `CONNECT`, `BINDADD`, and `CREATETAB`, for example:

          GRANT CONNECT   ON DATABASE TO USER userid
          GRANT BINDADD   ON DATABASE TO USER userid
          GRANT CREATETAB ON DATABASE TO USER userid

    Optionally, you can choose manual binding of the DRDA Gateway packages. See Manual Binding of DRDA Gateway Packagesfor instruction on how to manually bind packages for DB2 UDB for Linux, Unix, and Windows.

    Choose a user ID that will own the packages and `HS_TRANSACTION_LOG` table. Ensure that this user ID is defined in both the DB2 instance ID and the operating system.

    The user ID must be granted `SELECT` privilege on the table `SYSIBM.SYSPLAN`.
2.  Define the recovery user ID
    During gateway configuration, the recovery user ID and password are specified in the gateway initialization file using the `HS_FDS_RECOVERY_ACCOUNT` and `HS_FDS_RECOVERY_PWD` parameters. If a distributed transaction fails, then the recovery process connects to the remote database using the user ID and password that are defined in these parameters. This user ID must have execute privileges on the packages and must be defined to the DRDA database. If the user ID is not specified in `HS_FDS_RECOVERY_ACCOUNT`, then the gateway attempts to connect to a user ID of `RECOVER` when a distributed transaction is in doubt.

    Determine the user ID and password that you will use for recovery.

    The `HS_TRANSACTION_LOG` table must be created under the same schema as the recovery user.

    The recovery user ID must be granted `SELECT` privilege on the table `SYSIBM.SYSPLAN`.
3.  Determine DRDA location name for DB2 UDB for Linux, UNIX, and Windows instance
    The DRDA location name is required as a gateway parameter. To determine the location name, run the following SQL query from a DB2 CLI session:

        SELECT CURRENT SERVER FROM any_table

    where `any_table` is a valid table with one or more rows.

    If the value returned by this query is blank or null, then the DRDA location name has not been established. Contact your system administrator to set a location name for the instance.

### Manual Binding of DRDA Gateway Packages

The gateway uses several DB2 packages, which it normally uploads and binds during the first time the gateway connects to a DB2 instance. In some customer environments, the connecting userid may not have the necessary privileges to perform the binding, or some customers may prefer to manually bind the packages rather than allow the gateway to do the binding.

In such cases, Oracle provides a predefined set of packages for manual binding. These packages come with several restrictions that must be observed by setting specific gateway initialization parameters to set values otherwise, the gateway will attempt to rebind the package automatically.

This section contains the following sub-sections:

- Manually Binding of Packages for DB2 UDB for z/OS

- Manually Binding of Packages for DB2 UDB for Linux\_ Unix\_ and Windows

#### Manually Binding of Packages for DB2 UDB for z/OS

Perform the following steps to manually bind packages for DB2 UDB for z/OS:

1.  Allocate a sequential dataset on z/OS using the parameters `DSORG=PS`, `RECFM=FB`, `LRECL=80`, and `BLKSIZE=3120`. For example,
        userid.DBRMFILE.XMIT
2.  Allocate a Partitioned DataSet using the parameters `DSORG=PO`, `RECFM=FB`, `LRECL=80`, and `BLKSIZE=6160`. for example,
        userid.TG4DRDA.CNTL
3.  FTP the following file to the previously allocated sequential dataset in `BINARY` mode:
        ORACLE_HOME\dg4db2\admin\dg4db2_zos_dbrm.xmit

    Use the `PUT` command to replace the sequential dataset contents.
4.  FTP the following file to the previously allocated PDS in ASCII mode:
        ORACLE_HOME\dg4db2\admin\dg4db2_zos_bind.jcl

    Use the `PUT` command to place the file into the PDS as member name `BIND`.
5.  Use the TSO command option of ISPF (option 6) to issue the `RECEIVE` command:
        RECEIVE INDS('userid.DBRMFILE.XMIT')

    Specify DA(`userid.DDODBC.DBRMLIB`) as the parameters to the `RECEIVE` command. This will unpack the xmit file and create the specified PDS name.
6.  Edit the `BIND JCL` (`userid.TG4DRDA.CNTL(BIND)`)and follow the instructions to update the `JCL`. Once updated, submit the `JCL` to perform the actual binding of the packages and granting of execution privileges on the packages.

To use these packages with the gateway, please set the following init parameters in the gateway initialization file:

- `HS_OPEN_CURSORS=200`

- `HS_FDS_PACKAGE_COLLID=NULLID`

#### Manually Binding of Packages for DB2 UDB for Linux, Unix, and Windows

Perform the following steps to manually bind packages for DB2 UDB for Linux, Unix, and Windows:

1.  Copy the following files to the host running the DB2 instance from the `ORACLE_HOME``\dg4db2\admin` directoy:
         DDOC510A.bnd
         DDOC510B.bnd
         DDOC510C.bnd
         DDON510A.bnd
         DDON510B.bnd
         DDON510C.bnd
         DDOR510A.bnd
         DDOR510B.bnd
         DDOR510C.bnd
         DDOS510A.bnd
         DDOS510B.bnd
         DDOS510C.bnd
         DDOU510A.bnd
         DDOU510B.bnd
         DDOU510C.bnd
         dg4db2_luw_pkglist.lst

    If copying via FTP, then files ending in `.bnd` should be transfered in BINARY mode and files ending in `.lst` should be transfered in ASCII mode.
2.  Connect to the DB2 instance and issue the bind command. For example,
        db2 'connect to <database_name> user <userid> using <password>'
        db2 'bind @dg4db2_luw_pkglist.lst grant public'

To use these packages with the gateway, set the following initialization parameters in the gateway initialization file:

- `HS_OPEN_CURSORS=200`

- `HS_FDS_PACKAGE_COLLID=NULLID`
