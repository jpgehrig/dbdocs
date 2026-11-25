Consider installation, configuration, and administration of Oracle Database Provider for DRDA.

### 3.1 About Installing Oracle Database Provider for DRDA

Oracle Database Provider for DRDA is bundled with the Oracle Database software. Installation involves starting the Oracle Universal Installer and entering the Oracle home path.

Note that the following procedure creates the `drdaas.ora` configuration file in the directory `$``ORACLE_HOME``/drdaas/admin/`.

**Related Topics**

- Configuration File: drdaas.ora

#### 3.1.1 Installing Oracle Database Provider for DRDA

1.  Start Oracle Universal Installer.
2.  Enter the path of an existing `ORACLE_HOME`, or a new path for a stand-alone installation.
3.  \[Optional\] Enter the `ORACLE_HOME` name.
4.  Select Software Only Install.
5.  Select Finish.
6.  At the command prompt, create a diagnostic directory:
        % mkdir -p $ORACLE_HOME/log/diag/dps

### 3.2 Configuring Oracle Database Provider for DRDA

To configure Oracle Database Provider for DRDA, you must update the `drdaas.ora` configuration file with any necessary information.

Additionally, you must install the objects that depend on Oracle Database Provider for DRDA product in all Oracle Database instances that use Oracle Database Provider for DRDA.

#### 3.2.1 Updating the drdaas.ora Configuration File

Create the `drdaas.ora` configuration file and add initial instance and configuration parameters.

In more advanced scenarios, it may be necessary to specify more than one `DATA_PORT` parameter or configure more than one `RDB_MAP` entry. Still more complex installations may require multiple Oracle Database Provider for DRDA instances.

For a list of parameters and their options, refer to the section Configuration Parameters.

**Related Topics**

- Configuration Parameters

##### 3.2.1.1 DATA_PORT Considerations

Additional `DATA_PORT` entries may be specified with different host name or IP addresses, and unallocated network port numbers. This is called a Multiplexed Instance configuration.

##### 3.2.1.2 RDB_MAP Considerations

Additional `RDB_MAP` entries may be specified to add other map entries for converting between third-party relational databases and Oracle.

**Note:**

For some DRDA clients, such as the IBM DB2 Database for z/OS, the user must configure only one `RDB_MAP` entry for each Oracle Database Provider for DRDA instance. This is called a Dedicated Instance configuration.

##### 3.2.1.3 Oracle Database Provider for DRDA Instance Considerations

It may be necessary to define more than one Oracle Database Provider for DRDA Instance to accommodate an environment that contains both types of DRDA clients. Therefore, Oracle Database Provider for DRDA product supports the definition of multiple instance configurations in the same `drdaas.ora` configuration file.

#### 3.2.2 Installing Database Objects

There are two sets of database objects that must be installed: Global Objects and Per-User Objects.

##### 3.2.2.1 About Global Objects

Each instance of Oracle Database used in an Oracle Database Provider for DRDA configuration must install Oracle Database Provider for DRDA specific objects. This involves the following procedures:

- Creating a `SYSIBM` tablespace

- Installing Oracle Database Provider for DRDA catalogs

- Installing DB2 SQL translator

- Designate Oracle Database Provider for DRDA administrative role

**Related Topics**

- [Security and Storage Considerations for Oracle Database Provider for DRDA](security-and-storage-considerations.md)

##### 3.2.2.2 Creating a SYSIBM tablespace

1.  Connect to the database; this example uses `SYSDBA` privileges, but they are not necessary.
        > connect SYS as SYSDBA
2.  Create the tablespace `SYSIBM`.
        > create tablespace SYSIBM datafile 'sysibm01.dbf' size 70M reuse extent management local segment space management auto online;

    This creates tablespace `SYSIBM` in the directory specified by the parameter `DB_CREATE_FILE_DEST`.

**Related Topics**

- [SYSIBM Tablespace](security-and-storage-considerations.md)

