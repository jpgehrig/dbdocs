## Configuring File System Storage for Oracle Database

Complete these procedures to use file system storage for Oracle Database.

If you plan to place storage on Network File System (NFS) protocol devices, then Oracle recommends that you use Oracle Direct NFS (dNFS) to take advantage of performance optimizations built into the Oracle Direct NFS client.

For optimal database organization and performance, Oracle recommends that you install data files and the Oracle Database software in different disks.

- [Configuring NFS Buffer Size Parameters for Oracle Database](configuring-nfs-buffer-size-parameters-for-oracle-database.md)
  Set the values for the NFS buffer size parameters rsize and wsize to at least 32768.
- [Checking TCP Network Protocol Buffer for Direct NFS Client](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
  Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.
- [Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md)
  Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.
- [Enabling and Disabling Direct NFS Client Control of NFS](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
  Use these commands to enable or disable Direct NFS Client Oracle Disk Manager Control of NFS.
- [Enabling Hybrid Columnar Compression on Direct NFS Client](enabling-hcc-on-direct-nfs-client.md)
  Perform these steps to enable Hybrid Columnar Compression (HCC) on Direct NFS Client:

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md)
