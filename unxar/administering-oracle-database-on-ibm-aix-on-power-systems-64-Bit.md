This appendix contains information about administering Oracle Database on IBM AIX on POWER Systems (64-bit).

It includes the following topics:

- Memory and Paging

- Disk Input-Output Issues

- CPU Scheduling and Process Priorities

- AIXTHREAD_SCOPE Environment Variable

- Network Information Service external naming support

- Configuring IBM Java Secure Socket Extension Provider with Oracle JDBC Thin Driver

### C.1 Memory and Paging

Memory contention occurs when processes require more memory than is available. To cope with the shortage, the system pages the programs and data between memory and disks.

This section contains the following topics:

- Kernel Parameters

- Allocating Sufficient Paging Space

- Controlling Paging

- Setting the Database Block Size

- Tuning the Log Archive Buffers

- Input-Output Buffers and SQL\*Loader

#### C.1.1 Kernel Parameters

Oracle recommends to use the default AIX kernel settings. You must adjust the kernel settings as appropriately recommended by IBM support only.

**Note:**

Adjusting the Restricted Tunables parameter without the guidance from IBM support can have an undesirable impact on the system stability and performance.

#### C.1.2 Allocating Sufficient Paging Space

Inadequate paging space (swap space) usually causes the system to stop responding or show very slow response times. On IBM AIX on POWER Systems (64-bit), you can dynamically add paging space on raw disk partitions. The amount of paging space you should configure depends on the amount of physical memory present and the paging space requirements of the applications. Use the `lsps` command to monitor paging space use and the `vmstat` command to monitor system paging activities. To increase the paging space, use the `smit pgsp` command.

If paging space is preallocated, then Oracle recommends that you set the paging space to a value larger than the amount of RAM. But on IBM AIX on POWER Systems (64-bit), paging space is not allocated until required. The system uses swap space only if it runs out of real memory. If the memory is sized correctly, then there is no paging and the page space can be small. Workloads where the demand for pages does not fluctuate significantly perform well with a small paging space. Workloads likely to have peak periods of increased paging require enough paging space to handle the peak number of pages.

As a general rule, an initial setting for the paging space is half the size of RAM plus 4 GB, up to the size of a single internal disk. Monitor the paging space use with the `lsps -a` command, and monitor the system paging activities using the `vmstat` command. The metric percent used in the output of `lsps -a` is typically less than 25 percent on a healthy system. A properly sized deployment requires very little paging space because an excessive amount of swapping severely impacts performance. Excessive use of paging space and swapping indicates that the RAM on the system may be undersized.

**Caution:**

Do not undersize the paging space. If you do, then the system terminates active processes when it runs out of space. However, oversizing the paging space has little or no negative impact.

Oracle documentation suggests the following values as a starting point for an Oracle Database:

| RAM                    | Swap Space                |
|:-----------------------|:--------------------------|
| Between 1 GB and 2 GB  | 1.5 times the size of RAM |
| Between 2 GB and 16 GB | Equal to the size of RAM  |
| More than 16 GB        | 16 GB                     |

The RAM and swap space values for Oracle Grid Infrastructure are as follows:

- Between 4 GB RAM and 16 GB RAM, the swap space must be equal to the size of RAM.

- For more than 16 GB RAM, the swap space must be equal to 16 GB.

Because the individual server environment varies, some additional memory may be warranted in an Oracle Database 19c environment, based on the increased 19c memory footprint and increasing page size from 4 KB to 64 KB. The workload may need to be rebalanced to reduce paging, which impacts system performance.

#### C.1.3 Controlling Paging

Constant and excessive paging indicates that the real memory is over-committed. In general, you should:

- Avoid constant paging unless the system is equipped with very fast expanded storage that makes paging between memory and expanded storage much faster than Oracle Database can read and write data between the SGA and disks.

- Allocate limited memory resource to where it is most beneficial to system performance. It is sometimes a recursive process of balancing the memory resource requirements and trade-offs.

- If memory is not adequate, then build a prioritized list of memory-requiring processes and elements of the system. Assign memory to where the performance gains are the greatest. A prioritized list may look like the following:

  1.  Operating System and RDBMS kernels (to include SGA and its components, buffer cache, and shared pool)

  2.  User and application processes

For example, suppose you query Oracle Database dynamic performance tables and views and find that both the shared pool and database buffer cache require more memory. Then, assigning the limited spare memory to the shared pool may be more beneficial than assigning it to the database block buffer caches. These choices depend on the nature or shape of the database load.

