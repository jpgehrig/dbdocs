## Preparing Your System to Use Oracle ASM for Shared Storage

To use Oracle ASM as the shared storage solution for Oracle Clusterware or Oracle RAC files, you must perform certain tasks before you begin the software installation.

- [Identifying and Using Existing Oracle Database Disk Groups on Oracle ASM](identifying-existing-oracle-asm-disk-groups-to-use.md)
  Identify existing disk groups and determine the free disk space that they contain. Optionally, identify failure groups for the Oracle ASM disk group devices.
- [Selecting Disks to use with Oracle ASM Disk Groups](selecting-disks-to-use-with-oracle-asm-disk-groups.md)
  If you are sure that a suitable disk group does not exist on the system, then install or identify appropriate disk devices to add to a new disk group.
- [Specifying the Oracle ASM Disk Discovery String](specifying-the-oracle-asm-disk-discovery-string.md)
  When an Oracle ASM instance is initialized, Oracle ASM discovers and examines the contents of all of the disks that are in the paths that you designated with values in the `ASM_DISKSTRING` initialization parameter.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-asm.md)
