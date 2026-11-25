## Creating Disk Partitions using the DiskPart Utility

You can also use the DiskPart utility to manage disks.

1.  From an existing node in the cluster, run the DiskPart utility as follows:
        C:\> diskpart
        DISKPART>
2.  List the available disks.
    By specifying its disk number (n), select the disk on which you want to create a partition.

        DISKPART> list disk
        DISKPART> select disk n
3.  Create an extended partition:
        DISKPART> create part ext
4.  Create a logical drive of the desired size after the extended partition is created using the following syntax:
        DISKPART> create part log [size=n] [offset=n] [noerr]
5.  Repeat steps 2 through 4 for the second and any additional partitions. An optimal configuration is one partition for the Oracle home and one partition for Oracle Database files.
6.  List the available volumes, and remove any drive letters from the logical drives you plan to use.
        DISKPART> list volume
        DISKPART> select volume n
        DISKPART> remove
7.  On each node in the cluster, ensure that the partitions are visible.
    In the Windows Disk Management snap-in, from the Action menu, choose Rescan Disks.
8.  If the disks appear with drive letters on the remote node, then remove the drive letter.
    1.  In the Windows Disk Management snap-in, select the disk that has an assigned drive letter.
    2.  Right-click the selected disk and choose Change Drive Letter and Paths...
    3.  Select the drive letter and click Remove.
    4.  Repeat these steps for each shared disk partition that has an assigned drive letter.

**Parent topic:** [Configuring Disk Partitions on Shared Storage](configuring-disk-partitions-on-shared-storage.md)
