Large page support is a feature of Oracle Database.

It provides a performance boost for memory-intensive database instances running on Windows Server. By taking advantage of newly introduced operating system support, Oracle Database can now make more efficient use of processor memory addressing resources. Specifically, when large page support is enabled, the CPUs in the system access the Oracle Database buffers in RAM more quickly. Instead of addressing the buffers in 4KB increments, the CPUs are told to use 2 MB page sizes in Physical Address Extension (PAE) mode and 4MB page sizes in non-PAE mode when addressing the database buffers.

This feature is particularly useful when the Oracle buffer cache is several gigabytes. Smaller-sized configurations still see a gain when using large pages, but the gain will not be as great as when the database is accessing large amounts of memory.

If the service is running as a user instead of the default `SYSTEM` user, then the administrator must grant the "Lock pages in memory" privilege to the user. This privilege is not enabled by default when Windows is installed.

- [Granting Lock Pages in Memory Privilege](granting-lock-pages-in-memory-privilege.md)
  Use this procedure to grant lock pages in memory privilege.
- [Enabling Large Page Support](enabling-large-page-support.md)
  To take advantage of large pages, the amount of physical memory must be greater than the amount of System Global Area (SGA) specified in the parameter file.

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
