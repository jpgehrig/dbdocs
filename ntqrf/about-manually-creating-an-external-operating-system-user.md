Describes how to authenticate external operating system users (not database administrators) using Windows, so that a password is not required when accessing the database.

When you use Windows to authenticate external operating system users, your database relies solely on the operating system to restrict access to database user names.

Note that if a Windows Local User is used as the Oracle Home User for an Oracle home, then external user authentication of the Windows Local users is only supported from the same computer. Oracle recommends using Windows Domain User or Windows built-in user as the Oracle Home User to support external authentication of the Windows Domain User from the same computer or a different computer.

In the following procedure, two Windows user names are authenticated:

- Local user `jones`

- Domain user `jones` on domain `sales`

Local user `jones` logs into its local Windows client computer to access an Oracle Database server, which can be on a different computer. To access other databases and resources on other computers, the local user must provide a user name and password each time.

Domain user `jones` on domain `sales` logs into a `sales` domain that includes many other Windows computers and resources, one of which contains an Oracle Database server. The domain user can access all the resources the domain provides with a single user name and password.

- [Performing External User Authentication Tasks on the Oracle Database Server](performing-external-user-authentication-tasks-on-the-oracle-database-server.md)
  Use this procedure to perform external user authentication tasks.
- [Performing External User Authentication Tasks on the Client Computer](performing-external-user-authentication-tasks-on-the-oracle-client-computer.md)
  Use this procedure to perform external user authentication tasks on the client computer.

**Parent topic:** [Overview of Manually Administering External Users and Roles](overview-of-manually-administering-external-users-and-roles.md)