The following IBM AIX on POWER Systems (64-bit) commands provide paging status and statistics:

- `vmstat -s `

- `vmstat ``interval`` [``repeats``]`

- `sar -r ``interval`` [``repeats``]`

#### C.1.4 Setting the Database Block Size

You can configure Oracle Database block size for better Input-Output throughput. On IBM AIX on POWER Systems (64-bit), you can set the value of the `DB_BLOCK_SIZE` initialization parameter to between 2 KB and 32 KB, with a default of 4 KB. If Oracle Database is installed on a journaled file system, then the block size should be a multiple of the file system block size (4 KB on JFS, 16 KB to 1 MB on IBM Spectrum Scale (GPFS)). For databases on raw partitions, Oracle Database block size is a multiple of the operating system physical block size (512 bytes on IBM AIX on POWER Systems (64-bit)).

Oracle recommends smaller Oracle Database block sizes (2 KB or 4 KB) for online transaction processing or mixed workload environments and larger block sizes (8 KB, 16 KB, or 32 KB) for decision support system workload environments.

#### C.1.5 Tuning the Log Archive Buffers

By increasing the `LOG_BUFFER` size, you may be able to improve the speed of archiving the database, particularly if transactions are long or numerous. Monitor the log file Input-Output activity and system throughput to determine the optimum `LOG_BUFFER` size. Tune the `LOG_BUFFER` parameter carefully to ensure that the overall performance of normal database activity does not degrade.

For improved performance, create separate file systems for redo logs and control files (or a single file system for both), with an `agblksize` of 512 bytes rather than the default of 4 KB.

#### C.1.6 Input-Output Buffers and SQL\*Loader

For high-speed data loading, such as using the SQL\*Loader direct path option in addition to loading data in parallel, the CPU spends most of its time waiting for Input-Output to complete. By increasing the number of buffers, you can maximize CPU usage, and by doing this, increase overall throughput.

The number of buffers (set by the SQL\*Loader `BUFFERS` parameter) you choose depends on the amount of available memory and how much you want to maximize CPU usage.

The performance gains depend on CPU usage and the degree of parallelism that you use when loading data.

### C.2 Disk Input-Output Issues

Disk Input-Output contention can result from poor memory management (with subsequent paging and swapping), or poor distribution of tablespaces and files across disks.

Ensure that the Input-Output activity is distributed evenly across multiple disk drives by using IBM AIX on POWER Systems (64-bit) utilities such as `filemon`, `sar`, `iostat`, and other performance tools to identify disks with high Input-Output activity.

This section contains the following topics:

- IBM AIX on POWER Systems (64-Bit) Logical Volume Manager

- Using Journaled File Systems Compared to Raw Logical Volumes

- Using Asynchronous Input-Output

- Input-Output Slaves

- Using the DB_FILE_MULTIBLOCK_READ_COUNT Parameter

- Tuning Disk Input-Output Pacing

- Resilvering with Oracle Database

#### C.2.1 IBM AIX on POWER Systems (64-Bit) Logical Volume Manager

The IBM AIX on POWER Systems (64-bit) Logical Volume Manager can stripe data across multiple disks to reduce disk contention. The primary objective of striping is to achieve high performance when reading and writing large sequential files. With improved storage subsystems, it is no longer recommended to use LVM striping. Oracle recommends to use the default striping by the storage subsystems. The operating system is no longer aware about where the data resides physically as the LUNs presented to an AIX partition are logical and not physical.

#### C.2.2 Using Journaled File Systems Compared to Raw Logical Volumes

Address the following considerations when deciding whether to use journaled file systems or raw logical volumes:

- File systems are continually being improved, as are various file system implementations.

- Different vendors implement the file system layer in different ways to capitalize on the strengths of different disks. This makes it difficult to compare file systems across platforms.

- The Direct Input-Output and Concurrent Input-Output features included in IBM AIX on POWER Systems (64-bit) improve file system performance to a level comparable to raw logical volumes.

- In earlier versions of IBM AIX on POWER Systems (64-bit), file systems supported only buffered read and write and added extra contention because of imperfect inode locking. These two issues are solved by the JFS2 Concurrent Input-Output feature and the Spectrum Scale (GPFS)Direct Input-Output feature.

