## 7 Removing Oracle Database Software

These topics describe how to remove Oracle software and configuration files.

Use the `deinstall` command that is included in Oracle homes to remove Oracle software. Oracle does not support the removal of individual products or components.

**Caution:**

If you have a standalone database on a node in a cluster, and if you have multiple databases with the same global database name (GDN), then you cannot use the `deinstall` command to remove one database only.

- [About Oracle Deinstallation Options](about-oracle-deinstallation-options.md)
  You can stop and remove Oracle Database software and components in an Oracle Database home with the `deinstall` command.
- [Identifying All Instances On a Cluster](identifying-all-instances-on-a-cluster.md)
  Review this information to identify all instances associated with the Oracle home you want to remove.
- [Oracle Deinstallation (Deinstall)](oracle-deinstallation-tool-deinstall.md)
  You can run the `deinstall` command from an Oracle home directory after installation.
- [Deinstallation Examples for Oracle Database](deinstallation-examples-for-oracle-database.md)
  Use these examples to help you understand how to run the `deinstall` command.
- [Deinstallation Parameter File Example for Oracle RAC](deinstallation-parameter-file-example-for-oracle-rac.md)
  You can run the `deinstall` command on Oracle RAC Databases with the `-paramfile` option to use the values you specify in the parameter file.
