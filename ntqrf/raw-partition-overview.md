Data files for tablespaces can be stored on a file system or on raw partitions. A raw partition is a portion of a physical disk that is accessed at the lowest possible level.

Input/output (I/O) to a raw partition offers approximately a 5% to 10% performance improvement over I/O to a partition with a file system on it.

- [About Physical Disk](about-physical-disk.md)
  A physical disk represents the entire disk and points to the following:
- [About Logical Partition](about-logical-partitiion.md)
  Logical partitions point to drives other than `\Device\Harddisk``x``\Partition0`.
- [About Physical Disk and Logical Partition Considerations](about-physical-disk-and-logical-partition-considerations.md)
  Consider the following when deciding which raw partition to use:
- [About Compatibility Issues](about-compatibility-issues.md)
  You can create logical partitions, but define physical disk convention names for them. For example:

**Parent topic:** [Storing Tablespaces on Raw Partitions](storing-tablespaces-on-raw-partitions.md)
