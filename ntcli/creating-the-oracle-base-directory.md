## Creating the Oracle Base Directory

If you install Oracle Database Client on a computer with no other Oracle software installed, Oracle Universal Installer creates an Oracle base directory for you.

If Oracle software is already installed, one or more Oracle base directories already exist. In the latter case, Oracle Universal Installer offers you a choice of Oracle Base directories into which you can install Oracle Database Client.

You are not required to create an Oracle base directory before installation, but you can do so if you want. If a Windows User Account is used as the Oracle Home User, it can only share an Oracle base with other Oracle homes with the same Windows user account. If Windows Built-in Account is specified as the Oracle Home User, it can only share an Oracle base with other client Oracle homes using a Windows Built-in Account.

Oracle Database Client 19c cannot share an Oracle base with Oracle homes from earlier database versions, such as Oracle Database 18c and earlier.

**Note:**

You can choose to create a new Oracle base directory, even if other Oracle base directories exist on the system.

**Parent topic:** [Installation Considerations for Oracle Database Client](installation-considerations-for-oracle-database-client.md)
