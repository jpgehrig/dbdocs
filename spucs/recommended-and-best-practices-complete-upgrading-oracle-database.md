Oracle recommends that you complete these good practices guidelines for updating Oracle Database. Except where noted, these practices are recommended for all types of upgrades.

- Back Up the Database
  Oracle strongly recommends that you at least perform a level 1 backup, or if time allows, perform a level 0 backup.
- Run AutoUpgrade Postupgrade Checks
  If you did not run AutoUpgrade in `deploy` mode, then run Autoupgrade with the `preupgrade` parameter, run in `postfixups` mode.
- Regathering Fixed Objects Statistics with DBMS_STATS
  After an upgrade, or after other database configuration changes, Oracle strongly recommends that you regather fixed object statistics after you have run representative workloads on Oracle Database.
- Reset Passwords to Enforce Case-Sensitivity
  For upgraded databases, improve security by using case-sensitive passwords for default user accounts and user accounts.
- Finding and Resetting User Passwords That Use the 10G Password Version
  For better security, find and reset passwords for user accounts that use the `10G` password version so that they use later, more secure password versions.
- Understand Oracle Grid Infrastructure, Oracle ASM, and Oracle Clusterware
  Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM) are both part of an Oracle Grid Infrastructure installation.
- Oracle Grid Infrastructure Installation and Upgrade and Oracle ASM
  Oracle ASM is installed with Oracle Grid Infrastructure.
- Add New Features as Appropriate
  Review new features as part of your database upgrade plan.
- Develop New Administrative Procedures as Needed
  Plan a review of your scripts and procedures, and change as needed.
- Migrating From Rollback Segments To Automatic Undo Mode
  If your database release is earlier than Oracle Database 11g, then you must migrate the database that is being upgraded from using rollback segments (manual undo management) to automatic undo management.
- Migrating Tables from the LONG Data Type to the LOB Data Type
  You can use the `ALTER TABLE` statement to change the data type of a `LONG` column to `CLOB` and that of a `LONG RAW` column to `BLOB`.
- Turn off Traditional Auditing in Upgraded Oracle Databases
  Traditional auditing is deprecated in Oracle Database 21c, and is desupported in Oracle Database 23c. Oracle recommends that you turn off traditional audit in your database and use only unified auditing.
- Identify Oracle Text Indexes for Rebuilds
  You can run a script that helps you to identify Oracle Text index indexes with token tables that can benefit by being rebuilt after upgrading to the new Oracle Database release..
- Dropping and Recreating DBMS_SCHEDULER Jobs
  If DBMS_SCHEDULER jobs do not function after upgrading from an earlier release, drop and recreate the jobs.
- Transfer Unified Audit Records After the Upgrade
  Review these topics to understand how you can obtain better performance after you upgrade and migrate to unified auditing
- About Recovery Catalog Upgrade After Upgrading Oracle Database
  If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.
- Enabling Disabled Release Update Bug Fixes in the Upgraded Database
  Because bug fixes in Release Updates that can cause execution plan changes are disabled, Oracle recommends that you enable the disabled bug fixes that you want to use.
- About Testing the Upgraded Production Oracle Database
  Repeat tests on your production database that you carried out on your test database to ensure applications operate as expected.
- Upgrading the Time Zone File Version After Upgrading Oracle Database
  If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use any of the supported methods to upgrade the time zone file.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks.md)

### Back Up the Database

Oracle strongly recommends that you at least perform a level 1 backup, or if time allows, perform a level 0 backup.

**Related Topics**

- [Backing Up the Database](../bradv/backing-up-database.md)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Run AutoUpgrade Postupgrade Checks

If you did not run AutoUpgrade in `deploy` mode, then run Autoupgrade with the `preupgrade` parameter, run in `postfixups` mode.

**Note:**

If you ran AutoUpgrade in `deploy` mode, then this step was already completed for you, so you do not need to complete it now.

To see how to check your database after upgrades, use the following example.

Example 4-2 Running AutoUpgrade Using Postupgrade Fixup Mode

Suppose you have upgraded an Oracle Database 12c Release 2 (12.2) Oracle Database. To run postupgrade checks, you complete this procedure:

1.  Set the Oracle home environment to the source Oracle Database home:

        setenv ORACLE_HOME /u01/app/oracle/product/12.2.0/dbhome_1

    .

2.  Set the Oracle System Identifier (SID) to the source Oracle Database SID:

        setenv ORACLE_SID db122

    .

3.  Run AutoUpgrade using the preupgrade parameter in postfixups mode, setting the target home to the target Oracle Database Oracle home. For example:

        java -jar autoupgrade.jar -preupgrade "target_home=/u01/app/oracle/product/19.0.0/dbhome_1,dir=/autoupgrade/test/log" –mode postfixups

4.  Check the results of the postfixup script checks in the file `postfixups.xml` under directory `/autoupgrade/test/log/db122/102/postfixups`.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Regathering Fixed Objects Statistics with DBMS_STATS

After an upgrade, or after other database configuration changes, Oracle strongly recommends that you regather fixed object statistics after you have run representative workloads on Oracle Database.

**Note:**

To provide the most correct fixed object statistics for performance tuning, Oracle strongly recommends that you gather baseline statistics at a point when the system is running with a representative workload. For useful results, never run `DBMS_STATS.GATHER_FIXED_OBJECTS_STATS` immediately after the upgrade.

Fixed objects are the `X$` tables and their indexes. `V$` performance views are defined through `X$` tables. Gathering fixed object statistics is valuable for database performance, because these statistics help the optimizer to generate good execution plans, which can improve database performance. Failing to obtain representative statistics can lead to suboptimal execution plans, which can cause significant performance problems.

Ensure that your database has run representative workloads, and then gather fixed objects statistics by using the `DBMS_STATS.GATHER_FIXED_OBJECTS_STATS` PL/SQL procedure. `DBMS_STATS.GATHER_FIXED_OBJECTS_STATS` also displays recommendations for removing all hidden or underscore parameters and events from the `INIT.ORA` or `SPFILE`.

Because of the transient nature of `X$` tables, you must gather fixed objects statistics when there is a representative workload on the system. If you cannot gather fixed objects statistics during peak load, then Oracle recommends that you do it after the system is in a runtime state, and the most important types of fixed object tables are populated.

To gather statistics for fixed objects, run the following PL/SQL procedure:

    SQL> execute dbms_stats.gather_fixed_objects_stats;

**Related Topics**

- [Gathering Database Statistics](../tgdba/gathering-database-statistics.md)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Reset Passwords to Enforce Case-Sensitivity

For upgraded databases, improve security by using case-sensitive passwords for default user accounts and user accounts.

For greater security, Oracle recommends that you enable case sensitivity in passwords. Case sensitivity increases the security of passwords by requiring that users enter both the correct password string, and the correct case for each character in that string. For example, the password `hPP5620qr` fails if it is entered as `hpp5620QR` or `hPp5620Qr`.

To secure your database, create passwords in a secure fashion. If you have default passwords in your database, then change these passwords. By default, case sensitivity is enforce when you change passwords. Every password should satisfy the Oracle recommended password requirements, including passwords for predefined user accounts.

For new databases created after the upgrade, there are no additional tasks or management requirements.

#### Existing Database Requirements and Guidelines for Password Changes

- If the default security settings for Oracle Database 12c release 1 (12.1) and later are in place, then passwords must be at least eight characters, and passwords such as `welcome` and `oracle` are not allowed.

- The `IGNORECASE` parameter is deprecated. Do not use this parameter.

- For existing databases, to take advantage of password case-sensitivity, you must reset the passwords of existing users during the database upgrade procedure. Reset the password for each existing database user with an `ALTER` `USER` statement.

- Query the `PASSWORD_VERSIONS` column of `DBA_USERS` to find the `USERNAME` of accounts that only have the 10G password version, and do not have either the `11G` or the `12C` password version. Reset the password for any account that has only the `10G` password version.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about password case sensitivity

- [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md) for more information about password strength

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Finding and Resetting User Passwords That Use the 10G Password Version

For better security, find and reset passwords for user accounts that use the `10G` password version so that they use later, more secure password versions.

#### Finding All Password Versions of Current Users

You can query the `DBA_USERS` data dictionary view to find a list of all the password versions configured for user accounts.

For example:

    SELECT USERNAME,PASSWORD_VERSIONS FROM DBA_USERS;

    USERNAME                       PASSWORD_VERSIONS
    ------------------------------ -----------------
    JONES                          10G 11G 12C
    ADAMS                          10G 11G
    CLARK                          10G 11G
    PRESTON                        11G
    BLAKE                          10G

The `PASSWORD_VERSIONS` column shows the list of password versions that exist for the account. `10G` refers to the earlier case-insensitive Oracle password version, `11G` refers to the SHA-1-based password version, and `12C` refers to the SHA-2-based SHA-512 password version.

- User `jones`: The password for this user was reset in Oracle Database 12c Release 12.1 when the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter setting was `8`. This enabled all three password versions to be created.

- Users `adams` and `clark`: The passwords for these accounts were originally created in Oracle Database 10g and then reset in Oracle Database 11g. The Oracle Database 11g software was using the default `SQLNET.ALLOWED_LOGON_VERSION` setting of `8` at that time. Because case insensitivity is enabled by default, their passwords are now case sensitive, as is the password for `preston`.

- User `preston`: This account was imported from an Oracle Database 11g database that was running in Exclusive Mode (`SQLNET.ALLOWED_LOGON_VERSION = 12`).

- User `blake`: This account still uses the Oracle Database 10g password version. At this stage, user `blake` is prevented from logging in.

#### Resetting User Passwords That Use the 10G Password Version

