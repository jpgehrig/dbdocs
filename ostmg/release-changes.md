This chapter describes changes in Oracle Automatic Storage Management Administrator's Guide.

- Changes in Oracle Automatic Storage Management 19c

- Changes in Oracle ACFS and Oracle ADVM in Oracle ASM 19c

- Changes in Oracle Automatic Storage Management 18c

- Changes in Oracle ACFS and Oracle ADVM in Oracle ASM 18c

**See Also:**

- [Oracle Database Licensing Information User Manual](../dblic/index.md) to determine whether a feature is available on your edition of Oracle Database

- [Oracle Database New Features Guide](../newft/index.md) for a complete description of the new features in this release

- [Oracle Database Upgrade Guide](../upgrd/index.md) for a complete description of the deprecated and desupported features in this release

### Changes in Oracle Automatic Storage Management 19c

The following are changes in Oracle Automatic Storage Management 19c.

- New Features

- Deprecated Features

- Desupported Features

#### New Features

These are the new features for Oracle Automatic Storage Management 19c.

- SRVCTL command enhancements

  SRVCTL provides enhanced commands to manage Oracle ASM network resources.

  **See Also:**

  - [About Administering Oracle ASM Instances with Server Control Utility](admin-asm-instance.md) for a summary of Oracle ASM and Oracle ACFS tasks that can be performed with SRVCTL

  - [SRVCTL and CRSCTL Commands to Administer Oracle Flex ASM](manage-flex-asm.md) for information about SRVCTL commands to manage Oracle Flex ASM resources

  - [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md) and [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for information about SRVCTL commands

- Flushing the password file metadata

  After a change has been made to the location of the password file, the following SQL statement should be run to flush the password file metadata cache:

      SQL> ALTER SYSTEM FLUSH PASSWORDFILE_METADATA_CACHE

  Changes to the location of the password file could be introduced by running `orapwd`, or the ASMCMD `pwcopy`, `pwcreate`, `pwdelete`, `pwmove`, or `pwset` command. If the `V$PASSWORDFILE_INFO` does not display the correct password file location after a change, then flush the password file metadata cache to force a refresh of the password file location.

  **See Also:**

  - [Managing a Shared Password File in a Disk Group](authenticate-access-asm-instance.md) for information about managing a password file in a disk group.

  - [ASMCMD Instance Management Commands](asmcmd-instance-commands.md) for information about the ASMCMD commands for managing the password file.

- New and updated ASMCMD commands

  - The `password` option with the ASMCMD `pwcreate` command is now optional.

    New options have been added for to force a delete of the old password file and create a new password file (`—f`) and to specify the format of the password file (`——format`).

  - The new ASMCMD `setsparseparent` command sets the parent for a sparse child file.

  - The new ASMCMD `mvfile` command moves a file to the specified file group in the same disk group where the file is stored.

  **See Also:**

  - [pwcreate](asmcmd-instance-commands.md)

  - [setsparseparent](asmcmd-diskgroup-commands.md)

  - [mvfile](asmcmd-filegroup-commands.md)

- Support for Parity Protected Files

  The `REDUNDANCY` file type property specifies the redundancy for a file group. The `PARITY` value specifies single parity and the `DOUBLE` value specifies double parity. Parity settings are intended for write-once files, such as archive logs and backup sets.

  **See Also:**

  - [About Oracle ASM File Group Properties](asm-filegroups.md) for information about the Oracle ASM file group `REDUNDANCY` property

#### Deprecated Features

These are the deprecated features for Oracle ASM 19c.

- Deprecation of the `password` option with the ASMCMD `pwcreate` command

  **See Also:**

  - [pwcreate](asmcmd-instance-commands.md)

  - [Oracle Database Upgrade Guide](../upgrd/index.md)

#### Desupported Features

These are the desupported features for Oracle ASM 19c.

- Starting with Oracle Database 19c, leaf nodes are desupported as part of Oracle Flex Cluster architecture.

  **See Also:**

  - [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

### Changes in Oracle ACFS and Oracle ADVM in Oracle ASM 19c

The following are changes to Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and Oracle ASM Dynamic Volume Manager (Oracle ADVM) in Oracle Automatic Storage Management release 19c.

- New Features

- Deprecated Features

#### New Features

These are new features for Oracle ACFS 19c.

- Enhancements for Oracle ACFS `acfsutil` commands and views, providing more detailed output for diagnosis and analysis.

  Enhancements to Oracle ACFS `acfsutil` commands and views include:

  - Display open Oracle ACFS files at any given time using the `acfsutil` `info` `ftrace` command

  - Display lock contention statistics for cluster wide diagnostics using the `acfsutil` `lockstats` command

  - Perform a faster scan on relevant metadata only, rather than the entire collection, using the `acfsutil` `meta` command with the `—g` option

  - Display information for diagnosing Oracle ACFS metadata using the `acfsutil` `info` `file` command with the `—m` option

  - Shrinking an Oracle ACFS file system is supported in AIX environments using the `acfsutil` `size` command

  - Updated Oracle ACFS views (`V$ASM_FILESYSTEM`, `V$ASM_ACFSSNAPSHOTS`, `V$ASM_ACFSAUTORESIZE`) reflect content from prior releases

  **See Also:**

  - [Managing Oracle ACFS with Command-Line Tools](manage-acfs-advm-commands.md)

  - [Oracle ACFS Diagnostic Commands](acfs-advanced-topics.md)

  - [Using Views to Display Oracle ACFS Information](views-acfs-advm-info.md)

- Support for running the Oracle ACFS `fsck` command online (Linux)

  You can conduct an online analysis of the file system without any forced downtime and can perform checks of the Oracle ACFS file system without requiring a dismount of the file system (unmount). Running `fsck` online is supported only on Linux.

  **See Also:**

  - [Oracle ACFS Command-Line Tools for Linux Environments](acfs-commands-linux.md)

- Oracle ACFS Replication Improvements

  Oracle ACFS replication improvements enable more flexibility and capabilities for replication commands. These improvements include:

  - Oracle ACFS `acfsutil` `repl` commands, except `acfsutil` `repl` `info` `—c` `—u`, can now be invoked as an Oracle ASM user that is not root.

  - Oracle ACFS `acfsutil` `repl` `terminate` `standby` now has remote terminate capabilities with a new `remote` keyword to the standby termination command:

    `acfsutil` `repl` `terminate` `standby` `remote` standby-location

    The new `remote` keyword causes the standby to terminate replication processing on the primary location before terminating replication on the standby location.

  **See Also:**

  - [Oracle ACFS Replication](understand-acfs-admin.md)

  - [Oracle ACFS Command-Line Tools for Replication](acfs-commands-replication.md)

  - [Configuring Oracle ACFS Snapshot-Based Replication](configure-acfs-replication.md)

#### Deprecated Features

These are the deprecated features for Oracle ACFS 19c.

- Deprecation of Oracle ACFS Replication Version 1

  Starting with Oracle ACFS 19c (19.3), Oracle ACFS replication protocol version 1 is deprecated. Replication protocol version 1 has been replaced with snapshot-based replication version 2, introduced in Oracle ACFS 12c Release 2 (12.2.0.1).

  **See Also:**

  - [Oracle ACFS Replication](understand-acfs-admin.md) for an overview of Oracle ACFS snapshot-based replication

  - [Configuring Oracle ACFS Snapshot-Based Replication](configure-acfs-replication.md) for information about converting an existing Oracle ACFS replication protocol version 1 environment to snapshot-based replication

- Deprecation of Oracle ACFS Encryption on Solaris and Windows

  Starting with Oracle ACFS 19c (19.3), Oracle ACFS encryption is deprecated on Solaris and Microsoft Windows operating systems.

  Oracle ACFS Encryption on Oracle Solaris and Microsoft Windows is based on RSA technology. Retirement of RSA technology has been announced. Oracle ACFS Encryption continues to be supported on Linux, and is unaffected by this deprecation, because Linux uses an alternative technology.

- Deprecation of Oracle ACFS on Windows

  Starting with Oracle ACFS 19c (19.5), Oracle ACFS is deprecated on Microsoft Windows.

  Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle ACFS file systems on Microsoft Windows are deprecated, and can be desupported in a future release. Depending on the use case, to replace current Oracle ACFS file systems, Oracle recommends that you move to Oracle Automatic Storage Management (Oracle ASM), Oracle Database File System (DBFS), or Microsoft Windows shares.

- Deprecation of Oracle ACFS Security (Vault) and Oracle ACFS Auditing

  Starting with Oracle ACFS 19c (19.5), Oracle ACFS Security (Vault) and ACFS Auditing are deprecated.

  Deprecating certain clustering features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle ACFS Security (Vault) and Oracle ACFS Auditing are deprecated, and can be desupported in a future release.

- Deprecation of Oracle ACFS on Member Clusters (ACFS Remote)

  Starting with Oracle ACFS 19c (19.5), Oracle ACFS on Member Clusters (ACFS Remote) is deprecated.

  Oracle Oracle ACFS on Member Clusters (ACFS Remote) is deprecated, and can be removed in a future release. Deprecating certain clustering features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability across all features and functionality.

- Deprecation of Cluster Domain - Member Clusters

  Starting with Oracle Grid Infrastructure 19c (19.5), Member Clusters, which are part of the Oracle Cluster Domain architecture, are deprecated.

  Oracle Member Clusters are deprecated, and can be desupported in a future release. Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. The deprecation of Member Clusters affects the clustering used with the DSC, but not its ability to host services for other production clusters. Oracle recommends that customers align their next software or hardware upgrade with the transition off Cluster Domain - Member Clusters.

### Changes in Oracle Automatic Storage Management 18c

The following are changes in Oracle Automatic Storage Management 18c.

- New Features

- Deprecated Features

- Desupported Features

#### New Features

These are new features for Oracle ASM 18c.

- Converting Normal or High Redundancy Disk Groups to Flex Disk Groups without Restricted Mount

  You can convert a conventional disk group (disk group created before Oracle ASM 18c) to an Oracle ASM flex disk group without using the restrictive mount (`MOUNTED` `RESTRICTED`) option.

  Virtual Allocation Metadata (VAM) migration must be enabled and completed before converting without the use of a restrictive mount.

  **See Also:**

  - [About Oracle ASM Flex Disk Groups](asm-filegroups.md) for information about Oracle ASM flex disk groups

  - [Managing Oracle ASM Flex Disk Groups](asm-filegroups.md) for information about Oracle ASM flex disk groups, extended disk groups, and file groups

- Dropping Oracle ASM File Groups With a Cascade Option

  You can drop a file group and its associated files (drop including content) using the `CASCADE` keyword with `ALTER` `DISKGROUP` ... `DROP` `FILEGROUP` SQL statement.

  **See Also:**

  - [About Oracle ASM File Groups](asm-filegroups.md) for information about Oracle ASM file groups

  - [Managing Oracle ASM Flex Disk Groups](asm-filegroups.md) for information about Oracle ASM flex disk groups, extended disk groups, and file groups

- Oracle ASM Flex Disk Group Support for Multitenant Cloning

  You can create an Oracle ASM mirror clone of a multitenant database. Oracle ASM file group properties and the SQL syntax for administering pluggable databases have been updated.

  **See Also:**

  - [About Point-In-Time Database Cloning With Oracle ASM Flex Disk Groups](asm-filegroups.md) for information about point-in-time database clones

  - [Managing Oracle ASM Flex Disk Groups](asm-filegroups.md) for information about Oracle ASM flex disk groups, extended disk groups, and file groups

- Oracle ASM Miscellaneous Enhancements

  You can set the `CONTENT_HARDCHECK.ENABLED` disk group attribute to enable or disable Hardware Assisted Resilient Data (HARD) checking when performing data copy operations .

  The default value for the `DISK_REPAIR_TIME` disk group attribute has changed from 3.6 hours (`3.6h`) to 12 hours (`12h`).

  **See Also:**

  - [Managing Disk Group Attributes](manage-diskgroup-attributes.md) for information about disk group attributes

- Storage Conversion for Member Clusters

  You can use ASMCMD commands to administer the configuration of member clusters. For example, you can change the storage method from direct Oracle ASM to indirect Oracle ASM, or change from indirect Oracle ASM to direct Oracle ASM.

  **See Also:**

  - [Administering Oracle Flex ASM](manage-flex-asm.md) for information about administering Oracle Flex ASM

  - [ASMCMD Member Cluster Management Commands](asmcmd-cluster-commands.md)for information about ASMCMD commands to manage member clusters

  - [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for information about member clusters

- Changes to ASMCMD `showversion` and `showpatches` Commands

  Additional options have been provided for ASMCMD `showversion` and `showpatches` commands.

  **See Also:**

  [ASMCMD Instance Management Commands](asmcmd-instance-commands.md) for information about ASMCMD commands to manage Oracle ASM instances

#### Deprecated Features

These are deprecated features for Oracle ASM 18c.

- Starting with Oracle Database 18c, leaf nodes are deprecated as part of Oracle Flex Cluster architecture.

  **See Also:**

  - [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

- Deprecation of Oracle ASM Intelligent Data Placement

  The Oracle ASM Intelligent Data Placement (IDP) feature has been deprecated since Oracle ASM 12c Release 2 (12.2) and desupport is planned in a future release.

  **Note:**

  IDP is not supported when Virtual Allocation Metadata (VAM) migration is enabled.

#### Desupported Features

These are desupported features for Oracle ASM release 18c.

- Desupport os Oracle XDB Features

  Oracle XDB has features that have been desupported in Oracle Database release 18c, version 18.1.

- Desupport of `STANDBY_ARCHIVE_DEST`

  The `STANDBY_ARCHIVE_DEST` initialization parameter has been desupported in Oracle Database release 18c.

**See Also:**

- [Oracle Database Upgrade Guide](../upgrd/index.md) for a complete description of the deprecated and desupported features in Oracle Database release 12c and Oracle Database release 18c

### Changes in Oracle ACFS and Oracle ADVM in Oracle ASM 18c

The following are changes to Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and Oracle ASM Dynamic Volume Manager (Oracle ADVM) in Oracle Automatic Storage Management 18c.

- New Features

#### New Features

These are new features for Oracle ACFS and Oracle ADVM in Oracle ASM 18c.

- Enhancements for Oracle ACFS Replication

  Oracle ACFS replication provides replication role reversal functionality and the designation of an Oracle ACFS snapshot as a storage location participating in replication. Oracle ACFS replication provides replication role reversal functionality, which enables the original primary and standby locations to reverse roles. Using the `acfsutil` `repl` `reverse` command, you can change the original primary to the new standby, and the original standby to the new primary.

  The role reversal functionality enhances replication to provide additional disaster recovery capabilities. With the designation of an Oracle ACFS snapshot as a replication primary or standby location, you can choose to replicate either a mounted file system or a snapshot of a mounted file system.

  Oracle recommends Oracle Data Guard and Oracle Golden Gate for database disaster recovery.

  **See Also:**

  - [Oracle ACFS Replication](understand-acfs-admin.md)

  - [Oracle ACFS Command-Line Tools for Replication](acfs-commands-replication.md)

  - [Configuring Oracle ACFS Snapshot-Based Replication](configure-acfs-replication.md)

- Reducing the Size of an Oracle ACFS File System

  You can use the `acfsutil` `size` command to reduce the size of a file system whether or not the command must internally move user data or metadata to complete the action.

  **See Also:**

  - [Oracle ACFS Command-Line Utilities](acfs-commands-utilities.md)

- Oracle ACFS Remote Service for Member Clusters

  In addition to support for Oracle member clusters with attached local storage, Oracle ACFS provides Oracle ACFS remote service for native Oracle ACFS functionality on member clusters with no attached local storage (indirect storage member clusters). Utilizing an Oracle ACFS deployment on the Oracle Domain Services Cluster (DSC), Oracle ACFS remote service can be used for both Oracle Application Clusters and database member clusters to enable a flexible and file system-based deployment of applications and databases. Unlike NFS-based exports, Oracle ACFS remote service fully supports advanced Oracle ACFS features; such as replication, snapshots, and tagging; on the destination member cluster.

  **See Also:**

  - [About Oracle ACFS in the Cluster Domain](understand-acfs-concepts.md)

  - [Oracle ACFS Remote Service in the Cluster Domain](understand-acfs-admin.md)

  - [Oracle ACFS Command-Line Tools for Oracle ACFS in the Cluster Domain](acfs-commands-cluster-domain.md)

  - [ASMCMD Member Cluster Management Commands](asmcmd-cluster-commands.md)

  - [Managing Oracle Flex ASM](manage-flex-asm.md)

- Additional Information Displays for Oracle ACFS Storage Usage

  You can use the`acfsutil` `info` `storage` command to display a platform independent view that shows how the space in an Oracle ASM disk group is consumed by components of Oracle ASM, Oracle ACFS, and Oracle ADVM.

  **See Also:**

  - [Oracle ACFS Command-Line Utilities](acfs-commands-utilities.md)

- Enhancements to Oracle ACFS Snapshot Commands

  Oracle ACFS `acfsutil` commands have been updated to provide better management of Oracle ACFS snapshots.

  - You can create or delete snapshot links with the `acfsutil` `snap` `link` command. A snapshot link provides access to the contents of a snapshot using an alternate path which does not include the `.ACFS/snaps` directory, the default location where snapshots are created.

  - The `acfsutil` `snap` `dup` `apply` command provides the `—B` option to specify the name of a generated backup snapshot.

  **See Also:**

  - [Oracle ACFS Command-Line Tools for Snapshots](acfs-commands-snapshots.md)

  - [About Oracle ACFS Snapshots](understand-acfs-concepts.md)

- Temporarily Freezing Modification in an Oracle ACFS File System

  You can use the `acfsutil` `freeze` and `acfsutil` `thaw` commands to temporarily halt and resume modification activity in an Oracle ACFS file system. Using the `acfsutil` `freeze` command, you can create point-in-time images across different snapshots without stopping your applications. Cross-node communication ensures that all nodes perform a freeze operation. During the freeze, each node stops all modification operations on the specified file system, flushes user data and metadata, commits the data to disk, and then acknowledges when the operations are completed.

  **See Also:**

  - [Oracle ACFS Command-Line Utilities](acfs-commands-utilities.md)

- Enhancements to Oracle ACFS Diagnostic Commands

  Oracle ACFS diagnostic commands, such as `acfsutil` `meta`, have been updated to provide improved diagnostic management of Oracle ACFS.

  **See Also:**

  - [Oracle ACFS Diagnostic Commands](acfs-advanced-topics.md)
