This chapter describes how to tune Oracle Database. It contains the following sections:

- Importance of Tuning

- Operating System Tools

- Tuning Memory Management

- Tuning Disk Input-Output

- Monitoring Disk Performance

- System Global Area

- Tuning the Operating System Buffer Cache

### 8.1 Importance of Tuning

The intent of this section is to efficiently tune and optimize the performance of Oracle Database. Frequent tuning enhances system performance and prevents data bottlenecks.

Before tuning the database, you must observe its normal behavior by using the tools described in the "Operating System Tools" section.

### 8.2 Operating System Tools

Several operating system tools are available to enable you to assess database performance and determine database requirements. In addition to providing statistics for Oracle processes, these tools provide statistics for CPU usage, interrupts, swapping, paging, context switching, and I/O for the entire system.

This section provides information about the following common tools:

- vmstat

- sar

- iostat

- swap\_ swapinfo\_ swapon\_ or lsps

- Oracle Solaris Tools

- Linux Tools

- IBM AIX on POWER Systems (64-Bit) Tools

- HP-UX Tools

**See Also:**

The operating system documentation and man pages for more information about these tools

#### 8.2.1 vmstat

vmstat reports information about processes, memory, paging, block IO, traps, and cpu activity.

Use the `vmstat` command to view process, virtual memory, disk, trap, and CPU activity, depending on the switches that you supply with the command. Run one of the following commands to display a summary of CPU activity six times, at five-second intervals:

- On Oracle Solaris and HP-UX:

      $ vmstat -S 5 6

  **Note:**

  The `-S` option displays the swapping statistics.

- On Linux and IBM AIX on POWER Systems (64-bit):

      $ vmstat 5 6

The following is a sample output of this command on Linux:

    procs          memory                  swap      io      system       cpu
    r b     swpd   free   buff  cache      si so    bi bo   in  cs us   sy id wa st
    0 0    130668 103604 198144 5029000     0 0     1 68     8   6  0   0 100 0  0
    0 0    130668 103604 198144 5029000     0 0     0 86    226 352 0   0 100 0  0
    0 0    130668 103604 198148 5029000     0 0     0 58    223 357 0   0 100 0  0
    0 0    130668 103604 198152 5029004     0 0     0 68    223 358 0   0 100 0  0
    0 0    130668 103604 198152 5029004     0 0     0 56    223 357 0   0 100 0  0
    0 0    130668 103604 198152 5029004     0 0     0 57    228 362 0   0 100 0  0

The following is a sample output of the `$ vmstat -S 1 2` command on HP-UX:

    procs     memory             page             faults       cpu
    r b w   avm    free    si so pi po fr de sr  in    sy    cs us sy id
    1 0 0  112085 2189167  0  0  3  0  0  0  1  1033  32186 108  1  0  98
    1 0 0  112085 2189074  0  0  4  0  0  0  0  1022   508   60  0  0 100

The `w` sub column, under the `procs` column, shows the number of potential processes that have been swapped out and written to disk. If the value is not zero, then swapping occurs and the system is short of memory.

For HP-UX and Oracle Solaris, the `si` and `so` columns under the `page` column indicate the number of processes swapped-in and swapped-out per second, respectively. Ideally these values should be zero.

For Linux, the `si` and `so` columns represent amount of memory swapped-in and swapped-out.

The `sr` column under the `page` column indicates the scan rate. High scan rates are caused by a shortage of available memory.

The `pi` and `po` columns under the `page` column indicate the number of page-ins and page-outs per second, respectively. It is normal for the number of page-ins and page-outs to increase. Some paging always occurs even on systems with sufficient available memory.

**See Also:**

Refer to the vmstat man page for your platform for information about interpreting the output

#### 8.2.2 sar

Depending on the switches that you supply with the command, use the `sar` (system activity reporter) command to display cumulative activity counters in the operating system.

On UNIX systems, the following command displays a summary of the input and output activity every ten seconds:

    $ sar -b 10 10

The following example shows the output of this command on a Linux system:

    10:28:01       tps      rtps      wtps   bread/s   bwrtn/s
    10:28:11     17.20      0.00     17.20      0.00    300.80
    10:28:21     46.40      0.00     46.40      0.00    467.20
    10:28:31     16.40      0.00     16.40      0.00    283.20
    10:28:41     15.60      0.00     15.60      0.00    275.20
    10:28:51     17.02      0.00     17.02      0.00    254.65
    10:29:01     35.80      0.00     35.80      0.00    414.40
    10:29:11     15.80      0.00     15.80      0.00    273.60
    10:29:21     17.40      0.00     17.40      0.00    262.40
    10:29:31     32.20      0.00     32.20      0.00    406.40
    10:29:41     20.98      0.00     20.98      0.00    354.85

    Average:        23.48      0.00     23.48      0.00    329.28