##### 3.2.2.3 Installing Oracle Database Provider for DRDA Catalogs

1.  Change directory to `$``ORACLE_HOME``/rdbms/admin`
        $ cd $ORACLE_HOME/rdbms/admin
2.  Connect to the database with `SYSDBA` privileges.
        > connect SYS as SYSDBA
3.  Invoke the following SQL script:
        > @catdrdaas.sql
4.  If using Oracle Database Release 12c, invoke the following SQL script:
        > @prvtdpsadzoscat.plb

    If using Oracle Database Release 11.2, invoke the following SQL script:

        > @prvtdpsadzoscat11.plb

**Related Topics**

- [catdrdaas.sql](scripts-to-create-and-maintain-database-provider-for-DRDA.md)

##### 3.2.2.4 Installing DB2 SQL translator

The DB2 SQL Translator is available starting from Oracle Database 12c.

**Note:**

The SQL Translator is an optional feature that you can use, when the SQL used within the application consists of a lot of DB2 specific syntax.

1.  Change directory to `$``ORACLE_HOME``/drdaas/admin`
        $ cd $ORACLE_HOME/drdaas/admin
2.  Connect to the database with `SYSDBA` privileges.
        > connect SYS as SYSDBA
3.  Invoke the following SQL script, and answer its prompts:
        > @drdasqtt_translator_setup.sql

    The script `drdasqtt_translator_setup.sql` is demonstrated in the section Code for SQL Translation Interface Package and a Translation Profile.

**Related Topics**

- Creating a SQL Translation Interface Package and Translation Profile

##### 3.2.2.5 Designating Oracle Database Provider for DRDA Administrative Role

