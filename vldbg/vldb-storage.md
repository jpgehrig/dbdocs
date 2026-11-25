Storage management for the database files in a VLDB environment includes high availability, performance, and manageability aspects.

Storage performance in data warehouse environments often translates into I/O throughput (MB/s). For online transaction processing (OLTP) systems, the number of I/O requests per second (IOPS) is a key measure for performance.

This chapter discusses storage management for the database files in a VLDB environment only. Nondatabase files, including Oracle Database software, are not discussed because management of those files is no different from a non-VLDB environment. The focus is on the high availability, performance, and manageability aspects of storage systems for VLDB environments.

This chapter contains the following sections:

- High Availability

- Performance

- Scalability and Manageability

- Oracle ASM Settings Specific to VLDBs

**Note:**

Oracle Database supports the use of database files on raw devices and on file systems, and supports the use of Oracle Automatic Storage Management (Oracle ASM) on top of raw devices or logical volumes. Oracle ASM should be used whenever possible.

### 10.1 High Availability

High availability can be achieved by implementing storage redundancy.

In storage terms, these are mirroring techniques. There are three options for mirroring in a database environment:

- Hardware-based mirroring

- Using Oracle ASM for mirroring

- Software-based mirroring not using Oracle ASM

  Oracle recommends against software-based mirroring that does not use Oracle ASM.

This section contains the following topics:

- Hardware-Based Mirroring

- Mirroring Using Oracle ASM

**Note:**

In a cluster configuration, the software you use must support cluster capabilities. Oracle ASM is a cluster file system for Oracle Database files.

#### 10.1.1 Hardware-Based Mirroring

Most external storage devices provide support for different RAID (Redundant Array of Independent Disks) levels.

The most commonly used high availability hardware RAID levels in VLDB environments are RAID 1 and RAID 5. Though less commonly used in VLDB environments, other high availability RAID levels can also be used.

This section contains the following topics:

- RAID 1 Mirroring

- RAID 5 Mirroring

##### 10.1.1.1 RAID 1 Mirroring

RAID 1 is a basic mirroring technique.

Every storage block that has been written to storage is stored twice on different physical devices as defined by the RAID setup. RAID 1 provides fault tolerance because if one device fails, then there is another, mirrored, device that can respond to the request for data. The two write operations in a RAID 1 setup are generated at the storage level. RAID 1 requires at least two physical disks to be effective.

Storage devices generally provide capabilities to read either the primary or the mirror in case a request comes in, which may result in better performance compared to other RAID configurations designed for high availability. RAID 1 is the simplest hardware high availability implementation but requires double the amount of storage needed to store the data. RAID 1 is often combined with RAID 0 (striping) in RAID 0+1 configurations. In the simplest RAID 0+1 configuration, individual stripes are mirrored across two physical devices.

##### 10.1.1.2 RAID 5 Mirroring

RAID 5 requires at least 3 storage devices, but commonly 4 to 6 devices are used in a RAID 5 group.

When using RAID 5, for every data block written to a device, parity is calculated and stored on a different device. On read operations, the parity is checked. The parity calculation takes place in the storage layer. RAID 5 provides high availability for a device failure because the device's contents can be rebuilt based on the parities stored on other devices.

RAID 5 provides good read performance. Write performance may be slowed down by the parity calculation in the storage layer. RAID 5 does not require double the amount of storage but rather a smaller percentage depending on the number of devices in the RAID 5 group. RAID 5 is relatively complex and consequently, not all storage devices support a RAID 5 setup.

#### 10.1.2 Mirroring Using Oracle ASM

Oracle Automatic Storage Management (Oracle ASM) provides software-based mirroring capabilities.

Oracle ASM provides support for normal redundancy (mirroring) and high redundancy (triple mirroring). Oracle ASM also supports the use of external redundancy, in which case Oracle ASM does not perform additional mirroring. Oracle ASM normal redundancy can be compared to RAID 1 hardware mirroring.

With Oracle ASM mirroring, the mirror is produced by the database servers. Consequently, write operations require more I/O throughput when using Oracle ASM mirroring compared to using hardware-based mirroring. Depending on your configuration and the speed of the hardware RAID controllers, Oracle ASM mirroring or hardware RAID may introduce a bottleneck for data loads.

In Oracle ASM, the definition of failure groups enables redundancy, as Oracle ASM mirrors data across the boundaries of the failure group. For example, in a VLDB environment, you can define one failure group per disk array, in which case Oracle ASM ensures that mirrored data is stored on a different disk array. That way, you could not only survive a failure of a single disk in a disk array, but you could even survive the failure of an entire disk array or failure of all channels to that disk array. Hardware RAID configurations typically do not support this kind of fault tolerance.

