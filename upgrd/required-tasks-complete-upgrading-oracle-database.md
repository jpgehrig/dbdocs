## Required Tasks to Complete After Upgrading Oracle Database

Review and complete these required tasks that are specified for your environment after you complete your upgrade.

You must complete these postupgrade tasks after you upgrade Oracle Database.

**Note:**

This list of required tasks is based on the assumption that you have used AutoUpgrade to perform the upgrade. AutoUpgrade completes automatically many tasks that otherwise you are required to perform manually.

- Setting Environment Variables on Linux and Unix Systems After Manual Upgrades
  Check that required operating system environment variables point to the directories of the new Oracle Database release.
- Recompile Invalid Objects in the Database
  After you install, patch, or upgrade a database, recompile invalid objects on the CDB and PDBs with a recompilation driver script.
- Track Invalid Object Recompilation Progress
  Use these SQL queries to track the progress of `utlrp.sql` script recompilation of invalid objects.
- Update Listener Files Location on Oracle RAC Cluster Member Upgrades
  If you do not use a shared Oracle Base Home, and you perform an upgrade on an Oracle Database instance that is an Oracle Real Application Clusters member node, then you must update your listener path.
- Running OPatch Commands After Upgrading Oracle Database
  After you upgrade Oracle Database, you must run OPatch commands from the new Oracle home.
- Setting oratab and Scripts to Point to the New Oracle Location After Upgrading Oracle Database
  You must set scripts to point to the new Oracle home location.
- Check PL/SQL Packages and Dependent Procedures
  It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which can affect applications.
- Upgrading Tables Dependent on Oracle-Maintained Types
  Starting with Oracle Database 12c Release 2 (12.2) and later releases, you must manually upgrade user tables that depend on Oracle-Maintained types.
- Enabling the New Extended Data Type Capability
  Enabling a system to take advantage of the new extended data types requires specific upgrade actions.
- Adjusting Minimum and Maximum for Parallel Execution Servers
  Depending on your environment, you can reduce the default setting of the PARALLEL_MIN_SERVERS parameter.
- About Recovery Catalog Upgrade After Upgrading Oracle Database
  If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.
- Upgrading the Time Zone File Version After Upgrading Oracle Database
  If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use any of the supported methods to upgrade the time zone file.
- Upgrading Statistics Tables Created by the DBMS_STATS Package After Upgrading Oracle Database
  If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.
- Configuring the FTP and HTTP Ports and HTTP Authentication for Oracle XML DB
  Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later releases. Upgrades use digest authentication.
- Install Oracle Text Supplied Knowledge Bases After Upgrading Oracle Database
  After an Oracle Database upgrade, all user extensions to the Oracle Text supplied knowledge bases must be regenerated.
- Drop Earlier Release Oracle APEX
  To avoid invalid objects, drop Oracle APEX releases earlier than Application Express (APEX) 19.1.
- Replace the DEMO Directory in Read-Only Oracle Homes
  After upgrading Read-Only Oracle homes, make a copy of the earlier release Oracle Database `demo` directory, and replace the `demo` directory in the Read-Only Oracle home with the new release `demo` directory.
- Configure Access Control Lists (ACLs) to External Network Services
  Oracle Database 12c and later releases include fine-grained access control to the `UTL_TCP`, `UTL_SMTP`, `UTL_MAIL`, `UTL_HTTP`, or `UTL_INADDR` packages.
- Enabling Oracle Database Vault After Upgrading Oracle Database
  Depending on your target database release, you can be required to disable Oracle Database Vault to complete an Oracle Database upgrade.
- Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior
  Connections to Oracle Database from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)

### Setting Environment Variables on Linux and Unix Systems After Manual Upgrades

Check that required operating system environment variables point to the directories of the new Oracle Database release.

Typically, operating system environment variables are set in profiles and shell scripts. Confirm that the following Oracle user environment variables point to the directories of the new Oracle home:

- `ORACLE_HOME`

- `PATH`

Look for other environment variables that refer to the earlier release Oracle home, such as `LD_LIBRARY_PATH`. In general, you should replace all occurrences of the old Oracle home in your environment variables with the new Oracle home paths.

**Related Topics**