1.  Designate one or more user IDs to be an Oracle Database Provider for DRDA administrator. This role may set the access authority for DRDA packages and associated DRDA package attributes. Oracle user `SYSTEM` may be used, but the privilege may be granted to any user who performs the functions of DRDA administrator.
2.  Grant initial DRDA package binding authority. Invoke the following SQL script and answer the prompts:
        > @drdapkg_db2.sql

        SQL> Prompt Enter the OracleID under which the initial package BINDs will be made
        SQL> Use quotes (') if needed.
        SQL> Accept OracleID
        DRDAUSR

        SQL> Enter default collection ID for package binding (usually NULLID)
        SQL> Use quotes (') if needed.
        SQL> Accept DefaultCollection
        NULLID

**Related Topics**

- [DBMS_DRDAAS_ADMIN Package](PLSQL-packages-used.md)

#### 3.2.3 SQL Translation Profile

To facilitate correct interpretation of DRDA-based application SQL from it's native DB2 dialect to Oracle, the user must create a SQL Translation Profile.

SQL Translation Profiles are managed on a per-user basis. In contrast, DRDA packages are managed on the application basis. As a result, only one SQL translation profile name may be associated with a specific DRDA package. The same SQL Translation Profile may be also associated with many packages; for consistency, the same SQL Translation Profile should be associated with each defined package.

To create an additional translation profile, DRDA users must request a profile name from the DRDA administrator and then invoke the `drdasqtt_translator_setup.sql` script, in `$``ORACLE_HOME``/drdaas/admin/` directory. The section ‘Create a SQL Translation Interface Package and Translation Profile demonstrates how to create a SQL Translation Profile for profile name `DB2ZOS`; this code creates the template of a translation profile.

**Note:**

SQL Translation Profile is an optional feature, and can be used only when the SQL Translation Feature is configured.

**Related Topics**

- Creating a SQL Translation Interface Package and Translation Profile

##### 3.2.3.1 Prerequisites for Creating a SQL Translation Profile

This feature is available to users of Oracle Database 12c or higher.

The user must have `DRDAAS_USER_ROLE`, as described in the section Authorizing Oracle Database Provider for DRDA.

A DB2 SQL Translator must be loaded into the database. The user may create a translation profile using this translator.

##### 3.2.3.2 Creating a SQL Translation Interface Package and Translation Profile

Example 3-1 creates a SQL Translator Interface Package `SYSIBM.DBTooIntPkg`, and a SQL Translation Profile `TRANS_ADMIN.MyDBTooTransProfile`. It assumes that the third-party SQL translator is in JAVA, and that it appears entirely within an object `ThirdPartyDB2Translator.class` in the `rdbms/drdaas/jlib` directory.

Additional translations may be added, changed, or removed as needed. Please refer to the Oracle® Database SQL Translation and Migration Guide for details.

Example 3-1 Code for SQL Translation Interface Package and a Translation Profile

The following two lines describe the signatures of the two translator methods within the third-party object:

    ThirdPartyTranslator.translateSQL(oracle.sql.CLOB,oracle.sql.CLOB[])
    ThirdPartyTranslator.translateError(int,int[],java.lang.String[])

These signatures determine the method Oracle calls to translate both SQL text and Oracle Error codes. The method `translateSQL()`has two arguments: a `CLOB` for the original SQL text, and a `CLOB` for the CLOB output from the SQL translator. The second method may be ignored.

    connect / as sysdba
    @$ORACLE_HOME/drdaas/admin/drdasqtt_translator_setup.sql

    Enter schema in which the SQL Translator Interface Package will be created as well
    as into which the third-party SQL translator will be loaded (usually SYSIBM).
    SQL Translator Interface Package Schema:SYSIBM

    Enter unqualified name of the SQL Translator Interface Package
    SQL Translator Interface Package Name:DBTooIntPkg

    Enter schema in which the Translation Profile will be created:
    Translation Profile Schema:TRANS_ADMIN

    Enter the unqualified name of the translation profile:
    Translation Profile Name:MyDBTooTransProfile

    Enter the "language" type of the translator: C, java, etc
    Translator Language:JAVA

    Enter the path names of the third-party SQL Translator objects;
    (All objects must be located under the "rdbms/" directory,
    for example: "rdbms/drdaas/jlib/objecta.jar").

    Enter all path qualified objects, one per prompt, up to 10.

    Enter "" for all remaining object prompts.
    SQL Translator object#1: rdbms/drdaas/jlib/ThirdPartyDB2Translator.class
    SQL Translator object#2: ""
    ...
    SQL Translator object#10: ""

    Enter the signature for the entry for 'translateSQL' in one of the
    previously entered SQL Translator objects:
    Entry for
     translateSQL:ThirdPartyTranslator.translateSQL(oracle.sql.CLOB,oracle.sql.CLOB[])

    Enter the signature for the entry for 'translateError' in one of the
    previously entered SQL Translator objects callout for
     translateError:ThirdPartyTranslator.translateError(int,int[],java.lang.String[])

#### 3.2.4 Configuration File: drdaas.ora

The file `drdaas.ora` defines the instances of Oracle Database Provider for DRDA. This file is composed of initialization parameters that define the instances of the Application Server.

The file `drdaas.ora` may be customized. However, it may also be created at installation time from questions posed by the Installer and from user input.

The `drdaas.ora` configuration file must be located in the Oracle Home, under the product administration directory.

The default location is: `$ORACLE_HOME/drdaas/admin`.

Note that parameters that are qualified by the instance name apply only to that specific instance. Parameters that are not qualified by an instance name apply to all instances specified in the file.

Example 3-2 Sample configuration file, drdaas.ora

    # Example pre-configured instance named "drdaas"
    # defines a single port and an rdb map that uses
    # the local database instance accessed through
    # the ORACLE_SID environmental variable.
    drdaas.DATA_PORT = 10.0.0.1:1446
    drdaas.RDB_MAP = RDB(DB2DS4M)->ORACLE_SID
    #
    # Example instance using a single port and a single rdb map
    drdasingle.DATA_PORT = 10.0.0.1:1546
    drdasingle.RDB_MAP = RDB(DB2DSN1)->TNS(ora101)
    #
    # Example instance using multiple rdb mappings
    drdamulti.DATA_PORT = 10.0.0.1:2446
    drdamulti.RDB_MAP = RDB(DB2DSN1)->TNS(ora101)
    drdamulti.RDB_MAP = RDB(DB2DSN2)->TNS(ora102)
    drdamulti.RDB_MAP = RDB(DB2DSN3)->TNS(ora103)
    #
    # global section affects all instances unless overridden
    PROTOPROC_TRACE="ALL ERROR"

### 3.3 Authorizing Oracle Database Provider for DRDA

Oracle users must have the appropriate Oracle Database Provider for DRDA role in order to access Oracle Database Provider for DRDA catalogs and specific DRDA packages.

**Related Topics**

- About Global Objects

#### 3.3.1 Administrator Role

Users who must perform administrative functions must have the `DRDAAS_ADMIN_ROLE` role. This enables privilege grants on a specific DRDA package, and assigning package attributes (SQL translation profile name).

For installations that do not have the default role `ALL`, have several default roles for users, such as `CONNECT` or `RESOURCE`, and add the add `DRDAAS_ADMIN_ROLE` role to the default list.

The `DRDAAS_ADMIN_ROLE` role is not meant for users who must use the DRDA packages. They should have the `DRDAAS_USER_ROLE` assignment, instead.

Administration is mainly concerned with granting and revoking of privilege to users, setting attributes on packages, and dropping packages.

Users who create packages, or are designated as owners of a package, have implicit authority over that package and may grant access to others. For example, the package owner may grant `RUN` privileges to any number of users. An owner may also set package attributes and drop the package.

However, in order to bind a package initially, a user must have `BIND` privilege, either for any package in a collection, or specifically for that package. Only users who have the `DRDAAS_ADMIN_ROLE` role may grant authorization to users for packages that are not already bound, or are not created or owned by that user. For information on how to grant access to a package and how to set package attributes, refer DRDA Package Authorization.

**Related Topics**

- Granting DRDAAS_ADMIN_ROLE
- Adding DRDAA_ADMIN_ROLE
- Adding DRDAAS_USER_ROLE
- DRDA Package Authorization

##### 3.3.1.1 Granting DRDAAS_ADMIN_ROLE

Example 3-3 Granting the DRDAAS_ADMIN_ROLE

    connect sys as sysdba
    grant DRDAAS_ADMIN_ROLE to DRDAADMIN;

##### 3.3.1.2 Adding DRDAA_ADMIN_ROLE

Example 3-4 Adding DRDAAS_ADMIN_ROLE to Default Values

    alter user DRDAADMIN default role CONNECT, DRDAAS_ADMIN_ROLE;

##### 3.3.1.3 Dropping ORACLE.MYPACKAGE by Administrator

This function should be performed by a user with DRDA administrator role.

Example 3-5 Dropping package ORACLE.MYPACKAGE, as Administrator

    connect DRDAADM/password
    execute DBMS_DRDAAS_ADMIN.DROP_PACKAGE('ORACLE','MYPACKAGE);
    commit;

##### 3.3.1.4 Dropping ORACLE.MYPACKAGE by User

This function should be performed by a user with DRDA user role. This operation fails if user `DRDAUSR2` does not own package `ORACLE.MYPACKAGE`, if the user is not the creator of this package, or if the user has no `DROP` privilege for this package.

Example 3-6 Dropping package ORACLE.MYPACKAGE, as User

    connect DRDAUSR2/password
    execute DBMS_DRDAAS.DROP_PACKAGE('ORACLE','MYPACKAGE);
    commit;

##### 3.3.1.5 Maintaining DRDA Packages

Another primary responsibility of an administrator is to clean old or unused packages from the system. A list of all packages may be found by querying table `ALL_DRDAASPACKAGE`:

    SELECT * from ALL_DRDAASPACKAGE;

#### 3.3.2 DRDA Package Authorization

The DRDA administrator must perform these functions before supplying the user with the DRDA package name and (optionally) the SQL translation profile name.

Only a DRDA administrator may grant access to specific DRDA packages.

Refer the section on Granting and Revoking a User’s Package Privileges to understand how to grant the `BIND`, `DROP` and `EXECUTE` privileges to user `DRDAUSR``x` for package `ORACLE.MYPACKAGE`.

The DRDA Administrator may also designate a SQL translation profile name to associate with the DRDA package.

Refer the section on Setting and Deleting Translation Profile Name for a DRDA Package to understand how to set the profile name to `DB2ZOS`.

**Related Topics**

- Managing a User’s Package Privileges

##### 3.3.2.1 Managing a User’s Package Privileges

Example 3-7 Granting and Revoking a User's Package Privileges

    connect DRDAADM/password

    Rem Grant BIND on any package in collection ORACLE to DRDAUSR
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.BIND_PRIVILEGE, 'ORACLE', '*', 'DRDAUSR');

    Rem Grant BIND on package ORACLE.MYPACKAGE to user DRDAUSR2
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.BIND_PRIVILEGE, 'ORACLE', 'MYPACKAGE', 'DRDAUSR2');

    Rem Grant EXECUTE on package ORACLE.MYPACKAGE to PUBLIC
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.EXECUTE_PRIVILEGE, 'ORACLE', 'MYPACKAGE', 'PUBLIC');

    Rem Grant SET on package ORACLE.MYPACKAGE to user DRDAUSR3
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.SET_PRIVILEGE, 'ORACLE', 'MYPACKAGE', 'DRDAUSR3');

    Rem Grant DROP on any package in collection ORACLE to user DRDAUSR3
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.DROP_PRIVILEGE, 'ORACLE', '*', 'DRDAUSR3');

    Rem Grant ALL on any package in collection NULLID to user DRDAUSR3
    execute DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'NULLID', '*', 'DRDAUSR3');

    Rem Revoke BIND on package ORACLE.NOTYOURPKG from user DRDAUSR3
    execute DBMS_DRDAAS_ADMIN.REVOKE_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.BIND_PRIVILEGE, 'ORACLE', 'NOTYOURPKG', 'DRDAUSR3');

    Rem Revoke ALL on any package in Collection OTHER from user DRDAUSR4
    execute DBMS_DRDAAS_ADMIN.REVOKE_PRIVILEGE(
         DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'OTHER', '*', 'DRDAUSR4');

