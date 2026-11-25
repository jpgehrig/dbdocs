Lists the various database tools you can use to perform common database administration tasks.

Oracle recommends you use tools listed in the "Preferred Tool" column of the table. After choosing a tool to perform a task, go to Preferred Database Tools from the Start Menu, for instructions on how to start the tool.

**Note:**

The `VOLSIZE` parameter for the Export and Import utilities is not supported on Windows. If you attempt to use the utilities with the `VOLSIZE` parameter, then error `LRM-00101` occurs. For example:

    D:\> exp system full=y volsize=100m;
    Password: password
    LRM-00101: unknown parameter name 'volsize'
    EXP-00019: failed to process parameters, type 'EXP HELP=Y' for help
    EXP-00000: Export terminated unsuccessfully

Table 2-1 Preferred Database Tools

| Administration Task                                                                                 | Preferred Tool                             | Other Tools                         |
|:----------------------------------------------------------------------------------------------------|:-------------------------------------------|:------------------------------------|
| Create database services                                                                            | Database Configuration Assistant           | ORADIM                              |
| Delete database services                                                                            | Database Configuration Assistant           | ORADIM                              |
| Change passwords in the database password file                                                      | ORAPWD                                     | ORADIM                              |
| Update the password of an Oracle Home User                                                          | Oracle Home User Control                   | None                                |
| Migrate database users to a directory                                                               | User Migration Utility                     | None                                |
| Migrate a database                                                                                  | Oracle Database Upgrade Assistant          | Upgrade Information Tool            |
| Export data                                                                                         | Data Pump Export (EXPDP)                   | Export (EXP)                        |
| Import data                                                                                         | Data Pump Import (IMPDP)                   | Import (IMP)                        |
| Load data                                                                                           | Oracle Enterprise Manager Load Wizard      | SQL\*Loader (SQLLDR)                |
| Back up database                                                                                    | Oracle Enterprise Manager Backup Wizard    | Recovery Manager (RMAN)<br>OCOPY    |
| Recover database                                                                                    | Oracle Enterprise Manager Recovery Wizard  | Recovery Manager (RMAN)<br>OCOPY    |
| Store encrypted and decrypted Oracle Wallet (Oracle Advanced Security and security PKI integration) | Oracle Wallet Manager                      | None                                |
| Grant database roles                                                                                | Oracle Enterprise Manager Database Express | Local Users and Groups<br>SQL\*Plus |
| Create database objects                                                                             | Oracle Enterprise Manager Cloud Control    | SQL\*Plus                           |

- ORADIM can set a password only when none was previously set. If a password has been previously set, then ORADIM can change it only by deleting and re-creating Oracle Database services. Now, ORADIM creates the Oracle Database service, Oracle VSS Writer service, and Oracle Scheduler service to run under the Oracle Home User account. If this account is a Local or a Domain User Account, then ORADIM prompts for the password for that account and accepts the same through `stdin`.

  It is possible to specify both the Oracle Home User and its password using the `-RUNAS osusr[/ospass]` option to `oradim`. If the given `osusr` is different from the Oracle Home User, then the Oracle Home User is used instead of `osusr` along with the given `ospass`.

- User Migration Utility can migrate local or external users to enterprise users.

  For more information, see "Using the User Migration Utility" in [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-the-user-migration-utility.md).

- Oracle Database 11g Release 2 (11.2), Oracle Database 12c Release 1 (12.1), and Oracle Database 12c Release 2 (12.2) are supported for Oracle Database Upgrade Assistant upgrades in Oracle Database 19c. Oracle Database Upgrade Assistant can also be used to apply patch sets.

- Data Pump Export and Data Pump Import are preferred for Oracle Database 10g Release 1 (10.1) and later data; Export and Import are preferred for earlier data.

- If you back up files while you are shutting down the database, then your backup is invalid. You cannot use an invalid backup to restore files at a later date.

- You cannot use earlier versions of Oracle Wallet Manager to manage Oracle Database 10g Release 1 (10.1) and later wallets that contain password-based credentials for authentication to Oracle Internet Directory. These credentials are placed in the wallet when an Oracle Database server is registered in Oracle Internet Directory.

  The database wallet that Oracle Database Configuration Assistant automatically generates during database registration can be used only with Oracle Database 10g Release 1 (10.1) or later. You cannot use this database wallet for earlier versions of the database, nor can you use it for Oracle Internet Directory Release 9.0.4 or earlier.

**See Also:**

- [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-the-user-migration-utility.md)

- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

- [Oracle Database Upgrade Guide](../upgrd/upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

**Parent topic:** [Choosing a Database Tool](choosing-a-database-tool.md)
