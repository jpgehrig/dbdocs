Manually configure administrators, operators, users, and roles to be authenticated by the operating system.

Manual configuration involves using Oracle Database command-line tools, editing the registry, and creating local groups in Active Directory Users and Computers.

All of the following can be manually configured to access Oracle Database without a password:

- External operating system users

- Windows database administrators (with `SYSDBA` privilege)

- Windows database operators (with `SYSOPER` privilege)

In addition, you can manually create and grant local and external database roles to Windows domain users and global groups.

This section describes:

- [About Manually Creating an External Operating System User](about-manually-creating-an-external-operating-system-user.md)

  Describes how to authenticate external operating system users (not database administrators) using Windows, so that a password is not required when accessing the database. When you use Windows to authenticate external operating system users, your database relies solely on the operating system to restrict access to database user names.

- [Overview of Manually Granting Administrator, Operator, and Task-Specific Privileges for Databases](overview-of-manually-granting-administrator-operator-and-task-specific-privileges-for-databases.md)

  Describes how to enable Windows to grant the database administrator (`SYSDBA`), database operator (`SYSOPER`), database administrator for ASM (`SYSASM`), and new task-specific and less privileged than the `ORA_DBA/SYSDBA` system privileges to administrators.

- [Managing New Users and User Groups](managing-new-users-and-user-groups.md)

  During Oracle Database installation, `ORA_INSTALL, ORA_DBA, ORA_OPER, ORA_``HOMENAME``_DBA, ORA_``HOMENAME``_OPER, ORA_``HOMENAME``_SYSDG, ORA_``HOMENAME``_SYSBACKUP, ORA_``HOMENAME``_SYSKM, ORA_ASMADMIN, ORA_ASMDBA`, and `ORA_ASMOPER` user groups are automatically created with the required privileges.

- [Overview of Manually Creating an External Role](overview-of-manually-creating-an-external-role.md)

  Describes how to grant Oracle Database roles to users directly through Windows (known as external roles). When you use Windows to authenticate users, Windows local groups can grant these users external roles.

- [About Manually Migrating Users](about-manually-migrating-users.md)

  You can migrate local or external users to enterprise users with User Migration Utility. Migrating from a database user model to an enterprise user model provides solutions to administrative, security, and usability challenges in an enterprise environment. In an enterprise user model, all user information is moved to an LDAP directory service, which provides the following benefits:

  **Note:**

  Use extreme care when manually configuring administrators, operators, users, and roles to be authenticated by the operating system.

<!-- -->

- [About Manually Creating an External Operating System User](about-manually-creating-an-external-operating-system-user.md)
  Describes how to authenticate external operating system users (not database administrators) using Windows, so that a password is not required when accessing the database.
- [Overview of Manually Granting Administrator, Operator, and Task-Specific Privileges for Databases](overview-of-manually-granting-administrator-operator-and-task-specific-privileges-for-databases.md)
  Describes how to enable Windows to grant the database administrator (`SYSDBA`), database operator (`SYSOPER`), database administrator for ASM (`SYSASM`), and new task-specific and less privileged than the `ORA_DBA`/`SYSDBA` system privileges to administrators.
- [Managing New Users and User Groups](managing-new-users-and-user-groups.md)
  Learn how to manage new users and user groups.
- [Overview of Manually Creating an External Role](overview-of-manually-creating-an-external-role.md)
  Describes how to grant Oracle Database roles to users directly through Windows (known as external roles).
- [About Manually Migrating Users](about-manually-migrating-users.md)
  You can migrate local or external users to enterprise users with User Migration Utility.

**Parent topic:** [Administering External Users and Roles on Windows](administering-external-users-and-roles-on-windows.md)
