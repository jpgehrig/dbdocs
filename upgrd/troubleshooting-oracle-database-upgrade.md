## 5 Troubleshooting the Upgrade for Oracle Database

Use these troubleshooting tips to address errors or issues that you may encounter while upgrading your database.

Also review the related links to learn about changes that affect this release, which may be related to errors you receive, and to see how to rerun the upgrade after you resolve errors.

- About Starting Oracle Database in Upgrade Mode
  When you start Oracle Database in upgrade mode, you can only run queries on fixed views. If you attempt to run other views or PL/SQL, then you receive errors.
- Running DBUA with Different ORACLE_HOME Owner
  Review this topic if your Oracle Database homes are owned by different operating system user accounts, or you encounter an `upgrade.xml not found` error.
- Invalid Object Warnings and DBA Registry Errors
  Before you start your upgrade, Oracle strongly recommends that you run the preupgrade information tool (`preupgrd.jar`).
- Invalid Objects and Premature Use of Postupgrade Tool
  Never run the postupgrade status tool for the new Oracle Database release (`utlusts.sql`) until after you complete the upgrade.
- Resolving Oracle Database Upgrade Script Termination Errors
  Review this section if you encounter ORA-00942, ORA-00904, or ORA-01722 errors.
- Troubleshooting Causes of Resource Limits Errors while Upgrading Oracle Database
  Review this section if you encounter `ORA-01650`, `ORA-01651`, `ORA-01652`, `ORA-01653`, `ORA-01654`, `ORA-01655`, `ORA-0431`, `ORA-01562`, `ORA-19815`, or other errors that suggest resource limit errors.
- Resolving SQL\*Plus Edition Session Startup Error for Oracle Database
  Use this section to understand and resolve SP2–1540: "Oracle Database cannot startup in an Edition session."
- Error ORA-00020 Maximum Number of Processes Exceeded When Running utlrp.sql
  This error may indicate that your Oracle configuration does not have sufficient number of processes available for the recompile.
- Fixing ORA-28365: Wallet Is Not Open Error
  If you use Oracle wallet with Transparent Data Encryption (TDE), and you use Database Upgrade Assistant (DBUA) to upgrade the database, then you can encounter an ORA-28365 "wallet is not open" error.
- Resolving issues with view CDB_JAVA_POLICY
  If the view CDB_JAVA_POLICY becomes invalid, then use this procedure.
- Continuing Upgrades After Server Restarts (ADVM/ACFS Driver Error)
  On Windows platforms, an error may occur related to ADVM or ACFS drivers if a server restarts during an upgrade.
- Component Status and Upgrades
  Component status settings are affected both by the components that you previously installed, and by the support of those components for upgrades.
- Standard Edition Starter Database and Components with Status OPTION OFF
  Starting in Oracle Database 18c (18.1), all `OPTION OFF` components are upgraded to the new release, but these options are disabled for Oracle Database Standard Edition (SE) remain OPTION OFF.
- Adjusting Oracle ASM Password File Location After Upgrade
  You must create a new password file for Oracle ASM after an Oracle Grid Infrastructure upgrade.
- Fixing "Warning XDB Now Invalid" Errors with Pluggable Database Upgrades
  Review this topic if you encounter "Warning: XDB now invalid, invalid objects found” errors when upgrading pluggable databases (PDBs).
- Fixing ORA-27248: sys.dra_reevaluate_open_failures is running
  Use this procedure to identify `DRA_REEVALUATE_OPEN_FAILURES` jobs that block upgrades.
- Fixing Failed Upgrades Where Only Datapatch Fails
  If only datapatch fails during an upgrade, then rerun datapatch directly.

**Related Topics**

- [Rerunning Upgrades for Oracle Database](rerunning-upgrades-oracle-database.md)

### About Starting Oracle Database in Upgrade Mode

When you start Oracle Database in upgrade mode, you can only run queries on fixed views. If you attempt to run other views or PL/SQL, then you receive errors.

When the database is started in upgrade mode, only queries on fixed views execute without errors. This restriction applies until you either run the Parallel Upgrade Utility (`catctl.pl`) directly, or indirectly by using the `dbupgrade` script). Before running an upgrade script, using PL/SQL on any other view, or running queries on any other view returns an error. If you receive any of the errors described in this section, then issue the `SHUTDOWN ABORT` command to shut down the database, and then correct the problem.

The following list of errors can occur when you attempt to start the new Oracle Database release. Some of these errors write to the alert log, and not to your session.

