## ASM Disk Group Options for Interactive and Noninteractive Installation

You can select new disk groups during interactive installations, but you must use existing disk groups for noninteractive installations.

Select from the following choices to store either database or recovery files in an existing Oracle ASM disk group, depending on installation method:

- Installation method that runs Database Configuration Assistant in an interactive mode (either during installation or after installation)

  - Select new Disk Group

  - Select existing Disk Group

- Installation method that runs Database Configuration Assistant in a noninteractive mode (either during installation or after installation)

  Select an existing Disk Group only. You cannot create a disk group during noninteractive installations. You can add disk devices to an existing disk group if it has insufficient free space.

**Note:**

The Oracle ASM instance that manages the existing disk group can be running in a different Oracle home directory.

### Step 1: Enabling Disk Automounting

Before you can configure partitions or logical drives on Windows, you must enable disk automounting. Enable disk automounting when using:

- Disk partitions on both single-instance and Oracle RAC installations

- Cluster file system for Oracle RAC

- Oracle Clusterware

- Raw partitions for a single-node database installation

- Primary or logical partitions for Oracle Automatic Storage Management

To enable automounting:

1.  Enter the following commands at a command prompt:

        DRIVE_LETTER:\> diskpart
        DISKPART> automount enable
        DISKPART> exit

2.  Restart your computer.

### Step 2: Creating the Disk Partitions

To create disk partitions, use the disk administration tools provided by the operating system or third party vendors. The following administration tools are provided by the operating system:

- The graphical user interface Disk Management snap-in to manage disks.

  To access this tool, type `diskmgmt.msc` at the command prompt. (Optional) From the Start menu, select All Programs, then Administrative Tools, then Computer Management. Then select the Disk Management node in the Storage tree.

  Create primary partitions and logical drives in the extended partitions by selecting the New Simple Volume option. To create a raw device, assign a drive letter and remove the letter after the partition is created. You must select Do not format this partition to specify a raw partition. Do not use spanned volumes or striped volumes. These options convert the volume to a dynamic disk. Oracle Automatic Storage Management does not support dynamic disks.

  For other Windows, create primary partitions by selecting the New Partition option. Create the logical drives by selecting the New Logical Drive option.

- The command-line tool `diskpart.exe`, which lets you create primary partitions, extended partitions, and logical drives.

  To access this tool, enter `diskpart.exe` at the command prompt. The syntax for using `diskpart.exe` for the procedures in this section is as follows:

      DRIVE_LETTER:\> diskpart
      DISKPART> select disk diskn
      DISKPART> create partition primary | extended | logical size=sizen
      DISKPART>

  where:

  - `diskpart.exe` is the command-line tool for managing disks.

  - `diskn` is the disk number where the partitions are created.

  - `sizen` is the size of the partition, for example 500 represents 500 MB.

**See Also:**

The online help or documentation for the administration tool that you are using

You can enter the `diskpart.exe` commands directly at the command line. Alternatively, you can enter the commands in a text file, and then run `diskpart /s` using this file as a script.

You cannot create more than four primary disk partitions per disk. If you need more, you can get around this limitation by creating three primary partitions and then the fourth as an extended partition with as many logical partitions.

For example, to create the disk partitions on Disk 5 and assign them each a size:

    DISKPART> select disk 5
    DISKPART> create partition primary size=500
    DISKPART> ...
    DISKPART> create partition extended
    DISKPART> create partition logical size=800
    DISKPART> ...
    DISKPART> create partition logical size=500

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
