## Mounting NFS Storage Devices with Direct NFS Client

Direct NFS Client determines the mount point settings for the NFS storage devices based on the configuration information in `oranfstab`.

Direct NFS Client looks for the mount point entries in `ORACLE_HOME``\dbs\oranfstab`. It uses the first matched entry as the mount point.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
