## Supported Storage Options for Oracle Grid Infrastructure and Oracle RAC

Both Oracle Clusterware and the Oracle RAC database use files that must be available to all the nodes in the cluster. The following table shows the storage options supported for storing Oracle Clusterware and Oracle RAC files.

Table 6-1 Supported Storage Options for Oracle Clusterware and Oracle RAC Files and Home Directories

| Storage Option                                                                                                                                              | OCR and Voting Files | Oracle Grid Infrastructure Home | Oracle RAC Home | Oracle RAC Database Files                            | Oracle Recovery Files                                |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------|:--------------------------------|:----------------|:-----------------------------------------------------|:-----------------------------------------------------|
| Oracle Automatic Storage Management (Oracle ASM)                                                                                                            | Yes                  | No                              | No              | Yes                                                  | Yes                                                  |
| Oracle Automatic Storage Management Cluster File System (Oracle ACFS)                                                                                       | No                   | No                              | Yes             | Yes (Oracle Database 12c Release 12.1.0.2 and later) | Yes (Oracle Database 12c Release 12.1.0.2 and later) |
| Direct NFS Client access to a certified network attached storage (NAS) filer<br>Note: NFS or Direct NFS Client cannot be used for Oracle Clusterware files. | No                   | No                              | No              | Yes                                                  | Yes                                                  |
| Direct-attached storage (DAS)                                                                                                                               | No                   | No                              | Yes             | Yes                                                  | Yes                                                  |
| Shared disk partitions (raw devices)                                                                                                                        | No                   | No                              | No              | No                                                   | No                                                   |
| Local file system (NTFS formatted disk)                                                                                                                     | No                   | Yes                             | Yes             | No                                                   | No                                                   |

### Guidelines for Storage Options

Use the following guidelines when choosing storage options:

- You can choose any combination of the supported storage options for each file type provided that you satisfy all requirements listed for the chosen storage options.

- You can only use Oracle ASM to store Oracle Clusterware files.

- Direct use of raw or block devices is not supported. You can only use raw or block devices with Oracle ASM.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

**Parent topic:** [Configuring Shared Storage for Oracle Database and Grid Infrastructure](configuring-storage-for-oracle-database-and-grid-infrastructure.md)
