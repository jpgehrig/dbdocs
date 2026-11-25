This section describes concepts for the key Oracle ACFS components and contains the following topics:

- About Oracle ACFS

- About the Oracle ACFS Mount Model and Namespace

- About Oracle ACFS and Database Data Files

- About Oracle ACFS and Oracle Database Homes

- About Oracle ASM Dynamic Volume Manager

- About the Oracle ACFS Driver Model

- About the Oracle ACFS Mount Registry

- About Oracle ACFS in the Cluster Domain

- About Oracle ACFS Snapshots

- About Oracle ACFS and Backup and Restore

- About Oracle ACFS Integration with Oracle ASM

- About Oracle ACFS and External Tables on Windows

### About Oracle ACFS

Oracle ACFS is designed as a general-purpose, standalone server and clusterwide file system that delivers support for all customer files. Users and applications can access and manage Oracle ACFS using native operating system file system application programming interfaces (APIs) and command-line interface (CLI) tools. Users can also manage Oracle ACFS with Oracle ASM Configuration Assistant (ASMCA).

Oracle ACFS supports large files with 64-bit file and file system data structure sizes leading to exabyte capable file and file system capacities on 64 bit platforms. Variable extent-based storage allocation and high-performance directories contribute to fast performance and shared disk configurations that provide direct storage paths to Oracle ACFS file data from each cluster member. File system integrity and fast recovery is achieved with Oracle ACFS metadata checksums and journaling. Oracle ACFS is designed as a multi-node, shared file system model that delivers coherent, cached, direct storage paths to Oracle ACFS file data from each cluster member.

Oracle ACFS files systems are typically configured for clusterwide access. File systems, files, and directories are visible and accessible from all cluster members and can be referenced by users and applications using the same path names from any cluster member. This design enables simplified application deployments across cluster members and facilitates both multiple instance cluster applications and high availability (HA) failover of unmodified standalone server applications.

Oracle ACFS presents single system file access semantics across cluster configurations. Applications and users on all cluster members are always presented with the same view of shared Oracle ACFS file data, supported by the Oracle ACFS clusterwide user and metadata cache coherency mechanism.

### About the Oracle ACFS Mount Model and Namespace

Oracle ACFS is designed as a hierarchical file system containing files and subdirectories organized into a tree-structured namespace with files at the leaves. The namespace design is a single-file system naming model for both standalone server and cluster configurations. This design enables each cluster member to present shared files to cluster applications using the same path names, simplifying multi-node application and user access, and overall file system administration. The Oracle ACFS mount model also accommodates node local mounts and cluster node subset mounts in cluster configurations to accommodate additional customer requirements.

It is best practice for Oracle ACFS file systems to be Oracle Clusterware managed with Oracle Clusterware resources to ensure they are properly handled during Oracle Grid Infrastructure startup and shutdown.

You can explicitly use the `mount` command. However, if the resource has been created, then the file system may already be mounted.

### About Oracle ACFS and Database Data Files

**Note:**

The best practice for data files in Oracle ACFS is to use a clusterwide resource for the Oracle ACFS File system that stores the data files.

If the data files are added after the database installation is complete, you must modify the database dependencies to list the new Oracle ACFS file system. Failure to do so results in errors with application reliability. To specify the file systems in the dependency list, use the SRVCTL database object command to modify the Oracle ACFS paths used by the resource.

Oracle ACFS in Oracle Grid Infrastructure 18c cluster and standalone (Oracle Restart) configurations supports all database files for Oracle Database releases 11.2.0.4 or higher. Oracle ACFS can be configured for use with the database particularly to leverage Oracle ACFS snapshots for database testing and development. To support database files in cluster configurations, the `COMPATIBLE.ADVM` attribute must be set to `12.1` or higher for the disk group that contains the Oracle ACFS file system. In an Oracle Restart configuration, the `COMPATIBLE.ADVM` attribute must be set to `12.2.0.1` or higher to support all database files.

