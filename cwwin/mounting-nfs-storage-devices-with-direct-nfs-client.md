## Mounting NFS Storage Devices with Direct NFS Client

Direct NFS Client determines mount point settings for NFS storage devices based on the configuration information in oranfstab. Direct NFS Client uses the first matching entry as the mount point.

If Oracle Database cannot open an NFS server using Direct NFS Client, then an error message is written into the Oracle alert and trace files indicating that Direct NFS Client could not be established.

**Note:**

You can have only one active Direct NFS Client implementation for each instance. Using Direct NFS Client on an instance will prevent another Direct NFS Client implementation.

Direct NFS Client requires an NFS server supporting NFS read/write buffers of at least 16384 bytes.

Direct NFS Client issues writes at wtmax granularity to the NFS server. Direct NFS Client does not serve an NFS server with a wtmax less than 16384. Oracle recommends that you use the value 32768.

**See Also:**

"[Supported Storage Options for Oracle Grid Infrastructure and Oracle RAC](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)" for a list of the file types that are supported with Direct NFS Client.

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
