These topics describe how to remove Oracle software and configuration files.

Use the `deinstall` command that is included in Oracle homes to remove Oracle software. Oracle does not support the removal of individual products or components.

**Caution:**

If you have a standalone database on a node in a cluster, and if you have multiple databases with the same global database name (GDN), then you cannot use the `deinstall` command to remove one database only.

- [About Oracle Deinstallation Options](about-oracle-deinstallation-options.md)
  You can stop and remove Oracle Database software and components in an Oracle Database home with the `deinstall` command.
- [Oracle Deinstallation (Deinstall)](oracle-deinstallation-tool-deinstall.md)
  You can run the `deinstall` command from an Oracle home directory after installation.
- [Deinstallation Examples for Oracle Database](deinstallation-examples-for-oracle-database.md)
  Use these examples to help you understand how to run the `deinstall` command.
- [Deinstallation Response File Example for Oracle Grid Infrastructure for a Cluster](deinstallation-response-file-example-for-oracle-grid-infrastructure-for-a-cluster.md)
  You can run the `deinstall` command with the `-paramfile` option to use the values you specify in the response file.
- [Migrating Standalone Oracle Grid Infrastructure Servers to a Cluster](migrating-standalone-oracle-grid-infrastructure-servers-to-a-cluster.md)
  If you have an Oracle Database installation using Oracle Restart (that is, an Oracle Grid Infrastructure installation for a standalone server), and you want to configure that server as a cluster member node, then complete the following tasks:
- [Relinking Oracle Grid Infrastructure for a Cluster Binaries](relinking-oracle-grid-infrastructure-for-a-cluster-binaries.md)
  After installing Oracle Grid Infrastructure for a cluster (Oracle Clusterware and Oracle ASM configured for a cluster), if you need to modify the binaries, then use the following procedure, where `Grid_home` is the Oracle Grid Infrastructure for a cluster home:
- [Changing the Oracle Grid Infrastructure Home Path](changing-the-oracle-grid-infrastructure-home-path.md)
  After installing Oracle Grid Infrastructure for a cluster (Oracle Clusterware and Oracle ASM configured for a cluster), if you need to change the Grid home path, then use the following example as a guide to detach the existing Grid home, and to attach a new Grid home.
- [Unconfiguring Oracle Clusterware Without Removing Binaries](unconfiguring-oracle-clusterware-without-removing-binaries.md)
  Running the `rootcrs.sh` command flags `-deconfig -force` enables you to unconfigure Oracle Clusterware on one or more nodes without removing installed binaries.
