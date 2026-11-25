Identify storage requirements and Oracle ASM disk group options.

- [Identifying Storage Requirements for Oracle Automatic Storage Management](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  To identify the storage requirements for using Oracle ASM, you must determine the number of devices and the amount of free disk space that you require.
- [Oracle Clusterware Storage Space Requirements](clusterware-storage-requirements.md)
  Use this information to determine the minimum number of disks and the minimum disk space requirements based on the redundancy type, for installing Oracle Clusterware files for Oracle Standalone Cluster deployments.
- [About the Grid Infrastructure Management Repository](about-gimr.md)
  Every Oracle Domain Services Cluster contains a Grid Infrastructure Management Repository (GIMR), but GIMR configuration is optional for Oracle Standalone Cluster.
- [Using an Existing Oracle ASM Disk Group](using-an-existing-oracle-asm-disk-group.md)
  Use Oracle Enterprise Manager Cloud Control or the Oracle ASM command line tool (`asmcmd`) to identify existing disk groups, and to determine if sufficient space is available in the disk group.
- [About Upgrading Existing Oracle Automatic Storage Management Instances](upgrading-existing-oracle-asm-instances.md)
  Oracle Automatic Storage Management (Oracle ASM) upgrades are carried out during an Oracle Grid Infrastructure upgrade.
- [Selecting Disks to use with Oracle ASM Disk Groups](selecting-disks-to-use-with-oracle-asm.md)
  If you are sure that a suitable disk group does not exist on the system, then install or identify appropriate disk devices to add to a new disk group.
- [Specifying the Oracle ASM Disk Discovery String](specifying-oracle-asm-discovery-string.md)
  When an Oracle ASM instance is initialized, Oracle ASM discovers and examines the contents of all of the disks that are in the paths that you designated with values in the `ASM_DISKSTRING` initialization parameter.
- [Creating Files on a NAS Device for Use with Oracle Automatic Storage Management](creating-files-on-a-nas-device-for-use-with-oracle-automatic-storage-management.md)
  If you have a certified NAS storage device, then you can create zero-padded files in an NFS mounted directory and use those files as disk devices in an Oracle ASM disk group.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/create-diskgroups.md)

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md)
