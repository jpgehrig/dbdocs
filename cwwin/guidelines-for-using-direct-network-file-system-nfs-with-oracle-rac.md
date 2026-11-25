## Guidelines for Using Direct Network File System (NFS) with Oracle RAC

Network-attached storage (NAS) systems use a network file system (NFS) to access data. You can store Oracle RAC data files and recovery files on a supported NAS server using Direct NFS Client.

NFS file systems must be mounted and available over NFS mounts before you start the Oracle RAC installation. See your vendor documentation for NFS configuration and mounting information.

Note that the performance of Oracle Database software and the databases that use NFS storage depend on the performance of the network connection between the database server and the NAS device. For this reason, Oracle recommends that you connect the database server (or cluster node) to the NAS device using a private, dedicated, network connection, which should be Gigabit Ethernet or better.

**Parent topic:** [Guidelines for Choosing a Shared Storage Option](guidelines-for-choosing-a-shared-storage-option.md)