Support for database data files on Windows begins with Oracle Grid 12c Release 1 (12.1.0.2). For support of database files on Windows, the `COMPATIBLE.ADVM` attribute must be set to `12.1.0.2` or higher.

Support for database data files on Oracle Exadata (Linux) begins with Oracle Grid 12c Release 1 (12.1.0.2). However, Oracle ACFS does not currently have the ability to push database operations directly into storage.

Oracle ACFS on Oracle Grid Infrastructure 12.1.0.2 additionally supports all database files for Oracle Database 10g Release 2 (10.2.0.4 and 10.2.0.5) on Oracle Exadata (Linux) storage. For database file support with Oracle Database 10g Release 2 (10.2.0.4 and 10.2.0.5) on Oracle Exadata storage, the following conditions must be met:

- When creating an Oracle Database with DBCA, you must set the `REMOTE_LISTENER` initialization parameter to `your_scan_vip``:1521` otherwise DBCA fails during the create process.

- You must modify all the start and stop dependencies of the database instance resources to ensure that the resources start when starting Oracle Clusterware.

The following list provides important information about using Oracle ACFS with database files:

- Oracle ACFS support includes all file types supported by Oracle ASM.

- When storing database data files on Oracle ACFS, you must set the `FILESYSTEMIO_OPTIONS` initialization parameter to `setall`; other settings are not supported. To achieve optimal performance with database data files, set `ASM` and `ADVM` compatibility attributes to `12.1` or higher for the disk group that contains the Oracle ADVM volume intended to hold the data files. For volumes created before 12.1.0.2, set the stripe columns to `1`, or set the stripe columns to `8` and the stripe width to `1` `MB`. Volumes created while running 12.1.0.2 or higher already default to the high performance configuration (stripe columns = `8` and stripe width = `1` `MB`).

- To obtain optimal database performance with snapshots, the snapshots must be created after the `ADVM` compatibility attribute is set to `12.1` or higher.

- Use a 4 K or larger database block size and tablespace block size with Oracle ACFS for best performance.

- For best performance when using Oracle Exadata, use a 4 K metadata file system.

- Oracle ACFS does not support databases with 2 K block sizes.

- Do not export Oracle ACFS file systems containing database files through NFS to access them from a DNFS client. This configuration is not supported.

- If a data file is configured to automatically extend, then the size of the increments should be large enough to ensure that the extend operation occurs infrequently. Frequent automatic extends have a negative performance impact.

- Running a workload in a snapshot reduces resources for the primary workload running on the base files because the storage is shared between the base file system and the snapshots. To run test scenarios in Oracle ACFS snapshots without impacting the primary workload, copy the file system and then run test workloads on snapshots created in the copied file system.

- Oracle ACFS does not support encryption or replication with Oracle Database data files, tablespace files, control files, redo logs, archive logs, RMAN backups, Data Pump dumpsets or flashback files. To encrypt database data files on Oracle ACFS, Oracle recommends Oracle Advanced Security. Oracle Advanced Security provides Transparent Data Encryption (TDE) to encrypt data files for entire tablespaces. Oracle Data Guard and Oracle GoldenGate provide other replication options for database files on Oracle ACFS.

- Databases that share storage with snapshots or with the base of the file system can become fragmented under active online transaction processing (OLTP) workloads. This fragmentation can cause the location of the data in the volume to be discontiguous for sequential scans. Oracle ACFS automatically defragments these files in the background. Fragmentation is reported through the `acfsutil` `defrag` `dir` and `file` commands, and it can also be viewed with the `acfsutil` `info` `file` command. The `acfsutil` `defrag` `dir` and `file` commands also enable on-demand defragmentation of a file in the event the automatic defragmentation does not occur quickly enough.

**See Also:**

- [Creating Oracle ACFS Resources](understand-acfs-admin.md) for information about Oracle ACFS resources

- [What Types of Files Does Oracle ASM Support?](asm-files-directories-templates.md) for a list of file types supported by Oracle ASM

