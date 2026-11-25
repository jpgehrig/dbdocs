## Supported Storage Options for Oracle Grid Infrastructure

The following table shows the storage options supported for Oracle Grid Infrastructure binaries and files:

**Note:**

Oracle ASM Filter Driver (ASMFD) is deprecated on both Linux and Oracle Solaris beginning with Oracle Database 19c. It will be desupported in a future release.

On Linux systems running kernel 5.14 or higher (including Oracle Linux, RedHat Enterprise Linux, and SUSE Linux Enterprise Server), ASMFD filtering is already disabled and will not be supported going forward. Oracle recommends moving to ASMlib v3 for those environments, as it provides equivalent functionality. For details, see My Oracle Support Note Document 2806979.1. Migration steps are available. On Oracle Solaris, ASMFD is deprecated, but remains fully supported. No immediate action is required until a formal desupport notice is issued.

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

Table 7-1 Supported Storage Options for Oracle Grid Infrastructure

| Storage Option                                                                                                                                     | OCR and Voting Files | Oracle Clusterware Binaries | Oracle RAC Database Binaries | Oracle RAC Database Data Files                         | Oracle RAC Database Recovery Files                                                                                                       |
|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------|:----------------------------|:-----------------------------|:-------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Automatic Storage Management (Oracle ASM)<br>Note: Loopback devices are not supported for use with Oracle ASM                               | Yes                  | No                          | No                           | Yes                                                    | Yes                                                                                                                                      |
| Oracle Automatic Storage Management Cluster File System (Oracle ACFS)                                                                              | No                   | No                          | Yes                          | Yes for Oracle Database 12c Release 1 (12.1) and later | Yes for Oracle Database 12c Release 1 (12.1) and later                                                                                   |
| Local file system                                                                                                                                  | No                   | Yes                         | Yes                          | No                                                     | No                                                                                                                                       |
| OCFS2                                                                                                                                              | No                   | No                          | Yes                          | Yes                                                    | Yes                                                                                                                                      |
| NVMe over Fabrics (NVMe-oF) storage devices                                                                                                        | No                   | No                          | Yes                          | Yes                                                    | Yes<br>Note: In the Oracle Grid Infrastructure 19c release, NVMe-oF uses the kernel initiator, which exposes the disks as block devices. |
| Network file system (NFS) on a certified network-attached storage (NAS) filer<br>Note: Direct NFS Client does not support Oracle Clusterware files | Yes                  | Yes                         | Yes                          | Yes                                                    | Yes                                                                                                                                      |
| Direct-attached storage (DAS)                                                                                                                      | No                   | No                          | Yes                          | Yes                                                    | Yes                                                                                                                                      |
| Shared disk partitions (block devices or raw devices)                                                                                              | No                   | No                          | No                           | No                                                     | No                                                                                                                                       |

### Guidelines for Storage Options

Use the following guidelines when choosing storage options:

- You can choose any combination of the supported storage options for each file type provided that you satisfy all requirements listed for the chosen storage options.

- You can use Oracle ASM or shared file system to store Oracle Clusterware files.

- Direct use of raw or block devices is not supported.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
