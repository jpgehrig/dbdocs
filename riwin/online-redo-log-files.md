## About Online Redo Log Files

Each database instance must have at least two online redo log files. The online redo log files for a database instance are called the redo thread.

Each Oracle RAC database instance has its own redo thread to avoid contention for a single set of online redo log files. In case of instance failure, the online redo log files must be accessible by the surviving instances. Therefore, the online redo log files for an Oracle RAC database must be placed on shared storage or Oracle ASM. If you use a file system for storage, then the file system must be a shared or cluster file system.

The file names of the redo log files that are created with the preconfigured database configuration option vary by storage type.

**See Also:**

- [Oracle Database Concepts](../cncpt/physical-storage-structures.md) for more information about the online redo log files

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-storage-in-oracle-rac.md) for more information about storage for online redo log files

**Parent topic:** [Database Components Created Using Database Configuration Assistant](database-components-created-using-dbca.md)