The `sar` output provides a snapshot of system input and output activity at a given point in time. If you specify the interval time with multiple options, then the output can become difficult to read. If you specify an interval time of less than 5, then the `sar` activity itself can affect the output.

**See Also:**

The man page for more information about `sar`

#### 8.2.3 iostat

Use the `iostat` command to view terminal and disk activity, depending on the switches that you supply with the command. The output from the `iostat` command does not include disk request queues, but it shows which disks are busy. You can use this information to balance the Input-Output loads.

The following command displays terminal and disk activity five times, at five-second intervals:

    $ iostat 5 5

The following is sample output of the command on Oracle Solaris:

    tty          blkdev0           sd1           sd2           sd3          cpu
     tin tout kps tps serv  kps tps serv  kps tps serv  kps tps serv  us sy st id
       0    1   0   0    0    0   0   31    0   0   18    3   0   42   0  0  0 99
       0   16   0   0    0    0   0    0    0   0    0    1   0   14   0  0  0 100
       0   16   0   0    0    0   0    0    0   0    0    0   0    0   0  0  0 100
       0   16   0   0    0    0   0    0    0   0    0    0   0    0   0  0  0 100
       0   16   0   0    0    0   0    0    2   0   14   12   2   47   0  0  1 98

Use the `iostat` command to look for large disk request queues. A request queue shows how long the Input-Output requests on a particular disk device must wait to be serviced. Request queues are caused by a high volume of Input-Output requests to that disk or by Input-Output with long average seek times. Ideally, disk request queues should be at or near zero.

#### 8.2.4 swap, swapinfo, swapon, or lsps

Use the `swap`, `swapinfo`, `swapon`, or `lsps` command to report information about swap space usage. A shortage of swap space can stop processes to respond, leading to process failures with `Out of Memory` errors. The following table lists the appropriate command to use for each platform:

| Platform                          | Command                                            |
|:----------------------------------|:---------------------------------------------------|
| Oracle Solaris                    | `swap -lh` , `swap -sh`, and `zfs list rpool/swap` |
| Linux                             | `swapon -s`                                        |
| IBM AIX on POWER Systems (64-bit) | `lsps -a`                                          |
| HP-UX                             | `swapinfo -m`                                      |

The following example shows sample output from the `swap -l` command on Oracle Solaris:

    swapfile                     dev     swaplo    blocks     free
    /dev/zvol/dsk/rpool/swap    274,1      8       20971447    20971447

#### 8.2.5 Oracle Solaris Tools

On Oracle Solaris systems, use the `mpstat` command to view statistics for each processor in a multiprocessor system. Each row of the table represents the activity of one processor. The first row summarizes all activity since the last system restart. Each subsequent row summarizes activity for the preceding interval. All values are events per second unless otherwise noted. The arguments are for time intervals between statistics and number of iterations.

The following example shows sample output from the `mpstat` command:

    CPU minf mjf xcal  intr ithr  csw icsw migr smtx  srw syscl  usr sys  st idl
      0   3   0    2    319  103  109    0  19   11    0   73     0   1   0  99
      1   4   0    1    71   1     95    0  14   12    0   96     0   0   0  99

#### 8.2.6 Linux Tools

On Linux systems, use the `top`, `free`, and `cat /proc/meminfo` commands to view information about swap space, memory, and buffer usage.

#### 8.2.7 IBM AIX on POWER Systems (64-Bit) Tools

The following sections describe tools available on IBM AIX on POWER Systems (64-bit):

- Base Operation System Tools

- Performance Toolbox

- System Management Interface Tool

**See Also:**

The IBM AIX on POWER Systems (64-bit) operating system documentation and man pages for more information about these tools

##### 8.2.7.1 Base Operation System Tools

The IBM AIX on POWER Systems (64-bit) Base Operation System contains performance tools that are historically part of UNIX systems or are required to manage the implementation-specific features of IBM AIX on POWER Systems (64-bit). The following table lists the most important Base Operation System tools.

