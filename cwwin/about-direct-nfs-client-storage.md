## About Direct NFS Client Storage

Direct NFS Client integrates the NFS client functionality directly in the Oracle software to optimize the I/O path between Oracle and the NFS server. This integration can provide significant performance improvements.

Direct NFS Client supports NFSv3, NFSv4 and NFSv4.1 protocols to access the NFS server. Direct NFS Client also simplifies, and in many cases automates, the performance optimization of the NFS client configuration for database workloads. Starting with Oracle Database 12c release 2 (12.2), Windows Direct NFS Client supports all widely accepted NFS path formats including UNIX-style NFS paths and NFS Version 4 protocol.

Starting with Oracle Database 12c release 2, when you enable Direct NFS, you can also enable the Direct NFS dispatcher. The Direct NFS dispatcher consolidates the number of TCP connections that are created from a database instance to the NFS server. In large database deployments, using Direct NFS dispatcher improves scalability and network performance. Parallel NFS deployments also require a large number of connections. Hence, the Direct NFS dispatcher is recommended with Parallel NFS deployments too.

Direct NFS Client tunes itself to make optimal use of available resources and enables the storage of data files on supported NFS servers. Direct NFS Client obtains NFS mount points from the `oranfstab` file.

**Note:**

Use NFS servers supported for Oracle RAC. Check My Oracle Support, as described in [Checking Hardware and Software Certification on My Oracle Support](checking-hardware-and-software-certification-on-my-oracle-support.md).

### Direct NFS Client Requirements

- Direct NFS cannot provide service to NFS servers with write size values (`wtmax`) less than 32768.

- The Oracle files resident on the NFS server that are accessed by Direct NFS Client can also be accessed through a third-party NFS client. The volume must be mounted through Common Internet File System (CIFS) or kernel NFS to enable regular windows utilities and commands, such as copy, and so on, access the database files in the remote location.

- Volumes mounted through CIFS can not be used for storing Oracle database files without configuring Direct NFS Client. The atomic write requirements needed for database writes are not guaranteed through the CIFS protocol, consequently CIFS can only be used for OS level access, for example, for commands such as copy.

- To enable Oracle Database to use Direct NFS Client, the NFS file systems must be mounted and available before you start installation. Direct NFS Client manages settings after installation.

  If Oracle Database cannot open an NFS server using Direct NFS Client, then an informational message is logged into the Oracle alert log. A trace file is also created, indicating that Direct NFS Client could not connect to an NFS server.

- Some NFS file servers require NFS clients to connect using reserved ports. If your filer is running with reserved port checking, then you must disable it for Direct NFS to operate. To disable reserved port checking, consult your NFS file server documentation.

- For NFS servers that restrict port range, you can use the insecure option to enable clients other than an Administrator user to connect to the NFS server. Alternatively, you can disable Direct NFS Client.

- You can have only one active Direct NFS Client implementation for each instance. Using Direct NFS Client on an instance will prevent another Direct NFS Client implementation.

**See Also:**

- [Oracle Database Reference](../refrn/ENABLE_DNFS_DISPATCHER.md) for information on setting the enable_dnfs_dispatcher parameter in the initialization parameter file to enable Direct NFS dispatcher

- [Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md) for guidelines for managing Oracle data files created with Direct NFS client.

- [Oracle Database Performance Tuning Guide](../tgdba/managing-operating-system-resources.md) for performance benefits of enabling Parallel NFS and Direct NFS dispatcher

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/considerations-asm-storage.md) for guidelines regarding managing Oracle Database data files created with Direct NFS Client or kernel NFS

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
