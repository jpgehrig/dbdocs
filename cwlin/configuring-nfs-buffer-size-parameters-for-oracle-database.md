## Configuring NFS Buffer Size Parameters for Oracle Database

Set the values for the NFS buffer size parameters rsize and wsize to at least 32768.

For example, to use rsize and wsize buffer settings with the value 32768 for an Oracle Database data files mount point, set mount point parameters to values similar to the following:

    nfs_server:/vol/DATA/oradata /home/oracle/netapp nfs\
    rw,bg,hard,nointr,rsize=32768,wsize=32768,tcp,actimeo=0,vers=3,timeo=600

Direct NFS Client issues writes at `wtmax` granularity to the NFS server.

**Related Topics**

- [My Oracle Support note 359515.1](https://support.oracle.com/rs?type=doc&id=359515.1)

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
