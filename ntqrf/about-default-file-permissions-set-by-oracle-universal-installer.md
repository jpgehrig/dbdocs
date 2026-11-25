During Oracle Database installation, by default Oracle Universal Installer installs software in the `ORACLE_HOME` directory.

Oracle Universal Installer sets the following permissions to this directory, and to all files and directories under this directory:

### For the Oracle Grid Infrastructure home:

- Full control - `Administrators`, `SYSTEM`, `ORA_GRID_LISTENERS`, Oracle Installation User, Oracle Home User

- Read, execute, and list content - `Authenticated Users`

### For the Database ORACLE_HOME:

- Full control - `Administrators`, `SYSTEM`, Oracle Installation User, Oracle Home User, or `ORA_<HomeName>_SVCACCTS` group for Virtual Account homes.

- Read, execute, and list content - `Authenticated Users`

### For the Client ORACLE_HOME:

- Full control - `Administrators`, `SYSTEM`, Oracle Installation User, `ORA_``HOMENAME``_SVCSIDS` or the Oracle Home User

- Read, execute, and list content - `Authenticated Users`

Oracle Universal Installer sets the following permissions to the `ORACLE_BASE` directory, and to all the files and directories under this directory with the exception of database files, wallets, and so on:

- Full control - `Administrators`, `SYSTEM`, Oracle Installation User, Oracle Home User or `ORA_<HomeName>_SVCACCTS `group for Virtual Account homes.

- Full control - `ORA_GRID_LISTENERS` if the `ORACLE_BASE` is for the Oracle Grid Infrastructure `ORACLE_HOME`

- Full control - `ORA_``HOMENAME``_SVCSIDS` or Oracle Home User if the `ORACLE_BASE` is for a Client `ORACLE_HOME`

**Note:**

If these accounts already exist and have more restrictive permissions, then most restrictive permissions are retained. If accounts other than `Administrators`, `SYSTEM`, `Authenticated` `Users`, and the Oracle groups mentioned exist, then the permissions for these accounts are removed.

**See Also:**

- [Oracle Grid Infrastructure Installation Guide for Microsoft Windows x64 (64-Bit)](../cwwin/index.md)

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/operating-system-groups-created-during-oracle-database-installation.md)

**Parent topic:** [Setting File Permissions](about-setting-file-system-acls-manually.md)
