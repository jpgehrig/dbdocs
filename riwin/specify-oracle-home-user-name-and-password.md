## Specify Oracle Home User Name and Password

To provide enhanced security for your Oracle Database software, you can select to use an Oracle Home User.

An Oracle Home User is a standard Windows User Account (not an Administrator account), specified during installation, that runs the Windows services required by Oracle Database for the Oracle home.

The Oracle Home User is associated with an Oracle Home and it cannot be changed post installation. Different Oracle Homes on a system can share the same Oracle Home User or use different Oracle Home User names. For Oracle RAC databases, the Windows user account for the Oracle Home must be a domain account and it has to be an existing account.

For Administrator-managed databases, you can store the password for the Oracle Home User in a secure wallet in the Oracle Cluster Registry (OCR). If such a wallet exists in the OCR, then Oracle Database administration tools automatically use the password from the wallet and do not require you to enter the password for the Oracle Home User during administrative operations.

For Policy-managed databases, you must store the password for the Oracle Home User in a secure wallet in the OCR. Oracle Database Configuration Assistant automatically creates the wallet (if one does not exist) when a Policy-managed database is created.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows](../cwwin/creating-installation-groups-and-users-for-grid-and-rac.md)
- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/access-to-oracle-wallets-in-a-file-system-for-oracle-database-services.md)

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node](installing-oracle-rac-and-oracle-rac-one-node.md)