| Tool      | Function                                                                                           |
|:----------|:---------------------------------------------------------------------------------------------------|
| `lsattr`  | Displays the attributes of devices                                                                 |
| `lslv`    | Displays information about a logical volume or the logical volume allocations of a physical volume |
| `netstat` | Displays the contents of network-related data structures                                           |
| `nfsstat` | Displays statistics about Network File System and Remote Procedure Call activity                   |
| `nice`    | Changes the initial priority of a process                                                          |
| `no`      | Displays or sets network options                                                                   |
| `ps`      | Displays the status of one or more processes                                                       |
| `reorgvg` | Reorganizes the physical-partition allocation within a volume group                                |
| `time`    | Displays the elapsed execution, user CPU processing, and system CPU processing time                |
| `trace`   | Records and reports selected system events                                                         |
| `vmo`     | Manages Virtual Memory Manager tunable parameters                                                  |

##### 8.2.7.2 Performance Toolbox

The IBM AIX on POWER Systems (64-bit) Performance Toolbox contains tools for monitoring and tuning system activity locally and remotely. The Performance Tool Box consists of two main components, the Performance Tool Box Manager and the Performance Tool Box Agent. The Performance Tool Box Manager collects and displays data from various systems in the configuration by using the `xmperf` utility. The Performance Tool Box Agent collects and transmits data to the Performance Tool Box Manager by using the `xmserd` daemon. The Performance Tool Box Agent is also available as a separate product called Performance Aide for IBM AIX on POWER Systems (64-bit).

Both Performance Tool Box and Performance Aide include the monitoring and tuning tools listed in the following table:

| Tool        | Description                                                                              |
|:------------|:-----------------------------------------------------------------------------------------|
| `fdpr`      | Optimizes an executable program for a particular workload                                |
| `filemon`   | Uses the trace facility to monitor and report the activity of the file system            |
| `fileplace` | Displays the placement of blocks of a file within logical or physical volumes            |
| `lockstat`  | Displays statistics about contention for kernel locks                                    |
| `lvedit`    | Facilitates interactive placement of logical volumes within a volume group               |
| `netpmon`   | Uses the trace facility to report on network Input-Output and network-related CPU usage  |
| `rmss`      | Simulates systems with various memory sizes for performance testing                      |
| `svmon`     | Captures and analyzes information about virtual-memory usage                             |
| `syscalls`  | Records and counts system calls                                                          |
| `tprof`     | Uses the `trace` facility to report CPU usage at module and source-code-statement levels |
| `BigFoot`   | Reports the memory access patterns of processes                                          |
| `stem`      | Permits subroutine-level entry and exit instrumentation of existing executables          |

**See Also:**

- Performance Toolbox Version 2 and 3 Guide and Reference for information about these tools

- AIX 5L Performance Management Guide for information about the syntax of some of these tools

##### 8.2.7.3 System Management Interface Tool

The IBM AIX on POWER Systems (64-bit) System Management Interface Tool (SMIT) provides a menu-driven interface to various system administrative and performance tools. By using SMIT, you can navigate through large numbers of tools and focus on the jobs that you want to perform.

#### 8.2.8 HP-UX Tools

The following performance analysis tools are available on HP-UX systems:

- GlancePlus/UX

  This HP-UX utility is an online diagnostic tool that measures the activities of the system. GlancePlus displays information about how system resources are used. It displays dynamic information about the system Input-Output, CPU, and memory usage on a series of screens. You can use the utility to monitor how individual processes are using resources.

