Data files for tablespaces may be stored on a file system or on raw partitions.

A raw partition is a portion of a physical disk that is accessed at the lowest possible level.

UNIX supports raw partitions (logical drives). There is no limitation on the number of disk drives.

Windows is limited to using drive letters A-Z, but creating raw partitions lets you bypass the disk drive limitation and divide disks into smaller sections.

Use Windows disk management tools to create an extended partition on a physical drive. An extended partition points to raw space on the disk that can be assigned multiple logical partitions for database files.

An extended partition avoids the four-partition limit on Windows by allowing you to define large numbers of logical partitions to accommodate applications using Oracle Database. Logical partitions can then be given symbolic link names to free up drive letters.

On supported Windows operating systems, create primary partitions and logical drives in extended partitions by selecting the New Simple Volume option. To create a raw device, select Do not assign a drive letter or drive path. To mount the raw device, assign and remove a drive letter. Do not use spanned volumes or striped volumes. These options convert the volume to a dynamic disk. Oracle Automatic Storage Management does not support dynamic disks.

**Note:**

Oracle RAC is only supported on 64-bit Windows server operating systems.

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
