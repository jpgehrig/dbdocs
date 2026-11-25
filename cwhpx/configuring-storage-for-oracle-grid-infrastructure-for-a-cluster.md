Complete these procedures to configure Oracle Automatic Storage Management (Oracle ASM) for Oracle Grid Infrastructure for a cluster.

Oracle Grid Infrastructure for a cluster provides system support for Oracle Database. Oracle ASM is a volume manager and a file system for Oracle database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations. Oracle Automatic Storage Management also supports a general purpose file system for your application needs, including Oracle Database binaries. Oracle Automatic Storage Management is Oracle's recommended storage management solution. It provides an alternative to conventional volume managers and file systems.

**Note:**

Oracle ASM and shared file system are the supported storage management solutions for Oracle Cluster Registry (OCR) and Oracle Clusterware voting files. The OCR is a file that contains the configuration information and status of the cluster. The installer automatically initializes the OCR during the Oracle Clusterware installation. Database Configuration Assistant uses the OCR for storing the configurations for the cluster databases that it creates.

- [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
  Identify storage requirements and Oracle ASM disk group options.
- [Using Disk Groups with Oracle Database Files on Oracle ASM](using-disk-groups-with-oracle-database-files-on-oracle-asm.md)
  Review this information to configure Oracle Automatic Storage Management (Oracle ASM) storage for Oracle Clusterware and Oracle Database Files.
- [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
  Complete these procedures to use file system storage for Oracle Database.
- [Creating and Using Oracle ASM Credentials File](creating-and-using-oracle-asm-credentials-file.md)
  Review this information to create an Oracle ASM credentials file.
