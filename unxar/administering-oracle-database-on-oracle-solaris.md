This appendix contains information about administering Oracle Database on Oracle Solaris.

It contains the following topics:

Oracle Solaris Shared Memory Environment

About Creating Resource Pools on Oracle Solaris Systems

About Multi-CPU Binding Functionality

### B.1 Oracle Solaris Shared Memory Environment

This section describes how Oracle Database uses shared memory models like Optimized Shared Memory (OSM), Intimate Shared Memory (ISM), and Dynamic Intimate Shared Memory (DISM).

It contains the following topics:

- About Optimized Shared Memory

- Checking for Optimized Shared Memory

- About ISM and DISM

- Checking for ISM or DISM

- About the oradism Utility

- How Oracle Database Decides Between OSM\_ ISM and DISM

#### B.1.1 About Optimized Shared Memory

Starting with 12c, Oracle Database uses the Optimized Shared Memory (OSM) model of Oracle Solaris on Oracle Solaris 10 1/13 and Oracle Solaris 11.1 SRU 7.5 or later systems to implement Automatic Memory Management.

OSM allows dynamic resizing of System Global Area (SGA) without restarting the instance. It does not use the `oradism` utility and swap disk space. OSM is NUMA-optimized.

#### B.1.2 Checking for Optimized Shared Memory

**Note:**

Ensure that you set the `MEMORY_MAX_TARGET` to a greater value than `MEMORY_TARGET` to utilize Optimized Shared Memory.

To verify if Oracle Solaris uses Optimized Shared Memory (OSM), enter the following command:

    $ ipcs -dm

If the column `ALLOC` shows an integer, it specifies that OSM is in use. If the column `ALLOC` shows a hyphen, it specifies that OSM is not in use.

#### B.1.3 About ISM and DISM

On Oracle Solaris systems, Oracle Database uses Intimate Shared Memory (ISM) for shared memory segments because it shares virtual memory resources between Oracle processes. ISM causes the physical memory for the entire shared memory segment to be locked automatically.

On Oracle Solaris 10 systems prior to Oracle Solaris 10 1/13 and Oracle Solaris 11 SRU 7.5, Dynamic Intimate Shared Memory (DISM) is available. This enables Oracle Database to share virtual memory resources between processes sharing the segment, and at the same time, enables memory paging. The operating system does not have to lock down physical memory for the entire shared memory segment.

#### B.1.4 Checking for ISM or DISM

On Oracle Solaris, to determine if shared memory is in use, use the `ipcs -im` command. For example:

    % ipcs -im
    IPC status from <system> as of Thu Aug 19 01:09:30 PDT 2013
    T  ID    KEY        MODE      OWNER   GROUP  ISMATTCH
    Shared Memory:
    m  11  0xacea4150 --rw-rw---- oracle   dba     160

The `ISMATTCH` field shows 160 processes attached to this shared memory segment. However, `ISMATTCH `does not distinguish between Intimate Shared Memory (ISM) and Dynamic Intimate Shared Memory (DISM).

On Oracle Solaris 10 systems prior to Oracle Solaris 10 1/13 and Oracle Solaris 11 SRU 7.5, to identify if ISM or DISM is in use, or which memory locking service is active, use the `pmap –xs` command. For example:

    % ps -ef | grep ora | grep smon

    oracle 12524 1 0 05:40:13 ? 0:25 ora_smon_prod

    % pmap –xs 12524 | grep ism

    0000000380000000 38010880 38010880 - 38010880 256M rwxsR [ ism shmid=0xb ]
    0000000C90000000 131072 131072 - 131072 4M rwxsR [ ism shmid=0xb ]
    0000000C98000000 16 16 - 16 8K rwxsR [ ism shmid=0xb ]

**Note:**

The `ps —ef` command lists the background processes that are running. This information is required to determine if an Oracle database instance is running.

The output from the `pmap –xs` command shows three `ism` address ranges implying that ISM is in use. If DISM locks the memory ranges, then the output shows` dism` address ranges.

#### B.1.5 About the oradism Utility

