## Marking Disk Partitions for Oracle ASM Before Installation

The only partitions that OUI displays for Windows systems are logical drives that are on disks and have been marked (or stamped) with `asmtoolg` or by Oracle Automatic Storage Management (Oracle ASM) Filter Driver.

If you chose not to use Oracle ASM Filter Driver (Oracle ASMFD) for configuring and marking the disks to use with Oracle ASM, then you must create disk partitions and use the `asmtoolg` utility to mark the disk partitions prior to installing Oracle Grid Infrastructure. You also have the option of using the `asmtoolg` utility during Oracle Grid Infrastructure for a cluster installation.

All disk names created by `asmtoolg` or `asmtool` begin with the prefix `ORCLDISK` followed by a user-defined prefix (the default is `DATA`), and by a disk number for identification purposes. You can use them as raw devices in the Oracle ASM instance by specifying a name `\\.\ORCLDISKprefix``n`, where `prefix``n` either can be DATA, or a value you supply, and where n represents the disk number.

The `asmtoolg` and `asmtool` utilities only work on partitioned disks; you cannot use Oracle ASM on unpartitioned disks. You can also use these tools to reconfigure the disks after installation. These utilities are installed automatically as part of Oracle Grid Infrastructure.

**Note:**

If user account control (UAC) is enabled, then running `asmtoolg` or `asmtool` requires administrator-level permissions.

- [Using asmtoolg to Mark Disks](using-asmtoolg-graphical-user-interface-to-mark-disks.md)
  Use `asmtoolg` (GUI version) to create device names; use `asmtoolg` to add, change, delete, and examine the devices available for use in Oracle ASM.
- [Using asmtoolg to Remove Disk Stamps](using-asmtoolg-to-remove-disk-stamps.md)
  You can use `asmtoolg` (GUI version) to delete disk stamps.
- [asmtool Command Line Reference](asmtool-command-line-reference.md)
  `asmtool` is a command-line interface for marking (or stamping) disks to be used with Oracle ASM.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-asm.md)
