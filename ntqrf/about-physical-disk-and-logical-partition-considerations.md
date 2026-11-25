Consider the following when deciding which raw partition to use:

- Physical disks are automatically defined by Windows to represent the entire disk, and must never be defined by the user.

- Logical partitions must be defined by the user to represent a specific partition in a disk. These partitions must be logical partitions or drives contained in an extended partition. They must never be defined as `Partition0`.

- Using an entire disk (`Partition0`) for an Oracle Database data file and using a partition that occupies the entire disk for an Oracle Database data file are notthe same thing. Even when a partition occupies the entire disk, there is still a small space on the disk that is not part of the partition.

- If you are using an entire disk for an Oracle Database data file (`Partition0`), then use the predefined physical raw names that Windows provides.

- If you are using a specific partition and it occupies the entire disk, then use a logical partition.

- If you are using a specific partition created with Windows disk-management tools, then define and use a symbolic link name rather than a logical partition number (even if it occupies the entire disk).

**Note:**

For both physical and logical raw conventions, use OCOPY to transfer the contents of a raw partition to a standard file system for backup purposes.

**Parent topic:** [Raw Partition Overview](raw-partition-overview.md)
