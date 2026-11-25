Complete these procedures to use file system storage for Oracle Database.

For optimal database organization and performance, Oracle recommends that you install data files and the Oracle Database software in different disks.

- [Configuring NFS Buffer Size Parameters for Oracle Database](configuring-nfs-buffer-size-parameters-for-oracle-database.md)
  Set the values for the NFS buffer size parameters rsize and wsize to 32768.
- [Checking TCP Network Protocol Buffer for Direct NFS Client](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
  Check your TCP network buffer size to ensure that it is adequate for the speed of your servers.
- [Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md)
  Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.
- [Enabling and Disabling Direct NFS Client Control of NFS](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
  By default, Direct NFS Client is installed in a disabled state with single-instance Oracle Database installations. Before enabling Direct NFS, you must configure an `oranfstab` file.
- [Enabling HCC on Direct NFS Client](enabling-hcc-on-direct-nfs-client.md)
  Perform these steps to enable Hybrid Columnar Compression (HCC) on Direct NFS Client:
