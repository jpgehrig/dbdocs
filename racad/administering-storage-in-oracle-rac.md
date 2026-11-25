Oracle recommends Oracle Automatic Storage Management (Oracle ASM) as a storage management solution that provides an alternative to conventional volume managers, file systems, and raw devices.

Oracle ASM is a [volume manager](glossary.md) and a [file system](glossary.md) for Oracle database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations.

Oracle ASM uses disk groups to store data files; an Oracle ASM disk group is a collection of disks that Oracle ASM manages as a unit. Within a disk group, Oracle ASM exposes a file system interface for Oracle database files. The content of files that are stored in a disk group is evenly distributed to eliminate hot spots and to provide uniform performance across the disks. The performance is comparable to the performance of raw devices.

You can add or remove disks from a disk group while a database continues to access files from the disk group. When you add or remove disks from a disk group, Oracle ASM automatically redistributes the file contents and eliminates the need for downtime when redistributing the content.

The Oracle ASM volume manager functionality provides flexible server-based mirroring options. The Oracle ASM normal and high redundancy disk groups enable two-way and three-way mirroring respectively. You can use external redundancy to enable a Redundant Array of Independent Disks (RAID) storage subsystem to perform the mirroring protection function.

Oracle ASM also uses the Oracle Managed Files feature to simplify database file management. Oracle Managed Files automatically creates files in designated locations. Oracle Managed Files also names files and removes them while relinquishing space when tablespaces or files are deleted.

Oracle ASM reduces the administrative overhead for managing database storage by consolidating data storage into a small number of disk groups. The smaller number of disk groups consolidates the storage for multiple databases and dprovides for improved I/O performance.

Oracle ASM files can coexist with other storage management options such as raw disks and third-party file systems. This capability simplifies the integration of Oracle ASM into pre-existing environments.

Oracle ASM has easy to use management interfaces such as SQL\*Plus, the Oracle ASM Command Line Utility (ASMCMD) command-line interface, and Oracle ASM Configuration Assistant (ASMCA).

This chapter includes the following topics:

- Overview of Storage Management for Oracle RAC

- Data File Access in Oracle RAC

- NFS Server for Storage

- Redo Log File Storage in Oracle RAC

- Automatic Undo Management in Oracle RAC

- Oracle Automatic Storage Management with Oracle RAC

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/admin-asm-diskgroups.md)
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/part-instance-diskgroup.md)

### Overview of Storage Management for Oracle RAC

All data files (including an undo tablespace for each instance) and redo log files (at least two for each instance) for an Oracle RAC database must reside on shared storage.

Oracle recommends that you use Oracle ASM to store these files in an Oracle ASM disk group.

Oracle supports alternative ways of using shared storage, such as certified **cluster file system**s. In addition, Oracle recommends that you use one shared server parameter file (SPFILE) with instance-specific entries. Oracle RAC 12c allows storing shared password files in Oracle ASM and storing Oracle Database files on Oracle Automatic Storage Management Cluster File System (Oracle ACFS).

**Note:**

Oracle Database and related technologies, such as Oracle Clusterware, no longer support the use of raw (block) storage devices. You must move files to Oracle ASM before upgrading to Oracle Clusterware 12c.

Unless otherwise noted, Oracle Database storage features such as Oracle ASM, Oracle Managed Files, automatic segment-space management, and so on, function the same in Oracle RAC environments as they do in non-cluster Oracle database environments.

**Related Topics**

- [Overview of Installing Oracle Database Software and Creating a Database](../admqs/installing-oracle-database-creating-database.md)
- [Introducing Oracle Automatic Storage Management](../ostmg/asm-intro.md)
- [Oracle Database Structure and Storage](../admin/oracle-database-structure-and-storage.md)

### Data File Access in Oracle RAC

All Oracle RAC instances must be able to access all data files. If a data file must be recovered when the database is opened, then the first Oracle RAC instance to start is the instance that performs the recovery and verifies access to the file. As other instances start, they also verify their access to the data files. Similarly, when you add a tablespace or data file or bring a tablespace or data file online, all instances verify access to the file or files.

