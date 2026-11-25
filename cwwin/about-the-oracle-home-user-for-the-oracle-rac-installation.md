## About the Oracle Home User for the Oracle RAC Installation

The Oracle Home User for Oracle RAC can be different from the Oracle Home User you specified during the Oracle Grid Infrastructure installation.

During installation of Oracle RAC, you can either use a Windows built-in account or specify an optional, non-Administrator user that is a Windows domain user or a Windows Group Managed Service Account (gMSA) to be the Oracle Home User associated with the Oracle RAC home.

If a Windows domain user account or a gMSA is chosen, then it should be an existing domain user account with no administration privileges.

For Oracle RAC installations, Oracle recommends that you use a Windows domain user or a gMSA (instead of Windows built-in account) as the Oracle Home User for enhanced security.

The services created for the Oracle RAC software run using the privileges of the Oracle Home User for Oracle RAC, or the Local System built-in Windows account if you did not specify an Oracle Home User during installation. Oracle Universal Installer (OUI) creates multiple operating system groups, such as the `ORA_DBA` group, on all nodes. The user performing the installation is automatically added to those groups necessary for proper database administration.

For an administrator-managed database, you have the option of storing Oracle Home User password in a secure wallet (stored in Oracle Cluster Registry). Use the following CRSCTL command to create this secure wallet for storing the Windows operating system user name and password:

    crsctl add wallet -osuser -passwd

If the wallet (stored in Oracle Cluster Registry) exists, then Oracle administration tools automatically use the password from the wallet without prompting the administrator to enter the password of Oracle Home User for performing administrative operations.

A policy-managed database mandates the storage of Oracle Home User password in the wallet (stored in Oracle Cluster Registry). When a policy-managed database is created, DBCA automatically creates the wallet, if one does not exist.

**Note:**

If you choose to use an Oracle Home User for your Oracle RAC installation, then the Windows User Account you specify must be a domain user or a gMSA.

**Related Topics**

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md)

**Parent topic:** [Creating Installation Groups and Users for Oracle Grid Infrastructure and Oracle RAC](creating-installation-groups-and-users-for-grid-and-rac.md)
