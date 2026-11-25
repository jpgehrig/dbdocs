When an earlier version of the database is upgraded to Oracle Database 19c, Oracle Database Upgrade Assistant installs software in the following directories, where `database_name` is the database name or `SID`.

When an earlier version of the database is upgraded to Oracle Database 19c, Oracle Database Upgrade Assistant installs software in the following directories, where `database_name` is the database name or `SID`:

- `ORACLE_BASE``\admin\``database_name` (administration files)

- `ORACLE_BASE``\oradata\``database_name` (database file directories)

- `ORACLE_BASE``\oradata\``database_name` (redo log files and control files)

- `ORACLE_BASE``\``ORACLE_HOME``\database` (`SPFILE``SID``.ORA`)

Oracle Database Upgrade Assistant sets the following permissions to these directories, and to all files and directories under these directories:

- Full control `Administrators`, `SYSTEM`, Oracle Home User or `ORA_<HomeName>_SVCACCTS` group for Virtual Account homes

  **Note:**

  If these accounts already exist and have more restrictive permissions, then the most restrictive permissions are retained. If accounts other than `Administrators`, `SYSTEM`, and Oracle Home User already exist, then the permissions for these accounts are removed.

Oracle Database Upgrade Assistant can also configure Oracle Enterprise Manager. If the Enable daily backup option is selected while configuring Oracle Enterprise Manager, then Oracle Database Upgrade Assistant shows a separate screen asking for Fast Recovery Area. Oracle Database Upgrade Assistant tries to create the directory structure (if it does not exist) in the specified file system location. Oracle Database Upgrade Assistant also puts the same set of file permissions to this location. The default location shown by Oracle Database Upgrade Assistant for Fast Recovery Area is:

- `ORACLE_BASE``\recovery_area`

**Parent topic:** [Setting File Permissions](about-setting-file-system-acls-manually.md)