- HP Programmer's Analysis Kit

  HP Programmer's Analysis Kit consists of the following tools:

  - Puma

    This tool collects performance statistics during a program run. It provides several graphical displays for viewing and analyzing the collected statistics.

  - Thread Trace Visualizer

    This tool displays trace files produced by the instrumented thread library, `libpthread_tr.sl`, in a graphical format. It enables you to view how threads are interacting and to find where threads are blocked waiting for resources.

    HP Programmer's Analysis Kit is bundled with the HP Fortran 77, HP Fortran 90, HP C, HP C++, HP ANSI C++, and HP Pascal compilers.

    The following table lists the performance tuning tools that you can use for additional performance tuning on HP-UX:

    | Tool                     | Description                                                                                                                                                                                                                                                                  |
    |:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `caliper` (Itanium only) | Collects run-time application data for system analysis tasks such as cache misses, translation look-aside buffer or instruction cycles, along with fast dynamic instrumentation. It is a dynamic performance measurement tool for C, C++, Fortran, and assembly applications |
    | `gprof`                  | Creates an execution profile for programs                                                                                                                                                                                                                                    |
    | `monitor`                | Monitors the program counter and calls to certain functions                                                                                                                                                                                                                  |
    | `netfmt`                 | Monitors the network                                                                                                                                                                                                                                                         |
    | `netstat`                | Reports statistics on network performance                                                                                                                                                                                                                                    |
    | `nfsstat`                | Displays statistics about Network File System and Remote Procedure Call activity                                                                                                                                                                                             |
    | `nettl`                  | Captures network events or packets by logging and tracing                                                                                                                                                                                                                    |
    | `prof`                   | Creates an execution profile of C programs and displays performance statistics for the program, showing where the program is spending most of its execution time                                                                                                             |
    | `profil`                 | Copies program counter information into a buffer                                                                                                                                                                                                                             |
    | `top`                    | Displays the top processes on the system and periodically updates the information                                                                                                                                                                                            |

### 8.3 Tuning Memory Management

Start the memory tuning process by measuring paging and swapping space to determine how much memory is available. After you determine the system memory usage, tune the Oracle buffer cache.

The Oracle buffer manager ensures that the most frequently accessed data is cached longer. If you monitor the buffer manager and tune the buffer cache, then you can significantly improve Oracle Database performance. The optimal Oracle Database buffer size for the system depends on the overall system load and the relative priority of Oracle Database over other applications.

This section includes the following topics:

- Allocating Sufficient Swap Space

- Monitoring Paging

- Adjusting Oracle Block Size

- Allocating Memory Resource

#### 8.3.1 Allocating Sufficient Swap Space

Try to minimize swapping because it causes significant operating system overhead. To check for swapping, use the `sar` or `vmstat` commands. For information about the appropriate options to use with these commands, refer to the man pages.

If the system is swapping and you must conserve memory, then:

- Avoid running unnecessary system daemon processes or application processes.

- Decrease the number of database buffers to free some memory.

- Decrease the number of operating system file buffers.

To determine the amount of swap space, run one of the following commands, depending on the platform:

| Platform                          | Command                                                |
|:----------------------------------|:-------------------------------------------------------|
| Oracle Solaris                    | `swap -l`, `swap -s`, and `zfs get volsize rpool/swap` |
| Linux                             | `swapon -s`                                            |
| IBM AIX on POWER Systems (64-bit) | `lsps -a`                                              |
| HP-UX                             | `swapinfo -m`                                          |

Monitor the use of swap space, and increase it as required. The following table describes the initially recommended relationship between installed RAM and the configured swap space requirement:

| RAM                    | Swap Space                |
|:-----------------------|:--------------------------|
| Between 1 GB and 2 GB  | 1.5 times the size of RAM |
| Between 2 GB and 16 GB | Equal to the size of RAM  |
| More than 16 GB        | 16 GB                     |

To add swap space to the system, run one of the following commands, depending on the platform:

| Platform                          | Command                                                                                                                                                                                                                                                                                                                  |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Solaris                    | Use one of the following options:<br>• For a ZFS file system, extend the swap volume using the following command:<br>• `zfs set volsize=``newsize` `rpool/swap`<br>• where `newsize` is the size of the swap volume that you want to increase.<br>• For a non-ZFS file system, use the following command:<br>• `swap -a` |
| Linux                             | `swapon -a`                                                                                                                                                                                                                                                                                                              |
| IBM AIX on POWER Systems (64-bit) | `chps` or `mkps`                                                                                                                                                                                                                                                                                                         |
| HP-UX                             | `swapon`                                                                                                                                                                                                                                                                                                                 |

**See Also:**

- [My Oracle Support note 1587357.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1587357.1)

- The operating system documentation for more information about these commands

**Note:**

Starting with 12c, Oracle Database uses the Optimized Shared Memory (OSM) model of Oracle Solaris to implement Automatic Memory Management. Unlike DISM, OSM does not require the double allocation of swap disk space. For swap space requirements refer to the following note:

[My Oracle Support note 1010818.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1010818.1)

#### 8.3.2 Monitoring Paging

Paging may not present as serious a problem as swapping, because an entire program does not have to be stored in memory to run. A small number of page-outs may not noticeably affect the performance of the system.

To detect excessive paging, run measurements during periods of fast response or idle time to compare against measurements from periods of slow response.