Oracle Database uses the `oradism` utility to lock and unlock shared memory. The `oradism` utility is automatically set up during installation. It is not required to perform any configuration tasks to use dynamic SGA.

The process name for the `oradism` utility is `ora_dism_sid`, where `sid` is the system identifier. When using DISM, this process is started during instance startup, and automatically quits when the instance is shut down.

If a message is displayed in the alert log saying that the `oradism` utility is not set up correctly, then verify that the `oradism` utility is located in the `$ORACLE_HOME/bin` directory and that it has superuser privileges.

**Note:**

Optimized Shared Memory (OSM) does not use the `oradism` utility.

#### B.1.6 How Oracle Database Decides Between OSM, ISM and DISM

Oracle Database automatically uses Optimized Shared Memory (OSM) on Oracle Solaris systems where OSM is available. See "About Optimized Shared Memory" for more information on OSM.

On systems where OSM is not available, Oracle Database automatically selects Intimate Shared Memory (ISM) or Dynamic Intimate Shared Memory (DISM) based on the following criteria:

- Oracle Database uses DISM if it is available on the system, and if the value of the `SGA_MAX_SIZE` initialization parameter is larger than the size required for all SGA components combined. This enables Oracle Database to lock only the amount of physical memory that is used.

- Oracle Database uses ISM if the entire shared memory segment is in use at startup or if the value of the `SGA_MAX_SIZE` parameter equals or smaller than the size required for all SGA components combined.

Regardless of whether Oracle Database uses ISM or DISM, it can always exchange the memory between dynamically sizable components such as the buffer cache, the shared pool, and the large pool after it starts an instance. Oracle Database can relinquish memory from one dynamic SGA component and allocate it to another component.

Because shared memory segments are not implicitly locked in memory, when using DISM, Oracle Database explicitly locks shared memory that is currently in use at startup. When a dynamic SGA operation uses more shared memory, Oracle Database explicitly performs a lock operation on the memory that is put to use. When a dynamic SGA operation releases shared memory, Oracle Database explicitly performs an unlock operation on the memory that is freed, so that it becomes available to other applications.

**Note:**

Do not set the `LOCK_SGA` parameter to `TRUE` in the server parameter file. If you do, then Oracle Database 12c cannot start.

### B.2 About Creating Oracle Solaris Resource Pools

Oracle Solaris Resource Pools improve database performance by associating a dedicated set of CPUs to a database instance. Each database instance can only use the resources in its resource pool.

When consolidating on a large server, you may want to restrict the database to a specific subset of the CPU and memory. This feature makes it easy to enable CPU and memory restrictions for an Oracle Database instance.

Use the `setup_resource_pool.sh` script to create Oracle Solaris Resource Pools. Download this script from note 1928328.1 from the My Oracle Support website:

<https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=1928328.1>

### B.3 About Multi-CPU Binding Functionality

You can use Multi-CPU Binding (MCB) as part of your resource management policy to improve performance.

Multi-CPU binding (MCB) is an Oracle Solaris projects resource management functionality that binds a project to a specific set of CPUs, but does not bind the CPUs exclusively. MCB allows other processes also to use these CPUs, and allows overlapping of partitions. MCB is supported on Oracle Solaris 11.3 and later.

The resource pools feature also allows binding of CPUs. However, this method requires hard partitioning of processors in the system. Resource pools does not allow overlapping of partitions.

You can assign, modify, or remove MCBs through Oracle Solaris projects. Use the standard command-line tools `projadd(1M)` and `projmod(1M) `to create or modify the project file.

For database users, the advantages of using MCB over resource pools include:

- The ability to bind an Oracle instance to a particular NUMA location for performance, such as, near a specific I/O or networking device.

- The ability to bind multiple Oracle instances to different cores or sockets on a host to increase performance isolation without the need of a privileged administrator to partition the system.

**See Also:**

["Using Projects to Assign, Modify, and Remove Multi-CPU Binding"](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=using_projects_to_edit_multi_cpu_binding) and ["How to Use Projects to Assign, Modify, and Remove Multi-CPU Binding"](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=how_to_use_projects_to_edit_multi_cpu_binding) in Administering Resource Management in Oracle Solaris 11.3.