If you add a data file to a disk that other instances cannot access, then verification fails. Verification also fails if instances access different copies of the same data file. If verification fails for any instance, then diagnose and fix the problem. Then run the `ALTER SYSTEM CHECK DATAFILES` statement on each instance to verify data file access.

### NFS Server for Storage

An Oracle database can serve as a network file system (NFS) server. The database responds to NFS requests from any NFS client and stores both the files and their metadata within the database.

Files associated with a primary database, such as SQL scripts, can be automatically replicated on a standby database. You can also store unstructured data, such as emails, on the database.

You can create or destroy an Oracle file system and access it though the NFS server using the procedures documented in Oracle Database SecureFiles and Large Objects Developer's Guide.

**Related Topics**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introducing-network-file-system.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_FS.md)
- [Oracle Database Reference](../refrn/background-processes.md)

### Redo Log File Storage in Oracle RAC

In an Oracle RAC database, each instance must have at least two groups of redo log files. You must allocate the redo log groups before enabling a new instance with the `ALTER DATABASE ENABLE INSTANCE ``instance_name` command. When you use DBCA to create the database, DBCA allocates redo log files to instances, as required, automatically. You can change the number of redo log groups and the size of the redo log files as required either during the initial database creation or as a post-creation step.

When the current group fills, an instance begins writing to the next log file group. If your database is in `ARCHIVELOG` mode, then each instance must save filled online log groups as archived redo log files that are tracked in the control file. During database recovery, all enabled instances are checked to see if recovery is needed. If you remove an instance from your Oracle RAC database, then you should disable the instance's thread of redo so that Oracle does not have to check the thread during database recovery.

Redo log management must be considered when the number of instances for a particular production Oracle RAC database changes. For example, if you increase the cardinality of a server pool for a policy-managed database and a new server is allocated to the server pool, then Oracle starts an instance on the new server. As soon as the database instance on the new server starts, it will require a set of redo log groups. Using Oracle Managed Files based on an Oracle ASM disk group, allocation of the required redo log thread and respective files is performed automatically. You should create redo log groups only if you use administrator-managed databases.

For administrator-managed databases, each instance has its own online redo log groups. Create these redo log groups and establish group members. To add a redo log group to a specific instance, specify the `INSTANCE` clause in the `ALTER DATABASE ADD LOGFILE` statement. If you do not specify the instance when adding the redo log group, then the redo log group is added to the instance to which you are currently connected.

Each instance must have at least two groups of redo log files. You must allocate the redo log groups before enabling a new instance with the `ALTER DATABASE ENABLE INSTANCE` `instance_name` command. When the current group fills, an instance begins writing to the next log file group. If your database is in `ARCHIVELOG` mode, then each instance must save filled online log groups as archived redo log files that are tracked in the control file.

During database recovery, all enabled instances are checked to see if recovery is needed. If you remove an instance from your Oracle RAC database, then you should disable the instance's thread of redo so that Oracle does not have to check the thread during database recovery.

**Related Topics**

- [About Designing and Deploying Oracle RAC Environments](introduction-to-oracle-rac.md)
- [Oracle Database Administrator’s Guide](../admin/managing-the-redo-log.md)
- [Oracle Database SQL Language Reference](../sqlrf/ALTER-DATABASE.md)

### Automatic Undo Management in Oracle RAC

Oracle Database automatically manages undo segments within a specific undo tablespace that is assigned to an instance. Instances can always read all undo blocks throughout the [cluster](glossary.md) environment for consistent read purposes. Also, any instance can update any undo tablespace during transaction recovery, if that undo tablespace is not currently used by another instance for undo generation or transaction recovery.

You assign undo tablespaces in your Oracle RAC administrator-managed database by specifying a different value for the `UNDO_TABLESPACE` parameter for each instance in your SPFILE or individual PFILEs. For policy-managed databases, Oracle automatically allocates the undo tablespace when the instance starts if you have Oracle Managed Files enabled. You cannot simultaneously use automatic undo management and manual undo management in an Oracle RAC database. In other words, all instances of an Oracle RAC database must operate in the same undo mode.

