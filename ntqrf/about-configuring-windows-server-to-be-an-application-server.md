Windows memory manager divides up system memory into three different pools, described in Windows Server Memory Shares.

Table 8-1 Windows Server Memory Shares

| Pool                             | Percent of Total Memory |
|:---------------------------------|:------------------------|
| Kernel and other system services | 9%                      |
| File cache                       | 41%                     |
| Paged memory                     | 50%                     |

Windows Server memory manager tries to balance each application's usage of memory by dynamically paging memory between a physical RAM and a virtual memory paging file. If an application is particularly memory-intensive (like Oracle Database) or if a large number of applications run concurrently, then combined memory requirements of the applications might exceed physical memory capacity.

The large proportion of memory reserved for file caching (41%) can be quite beneficial to the file and print servers. But it might not be advantageous to the application servers that often run memory-intensive network applications. A Windows Server file cache is particularly unnecessary for Oracle Database, which performs its own caching through the System Global Area.

You can reset the Windows Server memory model from the default file and print server, with its large file cache, to a network applications model, with a reduced file cache and more physical memory available for Oracle Database.

**See Also:**

Your operating system documentation for instructions

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