You should remove the `10G` password version from the accounts of all users. In the following procedure, to reset the passwords of users who have the `10G` password version, you must temporarily relax the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` setting, which controls the ability level required of clients before login can be allowed. Relaxing the setting enables these users to log in and change their passwords, and hence generate the newer password versions in addition to the `10G` password version. Afterward, you can set the database to use Exclusive Mode and ensure that the clients have the `O5L_NP` capability. Then the users can reset their passwords again, so that their password versions no longer include `10G`, but only have the more secure `11G` and `12C` password versions.

1.  Query the `DBA_USERS` view to find users who only use the `10G` password version.
        SELECT USERNAME FROM DBA_USERS
        WHERE ( PASSWORD_VERSIONS = '10G '
        OR PASSWORD_VERSIONS = '10G HTTP ')
        AND USERNAME <> 'ANONYMOUS';
2.  Configure the database so that it does not run in Exclusive Mode, as follows:
    1.  Edit the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` setting in the `sqlnet.ora` file so that it is more permissive than the default. For example:
            SQLNET.ALLOWED_LOGON_VERSION_SERVER=11
    2.  If you are in the CDB root, then restart the database (for example, `SHUTDOWN IMMEDIATE` followed by `STARTUP`). If you are in a PDB, connect to the root using the `SYSDBA` administrative privilege, and then enter the following statements:
            ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
            ALTER PLUGGABLE DATABASE pdb_name OPEN;
3.  Expire the users that you found when you queried the `DBA_USERS` view to find users who only use the `10G` password version.
    You must expire the users who have only the `10G` password version, and do not have one or both of the `11G` or `12C` password versions.

    For example:

        ALTER USER username PASSWORD EXPIRE;
4.  Ask the users whose passwords you expired to log in.
    When the users log in, they are prompted to change their passwords. The database generates the missing `11G` and `12C` password versions for their account, in addition to the `10G` password version. The `10G` password version continues to be present, because the database is running in the permissive mode.
5.  Ensure that the client software with which the users are connecting has the `O5L_NP` ability.
    All Oracle Database release 11.2.0.3 and later clients have the `O5L_NP` ability. If you have an earlier Oracle Database client, then you must install the `CPUOct2012` patch.
6.  After all clients have the `O5L_NP` capability, set the security for the server back to Exclusive Mode, as follows:
    1.  Remove the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter from the server `sqlnet.ora` file, or set the value of `SQLNET.ALLOWED_LOGON_VERSION_SERVER` in the server `sqlnet.ora` file back to `12`, to set it to an Exclusive Mode.
            SQLNET.ALLOWED_LOGON_VERSION_SERVER = 12
    2.  If you are in the CDB root, then restart the database (for example, `SHUTDOWN IMMEDIATE` followed by `STARTUP`). If you are in a PDB, connect to the root using the `SYSDBA` administrative privilege, and then enter the following statements:
            ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
            ALTER PLUGGABLE DATABASE pdb_name OPEN;
7.  Find the accounts that still have the `10G` password version.
        SELECT USERNAME FROM DBA_USERS
        WHERE PASSWORD_VERSIONS LIKE '%10G%'
        AND USERNAME <> 'ANONYMOUS';
8.  Expire the accounts that still have the `10G` password version.
        ALTER USER username PASSWORD EXPIRE;
9.  Ask these users to log in to their accounts.
    When the users log in, they are prompted to reset their passwords. The database then generates only the `11G` and `12C` password versions for their accounts. Because the database is running in Exclusive Mode, the `10G` password version is no longer generated.
10. Rerun the following query:
        SELECT USERNAME FROM DBA_USERS
        WHERE PASSWORD_VERSIONS LIKE '%10G%'
        AND USERNAME <> 'ANONYMOUS';

    If this query does not return any results, then it means that no user accounts have the `10G` password version. Hence, the database is running in a more secure mode than in previous releases.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Understand Oracle Grid Infrastructure, Oracle ASM, and Oracle Clusterware

Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM) are both part of an Oracle Grid Infrastructure installation.

If Oracle Grid Infrastructure is installed for a single server, then it is deployed as an Oracle Restart installation with Oracle ASM. If Oracle Grid Infrastructure is installed for a cluster, then it is deployed as an Oracle Clusterware installation with Oracle ASM.

Oracle Restart enhances the availability of Oracle Database in a single-instance environment. If you install Oracle Restart, and there is a temporary failure of any part of the Oracle Database software stack, including the database, listener, and Oracle ASM instance, Oracle Restart automatically restarts the failed component. In addition, Oracle Restart starts all these components when the database host computer is restarted. The components are started in the proper order, taking into consideration the dependencies among components.

Oracle Clusterware is portable cluster software that enables clustering of single servers so that they cooperate as a single system. Oracle Clusterware also provides the required infrastructure for Oracle RAC. In addition, Oracle Clusterware enables the protection of any Oracle application or any other application within a cluster. In any case Oracle Clusterware is the intelligence in those systems that ensures required cooperation between the cluster nodes.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Oracle Grid Infrastructure Installation and Upgrade and Oracle ASM