- [volcreate](manage-advm-asmcmd.md) for information about creating a volume

- [mkfs](acfs-commands-linux.md) for information about setting the metadata block size with `mkfs` `-i`

- [Oracle ACFS Command-Line Utilities](acfs-commands-utilities.md) for information about `acfsutil` `defrag` and `acfsutil` `info` commands

- [Oracle Database Reference](../refrn/REMOTE_LISTENER.md) for information about the `REMOTE_LISTENER` initialization parameter

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/making-applications-highly-available-using-oracle-clusterware.md) for information about resource dependencies

- [Oracle Database Advanced Security Guide](../asoag/asopart1.md) for information about Transparent Data Encryption (TDE)

- [Oracle Data Guard Concepts and Administration](../sbydb/introduction-to-oracle-data-guard-concepts.md) for information about other replication options for database files on Oracle ACFS

- <https://www.oracle.com/middleware/technologies/goldengate.html> for Oracle GoldenGate documentation about other replication options for database files on Oracle ACFS

### About Oracle ACFS and Oracle Database Homes

An Oracle ACFS file system can be configured as an Oracle Database home.

When installing a database in a cluster, it is required to use a shared Oracle ACFS file system for the database home. You can use an Oracle ACFS file system for an Oracle Database home with Oracle 11g Release 2 (11.2) or later.

When installing Oracle Software, there must be a separate Oracle base (`ORACLE_BASE`) associated with each operating system user. For example, there should be a separate Oracle base for a grid user and a database user.

You can locate the Oracle Database base (`ORACLE_BASE` for database) directory and home (`ORACLE_HOME` for database) directory on an Oracle ACFS file system. The Oracle Database base (`ORACLE_BASE` for database) directory should not be the Oracle Grid Infrastructure base (`ORACLE_BASE` for grid) directory or should not be located under the Oracle Grid Infrastructure base directory (`ORACLE_BASE` for grid).

The Oracle Grid Infrastructure base (`ORACLE_BASE` for grid) directory and home (`ORACLE_HOME` for grid) directory cannot be located on the Oracle ACFS file system because the Oracle ACFS file system cannot be created until Oracle Grid Infrastructure is installed.

One or more Oracle Database homes on Oracle ACFS can be created under the same mount point with each home using a separate Oracle ACFS file system.

After the installation of Oracle Grid Infrastructure Software and before the installation of the Oracle Database software with Oracle Universal Installer (OUI), you can create an Oracle ACFS file system to be configured for use as an Oracle Database home.

You can also use the Oracle ASM Configuration Assistant (ASMCA) or Oracle ACFS commands to create the file system.

**Note:**

When an Oracle ACFS file system contains an Oracle Database home or Oracle Database uses the file system for any file storage, the file system must have an Oracle ACFS file system resource. If you have not used Oracle ASM Configuration Assistant to setup the mount point, then you must use Server Control Utility (SRVCTL) commands to set up Oracle Database dependencies.

In an Oracle Grid Infrastructure clusterware configuration, a clusterwide Oracle ACFS resource is required when using Oracle ACFS for the database home. To enable the database owner to act on the resource, the owner must be specified as a permitted user when creating the resource. You can specify the database owner with the `-u` option of the `srvctl` `add` `filesystem` or `acfsutil` `registry` command. Root privilege is required when adding the resource in Linux or Unix environments.

After the Oracle ACFS file system and resources are created, the Oracle ACFS-based database home mount point location can be selected as the Oracle Database home location by browsing to and then choosing the directory during the Oracle Universal Installer (OUI) Database Software installation.

You can use the `srvctl` `start` `filesystem` command to manually mount the Oracle ACFS file system.

**Note:**

When additional Oracle ACFS file systems are added to an Oracle Database after creation, they must be specified in the Oracle Database Resource Dependency list. Failure to do so results in errors with application reliability. To specify the file systems in the dependency list, use the SRVCTL database object command to modify the Oracle ACFS paths used by the resource.