##### 3.3.2.2 Managing DRDA Package Translation Profile

Example 3-8 Setting and Deleting Translation Profile Name for a DRDA Package

    connect DRDAADM/password

    Rem Set the DB2ZOS profile name for "any" package in collection ORACLE
    DBMS_DRDAAS_ADMIN.SET_PROFILE( 'ORACLE', '*', 'DB2ZOS' );

    Rem Set the MYDB2ZOS profile name for package ORACLE.MYPACKAGE
    DBMS_DRDAAS_ADMIN.SET_PROFILE( 'ORACLE', 'MYPACKAGE', 'MYDB2ZOS' );

    Rem Deleting the profile name for package ORACLE.MYPACKAGE
    execute DBMS_DRDAAS_ADMIN.SET_PROFILE( NULL, 'ORACLE', 'MYPACKAGE' );

    Rem Deleting the profile name for "any" package in collection ORACLE
    execute DBMS_DRDAAS_ADMIN.SET_PROFILE( NULL, 'ORACLE', '*' );

#### 3.3.3 User Role

Each user who accesses the database through DRDA must have the `DRDAAS_USER_ROLE` user role as a default.

Users commonly have the default role `ALL`, which immediately enables all granted roles. If a user has explicit default roles, they must also have the `DRDAAS_USER_ROLE` role, as described in the section Adding DRDAAS_USER_ROLE to Default Values.

