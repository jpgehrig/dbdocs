This appendix contains information about administering Oracle Database on Linux.

It contains the following topics:

- Supporting Asynchronous Input-Output

- Asynchronous Input-Output Support

- Enabling Direct Input-Output Support

- Enabling Simultaneous Multithreading

- Allocating Shared Resources

- About Creating cgroups on Linux Systems

- Overview of HugePages

**Note:**

Starting with Oracle Database 11g Release 2 (11.2), Linux x86-64 and IBM: Linux on System z media does not contain Linux x86 binaries.

### A.1 Supporting Asynchronous Input-Output

**Note:**

On Linux, Automatic Storage Management uses asynchronous Input-Output by default. Asynchronous Input-Output is not supported for database files stored on Network File Systems.

Oracle Database supports kernel asynchronous Input-Output. Asynchronous Input-Output is enabled by default on raw volumes. Automatic Storage Management uses asynchronous Input-Output by default.

By default, the `DISK_ASYNCH_IO` initialization parameter in the parameter file is set to TRUE. To enable asynchronous Input-Output on file system files:

1.  Ensure that all Oracle Database files are located on file systems that support asynchronous Input-Output.
2.  Set the `FILESYSTEMIO_OPTIONS` initialization parameter in the parameter file to `ASYNCH` or `SETALL`.
    **Note:**

    If the file system files are managed through ODM library interface or Direct NFS Client, asynchronous Input-Output is enabled by default. There is no need to set `FILESYSTEMIO_OPTIONS` to enable asynchronous Input-Output in these environments.

### A.2 Asynchronous Input-Output Support

**Note:**

On Linux, Automatic Storage Management uses asynchronous Input-Output by default. Asynchronous Input-Output is not supported for database files stored on Network File Systems.

Oracle Database supports kernel asynchronous Input-Output. This feature is disabled by default.

By default, the `DISK_ASYNCH_IO` initialization parameter in the parameter file is set to TRUE to enable asynchronous I/O on raw devices. To enable asynchronous Input-Output on file system files:

1.  Ensure that all Oracle Database files are located on file systems that support asynchronous Input-Output.
2.  Set the `FILESYSTEMIO_OPTIONS` initialization parameter in the parameter file to `ASYNCH` to enable asynchronous Input-Output. If you want to enable both asynchronous Input-Output and direct Input-Output, set the `FILESYSTEMIO_OPTIONS` initialization parameter in the parameter file to `SETALL.`

### A.3 Enabling Direct Input-Output Support

Direct Input-Output support is available and supported on Linux.

To enable direct Input-Output support:

- Set the `FILESYSTEMIO_OPTIONS` initialization parameter to `DIRECTIO`.

- Set the `FILESYSTEMIO_OPTIONS` initialization parameter in the parameter file to `SETALL`, which will enable both asynchronous Input-Output and direct Input-Output.

### A.4 Enabling Simultaneous Multithreading

If Simultaneous Multithreading is enabled, then the `v$osstat` view reports two additional rows corresponding to the online logical (`NUM_LCPUS`) and virtual CPUs (`NUM_VCPUS`).

### A.5 Allocating Shared Resources

To use the `MEMORY_TARGET` or `MEMORY_MAX_TARGET` feature, the following kernel parameters must be modified.

- `/dev/shm` mount point should be equal in size or larger than the value of `SGA_MAX_SIZE`, if set, or should be set to be at least `MEMORY_TARGET` or `MEMORY_MAX_TARGET`, whichever is larger. For example, with `MEMORY_MAX_TARGET=4GB` only set, to create a 4 GB system on the `/dev/shm` mount point:

  - Run the following command as the `root` user:

        # mount -t tmpfs shmfs -o size=4g /dev/shm

  - Ensure that the in-memory file system is mounted when the system restarts, add an entry in the `/etc/fstab` file similar to the following:

          tmpfs /dev/shm tmpfs size=4g 0

