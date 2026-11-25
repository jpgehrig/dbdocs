## Identifying Storage Requirements for Oracle Automatic Storage Management

To identify the storage requirements for using Oracle ASM, you must determine the number of devices and the amount of free disk space that you require. To complete this task, follow these steps:

1.  Determine whether you want to use Oracle ASM for Oracle Database files, recovery files, or both. Oracle Database files include data files, control files, redo log files, the server parameter file, and the password file.
    During the database installation, you have the option to select either a file system or Oracle ASM as the storage mechanism for Oracle Database files. Similarly, you also have the option to select either a file system or Oracle ASM as the storage mechanism for your recovery files.

    **Note:**

    You do not have to use the same storage mechanism for both Oracle Database files and recovery files. You can use a file system for one file type and Oracle ASM for the other.

    If you select Oracle ASM as your storage option for Oracle Database files, then depending on your choice in the Specify Recovery Options screen, you have the following recovery options:

    - If you select the Oracle ASM option for your recovery files, then Oracle Universal Installer provides you with only the option to use the same disk group for both Oracle Database files and recovery files.

    - If you decide not to enable recovery during the database installation, then, after the database installation, you can modify the `DB_RECOVERY_FILE_DEST` parameter to enable the fast recovery area.
2.  Choose the Oracle ASM redundancy level to use for each Oracle ASM disk group that you create.
    The redundancy level that you choose for the Oracle ASM disk group determines how Oracle ASM mirrors files in the disk group and determines the number of disks and amount of disk space that you require, as follows:

    - External redundancy

      This option does not allow Oracle ASM to mirror the contents of the disk group. Oracle recommends that you select this redundancy level either when the disk group contains devices, such as RAID devices, that provide their own data protection or when the database does not require uninterrupted access to data.

    - Normal redundancy

      To optimize performance and reliability in a normal redundancy disk group, Oracle ASM uses two-way mirroring for data files and three-way mirroring for control files, by default. In addition, you can choose the mirroring characteristics for individual files in a disk group.

      A normal redundancy disk group requires a minimum of two failure groups (or two disk devices) if you are using two-way mirroring. The effective disk space in a normal redundancy disk group is half the sum of the disk space of all of its devices.

      For most installations, Oracle recommends that you use normal redundancy disk groups. On Oracle Exadata, Oracle recommends that you use high redundancy disk groups for added protection against failure.

    - High redundancy

      The contents of the disk group are three-way mirrored by default. To create a disk group with high redundancy, you must specify at least three failure groups (a minimum of three devices).

      Although high-redundancy disk groups provide a high level of data protection, you must consider the higher cost of additional storage devices before deciding to use this redundancy level.

    - Flex redundancy

      A flex redundancy disk group is a new disk group type with features such as flexible file redundancy, mirror splitting, and redundancy change. A flex disk group can consolidate files with different redundancy requirements into a single disk group. It also provides the capability for databases to change the redundancy of its files.

      For database data, you can choose no mirroring (unprotected), two-way mirroring (mirrored), or three-way mirroring (high). A flex redundancy disk group requires a minimum of three disk devices (or three failure groups).
3.  Determine the total amount of disk space that you require for the database files and recovery files.
    If an Oracle ASM instance is running on the system, then you can use an existing disk group to meet these storage requirements. If necessary, you can add disks to an existing disk group during the database installation.

    See, "Oracle ASM Disk Space Requirements" in Oracle Database Installation Guide for the Oracle ASM disk space requirements.

    **Note:**

    - The disk devices must be owned by the user performing the grid installation.

      Check with your system administrator to determine if the disks used by Oracle ASM are mirrored at the storage level. If so, select External for the redundancy. If the disks are not mirrored at the storage level, then select Normal for the redundancy.

    - Every Oracle ASM disk is divided into allocation units (AU). An allocation unit is the fundamental unit of allocation within a disk group. You can select the AU Size value from 1, 2, 4, 8, 16, 32 or 64 MB, depending on the specific disk group compatibility level. The default value is 4 MB for flex disk group and 1 MB for all other disk group types. On engineered systems, the default value is 4 MB.
4.  Optionally, identify failure groups for the Oracle ASM disk group devices.
    If you intend to use a normal, high or flex redundancy disk group, then you can further protect your database against hardware failure by associating a set of disk devices in a custom failure group. By default, each device comprises its own failure group. However, if two disk devices in a normal redundancy disk group are attached to the same Host Bus Adapter (HBA), then the disk group becomes unavailable if the controller fails. The controller in this example is a single point of failure.

    To protect against failures of this type, use two HBAs, each with two disks, and define a failure group for the disks attached to each controller. This configuration enables the disk group to tolerate the failure of one HBA.

    Consider the following guidelines while defining custom failure groups:

    - Starting with release 12.2, you can specify custom failure groups in the Create ASM Disk Group screen during an Oracle Grid Infrastructure installation.

    - You can also define custom failure groups after installation, using the GUI tool ASMCA, the command line tool `asmcmd`, or SQL commands.

    - If you define custom failure groups, then for failure groups containing database files only, you must specify a minimum of two failure groups for normal redundancy disk groups and three failure groups for high redundancy disk groups.
5.  If you are sure that a suitable disk group does not exist on the system, then install or identify appropriate disk devices to add to a new disk group.
    Use the following guidelines when identifying appropriate disk devices:

    - The disk devices must be owned by the user performing the Oracle Grid Infrastructure installation.

    - All the devices in an Oracle ASM disk group must be the same size and have the same performance characteristics.

    - Do not specify multiple partitions on a single physical disk as a disk group device. Oracle ASM expects each disk group device to be on a separate physical disk.

    - Although you can specify a logical volume as a device in an Oracle ASM disk group, Oracle does not recommend their use because it adds a layer of complexity that is unnecessary with Oracle ASM. Oracle recommends that if you choose to use a logical volume manager, then use the logical volume manager to represent a single logical unit number (LUN) without striping or mirroring, so that you can minimize the effect on storage performance of the additional storage layer.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-filegroups.md)

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
