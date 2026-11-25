## Overview of Deinstallation Procedures

There are several tasks to perform when completely removing all Oracle databases, instances, and software from an Oracle home directory.

- Identify all instances associated with the Oracle home

- Shut down processes

- Remove listeners installed in the Oracle Database home

- Remove database instances

- Remove Oracle Automatic Storage Management (Oracle ASM) release 11.1 or earlier

- Remove Oracle Clusterware and Oracle ASM (Oracle Grid Infrastructure)

**Note:**

- For information on removing Oracle Database Vault, see [Oracle Database Vault Administrator's Guide](../dvadm/postinstallation-oracle-database-vault-procedures.md).

- For information on removing Oracle Configuration Manager, see Oracle Configuration Manager Installation and Administration Guide.

- With Oracle Grid Infrastructure 11g release 2 (11.2) and later, Oracle ASM and Oracle Clusterware comprise the Oracle Grid Infrastructure installation. These components are installed and removed together.

**Caution:**

If any cluster member node has more than one database with the same global database name (GDN) on a server, then you cannot use the deinstallation tool to remove only one database.

For example, if you have a standalone database on one of your cluster nodes with the GDN `mydb.example.com`, and your Oracle RAC database GDN is also `mydb.example.com`, then both databases on that node are removed by the deinstallation tool.

**Parent topic:** [Removing Oracle RAC Software](removing-oracle-rac-software.md)