- The number of file descriptors for each Oracle instance are increased by 512\*`PROCESSES`. Therefore, the maximum number of file descriptors should be at least this value, plus some more for the operating system requirements. For example, if the `cat /proc/sys/fs/file-max` command returns 32768 and `PROCESSES` are 100, you can set it to 6815744 or higher as `root`, to have 51200 available for Oracle. Use one of the following options to set the value for the `file-max` descriptor.

  - Run the following command:

        echo 6815744 > /proc/sys/fs/file-max

    OR

  - Modify the following entry in the `/etc/sysctl.conf` file and restart the system as `root`.

        fs.file-max = 6815744

- Per-process number of file descriptors must be at least 512. For example, as `root` run the following command.

  - On bash and sh:

        # ulimit -n

  - On csh:

        # limit descriptors

  If the preceding command returns 200, then run the following command to set the value for the per processor file descriptors limit, for example to 1000:

  - On bash and sh:

        # sudo sh
        # ulimit -n 1000

  - On csh:

        # sudo sh
        # limit descriptors 1000

- `MEMORY_TARGET` and `MEMORY_MAX_TARGET` cannot be used when `LOCK_SGA` is enabled. `MEMORY_TARGET` and `MEMORY_MAX_TARGET` also cannot be used with huge pages on Linux.

### A.6 About Creating Cgroups on Linux Systems

Cgroups, or control groups, improve database performance by associating a dedicated set of CPUs to a database instance. Each database instance can only use the resources in its cgroup.

When consolidating on a large server, you may want to restrict the database to a specific subset of the CPU and memory. This feature makes it easy to enable CPU and memory restrictions for an Oracle Database instance.

Use the `setup_processor_group.sh` script to create cgroups. Download this script from note 1585184.1 on the My Oracle Support website:

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1585184.1>

### A.7 Overview of HugePages

HugePages is a feature integrated into the Linux kernel 2.6. Enabling HugePages makes it possible for the operating system to support memory pages greater than the default (usually 4 KB). Using very large page sizes can improve system performance by reducing the amount of system resources required to access page table entries. HugePages is useful for both 32-bit and 64-bit configurations. HugePage sizes vary from 2 MB to 256 MB, depending on the kernel version and the hardware architecture. For Oracle Databases, using HugePages reduces the operating system maintenance of page states, and increases Translation Lookaside Buffer (TLB) hit ratio.

**Note:**

Transparent Hugepages is currently not an alternative to manually configure HugePages.

This section includes the following topics:

- Reviewing HugePages Memory Allocation

- Using HugePages on Linux

- Tuning SGA With HugePages

- Configuring HugePages on Linux

- Restrictions for HugePages Configurations

- Disabling Transparent HugePages

#### A.7.1 Reviewing HugePages Memory Allocation

Review this information if your operating system has HugePages enabled.

On Linux platform installations, Oracle recommends that you use HugePages to obtain the best performance for Oracle Databases. When you upgrade Oracle Grid Infrastructure and Oracle Databases on servers that have HugePages enabled, Oracle recommends that you review your HugePages memory allocation requirements.

##### GIMR and HugePages Memory

Oracle Grid Infrastructure installations include the Grid Infrastructure Management Repository (GIMR). When HugePages is configured on cluster member nodes, the GIMR system global area (SGA) is installed into HugePages memory. The GIMR SGA occupies up to 1 GB of HugePages memory. Oracle Grid Infrastructure starts up before Oracle Databases installed on the cluster.

If your cluster member node operating system memory allocations to HugePages are insufficient for the size of the SGAs for all of the Oracle Database instances on the cluster, then you may find that one or more of your Oracle Database SGAs are mapped to regular pages, instead of Huge Pages, which reduces expected performance. To avoid this issue, when you plan your upgrade, ensure that the memory you reserve for HugePages is large enough to accommodate your memory requirements.

Allocate memory to HugePages large enough for all databases planned to run SGA on the cluster, and to accommodate the SGA for the Grid Infrastructure Management Repository.

#### A.7.2 Using HugePages on Linux

To enable Oracle Database to use large pages (sometimes called HugePages) on Linux, set the value of the `vm.nr_hugepages` kernel parameter to specify the number of large pages that you want to reserve. You must specify adequate large pages to hold the entire SGA for the database instance. To determine the required parameter value, divide the SGA size for the instance by the size of a large page, then round up the result to the nearest integer.

