Oracle Universal Installer, Oracle Database Configuration Assistant, and Oracle Database Upgrade Assistant set file permissions when you install or upgrade Oracle Database software.

- [About Default File Permissions Set by Oracle Universal Installer](about-default-file-permissions-set-by-oracle-universal-installer.md)
  During Oracle Database installation, by default Oracle Universal Installer installs software in the `ORACLE_HOME` directory.
- [About File Permissions Set by Oracle Database Configuration Assistant](about-file-permissions-set-by-oracle-database-configuration-assistant.md)
  During Oracle Database configuration, Oracle Database Configuration Assistant installs files and directories in the following default locations, where `database_name` is the database name or `SID`.
- [About File Permissions Set by Oracle Database Upgrade Assistant](about-file-permissions-set-by-oracle-database-upgrade-assistant.md)
  When an earlier version of the database is upgraded to Oracle Database 19c, Oracle Database Upgrade Assistant installs software in the following directories, where `database_name` is the database name or `SID`.
- [About Setting Permissions for Oracle Wallets](about-setting-permissions-for-oracle-wallets.md)
  When an Oracle Wallet is created in the file system, the user creating the wallet is granted access to the wallet by wallet creation tools.
- [About Setting File System ACLs Manually](setting-file-system-acls-manually.md)
  As Oracle Database services now run under a standard Windows User Account, a file might not be accessible by Oracle Database services unless the file system Access Control Lists (ACLs) grant access to the file.

**Parent topic:** [Overview of NTFS File System and Windows Registry Permissions](overview-of-ntfs-file-system-and-windows-registry-permissions.md)
