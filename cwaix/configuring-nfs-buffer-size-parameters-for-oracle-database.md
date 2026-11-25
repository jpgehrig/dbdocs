Set the values for the NFS buffer size parameters rsize and wsize to 32768.

For example, to use `rsize` and `wsize` buffer settings with the value 32768 for an Oracle Database data files mount point, set mount point parameters to values similar to the following:

    /NFS_mount:
    dev = "/NFS_mount"
    vfs = nfs
    nodename = NFS_server
    mount = true
    options = bg,soft,intr,rsize=32768,wsize=32768
    account = false

Direct NFS Client issues writes at `wtmax` granularity to the NFS server.

**Related Topics**

- [My Oracle Support note 359515.1](https://support.oracle.com/rs?type=doc&id=359515.1)

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