**Related Topics**

- [Setting SPFILE Parameter Values for Oracle RAC](administering-database-instances-and-cluster-databases.md)
- [Oracle Database Administrator’s Guide](../admin/managing-tablespaces.md)

### Oracle Automatic Storage Management with Oracle RAC

Oracle ASM automatically maximizes I/O performance by managing the storage configuration across the disks that Oracle ASM manages.

Oracle ASM does this by evenly distributing the database files across all of the available storage assigned to the disk groups within Oracle ASM. Oracle ASM allocates your total disk space requirements into uniformly sized units across all disks in a disk group. Oracle ASM can also automatically mirror files to prevent data loss. Because of these features, Oracle ASM also significantly reduces your administrative overhead.

Oracle ASM instances are created on each node where you install Oracle Clusterware. Each Oracle ASM instance has either an SPFILE or PFILE type parameter file. Oracle recommends that you back up the parameter files and the TNS entries for nondefault Oracle Net listeners.

To use Oracle ASM with Oracle RAC, select Oracle ASM as your storage option when you create your database with the Database Configuration Assistant (DBCA). As in noncluster Oracle databases, using Oracle ASM with Oracle RAC does not require I/O tuning.

The following topics describe Oracle ASM and Oracle ASM administration, as follows:

- Storage Management in Oracle RAC

- Modifying Disk Group Configurations for Oracle ASM

- Oracle ASM Disk Group Management

- Configuring Preferred Mirror Read Disks in Extended Distance Clusters

- Converting Nonclustered Oracle ASM to Clustered Oracle ASM

- Administering Oracle ASM Instances with SRVCTL in Oracle RAC

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md)

#### Storage Management in Oracle RAC

You can create Oracle ASM disk groups and configure mirroring for Oracle ASM disk groups using the Oracle ASM configuration assistant (ASMCA).

Alternatively, you can use Oracle Enterprise Manager to administer Oracle ASM disk groups after you have discovered the respective servers with Oracle Enterprise Manager.

The Oracle tools that you use to manage Oracle ASM, including ASMCA, Oracle Enterprise Manager, and the silent mode install and upgrade commands, include options to manage Oracle ASM instances and disk groups.

You can use the Cluster Verification Utility (CVU) to verify the integrity of Oracle ASM across the cluster. Typically, this check ensures that the Oracle ASM instances on all nodes run from the same Oracle home and, if `asmlib` exists, that it is a valid version and has valid ownership. Run the following command to perform this check:

    cluvfy comp asm [-n node_list] [-verbose]

Replace `node_list` with a comma-delimited list of node names on which the check is to be performed. Specify `all` to check all nodes in the cluster.

Use the `cluvfy comp ssa` command to locate shared storage.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cluster-verification-utility-reference.md)

#### Modifying Disk Group Configurations for Oracle ASM

When you create a disk group for a cluster or add new disks to an existing clustered disk group, prepare the underlying physical storage on shared disks and give the Oracle user permission to read and write to the disk.

The shared disk requirement is the only substantial difference between using Oracle ASM with an Oracle RAC database compared to using it with a noncluster Oracle database. Oracle ASM automatically redistributes the data files after you add or delete a disk or disk group.

In a cluster, each Oracle ASM instance manages its node's metadata updates to the disk groups. In addition, each Oracle ASM instance coordinates disk group metadata with other nodes in the cluster. As with noncluster Oracle databases, you can use Oracle Enterprise Manager, ASMCA, SQL\*Plus, and the Server Control Utility (SRVCTL) to administer disk groups for Oracle ASM that are used by Oracle RAC. Oracle Automatic Storage Management Administrator's Guide explains how to use SQL\*Plus to administer Oracle ASM instances. Subsequent sections describe how to use the other tools.

