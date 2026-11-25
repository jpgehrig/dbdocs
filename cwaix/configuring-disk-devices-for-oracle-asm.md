Complete these tasks to configure disk devices for use with Oracle Automatic Storage Management (Oracle ASM).

1.   If necessary, install the disks that you intend to use for the disk group and restart the system.
2.  To ensure that the disks are available, enter the following command:
        # /usr/sbin/lsdev -Cc disk

    The output from this command is similar to the following:

        hdisk0 Available 1A-09-00-8,0  16 Bit LVD SCSI Disk Drive
        hdisk1 Available 1A-09-00-9,0  16 Bit LVD SCSI Disk Drive
        hdisk2 Available 17-08-L       SSA Logical Disk Drive
3.   If a disk is not listed as available, then configure the new disks:
        # /usr/sbin/cfgmgr
4.   Enter the following command on any node to identify the device names for the physical disks that you want to use:
        # /usr/sbin/lspv | grep -i none

    This command displays information similar to the following for each disk that is not configured in a volume group:

        hdisk2     0000078752249812   None

    In this example, `hdisk2` is the device name of the disk and `0000078752249812` is the physical volume ID (PVID). The disks that you want to use may have a PVID, but they must not belong to a volume group.
5.  Enter commands similar to the following to clear the PVID from each disk device that you want to use:
        # /usr/sbin/chdev -l hdiskn -a pv=clear
6.  Enter commands similar to the following to change the owner, group, and permissions on the character file for each disk that you want to add to the disk group:
        # chown -R grid:asmadmin /dev/rhdiskn
        # chmod 660 /dev/rhdiskn

    **Note:**

    If you are using a multi-pathing disk driver with Automatic Storage Management, then ensure that you set the permissions only on the correct logical device name for the disk.

**Parent topic:** [Using Disk Groups with Oracle Database Files on Oracle ASM](using-disk-groups-for-oracle-database-data-files.md)
