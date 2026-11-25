Learn how to configure your system to store data files for a tablespace on raw partitions.

**Note:**

Oracle RAC requires additional configuration tools.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/glossary.md) for information about creating logical partitions and assigning symbolic links. Do not use this appendix to create partitions for Oracle RAC.

- [Raw Partition Overview](raw-partition-overview.md)
  Data files for tablespaces can be stored on a file system or on raw partitions. A raw partition is a portion of a physical disk that is accessed at the lowest possible level.
- [Configuring Disks for Oracle Automatic Storage Management](configuring-disks-for-oracle-automatic-storage-management.md)
  To use Oracle Automatic Storage Management with direct attached storage (DAS) or storage area network (SAN) storage, the disks must be stamped with a header by `asmtool` or `asmtoolg` (GUI version).
