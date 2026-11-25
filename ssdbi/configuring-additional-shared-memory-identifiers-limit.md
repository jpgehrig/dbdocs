Starting with 18c, on Oracle Solaris systems, Oracle Database uses a new method of sharing memory among a group of processes, also known as Managed Global Areas (MGA). The operating system memory allocation mechanism for this new method is Optimized Shared Memory (OSM).

Oracle recommends that you configure the additional shared memory identifiers and increase the shared memory limits as follows:

Additional number of MGA segments (project.max-shm-ids) = MGA memory size / granule size

Where:

MGA memory size is the cumulative MGA memory requirement size for all processes in an Oracle Database instance. Typically, 2MB per Oracle process.

Minimum value of granule size is 4 MB. For large SGA, granule size may increase automatically upto 512 MB.

Refer to the following table to determine the approximate granule size.

Table 14-3 Granule Size for SGA Values

| SGA                      | Granule Size |
|:-------------------------|:-------------|
| Less than 1 GB           | 4 MB         |
| Between 1 GB and 8 GB    | 16 MB        |
| Between 8 GB and 16 GB   | 32 MB        |
| Between 16 GB and 32 GB  | 64 MB        |
| Between 32 GB and 64 GB  | 128 MB       |
| Between 64 GB and 128 GB | 256 MB       |
| Greater than 128 GB      | 512 MB       |

**Parent topic:** [Configuring Kernel Parameters on Oracle Solaris](configuring-kernel-parameters-on-oracle-solaris.md)