- The introduction of more powerful Logical Volume Manager interfaces substantially reduces the tasks of configuring and backing up logical disks based on raw logical volumes.

- Oracle ASM works best when you add raw disk devices to disk groups. If you are using Oracle ASM, then do not use Logical Volume Manager for striping. Oracle ASM implements striping and mirroring.

**Note:**

To use the Oracle RAC option, you must place data files on an Oracle ASM disk group or on a Spectrum Scale (GPFS) file system. You cannot use JFS or JFS2. Direct Input-Output is implicitly enabled when you use Spectrum Scale (GPFS).

##### File System Options

IBM AIX on POWER Systems (64-bit) includes Direct Input-Output and Concurrent Input-Output support. Direct Input-Output and Concurrent Input-Output support enables database files to exist on file systems while bypassing the operating system buffer cache and removing inode locking operations that are redundant with the features provided by Oracle Database.

The following table lists file systems available on IBM AIX on POWER Systems (64-bit) and the recommended setting:

| File System           | Option | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:----------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| JFS                   | dio    | Concurrent Input-Output is not available on JFS. Direct Input-Output is available, but performance is degraded compared to JFS2 with Concurrent Input-Output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| JFS large file        | none   | Oracle does not recommend using JFS large file for Oracle Database because its 128 KB alignment constraint prevents you from using Direct Input-Output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| JFS2                  | cio    | Concurrent Input-Output is a better setting than Direct Input-Output on JFS2, because it provides support for multiple concurrent readers and writers on the same file. However, due to IBM AIX on POWER Systems (64-bit) restrictions on JFS2/CIO, Concurrent Input-Output is intended to be used only with Oracle data files, control files, and log files. It should be applied only to file systems that are dedicated to such a purpose. For the same reason, the Oracle home directory is not supported on a JFS2 file system mounted with the `CIO` option. For example, during installation, if you inadvertently specify that the Oracle home directory is on a JFS2 file system mounted with the `CIO` option, then while trying to relink Oracle, you may encounter the following error:<br>`"ld: 0711-866 INTERNAL ERROR: Output symbol table size miscalculated"`<br>Note: For Oracle Database 11g Release 2 (11.2.0.2) and later, on IBM AIX on POWER Systems (64-bit) 6.1 systems and newer, Oracle recommends that you do not use the `CIO` mount option on a JFS2 file system. For the latest Oracle Database releases, it is not necessary to use the `CIO` mount option because, Oracle opens the filesystem with the `O_CIOR` option internally. This gives the benefits of `CIO` while allowing other applications to open the Oracle data files in read only mode without the `O_CIO` option. |
| Spectrum Scale (GPFS) | NA     | Oracle Database silently enables Direct Input-Output on Spectrum Scale for optimum performance. Spectrum Scale Direct Input-Output already supports multiple readers and writers on multiple nodes. Therefore, Direct Input-Output and Concurrent Input-Output are the same thing on Spectrum Scale.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

##### Considerations for JFS and JFS2

If you are placing Oracle Database logs on a JFS2 file system, then the optimal configuration is to create the file system using the `agblksize=512` option and to mount it with the `CIO` option.

Before Oracle Database 12c, Direct Input-Output and Concurrent Input-Output could not be enabled at the file level on JFS/JFS2. Therefore, the Oracle home directory and data files had to be placed in separate file systems for optimal performance. The Oracle home directory was placed on a file system mounted with default options, with the data files and logs on file systems mounted using the `DIO` or `CIO` options.

With Oracle Database 12c, you can enable Direct Input-Output and Concurrent Input-Output on JFS/JFS2 at the file level. You can do this by setting the `FILESYSTEMIO_OPTIONS` parameter in the server parameter file to `SETALL` or `DIRECTIO`. This enables Concurrent Input-Output on JFS2 and Direct Input-Output on JFS for all data file Input-Output. Because the `DIRECTIO` setting disables asynchronous Input-Output it should normally not be used. As a result of this 12c feature, you can place data files on the same JFS/JFS2 file system as the Oracle home directory and still use Direct Input-Output or Concurrent Input-Output for improved performance. As mentioned earlier, you should still place Oracle Database logs on a separate JFS2 file system for optimal performance.

**See Also:**

[Oracle Architecture and Tuning on AIX v2.30](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=oracle_architecture_and_tuning_on_aix) for more information

##### Considerations for Spectrum Scale