Note that failing to specify the complete list of default roles may prevent the user from connecting to the database, or form being able to address certain resources implicitly.

Refer to Oracle® Database SQL Language Reference and Oracle Database Security Guide.

**Related Topics**

- Adding DRDAAS_USER_ROLE

##### 3.3.3.1 Granting the DRDAAS_USER_ROLE

Example 3-9 Granting the DRDAAS_USER_ROLE

    connect sys as sysdba
    grant DRDAAS_USER_ROLE to DRDAUSR;

##### 3.3.3.2 Adding DRDAAS_USER_ROLE

Example 3-10 Adding DRDAAS_USER_ROLE to Default Values

    alter user DRDAUSR default role CONNECT, RESOURCE, DRDAAS_USER_ROLE;

### 3.4 Uninstalling Oracle Database Provider for DRDA

Full uninstall of Oracle Database Provider for DRDA involves the removal of the Database objects and uninstall of Oracle Database Provider for DRDA software. The product-dependent objects are removed, while the customer data remains intact.

#### 3.4.1 Removing the Database Objects

The following steps remove all Oracle Database Provider for DRDA objects from the database, and drop the user-created tablespace.

##### To remove Database objects:

1.  Change directory to `$``ORACLE_HOME``/rdbms/admin`.
        > cd $ORACLE_HOME/rdbms/admin
