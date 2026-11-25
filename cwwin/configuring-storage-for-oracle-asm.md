## 7 Configuring Storage for Oracle Automatic Storage Management

Identify storage requirements and Oracle Automatic Storage Management (Oracle ASM) disk group options.

When configuring disks for use with Oracle ASM, you can use the `asmtool` utility to mark the disks prior to installation.

- [Identifying Storage Requirements for Using Oracle ASM for Shared Storage](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  Before installing Oracle Grid Infrastructure, you must identify and determine how many devices are available for use by Oracle ASM, the amount of free disk space available on each disk, and the redundancy level to use with Oracle ASM.
- [Oracle Clusterware Storage Space Requirements](oracle-clusterware-storage-requirements.md)
  Use this information to determine the minimum number of disks and the minimum disk space requirements based on the redundancy type, for installing Oracle Clusterware files, and installing the starter database, for various Oracle Cluster deployments.
- [About the Grid Infrastructure Management Repository](about-grid-insfrastructure-management-repository.md)
  The Grid Infrastructure Management Repository (GIMR) is a multitenant database with a pluggable database (PDB) for the GIMR of each cluster.
- [Restrictions for Disk Partitions Used By Oracle ASM](restrictions-for-disk-partitions-used-by-oracle-asm.md)
  Be aware of the following restrictions when configuring disk partitions for use with Oracle ASM:
- [Preparing Your System to Use Oracle ASM for Shared Storage](preparing-your-system-to-use-oracle-asm-for-shared-storage.md)
  To use Oracle ASM as the shared storage solution for Oracle Clusterware or Oracle RAC files, you must perform certain tasks before you begin the software installation.
- [Marking Disk Partitions for Oracle ASM Before Installation](configuring-marking-disk-partitions-for-asm.md)
  The only partitions that OUI displays for Windows systems are logical drives that are on disks and have been marked (or stamped) with `asmtoolg` or by Oracle Automatic Storage Management (Oracle ASM) Filter Driver.
- [Configuring Oracle Automatic Storage Management Cluster File System](configuring-oracle-automatic-storage-management-cluster-file-system.md)
  If you want to install Oracle RAC on Oracle ACFS, you must first create the Oracle home directory in Oracle ACFS.
