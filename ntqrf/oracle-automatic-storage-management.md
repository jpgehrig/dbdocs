Oracle Automatic Storage Management (Oracle ASM) is an integrated file system and volume manager expressly built for Oracle Database files.

Oracle ASM provides the performance of raw I/O with the easy management of a file system. It simplifies database administration by eliminating the need for you to directly manage potentially thousands of Oracle Database files. It enables you to divide all available storage into disk groups. You manage a small set of disk groups, and Oracle ASM automates the placement of the database files within those disk groups.

Oracle recommends that you use Oracle ASM instead of raw files to store data files. It provides the performance benefits of raw files with much better manageability. Oracle ASM is available for both single instance and Oracle Real Application Clusters (Oracle RAC) databases.

You can store Oracle Cluster Registry and voting files in Oracle ASM disk groups and store database data files in the `data` disk group. The voting files and Oracle Cluster Registry are two important components of Oracle Clusterware.

**Note:**

- You must be logged on either as an Administrator or a user name that is a member of the Administrators group.

- To open Disk Management console, click Start, Run, and then enter: `diskmgmt.msc`.

- Storing data files on raw devices is no longer supported. You must use a file system or Oracle Automatic Storage Management.

- NFS or Direct NFS cannot be used for Oracle Clusterware files.

**Related Topics**

- [Storing Tablespaces on Raw Partitions](storing-tablespaces-on-raw-partitions.md)

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md)

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/identifying-tablespaces-and-data-files.md)

**Parent topic:** [Overview of Oracle Database on Windows Architecture](overview-of-oracle-database-on-windows-architecture.md)
