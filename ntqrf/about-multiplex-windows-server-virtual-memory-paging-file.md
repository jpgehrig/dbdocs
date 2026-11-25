Discusses about Multiplexing the Windows Server virtual memory paging file to boost system performance.

Some virtual memory paging is likely even if Oracle Database is the only network application running on Windows Server, because Windows Server memory manager attempts to move seldom-used pages to disk to free up more physical memory for hot pages.

Multiplexing the Windows Server virtual memory paging file is a good strategy to boost overall system performance. Splitting the paging file onto at least two different physical volumes (or logical volumes as long as underlying physical volumes do not overlap) provides a significant performance boost to virtual memory swapping operations.

Even though this is a good technique to increase speed of virtual memory paging, too much paging activity is still a performance hit and must be corrected by adding more RAM to the server.

### About General Page File Sizing Tip

Oracle recommends setting virtual memory to one times the size of RAM, if physical memory is between 2GB and 16GB. If physical memory is more than 16 GB, then set virtual memory to 16 GB.

Configurations where combined size is two to four times the size of physical RAM are not uncommon. Minimize paging as much as possible. But situations in which the operating system runs out of or low on paging space are to be avoided at all costs. Adequately-sized paging files spaced across physical disks spread out I/O most efficiently, because the operating system spreads paging evenly across page files.

**Note:**

Internal read/write batch size for Windows is 4K.

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
