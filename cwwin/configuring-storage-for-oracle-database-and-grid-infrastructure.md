## 6 Configuring Shared Storage for Oracle Database and Grid Infrastructure

Review supported storage options and perform prerequisite tasks as part of your installation planning process.

**Note:**

If you are currently using OCFS for Windows as your shared storage, then you must migrate to using Oracle ASM before the upgrade of Oracle Database and Oracle Grid Infrastructure.

- [Supported Storage Options for Oracle Grid Infrastructure and Oracle RAC](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
  Both Oracle Clusterware and the Oracle RAC database use files that must be available to all the nodes in the cluster. The following table shows the storage options supported for storing Oracle Clusterware and Oracle RAC files.
- [Oracle ACFS and Oracle ADVM](understanding-oracle-asm-cluster-file-system.md)
  Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is a multi-platform, scalable file system, and storage management technology that extends Oracle Automatic Storage Management (Oracle ASM) functionality to support all file types.
- [Storage Considerations for Oracle Grid Infrastructure and Oracle RAC](storage-considerations-for-oracle-gird-infrastructure-and-oracle-rac.md)
  For all installations, you must choose the storage option to use for Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM), and Oracle Real Application Clusters (Oracle RAC) databases.
- [Guidelines for Choosing a Shared Storage Option](guidelines-for-choosing-a-shared-storage-option.md)
  You can choose any combination of the supported shared storage options for each file type if you satisfy all requirements listed for the chosen storage option.
- [About Migrating Existing Oracle ASM Instances](about-migrating-existing-oracle-asm-instances.md)
  You can use Oracle Automatic Storage Management Configuration Assistant (ASMCA) to upgrade the existing Oracle ASM instance to Oracle ASM 12c release 1 (12.1) or higher.
- [Preliminary Shared Disk Preparation](preliminary-shared-disk-preparation.md)
  When using shared storage on a Windows platform, there are additional preinstallation tasks to complete.
- [Configuring Disk Partitions on Shared Storage](configuring-disk-partitions-on-shared-storage.md)
  Use the disk administration tools provided by the operating system or third-party vendors to create disk partitions.
