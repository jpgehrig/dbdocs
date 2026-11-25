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
- [Downgrading Oracle Restart](downgrading-oracle-restart.md)
  Use this procedure to deconfigure and downgrade Oracle Restart, or to troubleshoot Oracle Restart installation errors.
- [Removing an RPM-based Oracle Database Installation](removing-rpm-based-database-installation.md)
  Use this procedure to remove and deinstall a database installed using the `yum` command.
- [Deinstalling Previous Release Grid Home](deinstalling-previous-release-grid-home.md)
  Use this procedure to deinstall the previous release Grid home.