Oracle ASM is installed with Oracle Grid Infrastructure.

In earlier releases, Oracle ASM was installed as part of the Oracle Database installation. Starting with Oracle Database release 11.2, Oracle ASM is installed when you install the Grid Infrastructure components. Oracle ASM shares an Oracle home with Oracle Clusterware.

**See Also:**

[Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your platform for information about Oracle homes, role-allocated system privileges groups, different installation software owner users, and other changes.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Add New Features as Appropriate

Review new features as part of your database upgrade plan.

Oracle Database New Features Guide describes many of the new features available in the new Oracle Database release. Determine which of these new features can benefit the database and applications. You can then develop a plan for using these features.

It is not necessary to make any immediate changes to begin using your new Oracle Database software. You can choose to introduce new feature enhancements into your database and applications gradually.

**See Also:**

[Oracle Database New Features Guide](../newft/index.md)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Develop New Administrative Procedures as Needed

Plan a review of your scripts and procedures, and change as needed.

After familiarizing yourself with the features of the new Oracle Database release, review your database administration scripts and procedures to determine whether any changes are necessary.

Coordinate your changes to the database with the changes that are necessary for each application. For example, by enabling integrity constraints in the database, you may be able to remove some data checking from your applications.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Migrating From Rollback Segments To Automatic Undo Mode

If your database release is earlier than Oracle Database 11g, then you must migrate the database that is being upgraded from using rollback segments (manual undo management) to automatic undo management.

Automatic undo management is the default undo space management mode. The `UNDO_MANAGEMENT` initialization parameter specifies which undo space management mode the system should use:

- If UNDO_MANAGEMENT is set to `AUTO` (or if UNDO_MANAGEMENT is not set), then the database instance starts in automatic undo management mode.

  A null UNDO_MANAGEMENT initialization parameter defaults to automatic undo management mode in Oracle Database 11g Release 1 (11.1) and later. In earlier releases it defaults to manual undo management mode. Use caution when upgrading earlier releases.

- If UNDO_MANAGEMENT is set to `MANUAL`, then undo space is allocated externally as rollback segments.

1.  Set the UNDO_MANAGEMENT parameter to `UNDO_MANAGEMENT=MANUAL`.
2.  Start the instance again and run through a standard business cycle to obtain a representative workload. Assess the workload, and compute the size of the undo tablespace that you require for automatic undo management.
3.  After the standard business cycle completes, run the following function to collect the undo tablespace size, and to help with the sizing of the undo tablespace. You require SYSDBA privileges to run this function.
        DECLARE
           utbsiz_in_MB NUMBER;
        BEGIN
           utbsiz_in_MB := DBMS_UNDO_ADV.RBU_MIGRATION;
        end;
        /

    This function runs a PL/SQL procedure that provides information on how to size your new undo tablespace based on the configuration and usage of the rollback segments in your system. The function returns the sizing information directly.
4.  Create an undo tablespace of the required size and turn on the automatic undo management by setting `UNDO_MANAGEMENT=AUTO` or by removing the parameter.
5.  For Oracle RAC configurations, repeat these steps on all instances.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Migrating Tables from the LONG Data Type to the LOB Data Type

You can use the `ALTER TABLE` statement to change the data type of a `LONG` column to `CLOB` and that of a `LONG RAW` column to `BLOB`.

The `LOB` data types (`BFILE`, `BLOB`, `CLOB`, and `NCLOB`) can provide many advantages over `LONG` data types.

In the following example, the `LONG` column named `long_col` in table `long_tab` is changed to data type `CLOB`:

    SQL> ALTER TABLE Long_tab MODIFY ( long_col CLOB );

After using this method to change `LONG` columns to LOBs, all the existing constraints and triggers on the table are still usable. However, all the indexes, including Domain indexes and Functional indexes, on all columns of the table become unusable and must be rebuilt using an `ALTER INDEX...REBUILD` statement. Also, the Domain indexes on the `LONG` column must be dropped before changing the `LONG` column to a LOB.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md) for information about modifying applications to use LOB data

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Turn off Traditional Auditing in Upgraded Oracle Databases

Traditional auditing is deprecated in Oracle Database 21c, and is desupported in Oracle Database 23c. Oracle recommends that you turn off traditional audit in your database and use only unified auditing.

Unified Auditing and Traditional Auditing (mixed mode) has been the default auditing mode from Oracle Database 12c onward. Mixed mode auditing was offered to enable you to become familiar with Unified Auditing, and to transition from Traditional Auditing. With the deprecation of Traditional Auditing in Oracle Database 21c, Oracle recommends that you turn off traditional audit in your database and use only unified auditing.. Refer to the procedure in Oracle Database Security Guide.

- Understanding Auditing for Oracle Database
  Decide which audit policies you want to use in the upgraded database.
- Turning Off Traditional Auditing and Using Unified Auditing for Oracle Database
  Use this procedure for multitenant container (CDB) databases to turn off traditional auditing, and to use unified auditing.
