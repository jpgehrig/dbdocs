You can create logical partitions, but define physical disk convention names for them. For example:

    \\.\PhysicalDriveACCOUNTING_1 = \Device\Harddisk2\Partition1
    \\.\PhysicalDriveACCOUNTING_2 = \Device\Harddisk3\Partition1

Oracle Database then handles data files using the physical disk convention even though it really is a logical partition. This does not cause any data corruption or loss as long as you continue to use physical disk naming conventions. Oracle recommends that you convert to the logical partition at your earliest convenience.

You can also create logical names representing `Partition0`, but this is definitely not recommended. For example:

    \\.\ACCOUNTING_1 = \Device\Harddisk1\Partition0

This poses severe problems, because Disk Management typically writes a signature into the first block of every disk, and consequently may overwrite a portion of the data file header. It can also cause data loss. Never use `Partition0` with the logical partition convention.

Physical and logical partition conventions are not compatible with one another because of the extra block that is skipped for physical raw conventions. This also means you cannot simply use OCOPY to copy from a physical disk to a logical partition, because contents of these partitions are incompatible.

To convert from a physical convention to a logical convention, you must:

1.  Perform a full database export to a (local) file system.

2.  Create logical partitions and define logical names for these partitions.

3.  Recreate the database by using the new logical partitions.

4.  Perform the full database import to the newly-created database.

If your database installation uses physical disk conventions with logical partitions, Oracle recommends converting to the logical partition conventions at your earliest convenience, using the preceding steps.

**See Also:**

Your operating system documentation for information about creating extended and logical partitions

**Parent topic:** [Raw Partition Overview](raw-partition-overview.md)
