Review and complete these required tasks that are specified for your environment after you complete your upgrade.

You must complete these postupgrade tasks after you upgrade Oracle Database.

**Note:**

This list of required tasks is based on the assumption that you have used AutoUpgrade to perform the upgrade. AutoUpgrade completes automatically many tasks that otherwise you are required to perform manually.

- Setting Environment Variables on Linux and Unix Systems After Manual Upgrades
  Check that required operating system environment variables point to the directories of the new Oracle Database release.
- Check PL/SQL Packages and Dependent Procedures
  It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which can affect applications.
- Upgrading Statistics Tables Created by the DBMS_STATS Package After Upgrading Oracle Database
  If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.
- Configuring the FTP and HTTP Ports and HTTP Authentication for Oracle XML DB
  Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later releases. Upgrades use digest authentication.
- Install Oracle Text Supplied Knowledge Bases After Upgrading Oracle Database
  After an Oracle Database upgrade, all user extensions to the Oracle Text supplied knowledge bases must be regenerated.
- Replace the DEMO Directory in Read-Only Oracle Homes
  After upgrading Read-Only Oracle homes, make a copy of the earlier release Oracle Database `demo` directory, and replace the `demo` directory in the Read-Only Oracle home with the new release `demo` directory.
- Configure Access Control Lists (ACLs) to External Network Services
  Oracle Database 12c and later releases include fine-grained access control to the `UTL_TCP`, `UTL_SMTP`, `UTL_MAIL`, `UTL_HTTP`, or `UTL_INADDR` packages.
- Enabling Oracle Database Vault After Upgrading Oracle Database
  Depending on your target database release, you can be required to disable Oracle Database Vault to complete an Oracle Database upgrade.
- Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior
  Connections to Oracle Database from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks.md)

### Setting Environment Variables on Linux and Unix Systems After Manual Upgrades

Check that required operating system environment variables point to the directories of the new Oracle Database release.

Typically, operating system environment variables are set in profiles and shell scripts. Confirm that the following Oracle user environment variables point to the directories of the new Oracle home:

- `ORACLE_HOME`

- `PATH`

Look for other environment variables that refer to the earlier release Oracle home, such as `LD_LIBRARY_PATH`. In general, you should replace all occurrences of the old Oracle home in your environment variables with the new Oracle home paths.

**Related Topics**

- [Step 2: Ensure That the Required Environment Variables Are Set](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** Required Tasks to Complete After Upgrading Oracle Database

### Check PL/SQL Packages and Dependent Procedures

It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which can affect applications.

After the upgrade, if you use AutoUpgrade, review the AutoUpgrade report on invalid objects. If you use a replay upgrade, then check to ensure that any packages that you may have used in your own scripts, or that you call from your scripts, are available in the new release. Testing procedures dependent on packages should be part of your upgrade plan.

Code in database applications can reference objects in the connected database. For example, Oracle Call Interface (OCI) and precompiler applications can submit anonymous PL/SQL blocks. Triggers in Oracle Forms applications can reference a schema object. Such applications are dependent on the schema objects they reference. Dependency management techniques vary, depending on the development environment. Oracle Database does not automatically track application dependencies.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-schema-objects.md)

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

### Replace the DEMO Directory in Read-Only Oracle Homes

After upgrading Read-Only Oracle homes, make a copy of the earlier release Oracle Database `demo` directory, and replace the `demo` directory in the Read-Only Oracle home with the new release `demo` directory.

Oracle Database 18c and later releases contain a product demonstration directory in the file path `Oracle_home``/rdbms/demo`. These directories include examples and product demonstrations that are specific to the options and features for each Oracle Database release, some of which you can add to after upgrade by installing Oracle Database Examples. In your earlier release, if you downloaded and worked with the earlier release demonstration files, then you have two problems: you want to save your earlier release work for review and testing with the new release, and you want to obtain refreshes of the demonstrations that are specific to the new release.

After upgrading the Oracle home, and downloading and doing any other work you want to do with the new demonstration files, you can then refresh your old demonstration files.

Example 4-1 Copying the Earlier Release Demo Directory and Refreshing the Demonstrations in the Read-Only Oracle Home

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

Table 4-1 Common Oracle Database Vault Upgrade Scenarios and Upgrade Preparation Tasks

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