Oracle ACFS file systems can be also configured for use as a home for applications. However, Oracle ACFS file systems cannot be used for an Oracle base directory or an Oracle Grid Infrastructure home that contains the software for Oracle Clusterware, Oracle ASM, Oracle ACFS, and Oracle ADVM components.

To reduce contention on an Oracle ACFS file system in an Oracle RAC environment where the Oracle Database home is shared on Oracle ACFS, Oracle Database auditing operating system files should be configured as node specific. For a node-specific setup, you must ensure that the `AUDIT_FILE_DEST` initialization parameter in the configuration file of each database instance points to a unique location rather than one location for all the database instances.

For example, if you have a database with the Oracle name set to `TEST` and you want to ensure that the location of `AUDIT_FILE_DEST` initialization parameter for each database instance, such as `TEST1` or `TEST2`, points to a node specific location for that instance, you can run the following SQL statement:

    SQL> ALTER SYSTEM SET AUDIT_FILE_DEST='$ORACLE_BASE/admin/adump/TEST/@'
         SCOPE=SPFILE SID='*';

In the previous example, `@` expands to the `ORACLE_SID` of each instance. If `ORACLE_BASE` has been set to `/acfsmounts` in this example, then that value could have been used in place of the `ORACLE_BASE` variable.

**See Also:**

- [Managing Oracle ACFS with Command-Line Tools](manage-acfs-advm-commands.md) for information about using Oracle ACFS commands to create a file system

- [Creating an Oracle ACFS File System for Database Use](manage-acfs-advm-asmca.md) for information about using ASMCA

- [Creating Oracle ACFS Resources](understand-acfs-admin.md) for additional information Oracle ACFS resources

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md) and [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-storage-in-oracle-rac.md) for information about SRVCTL commands

- [Oracle Database Installation Guide](../install-and-upgrade.md) for your environment for information about the installation of Oracle Database software and storage options and about Optimal Flexible Architecture (OFA) recommendations for Oracle base and home directories

