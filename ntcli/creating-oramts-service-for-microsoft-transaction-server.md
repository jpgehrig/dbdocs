## Creating the OraMTS Service for Microsoft Transaction Server

Oracle Services for Microsoft Transaction Server (OraMTS) permit Oracle databases to be used as resource managers in Microsoft application coordinated transactions.

OraMTS acts as a proxy for the Oracle database to the Microsoft Distributed Transaction Coordinator (MSDTC). As a result, OraMTS provides client-side connection pooling and allows client components that leverage Oracle to participate in promotable and distributed transactions. In addition, OraMTS can operate with Oracle databases running on any operating system, given that the services themselves are run on Windows.

On releases before Oracle Database 12c, the OraMTS service was created as part of a software-only installation. Now, you must use a configuration tool to create this service.

To create the OraMTS service after performing a software-only installation for Oracle Database, perform the following steps:

1.  Open a command window.
2.  Change directories to `ORACLE_HOME``\bin`.
3.  Run the `OraMTSCtl` utility to create the OraMTS Service:
        C:\ORACLE_HOME\bin> oramtsctl.exe -new

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