- `ORA-00401: the value for parameter compatible is not supported by this release`

  The `COMPATIBLE` initialization parameter is set to a value less than `11.2.0`.

- `ORA-39701: database must be mounted EXCLUSIVE for UPGRADE or DOWNGRADE`

  The `CLUSTER_DATABASE` initialization parameter is set to `TRUE` instead of `FALSE`.

- `ORA-39700: database must be opened with UPGRADE option`

  The `STARTUP` command was issued without the `UPGRADE` keyword.

- `Ora-00704: bootstrap failure`

  The path variable can be pointing to the earlier release Oracle home.

- `ORA-00336: log file size xxxx blocks is less than minimum 8192 blocks`

  A redo log file size is less than 4 MB.

If errors appear listing desupported initialization parameters, then make a note of the desupported initialization parameters, and continue with the upgrade. Remove the desupported initialization parameters the next time you shut down the database.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=1349722.1>

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Running DBUA with Different ORACLE_HOME Owner

Review this topic if your Oracle Database homes are owned by different operating system user accounts, or you encounter an `upgrade.xml not found` error.

DBUA upgrades by default assume that both the source Oracle home and the target Oracle home are owned by the same user. If each Oracle home is not owned by the same user, then you must change to database file permissions and pass additional parameters to DBUA. If you do not do this, then during upgrade, the DBUA Prerequisite Checks page reports `upgrade.xml not found` errors. You are not permitted to proceed with the upgrade until this error is corrected.

- All Oracle Database installation owners should have the group that you designate as the `OINSTALL` group (or Oracle Inventory group) as their primary group. Ensure all database files (data files, the redo file, control files, archive log destination, recovery area, SPFILE, and password file) are readable and writable by both the new target release and the source (earlier) release binary owners. If this is not the case, then confirm that each installation owner has the same group as their primary group, and ensure that members of the `OINSTALL` group have read/write access to all of the earlier release and later release Oracle Database files and directories.

- Run DBUA by specifying the `-logdir` command line option, and provide a directory to which both the new release and earlier release binary owners can write. For example: `/tmp`. DBUA uses the directory you designate with the `logdir ` parameter to store the output from the Pre-upgrade Information Tool, and to store any DBUA log files generated during the upgrade. You run the Pre-Upgrade Information tool from the earlier release Oracle Database instance as the earlier release Oracle Database installation owner user account.

  For example:

      dbua -logdir /tmp

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Invalid Object Warnings and DBA Registry Errors

Before you start your upgrade, Oracle strongly recommends that you run the preupgrade information tool (`preupgrd.jar`).

The preupgrade information tool identifies invalid SYS and SYSTEM objects, as well as other invalid objects. Use `utlrp.sql` to recompile invalid objects. If you fail to do this before an upgrade, then it becomes difficult to determine which objects in your system were invalid before starting the upgrade, and which objects become invalid as a result of the upgrade.

**Related Topics**

- [Pre-Upgrade Information Tool and AutoUpgrade Preupgrade](using-preupgrade-information-tool-for-oracle-database.md)

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Invalid Objects and Premature Use of Postupgrade Tool

Never run the postupgrade status tool for the new Oracle Database release (`utlusts.sql`) until after you complete the upgrade.

Oracle recommends that you run the postupgrade status tool only after the upgrade process is complete, and after you have run `utlrp.sql`. If the postupgrade status tool is run before you run `@utlrp.sql`, then the output of tool may not display the accurate final component status value. If the tool is run before running `utlrp.sql`, then the component status values may not properly reflect the final state. You can only determine the final component state after running `utlrp.sql`.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Resolving Oracle Database Upgrade Script Termination Errors

Review this section if you encounter ORA-00942, ORA-00904, or ORA-01722 errors.

If you did not run AutoUpgrade with the `preupgrade` parameter before starting the upgrade, then the `catctl.pl` and `catupgrd.sql` scripts terminate with errors such as the following:

    ORA-00942: table or view does not exist
    ORA-00904: "TZ_VERSION": invalid identifier
    ORA-01722: invalid number

**Note:**

AutoUpgrade and Replay Upgrade are the only supported method for upgrading to Oracle Database 23ai. All other methods, including Database Upgrade Assistant (DBUA), are desupported.

If you receive any of these errors, then use this procedure to correct the problem:

1.  Enter a `SHUTDOWN ABORT` command, and wait for the command to complete running.

2.  Revert to the original Oracle home directory

