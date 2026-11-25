Logical partitions point to drives other than `\Device\Harddisk``x``\Partition0`.

They are initially assigned names with drive letters (`\\.\``drive_letter`:) and typically re-assigned symbolic link names (`\\.\``symbolic link name`). For example,` \\.\D`: may be assigned a symbolic link name of `\\.\ACCOUNTING_1`. Regardless of whether a drive letter or symbolic link name is used, logical partitions are defined to represent a specific partition in a disk rather than the entire disk. Internally, these names can expand to:

    \\.\D:= \Device\Harddisk2\Partition1
    \\.\ACCOUNTING_1= \Device\Harddisk3\Partition2

**Note:**

Oracle Database does not skip the first block of a logical raw partition used for an Oracle Database data file.

**Parent topic:** [Raw Partition Overview](raw-partition-overview.md)
