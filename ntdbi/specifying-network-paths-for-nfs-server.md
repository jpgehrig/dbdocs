## Specifying Network Paths for a NFS Server

Direct NFS Client can use up to four network paths defined in the oranfstab file for an NFS server.

The Direct NFS Client performs load balancing across all specified paths. If a specified path fails, then Direct NFS Client reissues I/O commands over any remaining paths.

Direct NFS Client requires an NFS server supporting NFS read/write buffers of at least 16384 bytes.

Direct NFS Client issues writes at `wtmax` granularity to the NFS server. Direct NFS Client does not serve an NFS server with a `wtmax` less than 16384. Oracle recommends that you use the value 32768.

For NFS servers that restrict port range, you can use the `insecure` option to enable clients other than `root` to connect to the NFS server. Alternatively, you can disable Direct NFS Client.

**Note:**

Use NFS servers supported for Oracle Database. See the My Oracle Support website for support information:

[`https://support.oracle.com`](https://support.oracle.com)

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
