## Setting-Up a DAX-Capable File System

Learn how to create and mount a DAX-capable file system.

The XFS file system features DAX-capable mounts. Ensure that XFS creates mappings from the physical pages in the PMEM device to virtual pages using HugePages mappings.

1.  Create an XFS file system with the data partition as the real time device and an extent size of 2 MiB. Configuring the data partition as a real time device guarantees 2 MiB aligned extents.
        # mkfs.xfs -f -m rmapbt=0,reflink=0 -d rtinherit=1 -r rtdev=/dev/pmem0p2,extsize=2m /dev/pmem0p1
        meta-data=/dev/pmem0p1           isize=256    agcount=4, agsize=2097152 blks
                 =                       sectsz=4096  attr=2, projid32bit=1
                 =                       crc=0        finobt=0, sparse=0, rmapbt=0, reflink=0
        data     =                       bsize=4096   blocks=8388608, imaxpct=25
                 =                       sunit=0      swidth=0 blks
        naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
        log      =internal log           bsize=4096   blocks=4096, version=2
                 =                       sectsz=4096  sunit=1 blks, lazy-count=1
        realtime =/dev/pmem0p2           extsz=2097152 blocks=381771264, rtextents=745647
2.  Mount the Persistent Memory (PMEM) device with DAX option using the following real time device mount options.
        # mount /dev/pmem0p1 /mnt/pmem0 -o dax,rtdev=/dev/pmem0p2
3.  Verify if the file system is mounted with the `dax` option.
        # mount | grep dax

        /dev/pmem0p1 on /mnt/pmem0 type xfs (rw,relatime,attr2,dax,inode64,rtdev=/dev/pmem0p2,noquota)
4.  Format the `/dev/pmem1` device and mount and verify the `dax` option in the mount point.
        # mkfs.xfs -f -m rmapbt=0,reflink=0 -d rtinherit=1 -r rtdev=/dev/pmem1p2,extsize=2m /dev/pmem1p1

        # mount /dev/pmem1p1 /mnt/pmem1 -o dax,rtdev=/dev/pmem1p2

        # mount | grep dax

        /dev/pmem0p1 on /mnt/pmem0 type xfs (rw,relatime,attr2,dax,inode64,rtdev=/dev/pmem0p2,noquota)
        /dev/pmem1p1 on /mnt/pmem1 type xfs (rw,relatime,attr2,dax,inode64,rtdev=/dev/pmem1p2,noquota)

**Parent topic:** [Setting-Up Hardware and Operating System Components for OMS](setting-up-hardware-oms.md)