3.  Run the AutoUpgrade utility using the preupgrade parameter, and correct the issues that it reports in the `upgrade.xml` file.

**Related Topics**

- [Pre-Upgrade Information Tool for Oracle Database](using-preupgrade-information-tool-for-oracle-database.md)

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Troubleshooting Causes of Resource Limits Errors while Upgrading Oracle Database

Review this section if you encounter `ORA-01650`, `ORA-01651`, `ORA-01652`, `ORA-01653`, `ORA-01654`, `ORA-01655`, `ORA-0431`, `ORA-01562`, `ORA-19815`, or other errors that suggest resource limit errors.

If you run out of resources during an upgrade, then increase the resource allocation. After increasing the resource allocation, shut down the instance with SHUTDOWN ABORT, and restart the instance in UPGRADE mode before re-running the `catupgrd.sql` script. If you run the upgrade using the Parallel Upgrade Utility (`catctl.pl`), then to automatically resume the upgrade from the point of failure, run the utility with the `-R` option. After you fix issues, AutoUpgrade automatically resumes upgrades.

The resources that generally require increases for a new Oracle Database release are as follows:

- `SYSTEM` and `SYSAUX` tablespaces

  If your `SYSTEM` tablespace size is insufficient, then typically you receive the following error message:

      ORA-01650: unable to extend rollback segment string by string in tablespace string
      ORA-01651: unable to extend save undo segment by string for tablespace string
      ORA-01652: unable to extend temp segment by string in tablespace string
      ORA-01653: unable to extend table string.string by string in tablespace string
      ORA-01654: unable to extend index string.string by string in tablespace string
      ORA-01655: unable to extend cluster string.string by string in tablespace string

  To avoid these errors, set `AUTOEXTEND ON MAXSIZE UNLIMITED` for the `SYSTEM` and `SYSAUX` tablespaces.

