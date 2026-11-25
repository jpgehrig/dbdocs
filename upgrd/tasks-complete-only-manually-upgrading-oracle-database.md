## Tasks to Complete Only After Manually Upgrading Oracle Database

After you complete your upgrade, you must perform the tasks described here if you upgrade your database manually instead of using DBUA.

- Changing Passwords for Oracle Supplied Accounts
  Oracle recommends that you carry out these tasks to protect new Oracle user accounts.
- Migrating Your Initialization Parameter File to a Server Parameter File
  If you are currently using a traditional initialization parameter file, then use this procedure to migrate to a server parameter file.
- Identifying and Copying Oracle Text Files to a New Oracle Home
  To upgrade Oracle Text, use this procedure to identify and copy required files from your existing Oracle home to the new release Oracle home. Complete this task after you upgrade Oracle Database.
- Upgrading the Oracle Clusterware Configuration
  If you are using Oracle Clusterware, then you must upgrade the Oracle Clusterware keys for the database.
- Adjust the Initialization Parameter File for the New Release
  Review these topics to help you to check your initialization parameters after upgrading.
- Set CLUSTER_DATABASE Initialization Parameter For Oracle RAC After Upgrade
  For manual upgrades of Oracle RAC database instances, you must change the CLUSTER_DATABASE initialization parameter to rejoin the node to the new release cluster.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)

### Changing Passwords for Oracle Supplied Accounts

Oracle recommends that you carry out these tasks to protect new Oracle user accounts.

Depending on the release from which you upgraded, there may be new Oracle user accounts on your database. Oracle recommends that you lock all Oracle supplied accounts except for `SYS` and `SYSTEM`, and expire their passwords, so that new passwords are required when the accounts are unlocked.

**Note:**

If the default Oracle Database 12c security settings are in place, then passwords must be at least eight characters, and passwords such as `welcome` and `oracle` are not allowed.

**See Also:**

[Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md) about password requirements

You can view the status of all accounts by issuing the following SQL statement:

    SQL> SELECT username, account_status
             FROM dba_users
             ORDER BY username;

To lock and expire passwords, issue the following SQL statement:

    SQL> ALTER USER username PASSWORD EXPIRE ACCOUNT LOCK;

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database

### Migrating Your Initialization Parameter File to a Server Parameter File

If you are currently using a traditional initialization parameter file, then use this procedure to migrate to a server parameter file.

1.  If the initialization parameter file is located on a client computer, then transfer the file from the client computer to the server computer.

2.  Create a server parameter file using the `CREATE SPFILE` statement. This statement reads the initialization parameter file to create a server parameter file. You are not required to start the database to issue a `CREATE SPFILE` statement.

3.  Start up the instance using the newly-created server parameter file.

**Note:**

If you are using Oracle Real Application Clusters (Oracle RAC), then you must combine all of your instance-specific initialization parameter files into a single initialization parameter file. Complete the procedures necessary for using a server parameter file with cluster databases.

**Related Topics**

- [Overview of Initialization Parameter Files in Oracle RAC](../racad/administering-database-instances-and-cluster-databases.md)

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database

### Identifying and Copying Oracle Text Files to a New Oracle Home

To upgrade Oracle Text, use this procedure to identify and copy required files from your existing Oracle home to the new release Oracle home. Complete this task after you upgrade Oracle Database.

Certain Oracle Text features rely on files under the Oracle home that you have configured. After manually upgrading to a new Oracle Database release, or after any process that changes the Oracle home, you must identify and move these files manually. These files include user filters, mail filter configuration files, and all knowledge base extension files. After you identify the files, copy the files from your existing Oracle home to the new Oracle home.

To identify and copy required files from your existing Oracle home to the new release Oracle home:

1.  Log in with the `SYS,` `SYSTEM,` or `CTXSYS` system privileges for the upgraded database.
2.  Under the Oracle home of the upgraded database, run the `$ORACLE_HOME/ctx/admin/ctx_oh_files.sql` SQL script.
    For example:

        sqlplus / as sysdba
        connected
        SQL> @?/ctx/admin/ctx_oh_files
3.  Review the output of the `ctx_oh_files.sql` command, and copy the files to the new Oracle home.

**Related Topics**

- [Oracle Text Application Developer's Guide](../ccapp/migrating-oracle-text-applications.md)

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database

### Upgrading the Oracle Clusterware Configuration

If you are using Oracle Clusterware, then you must upgrade the Oracle Clusterware keys for the database.

Run `srvctl` for Oracle Database 12c to upgrade the database. For example:

    ORACLE_HOME/bin/srvctl upgrade database -db name -o ORACLE_HOME

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md)

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database

