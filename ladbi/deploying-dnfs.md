## Deploying Oracle Direct NFS

If you plan to place storage on Network File System (NFS) protocol devices, then Oracle recommends that you use Oracle Direct NFS (dNFS) to take advantage of performance optimizations built into the Oracle Direct NFS client.

- [Configuring NFS Buffer Size Parameters for Oracle Database](configuring-nfs-buffer-size-parameters-for-oracle-database.md)
  Set the values for the NFS buffer size parameters rsize and wsize to at least 32768.
- [Checking TCP Network Protocol Buffer for Direct NFS Client](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
  Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.
- [Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md)
  Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.
- [Enabling and Disabling Direct NFS Client Control of NFS](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
  By default, Direct NFS Client is installed in a disabled state with single-instance Oracle Database installations. Before enabling Direct NFS, you must configure an `oranfstab` file.
- [Enabling Hybrid Columnar Compression on Direct NFS Client](enabling-hcc-on-direct-nfs-client.md)
  Perform these steps to enable Hybrid Columnar Compression (HCC) on Direct NFS Client:

**Related Topics**

- [My Oracle Support note 1496040.1](https://support.oracle.com/rs?type=doc&id=1496040.1)

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
