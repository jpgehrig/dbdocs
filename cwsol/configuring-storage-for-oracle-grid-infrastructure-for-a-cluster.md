Complete these procedures to configure Oracle Automatic Storage Management (Oracle ASM) for Oracle Grid Infrastructure for a cluster.

Oracle Grid Infrastructure for a cluster provides system support for Oracle Database. Oracle ASM is a volume manager and a file system for Oracle database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations. Oracle Automatic Storage Management also supports a general purpose file system for your application needs, including Oracle Database binaries. Oracle Automatic Storage Management is Oracle's recommended storage management solution. It provides an alternative to conventional volume managers and file systems.

**Note:**

Oracle ASM and shared file system are the supported storage management solutions for Oracle Cluster Registry (OCR) and Oracle Clusterware voting files. The OCR is a file that contains the configuration information and status of the cluster. The installer automatically initializes the OCR during the Oracle Clusterware installation. Database Configuration Assistant uses the OCR for storing the configurations for the cluster databases that it creates.

- [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
  Identify storage requirements and Oracle ASM disk group options.
- [Configuring Storage Device Path Persistence Using Oracle ASMFD](configuring-storage-device-path-persistence-using-oracle-asmfd.md)
  Oracle ASM Filter Driver (Oracle ASMFD) maintains storage file path persistence and helps to protect files from accidental overwrites.
- [Using Disk Groups with Oracle Database Files on Oracle ASM](using-disk-groups-with-oracle-database-files-on-oracle-asm.md)
  Review this information to configure Oracle Automatic Storage Management (Oracle ASM) storage for Oracle Clusterware and Oracle Database Files.
- [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
  Complete these procedures to use file system storage for Oracle Database.
- [Creating Member Cluster Manifest File for Oracle Member Clusters](creating-member-cluster-manifest-file.md)
  Create a Member Cluster Manifest file to specify the Oracle Member Cluster configuration for the Grid Infrastructure Management Repository (GIMR), Grid Naming Service, Oracle ASM storage server, and Oracle Fleet Patching and Provisioning configuration.
- [Configuring Oracle Automatic Storage Management Cluster File System](configuring-oracle-automatic-storage-management-cluster-file-system.md)
  Review this information to configure Oracle ACFS for an Oracle RAC Oracle Database home.
