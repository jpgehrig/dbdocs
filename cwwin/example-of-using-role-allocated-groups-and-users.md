## Example of Using Role-Allocated Groups and Users

You can use role-allocated groups and users that is compliant with an Optimal Flexible Architecture (OFA) deployment.

Assumptions:

- The user installing the Oracle Grid Infrastructure software is named `RACDOMAIN\grid`. This user was created before starting the installation.

  The option to use the Windows Built-in Account was selected for the Oracle Home user for Oracle Grid Infrastructure.

- The name of the home directory for the Oracle Grid Infrastructure installation is `OraGrid19c`.

- The user installing the Oracle RAC software is named `oracle`. This user was created before starting the installation.

  During installation of Oracle RAC, an Oracle Home user named `RACDOMAIN\oradba1` is specified. The `oradba1` user is a Windows domain user that was created before the installation was started.

  The name of the Oracle home for the Oracle RAC installation is `OraRAC19c_home1`.

- You have a second, Oracle Database installation (not Oracle RAC) on this server. The installation was performed by the `oracle` user. The Oracle Home user is `oradba2`, and this user was not created before starting the installation.

  The Oracle Home name is `OraDB19c_home1`.

- Both the Oracle databases and Oracle Clusterware are configured to use Oracle ASM for data storage.

After installing the Oracle software, you have the following groups and users:

| Operating System Group Name                                                          | Type of Group                                                                                        | Members                                                                                                        |
|:-------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------|
| `ORA_DBA`                                                                            | OSDBA group                                                                                          | `oracle`, `RACDOMAIN\grid`, and the Local System built-in Windows account                                      |
| ` ORA_OraRAC19c_home1_DBA`                                                           | OSDBA group for the Oracle RAC home directory                                                        | `RACDOMAIN\oradba1`                                                                                            |
| `ORA_OraDB19c_home1_DBA`                                                             | OSDBA group for the Oracle Database home directory                                                   | `oradba2`                                                                                                      |
| `ORA_OPER`                                                                           | OSOPER group                                                                                         | none                                                                                                           |
| `ORA_OraRAC19c_home1_OPER`                                                           | OSOPER group for the Oracle RAC home directory                                                       | none                                                                                                           |
| `ORA_OraDB19c_home1_OPER`                                                            | OSOPER group for the Oracle Database home directory                                                  | none                                                                                                           |
| `ORA_ASMADMIN`                                                                       | OSASM group                                                                                          | `RACDOMAIN\grid` and the Local System built-in Windows account, and the database service IDs                   |
| `ORA_ASMOPER`                                                                        | OSOPER for ASM group                                                                                 | none                                                                                                           |
| `ORA_ASMDBA`                                                                         | OSDBA for ASM group for Oracle ASM clients                                                           | `RACDOMAIN\grid`, `oracle`, the Local System built-in Windows account, and Oracle Home Users of database homes |
| `ORA_RAC19c_home1_SYSBACKUP`, `ORA_RAC19c_home1_SYSDG`, and `ORA_RAC19c_home1_SYSKM` | Specialized role groups that authorize users with the SYSBACKUP, SYSDG, and SYSKM system privileges. | none                                                                                                           |
| `ORA_DB19c_home1_SYSBACKUP`, `ORA_DB19c_home1_SYSDG`, and `ORA_DB19c_home1_SYSKM`    | Specialized role groups that authorize users with the SYSBACKUP, SYSDG, and SYSKM system privileges. | none                                                                                                           |

If there are no users listed for an operating system group, then that means the group has no members after installation.

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