2.  Connect to the database using the `SYSDBA` option.
        connect / as sysdba
3.  Run the removal script.
        catnodrdaas.sql
4.  Drop the user-created tablespace `sysibm` and its contents.
        > drop tablespace sysibm;

See [Oracle® Database SQL Language Reference](../sqlrf/DROP-TABLESPACE.md) for `DROP TABLESPACE` options.

#### 3.4.2 Uninstalling Oracle Database Provider for DRDA software

To uninstall Oracle Database Provider for DRDA software, you must use the Oracle Universal Installer with the `-deinstall` option. You may choose specify path to Oracle Home using the `-home` option, or choose Oracle Home when Oracle Universal Installer is running.See further instructions on uninstalling Oracle software in [Oracle® Database Installation Guide](../ladbi/index.md).

##### To uninstall Oracle Database Provider for DRDA software:

1.  In Oracle Universal Installer, click Installed Products.
2.  Select the desired `ORACLE_HOME`.
    Either select the whole `ORACLE_HOME`, or open `ORACLE_HOME` navigation tree and select Oracle Database Provider for DRDA product software.
3.   Click Remove.

### 3.5 Configuration Parameters

Oracle Database Provider for DRDA uses several parameters to configure its environment; they are specified in the configuration file.

#### 3.5.1 DATA_PORT

This designates the DRDA data port used by this instance, and is represented by an Internet Address and Port Number.

##### Default Value

There is no default port number; an explicit port number must be specified. Oracle recommends using `1446`.

##### Allowable Values

A valid, unallocated TCP/IP network port number, optionally prefixed with a specific host name or IP address associated with a defined network interface on the local machine.

##### Syntax

`DATA_PORT = {``host_name``|``ip_address``:}``number`

##### Usage Example

    DATA_PORT = 10.0.0.1:1446

#### 3.5.2 RDB_MAP

This `string` parameter maps relational database names, as passed in the DRDA `ACCRDB` command object, to Oracle TNS entries, or to the locally addressable Oracle instance. This parameter may contain several occurrences of a map entry.

This has no default value.

A list of optional values includes the following:

- `tns_name_entry` corresponds to a TNS entry in the local `tnsnames.ora` configuration file.

- `tns_entry` is a fully-formed TNS descriptor string. It may be used instead of a TNS name entry.

- `oracle_sid` uses the `$ORACLE_SID` environment variable value that is set prior to starting an Oracle Database Provider for DRDA instance.

Note that the use of one or more occurrences of `RDB_MAP` determines a mode of compatibility with older application requesters. The default is a single, dedicated definition that connects to a single Oracle Database instance based on the `ORACLE_SID` environmental variable.