- About Managing Earlier Audit Records After You Move to Unified Auditing
  Review, archive, and purge earlier audit trails in preparation for using the unified audit trail.
- Moving From Pure Unified Auditing to Mixed-Mode Auditing
  Use this procedure to turn on traditional auditing in mixed-mode audit configuration.
- Obtaining Documentation References if You Choose Not to Use Unified Auditing
  You can access documentation listed here to obtain configuration information about how to use non-unified auditing.

**Related Topics**

- [Checking if Your Database Has Migrated to Unified Auditing](../dbseg/introduction-to-auditing.md)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

#### Understanding Auditing for Oracle Database

Decide which audit policies you want to use in the upgraded database.

For newly created databases, the mixed-mode method of unified auditing is enabled by default, which has both traditional auditing and unified auditing. The predefined audit policies `ORA_SECURECONFIG` and `ORA_LOGIN_LOGOUT` policies are enabled by default. Oracle recommends that you consider turning off traditional auditing and use only unified

If you have upgraded from an earlier release to Oracle Database 12c, then your database uses the same auditing functionality that was used in the earlier release. Oracle recommends that you consider turning off traditional auditing, and ensure the predefined audit policies `ORA_SECURECONFIG` and `ORA_LOGIN_LOGOUT` policies are enabled so that you can start using pure unified auditing.

To enable and configure the audit policies and how they are used, choose one method as follows:

- Use the pure unified audit facility.

  Transition to unified auditing to use the full unified auditing facility features. After you complete the procedure to transition to unified auditing, you can create and enable new audit policies and also use the predefined audit policies. The audit records for these policies write to the unified audit trail. The earlier audit trails and their audit records remain, but no new audit records write to the earlier audit trails.

  **Note:**

  The audit configuration from the earlier release has no effect in the unified audit system. Only unified audit policies generate audit records inside the unified audit trail.

- Use a mixed-mode audit facility.

  The mixed-mode audit facility assists you transition to unified auditing. It enables both traditional and unified auditing facilities to run simultaneously and applies to both new and upgraded databases. The mixed-mode unified auditing facility becomes available if you enable at least one of the unified auditing predefined audit policies. Audit records for these policies write to the unified audit trail. The audit configuration in the earlier release of Oracle Database is also available, and the audit records for this configuration write to the earlier audit trails. If you decide that you prefer using the pure unified audit facility, then you can migrate to it.

  **Note:**

  If the database is not writable, then audit records write to new format operating system files in the `$ORACLE_BASE/audit/$ORACLE_SID` directory.

**Related Topics**

- [Auditing Activities with the Predefined Unified Audit Policies](../dbseg/configuring-audit-policies.md)
- [Secure Options Predefined Unified Audit Policy](../dbseg/configuring-audit-policies.md)

**Parent topic:** Turn off Traditional Auditing in Upgraded Oracle Databases

#### Turning Off Traditional Auditing and Using Unified Auditing for Oracle Database

Use this procedure for multitenant container (CDB) databases to turn off traditional auditing, and to use unified auditing.

Perform the following procedure in the `root`. The procedure configures both the `root` CDB and any associated PDBs to use unified auditing.

**Note:**

Oracle recommends that you start using unified auditing now. It is deprecated in Oracle Database 21c, and desupported in Oracle Database 23c.

If you need to continue using traditional auditing as a transition, you can disable unified auditing from the container database (CDB) root only, not for individual pluggable databases (PDBs).

However, when unified auditing is disabled, individual PDBs can use the mixed mode auditing, depending on whether or not the local audit policy is enabled in that PDB. If you have a CDB common audit policy enabled, then all PDBs use mixed mode auditing.

1.  Log in to SQL\*Plus as user `SYS` with the `SYSDBA` privilege.

        sqlplus sys as sysdba
        Enter password: password

    In the multitenant environment, this login connects you to `root`.

2.  Check if your Oracle Database is migrated to unified auditing using this query:

        SQL> SELECT VALUE FROM V$OPTION WHERE PARAMETER = 'Unified Auditing';

    If the output for the `VALUE` column is `TRUE`, then unified auditing is already enabled in your database. You can proceed to Managing Earlier Audit Records. If the output is `FALSE`, then complete the remaining steps in this procedure.

3.  Stop the database. For single-instance environments, enter the following commands from SQL\*Plus:

        SQL> SHUTDOWN IMMEDIATE
        SQL> EXIT

    For Windows systems, stop the Oracle service:

        net stop OracleService%ORACLE_SID%

    For Oracle Real Application Clusters (Oracle RAC) installations, shut down each database instance as follows:

        srvctl stop database -db db_name

4.  Stop the listener. (Stopping the listener is not necessary for Oracle RAC and Oracle Grid Infrastructure listeners.)

        lsnrctl stop listener_name

    You can find the name of the listener by running the `lsnrctl status` command. The `Alias` setting indicates the name.

