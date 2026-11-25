Describes how to enable Windows to grant the database administrator (`SYSDBA`), database operator (`SYSOPER`), database administrator for ASM (`SYSASM`), and new task-specific and less privileged than the `ORA_DBA`/`SYSDBA` system privileges to administrators.

With these privileges, the administrator can issue the following commands from a client computer and connect to Oracle Database without entering a password:

    SQL> CONNECT / AS SYSOPER
    SQL> CONNECT / AS SYSDBA
    SQL> CONNECT / AS SYSASM
    SQL> CONNECT / AS SYSBACKUP
    SQL> CONNECT / AS SYSDG
    SQL> CONNECT / AS SYSKM

To enable this feature, a Windows local or a domain user name of the administrator must belong to one of the Windows local groups listed in Windows Local Groups with SYSDBA, SYSOPER, SYSASM, SYSDG, SYSBACKUP, and SYSKM Privileges.

Table 11-1 Windows Local Groups with SYSDBA, SYSOPER, SYSASM, SYSDG, SYSBACKUP, and SYSKM Privileges

| Local Group                  | System Privileges                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------|
| `ORA_OPER`                   | `SYSOPER` privileges for all databases on a computer                                                                  |
| `ORA_DBA` Note               | `SYSDBA` privileges for all databases on a computer                                                                   |
| `ORA_``SID``_OPER`           | `SYSOPER` privileges for a single database (identified by `SID`)                                                      |
| `ORA_``SID``_DBA`            | `SYSDBA` privileges for a single database (identified by `SID`)                                                       |
| `ORA_``HOMENAME``_DBA`       | `SYSDBA` privileges for all database instances of the specified Oracle home.                                          |
| `ORA_``HOMENAME``_OPER`      | `SYSOPER` privileges for starting up and shutting down all databases instances that run from a specified Oracle home. |
| `ORA_``HOMENAME``_SYSDG`     | `SYSDG` privilege for all database instances that run from the particular Oracle home                                 |
| `ORA_``HOMENAME``_SYSBACKUP` | `SYSBACKUP` privilege for all database instances that run from the particular Oracle home                             |
| `ORA_``HOMENAME``_SYSKM`     | `SYSKM` privilege for all database instances that run from the particular Oracle home                                 |
| `ORA_ASMADMIN`               | `SYSASM` privileges for all ASM instances on a computer                                                               |
| `ORA_ASMDBA`                 | `SYSDBA` privileges for all ASM instances on a computer                                                               |
| `ORA_ASMOPER`                | `SYSOPER` privileges for all ASM instances on a computer                                                              |

### Note

All the groups mentioned in the table above are automatically created during installation and the Oracle Home User is automatically added to `ORA_``HOMENAME``_DBA` group. See section "[Overview of Operating System Authentication Enabled at Installation](overview-of-operating-system-authentication-enabled-at-installation.md)" for information.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md)

The manual procedure for enabling administrators to connect as `SYSOPER`, `SYSDBA`, `SYSASM`, `SYSDG`, `SYSKM`, or `SYSBACKUP` without a password is divided into two sets of tasks performed on different computers:

- [Running System Privilege Authentication Tasks on the Oracle Database Server](running-system-privilege-authentication-tasks-on-the-database-server.md)
  Learn about running system privilege authentication tasks on the Oracle Database server.
- [Running System Privilege Authentication Tasks on the Client Computer](running-system-privilege-authentication-tasks-on-the-client-computer.md)
  Learn about running system privilege authentication tasks on the client computer.

**Parent topic:** [Overview of Manually Administering External Users and Roles](overview-of-manually-administering-external-users-and-roles.md)
