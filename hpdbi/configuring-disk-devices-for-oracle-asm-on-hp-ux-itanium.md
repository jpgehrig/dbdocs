Complete these tasks to configure disk devices for use with Oracle Automatic Storage Management (Oracle ASM).

1.   If necessary, install the disks that you intend to use for the disk group and restart the system.
2.  Ensure the disks are available:
    This command displays information about each disk attached to the system, including the block device name (`/dev/dsk/cxtydz`).
        # /usr/sbin/ioscan -fun -C disk

    The output from this command is similar to the following:

        Class  I  H/W Path    Driver S/W State   H/W Type     Description
        ==========================================================================
        disk    0  0/0/1/0.6.0 sdisk  CLAIMED     DEVICE       HP   DVD 6x/32x
                               /dev/dsk/c0t6d0   /dev/rdsk/c0t6d0
        disk    1  0/0/1/1.2.0 sdisk  CLAIMED     DEVICE      SEAGATE ST39103LC
                               /dev/dsk/c1t2d0   /dev/rdsk/c1t2d0

    On HP-UX 11i v.3, you can also use agile view to review mass storage devices, including block devices (`/dev/disk/diskxyz`), or character raw devices (`/dev/rdisk/diskxyz`). For example:

        #>/usr/sbin/ioscan -funN -C disk
        Class I    H/W Path       Driver  S/W State H/W Type   Desc
        ===================================================================
        disk  4  64000/0xfa00/0x1 esdisk  CLAIMED    DEVICE  HP73.4GST373454LC
                   /dev/disk/disk4    /dev/rdisk/disk4
        disk 907 64000/0xfa00/0x2f esdisk  CLAIMED   DEVICE  COMPAQ MSA1000 VOLUME
                   /dev/disk/disk907  /dev/rdisk/disk907
3.  If the `ioscan` command does not display the device name information for a device that you want to use, then enter the following command to install the special device files for any new devices:
        # /usr/sbin/insf -e
4.  For each disk that you want to add to a disk group, verify that it is not already part of an LVM volume group:
        # /sbin/pvdisplay /dev/dsk/cxtydz

    If this command displays volume group information, then the disk is already part of a volume group. The disks that you choose must not be part of an LVM volume group.
    **Note:**

    If you are using different volume management software, for example VERITAS Volume Manager, then refer to the appropriate documentation for information about verifying that a disk is not in use.
5.  Change the owner, group, and permissions on the character file for each disk that you want to add to a disk group:
        # chown oracle:dba /dev/rdsk/cxtydz
        # chmod 660 /dev/rdsk/cxtydz

    **Note:**

    If you are using a multi-pathing disk driver with Oracle Automatic Storage Management, then ensure that you set the permissions only on the correct logical device name for the disk.

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
