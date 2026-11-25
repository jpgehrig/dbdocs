Parameter `SGA_MAX_SIZE` holds the maximum size that System Global Area (SGA) can reach for a particular instance.

Oracle Database can change its SGA configuration while the instance is running. This allows sizes of the buffer cache, shared pool, and the large pool to be changed without an instance shutdown.

Oracle Database can start the instances unconfigured and allow the instance to use more memory by growing SGA up to a maximum of `SGA_MAX_SIZE`. If no `SGA_MAX_SIZE` value is specified, then Oracle Database selects a default value that is the sum of all components specified or defaulted at initialization time. If `SGA_MAX_SIZE` specified in the initialization parameter file is less than the sum of all components specified or defaulted to at initialization time, then the setting of `SGA_MAX_SIZE` in the initialization parameter file serves as an upper bound.

Memory allocated for the SGA of an instance is displayed on an instance startup when using Oracle Enterprise Manager (or SQL\*Plus). You can also display the SGA size of the current instance by using the SQL\*Plus `SHOW` statement with the SGA clause.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/database-memory-allocation.md) for more information about SGA initialization parameters

- [Oracle Database Concepts](../cncpt/memory-architecture.md) for more information about SGA and its components

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