- [Step 2: Ensure That the Required Environment Variables Are Set](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Recompile Invalid Objects in the Database

After you install, patch, or upgrade a database, recompile invalid objects on the CDB and PDBs with a recompilation driver script.

By default, AutoUpgrade performs a recompilation of invalid Oracle objects, which is controlled by the configuraiton file run_utlrp local parameter (default: `prefix``.run_utlrp=yes`). In addition, Oracle provides the recompilation scripts `utlrp.sql` and `utlprp.sql`. These scripts are located in the `Oracle_home``/rdbms/admin` directory.

**Note:**

Starting with AutoUpgrade 23.1, when you run the AutoUpgrade utility, AutoUpgrade runs the `utlprpom.sql` script, and does not run `utlrp.sql`. When AutoUpgrade is used for upgrades to Oracle Database 12c Release 2 (12.2.0.1) and later releases, AutoUpgrade only recompiles invalid objects owned by Oracle-maintained schemas. Because database upgrades do not need to touch user objects, AutoUpgrade maintains this policy when it recompiles invalid objects.

After installing a database, recomplile all invalid objects;

1.  Change directory to `Oracle_home``/rdbms/admin`. For example

        $ cd $ORACLE_HOME/rdbms/admin

2.  Use the `catcon.pl` script in the Oracle home to run `utlrp.sql`. For example:

        $ORACLE_HOME/perl/bin/perl catcon.pl --n 1 --e --b utlrp --d '''.''' utlrp.sql

    Note the following conditions of this use case:

    - `--n` parameter: is set to 1, so the script runs each PDB recompilation in sequence.

    - `--e` parameter: turns echo on.

    - `--b` parameter: Sets the log file base name. It is set to `utlrp`.

    Expect a time delay for the serial recompilation of PDBs to complete. Depending on the number of PDBs that you are upgrading, the recompilation can extend significantly beyond the time required for the upgrade scripts to complete.

    The `utlrp.sql` script automatically recompiles invalid objects in either serial or parallel recompilation, based on both the number of invalid objects, and on the number of CPUs available. CPUs are calculated using the number of CPUs (cpu_count) multiplied by the number of threads for each CPU (parallel_threads_per_cpu). On Oracle Real Application Clusters (Oracle RAC), this number is added across all Oracle RAC nodes.

After patching or upgrading a database, there is more than one approach you can use to recompile invalid Oracle-owned and user-owned objects:

Recompile all invalid objects (the invalid objects in both Oracle and user schemas) by using `utlrp.sql` or `utlprp.sql`.

If time is a factor and the type of invalid objects is predominately application owned, then you can recompile Oracle-owned invalid objects first, and defer recompiling application-owned invalid objects to a later time. To recompile invalid objects in Oracle schemas, use `utlprpom.sql`. To recompile the remaining invalid objects, use `utlrp.sql` or `utlprp.sql`.

**Note:**

When you use either `utlprp.sql` or `utlprpom.sql`, note that both scripts require you to define the degree of parallelism that the script should use, or determine the number of parallel recompile jobs to use.

The script uses syntax as follows, where `base` is the base name you want to have given to log files, `N` is the number of PDBs on which you want to run recompilation jobs in parallel (degrees of parallelism), `script.sql` is the Oracle recompilation script you chose to use, and `P` is the number of PDBs on which you want to run in parallel:

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -b base -d $ORACLE_HOME/rdbms/admin
              -n N -l /tmp script.sql '--pP'

Suppose you are running recompilation in a CDB using the log file base name `recomp`, with a degrees of parallelism setting of 3 jobs per PDB container, the script you choose to use is `utlprp.sql`, and you want to recompile across at most 10 PDBs at a time. In that case, the syntax you use to run the recompile operation is similar to the following,

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -b recomp -d $ORACLE_HOME/rdbms/admin -n 10 -l /tmp utlprp.sql '--p3'

**Related Topics**

- [Syntax and Parameters for catcon.pl](../multi/administering-a-cdb-with-sql-plus.md)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Track Invalid Object Recompilation Progress

Use these SQL queries to track the progress of `utlrp.sql` script recompilation of invalid objects.

**Note:**

If you upgraded using the AutoUpgrade utility, then AutoUpgrade automatically takes care of this task during the upgrade. You do not need to perform this task.

Oracle recommends that you run the `utlrp.sql` script after upgrade to recompile invalid objects. You can run SQL queries to monitor the script.

Example 6-4 Number of Invalid Objects Remaining

Enter this query to return the number of remaining invalid objects. This number decreases over time as the `utlrp.sql` script runs.

    select COUNT(*) "OBJECTS WITH ERRORS" from obj$ where status in (3,4,5,6);

Example 6-5 Number of Objects Recompiled

Enter this query to return the number of objects that `utlrp.sql` has compiled. This number increases over time as the script runs.

    SELECT COUNT(*) FROM UTL_RECOMP_COMPILED;

Example 6-6 Number of Objects Recompiled with Errors

Enter this query to return the number of objects that `utlrp.sql` has compiled with errors.

    select COUNT(DISTINCT(obj#)) "OBJECTS WITH ERRORS" from utl_recomp_errors;

If the number is higher than expected, then examine the error messages reported with each object. If you see errors due to system misconfiguration or resource constraints, then fix the cause of these errors, and run `utlrp.sql` again.

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Update Listener Files Location on Oracle RAC Cluster Member Upgrades

If you do not use a shared Oracle Base Home, and you perform an upgrade on an Oracle Database instance that is an Oracle Real Application Clusters member node, then you must update your listener path.

If you do not use a shared Oracle Base Home, and you perform an upgrade on an Oracle Database instance that is an Oracle Real Application Clusters cluster member node, but you do not use Database Configuration Assistant (DBCA), then you must manually update all of the remote `tnsnames.ora` files. If the files are not updated, then the following error occurs:

    TNS-03505: Failed to resolve name

In Oracle Database releases after Oracle Database 19c, the default network administration directory changes from the previous default in the local Oracle home, `Oracle_home``/network` (for example, `/u01/app/oracle/product/19.1.0/dbhome_1/network`), to a new location. The new default location is the shared Oracle Base Home, in the path `ORACLE_BASE``/homes/``HOME_NAME``/network/admin`. For example: `/u01/app/oracle/homes/23.0.0Home1/network/admin` is the Oracle home of a specific Oracle Real Application Clusters (Oracle RAC) instance, which is located in the default path for read-only Oracle homes. That file path is the default location of the local `tnsnames.ora` and `sqlnet.ora` files.

During the upgrade, Net Configuration Assistant (NetCA, or `netca`) updates the location of the network listener files, `tnsnames.ora` and `sqlnet.ora` on the local host. However, NetCA does not update the location of those network listener files for the instance on all cluster member nodes. To ensure that all cluster member nodes can resolve service requests to the upgraded cluster member node instance, you must do one of the following:

- On each cluster member node, Manually copy the `tnsnames.ora` and `sqlnet.ora` files from the existing location to `ORACLE_BASE``/homes/``HOME_NAME``/network/admin/`.
- Set an environment variable on the upgraded cluster member node to point to the existing network administration files location.

Example 6-7 Copy TNSNAMES.ORA and SQLNET.ORA to New Default Network Administration Directory

In this example, you copy the existing `tnsnames.ora` and `sqlnet.ora` files to the new default network location on each cluster member node

1.  Log in as the Oracle installation owner, and change directory to the earlier release network administration directory. For example:

        cd $ORACLE_HOME/network

2.  Use secure copy (`scp`) to copy the listener files to the default network directory location on another cluster member node. For example, where `racnode2` is a cluster member node to which you want to copy the listener files:

        cd $OLD_ORACLE_HOME/network
        scp tnsnames.ora sqlnet.ora \
        oracle@racnode2:/u01/app/oracle/homes/23.0.0Home1/network/admin/

Example 6-8 Set the TNS_ADMIN Environment Variable

On the upgraded node, log in as the Oracle user, and then set an environment variable for TNS_ADMIN to point to the location of your existing listener files. For example:

    /home/oracle oracle> $ export TNS_ADMIN=$ORACLE_HOME/network/admin

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Running OPatch Commands After Upgrading Oracle Database

After you upgrade Oracle Database, you must run OPatch commands from the new Oracle home.

OPatch is a Java-based utility that you install with Oracle Universal Installer. Opatch is platform-independent. It runs on all supported operating systems. Another version of OPatch, called standalone OPatch, is also available. It runs on Oracle homes without Oracle Universal Installer.

Patches are a small collection of files copied over to an existing installation. They are associated with particular versions of Oracle products. When applied to the correct version of an installed product, patches result in an upgraded version of the product.

#### Run Opatch to Check the Oracle Database Inventory

Log in as the Oracle installation owner, and run the `lsinventory` command from the new Oracle home. The command generates an accurate and complete inventory of the Oracle software installed on the system:

    opatch lsinventory –patch

Refer to My Oracle Support note 756671.1 regularly to obtain current recommendations regarding Release Updates (Updates) and Release Update Revisions (Revisions).

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=756671.1>

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Setting oratab and Scripts to Point to the New Oracle Location After Upgrading Oracle Database

You must set scripts to point to the new Oracle home location.

After you upgrade Oracle Database to a new release, if you do not use AutoUpgrade for your database upgrade, then you must ensure that your `oratab` file and any client scripts that set the value of `ORACLE_HOME` point to the new Oracle home that is created for the new Oracle Database release. If you perform your upgrade using either AutoUpgrade or DBUA, then these utilities automatically point `oratab` to the new Oracle home. However, regardless of the method you use to upgrade, you must check client scripts.

If you upgrade your database manually, then you must log in as the Oracle installation owner for the new Oracle Database release, and update the `oratab` file manually. The location of the `oratab` file can vary, depending on your operating system.

**Related Topics**

- [Step 2: Set Operating System Environment Variables](../admin/getting-started-with-database-administration.md)
- [My Oracle Support Note 394251.1](https://support.oracle.com/rs?type=doc&id=394251.1)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Check PL/SQL Packages and Dependent Procedures

It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which can affect applications.

After the upgrade, if you use AutoUpgrade, review the AutoUpgrade report on invalid objects. If you use a replay upgrade, then check to ensure that any packages that you may have used in your own scripts, or that you call from your scripts, are available in the new release. Testing procedures dependent on packages should be part of your upgrade plan.

Code in database applications can reference objects in the connected database. For example, Oracle Call Interface (OCI) and precompiler applications can submit anonymous PL/SQL blocks. Triggers in Oracle Forms applications can reference a schema object. Such applications are dependent on the schema objects they reference. Dependency management techniques vary, depending on the development environment. Oracle Database does not automatically track application dependencies.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-schema-objects.md)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Upgrading Tables Dependent on Oracle-Maintained Types

Starting with Oracle Database 12c Release 2 (12.2) and later releases, you must manually upgrade user tables that depend on Oracle-Maintained types.

**Note:**

If you upgraded using the AutoUpgrade utility, then AutoUpgrade automatically takes care of this task during the upgrade. You do not need to perform this task.

If your database has user tables that are dependent on Oracle-Maintained types (for example, `AQ` queue tables), then run the `utluptabdata.sql` command after the upgrade to carry out `ALTER TABLE UPGRADE` on any user tables affected by changes in Oracle-Maintained types. This change in behavior enables user tables to remain in `READ ONLY` state during an upgrade. Users are prevented from logging into applications using SYSDBA privileges (`AS SYSDBA`), and changing application tables that are dependent on Oracle-Maintained types.

To identify tables that you need to upgrade after the database upgrade completes, connect to the database `AS SYSDBA`, and run the following query:

    COLUMN owner FORMAT A30
    COLUMN table_name FORMAT A30
    SELECT DISTINCT owner, table_name
    FROM dba_tab_cols
    WHERE data_upgraded = 'NO'
    ORDER BY 1,2;

This query lists all tables that are not listed as `UPGRADED`. However, the `utluptabdata.sql` script only upgrades tables that depend on Oracle-Maintained types. If any tables are listed by the query, then run the `utluptabdata.sql` script to perform `ALTER TABLE UPGRADE` commands on dependent user tables, so that these Oracle-Maintained types are upgraded to the latest version of the type.

You must run the `utluptabdata.sql` script either with a user account with `ALTER` privileges for all of the tables dependent on Oracle-Maintained types, or with a user granted the SYSDBA system privileges, and that is logged in `AS SYSDBA`.

When the parameter SERVEROUTPUT is set to `ON`, the `utluptabdata.sql` script displays the names of all upgraded tables, and lists any error encountered during the table upgrade. To set the server output to `ON`, run the following command:

    SET SERVEROUTPUT ON
    @utluptabdata.sql

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Enabling the New Extended Data Type Capability

Enabling a system to take advantage of the new extended data types requires specific upgrade actions.

Oracle Database 12c introduced `MAX_STRING_SIZE` to control the maximum size of `VARCHAR2`, `NVARCHAR2`, and `RAW` data types in SQL. Setting `MAX_STRING_SIZE = EXTENDED` enables the 32767 byte limit introduced in Oracle Database 12c.

To be able to set `MAX_STRING_SIZE = EXTENDED`, you must set the `COMPATIBLE` initialization parameter to `12.0.0.0` or higher

In addition, you must run the script `utl32k.sql` script while the database is open in upgrade mode so that you invalidate and recompile objects that are affected by the change in data type sizes. For example:

    CONNNECT SYS / AS SYSDBA
    SHUTDOWN IMMEDIATE;
    STARTUP UPGRADE;
    ALTER SYSTEM SET max_string_size=extended;
    START $ORACLE_HOME/rdbms/admin/utl32k.sql
    SHUTDOWN IMMEDIATE;
    STARTUP;

**Caution:**

You can change the value of `MAX_STRING_SIZE` from `STANDARD` to `EXTENDED`. However, you cannot change the value of `MAX_STRING_SIZE` from `EXTENDED` to `STANDARD`. By setting `MAX_STRING_SIZE = EXTENDED`, you are taking an explicit action that can introduce application incompatibility in your database.

**See Also:**

[Oracle Database Reference](../refrn/MAX_STRING_SIZE.md) for complete information about `MAX_STRING_SIZE`, including recommendations and procedures

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Adjusting Minimum and Maximum for Parallel Execution Servers

Depending on your environment, you can reduce the default setting of the PARALLEL_MIN_SERVERS parameter.

In Oracle Database 12c, the default for PARALLEL_MIN_SERVERS changed from `0` to a value that was provided based on your hardware platform. This change was made to provide sufficient minimal support for parallel execution. If you find that the new default setting is too high, then adjust the setting for your requirements. The default for `PARALLEL_MAX_SERVERS` has not changed. If the default in your old environment is unchanged, then you do not need to take further action.

**See Also:**

[Oracle Database Reference](../refrn/PARALLEL_MIN_SERVERS.md) for information about `PARALLEL_MIN_SERVERS`

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### About Recovery Catalog Upgrade After Upgrading Oracle Database

If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.

**Note:**

You can configure AutoUpgrade to perform this task for you. To use AutoUpgrade for this task, specify the configuration file parameter `rman_catalog_connect_string`, and specify the connect string to the catalog database hosting the RMAN catalog schema. When you run AutoUpgrade, specify the RMAN username and password using the AutoUpgrade command-line parameter `load_password` with the option `group rman`. As AutoUpgrade runs, it will prompt you to provide the RMAN username and password, which AutoUpgrade then loads into its keystore, so that AutoUpgrade can connect to the RMAN catalog schema and upgrade the recovery catalog schema.

**See Also:**

- [Maintaining RMAN Backups and Repository Records](../bradv/maintaining-rman-backups.md)
- [Upgrading the Recovery Catalog](../bradv/managing-recovery-catalog.md)
- [My Oracle Support RMAN Compatibility Matrix (Doc ID 73431.1)](https://support.oracle.com/rs?type=doc&id=73431.1)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Upgrading the Time Zone File Version After Upgrading Oracle Database

If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use any of the supported methods to upgrade the time zone file.

By default, AutoUpgrade changes the database time zone to the latest available level. If you don’t want the time zone to be upgraded, then you must explicitly set the local parameter `timezone_upg` in your AutoUpgrade configuration file to `no`. For example:

`upg1.timezone_upg=no`

**Note:**

If you explicitly disable the time zone file upgrade in your AutoUpgrade configuration file, then Oracle recommends that you perform this task either as part of your upgrade plan, or at a later point in time.

**Related Topics**

- [Datetime and Time Zone Parameters and Environment Variables](../nlspg/datetime-data-types-and-time-zone-support.md)
- [Primary Note DST FAQ : Updated DST Transitions and New Time Zones in Oracle RDBMS and OJVM Time Zone File Patches (Doc ID 412160.1)](https://support.oracle.com/rs?type=doc&id=412160.1)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Upgrading Statistics Tables Created by the DBMS_STATS Package After Upgrading Oracle Database

If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.

In the following example, `green` is the owner of the statistics table and `STAT_TABLE` is the name of the statistics table.

    EXECUTE DBMS_STATS.UPGRADE_STAT_TABLE('green', 'stat_table');

Perform this procedure for each statistics table.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for information about the DBMS_STATS package

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Configuring the FTP and HTTP Ports and HTTP Authentication for Oracle XML DB

Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later releases. Upgrades use digest authentication.

Oracle recommends that when you configure ports, you also configure the authentication for HTTP for accessing Oracle XML DB Repository to take advantage of improved security features.

Starting with Oracle Database 12c, Oracle enhanced database security by supporting digest authentication. Digest authentication is an industry-standard protocol that is commonly used with the HTTP protocol. It is supported by most HTTP clients. Digest authentication ensures that passwords are always transmitted in a secure manner, even when an encrypted (HTTPS) connection is not in use. Support for digest authentication enables organizations to deploy applications that use Oracle XML DB HTTP, without having to worry about passwords being compromised. Digest authentication support in Oracle XML DB also ensures that the Oracle XML DB HTTP server remains compatible with Microsoft Web Folders WebDAV clients.

After installing or upgrading for the new release, you must manually configure the FTP and HTTP ports for Oracle XML DB as follows:

1.  Use `DBMS_XDB_CONFIG.setHTTPPort(``HTTP_port_number``)` to set the HTTP port for Oracle XML DB:

        SQL> exec DBMS_XDB_CONFIG.setHTTPPort(port_number);

2.  Use `DBMS_XDB_CONFIG.setFTPPort(``FTP_port_number``)` to set the FTP port for Oracle XML DB:

        SQL> exec DBMS_XDB_CONFIG.setFTPPort(FTP_port_number);

    **Note:**

    You can query the port numbers to use for FTP and HTTP in the procedure by using `DBMS_XDB_CONFIG.getFTPPort` and `DBMS_XDB_CONFIG.getHTTPPort` respectively.

3.  To see all the used port numbers, query `DBMS_XDB_CONFIG.usedport`.

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Install Oracle Text Supplied Knowledge Bases After Upgrading Oracle Database

After an Oracle Database upgrade, all user extensions to the Oracle Text supplied knowledge bases must be regenerated.

Regenerating the user extensions affect all databases installed in the given Oracle home.

After an upgrade, the Oracle Text-supplied knowledge bases that are part of the companion products for the new Oracle Database are not immediately available. Any Oracle Text features dependent on the supplied knowledge bases that were available before the upgrade do not function after the upgrade. To re-enable such features, you must install the Oracle Text supplied knowledge bases from the installation media for the new Oracle Database release.

**See Also:**

- [Oracle Text Application Developer's Guide](../ccapp/working-with-thesaurus-in-oracle-text.md) for information about Oracle Text-supplied knowledge bases

- [Oracle Database Installation Guide](../install-and-upgrade.md) for companion products

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Drop Earlier Release Oracle APEX

To avoid invalid objects, drop Oracle APEX releases earlier than Application Express (APEX) 19.1.

The package `DBMS_OBFUSCATION_TOOLKIT` was deprecated in Oracle Database 11g Release 2 (11.2). Starting in Oracle Database 21c, `DBMS_OBFUSCATION_TOOLKIT` is desupported, and replaced with `DBMS_CRYPT`. In releases earlier than Oracle Database 21c, Oracle APEX continued to have a dependency on `DBMS_OBFUSCATION_TOOLKIT`. In Oracle Database 21c, which includes APEX release 19.2, this dependency is removed.

During Oracle Database upgrade, APEX is not automatically upgraded to the release shipped with the Oracle Database release. Before upgrade, when you run AutoUpgrade using the `preupgrade` parameter, the output `upgrade.xml` file reports that you must upgrade APEX releases earlier than APEX 19.1.0.00.15, because of the earlier release dependency on `DBMS_OBFUSCATION_TOOLKIT`.

To avoid `INVALID` objects, either before or after you upgrade Oracle Database, you must upgrade APEX to at least the version that ships with Oracle Database 21c, and then drop earlier releases of APEX.

1.  Log in to the new Oracle Database Oracle home

2.  Upgrade Oracle APEX, using at least Oracle Application Express 19.2, which is shipped in the Oracle home (APEX 19.2), or a later version, when it is available

3.  Drop earlier release APEX users.

    For example:

        drop user APEX_050000 cascade;
        drop user APEX_040200 cascade;
        drop user APEX_030100 cascade;

4.  Drop earlier release APEX SYS owned objects.

    For example:

        drop package SYS.WWV_DBMS_SQL;

**Note:**

Starting with Oracle APEX 18c (18.1), the `SYS.WWV_DBMS_SQL` object is appended with the Oracle APEX release schema.

For example:

    SYS.WWV_DBMS_SQL_APEX_180100

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Replace the DEMO Directory in Read-Only Oracle Homes

After upgrading Read-Only Oracle homes, make a copy of the earlier release Oracle Database `demo` directory, and replace the `demo` directory in the Read-Only Oracle home with the new release `demo` directory.

Oracle Database 18c and later releases contain a product demonstration directory in the file path `Oracle_home``/rdbms/demo`. These directories include examples and product demonstrations that are specific to the options and features for each Oracle Database release, some of which you can add to after upgrade by installing Oracle Database Examples. In your earlier release, if you downloaded and worked with the earlier release demonstration files, then you have two problems: you want to save your earlier release work for review and testing with the new release, and you want to obtain refreshes of the demonstrations that are specific to the new release.

After upgrading the Oracle home, and downloading and doing any other work you want to do with the new demonstration files, you can then refresh your old demonstration files.

Example 6-9 Copying the Earlier Release Demo Directory and Refreshing the Demonstrations in the Read-Only Oracle Home

After the upgrade, use this procedure to save any work in your earlier `demo` directory in the Read-Only Oracle home, and and replace the earlier release `demo` directory with the new release `demo` directory:

1.  Log in as the Oracle software owner user (`oracle`).

2.  Check if the `rdbms/demo` directory is copied to the Read Only Oracle home.

    In this example, the environment variable `ORACLE_BASE_HOME` is defined as the path to the Read-Only Oracle home.

    Linux and Unix platforms:

        $ ls -l -d $ORACLE_BASE_HOME/rdbms/demo
        /u01/app/oracle/product/19.0.0/dbhome_1/rdbms/demo

    Microsoft Windows platforms

        ls -l -d %ORACLE_BASE_HOME%\rdbms\demo
        %ORACLE_BASE_HOME%\rdbms\demo

3.  Change directory to the Read-Only Oracle home, and make a copy, where `demo.old_release18` is the name you give to your earlier release demonstration files:

        cd $ORACLE_BASE_HOME/rdbms
        mv demo demo.old_release18

4.  Copy the new `demo` directory from the upgraded Oracle home to the Read-Only Oracle home.

    In this example, the environment variable ORACLE_HOME is defined as the new release Oracle home.

    Linux and Unix:

        cp -r $ORACLE_HOME/rdbms/demo demo

    Microsoft Windows

        xcopy c:\%ORACLE_HOME%\rdbms\demo c:%ORACLE_BASE_HOME%\rdbms\demo /E

<!-- -->

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Configure Access Control Lists (ACLs) to External Network Services

Oracle Database 12c and later releases include fine-grained access control to the `UTL_TCP`, `UTL_SMTP`, `UTL_MAIL`, `UTL_HTTP`, or `UTL_INADDR` packages.

If you have applications that use these packages, then after upgrading Oracle Database you must configure network access control lists (ACLs) in the database before the affected packages can work as they did in earlier releases. Without the ACLs, your applications can fail with the error "ORA-24247: network access denied by access control list (ACL)."

**See Also:**

[Oracle Database Security Guide](../dbseg/managing-fine-grained-access-in-pl-sql-packages-and-types.md) for more complicated situations, such as connecting some users to host A and other users to host B

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Enabling Oracle Database Vault After Upgrading Oracle Database

Depending on your target database release, you can be required to disable Oracle Database Vault to complete an Oracle Database upgrade.

- Upgrading Oracle Database Without Disabling Oracle Database Vault
  To upgrade to Oracle Database 12c Release 2 (12.2.0.1) or later releases, either grant the `DV_PATCH_ADMIN` role to `SYS` commonly in the root container, and revoke after the upgrade, or disable Oracle Database Vault and reenable it after upgrade.
- Common Upgrade Scenarios with Oracle Database Vault
  The requirements to enable Oracle Database Vault after upgrades change, depending on your source Oracle Database release.

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

#### Upgrading Oracle Database Without Disabling Oracle Database Vault

To upgrade to Oracle Database 12c Release 2 (12.2.0.1) or later releases, either grant the `DV_PATCH_ADMIN` role to `SYS` commonly in the root container, and revoke after the upgrade, or disable Oracle Database Vault and reenable it after upgrade.

If Oracle Database Vault is enabled and you are upgrading an entire CDB, then use one of the following methods:

- CDB upgrade method 1: Temporarily grant the `DV_PATCH_ADMIN` to user `SYS` commonly by logging into the root container as a common user with the `DV_OWNER` role, and then issuing the `GRANT DV_PATCH_ADMIN TO SYS CONTAINER=ALL` statement. Oracle Database Vault controls will be in the same state as it was before the upgrade. When the upgrade is complete, log into the root container as the `DV_OWNER` user, and revoke the `DV_PATCH_ADMIN` role from `SYS` by issuing the `REVOKE DV_PATCH_ADMIN FROM SYS CONTAINER=ALL` statement.
- CDB upgrade method 2: Log into each container as a user who has the `DV_OWNER` role, and then run the `DBMS_MACADM.DISABLE_DV` procedure. You must first disable Oracle Database Vault on the PDBs, and then after that, disable Oracle Database Vault on the root container last. If you are upgrading only one PDB, then you can disable Oracle Database Vault in that PDB only. After you have completed the upgrade, you can enable Oracle Database Vault by logging into each container as the `DV_OWNER` user and then executing the `DVSYS.DBMS_MACADM.ENABLE_DV` procedure. The order of enabling Oracle Database Vault must be the root container first and PDBs afterward. You can enable the PDBs in any order, but the root container must be enabled first.

If you manually disable Oracle Database Vault before the upgrade, then you must enable Oracle Database Vault manually after the upgrade.

If you did not have Oracle Database Vault enabled before the upgrade, then you can enable it manually after the upgrade.

**Note:**

This procedure applies to non-CDB upgrades as well

**Related Topics**

- [Oracle Database - Overview of Database Patch Delivery Methods for 12.2.0.1 and greater (Doc ID 2337415.1)](https://support.oracle.com/rs?type=doc&id=2337415.1)
- [Disabling and Enabling Oracle Database Vault Oracle Database Vault Administrator’s Guide](../dvadm/disabling-and-enabling-oracle-database-vault.md)

**Parent topic:** Enabling Oracle Database Vault After Upgrading Oracle Database

#### Common Upgrade Scenarios with Oracle Database Vault

The requirements to enable Oracle Database Vault after upgrades change, depending on your source Oracle Database release.

- Upgrades from Oracle Database 11g release 2 (11.2) or earlier: After the upgrade, Oracle Database Vault is disabled by default.

- Upgrades from Oracle Database 12c release 1 (12.1) or later: After the upgrade, Oracle Database Vault has the same enforcement status that you had in place before the upgrade.

Table 6-1 Common Oracle Database Vault Upgrade Scenarios and Upgrade Preparation Tasks

| Source Database Release     | Target Database Release | Do you need to disable Database Vault Before Upgrade | What is Database Vault Status After Upgrade                                              |
|:----------------------------|:------------------------|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------|
| 11.2 or earlier             | 12.1                    | Yes                                                  | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 11.2.or earlier             | 12.2, 18.1 and later    | No                                                   | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 12.1, 12.2, 18.1, and later | 12.2, 18.1 and later    | No                                                   | Database Vault has the same enforcement status that you had in place before the upgrade. |

**Parent topic:** Enabling Oracle Database Vault After Upgrading Oracle Database

### Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior

Connections to Oracle Database from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`.

Starting with Oracle Database 18c, the default value for the `SQLNET.ALLOWED_LOGON_VERSION` parameter changed from 11 in Oracle Database 12c (12.2) to 12 in Oracle Database 18c and later releases. The use of this parameter is deprecated.

`SQLNET.ALLOWED_LOGON_VERSION` is now replaced with the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` and `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` parameters. If you have not explicitly set the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter in the upgraded database, then connections from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`. For better security, check the password verifiers of your database users, and then configure the database to use the correct password verifier by setting the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` and `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` parameters.

If you have password-protected roles (secure roles) in your existing database, and if you upgrade to Oracle Database 18c and later releases with the default `SQLNET.ALLOWED_LOGON_VERSION_SERVER` setting of 12, because those secure roles only have release 10g verifiers, then the password for each secure role must be reset by the administrator so that the secure roles can remain usable after the upgrade.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for information about ensuring against password security threats

- [Oracle Database Security GuideOracle Database Security Guide](../dbseg/configuring-authentication.md) for information about setting the password versions of users

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database