Use the `vmstat` or `sar` command to monitor paging.

**See Also:**

The man pages or the operating system documentation for information about interpreting the results for the platform

In Oracle Solaris, `vmstat —p` indicates the number of address translation page faults. Address translation faults occur when a process refers to a valid page not in memory.

Analyzing memory related issues should start with checking the amount of free memory in the `vmstat` output. If free memory is low, then the `sr` (scan rate) column should be checked for non-zero values. This indicates that the page scanner is scanning memory pages to put back on the free list to be reused.

Anonymous (bad) paging can be observed in the `vmstat -p` command output under the `api` (anonymous page-in) and `apo` (anonymous page-out) columns. This kind of paging takes place when the system moves anonymous pages to the swap device during a memory shortage.

If the system consistently has excessive page-out activity, then consider the following solutions:

- Install more memory.

- Move some work to another system.

- Configure the System Global Area (SGA) to use less memory.

**Related Topics**

- [MOS Document: 1007494.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1007494.1)

#### 8.3.3 Adjusting Oracle Block Size

During read operations, entire operating system blocks are read from the disk. If the database block size is smaller than the operating system file system block size, then Input-Output bandwidth is inefficient. If you set Oracle Database block size to be a multiple of the file system block size, then you can increase performance by up to 5 percent.

The `DB_BLOCK_SIZE` initialization parameter sets the database block size. However, to change the value of this parameter, you must re-create the database.

To see the current value of the `DB_BLOCK_SIZE` parameter, run the `SHOW PARAMETER` `DB_BLOCK_SIZE` command in SQL\*Plus.

#### 8.3.4 Allocating Memory Resource

You can set parameters to automatically allocate memory based on the demands of workload and the requirements of various database instances running on the same system. The `MEMORY_TARGET` parameter specifies the Oracle systemwide usable memory for that instance and automatically tunes SGA and Process Global Area (PGA) components. The `MEMORY_MAX_TARGET` parameter identifies the value up to which the `MEMORY_TARGET` parameter can grow dynamically.

By default, the value for both these parameters is zero and there is no auto-tuning. You can activate auto-tuning by setting the `MEMORY_TARGET` parameter to a nonzero value. To dynamically enable the `MEMORY_TARGET` parameter, the `MEMORY_MAX_TARGET` parameter must be set at startup.

**Note:**

If you just set the `MEMORY_TARGET` parameter to a nonzero value, the `MEMORY_MAX_TARGET` parameter automatically acquires this value.

The `MEMORY_TARGET` and `MEMORY_MAX_TARGET` parameters are only supported on Linux, Oracle Solaris, HP-UX, and IBM AIX on POWER Systems (64-bit) platforms.

On Oracle Solaris, Dynamic Intimate Shared Memory is enabled for `MEMORY_TARGET` or `MEMORY_MAX_TARGET`. For more information, refer to [“Administering Oracle Database on Oracle Solaris”](administering-oracle-database-on-oracle-solaris.md) section.

On Linux, some shared resource requirements are increased when `MEMORY_TARGET` or `MEMORY_MAX_TARGET` are enabled. For more information, refer to the "[Allocating Shared Resources](administering-oracle-database-on-linux.md)" section.

**Tip:**

You can set the `MEMORY_TARGET` and `MEMORY_MAX_TARGET` parameters based on original setup, memory available for Oracle on the computer, and workload memory requirements.

### 8.4 Tuning Disk Input-Output

Balance Input-Output evenly across all available disks to reduce disk access times. For smaller databases and those not using RAID, ensure that different data files and tablespaces are distributed across the available disks.

This section contains the following topics:

- Using Automatic Storage Management

- Choosing the Appropriate File System Type

#### 8.4.1 Using Automatic Storage Management

If you choose to use Automatic Storage Management for database storage, then all database Input-Output is balanced across all available disk devices in the Automatic Storage Management disk group.

By using Automatic Storage Management, you avoid manually tuning disk Input-Output.

#### 8.4.2 Choosing the Appropriate File System Type

Depending on the operating system, you can choose from a range of file system types. Each file system type has different characteristics. This fact can have a substantial impact on database performance. The following table lists common file system types:

| File System | Platform                                                     | Description                             |
|:------------|:-------------------------------------------------------------|:----------------------------------------|
| ZFS         | Oracle Solaris                                               | Oracle Solaris ZFS file system          |
| S5          | HP-UX                                                        | UNIX System V file system               |
| UFS         | Oracle Solaris, IBM AIX on POWER Systems (64-bit), and HP-UX | Unix file system, derived from BSD UNIX |
| VxFS        | Oracle Solaris, IBM AIX on POWER Systems (64-bit), and HP-UX | VERITAS file system                     |
| ext2/ext3   | Linux                                                        | Extended file system for Linux          |
| OCFS2       | Linux                                                        | Oracle cluster file system              |
| JFS/JFS2    | IBM AIX on POWER Systems (64-bit)                            | Journaled file system                   |
| GPFS        | IBM AIX on POWER Systems (64-bit)                            | General parallel file system            |

The suitability of a file system for an application is usually not documented. For example, even different implementations of the UFS are hard to compare. Depending on the file system that you choose, performance differences can be up to 20 percent. If you choose to use a file system, then:

- Make a new file system partition to ensure that the hard disk is clean and unfragmented.

- Perform a file system check on the partition before using it for database files.

- Distribute disk Input-Output as evenly as possible.

- If you are not using a logical volume manager or a RAID device, then consider placing log files on a different file system from data files.

**See Also:**

"Tuning ZFS for Database Products" in Oracle Solaris 11.3 Tunable Parameters Reference Manual for more information on tuning ZFS for Oracle Database

.

### 8.5 Monitoring Disk Performance

The following sections describe the procedure for monitoring disk performance:

- Monitoring Disk Performance on Other Operating Systems

- Using Disk Resync to Monitor Automatic Storage Management Disk Group

#### 8.5.1 Monitoring Disk Performance on Operating Systems

To monitor disk performance, use the `sar -b` and `sar -u` commands.

The following table describes the columns of the `sar -b` command output that are significant for analyzing disk performance:

| Columns              | Description                                                                                       |
|:---------------------|:--------------------------------------------------------------------------------------------------|
| `bread/s`, `bwrit/s` | Blocks read and blocks written per second (important for file system databases)                   |
| `pread/s`, `pwrit/s` | Number of I/O operations per second on raw devices (important for raw partition database systems) |

Key indicators are:

- The sum of the `bread`, `bwrit`, `pread`, and `pwrit` column values indicates the level of activity of the disk Input-Output subsystem. The higher the sum, the busier the Input-Output subsystem. The larger the number of physical drives, the higher the sum threshold number can be.

- The `%rcache` column value should be greater than 90 and the `%wcache` column value should be greater than 60. Otherwise, the system may be disk Input-Output bound.

#### 8.5.2 Using Disk Resync to Monitor Automatic Storage Management Disk Group

Use the `alter diskgroup disk online` and `alter diskgroup disk offline` commands to temporarily suspend Input-Output to a set of disks. You can use these commands to perform regular maintenance tasks or upgrades such as disk firmware upgrade. If transient failures occur on some disks in a disk group, then use `alter diskgroup disk online` to quickly recover the disk group.

### 8.6 System Global Area

The SGA is the Oracle structure that is located in shared memory. It contains static data structures, locks, and data buffers.

The maximum size of a single shared memory segment is specified by the `shmmax` kernel parameter.

The following table shows the recommended value for this parameter, depending on the platform:

| Platform                          | Recommended Value                                                                                                     |
|:----------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| Oracle Solaris                    | 4294967295 or 4 GB minus 16 MB                                                                                        |
| Linux                             | Minimum of the following values:<br>• Half the size of the physical memory installed on the system<br>• 4 GB - 1 byte |
| IBM AIX on POWER Systems (64-bit) | NA                                                                                                                    |
| HP-UX                             | The size of the physical memory installed on the system                                                               |

If the size of the SGA exceeds the maximum size of a shared memory segment (`shm``max` or `shm``_max`), then Oracle Database attempts to attach more contiguous segments to fulfill the requested SGA size. The `shm``seg` kernel parameter specifies the maximum number of segments that can be attached by any process. Set the following initialization parameters to control the size of the SGA:

- `DB_CACHE_SIZE`

- `DB_BLOCK_SIZE`

- `JAVA_POOL_SIZE`

- `LARGE_POOL_SIZE`

- `LOG_BUFFERS`

- `SHARED_POOL_SIZE`

Alternatively, set the `SGA_TARGET` initialization parameter to enable automatic tuning of the SGA size.

Use caution when setting values for these parameters. When values are set too high, too much of the physical memory is devoted to shared memory. This results in poor performance.