5.  Go to the directory `$ORACLE_HOME/rdbms/lib`.

6.  Enable unified auditing for the Oracle user.

    - Linux and Unix

          make -f ins_rdbms.mk uniaud_on oracle ORACLE_HOME=$ORACLE_HOME

    - Microsoft Windows

      Rename the file `%ORACLE_HOME%/bin/orauniaud12.dll.dbl` to `%ORACLE_HOME%/bin/orauniaud12.dll`.

    **Note:**

    For Oracle RAC databases that have non-shared Oracle homes, you must repeat this step on each cluster member node, so that the binaries are updated inside the local ORACLE_HOME on each cluster node.

7.  Restart the listener.

        lsnrctl start listener_name

8.  Restart the database.

    Log in to SQL\*Plus and then enter the `STARTUP` command:

        sqlplus sys as sysoper
        Enter password: password

        SQL> STARTUP

    For Microsoft Windows systems, start the Oracle service:

        net start OracleService%ORACLE_SID%

    For Oracle RAC installations, start each database instance:

        srvctl start database -db db_name

After you migrate to unified auditing, refer to My Oracle Support Doc ID 2369172.1, "LOB Columns of Database Audit Trails should use Securefile Storage" and review information about the Oracle home script `Oracle_home``/rdbms/admin/auditpostupgrade.sql`. To obtain performance benefits of unified auditing, Oracle strongly recommends that you run this script after completing the upgrade.

**Related Topics**

