During Oracle Database configuration, Oracle Database Configuration Assistant installs files and directories in the following default locations, where `database_name` is the database name or `SID`.

- `ORACLE_BASE``\admin\``database_name` (administration file directories)

- `ORACLE_BASE``\oradata\``database_name` (database file directories)

- `ORACLE_BASE``\oradata\``database_name` (redo log files and control files)

- `ORACLE_HOME``\database` (`SPFILE``SID``.ORA`)

Oracle Database Configuration Assistant sets the following permission to these directories, and to all the files and directories under these directories:

- Full control `Administrators`, `SYSTEM`, Oracle Home User or `ORA_<HomeName>_SVCACCTS` group for Virtual Account homes

  **Note:**

  If these accounts already exist and have more restrictive permissions, then the most restrictive permissions are retained. If accounts other than `Administrators`, `SYSTEM`, and Oracle Home User already exist, then the permissions for these accounts are removed.

**Parent topic:** [Setting File Permissions](about-setting-file-system-acls-manually.md)
