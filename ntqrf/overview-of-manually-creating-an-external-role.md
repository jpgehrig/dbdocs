Describes how to grant Oracle Database roles to users directly through Windows (known as external roles).

When you use Windows to authenticate users, Windows local groups can grant these users external roles.

All privileges for these roles are active when the user connects. When using external roles, all roles are granted and managed through the operating system. You cannot use both external roles and Oracle Database roles at the same time.

Consider the following example. With external roles enabled, you log on to a Windows domain with domain user name `sales\jones` (`sales` is the domain name and `jones` is the domain user name). You then connect to Oracle Database as Oracle Database user `smith`. In this case, you receive the roles granted to `sales\jones` but not the roles granted to `smith`.

The procedure for manually creating an external role is divided into two sets of authorization tasks performed on different computers:

- [Performing External Role Authorization Tasks on the Oracle Database Server](performing-external-role-authorization-tasks-on-the-oracle-database-server.md)
  Learn how to perform external role authorization tasks on the Oracle Database server.
- [Performing External Role Authorization Tasks on the Client Computer](performing-external-role-authorization-tasks-on-the-oracle-client-computer.md)
  Learn how to perform external role authorization tasks on the client computer.

**Parent topic:** [Overview of Manually Administering External Users and Roles](overview-of-manually-administering-external-users-and-roles.md)
