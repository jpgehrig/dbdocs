Oracle Database 19c mandates that the administrator starting all the administration tools such as Oracle Database Configuration Assistant, Oracle Database Upgrade Assistant, Oracle Net Configuration Assistant, and Oracle ASM Configuration Assistant, must be an operating system administrator.

The administrator must also be a member of the `ORA_DBA` and `ORA_ASMADMIN` group for using the Oracle Database Configuration Assistant and Oracle Database Upgrade Assistant tools when accessing Oracle ASM. The administrator must be a member of the `ORA_ASMADMIN` group for using the Oracle ASM Configuration Assistant tool.

Oracle needs the password of Oracle Home User to create new Windows services for Database, Listener, and other entities. To support this, all the administration tools have been modified to prompt for the password of Oracle Home User that is required only when the Oracle Home User is a Local or a Domain Windows User Account and the password for the Oracle Home User is not stored in the Oracle Wallet.

- [Starting Database Tools in Multiple Oracle Homes](starting-database-tools-in-multiple-oracle-homes.md)
  You can start database tools in multiple Oracle homes.
- [Running Tools with Windows User Account Control](running-tools-with-windows-user-account-control.md)
  You must ensure that only trusted applications run on your computer.
- [Starting Database Tools from the Start Menu](starting-database-tools-from-the-start-menu.md)
  Describes how to start assistants and other tools from the Start menu.
- [Starting Database Tools from the Command Line](starting-database-tools-from-the-command-line.md)
  Describes how to start Oracle Database tools from the command line, and where to go for further information on using these products.
- [Starting Windows Tools](starting-windows-tools.md)
  Describes how to start each Windows tool and where to go for more information on using these products.

**Parent topic:** [Database Tools on Windows](database-tools-on-windows.md)