- [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your environment for information about the installation of Oracle Grid Infrastructure software and storage options

- [Oracle Database Administrator's Guide](../admin/using-oracle-managed-files.md) for information about using Oracle Managed files

- [Oracle Database Reference](../refrn/AUDIT_FILE_DEST.md) for information about the `AUDIT_FILE_DEST` initialization parameter

### About Oracle ASM Dynamic Volume Manager

The Oracle ASM Dynamic Volume Manager (Oracle ADVM) provides volume management services and a standard disk device driver interface to clients. File systems and other disk-based applications send I/O requests to Oracle ADVM volume devices as they would to other storage devices on a vendor operating system.

For more information about Oracle ADVM, refer to [Overview of Oracle ASM Dynamic Volume Manager](overview-advm.md).

### About the Oracle ACFS Driver Model

An Oracle ACFS file system is installed as a dynamically loadable vendor operating system (OS) file system driver and tool set that is developed for each supported operating system platform. The driver is implemented as a Virtual File System (VFS) and processes all file and directory operations directed to a specific file system.

**Note:**

Errors encountered by the drivers are written to the native operating system console and system event loggers. Refer to [Understanding Oracle ACFS I/O Failure Console Messages](acfs-advanced-topics.md).

### About the Oracle ACFS Mount Registry

The Oracle ACFS mount registry supports Oracle Grid Infrastructure cluster configurations, but does not support Oracle Restart configurations.

File systems that are to be mounted persistently (across restarts) can be registered with the Oracle ACFS mount registry. In cluster configurations, registered Oracle ACFS file systems are automatically mounted by the mount registry, similar to a clusterwide mount table. However, in Oracle Restart configurations the automatic mounting of registered Oracle ACFS file systems is not supported.

By default, an Oracle ACFS file system that is inserted into the Oracle ACFS mount registry is automatically mounted on all cluster members, including cluster members that are added after the registry addition. However, the Oracle ACFS mount registry also accommodates standalone and multi-node (subset of cluster nodes) file system registrations. The mount registry actions for each cluster member mount only registered file systems that have been designated for mounting on that member.

The Oracle ACFS mount registry is implemented using Oracle Clusterware resources, specifically the Oracle ACFS resource. The Oracle ACFS resource actions are designed to automatically mount a file system only one time for each Oracle Grid Infrastructure initialization to avoid potential conflicts with administrative actions to dismount a given file system.

**See Also:**

- [Oracle ACFS and Oracle Restart](acfs-advanced-topics.md) for more information about Oracle ACFS and Oracle Restart

- [acfsutil registry](acfs-commands-utilities.md) for information about registering an Oracle ACFS file system using the `acfsutil` command

- [Oracle Clusterware Resources and Oracle ACFS Administration](understand-acfs-admin.md) for more information about the implementation of the mount registry and Oracle ACFS resources

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md) and [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-storage-in-oracle-rac.md) for information about SRVCTL commands, including the `srvctl` `add` `filesystem` command

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for information about Oracle Clusterware resources

### About Oracle ACFS in the Cluster Domain

In addition to support for Oracle Database member clusters with attached local storage, Oracle ACFS provides Oracle ACFS remote service for native Oracle ACFS functionality on Oracle Database member clusters with no attached local storage (InDirect Storage Member Cluster). Utilizing an Oracle ACFS deployment on the Oracle Domain Services Cluster (DSC), Oracle ACFS remote service can be used for both Oracle Database application clusters and Oracle Database member clusters to enable a flexible and file system-based deployment of applications and databases. Unlike NFS-based exports, Oracle ACFS remote service fully supports advanced Oracle ACFS features; such as replication, snapshots, and tagging; on the destination member cluster.

#### Oracle Database Member Clusters

Oracle Database member clusters can be configured with or without local storage.

- Oracle Database member clusters with attached local storage

  Oracle Database member clusters can be configured with local storage. These clusters utilize a GIMR from the Domain Services Cluster, and operate similar to a standalone Oracle ASM cluster. Oracle ACFS in these clusters operate normally with the full Oracle ASM Proxy and all traditional tools. These member clusters manage their own storage.

- Oracle Database member clusters with No Attached Local Storage

  Oracle Database member clusters can also be configured without attached local storage. These InDirect Storage Member Clusters utilize consolidated storage services from the Domain Services Cluster (DSC). To use Oracle ACFS file systems and Oracle ADVM volumes, the Oracle Database member clusters use the Oracle ACFS remote service from the Domain Services Cluster.

  An InDirect Storage Member Cluster provides for a small lightweight Oracle Clusterware (CRS) stack that can run traditional databases or other applications. This member cluster consumes less memory, is easier to provision, and can be easily hosted in VMs because there are no direct attached storage requirements. InDirect Storage Member clusters are very suited for resource and application consolidation. In this scenario, Oracle ACFS Remote enables full storage and resource consolidation on the Domain Services Cluster, enabling a new generation of compact and cheap computing resources.

#### Oracle ACFS Remote Service

Oracle ACFS remote service enables the use of Oracle ACFS in an InDirect Storage Member Cluster. Oracle ACFS remote service is provided as another service of the DSC. Because an InDirect Storage Member Cluster has no direct attached storage to the Oracle Database member cluster, Oracle ACFS remote service provides an Oracle ACFS enabled storage fast-path between the DSC and the member cluster for Oracle ACFS usage over standard block transports.

When Oracle ACFS remote service is in use, the Oracle Database member cluster has access to all Oracle ACFS functionality, including snapshots, resizing, Oracle Database and other POSIX applications, plus ACFS NAS/MAX, tagging, checking, repairing, scrubbing, security, encryption, and compression. When an application uses the Oracle ACFS remote service export functionality on the member cluster, there is no functional or programmatic difference between Oracle ACFS use locally or remotely. In addition, all Oracle ACFS tools and utilities continue to operate normally. As part of its default configuration, Oracle ACFS remote service provides for high availability of exports. If a transport or DSC node is unavailable, then operations continue on other nodes of the DSC. This continuation provides for full failover and availability of the member cluster operations. Oracle ACFS Remote also handles temporary transport level outages in a similar manner.

#### Repositories, Exports, and Transports

Repository, export, and transport are integral components of Oracle ACFS remote service.

- Repository

  A repository is a directory in an Oracle ACFS file system on the DSC that serves as a host for exports. The file system is a standard Oracle ACFS file system, enabling standard Oracle ACFS functionality to be applied to the file system, including resizing, replication, and snapshots. Because it is an Oracle ACFS file system, the repository is subject to the 1 petabyte Oracle ACFS file system limitation. If the total of the expected backing files in all repositories on the Oracle ACFS file system exceeds the file system size, then multiple repositories are necessary.

  Oracle ACFS file compression is not supported in a repository.

- Export

  The DSC provides exports. These exports start as backing files that reside in an Oracle ACFS remote service repository on the DSC. The file is then exported using a transport so that only the intended member cluster nodes have access to the export using that transport. Exports are managed using the `advmutil` `export` series of commands. After a file is in use by Oracle ACFS remote service, it cannot be removed until the file is removed from use by Oracle ACFS remote service.

- Transport

  Oracle ACFS remote service uses transports to provide access to the exports. For Oracle ASM release 18c, version 18.1, only the iSCSI transport is supported. This transport is configured using a small transport definition file and automatically managed by Oracle ACFS remote service. Transports are managed using the `advmutil` `transport` series of commands.

**See Also:**

- [Oracle ACFS Remote Service in the Cluster Domain](understand-acfs-admin.md)

- [Oracle ACFS Command-Line Tools for Oracle ACFS in the Cluster Domain](acfs-commands-cluster-domain.md)

- [ASMCMD Member Cluster Management Commands](asmcmd-cluster-commands.md)

- [Managing Oracle Flex ASM](manage-flex-asm.md)

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for an overview of Oracle Clusterware architecture

### About Oracle ACFS Snapshots

An Oracle ACFS snapshot is an online, read-only or read-write, point in time copy of an Oracle ACFS file system.

The snapshot copy is space-efficient and uses Copy-On-Write functionality. Before an Oracle ACFS file extent is modified or deleted, its current value is copied to the snapshot to maintain the point-in-time view of the file system.

Oracle ACFS snapshots are immediately available for use after they are created. The snapshots are created in the `.ACFS/snaps/` directory of the file system. They are always online while the file system is mounted. Consequently, an Oracle ACFS snapshot can support the online recovery of files inadvertently modified or deleted from a file system. An Oracle ACFS snapshot can also be used as the source of a file system backup, as it can be created on demand to deliver a current, consistent, online view of an active file system.

Up to 1023 read-only, read-write, or combination of read-only and read-write snapshot views are supported for each file system, enabling flexible online file recovery solutions spanning multiple views to be employed. On 64-bit systems, Oracle ACFS supports 1023 snapshots. The total number of snapshots can be any combination of read-only and read-write snapshots. To support the creation of more than 63 snapshots, the disk group compatibility attribute for `ADVM` must be set to `12.1.0.2` or greater. Also, the following conditions must be met to create more than 63 snapshots.

- All snapshots of the file system that were created with `COMPATIBLE.ADVM` set to less than `12.1.0.2` must be deleted.

- All snapshots of the file system that were created after setting `COMPATIBLE.ADVM` to `12.1.0.2` or greater while older snapshots existed must be deleted.

Oracle ACFS read-write snapshots enable fast creation of an snapshot image that can be both read and written without impacting the state of the Oracle ACFS file system hosting the snapshot images. You can use read-write snapshots for:

- Testing of new versions of application software on production file data reflected in the read-write snapshot image without modifying the original production file system

- Running test scenarios on a real data set without modifying the original production file system

To use Oracle ACFS read-write snapshots, the disk group compatibility attribute for `ADVM` must be set to `11.2.0.3.0` or higher. If you create a read-write snapshot on an existing Oracle ACFS file system from a version earlier than `11.2.0.3.0`, then the file system is updated to the `11.2.0.3.0` or higher format. After a file system has been updated to a higher version, an Oracle ACFS file system cannot be reverted to an earlier version, and accordingly cannot be mounted on an earlier Oracle Grid Infrastructure version.

You can create a snapshot from an existing snapshot in the same Oracle ACFS file system. In addition, you can convert a snapshot between read-only and read-write formats. To create from an existing snapshot or convert a snapshot, the disk group compatibility attribute for `ADVM` must be set to `12.1` or higher. In addition, creation from an existing snapshot is not permitted if there are:

- Any snapshots present in the file system that were created with the `ADVM` compatibility set to less than 12.1

- Any snapshots of the file system that were created after `ADVM` compatibility was set to `12.1` but while 11.2 snapshots existed

Oracle ACFS snapshot storage is maintained within the file system, eliminating the management of separate storage pools for file systems and snapshots. Oracle ACFS file systems can be dynamically resized to accommodate additional file and snapshot storage requirements.

You cannot modify security or encryption metadata in read-write snapshots except for enabling or disabling security or encryption. No other alteration is permitted on Oracle ACFS security or encryption metadata in a snapshot. If a file was not secured by a security realm in the snapshot, it cannot be realm secured by adding the corresponding file in the active file system to a security realm. If a file was not encrypted in the snapshot, that file cannot be encrypted by encrypting the corresponding file in the active file system.

A new file created in a realm-secured directory in a read-write snapshot inherits the realm security attributes of the parent directory. If the realm protecting the new file has encryption turned on, the file is encrypted with the encryption parameters set in the realm. If the realm protecting the new file has encryption turned off, the file is decrypted. Files and directories in a read-write snapshot cannot be added to or removed from any security realm.

Files in a read-write snapshot can be encrypted, decrypted, or rekeyed if the operation target is a path specified for a file or directory of the read-write snapshot. However, if an encryption, decryption, or rekey operation is specified at the file system level, then the operation does not process files and directories of snapshots in the `.ACFS/snaps/` directory.

All Oracle ACFS snapshot operations are serialized clusterwide in the kernel. For example, if a snapshot create operation is initiated at the same time as a snapshot delete operation, then both operations would complete, but they would not run in parallel inside of the kernel. One operation would complete before the other was started.

The `acfsutil` `snap` `duplicate` commands can be invoked manually to enable a target file system or writable snapshot to track the evolution of a source file system or snapshot with minimal overhead. Oracle ACFS updates the target after each apply operation to indicate its current contents, and checks before starting the next apply operation to ensure that the starting point of the incoming snapshot duplication stream matches the endpoint of the last-applied stream. The target remains writable by any and all applications even when it is in use by `acfsutil` `snap` `duplicate` `apply` . Oracle ACFS determines any updates to the target by a process other than the apply process, and if such an update occurs, invalidates the internal metadata that track the target contents. This prevents further apply operations to the target, and avoids the possibility of a future apply operation yielding unexpected results.

The use of the `acfsutil` `snap` `duplicate` commands interacts with Oracle ACFS replication operations. A target file system in use by `acfsutil` `snap` `duplicate` `apply` cannot be specified for use as a file system for replication. And a file system in use by replication cannot be specified as the target for `acfsutil` `snap` `duplicate` `apply`.

To run the `acfsutil` `snap` `duplicate` commands, the disk group compatibility attribute for `ADVM` must be set to at least `12.2`.

Additional `acfsutil snap` commands are available to manage duplicate snapshots and remaster an Oracle ADVM volume with an existing snapshot.

Oracle ACFS snapshots are administered with the `acfsutil` `snap` commands.

**Note:**

The `link()` and `rename(`) system calls fail if an attempt is made to link or rename a file in the Oracle ACFS file system and a file in any associated read-write snapshot, or vice versa. Any tools which use the `link()` and `rename()` system calls, such as `ln` and `mv`, also fail in the same scenario.

