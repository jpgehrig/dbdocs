## 8 Configuring Direct NFS Client for Oracle RAC Data Files

Direct NFS Client is an interface for NFS systems provided by Oracle.

- [About Direct NFS Client Storage](about-direct-nfs-client-storage.md)
  Direct NFS Client integrates the NFS client functionality directly in the Oracle software to optimize the I/O path between Oracle and the NFS server. This integration can provide significant performance improvements.
- [Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md)
  If you use Direct NFS Client, then you must create a configuration file, `oranfstab`, to specify the options, attributes, and parameters that enable Oracle Database to use Direct NFS Client.
- [Configurable Attributes for the oranfstab File](configurable-attributes-for-the-oranfstab-file.md)
  You can configure various settings in the `oranfstab` file.
- [Mounting NFS Storage Devices with Direct NFS Client](mounting-nfs-storage-devices-with-direct-nfs-client.md)
  Direct NFS Client determines mount point settings for NFS storage devices based on the configuration information in oranfstab. Direct NFS Client uses the first matching entry as the mount point.
- [Specifying Network Paths for a NFS Server](specifying-network-paths-for-a-nfs-server.md)
  Direct NFS Client can use up to four network paths defined in the `oranfstab` file for an NFS server.
- [Enabling Direct NFS Client](enabling-direct-nfs-client.md)
  You enable Direct NFS Client by running the `enable_dnfs.bat` command
- [Performing Basic File Operations Using the ORADNFS Utility](performing-basic-file-operations-using-the-oradnfs-utility.md)
  ORADNFS is a utility which enables the database administrators to perform basic file operations over Direct NFS Client on Microsoft Windows platforms.
- [Monitoring Direct NFS Client Usage](monitoring-direct-nfs-client-usage.md)
  You use data dictionary view to monitor the Direct NFS client.
- [Disabling Direct NFS Client](disabling-oracle-disk-management-control-of-nfs-for-direct-nfs-client.md)
  You disable Direct NFS Client by running the `disable_dnfs.bat` command.