##### Allowable Values

A valid, unallocated TCP/IP network port number, optionally prefixed with a specific host name or IP address associated with a defined network interface on the local machine.

##### Syntax

    RDB_MAP = RDB(rdb_name)->TNS(tns_name_entry)
    RDB_MAP = RDB(rdb_name)->ORACLE_SID
    RDB_MAP = RDB(rdb_name)->"tns_entry"

##### Usage Examples

    RDB_MAP = RDB(DB2DSN1)->ORACLE_SID
    RDB_MAP = RDB(DB2DSN2)->TNS(ora101)
    RDB_MAP = RDB(DB2DSN3)->"(ADDRESS=(PROTOCOL=TCP)(HOST=10.0.0.1)(PORT=1446))"

#### 3.5.3 PROTOPROC_TRACE

This parameter designates the trace facility and level of detail for tracing of the DRDA Protocol Processor. All initial Oracle Database Provider for DRDA sessions run with this setting. The parameter consists of a value pair that represents facility and level values. Multiple values may be specified simultaneously if the value tuples are separated by a comma.

It also designates the initial level of trace under which all AS session threads execute. `PROTOPROC_TRACE` is a decimal number or textual designated equivalent.

The facility names used with PROTOPROC_TRACE parameter are as follows:

- `TASK` – Task-specific operations

- `NET` – Network-specific operations

- `SQL` – SQL-specific operations

- `OCI` – OCI resource operations

- `MEM` – Memory resource operations

- `ALL` – All facilities mentioned already

The values of `PROTOPROC_TRACE` level are additive. For example, setting `ERROR(4)` includes `WARN(2)` and `INFO(1)` messages. The following values are expected:

- `0` or `NONE` – No trace is generated; this is the default.

- `1` or `INFO` – Minimal trace is generated.

- `2` or `WARN` – Warning information is generated.

- `4` or `ERROR` – Error information is generated.

- `8` or `ADMIN` – Administration information is generated.

- `255` or `ALL` – All details are generated.

##### Default Value

`0` or none

##### Allowable Values

Facility name followed by level.

##### Usage Example

    PROTOPROC_TRACE="ALL ADMIN"
    PROTOPROC_TRACE="TASK WARN, NET ADMIN, MEM INFO"

#### 3.5.4 PROTOPROC_OPTIONS

The `PROTOPROC_OPTIONS` parameter specifies protoproc processing options, effecting DRDA protocol operations.

##### Default Value

There is no default value for this parameter.

##### Allowable Values

The following values may be specified:

- `QRYDTA/ELMODE`

  Enables Extended Length Mode for all returned Query Data objects. Generally, this is used with queries that do not involve LOBs.

- `EXTDTA/ELMODE`

  Enables Extended Length Mode for all returned Extended Data objects. Typically used with queries involving LOBs.

- `ALLDSS/ELMODE`

  Enables Extended Length Mode for all protocol objects. This is an alternative to either above value, and should not be specified unless other values have no positive effect.

- `LOGNAME/<NAME>`

  Specifies a static DRDA Log Name. The Log Name should alphanumeric and consist of 18 characters. This option may be required when you use DB2 for z/OS as a client.

- `LOGTSTMP/<YYYYMMDDHHMMSSTTTT>`

  Specifies a static DRDA Log Timestamp. The timestamp must have the following format:

  `YYYYMMDDHHMMSSTTTT`

  This value may be required when you use DB2 for z/OS as a client.

##### Syntax

`PROTOPROC_OPTIONS = value {, value ...}`

##### Usage Example

`PROTOPROC_OPTIONS = QRYDTA/ELMODE, EXTDTA/ELMODE, LOGNAME/ORACLEDB, LOGTSTMP/201609191201020001`

**See Also:**

[Extended Length Mode](restrictions-of-oracle-database-provider-for-DRDA.md) section, in Chapter 12 — Restrictions on Using Oracle Database Provider for DRDA
