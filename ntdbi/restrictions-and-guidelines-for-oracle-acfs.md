## Restrictions and Guidelines for Oracle ACFS

Review these guidelines and restrictions as part of your storage plan for using Oracle ACFS for single instance and cluster configurations.

- Oracle Automatic Storage Management Cluster File System (Oracle ACFS) provides a general purpose file system.

- You can only use Oracle ACFS when Oracle ASM is configured.

- You must use a domain user when installing Oracle Grid Infrastructure if you plan to use Oracle ACFS.

- When creating Oracle ACFS file systems on Windows, log on as a Windows domain user. Also, when creating files in an Oracle ACFS file system on Windows, you should be logged in as a Windows domain user to ensure that the files are accessible by all nodes.

  When using a file system across cluster nodes, the best practice is to mount the file system using a domain user, to ensure that the security identifier is the same across cluster nodes. Windows security identifiers, which are used in defining access rights to files and directories, use information which identifies the user. Local users are only known in the context of the local node. Oracle ACFS uses this information during the first file system mount to set the default access rights to the file system.

Note the following general guidelines and restrictions for placing Oracle Database and Oracle Grid Infrastructure files on Oracle ACFS:

- Starting with Oracle Grid Infrastructure 12c Release 1 (12.1) for a cluster, you can place Oracle Database binaries, data files, and administrative files (for example, trace files) on Oracle ACFS.

- Oracle ACFS does not support encryption or replication with Oracle Database data files, tablespace files, control files, redo logs, archive logs, RMAN backups, Data Pump dumpsets, and flashback files

- You can place Oracle Database homes on Oracle ACFS only if the database release is Oracle Database 11g release 2 or later. You cannot install earlier releases of Oracle Database on Oracle ACFS.

- For installations of Oracle Clusterware, you cannot place Oracle Clusterware files on Oracle ACFS.

- For policy-managed Oracle Flex Cluster databases, Oracle ACFS can run on any cluster node.

The following restrictions apply if you run Oracle ACFS in an Oracle Restart configuration:

- Starting with Oracle Database 18c, configuration assistants do not allow the creation of Oracle Database homes on Oracle ACFS in an Oracle Restart configuration.

- Oracle Restart does not support Oracle ACFS resources on all platforms.

- Starting with Oracle Database 12c, Oracle Restart configurations do not support the Oracle ACFS registry.

- You must manually load Oracle ACFS drivers after a system restart.

- You must manually mount an Oracle ACFS file system, and unmount it after the Oracle ASM instance has finished running.

- Creating Oracle data files on an Oracle ACFS file system is not supported in Oracle Restart configurations. Creating Oracle data files on an Oracle ACFS file system is supported on Oracle Grid Infrastructure for a cluster configurations.

**Parent topic:** [Oracle ACFS and Oracle ADVM](oracle-acfs-and-oracle-advm.md)
