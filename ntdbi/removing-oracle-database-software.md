## 10 Removing Oracle Database Software

These topics describe how to remove Oracle software and configuration files.

Use the `deinstall` command that is included in Oracle homes to remove Oracle software. Oracle does not support the removal of individual products or components.

**Caution:**

If you have a standalone database on a node in a cluster and you have multiple databases with the same global database name (GDN), then you cannot use the deinstallation tool to remove one database only.

- [About Oracle Deinstallation Options](about-oracle-deinstallation-options.md)
  The `deinstall.bat` command stops Oracle software, and removes Oracle software and configuration files on the operating system.
- [Files Deleted by the deinstall Command](files-deleted-by-deinstallation-tool.md)
  The `deinstall` command removes Oracle software and files from your system.
- [Deinstallation Examples for Oracle Database](deinstallation-examples-for-oracle-database.md)
  Use these examples to help you understand how to run the `deinstall` command.

**See Also:**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows x64 (64-Bit)](../cwwin/removing-oracle-clusterware-and-oracle-asm-software.md)

- [Oracle Real Application Clusters Installation Guide for Microsoft Windows x64 (64-Bit)](../riwin/removing-oracle-rac-software.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md)