To determine the default large page size, run the following command:

    # grep Hugepagesize /proc/meminfo

For example, if `/proc/meminfo` lists the large page size as 2 MB, and the total SGA size for the instance is 1.6 GB, then set the value for the `vm.nr_hugepages` kernel parameter to 820 (1.6 GB / 2 MB = 819.2).

#### A.7.3 Tuning SGA With HugePages

Without HugePages, the operating system keeps each 4 KB of memory as a page. When it allocates pages to the database System Global Area (SGA), the operating system kernel must continually update its page table with the page lifecycle (dirty, free, mapped to a process, and so on) for each 4 KB page allocated to the SGA.

With HugePages, the operating system page table (virtual memory to physical memory mapping) is smaller, because each page table entry is pointing to pages from 2 MB to 256 MB.

Also, the kernel has fewer pages whose lifecycle must be monitored. For example, if you use HugePages with 64-bit hardware, and you want to map 256 MB of memory, you may need one page table entry (PTE). If you do not use HugePages, and you want to map 256 MB of memory, then you must have 256 MB \* 1024 KB/4 KB = 65536 PTEs.

HugePages provides the following advantages:

- Increased performance through increased TLB hits

- Pages are locked in memory and never swapped out, which provides RAM for shared memory structures such as SGA

- Contiguous pages are preallocated and cannot be used for anything else but for System V shared memory (for example, SGA)

- Less bookkeeping work for the kernel for that part of virtual memory because of larger page sizes

#### A.7.4 Configuring HugePages on Linux

Complete the following steps to configure HugePages on the computer:

1.  Run the following command to determine if the kernel supports HugePages:

        $ grep Huge /proc/meminfo

2.  Some Linux systems do not support HugePages by default. For such systems, build the Linux kernel using the `CONFIG_HUGETLBFS` and `CONFIG_HUGETLB_PAGE `configuration options. `CONFIG_HUGETLBFS` is located under File Systems and `CONFIG_HUGETLB_PAGE` is selected when you select `CONFIG_HUGETLBFS`.

3.  Edit the `memlock` setting in the `/etc/security/limits.conf` file. The `memlock` setting is specified in KB, and the maximum locked memory limit should be set to at least 90 percent of the current RAM when HugePages memory is enabled and at least 3145728 KB (3 GB) when HugePages memory is disabled. For example, if you have 64 GB RAM installed, then add the following entries to increase the maximum locked-in-memory address space:

        *   soft   memlock    60397977
        *   hard   memlock    60397977

    You can also set the `memlock` value higher than your SGA requirements.

4.  Log in as `oracle` user again and run the `ulimit -l` command to verify the new `memlock `setting:

        $ ulimit -l
        60397977

5.  Run the following command to display the value of `Hugepagesize` variable:

        $ grep Hugepagesize /proc/meminfo