### Adjust the Initialization Parameter File for the New Release

Review these topics to help you to check your initialization parameters after upgrading.

Each release of Oracle Database introduces new initialization parameters, deprecates some initialization parameters, and desupports some initialization parameters. You must adjust the parameter file to account for these changes, and to take advantage of new initialization parameters that can be beneficial to your system. Additionally, when you perform a manual upgrade without using DBUA, the `tnsnames.ora` file is not automatically populated with new configuration information and settings. Therefore, you must manually update `tnsnames.ora` and adjust `local_listener` and `remote_listener` parameter references if these must be resolved.

- Setting the COMPATIBLE Initialization Parameter After Upgrade
  After testing, you can set the COMPATIBLE initialization parameter to the compatibility level you want for your new database.
- Adjust TNSNAMES.ORA and LISTENER Parameters After Upgrade
  After performing a manual upgrade, if you must resolve `local_listener` and `remote_listener` in `tnsnames.ora`, then you must manually adjust those parameters.

**See Also:**

- [Oracle Database Reference](../refrn/index.md) “Changes In this Release” section for a list of new initialization parameters, and for information about each parameter

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database

#### Setting the COMPATIBLE Initialization Parameter After Upgrade

After testing, you can set the COMPATIBLE initialization parameter to the compatibility level you want for your new database.

The COMPATIBLE initialization parameter controls the compatibility level of your database. Set the COMPATIBLE initialization parameter to a higher value only when you are certain that you no longer need the ability to downgrade your database.

1.  Perform a backup of your database before you raise the COMPATIBLE initialization parameter (optional).

    Raising the COMPATIBLE initialization parameter can cause your database to become incompatible with earlier releases of Oracle Database. A backup ensures that you can return to the earlier release if necessary.

2.  If you are using a server parameter file, then complete the following steps:

    1.  To set or change the value of the COMPATIBLE initialization parameter, update the server parameter file.

        For example, to set the COMPATIBLE initialization parameter to `12.2.0`, enter the following statement:

            SQL> ALTER SYSTEM SET COMPATIBLE = '12.2.0' SCOPE=SPFILE;

    2.  Shut down and restart the instance.

3.  If you are using an initialization parameter file, then complete the following steps:

    1.  If an instance is running, then shut it down.

        For example:

            SQL> SHUTDOWN IMMEDIATE

    2.  To set or change the value of the COMPATIBLE initialization parameter, you edit the initialization parameter file.

        For example, to set the COMPATIBLE initialization parameter to `for Oracle Database release 12.2`, enter the following in the initialization parameter file:

            COMPATIBLE = 12.2.0

    3.  Start the instance using `STARTUP`.

**Note:**

If you are using an ASM disk group, then the disk group compatibility attribute must be equal to or less than the value for the database compatibility parameter in `init.ora`.

**See Also:**

[Oracle Database Backup and Recovery User's Guide](../bradv/backing-up-database.md) for more information about performing a backup

**Parent topic:** Adjust the Initialization Parameter File for the New Release

#### Adjust TNSNAMES.ORA and LISTENER Parameters After Upgrade

After performing a manual upgrade, if you must resolve `local_listener` and `remote_listener` in `tnsnames.ora`, then you must manually adjust those parameters.

Oracle's automated upgrade utilities perform changes to network naming and listeners during automatic upgrades. However, during a manual upgrade, neither `tnsnames.ora` nor the listeners are changed.

**Related Topics**

- [Configuring the tnsnames.ora File After Installation](../netag/configuring-naming-methods.md)

**Parent topic:** Adjust the Initialization Parameter File for the New Release

### Set CLUSTER_DATABASE Initialization Parameter For Oracle RAC After Upgrade

For manual upgrades of Oracle RAC database instances, you must change the CLUSTER_DATABASE initialization parameter to rejoin the node to the new release cluster.

In upgrades of cluster member nodes, you set the `CLUSTER_DATABASE` initialization parameter to `false` before upgrading a cluster database.

After you complete the upgrade, you must set this parameter to `true`, so that you can rejoin the node to the new release cluster.

**Note:**

If you carry out your upgrade using Database Upgrade Assistant (DBUA), then DBUA performs this task for you.

**Parent topic:** Tasks to Complete Only After Manually Upgrading Oracle Database
