## Specifying Network Paths for a NFS Server

Direct NFS Client can use up to four network paths defined in the `oranfstab` file for an NFS server.

Direct NFS Client performs load balancing across all specified paths. If a specified path fails, then Direct NFS Client reissues all outstanding requests over any remaining paths.

**Note:**

You can have only one active Direct NFS Client implementation for each instance. Using Direct NFS Client on an instance prevents the use of another Direct NFS Client implementation.

**See Also:**

[Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md) for examples of configuring network paths for Direct NFS Client attributes in an `oranfstab` file.

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
