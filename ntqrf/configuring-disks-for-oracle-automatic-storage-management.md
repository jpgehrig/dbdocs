To use Oracle Automatic Storage Management with direct attached storage (DAS) or storage area network (SAN) storage, the disks must be stamped with a header by `asmtool` or `asmtoolg` (GUI version).

Each DAS or SAN disk must have a partition table. Oracle recommends creating exactly one partition for each disk containing the entire disk. Use Microsoft Computer Management or the command-line tool `diskpart` to create the partition. Once the partitions have been created, run `asmtoolg` or `asmtool`. These tools associate meaningful, persistent names with disks to facilitate using those disks with Oracle Automatic Storage Management. Oracle Automatic Storage Management uses disk strings to more easily operate on groups of disks at once, so the names created by `asmtool` make this easier than using Windows drive letters. All disk names created by `asmtool` begin with the prefix `ORCLDISK` for identification purposes.

Oracle Automatic Storage Management uses the value of initialization parameter `ASM_DISKSTRING` as its search path when it discovers disks. The default value of `ASM_DISKSTRING` is `\\.\ORCLDISK``n`. If you want a different search path, then you must specify a different value for this parameter.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/configuring-disks-manually-for-oracle-automatic-storage-management.md) "Step 3: Manually Configuring Disks for Oracle Automatic Storage Management" for instructions on using `asmtool` or `asmtoolg`

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/init-params-asm-instance.md)

  for information about "Initialization Parameter Files for an Oracle ASM Instance"

**Parent topic:** [Storing Tablespaces on Raw Partitions](storing-tablespaces-on-raw-partitions.md)
