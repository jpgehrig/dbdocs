## Creating Disk Partitions Using the Disk Management Interface

Use the graphical user interface Disk Management snap-in to manage disks.

You can create either Primary partitions or Extended partitions using this method.

1.  To access the Disk Management snap-in, do one of the following:
    - Type `diskmgmt.msc` at the command prompt to create Primary partitions.

      Use the command `diskpart.exe` to create Extended partitinos.

    - From the Start menu, select Administrative Tools, then Computer Management. Then select the Disk Management node in the Storage tree.
2.  Create primary partitions and logical drives in extended partitions by selecting the New Simple Volume option.
    Use a basic disk with a Master Boot Record (MBR) partition style as an extended partition for creating partitions. Do not use spanned volumes or striped volumes. These options convert the volume to a dynamic disk. Oracle Automatic Storage Management does not support dynamic disks.
    1.  In the Assign Drive Letter or Path window, select Do not assign a drive letter or drive path
    2.  In the Format Partition window, select Do not format this volume to specify raw partition.
3.  On each node in the cluster, ensure that the partitions are visible.
    In the Disk Management snap-in, from the Action menu, choose Rescan Disks.
4.  If the disks appear with drive letters on the remote node, then remove the drive letter.
    1.  In the Disk Management snap-in, select the disk that has an assigned drive letter.
    2.  Right-click the selected disk and choose Change Drive Letter and Paths...
    3.  Select the drive letter and click Remove.
    4.  Repeat these steps for each shared disk partition that has an assigned drive letter.

**Related Topics**

- [My Oracle Support Note 782450.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=782450.1)

**Parent topic:** [Configuring Disk Partitions on Shared Storage](configuring-disk-partitions-on-shared-storage.md)
