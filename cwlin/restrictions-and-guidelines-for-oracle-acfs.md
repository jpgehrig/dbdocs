## Restrictions and Guidelines for Oracle ACFS

Review these topics as part of your storage plan for using Oracle ACFS for single instance and cluster configurations.

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

- Oracle Automatic Storage Management Cluster File System (Oracle ACFS) provides a general purpose file system.

- You can only use Oracle ACFS when Oracle ASM is configured.

- Note the following general guidelines and restrictions for placing Oracle Database and Oracle Grid Infrastructure files on Oracle ACFS:

  - You can place Oracle Database binaries, data files, and administrative files (for example, trace files) on Oracle ACFS.

  - Oracle ACFS does not support encryption or replication with Oracle Database data files, tablespace files, control files, redo logs, archive logs, RMAN backups, Data Pump dumpsets, and flashback files.

  - You can place Oracle Database homes on Oracle ACFS only if the database release is Oracle Database 11g Release 2, or more recent releases. You cannot install earlier releases of Oracle Database on Oracle ACFS.

  - For installations on Oracle Clusterware, you cannot place Oracle Clusterware files on Oracle ACFS.

- Oracle Restart does not support root-based Oracle Clusterware resources. For this reason, the following restrictions apply if you run Oracle ACFS on an Oracle Restart Configuration:

  - Starting with Oracle Database 18c, configuration assistants do not allow the creation of Oracle Database homes on Oracle ACFS in an Oracle Restart configuration.

  - Oracle Restart does not support Oracle ACFS resources on all platforms.

  - Starting with Oracle Database 12c, Oracle Restart configurations do not support the Oracle ACFS registry.

  - On Linux, Oracle ACFS provides an automated mechanism to load and unload drivers and mount and unmount Oracle ACFS file systems on system restart and shutdown. However, Oracle ACFS does not provide automated recovery of mounted file systems when the system is running. Other than Linux, Oracle ACFS does not provide this automated mechanism on other operating systems.

  - Creating Oracle data files on an Oracle ACFS file system is not supported in Oracle Restart configurations. Creating Oracle data files on an Oracle ACFS file system is supported on Oracle Grid Infrastructure for a cluster configurations.

- Oracle ACFS and Oracle ADVM are not supported on IBM AIX Workload Partitions (WPARs).

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/acfs-advanced-topics.md)

**Parent topic:** [Oracle ACFS and Oracle ADVM](oracle-acfs-and-oracle-advm.md)