If you are using Spectrum Scale (GPFS), then you can use the same file system for all purposes. This includes using it for the Oracle home directory and for storing data files and logs. For optimal performance, you should use a large Spectrum Scale block size (typically, at least 512 KB). Spectrum Scale is designed for scalability, and there is no requirement to create multiple Spectrum Scale file systems as long as the amount of data fits in a single Spectrum Scale file system.

#### C.2.3 Using Asynchronous Input-Output

Oracle Database takes full advantage of asynchronous Input-Output provided by IBM AIX on POWER Systems (64-bit), resulting in faster database access.

IBM AIX on POWER Systems (64-bit) support asynchronous Input-Output for database files created on file system partitions. When using asynchronous Input-Output on file systems, the kernel database processes (`aioserver`) control each request from the time a request is taken off the queue to the time it is completed. The number of `aioserver` servers determines the number of asynchronous Input-Output requests that can be processed in the system concurrently. There is no need to adjust the AIO tunables as the defaults for AIO tunables have been significantly increased.

#### C.2.4 Input-Output Slaves

Input-Output Slaves are specialized Oracle processes that perform only Input-Output. They are rarely used on IBM AIX on POWER Systems (64-bit), because asynchronous Input-Output is the default and recommended way for Oracle to perform Input-Output operations on IBM AIX on POWER Systems (64-bit). Input-Output Slaves are allocated from shared memory buffers. Input-Output Slaves use the initialization parameters listed in the following table:

| Parameter               | Range of Values | Default Value |
|:------------------------|:----------------|:--------------|
| `DISK_ASYNCH_IO`        | `true`/`false`  | `true`        |
| `TAPE_ASYNCH_IO`        | `true`/`false`  | `true`        |
| `BACKUP_TAPE_IO_SLAVES` | `true`/`false`  | `false`       |
| `DBWR_IO_SLAVES`        | 0 - 999         | 0             |
| `DB_WRITER_PROCESSES`   | 1-20            | 1             |

Generally, you do not adjust the parameters in the preceding table. However, on large workloads, the database writer may become a bottleneck. If it does, then increase the value of `DB_WRITER_PROCESSES`. As a general rule, do not increase the number of database writer processes above one for each pair of CPUs in the system or partition.

There are times when you must turn off asynchronous I/O. For example, if instructed to do so by Oracle Support for debugging. You can use the `DISK_ASYNCH_IO` and `TAPE_ASYNCH_IO` parameters to switch off asynchronous I/O for disk or tape devices. `TAPE_ASYNCH_IO` support is only available when the Media Manager software supports it and for Recovery Manager, if `BACKUP_TAPE_IO_SLAVES` is true.

Set the `DBWR_IO_SLAVES` parameter to greater than 0 only if the `DISK_ASYNCH_IO` parameter is set to `false`. Otherwise, the database writer process becomes a bottleneck. In this case, the optimal value on IBM AIX on POWER Systems (64-bit) for the `DBWR_IO_SLAVES` parameter is 4.

#### C.2.5 Using the DB_FILE_MULTIBLOCK_READ_COUNT Parameter

When using Direct Input-Output or Concurrent Input-Output with Oracle Database 19c, the IBM AIX on POWER Systems (64-bit) file system does not perform any read-ahead on sequential scans. For this reason the `DB_FILE_MULTIBLOCK_READ_COUNT` value in the server parameter file should be increased when Direct Input-Output or Concurrent Input-Output is enabled on Oracle data files. The read ahead is performed by Oracle Database as specified by the `DB_FILE_MULTIBLOCK_READ_COUNT` initialization parameter.

Setting a large value for the `DB_FILE_MULTIBLOCK_READ_COUNT` initialization parameter usually yields better Input-Output throughput on sequential scans. On IBM AIX on POWER Systems (64-bit), this parameter ranges from 1 to 512, but using a value higher than 16 usually does not provide additional performance gain.

Set this parameter so that its value when multiplied by the value of the `DB_BLOCK_SIZE` parameter produces a number larger than the Logical Volume Manager stripe size. Such a setting causes more disks to be used.

#### C.2.6 Tuning Disk Input-Output Pacing

Disk Input-Output pacing is an IBM AIX on POWER Systems (64-bit) mechanism that enables the system administrator to limit the number of pending Input-Output requests to a file. This prevents disk Input-Output intensive processes from saturating the CPU. Therefore, the response time of interactive and CPU-intensive processes does not deteriorate.

