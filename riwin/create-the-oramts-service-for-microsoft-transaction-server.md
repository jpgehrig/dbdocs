## Create the OraMTS Service for Microsoft Transaction Server

To enable client components to use Oracle databases as resource managers in Microsoft application coordinated transactions, create the Oracle Service for Microsoft Transaction Server (OraMTS).

OraMTS acts as a proxy for the Oracle database to the Microsoft Distributed Transaction Coordinator (MSDTC). As a result, OraMTS provides client-side connection pooling and allows client components that leverage Oracle to participate in promotable and distributed transactions. In addition, OraMTS can operate with Oracle databases running on any operating system, given that the services themselves are run on Windows.

On releases earlier than Oracle Database 12c, the OraMTS service was created as part of a software-only installation. Starting with Oracle Database 12c, you must use a configuration tool to create this service.

To create the OraMTS service after performing a software-only installation of Oracle RAC or after adding a node to an existing cluster, perform the following steps:

1.  Open a command window.
2.  Change directories to `%ORACLE_HOME%\bin`.
3.  Run the `OraMTSCtl` utility to create the OraMTS Service, where host_name is a list of nodes on which you want to create the service:
        C:\..bin> oramtsctl.exe -new -host host_name

**See Also:**

[Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/install.md) for more information about installing OraMTS

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