Oracle ASM using normal redundancy requires double the amount of disk space needed to store the data. High redundancy requires triple the amount of disk space.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/mirroring-diskgroup-redundancy.md)

### 10.2 Performance

To achieve the optimum throughput from storage devices, multiple disks must work in parallel.

Optimum throughput can be achieved using a technique called striping, which stores data blocks in equisized slices (stripes) across multiple devices. Striping enables storage configurations for good performance and throughput.

Optimum storage device performance is a trade-off between seek time and accessing consecutive blocks on disk. In a VLDB environment, a 1 MB stripe size provides a good balance for optimal performance and throughput, both for OLTP systems and data warehouse systems. There are three options for striping in a database environment:

- Hardware-based striping

- Software-based striping using Oracle ASM

- Software-based striping not using Oracle ASM

It is possible to use a combination of striping techniques, but you must ensure that you physically store stripes on different devices to get the performance advantages out of striping. From a conceptual perspective, software-based striping not using Oracle ASM is very similar to hardware-based striping.

This section contains the following topics:

- Hardware-Based Striping

- Striping Using Oracle ASM

- Information Lifecycle Management

- Partition Placement

- Bigfile Tablespaces

- Oracle Database File System (DBFS)

**Note:**

In a cluster configuration, the software you use must support cluster capabilities. Oracle ASM is a cluster file system for Oracle Database files.

#### 10.2.1 Hardware-Based Striping

Most external storage devices provide striping capabilities. The most commonly used striping techniques to improve storage performance are RAID 0 and RAID 5.

This section contains the following topics:

- RAID 0 Striping

- RAID 5 Striping

##### 10.2.1.1 RAID 0 Striping

RAID 0 requires at least two devices to implement.

Data blocks written to the devices are split up and alternatively stored across the devices using the stripe size. This technique enables the use of multiple devices and multiple channels to the devices.

RAID 0, despite its RAID name, is not redundant. Loss of a device in a RAID 0 configuration results in data loss, and should always be combined with some redundancy in a critical environment. Database implementations using RAID 0 are often combined with RAID 1, basic mirroring, in RAID 0+1 configurations.

##### 10.2.1.2 RAID 5 Striping

RAID 5 configurations spread data across the available devices in the RAID group using a hardware-specific stripe size.

Consequently, multiple devices and channels are used to read and write data. Due to its more complex parity calculation, not all storage devices support RAID 5 configurations.

#### 10.2.2 Striping Using Oracle ASM

Oracle Automatic Storage Management (Oracle ASM) always stripes across all devices presented to it as a disk group.

A disk group is a logical storage pool in which you create data files. The default Oracle ASM stripe size generally is a good stripe size for a VLDB.

Use disks with the same performance characteristics in a disk group. All disks in a disk group should also be the same size for optimum data distribution and hence optimum performance and throughput. The disk group should span as many physical spindles as possible to get the best performance. The disk group configuration for a VLDB does not have to be different from the disk group configuration for a non-VLDB.

Oracle ASM can be used on top of previously striped storage devices. If you use such a configuration, then ensure that you do not introduce hot spots by defining disk groups that span logical devices which physically may be using the same resource (disk, controller, or channel to disk) rather than other available resources. Always ensure that Oracle ASM stripes are distributed equally across all physical devices.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md) for more information about Oracle ASM striping

#### 10.2.3 Information Lifecycle Management

In an Information Lifecycle Management (ILM) environment, you cannot use striping across all devices, because all data would then be distributed across all storage pools.

In an ILM environment, different storage pools typically have different performance characteristics. Tablespaces should not span storage pools, and data files for the same tablespace should not be stored in multiple storage pools.

Storage in an ILM environment should be configured to use striping across all devices in a storage pool. If you use Oracle ASM, then separate disk groups for different storage pools should be created. Using this approach, tablespaces do not store data files in different disk groups. Data can be moved online between tablespaces using partition movement operations for partitioned tables, or using the `DBMS_REDEFINITION` package when the tables are not partitioned.

**See Also:**

[Managing and Maintaining Time-Based Information](time-based-info.md) for information about Information Lifecycle Management environment

#### 10.2.4 Partition Placement

Partition placement is not a concern if you stripe across all available devices and distribute the load across all available resources.

If you cannot stripe data files across all available devices, then consider partition placement to optimize the use of all available hardware resources (physical disk spindles, disk controllers, and channels to disk).

I/O-intensive queries or DML operations should make optimal use of all available resources. Storing database object partitions in specific tablespaces, each of which uses a different set of hardware resources, enables you to use all resources for operations against a single partitioned database object. Ensure that I/O-intensive operations can use all resources by using an appropriate partitioning technique.

Hash partitioning and hash subpartitioning on a unique or almost unique column or set of columns with the number of hash partitions equal to a power of 2 is the only technique likely to result in an even workload distribution when using partition placement to optimize I/O resource utilization. Other partitioning and subpartitioning techniques may yield similar benefits depending on your application.

#### 10.2.5 Bigfile Tablespaces

Oracle Database enables the creation of bigfile tablespaces.

A bigfile tablespace consists of a single data or temporary file which can be up to 128 TB. The use of bigfile tablespaces can significantly reduce the number of data files for your database. Oracle Database supports parallel RMAN backup and restore on single data files.

Consequently, there is no disadvantage to using bigfile tablespaces and you may choose to use bigfile tablespaces to significantly reduce the number of data and temporary files.

File allocation is a serial process. If you use automatic allocation for your tables and automatically extensible data files, then a large data load can be impacted by the amount of time it takes to extend the file, regardless of whether you use bigfile tablespaces. However, if you preallocate data files and you use multiple data files, then multiple processes are spawned to add data files concurrently.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md)

#### 10.2.6 Oracle Database File System (DBFS)

Oracle Database File System (DBFS) leverages the benefits of the database to store files, and the strengths of the database in efficiently managing relational data to implement a standard file system interface for files stored in the database.

With this interface, storing files in the database is no longer limited to programs specifically written to use BLOB and CLOB programmatic interfaces. Files in the database can now be transparently accessed using any operating system (OS) program that acts on files.

Oracle Database File System (DBFS) creates a standard file system interface on top of files and directories that are stored in database tables. With DBFS, the server is the database. Files are stored as Oracle SecureFiles LOBs in a database table. A set of PL/SQL procedures implement the file system access primitives such as create, open, read, write, and list directory. The implementation of the file system in the database is called the DBFS Content Store. The DBFS Content Store allows each database user to create one or more file systems that can be mounted by clients. Each file system has its own dedicated tables that hold the file system content.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/database-file-system.md) for information about Oracle SecureFiles LOBs, stores, and Oracle Database File System

### 10.3 Scalability and Manageability

Storage scalability and management is an important factor in a VLDB environment.

A very important characteristic of a VLDB is its large size. The large size introduces the following challenges:

- Simple statistics suggest that storage components are more likely to fail because VLDBs use more components.

- A small relative growth in a VLDB may amount to a significant absolute growth, resulting in possibly many devices to be added.

- Despite its size, performance and (often) availability requirements are not different from smaller systems.

The storage configuration you choose should be able to handle these challenges. Regardless of whether storage is added or removed, deliberately or accidentally, your system should remain in an optimal state from a performance and high availability perspective.

This section contains the following topics:

- Stripe and Mirror Everything (SAME)

- SAME and Manageability

#### 10.3.1 Stripe and Mirror Everything (SAME)

The stripe and mirror everything (SAME) methodology has been recommended by Oracle for many years and is a means to optimize high availability, performance, and manageability.

To simplify the configuration further, a fixed stripe size of 1 MB is recommended in the SAME methodology as a good starting point for both OLTP and data warehouse systems. Oracle ASM implements the SAME methodology and adds automation on top of it.

#### 10.3.2 SAME and Manageability

To achieve maximum performance, the SAME methodology proposes to stripe across as many physical devices as possible.

This can be achieved without Oracle ASM, but if the storage configuration changes, for example, by adding or removing devices, then the layout of the database files on the devices should change. Oracle ASM performs this task automatically in the background. In most non-Oracle ASM environments, re-striping is a major task that often involves manual intervention.

In an ILM environment, you apply the SAME methodology to every storage pool.

### 10.4 Oracle ASM Settings Specific to VLDBs

Configuration of Oracle Automatic Storage Management for VLDBs is similar to Oracle ASM configuration for non-VLDBs.

Certain parameter values, such as the memory allocation to the Oracle ASM instance, may need a higher value.

Oracle Database supports Oracle ASM variable allocation units. Large variable allocation units are beneficial for environments that use large sequential I/O operations. VLDBs in general, and large data warehouses in particular, are good candidate environments to take advantage of large allocation units. Allocation units can be set between 1 MB and 64 MB in powers of two (that is, 1, 2, 4, 8, 16, 32, and 64). If your workload contains a significant number of queries scanning large tables, then you should use large Oracle ASM allocation units. Use 64 MB for a very large data warehouse system. Large allocation units also reduce the memory requirements for Oracle ASM and improve the Oracle ASM startup time.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-instance.md) for information about how to set up and configure Oracle ASM
