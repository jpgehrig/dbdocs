## 5 Configuring File System Storage for Oracle Database

Complete these procedures to use file system storage for Oracle Database.

For optimal database organization and performance, Oracle recommends that you install data files and the Oracle Database software in different disks.

If you plan to place storage on Network File System (NFS) protocol devices, then Oracle recommends that you use Oracle Direct NFS (dNFS) to take advantage of performance optimizations built into the Oracle Direct NFS client.

- [About Direct NFS Client Storage](direct-nfs-client-storage.md)
  With Oracle Database, you can store data files on a supported NFS system. You can configure Oracle Database to access NFS servers directly using an Oracle internal Direct NFS Client.
- [About the Oranfstab File for Direct NFS Client](about-oranfstab-file-for-direct-nfs-client.md)
  To enable the Direct NFS Client, you must add an `oranfstab` file to `ORACLE_HOME``\dbs`.
- [Mounting NFS Storage Devices with Direct NFS Client](mounting-nfs-storage-devices-with-direct-nfs-client.md)
  Direct NFS Client determines the mount point settings for the NFS storage devices based on the configuration information in `oranfstab`.
- [Specifying Network Paths for a NFS Server](specifying-network-paths-for-nfs-server.md)
  Direct NFS Client can use up to four network paths defined in the oranfstab file for an NFS server.
- [Creating an oranfstab File for Direct NFS Client](creating-oranfstab-file-for-direct-nfs-client.md)
  Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.
- [Performing Basic File Operations Using the ORADNFS Utility](performing-basic-file-operations-using-oradnfs-utility.md)
  ORADNFS is a utility which enables the database administrators to perform basic file operations over Direct NFS Client on Microsoft Windows platforms.
- [Monitoring Direct NFS Client Usage](monitoring-direct-nfs-client-usage.md)
  Use the following views for Direct NFS Client management:
- [Enabling Direct NFS Client](enabling-direct-nfs-client.md)
  To enable Direct NFS Client, you must add an `oranfstab` file to the `Oracle_home``\dbs` directory and modify the related DLL files used by the Oracle Database software.
- [Disabling Direct NFS Client](disabling-direct-nfs-client.md)
  Complete the following steps to disable the Direct NFS Client:
- [Enabling HCC on Direct NFS Client](enabling-hcc-on-direct-nfs-client.md)
  To enable Hybrid Columnar Compression (HCC) on Direct NFS Client, perform the following steps:

**Related Topics**

- [My Oracle Support note 1496040.1](https://support.oracle.com/rs?type=doc&id=1496040.1)
