Oracle Database supports the use of Oracle Home User, specified at the time of Oracle Database installation. Oracle Home User is used to run the Windows services for the Oracle home.

Oracle Home User can be a Windows Built-in Account or a Virtual Account or a standard Windows User Account (not an Administrator account). Oracle Home User cannot be changed post installation.

If a Windows Built-in Account is used, then no user name or password is required during installation and administration. However, if a Windows User Account is used as Oracle Home User, then you must provide the user name and password during installation and some of the administration tasks.

Virtual Accounts allow you to install an Oracle Database and, create and manage Database services without passwords. A Virtual Account can be used as the Oracle Home User for Oracle Database Single Instance installations and does not require a user name or password during installation and administration.

Oracle Home User is different from Oracle Installation User. Oracle Installation User is the user, who installs a given Oracle Home and hence requires administrative privileges. Oracle Home User is used to run the Windows services. You must not log into the Windows system as Oracle Home User to perform administrative tasks.

Note that the Windows administrator privilege is still required to perform Oracle administrative functions such as installation, upgrade, patching, and other functions.

**Note:**

A Windows User Account used as Oracle Home User cannot have the administrator privileges as it causes the Oracle Universal Installer to display an error message.

- [Managing Oracle Home User](managing-oracle-home-user.md)
  If you use a Windows User Account as the Oracle Home User, then you must ensure that this user account is present in the Windows system and its password is managed securely to ensure the proper operation and security of the database.
- [Using Oracle Home User for an Oracle Database and Oracle Database Client](using-oracle-home-user-for-oracle-single-instance-database-and-oracle-database-client.md)
  For a single-instance Oracle Database and Oracle Database Client installations, you can use Built-in Account or a Windows User Account as the Oracle Home User. Single-instance Oracle Database installations may also use a Virtual Account.
- [Using Oracle Home User for Multiple Oracle Homes](using-oracle-home-user-in-case-of-multiple-oracle-home.md)
  Different Oracle homes on a system can use the same Oracle Home User or use different Oracle Home User names. Note that the earlier releases (11.2 and earlier) of Oracle Database are treated equivalent to using the Windows Built-in Account as the Oracle Home User.
- [Using Oracle Home User During Oracle Database Upgrade](using-oracle-home-user-during-oracle-database-upgrade.md)
  You can use Oracle Database Upgrade Assistant to upgrade or move databases across Oracle homes if both the Oracle homes use the same Windows User Account as Oracle Home User, or at least one of the Oracle homes is configured to use Windows built-in account as the Oracle Home User.
- [Converting from Single-Instance Oracle Database to Oracle Real Application Clusters](converting-from-single-instance-oracle-database-to-oracle-real-application-clusters.md)
  You can convert from Oracle Database 19c single-instance databases to Oracle RAC using Oracle Database Configuration Assistant, `rconfig`, or Oracle Enterprise Manager.

**See Also:**

- Microsoft documentation for more information on different types of Windows user accounts

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/install-oracle-database.md)
