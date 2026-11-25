If you use a Windows User Account as the Oracle Home User, then you must ensure that this user account is present in the Windows system and its password is managed securely to ensure the proper operation and security of the database.

You must secure the password of this Windows User Account and ensure that only database administrators have access to this password as one can log on to the database as the database administrator from this Windows User Account. You must also change the password for this Windows User Account at regular intervals for security reasons. You can change the password using Windows tools. However, when you change the password for this Windows User Account, you must also update the password for all Oracle services running under the Windows User Account.

This release has introduced a new Windows utility called the Oracle Home User Control. This is a command-line tool that displays the Oracle Home User name associated with the current Oracle home and updates the password for all Oracle services running under a specific Windows User Account (used as Oracle Home User).

**Related Topics**

- [Using the Oracle Home User Control Tool](using-the-oracle-home-user-control-tool.md)

**Parent topic:** [Supporting Oracle Home User on Windows](supporting-oracle-home-user-on-windows.md)
