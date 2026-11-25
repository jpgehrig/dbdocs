## Creating and Mounting the Oracle Memory Speed File System

Learn how to create an Oracle Memory Speed (OMS) file system and mount it.

1.  Create the mount directories and remove the write and execute permissions:
        $ mkdir /oracle/omsfs_1
        $ chmod -wx /oracle/omsfs_1
        $ mkdir /oracle/omsfs_2
        $ chmod -wx /oracle/omsfs_2
        $ ls -l /oracle

        dr--r--r-- 2 oracle dba 6 Feb 23 21:36 omsfs_1
        dr--r--r-- 2 oracle dba 6 Feb 23 21:36 omsfs_2
2.  Start the `omsfscmds` utility and create and mount the file systems using the `mkfs` and `mount` commands respectively.
        $ $ORACLE_HOME/bin/omsfscmds
        OMS> mkfs /mnt/pmem0/omsuberfile.test
        OMS:mkfs:No blocksize specified, using 4K
        OMS:mkfs: Device /mnt/pmem0/omsuberfile.test formatted with
        blocksize 4096
        OMS> mount /mnt/pmem0/omsuberfile.test /oracle/omsfs_1
        OMS:mount: Mounted /mnt/pmem0/omsuberfile.test at
        /oracle/omsfs_1
        OMS> mkfs /mnt/pmem1/omsuberfile.test
        OMS:mkfs:No blocksize specified, using 4K
        OMS:mkfs: Device /mnt/pmem1/omsuberfile.test formatted with
        blocksize 4096
        OMS> mount /mnt/pmem1/omsuberfile.test /oracle/omsfs_2
        OMS:mount: Mounted /mnt/pmem1/omsuberfile.test at
        /oracle/omsfs_2
        OMS> lsmount
        fsindex : 0
        Mountpt : /oracle/omsfs_1
        Deviceid: /mnt/pmem0/omsuberfile.test
        fsindex : 1
        Mountpt : /oracle/omsfs_2
        Deviceid: /mnt/pmem1/omsuberfile.test

    Currently, the only supported block size for OMS file systems is 4 KB. In this example, the two OMS file systems are mounted and available for use. `/dev/pmem0` resides on socket 0, hence files placed in `/oracle/omsfs_1` reside in socket 0. Similarly, `/dev/pmem1` resides in socket 1, hence files placed in `/oracle/omsfs_2` are in socket 1.

    You can mount a maximum of two file systems simultaneously. This enables OMS to use PMEM devices on two socket servers.

    OMS mount points are automatically remounted if you reboot the node and restart the daemon.

**Related Topics**

- [mkfs and forcemkfs Command Reference](oms-mkfs-forcemkfs.md)
- [mount, unmount and lsmount Command Reference](oms-mount-lsmount.md)

**Parent topic:** [Setting-Up the Oracle Memory Speed File System](setting-up-oms-filesystem.md)