You can achieve disk Input-Output pacing by adjusting two system parameters: the high-water mark and the low-water mark. When a process writes to a file that already has a pending high-water mark Input-Output request, the process is put to sleep. The process wakes up when the number of outstanding Input-Output requests falls lower than or equals the low-water mark.

Starting from IBM AIX 6.1 version, the file systems and AIX I/O subsystem are modified to accommodate large surges of file system I/O. In addition to these changes, the default values for I/O pacing have been modified. The default values for IBM AIX 6.1 version and earlier was 0 to no I/O pacing. The default values for IBM AIX 6.1 version and later are as follows:

- `minpout`=4096

- `maxpout`=8193

#### C.2.7 Resilvering with Oracle Database

If you disable mirror write consistency for an Oracle data file allocated on a raw logical volume, then the Oracle Database crash recovery process uses resilvering to recover after a system failure. This resilvering process prevents database inconsistencies or corruption.

During crash recovery, if a data file is allocated on a logical volume with multiple copies, then the resilvering process performs a checksum on the data blocks of all the copies. It then performs one of the following:

- If the data blocks in a copy have valid checksums, then the resilvering process uses that copy to update the copies that have invalid checksums.

- If all copies have blocks with invalid checksums, then the resilvering process rebuilds the blocks using information from the redo log file. It then writes the data file to the logical volume and updates all the copies.

On IBM AIX on POWER Systems (64-bit), the resilvering process works only for data files allocated on raw logical volumes for which mirror write consistency is disabled. Resilvering is not required for data files on mirrored logical volumes with mirror write consistency enabled, because mirror write consistency ensures that all copies are synchronized.

If the system fails while you are upgrading an earlier release of Oracle Database that used data files on logical volumes for which mirror write consistency was disabled, then run the `syncvg` command to synchronize the mirrored logical volume before starting Oracle Database. If you do not synchronize the mirrored logical volume before starting the database, then Oracle Database may read incorrect data from a logical volume copy.

**Note:**

If a disk drive fails, then resilvering does not occur. You must run the `syncvg` command before you can reactivate the logical volume.

**Caution:**

Oracle supports resilvering for data files only. Do not disable mirror write consistency for redo log files.

### C.3 CPU Scheduling and Process Priorities

The CPU is another system component for which processes may contend. Although the IBM AIX on POWER Systems (64-bit) kernel allocates CPU effectively most of the time, many processes compete for CPU cycles. If the system has multiple CPU (SMP), then there may be different levels of contention on each CPU.

### C.4 AIXTHREAD_SCOPE Environment Variable

Oracle recommends using IBM AIX 7.1 version and IBM AIX 6.1 default (system wide scope) setting of the `AIXTHREAD_SCOPE` environment variable to `S (1:1)`.

**See Also:**

[Thread tuning](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=aix_thread_tuning) for additional information about thread tuning

### C.5 Network Information Service external naming support

Network Information Service external naming adapter is supported on IBM AIX on POWER Systems (64-bit). To configure and use Network Information Service external naming, refer to [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md).

### C.6 Configuring IBM Java Secure Socket Extension Provider with Oracle JDBC Thin Driver

IBM Java 1.6 SR 16 is shipped with Oracle Database 12c Release 1 (12.1). If you want to configure SSL on IBM JDK, then you may face the following issues:

- IBM JSSE does not support `SSLv2Hello` SSL protocol. However, it accepts the `SSLv2Hello` message from the client encapsulating

  `SSLv3` or `TLS1.0` hello message.

  For SSL clients using Thin JDBC connectors, you must set `oracle.net.ss1_version` system property to select `TLSv1` SSL protocol or `SSLv3` SSL protocol since `SSLv3` is not recommended anymore after the `POODLE` security issue. System property recommendation is to set `TLSV1.0`, `TLSV1.1`, and `TLSV1.2` on recommending `SSLv3`, or the connection will fail.

- IBM JSSE does not allow anonymous ciphers

  For SSL clients using anonymous ciphers, you must replace the Default Trust Manager with a Custom Trust Manager that accepts anonymous ciphers.

**See Also:**

- [Padding Oracle On Downgraded Legacy Encryption (POODLE) security vulnerability](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=poodle_security_vulnerability) for more information

- IBM JSSE documentation for more information about creating and installing Custom Trust Manager
