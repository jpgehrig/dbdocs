## Configuring Disk Devices to Use Oracle ASMLIB

Configure disk devices to use in an Oracle Automatic Storage Management disk group.

To configure the disk devices to use in an Oracle Automatic Storage Management disk group, perform the following steps:

1.  If you intend to use IDE, SCSI, or RAID devices in the Oracle Automatic Storage Management disk group, then perform the following steps:

    1.  Install or configure the disk devices that you intend to use for the disk group and restart the system.

    2.  Enter the following command to identify the device name for the disks to use:

            # /sbin/fdisk -l

        Depending on the type of disk, the device name can vary.

        Table 9-3 Device Name Formats Based on Disk Type

        | Disk Type | Device Name Format                    | Description                                                                                                                                                                                                                                                                                                                           |
        |:----------|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
        | IDE disk  | `/dev/hdxn`                           | In this example, `x` is a letter that identifies the IDE disk, and `n` is the partition number. For example, `/dev/hda` is the first disk on the first IDE bus.                                                                                                                                                                       |
        | SCSI disk | `/dev/sdxn`                           | In this example, `x` is a letter that identifies the IDE disk, and `n` is the partition number. For example, `/dev/hda` is the first disk on the first IDE bus.                                                                                                                                                                       |
        | RAID disk | `/dev/rd/cxdypz`<br>`/dev/ida/cxdypz` | Depending on the RAID controller, RAID devices can have different device names. In the examples shown, `x` is a number that identifies the controller, `y` is a number that identifies the disk, and `z` is a number that identifies the partition. For example, `/dev/ida/c0d1` is the second logical drive on the first controller. |

        To include devices in a disk group, you can specify either whole-drive device names or partition device names.

        **Note:**

        Oracle recommends that you create a single whole-disk partition on each disk to use.

    3.  Use either `fdisk` or `parted` to create a single whole-disk partition on the disk devices.

2.  Enter a command similar to the following to mark a disk as an Oracle Automatic Storage Management disk:

        # /usr/sbin/oracleasm createdisk DISK1 /dev/sdb1

    In this example, `DISK1` is a name assigned to the disk.

    **Note:**

    - The disk names you specify can contain uppercase letters, numbers, and the underscore character. They must start with an uppercase letter.

    - To create a database during the installation using the Oracle Automatic Storage Management library driver, you must change the disk discovery string to `ORCL:*`.

    - If you are using a multi-pathing disk driver with Oracle ASM, then make sure that you specify the correct logical device name for the disk.

3.  To make the disk available on the other nodes in the cluster, enter the following command as `root` on each node:

        # /usr/sbin/oracleasm scandisks

    This command identifies shared disks attached to the node that are marked as Oracle ASM disks.

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
