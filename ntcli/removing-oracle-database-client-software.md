## 5 Removing Oracle Database Client Software

Learn how to remove Oracle software and configuration files.

You can remove Oracle software either by using Oracle Universal Installer with the `deinstall` option, or by using the deinstallation tool (`deinstall`) that is included in Oracle homes. Oracle does not support the removal of individual products or components related to the specified Oracle home. It includes information about removing Oracle software using the deinstallation tool.

The deinstallation tool removes standalone Oracle Database installations, Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM) from your server, as well as Oracle Real Application Clusters (Oracle RAC) and Oracle Database client installations.

Oracle recommends that you use the deinstallation tool to remove the entire Oracle home associated with the Oracle Database, Oracle Clusterware, Oracle ASM, Oracle RAC, or Oracle Database client installation. Oracle does not support the removal of individual products or components.

**Caution:**

If you have a standalone database on a node in a cluster and you have multiple databases with the same global database name (GDN), then you cannot use the deinstallation tool to remove one database only.

**Caution:**

You must use the deinstallation tool from the same release to remove Oracle software. Do not run the deinstallation tool from a later release to remove Oracle software from an earlier release. For example, do not run the deinstallation tool from the 12.2.0.1 installation media to remove Oracle software from an existing 11.2.0.4 Oracle home.

- [About Oracle Deinstallation Options](about-oracle-deinstallation-options.md)
  You can stop and remove Oracle Database software and components in an Oracle Database home with Oracle Universal Installer.
- [Deinstallation Examples for Oracle Database Client](deinstallation-examples-for-oracle-database-client.md)
  Use these examples to learn how to run deinstallation using a standalone tool (`deinstall`).
- [Example of Running the Deinstallation Tool](example-of-running-the-deinstallation-tool.md)
  Review the examples to help you understand how to run the deinstallation tool.
- [Deinstallation Response File Example for Oracle Database Client](deinstallation-response-file-example-for-oracle-database-client.md)
  You can run the deinstallation tool with the `-paramfile` option to use the values you specify in the response file.