**Note:**

When you start ASMCA, if there is not an Oracle ASM instance, then the utility prompts you to create one.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-instance.md)

#### Oracle ASM Disk Group Management

To use Oracle ASM, you must first create disk groups with ASMCA before creating a database with Oracle DBCA.

You can also use the disk group management commands to create and manage an Oracle ASM instance and its associated disk groups independently of creating a database. You can use Oracle Enterprise Manager or ASMCA to add disks to a disk group, to mount a disk group or to mount all of the disk groups, or to create Oracle ASM instances. Additionally, you can use Oracle Enterprise Manager to dismount and drop disk groups or to delete Oracle ASM instances.

Oracle ASM instances are created when you install Oracle Clusterware. To create an Oracle ASM disk group, run ASMCA from the `Grid_home``/bin` directory. You can also use the Oracle ASM Disk Groups page in ASMCA for Oracle ASM management. That is, you can configure Oracle ASM storage separately from database creation. For example, from the ASM Disk Groups page, you can create disk groups, add disks to existing disk groups, or mount disk groups that are not currently mounted.

When you start ASMCA, if the Oracle ASM instance has not been created, then ASMCA prompts you to create the instance. ASMCA prompts you for the `sysasm` password and the `ASMSNMP` password.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmca.md)

#### Configuring Preferred Mirror Read Disks in Extended Distance Clusters

You can configure preferred read disks to improve performance.

When you configure Oracle Automatic Storage Management (Oracle ASM) failure groups, it may be more efficient for a node to read from an extent that is closest to the node, even if that extent is a secondary extent. You can configure Oracle ASM to read from a secondary extent if that extent is closer to the node instead of Oracle ASM reading from the primary copy which might be farther from the node. Using preferred read failure groups is most beneficial in an extended distance cluster.

To configure this feature, set the `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter to specify a list of failure group names as preferred read disks. Oracle recommends that you configure at least one mirrored extent copy from a disk that is local to a node in an extended cluster. However, a failure group that is preferred for one instance might be remote to another instance in the same Oracle Real Application Clusters (Oracle RAC) database. The parameter setting for preferred read failure groups is instance specific.

**Related Topics**

- [Preferred Read Failure Groups](../ostmg/mirroring-diskgroup-redundancy.md)
- [ASM_PREFERRED_READ_FAILURE_GROUPS](../refrn/ASM_PREFERRED_READ_FAILURE_GROUPS.md)

#### Converting Nonclustered Oracle ASM to Clustered Oracle ASM

When installing Oracle Grid Infrastructure, any nonclustered Oracle Automatic Storage Management (Oracle ASM) instances are automatically converted to clustered Oracle ASM.

**Related Topics**

- [Preferred Read Failure Groups](../ostmg/mirroring-diskgroup-redundancy.md)

#### Administering Oracle ASM Instances with SRVCTL in Oracle RAC

You can use the Server Control Utility (SRVCTL) to add or remove an Oracle ASM instance.

To issue SRVCTL commands to manage Oracle ASM, log in as the operating system user who owns the Oracle Grid Infrastructure home and issue the SRVCTL commands from the bin directory of the Oracle Grid Infrastructure home.

Use the following syntax to add an Oracle ASM instance:

    srvctl add asm

Use the following syntax to remove an Oracle ASM instance:

    srvctl remove asm [-force]

You can also use SRVCTL to start, stop, and obtain the status of an Oracle ASM instance as in the following examples.

Use the following syntax to start an Oracle ASM instance:

    srvctl start asm [-node node_name] [-startoption start_options]

Use the following syntax to stop an Oracle ASM instance:

    srvctl stop asm [-node node_name] [-stopoption stop_options]

Use the following syntax to show the configuration of an Oracle ASM instance:

    srvctl config asm -node node_name

Use the following syntax to display the state of an Oracle ASM instance:

    srvctl status asm [-node node_name]

**Related Topics**

- [Server Control Utility Reference](server-control-utility-reference.md)
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-instance.md)
