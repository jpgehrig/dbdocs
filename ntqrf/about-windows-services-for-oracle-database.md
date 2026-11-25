ORADIM creates Oracle Database service, Oracle VSS Writer service, and Oracle Scheduler service to run under the Oracle Home User account.

Oracle Home User is the standard Windows User Account (not an Administrator), specified during installation, that runs most of the Windows services required by Oracle for Oracle home.

If this Oracle Home User is a Windows Local User Account or a Windows Domain User Account, then ORADIM prompts for a password for that account and accepts the same through `stdin`.

All Oracle administration tools that create Windows services have been modified to prompt for the password of Oracle Home User when the Oracle Home User is a Windows Local User Account or a Windows Domain User Account, and the password for Oracle Home User is not stored in the Oracle Wallet.

- [About Running Windows Services in Oracle Home](about-running-windows-services-in-oracle-home.md)
  Depending on the type of database installation and user account used as the Oracle Home User, Windows services run under low-privileged, non-administrative accounts such as a LocalService, or an authenticated Windows User Account, or as a high-privileged Local System Account (LSA) in Oracle home.
- [Additional Privileges Required by Oracle Database Services](additonal-privileges-required-by-oracle-database-services.md)
  Certain functions performed by the Oracle Database service require additional privileges.
- [Granting Additional Operating System Privileges Manually](granting-additional-operating-system-privileges-manually.md)
  To grant an operating system privilege to a specific user, perform the following steps:

**Related Topics**

- [About Creating and Starting an Oracle Database Service](about-creating-and-starting-an-oracle-database-service.md)
- [About Ways to Manage Oracle Database Services](about-ways-to-manage-oracle-database-services.md)

**Parent topic:** [Running Windows Services](running-windows-services.md)
