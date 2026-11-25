A physical disk represents the entire disk and points to the following:

    \Device\Harddiskx\Partition0

Symbolic link name `\\.\PhysicalDrive``x` is automatically defined by Windows for every hard disk in the computer. For example, a computer with three hard disks have the following symbolic links:

    \\.\PhysicalDrive0
    \\.\PhysicalDrive1
    \\.\PhysicalDrive2

Internally, these names expand to the following:

    \\.\PhysicalDrive0 =\Device\Harddisk0\Partition0
    \\.\PhysicalDrive1 =\Device\Harddisk1\Partition0
    \\.\PhysicalDrive2 =\Device\Harddisk2\Partition0

`Partition0` is special, because it represents the entire physical disk regardless of any partitioning scheme on that disk. Windows writes a signature on the first block of all disks it recognizes. To avoid overwriting that block, Oracle Database skips the first block of a physical raw partition that is used for an Oracle Database data file.

**Note:**

Although you can use physical disks, Oracle recommends that you use logical partitions.

**Parent topic:** [Raw Partition Overview](raw-partition-overview.md)
