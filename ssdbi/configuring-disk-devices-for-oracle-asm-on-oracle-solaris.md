Complete these tasks to configure disk devices for use with Oracle Automatic Storage Management (Oracle ASM).

1.   If necessary, install the disks that you intend to use for the disk group and restart the system.
2.  Identify devices that are part of a logical volume manager (LVM) disk group:
    This command displays information about VERITAS Volume Manager disks. If you use a different LVM, then refer to the appropriate documentation for information about determining which disk devices it is managing.
        # vxdiskconfig
        # /usr/sbin/vxdisk list

    If this command displays disk group information associated with a disk device, then the disk is already part of an LVM disk group. Do not use disks that are part of an LVM disk group.
3.  Create or identify the disk slices (partitions) that you want to include in the Oracle Automatic Storage Management disk group:
    1.  List the disks attached to the system:

            # /usr/sbin/format

        The output from this command is similar to the following:

            AVAILABLE DISK SELECTIONS:
            AVAILABLE DISK SELECTIONS:
                   0. c0t0d0 < ST34321A cyl 8892 alt 2 hd 15 sec 63 >
                      /pci@1f,0/pci@1,1/ide@3/dad@0,0
                   1. c1t5d0 < SUN9.0G cyl 4924 alt 2 hd 27 sec 133 >
                      /pci@1f,0/pci@1/scsi@1/sd@5,0

        This command displays information about each disk attached to the system, including the device name. For example, `cxtydz`.

    2.  Enter the number corresponding to the disk that you want to use.

    3.  Use the `fdisk` command to create an Oracle Solaris partition on the disk if one does not already exist.

        Oracle Solaris `fdisk` partitions must start at cylinder 1, not cylinder 0. If you create an `fdisk` partition, then you must label the disk before continuing.

    4.  Enter the `partition` command, followed by the `print` command to display the partition table for the disk that you want to use.

    5.  If necessary, create a single whole-disk slice, starting at cylinder 1.

        **Note:**

        To prevent Automatic Storage Management from overwriting the partition table, you cannot use slices that start at cylinder 0 (for example, slice 2).

    6.  Make a note of the number of the slice that you want to use.

    7.  If you modified a partition table or created a new one, then enter the `label` command to write the partition table and label to the disk.

    8.  Enter q to return to the format menu.

    9.  If you have finished creating slices, then enter q to quit the `format` utility. Else, enter the disk command to select a new disk and repeat steps b to g to create or identify the slices on that disks.
4.  If you plan to use existing slices, then verify that they are not mounted as file systems:
        # df -h /tmp

    This command displays information about the slices on disk devices that are mounted as file systems. The device name for a slice includes the disk device name followed by the slice number, for example `cxtydzsn`, where `sn` is the slice number.
5.  On every node, change the owner, group, and permissions on the file for each disk slice that you want to add to a disk group:
        # chown grid:asmadmin /dev/rdsk/cxtydzs6
        # chmod 660 /dev/rdsk/cxtydzs6

    In this example, the device name specifies slice 6.

    **Note:**

    If you are using a multi-pathing disk driver with Oracle Automatic Storage Management, then ensure that you set the permissions only on the correct logical device name for the disk.

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