**See Also:**

- [acfsutil snap create](acfs-commands-snapshots.md) for additional information on the target used with the `acfsutil` `snap` `duplicate` command

- [Oracle ACFS Replication](understand-acfs-admin.md) for information about Oracle ACFS replication

- [Oracle ACFS Security](understand-acfs-admin.md) for information about Oracle ACFS security

- [Oracle ACFS Encryption](understand-acfs-admin.md) for information about Oracle ACFS encryption

- [Oracle ACFS Command-Line Tools for Snapshots](acfs-commands-snapshots.md) for information about the `acfsutil` `snap` commands

### About Oracle ACFS and Backup and Restore

Oracle ACFS runs on operating system platforms as a native file system technology supporting native operating system file system application programming interfaces (APIs). Consequently, backup applications that access files using the native operating system file system interfaces are able to access and backup Oracle ACFS file systems and other native operating system file systems. Oracle ACFS snapshots can be dynamically created and used to present a consistent, on-line view of an active file system to a backup application.

Backup applications that use interfaces other than the standard operating system interfaces (read or write) are not supported with Oracle ACFS. For example, Windows backup applications that depend upon the presence of reparse points or the Windows Volume Shadow Copy Service (VSS) are not supported.

**Note:**

When Oracle ACFS is used with Oracle Recovery Manager (RMAN) backups or restore, you should tune RMAN to improve performance because the default values may not be ideal for Oracle ACFS file systems. For example, you can adjust RMAN parameters to match the buffer size with the volume stripe width or Oracle ASM AU size. Also, you can adjust the number of buffers to match the number of devices in the Oracle ASM disk group.

