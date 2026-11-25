## Supported Storage Options for Oracle Database

The following table shows the storage options supported for Oracle Database binaries and files:

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

Table 7-1 Supported Storage Options for Oracle Database

| Storage Option                                                                                                       | Oracle Database Binaries | Oracle Database Data Files                           | Oracle Database Recovery Files                                                                                    |
|:---------------------------------------------------------------------------------------------------------------------|:-------------------------|:-----------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| Oracle Automatic Storage Management (Oracle ASM)<br>Note: Loopback devices are not supported for use with Oracle ASM | No                       | Yes                                                  | Yes                                                                                                               |
| Oracle Automatic Storage Management Cluster File System (Oracle ACFS)                                                | Yes                      | Yes (Oracle Database 12c Release 1 (12.1) and later) | Yes (Oracle Database 12c Release 1 (12.1) and later                                                               |
| Local file system                                                                                                    | Yes                      | Yes, but not recommended                             | Yes, but not recommended                                                                                          |
| NVMe over Fabrics (NVMe-oF) storage devices                                                                          | Yes                      | Yes                                                  | Yes<br>Note: In Oracle Database 19c, NVMe-oF uses the kernel initiator, which exposes the disks as block devices. |
| Network file system (NFS) on a certified network-attached storage (NAS) filer                                        | Yes                      | Yes                                                  | Yes                                                                                                               |
| Oracle Memory Speed                                                                                                  | No                       | Yes                                                  | Yes                                                                                                               |

### Guidelines for Storage Options

Use the following guidelines when choosing storage options:

- Oracle strongly recommends that you use a dedicated set of disks for Oracle ASM.

- You can choose any combination of the supported storage options for each file type provided that you satisfy all requirements listed for the chosen storage options.

- You can use Oracle ASM to store Oracle Clusterware files.

- Direct use of raw or block devices is not supported.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
