Oracle Database supports 64-bit file I/O to allow the use of files larger than 4 gigabytes (GB).

In addition, physical and logical raw files are supported as data, log, and control files to support Oracle Real Application Clusters (Oracle RAC) on Windows and for those cases where performance must be maximized.

Instead of using the operating system kernel NFS client, you can configure Oracle Database to access NFS V3 servers directly using an Oracle internal Direct NFS client. Through this integration, Oracle can optimize the I/O path between Oracle and the NFS server, resulting in a significantly superior performance. In addition, Direct NFS client simplifies and optimizes the NFS client configuration for database workloads.

Now, the Direct NFS client supports all widely accepted NFS path formats, including both Windows-style and UNIX-style NFS paths.

Volumes mounted through CIFS cannot be used for storing Oracle database files without configuring the Direct NFS client. The atomic write requirements needed for database writes are not guaranteed through the CIFS protocol. Consequently, CIFS can be used only for operating system-level commands such as, copy, move, and so on.

The Direct NFS client currently supports up to four parallel network paths to provide scalability and high availability. The Direct NFS client delivers optimized performance by automatically load balancing requests across all specified paths. If one network path fails, then the Direct NFS client resends commands over any remaining paths ensuring fault tolerance and high availability.

A new parameter called `dnfs_batch_size` is now added to control the number of asynchronous I/O operations that can be queued by an Oracle process when the Direct NFS client is enabled. Set this parameter only if the Direct NFS client is overwhelming the NFS server or the network. This parameter helps the user to manage the load that the Direct NFS client can generate. In typical environments, you must not set this parameter. The default value of this parameter is 4096. To reduce the Direct NFS client load, Oracle recommends a value of 128 that can be changed based on the NFS server performance.

**See Also:**

Your vendor documentation to complete NFS configuration and mounting

**Parent topic:** [Overview of Oracle Database on Windows Architecture](overview-of-oracle-database-on-windows-architecture.md)
