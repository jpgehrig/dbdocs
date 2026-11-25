## About Direct NFS Client Storage

With Oracle Database, you can store data files on a supported NFS system. You can configure Oracle Database to access NFS servers directly using an Oracle internal Direct NFS Client.

Direct NFS Client supports NFSv3, NFSv4, NFSv4.1, and pNFS protocols to access the NFS server. If Oracle Database cannot open an NFS server using Direct NFS Client, then an informational message is logged into the Oracle alert and trace files indicating that Direct NFS Client could not be established.

Starting with Oracle Database 12c Release 2, when you enable Direct NFS, you can access Direct NFS dispatcher. The Direct NFS dispatcher consolidates the number of TCP connections that are created from a database instance to the NFS server. In large database deployments, using Direct NFS dispatcher improves scalability and network performance. Parallel NFS deployments also require a large number of connections. Hence, the Direct NFS dispatcher is recommended with Parallel NFS deployments too.

Direct NFS Client supports Dispatcher or the Input/Output (I/O) infrastructure. Dispatcher enables database processes to use I/O slave processes to perform I/O operations. This limits the number of sockets and Transmission Control Protocol (TCP) connections that the Direct NFS Client requires to connect to the NFS server.

Starting with Oracle Database 12c Release 2 (12.2), Windows Direct NFS Client supports all widely accepted NFS path formats including UNIX-style NFS paths, NFS version 4, and NFS version 4.1 protocols.

The Oracle database files resident on the NFS server that are served by the Direct NFS Client can also be accessed through a third party NFS client. The volume must be mounted through CIFS or kernel NFS to enable regular windows utilities and commands, such as copy, and so on, access the database files in the remote location. Volumes mounted through CIFS cannot be used for database file storage without configuring Direct NFS Client. The atomic write requirements required for database access are not guaranteed by CIFS protocol. Consequently, CIFS can only be used for the operating system level commands, such as copy, move, and so on.

Some NFS file servers require NFS clients to connect using reserved ports. If your filer is running with reserved port checking, then you must disable it for Direct NFS Client to operate. To disable reserved port checking, consult your NFS file server documentation.

**See Also:**

- [Oracle Database Reference](../refrn/V-DNFS_SERVERS.md)

- [Oracle Database Performance Tuning Guide](../tgdba/managing-operating-system-resources.md)

- [Oracle Database Administrator's Guide](../admin/managing-data-files-and-temp-files.md)

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