**See Also:**

- [Oracle ACFS Tagging](understand-acfs-admin.md) for information about using common operating system utilities to preserve Extend Attributes for tagging definitions

- [md_backup](asmcmd-diskgroup-commands.md) and [md_restore](asmcmd-diskgroup-commands.md) for information about backing up and restoring Oracle ACFS metadata

- [My Oracle Support](https://support.oracle.com) ([`https://support.oracle.com`](https://support.oracle.com)) for articles about tuning RMAN tuning, such as RMAN Performance Tuning Using Buffer Memory Parameters (Doc ID 1072545.1) and RMAN Performance Troubleshooting (Doc ID 1326686.1)

### About Oracle ACFS Integration with Oracle ASM

Oracle ACFS is always configured with Oracle ASM storage and interfaces with Oracle ASM storage through a traditional device file. This device file is presented by Oracle ADVM and is constructed using a dynamic volume file. The Oracle ADVM volume device file is created automatically following the creation of an Oracle ADVM volume. An Oracle ACFS file system is then bound to the Oracle ADVM device file during the file system creation.

After an Oracle ACFS is configured and mounted, the file system inherits the Oracle ASM storage management features associated with an Oracle ADVM volume, including dynamic balanced distribution, mirroring and striping, and dynamic resizing.

The Oracle ACFS driver establishes communication with the Oracle ASM instance to receive Oracle ASM status information including Oracle ASM instance and disk group state transitions. However, I/O does not go through Oracle ASM nor through the Oracle ASM proxy, but rather goes directly to the underlying Oracle ASM storage.

For information about Oracle ACFS and Oracle ASM operations, refer to [Oracle ACFS and Dismount or Shutdown Operations](understand-acfs-admin.md).

### About Oracle ACFS and External Tables on Windows

To access an external table stored on an Oracle ACFS file system on Windows, the external table must be created with the `DISABLE_DIRECTORY_LINK_CHECK` access parameter.

**See Also:**

- [Oracle Database Utilities](../sutil/oracle_loader-access-driver.md) for information about the `DISABLE_DIRECTORY_LINK_CHECK` access parameter

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about creating external tables
