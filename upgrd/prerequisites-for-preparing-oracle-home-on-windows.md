## Prerequisites for Preparing Oracle Home on Windows

Your system must meet these requirements before you can upgrade Oracle Database on Microsoft Windows platforms.

For security reasons, different Microsoft Windows user accounts configured as Oracle home users for different Oracle homes are not allowed to share the same Oracle Base.

- Database upgrade is supported when the same Windows user account is used as the Oracle home user in both the source and destination Oracle homes.

- Database upgrade is supported when the Oracle home from which the database is being upgraded uses the Windows Built-in Account. Releases earlier than Oracle Database 12c (release 11.2 and earlier) only supported the built-in account option for the Oracle home user on Windows.

- The Oracle home user may not have access to files outside its own Oracle Base and Oracle home. If that is the case, then if you choose a different Oracle Base during upgrade, it is possible that Oracle Database services cannot access files in the older Oracle Base. Using DBUA for database upgrade ensures that the Oracle home user has access to files outside of its own Oracle Base and its own Oracle home.

  Before upgrading manually, or before using the custom files from the older Oracle Base (for example, wallets, configuration files and other custom files ), you must grant access to the Oracle home user for these outside files, or copy these files to the new Oracle Base.

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/administering-database-on-windows.md) for information about database administration on Windows

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