An Oracle Database configured with Shared Server requires a higher setting for the `SHARED_POOL_SIZE` initialization parameter, or a custom configuration that uses the `LARGE_POOL_SIZE` initialization parameter. If you installed the database with Oracle Universal Installer, then the value of the `SHARED_POOL_SIZE` parameter is set automatically by Oracle Database Configuration Assistant. However, if you created a database manually, then increase the value of the `SHARED_POOL_SIZE` parameter in the parameter file by 1 KB for each concurrent user.

Sufficient shared memory must be available to each Oracle process to address the entire SGA:

- Determining the Size of the SGA

- System Resource Verifier Utility

- Guidelines for Setting Semaphore Parameters

- Shared Memory on IBM AIX on POWER Systems (64-Bit)

#### 8.6.1 Determining the Size of the SGA

You can determine the SGA size in one of the following ways:

- Run the following SQL\*Plus command to display the size of the SGA for a running database:

      SQL> SHOW SGA

  The result is shown in bytes.

- Start the database instance to view the size of the SGA displayed next to the Total System Global Area heading.

- Run the `ipcs` command as the `oracle` user.

#### 8.6.2 System Resource Verifier Utility

The System Resource Verifier utility (`sysresv`) is available with Oracle8`i` and later releases. It provides Oracle instance and operating system resource information for the Oracle system identifiers (`ORACLE_SID`) that you specify. This utility is located in `$ORACLE_HOME/bin`, but it can be used from other locations.

##### 8.6.2.1 Purpose of the sysresv Utility

Use the `sysresv` utility to display the status of an Oracle instance and identify the operating system resources it uses, such as the memory and semaphore parameters. This utility is especially useful when multiple instances are running. For example, if an instance is not responsive, then you can use this utility to remove operating system resources.

You can use this utility when an Oracle instance has crashed or was aborted, and memory and semaphores related to this instance were not cleaned up automatically. This utility is also useful in determining which Oracle instance is running.

##### 8.6.2.2 Preconditions for Using sysresv

To use the `sysresv` utility, you must have access to the System Global Area (SGA). To access the SGA, you must be the Oracle owner or a member of the group that owns the Oracle binary.

##### 8.6.2.3 Syntax for sysresv

The syntax for the `sysresv` utility is as follows:

    sysresv [-i] [-f] [-d on|off] [-l sid1[ sid2 ...]]

Where:

- `-i` Prompt before removing IPC resources for each `sid`

- `-f` Remove IPC resources without prompting for confirmation. This flag overrides the `-i `option

- `-d on|off `List IPC resources for each `sid` if on. If not specified, the default for `-d` is on

- `-l sid1 [sid2 sid3]` run the `sysresv` check against one or more space-delimited system identifiers

If `sysresv` is used without flags, then it reports IPC resources for the Oracle instance identified by the `$ORACLE_SID` environment variable in the Oracle installation owner user profile list of environment variables.

##### 8.6.2.4 Examples of Using sysresv

The following example shows how to use the `sysresv` utility:

    $ sysresv
    IPV Resources for ORACLE_SID "sales" :
    Shared Memory:
    ID                            KEY
    10345                    0x51c051ad
    Semaphores
    ID
    10345                    0x51c051ad
    Oracle Instance alive for sid "sales"

#### 8.6.3 Guidelines for Setting Semaphore Parameters

Use the following guidelines only if the default semaphore parameter values are too low to accommodate all Oracle processes:

**Note:**

Oracle recommends that you see the operating system documentation for more information about setting semaphore parameters.

1.  Calculate the minimum total semaphore requirements using the following formula:
        sum (process parameters of all database instances on the system) + overhead for oracle background processes + system and other application requirements
2.  Set `semmns` (maximum number of semaphores allowed for the server) to this total.
3.  Set `semmsl` (maximum number of semaphores in a semaphore set) to 250.
4.  Set `semmni` (maximum number of semaphore sets) to `semmns/semmsl `rounded up to the nearest multiple of 1024.
    **Note:**

    Oracle Solaris does not use these semaphore parameters, but uses resource controls. See My Oracle Support note 1006158.1:

    [`https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1006158.1`](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1006158.1)

    **See Also:**

    My Oracle Support note 226209.1, "Linux: How to Check Current Shared Memory, Semaphore Values," at the following URL:

    [`https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=226209.1`](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=226209.1)

