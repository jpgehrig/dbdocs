## About Direct NFS Client Mounts to NFS Storage Devices

Direct NFS Client integrates the NFS client functionality directly in the Oracle software to optimize the I/O path between Oracle and the NFS server. This integration can provide significant performance improvements.

Direct NFS Client supports NFSv3, NFSv4, NFSv4.1, and pNFS protocols to access the NFS server. Direct NFS Client also simplifies, and in many cases automates, the performance optimization of the NFS client configuration for database workloads.

Starting with Oracle Database 12c Release 2, when you enable Direct NFS, you can also enable the Direct NFS dispatcher. The Direct NFS dispatcher consolidates the number of TCP connections that are created from a database instance to the NFS server. In large database deployments, using Direct NFS dispatcher improves scalability and network performance. Parallel NFS deployments also require a large number of connections. Hence, the Direct NFS dispatcher is recommended with Parallel NFS deployments too.

Direct NFS Client can obtain NFS mount points either from the operating system mount entries, or from the `oranfstab` file.

### Direct NFS Client Requirements

- NFS servers must have write size values (wtmax) of 32768 or greater to work with Direct NFS Client.

- NFS mount points must be mounted both by the operating system kernel NFS client and Direct NFS Client, even though you configure Direct NFS Client to provide file service.

  If Oracle Database cannot connect to an NFS server using Direct NFS Client, then Oracle Database connects to the NFS server using the operating system kernel NFS client. When Oracle Database fails to connect to NAS storage though Direct NFS Client, it logs an informational message about the Direct NFS Client connect error in the Oracle alert and trace files.

- Follow standard guidelines for maintaining integrity of Oracle Database files mounted by both operating system NFS and by Direct NFS Client.

### Direct NFS Mount Point Search Order

Direct NFS Client searches for mount entries in the following order:

1.  `$ORACLE_HOME/dbs/oranfstab`

2.  `/etc/oranfstab`

3.  `/etc/mtab`

Direct NFS Client uses the first matching entry as the mount point.

**Note:**

You can have only one active NFS Client implementation for each instance. Enabling Direct NFS Client on an instance prevents you from using another NFS Client implementation, such as kernel NFS Client.

**See Also:**

- [Oracle Database Reference](../refrn/ENABLE_DNFS_DISPATCHER.md) for information about setting the `enable_dnfs_dispatcher` parameter in the initialization parameter file to enable Direct NFS dispatcher

- [Oracle Database Performance Tuning Guide](../tgdba/managing-operating-system-resources.md) for performance benefits of enabling Parallel NFS and Direct NFS dispatcher

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/considerations-asm-storage.md) for guidelines about managing Oracle Database data files created with Direct NFS Client or kernel NFS

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