6.  Complete the following procedure to create a script that computes recommended values for `hugepages` configuration for the current shared memory segments:

    1.  Create a text file named `hugepages_settings.sh`.

        See [My Oracle Support note 401749.1](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=273574277070798&id=401749.1&_adf.ctrl-state=1c5pqymcb4_52#CODE) for details about creating the `hugepages_settings.sh` script.

    2.  Run the following command to change the permission of the file:

            $ chmod +x hugepages_settings.sh

7.  Run the `hugepages_settings.sh `script to compute the values for `hugepages` configuration:

        $ ./hugepages_settings.sh

    **Note:**

    Before running this script, ensure that all the applications that use `hugepages` run.

8.  Set the following kernel parameter, where value is the HugePages value that you determined in step 7:

        # sysctl -w vm.nr_hugepages=value

9.  To ensure that HugePages is allocated after system restarts, add the following entry to the `/etc/sysctl.conf` file, where value is the HugePages value that you determined in step 7:

        vm.nr_hugepages=value

10. Run the following command to check the available `hugepages`:

        $ grep Huge /proc/meminfo

11. Restart the instance.

12. Run the following command to check the available `hugepages` (1 or 2 pages free):

        $ grep Huge /proc/meminfo

    **Note:**

    If you cannot set your HugePages allocation using `nr_hugepages`, then your available memory may be fragmented. Restart your server for the Hugepages allocation to take effect.

#### A.7.5 Restrictions for HugePages Configurations

HugePages has the following limitations:

- You must unset both the `MEMORY_TARGET` and `MEMORY_MAX_TARGET` initialization parameters. For example, to unset the parameters for the database instance, use the command `ALTER SYSTEM RESET`.

- Automatic Memory Management (AMM) and HugePages are not compatible. When you use AMM, the entire SGA memory is allocated by creating files under `/dev/shm`. When Oracle Database allocates SGA with AMM, HugePages are not reserved. To use HugePages on Oracle Database 19c, You must disable AMM.

- If you are using VLM in a 32-bit environment, then you cannot use HugePages for the Database Buffer cache. You can use HugePages for other parts of the SGA, such as `shared_pool`, `large_pool`, and so on. Memory allocation for VLM (buffer cache) is done using shared memory file systems (`ramfs/tmpfs/shmfs`). Memory file systems do not reserve or use HugePages.

- HugePages are not subject to allocation or release after system startup, unless a system administrator changes the HugePages configuration, either by modifying the number of pages available, or by modifying the pool size. If the space required is not reserved in memory during system startup, then HugePages allocation fails.

- Ensure that HugePages is configured properly as the system may run out of memory if excess HugePages is not used by the application.

- If there is insufficient HugePages when an instance starts and the initialization parameter `use_large_pages` is set to `only`, then the database fails to start and an alert log message provides the necessary information on Hugepages.

#### A.7.6 Disabling Transparent HugePages

Oracle recommends that you disable Transparent HugePages before you start installation.

Transparent HugePages memory differs from standard HugePages memory because the kernel `khugepaged` thread allocates memory dynamically during runtime. Standard HugePages memory is pre-allocated at startup, and does not change during runtime.

**Note:**

Although Transparent HugePages is disabled on UEK2 and later UEK kernels, Transparent HugePages may be enabled by default on your Linux system.

Transparent HugePages memory is enabled by default with Oracle Linux 6 and later, Red Hat Enterprise Linux 6 and later, SUSE 11 and later, kernels.

Transparent HugePages can cause memory allocation delays during runtime. To avoid performance issues, Oracle recommends that you disable Transparent HugePages on all Oracle Database servers. Oracle recommends that you instead use standard HugePages for enhanced performance.

To check if Transparent HugePages is enabled, run one of the following commands as the `root` user:

Red Hat Enterprise Linux kernels:

    # cat /sys/kernel/mm/redhat_transparent_hugepage/enabled

Other kernels:

    # cat /sys/kernel/mm/transparent_hugepage/enabled

The following is a sample output that shows Transparent HugePages are being used as the \[always\] flag is enabled.

    [always] never

**Note:**

If Transparent HugePages is removed from the kernel, then neither `/sys/kernel/mm/transparent_hugepage` nor `/sys/kernel/mm/redhat_transparent_hugepage files` exist.

To disable Transparent HugePages:

1.  For Oracle Linux 7 and later, and Red Hat Enterprise Linux 7 and later, add or modify the transparent_hugepage=never parameter in the `/etc/default/grub` file:

        transparent_hugepage=never

    For example:
        GRUB_TIMEOUT=5
        GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
        GRUB_DEFAULT=saved
        GRUB_DISABLE_SUBMENU=true
        GRUB_TERMINAL_OUTPUT="console"
        GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet numa=off transparent_hugepage=never"
        GRUB_DISABLE_RECOVERY="true"

    **Note:**

    The file name may vary for your operating systems. Check your operating system documentation for the exact file name and the steps to disable Transparent HugePages.

2.  Run the `grub2–mkconfig `command to regenerate the `grub.cfg` file.

        # grub2-mkconfig -o /boot/grub2/grub.cfg

3.  Restart the system to make the changes permanent.
