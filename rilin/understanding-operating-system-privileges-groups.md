## Understanding Operating System Privileges Groups

Review this information for system privileges required for Oracle Database or Oracle Automatic Storage Management (Oracle ASM) administration.

As an administrator, you often perform special operations such as shutting down or starting up a database, or configuring storage. Because only an administrator responsible for these administration decisions must perform these operations, system privileges for Oracle Database or Oracle Automatic Storage Management (Oracle ASM) administration require a secure authentication scheme.

Membership in special operating system groups enables administrators to authenticate to Oracle Database or Oracle ASM through the operating system rather than with a user name and password. This is known as operating system authentication. Each Oracle Database in a cluster can have its own operating system privileges groups, so that operating system authentication can be separated for each Oracle Database on a cluster. Because there can be only one Oracle Grid Infrastructure installation on a cluster, there can be only one set of operating system privileges groups for Oracle ASM.

During installation of Oracle Grid Infrastructure and Oracle Database, you provide the group names of operating system groups. These operating system groups are designated with the logical role of granting operating system group authentication for administration system privilege for Oracle Database and Oracle ASM.

In an Oracle RAC cluster, the group ID number (GID) for system privileges groups must be identical on each cluster member node. One operating system group can be designated the logical group whose members are granted all system privileges for Oracle Database and Oracle ASM, including the `OINSTALL` system privileges for installation owners. You can also delegate logical system privileges to two or more actual operating system groups. Oracle recommends that you designate separate operating system groups for each logical system privilege. This enables you to grant one or more subsets of administrator system privileges to database administrators. These database administrators can then perform standard database administration tasks without requiring the `SYSDBA` system privileges.

System privileges groups are listed in the following table:

Table 6-1 Role-Allocated Oracle System Privileges Operating System Groups

| Logical Operating System Group Name | Default Actual UNIX or Linux Group Name | System Privileges Authenticated By Group Membership                                                                                                                                                                    |
|:------------------------------------|:----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OINSTALL                            | `oinstall`                              | Install system privileges for installation owners, which includes privileges to write to the central `oraInventory` directory for each server, and other privileges granted to Oracle binary installation owner users. |
| OSDBA                               | `dba`                                   | `SYSDBA` system privileges for an Oracle Database, which includes all system privileges for the database.                                                                                                              |
| OSOPER                              | `oper`                                  | `SYSOPER` startup and shutdown system privileges for an Oracle Database.                                                                                                                                               |
| OSBACKUPDBA                         | `backupdba`                             | `SYSBACKUP` backup and recovery system privileges for an Oracle Database.                                                                                                                                              |
| OSDGDBA                             | `dgdba`                                 | `SYSDG` system privileges to administer and monitor Oracle Data Guard.                                                                                                                                                 |
| OSKMDBA                             | `kmdba`                                 | `SYSKM` system privileges for encryption key management for applications such as Oracle Wallet Manager.                                                                                                                |
| OSASM                               | `asmadmin`                              | `SYSASM` system privileges for Oracle ASM on a cluster, which includes all system privileges for Oracle ASM storage.                                                                                                   |
| OSOPER for ASM                      | `asmoper`                               | `SYSOPER` startup and shutdown system privileges for Oracle ASM on the cluster.                                                                                                                                        |
| OSDBA for ASM                       | `asmdba`                                | `SYSDBA` for ASM system privileges to obtain read and write access to files managed by Oracle ASM. All Oracle Database software owners must be a member of this group.                                                 |
| OSRACDBA                            | `racdba`                                | `SYSRAC` privileges to perform day to day administration of Oracle databases on an Oracle RAC cluster. All Oracle Database software owners must be a member of this group.                                             |

**See Also:**

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md) for more information about operating system groups and Oracle Database system privileges

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md) for more information about operating system groups and Oracle ASM system privileges

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
