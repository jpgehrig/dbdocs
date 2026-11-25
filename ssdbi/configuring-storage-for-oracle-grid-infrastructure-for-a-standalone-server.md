Complete these procedures to use Oracle Grid Infrastructure for a standalone server, which includes Oracle Automatic Storage Management (Oracle ASM).

Oracle Grid Infrastructure for a standalone server, also known as Oracle Restart, provides system support for a single-instance Oracle Database. Oracle ASM is a volume manager and a file system for Oracle database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations. Oracle Automatic Storage Management also supports a general purpose file system for your application needs, including Oracle Database binaries. Oracle Automatic Storage Management is Oracle's recommended storage management solution. It provides an alternative to conventional volume managers and file systems.

**Note:**

- If you want to use Oracle ASM or Oracle Restart, then you must install Oracle Grid Infrastructure for a standalone server before you install and create the database. Otherwise, you must manually register the database with Oracle Restart.

- You can neither install Oracle Restart on an Oracle Grid Infrastructure cluster member node, nor add an Oracle Restart server to an Oracle Grid Infrastructure cluster member node. Oracle Restart supports single-instance databases on one server, while Oracle Grid Infrastructure for a Cluster supports single-instance or Oracle RAC databases on a cluster.

<!-- -->

- [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
  Identify storage requirements and Oracle ASM disk group options.
- [Configuring Storage Device Path Persistence Using Oracle ASMFD](configuring-storage-device-path-persistence-using-oracle-asmfd.md)
  Oracle ASM Filter Driver (Oracle ASMFD) maintains storage file path persistence and helps to protect files from accidental overwrites.
- [Configuring Disk Devices for Oracle ASM on Oracle Solaris](configuring-disk-devices-for-oracle-asm-on-oracle-solaris.md)
  Complete these tasks to configure disk devices for use with Oracle Automatic Storage Management (Oracle ASM).
- [Creating DAS or SAN Disk Partitions for Oracle Automatic Storage Management](creating-das-or-san-disk-partitions-for-oracle-automatic-storage-management.md)
  You can use direct-attached storage (DAS) and storage area network (SAN) disks with Oracle ASM.
- [Creating Directories for Oracle Database Files](creating-directories-for-oracle-database-files.md)
  You can store Oracle Database and recovery files on a separate file system from the configuration files.
- [Creating Files on a NAS Device for Use with Oracle Automatic Storage Management](creating-files-on-a-nas-device-for-use-with-oracle-automatic-storage-management.md)
  If you have a certified NAS storage device, then you can create zero-padded files in an NFS mounted directory and use those files as disk devices in an Oracle ASM disk group.
