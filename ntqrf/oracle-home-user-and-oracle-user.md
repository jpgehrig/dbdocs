On Linux and UNIX systems, you must create and use a software owner user account (`oracle`), and this user must belong to the Oracle Inventory group (`oinstall`) and also must be a member of the appropriate OSDBA, OSOPER, OSBACKUPDBA, OSDGDBA, and OSKMDBA groups.

On Windows, you use an existing Windows User Account or create a new standard Windows User Account (not an administrator account) as the Oracle Home User. The various Oracle services on Windows run with the privileges of the Oracle Home User. This user is automatically added to various groups as required.

**Related Topics**

- [Supporting Oracle Home User on Windows](supporting-oracle-home-user-on-windows.md)

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
