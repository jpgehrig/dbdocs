## About the Oracle Home User for the Oracle Grid Infrastructure Installation

During installation of Oracle Grid Infrastructure, you can specify an optional Oracle Home user for Grid Infrastructure Management Repository configuration.

For example, assume that you use an Administrator user named `OraSys` to install the software (Oracle Installation user), then you can specify the `ORADOMAIN\OraGrid` domain user as the Oracle Home user for this installation. The specified Oracle Home domain user must exist before you install the Oracle Grid Infrastructure software.

If you specify an existing user as the Oracle Home user, then the Windows User Account you specify must be a domain user or Group Managed Service Account (gMSA) user. When you use an Oracle Home User, a secure wallet in Oracle Cluster Registry (created automatically) stores the Oracle Home User name and password information. If you decide not to create an Oracle Home user, then the Windows built-in account is used as Oracle Home User.

**Note:**

- Oracle recommends not to use the Windows built-in account (LocalSystem) as the Oracle Home user for Grid Infrastructure Management Repository configuration, as this account is less secure.
- You cannot change the Oracle Home User after the installation is complete. If you must change the Oracle Home User, then you must reinstall the Oracle Grid Infrastructure software.

If you perform a software-only installation of Oracle Grid Infrastructure, then Oracle recommends that you choose a Windows Domain User account to configure the Oracle Grid Infrastructure Management Repository after installation.

During installation, the installer creates the software services and configures the Access Control Lists (ACLs) based on the information you provided about the Oracle Home User.

When you specify an Oracle Home user, the installer configures that user as the Oracle Service user for GIMR that runs from the Grid home. The Oracle Service user is the operating system user from which the services inherit privileges.

**Related Topics**

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md)

**Parent topic:** [Creating Installation Groups and Users for Oracle Grid Infrastructure and Oracle RAC](creating-installation-groups-and-users-for-grid-and-rac.md)
