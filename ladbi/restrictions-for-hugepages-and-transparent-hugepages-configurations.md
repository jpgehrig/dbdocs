## Restrictions for HugePages and Transparent HugePages Configurations

Review the HugePages and Transparent HugePages guidelines discussed in this section.

Oracle recommends that you disable Transparent HugePages, because they may cause delays in accessing memory that can result in node restarts in Oracle RAC environments, or performance issues or delays for Oracle Database single instances. Oracle continues to recommend using standard HugePages for Linux.

Transparent HugePages memory is enabled by default with Oracle Linux 6 and later, Red Hat Enterprise Linux 6 and later, SUSE 11 and later, kernels.

If you install Oracle Database Preinstallation RPM, then it disables Transparent HugePages.

Transparent Hugepages are similar to standard HugePages. However, while standard HugePages allocate memory at startup, Transparent Hugepages memory uses the `khugepaged` thread in the kernel to allocate memory dynamically during runtime, using swappable HugePages.

HugePages allocates non-swappable memory for large page tables using memory-mapped files. HugePages are not enabled by default. If you enable HugePages, then you should deduct the memory allocated to HugePages from the available RAM before calculating swap space. Refer to your distribution documentation and to Oracle Technology Network and My Oracle Support for more information.

During Oracle Grid Infrastructure installation, the Grid Infrastructure Management Repository (GIMR) is configured to use HugePages. Because the Grid Infrastructure Management Repository database starts before all other databases installed on the cluster, if the space allocated to HugePages is insufficient, then the System Global Area (SGA) of one or more databases may be mapped to regular pages, instead of Hugepages, which can adversely affect performance. Configure the HugePages memory allocation to a size large enough to accommodate the sum of the SGA sizes of all the databases you intend to install on the cluster, as well as the Grid Infrastructure Management Repository.

**Parent topic:** [Guidelines for Linux Operating System Installation](guidelines-for-linux-operating-system-installation.md)
