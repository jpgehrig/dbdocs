When an Oracle Wallet is created in the file system, the user creating the wallet is granted access to the wallet by wallet creation tools.

Oracle Database Windows services may run under a standard Windows User Account or Virtual Account and might not be able to access to the wallet. You may need to change the file system ACL for the wallet file manually to grant access to database and listener services.

**Parent topic:** [Setting File Permissions](about-setting-file-system-acls-manually.md)