#### 8.6.4 Shared Memory on IBM AIX on POWER Systems (64-Bit)

**Note:**

The information in this section applies only to IBM AIX on POWER Systems (64-bit).

Shared memory uses common virtual memory resources across processes. Processes share virtual memory segments through a common set of virtual memory translation resources, for example, tables and cached entries, for improved performance.

Shared memory can be pinned to prevent paging and to reduce Input-Output overhead. To perform this, set the `LOCK_SGA` parameter to `true`. On IBM AIX on POWER Systems (64-bit) 5L, the same parameter activates the large page feature whenever the underlying hardware supports it.

Run the following command to make pinned memory available to Oracle Database:

    $ /usr/sbin/vmo -r -o v_pinshm=1

Run a command similar to the following to set the maximum percentage of real memory available for pinned memory, where `percent_of_real_memory` is the maximum percent of real memory that you want to set:

    $ /usr/sbin/vmo -r -o maxpin percent=percent_of_real_memory

When using the `maxpin percent` option, it is important that the amount of pinned memory exceeds the Oracle SGA size by at least 3 percent of the real memory on the system, enabling free pinnable memory for use by the kernel. For example, if you have 2 GB of physical memory and you want to pin the SGA by 400 MB (20 percent of the RAM), then run the following command:

    $ /usr/sbin/vmo -r -o maxpin percent=23

**Note:**

The default `maxpin percent` value, which is set at 80 `percent`, works for most installations.

Use the `svmon` command to monitor the use of pinned memory during the operation of the system. Oracle Database attempts to pin memory only if the `LOCK_SGA` parameter is set to `true`. If the SGA size exceeds the size of memory available for pinning, then the portion of the SGA exceeding these sizes is allocated to ordinary shared memory.

##### Large Page Feature on IBM AIX on POWER Systems (64-Bit) POWER4 and POWER5 Based Systems

To turn on and reserve 10 large pages each of size 16 MB on a POWER4 or POWER5 system, run the following command:

    $ /usr/sbin/vmo -r -o lgpg_regions=10 -o lgpg_size=16777216

This command proposes `bosboot` and warns that a restart is required for the changes to take affect.

Oracle recommends specifying enough large pages to contain the entire SGA. The Oracle database instance attempts to allocate large pages when the `LOCK_SGA` parameter is set to `true`.

The 16 MB pages are always pinned, and cannot be used for standard memory. If a pool of 16 MB size pages is configured, then this memory is unusable for allocation of standard memory even if no other application is currently using large pages.

The POWER5 based systems support 64 K pages. Oracle uses them for SGA if they are available. These 64K pages do not require any additional configuration and do not depend on `LOCK_SGA` parameter setting.

To monitor use of large pages, use the following command:

    $ vmstat -P all

For the IBM AIX on POWER Systems (64-bit) operating system to use 16 MB pages, or pinned memory when allocating shared memory, the Oracle user ID must have `CAP_BYPASS_RAC_VMM` and `CAP_PROPAGATE` capabilities. User ID that is used to start the database instance must also have the same capabilities. In particular, when using large pages on an Oracle Real Application Cluster (Oracle RAC) database, where the `srvctl` command is used to start and stop the Oracle RAC database instances, it is also necessary to set the `CAP_BYPASS_RAC_VMM` and `CAP_PROPAGATE` capabilities for the `root` user.

**See Also:**

The IBM AIX on POWER Systems (64-bit) documentation for more information about enabling and tuning pinned memory and large pages

Capabilities can be set and examined using the following commands:

- Run the following command to check the current capabilities:

      $ lsuser –a capabilities oracle

- Add the `CAP_BYPASS_RAC_VMM` and `CAP_PROPAGATE` capabilities to this user ID:

      $ chuser capabilities=CAP_BYPASS_RAC_VMM,CAP_PROPAGATE oracle

**Note:**

Only the `root` user can display and set the capabilities attribute.

### 8.7 Tuning the Operating System Buffer Cache

Adjust the size of Oracle Database buffer cache. If memory is limited, then adjust the operating system buffer cache.

The operating system buffer cache holds blocks of data in memory while they are being transferred from memory to disk, or from disk to memory.

Oracle Database buffer cache is the area in memory that stores Oracle Database buffers.

If the amount of memory on the system is limited, then make a corresponding decrease in the operating system buffer cache size.

Use the `sar` command to determine which buffer caches you must increase or decrease.