- [LOB Columns of Database Audit Trails should use Securefile Storage (Doc ID 2659172.1)](https://support.oracle.com/rs?type=doc&id=2369172.1)

**Parent topic:** Turn off Traditional Auditing in Upgraded Oracle Databases

#### About Managing Earlier Audit Records After You Move to Unified Auditing

Review, archive, and purge earlier audit trails in preparation for using the unified audit trail.

After you complete the procedure in Oracle Database to turn off traditional auditing and use unified auditing, any audit records that your database had before remain in their earlier audit trails. You can archive these audit records and then purge their audit trails. With unified auditing in place, any new audit records write to the unified audit trail.

**Related Topics**

- [Archiving the Audit Trail](../dbseg/administering-the-audit-trail.md)
- [Purging Audit Trail Records](../dbseg/administering-the-audit-trail.md)

**Parent topic:** Turn off Traditional Auditing in Upgraded Oracle Databases

#### Moving From Pure Unified Auditing to Mixed-Mode Auditing

Use this procedure to turn on traditional auditing in mixed-mode audit configuration.

If you decide that you want to re-enable traditional auditing in mixed-mode, then you can use this procedure to turn on traditional auditing. In this case, your database uses the mixed-mode audit facility.

**Note:**

Be aware that traditional auditing is deprecated, and is desupported in Oracle Database 23c. Plan accordingly.

1.  Stop the database.

        sqlplus sys as sysoper
        Enter password: password

        SQL> SHUTDOWN IMMEDIATE
        SQL> EXIT

    For Microsoft Windows systems, stop the Oracle service:

        net stop OracleService%ORACLE_SID%

    For Oracle RAC installations, shut down each database instance as follows:

        srvctl stop database -db db_name

2.  Go to the `$ORACLE_HOME/rdbms/lib` directory.

3.  Disable the unified auditing executable.

    - Linux/Unix: Run the following command:

          make -f ins_rdbms.mk uniaud_off oracle ORACLE_HOME=$ORACLE_HOME

    - Microsoft Windows: Rename the `%ORACLE_HOME%/bin/orauniaud12.dll` file to `%ORACLE_HOME%/bin/orauniaud12.dll.dbl`.

4.  Restart the database.

        sqlplus sys as sysoper
        Enter password: password

        SQL> STARTUP
        SQL> EXIT

    For Microsoft Windows systems, start the Oracle service again.

        net start OracleService%ORACLE_SID%

    For Oracle RAC installations, start each database instance using the following syntax:

        srvctl start database -db db_name

**Parent topic:** Turn off Traditional Auditing in Upgraded Oracle Databases

#### Obtaining Documentation References if You Choose Not to Use Unified Auditing

You can access documentation listed here to obtain configuration information about how to use non-unified auditing.

After upgrading to the new release Oracle Database, if you choose not to change to unified auditing, then Oracle documentation and Oracle Technology Network provide information about traditional non-unified auditing.

- Oracle Database Security Guide: This guide is the main source of information for configuring auditing. You must use the Oracle Database Release 11g version of this manual. To access this guide:

  1.  Visit the database page on `docs.oracle.com` site on Oracle Technology Network:

      [`https://docs.oracle.com/en/database/index.html`](https://docs.oracle.com/en/database/index.html)

  2.  Select Oracle Database.

  3.  In the Downloads page, select the Documentation tab.

  4.  On the release list field, select Earlier Releases, and select Oracle Database 11g Release 2 (11.2).

  5.  From the Oracle Database 11g Release 2 (11.2) Documentation page, select the All Books link to display publications in the documentation set.

  6.  Search for Security Guide.

  7.  Select either the HTML or the PDF link for this guide.

**Parent topic:** Turn off Traditional Auditing in Upgraded Oracle Databases

### Identify Oracle Text Indexes for Rebuilds

You can run a script that helps you to identify Oracle Text index indexes with token tables that can benefit by being rebuilt after upgrading to the new Oracle Database release..

When you upgrade from Oracle Database 12c release 1 (12.2.0.1) to Oracle Database 18c and later releases, the Oracle Text token tables (`$I`, `$P`, and so on) are expanded from 64 bytes to 255 bytes. However, if you have indexes with existing token tables using the smaller size range, then the Oracle Text indexes cannot take advantage of this widened token column range. You must rebuild the indexes to use the 255 byte size range. Oracle provides a script that can assist you to identify indexes that can benefit by being rebuilt.

Obtain the script from My Oracle Support:

<https://support.oracle.com/rs?type=doc&id=2287094.1>

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Dropping and Recreating DBMS_SCHEDULER Jobs

If DBMS_SCHEDULER jobs do not function after upgrading from an earlier release, drop and recreate the jobs.

If you find that DBMS_SCHEDULER jobs are not functioning after an upgrade. drop and recreate those jobs. This issue can occur even if the upgrade process does not report issues, and system objects are valid.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Transfer Unified Audit Records After the Upgrade

Review these topics to understand how you can obtain better performance after you upgrade and migrate to unified auditing

- About Transferring Unified Audit Records After an Upgrade
  Transferring the unified audit records from Oracle Database 12c release 12.1 to the new relational table under the `AUDSYS` schema for the new Oracle Database release improves the read performance of the unified audit trail.
- Transferring Unified Audit Records After an Upgrade
  You can transfer unified audit records to the new relational table in AUDSYS by using the DBMS_AUDIT_MGMT.TRANSFER_UNIFIED_AUDIT_RECORDS PL/SQL procedure.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

#### About Transferring Unified Audit Records After an Upgrade

Transferring the unified audit records from Oracle Database 12c release 12.1 to the new relational table under the `AUDSYS` schema for the new Oracle Database release improves the read performance of the unified audit trail.

Starting with Oracle Database 12c Release 2, unified audit records are written directly to a new internal relational table that is located in the AUDSYS schema. In Oracle Database 12c release 12.1, the unified audit records were written to the common logging infrastructure (CLI) SGA queues. If you migrated to unified auditing in that release, then to obtain better read performance, you can transfer the unified audit records that are from that release to the new Oracle Database release internal table. It is not mandatory that you perform this transfer, but Oracle recommends that you do so to obtain better unified audit trail read performance. This is a one-time operation. All new unified audit records that are generated after the upgrade are written to the new table. The table is a read-only table. Any attempt to modify the metadata or data of this table is mandatorily audited.

After you upgrade to the new Oracle Database release, if you have any unified audit records present in the `UNIFIED_AUDIT_TRAIL` from the earlier release, then consider transferring them to the new internal relational table by using the transfer procedure for better read performance of the unified audit trail.

As with the `SYS` schema, you cannot query the AUDSYS schema if you have the SELECT ANY TABLE system privilege. In addition, this table is not listed as a schema object in the ALL_TABLES data dictionary view unless you have either the SELECT ANY DICTIONARY system privilege or an explicit SELECT privilege on this internal table. Until the database is open read write, the audit records are written to operating system spillover files (`.bin` format). However, you can transfer the audit records in these operating system files to the internal relational table after the database opens in the read write mode by using the DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES procedure.

**Parent topic:** Transfer Unified Audit Records After the Upgrade

#### Transferring Unified Audit Records After an Upgrade

You can transfer unified audit records to the new relational table in AUDSYS by using the DBMS_AUDIT_MGMT.TRANSFER_UNIFIED_AUDIT_RECORDS PL/SQL procedure.

1.  Log in to the database instance as a user who has been granted the AUDIT_ADMIN role.
    For example, in a non-multitenant environment:

        sqlplus sec_admin
        Enter password: password

    For a multitenant environment, connect to the root:

        sqlplus c##sec_admin@root
        Enter password: password

    You can perform this procedure execution in the root as well as in a PDB, because the UNIFIED_AUDIT_TRAIL view is container specific. In addition, the transfer procedure is container specific. That is, performing the transfer from the root does not affect the unified audit records that are present in the unified audit trail for the PDB.
2.  For a multitenant environment, query the DBA_PDB_HISTORY view to find the correct GUID that is associated with the CLI table that is specific to the container from which audit records must be transferred.
    For example:

        SQL> SELECT PDB_NAME, PDB_GUID FROM DBA_PDB_HISTORY;

        PDB_NAME  PDB_GUID
        --------  --------------------------------
        HR_PDB    33D96CA7862D53DFE0534DC0E40A7C9B
        ...
3.  In a multitenant environment, connect to the container for which you want to transfer the audit records.
    You cannot perform the transfer operation on a container that is different from the one in which you are currently connected.
4.  Run the DBMS_AUDIT_MGMT.TRANSFER_UNIFIED_AUDIT_RECORDS procedure.
    For example:
        SQL> EXEC DBMS_AUDIT_MGMT.TRANSFER_UNIFIED_AUDIT_RECORDS;

        PL/SQL procedure successfully completed.

    Or, to specify the PDB GUID:

        SQL> EXEC DBMS_AUDIT_MGMT.TRANSFER_UNIFIED_AUDIT_RECORDS ('33D96CA7862D53DFE0534DC0E40A7C9B');

        PL/SQL procedure successfully completed.
5.  If the database is in open read write mode, then run the DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES procedure.
    Until the database is in open read write mode, audit records are written to operating system (OS) files. The DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES procedure moves the unified audit records that are present in the files to database tables. You can find the unified audit records that are present in the OS spillover files by querying the V\$UNIFIED_AUDIT_TRAIL dynamic view.

    For example, if you want to run this procedure for audit records in the HR_PDB container, then you must connect to that PDB first:

        SQL> CONNECT sec_admin@HR_PDB
        Enter password: password

        SQL> EXEC DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES;

        PL/SQL procedure successfully completed.
6.  Query the UNIFIED_AUDIT_TRAIL data dictionary view to check if the records transferred correctly.
    Oracle highly recommends that you query UNIFIED_AUDIT_TRAIL. After a successful audit record transfer, you should query the UNIFIED_AUDIT_TRAIL because querying the V\$UNIFIED_AUDIT_TRAIL dynamic view will show the audit records that are present only in the OS spillover files.

**Parent topic:** Transfer Unified Audit Records After the Upgrade

### About Recovery Catalog Upgrade After Upgrading Oracle Database

If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.

**See Also:**

- [Maintaining RMAN Backups and Repository Records](../bradv/maintaining-rman-backups.md)
- [Upgrading the Recovery Catalog](../bradv/managing-recovery-catalog.md)
- [My Oracle Support RMAN Compatibility Matrix (Doc ID 73431.1)](https://support.oracle.com/rs?type=doc&id=73431.1)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Enabling Disabled Release Update Bug Fixes in the Upgraded Database

Because bug fixes in Release Updates that can cause execution plan changes are disabled, Oracle recommends that you enable the disabled bug fixes that you want to use.

After you upgrade your database, the bug fix patches that can cause execution plan changes included in the Release Updates are installed disabled by default. These bug fixes will not be activated until you enable the fixes. You can either enable these fixes manually, with `PFILE` or `ALTER SYSTEM` commands, or you can use the `DBMS_OPTIM_BUNDLE` package. Starting with AutoUpgrade 19.12, the `DBMS_OPTIM_BUNDLE` package includes 58 standard fixes. You can now add additional fixes using `DBMS_OPTIM_BUNDLE`. If you add fixes, then the fixes that you add are run in addition to the default fixes.

Oracle strongly recommends that you enable these disabled patches that you want to use in your production system, and run complete workload performance tests using these patches as part of your upgrade test plan.

For more information about using `DBMS_OPTIM_BUNDLE` to enable patches that were disabled because they can change execution plans, see Oracle Database PL/SQL Packages and Types Reference, and My Oracle Support note 2147007.1.

**Related Topics**

- [DBMS_OPTIM_BUNDLE](../arpls/dbms_optim_bundle.md)
- [My Oracle Support Doc ID 2147007.1 Managing "installed but disabled" bug fixes in Database Release Updates using DBMS_OPTIM_BUNDLE](https://support.oracle.com/rs?type=doc&id=2147007.1)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### About Testing the Upgraded Production Oracle Database

Repeat tests on your production database that you carried out on your test database to ensure applications operate as expected.

If you upgraded a test database to the new Oracle Database release, and then tested it, then you can now repeat those tests on the production database that you upgraded to the new Oracle Database release. Compare the results, noting anomalies. Repeat the test upgrade as many times as necessary.

To verify that your applications operate properly with a new Oracle Database release, test the newly upgraded production database with your existing applications. You also can test enhanced functions by adding available Oracle Database features, and then testing them. However, first ensure that the applications operate in the same manner as they did before the upgrade.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Upgrading the Time Zone File Version After Upgrading Oracle Database

If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use any of the supported methods to upgrade the time zone file.

**Note:**

By default, if time zone files need to be updated, then AutoUpgrade typically performs this task for you. However, if you explicitly disable the time zone file upgrade in your AutoUpgrade configuration file, then you should perform this task either as part of your upgrade plan, or at a later point in time.

**Related Topics**

- [Datetime Data Types and Time Zone Support](../nlspg/datetime-data-types-and-time-zone-support.md)
- [My Oracle Support Doc ID 1585343.1](https://support.oracle.com/rs?type=doc&id=1585343.1)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database
