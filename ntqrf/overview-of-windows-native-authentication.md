Oracle Database can use Windows user login credentials to authenticate database users.

Benefits include:

- Enabling users to connect to Oracle Database without supplying a username or password

- Centralizing Oracle Database user authentication and role authorization information in Windows, which frees Oracle Database from storing or managing user passwords or role information

The Windows native authentication adapter (automatically installed with Oracle Net Services) enables database user authentication through Windows. This enables client computers to make secure connections to Oracle Database on a Windows server. The server then permits the user to perform database actions on the server.

**Note:**

Current user database links are not supported with Windows native authentication.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md)

- [Oracle Internet Directory Administrator's Guide](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntqrf&id=OIDAG031)

**Parent topic:** [Authenticating Database Users with Windows](authenticating-database-users-with-windows.md)