- Shared memory

  In some cases, you may require larger shared memory pool sizes. The error message indicates which shared memory initialization parameter you must increase, in the following format:

      ORA-04031: unable to allocate string bytes of shared memory ("string","string","string","string")

  **See Also:**

  [Oracle Database Administrator's Guide](../admin/managing-memory.md) for information about using manual shared memory management

- Rollback segments/undo tablespace

  If you are using rollback segments, then you must have a single large (100 MB) `PUBLIC` rollback segment online while the upgrade scripts are being run. Smaller public rollback segments should be taken offline during the upgrade. If your rollback segment size is insufficient, then typically you encounter the following error:

      ORA-01562: failed to extend rollback segment number string

  If you are using an undo tablespace, then be sure it is at least 400 MB.

- Fast Recovery Area

  If you are using a Fast Recovery Area and it fills up during the upgrade, then the following error appears in the alert log, followed by suggestions for recovering from the problem:

      ORA-19815: WARNING: db_recovery_file_dest_size of string bytes is 98.99%
      used, and has string remaining bytes available.

  Identify the root cause of the problem, and take appropriate actions to proceed with the upgrade. To avoid issues during the upgrade, increase the amount of space available in your Fast Recovery Area before starting the upgrade.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Resolving SQL\*Plus Edition Session Startup Error for Oracle Database

Use this section to understand and resolve SP2–1540: "Oracle Database cannot startup in an Edition session."

If an upgrade script or a command running in SQL\*Plus set the EDITION parameter, then Oracle Database cannot start properly afterward. When you attempt to start the database, you receive the following error:

    SP2-1540: "Oracle Database cannot startup in an Edition session"

To avoid this problem, after running `catugrd.sql` or any SQL\*Plus session where this parameter is changed, exit the SQL\*Plus session and restart the instance in a different session.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Error ORA-00020 Maximum Number of Processes Exceeded When Running utlrp.sql

This error may indicate that your Oracle configuration does not have sufficient number of processes available for the recompile.

Refer to Oracle documentation for more details about setting the PROCESSES parameter.

**See Also:**

[Oracle Database Reference](../refrn/PROCESSES.md)

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Fixing ORA-28365: Wallet Is Not Open Error

If you use Oracle wallet with Transparent Data Encryption (TDE), and you use Database Upgrade Assistant (DBUA) to upgrade the database, then you can encounter an ORA-28365 "wallet is not open" error.

To avoid this problem, complete the following tasks before upgrading:

1.  Log in as an authorized user.
2.  Manually copy the `sqlnet.ora` file, and the wallet file, `ewallet.p12`, to the new release Oracle home.
3.  Open the Oracle wallet in mount.
    For example:

        SQL> STARTUP MOUNT;
        SQL> ALTER SYSTEM SET ENCRYPTION WALLET OPEN
4.  Start the upgrade as usual.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Resolving issues with view CDB_JAVA_POLICY

If the view CDB_JAVA_POLICY becomes invalid, then use this procedure.

After an upgrade to Oracle Database 12c release 2 (12.2) and later releases, or a downgrade from release 12.2 or later releases to 12.1, you can encounter issues with the CDB_JAVA_POLICY view. CDB_JAVA_POLICY can become invalid, or it can encounter errors when you use it in a manner that normally works. If this happens, then connect as SYS, and run the following commands.

Non-CDBs:

    alter session set "_ORACLE_SCRIPT"=true;

    exec CDBView.create_cdbview(false,'SYS','dba_java_policy','CDB_java_policy');

    grant select on SYS.CDB_java_policy to select_catalog_role
    /
    create or replace public synonym CDB_java_policy for SYS.CDB_java_policy
    /

Multitenant architecture systems:

Run these same commands, but run them first in CDB\$ROOT, and then in other containers in the CDB.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Continuing Upgrades After Server Restarts (ADVM/ACFS Driver Error)

On Windows platforms, an error may occur related to ADVM or ACFS drivers if a server restarts during an upgrade.

If a server restarts during the upgrade, then you may see one of the following error messages:

    ACFS-9427: Failed to unload ADVM/ACFS drivers. A system reboot is recommended

    ACFS-9428 Failed to load ADVM/ACFS drivers. A system reboot is recommended.

- Cause

  The ADVM and ACFS drivers are still in use. You must restart the system to start the new drivers.

- Action

  Complete the steps as described in the following procedures.

For nodes other than the first node (the node on which the upgrade is started):

1.  Restart the node where the error occurs.

2.  Run the root script on that node again.

For first nodes (the node on which the upgrade is started):

1.  Complete the upgrade of all other nodes in the cluster.

2.  Restart the first node.

3.  Run the root script on the first node again.

4.  To complete the upgrade, log in as root, and run the script `configToolAllCommands`, located in the path `Grid_home``/cfgtoollogs/configToolAllCommands`.

**See Also:**

[Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your operating system for more information about troubleshooting upgrade issues for clusters

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Component Status and Upgrades

Component status settings are affected both by the components that you previously installed, and by the support of those components for upgrades.

Topics:

- Understanding Component Status With the Post-Upgrade Status Tool
  The Post-Upgrade Status tool, `utlusts.sql`, reports database component status after an upgrade is completed.
- Component OPTION OFF Status and Upgrades
  The upgrade status of `OPTION OFF` components is affected both by the support in the target release for a component, and if a component must be upgraded as part of an upgrade.
- Example of an Upgrade Summary Report
  Upgrade summary reports provide information about the upgrade status of components.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

#### Understanding Component Status With the Post-Upgrade Status Tool

The Post-Upgrade Status tool, `utlusts.sql`, reports database component status after an upgrade is completed.

You can run the Post-Upgrade Status Tool `utlusts.sql` anytime after upgrade, post-upgrade, or after recompiling invalid objects with `utlrp.sql`.

The following list briefly describes the status values that the Post-Upgrade Status tool reports:

- `INVALID`

  When the upgrade completed, some objects for the component remained in an invalid state. If you find no errors in the log file for component upgrades then run the script `utlrp.sql`. Running this script may change the status of invalid components to `VALID` without rerunning the entire upgrade. Check the `DBA_REGISTRY` view after running `utlrp.sql`.

- `VALID`

  The component is valid with no errors.

- `LOADING`

  The component is loading

- `LOADED`

  The component has successfully finished loading.

- `UPGRADING`

  The component is in process being upgraded.

- `UPGRADED`

  The component has completed upgrading with no errors.

- `DOWNGRADING`

  The component is in process being downgraded.

- `DOWNGRADED`

  The component has completed downgrading with no errors.

- `REMOVING`

  The component is in process being removed.

- `REMOVED`

  The component was not upgraded because it was removed from the database.

- `OPTION OFF`

  The server option required for the component was not installed or was not linked with the server. Check the `V$OPTION` view and the install logs. Install the component or relink the server with the required option, and then re-run the Parallel Upgrade Utility.

- `NO SCRIPT`

  The component upgrade script was not found in `$ORACLE_HOME`. Check the install logs, install the component software, and then re-run the Parallel Upgrade Utility.

**Note:**

You can run the Parallel Upgrade Utility (`catctl.pl` using the command-line scripts `dbupgrade`, on all supported platforms).

**Parent topic:** Component Status and Upgrades

#### Component OPTION OFF Status and Upgrades

The upgrade status of `OPTION OFF` components is affected both by the support in the target release for a component, and if a component must be upgraded as part of an upgrade.

There are three cases where `OPTION OFF` components are upgraded, or are not upgraded.

##### Unsupported Components With Status `OPTION OFF`

If there is a component in the database that is in the status `OPTION OFF`, and that component is no longer supported for database upgrades to the target release, then this component is not upgraded. After the upgrade, its version and status remain unchanged.

##### Supported Components With Status `OPTION OFF`

If there is a component in the database that is in the status `OPTION OFF`, but that component is supported for database upgrades to the target release, then this component is upgraded. After the upgrade, the component’s version matches the target release version. The status for this component is either `UPGRADED` (a successful upgrade), or `INVALID` (errors). Rerun the upgrade as needed, until all the upgraded components have a status of `UPGRADED`. Then run `utlrp.sql`. If a component was in the status `OPTION OFF` before the upgrade, then after it is upgraded, and its compile and validation is successful, its status reverts back to `OPTION OFF`.

##### Supported Components With Required Options That Must Be Upgraded

All components with required options must be upgraded. These components are:

- `RAC`

- `SDO`

- `APS`

- `XOQ`

Components that must be upgraded follow the same procedure for upgrades as for standard supported components with status `OPTION OFF`

**Parent topic:** Component Status and Upgrades

#### Example of an Upgrade Summary Report

Upgrade summary reports provide information about the upgrade status of components.

After the upgrade completes, starting with Oracle Database 12c release 2, the upgrade utility script (for example, in Oracle Database 19c, `utlusts.sql`) writes a copy of the report using the following write order:

1.  `ORACLE_BASE/cfgtoollogs/``db_unique_name``/upgrade``YYMMDDHHMMSC``/upg_summary.rpt`

2.  `$ORACLE_HOME/rdbms/log/upg_summary.rpt`

3.  Linux and UNIX:

        /tmp/upg_summary.rpt

    Windows:

         \TEMP\upg_summary.rpt

If the utility script cannot create the report under the first directory scheme, then it attempts to write to the second location, and then the third location. If it cannot write to any of these paths, then it does not write an upgrade summary report. This example is from Oracle Database 18c.

Example 5-1 Upgrade Summary Report for the Post-Upgrade Status Tool

    Oracle Database Release 18 Post-Upgrade Status Tool    05-27-2018 23:41:0

    Component                               Current         Full     Elapsed Time
    Name                                    Status          Version  HH:MM:SS

    Oracle Server                          UPGRADED      18.3.0.0.0  00:18:21
    JServer JAVA Virtual Machine           UPGRADED      18.3.0.0.0  00:04:31
    Oracle XDK                             UPGRADED      18.3.0.0.0  00:00:51
    Oracle Database Java Packages          UPGRADED      18.3.0.0.0  00:00:22
    OLAP Analytic Workspace                UPGRADED      18.3.0.0.0  00:00:51
    Oracle Label Security                  UPGRADED      18.3.0.0.0  00:00:20
    Oracle Database Vault                  UPGRADED      18.3.0.0.0  00:00:40
    Oracle Text                            UPGRADED      18.3.0.0.0  00:01:37
    Oracle Workspace Manager               UPGRADED      18.3.0.0.0  00:01:10
    Oracle Real Application Clusters       UPGRADED      18.3.0.0.0  00:00:00
    Oracle XML Database                    UPGRADED      18.3.0.0.0  00:02:17
    Oracle Multimedia                      UPGRADED      18.3.0.0.0  00:03:01
    Spatial                                UPGRADED      18.3.0.0.0  00:06:23
    Oracle OLAP API                        UPGRADED      18.3.0.0.0  00:00:22
    Upgrade Datapatch                                                00:00:10
    Final Actions                                                    00:00:20
    Post Upgrade                                                     00:00:05
    Post Upgrade Datapatch                                           00:00:04

    Total Upgrade Time: 00:41:45

**Parent topic:** Component Status and Upgrades

### Standard Edition Starter Database and Components with Status OPTION OFF

Starting in Oracle Database 18c (18.1), all `OPTION OFF` components are upgraded to the new release, but these options are disabled for Oracle Database Standard Edition (SE) remain OPTION OFF.

When you upgrade Oracle Database Standard Edition (SE) starter databases, the components that are not included with starter databases are turned on and upgraded. When `utlrp.sql` is run, options that are not turned on with your server and not included with SE are reset to `OPTION OFF` in the `DBA_REGISTRY` view.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Adjusting Oracle ASM Password File Location After Upgrade

You must create a new password file for Oracle ASM after an Oracle Grid Infrastructure upgrade.

The Oracle ASM password file location is not shown in the command output when you run `srvctl config asm` after a Grid Infrastructure upgrade. The location of the password file is not automatically passed to the new Oracle ASM disk group. To enable SRVCTL to have the password file location after upgrade, you must advance the diskgroup compatibility setting and create a PWFILE in the disk group. Then SRVCTL reports the configured location of the shared PWFILE.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md) for information about managing shared password files in disk groups

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Fixing "Warning XDB Now Invalid" Errors with Pluggable Database Upgrades

Review this topic if you encounter "Warning: XDB now invalid, invalid objects found” errors when upgrading pluggable databases (PDBs).

You can encounter XML object errors when you plug an Oracle Database 12c release 1 (12.1) pluggable database (PDB) into an Oracle Database 12c release 2 (12.2) or later release multitenant container database (CDB).

Common objects (objects with sharing='METADATA LINK' in `dba_objects`) are created by registering system-generated names in an object-relational XML schema. Those common types are created by registering some ORDSYS schemas with object-relational storage.

The names of these common objects are system-generated, and the names generated in release 12.1 can be different from the names used for these objects in release 12.2 and later releases. Because of these possible name changes, you can find that the release 12.1 object types do not have matching common types in the release 12.2 or later release CDB root.

Resolve this issue using the following procedure:

1.  Query the view `PDB_PLUG_IN_VIOLATIONS` in the target CDB root to see if there is any action containing `'GetTypeDDL'`
    If you find `'GetTypeDDL'` actions, then the upgraded PDB has the common objects issue.
2.  Run the PL/SQL packages `SET SERVEROUTPUT ON` and `exec xdb.DBMS_XMLSTORAGE_MANAGE.GetTypeDDL` in the target PDB to generate a user-named SQL script (for example, `script1.sql`).
3.  Run the script you created in step 2 (for example, `script1.sql` in the source 12.1 CDB to obtain the type creation script for each of the common types for which you are encountering errors
4.  Generate another user-named SQL script (for example, `script2.sql`) that contains these creation scripts.
5.  Run the script that you created on the source 12.1 CDB (for example, `script2.sql`) in the target PDB.

The script that you generate from the release 12.1 source CDB type creation scripts generates all of these objects in the target PDB. Making these common objects available in the target PDB should eliminate the invalid XDB errors.

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Fixing ORA-27248: sys.dra_reevaluate_open_failures is running

Use this procedure to identify `DRA_REEVALUATE_OPEN_FAILURES` jobs that block upgrades.

During an upgrade, if DBUA fails with the error `ORA-27248: sys.dra_reevaluate_open_failures is running`, then the job `DRA_REEVALUATE_OPEN_FAILURES` is running, which causes upgrade failures. Ensure that the job is stopped before continuing the upgrade.

In a job definition, if `ALLOW_RUNS_IN_RESTRICTED_MODE` is set to TRUE, and the job owner is permitted to log in during restricted mode, then that job is permitted to run when the database is in restricted or upgrade mode. The default setting for this parameter is FALSE.

Use the following query to see the state of any running jobs:

    SQL> select OBJECT_NAME, Owner, OBJECT_TYPE from dba_objects whereobject_name like '%DRA_REEVA%';

**Parent topic:** Troubleshooting the Upgrade for Oracle Database

### Fixing Failed Upgrades Where Only Datapatch Fails

If only datapatch fails during an upgrade, then rerun datapatch directly.

The Datapatch script is a shell script. In some patching operations, the final post-upgrade patches may not run, due to errors such as ORA-20001. If only the Datapatch script fails, then you do not need to run the upgrade again to fix this issue. Instead, run the datapatch script directly.

To fix a failed datapatch, log in as the Oracle user, and complete this procedure:

1.   Change directory to Opatch inside the upgraded Oracle home.
        $ cd $ORACLE_HOME/OPatch
2.  Run the datapatch command.
    On Linux and Unix:

        ./datapatch -verbose

    On Microsoft Windows:

        datapatch -verbose

**Parent topic:** Troubleshooting the Upgrade for Oracle Database
