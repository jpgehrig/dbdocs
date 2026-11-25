As Oracle Database services now run under a standard Windows User Account, a file might not be accessible by Oracle Database services unless the file system Access Control Lists (ACLs) grant access to the file.

Though Oracle installation configures the ACLs in a way to ensure that you do not have to change ACLs manually for typical usage, it is necessary to change ACLs manually, for example, to manually upgrade databases, and database files not in Oracle base, or to grant access to wallets in the file system.

The rules to set file system ACLs manually are:

- To allow Oracle Database service access to a file: Grant access to Oracle Home User for the file when a Windows User Account is used as the Oracle Home User. If a Windows built-in account is used as the Oracle Home User, then no such permission is necessary because the Oracle Database services run under the administrative account.

- To allow Oracle Grid Listeners services access to a file: Grant access to `ORA_GRID_LISTENERS` group for the file.

- To allow Oracle services from a client `ORACLE_HOME` access to a file: Grant access to Oracle Home User for the file when a Windows User Account is used as the Oracle Home User for the client home. If a Windows built-in account is used as the Oracle Home User, then grant access to the `ORA_``HOMENAME``_SVCSIDS `group for the file.

**Parent topic:** [Setting File Permissions](about-setting-file-system-acls-manually.md)
