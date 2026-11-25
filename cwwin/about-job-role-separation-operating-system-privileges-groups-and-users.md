## About Job Role Separation Operating System Privileges Groups and Users

Job role separation requires that you create different operating system groups for each set of system privileges that you grant through operating system authorization.

With Oracle Grid Infrastructure job role separation, Oracle ASM has separate operating system groups that provide operating system authentication for Oracle ASM system privileges for storage tier administration. This operating system authentication is separated from Oracle Database operating system authentication. In addition, the Oracle Grid Infrastructure Installation user provides operating system user authentication for modifications to Oracle Grid Infrastructure binaries.

With Oracle Database job role separation, each Oracle Database installation has separate operating system groups. The operating system groups provide authorization for system privileges on that Oracle Database, so multiple databases can be installed on the cluster without sharing operating system authentication for system privileges. In addition, each Oracle software installation is associated with an Oracle Installation user, to provide operating system user authorization for modifications to Oracle Database binaries.

**Note:**

Any Oracle software owner can start and stop all databases and shared Oracle Grid Infrastructure resources such as Oracle ASM or Virtual IP (VIP). Job role separation configuration enables database security, and does not restrict user roles in starting and stopping various Oracle Clusterware resources.

During the Oracle Database installation, the installation creates the OSDBA, OSOPER, OSBACKUPDBA, OSDGDBA, OSKMDBA, and OSRACDBA groups and you can assign users to these groups. Members of these groups are granted operating system authentication for the set of database system privileges each group authorizes. Oracle recommends that you use different operating system groups for each set of system privileges.

**Note:**

This configuration is optional, to restrict user access to Oracle software by responsibility areas for different administrator users.

To configure users for installation that are on a network directory service such as Network Information Services (NIS), refer to your directory service documentation.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md)

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
