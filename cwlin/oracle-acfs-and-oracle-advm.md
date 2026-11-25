## Oracle ACFS and Oracle ADVM

Oracle Automatic Storage Management Cluster File System (Oracle ACFS) extends Oracle ASM technology to support of all of your application data in both single instance and cluster configurations.

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

To align the support for the IBM AIX platform, Oracle Automatic Storage Management Cluster File System (ACFS) on IBM AIX (called Oracle Advanced Cluster File System starting with Oracle Database 21c) is deprecated in Oracle Database 19c. For data or files currently stored on an ACFS file system that cannot be stored in the Oracle database, the IBM General Parallel File System (GPFS) can be used.

Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM) provides volume management services and a standard disk device driver interface to clients. Oracle ACFS communicates with Oracle ASM through the Oracle ADVM interface.

- [Oracle ACFS and Oracle ADVM Support on Linux x86–64](oracle-acfs-and-oracle-advm-support-on-linux.md)
  Oracle ACFS and Oracle ADVM are supported on Oracle Linux, Red Hat Enterprise Linux, and SUSE Linux Enterprise Server.
- [Restrictions and Guidelines for Oracle ACFS](restrictions-and-guidelines-for-oracle-acfs.md)
  Review these topics as part of your storage plan for using Oracle ACFS for single instance and cluster configurations.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/index.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
