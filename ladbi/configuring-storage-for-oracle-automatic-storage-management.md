## Configuring Storage for Oracle Automatic Storage Management

Identify storage requirements and Oracle ASM disk group options.

**Note:**

Oracle ASM Filter Driver (ASMFD) is deprecated on both Linux and Oracle Solaris beginning with Oracle Database 19c. It will be desupported in a future release.

On Linux systems running kernel 5.14 or higher (including Oracle Linux, RedHat Enterprise Linux, and SUSE Linux Enterprise Server), ASMFD filtering is already disabled and will not be supported going forward. Oracle recommends moving to ASMlib v3 for those environments, as it provides equivalent functionality. For details, see My Oracle Support Note Document 2806979.1. Migration steps are available. On Oracle Solaris, ASMFD is deprecated, but remains fully supported. No immediate action is required until a formal desupport notice is issued.

- [Identifying Storage Requirements for Oracle Automatic Storage Management](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  To identify the storage requirements for using Oracle ASM, you must determine the number of devices and the amount of free disk space that you require.
- [Oracle ASM Disk Space Requirements](disk_space_requirements_for_oracle_asm.md)
  Determine the total amount of Oracle Automatic Storage Management (Oracle ASM) disk space that you require for the database files and recovery files.
- [ASM Disk Group Options for Installation](asm-disk-group-options-for-interactive-and-noninteractive-installation.md)
  Plan how you want to configure Oracle ASM disk groups for deployment.
- [Using an Existing Oracle ASM Disk Group](using-an-existing-oracle-asm-disk-group.md)
  Use Oracle Enterprise Manager Cloud Control or the Oracle ASM command line tool (`asmcmd`) to identify existing disk groups, and to determine if sufficient space is available in the disk group.

**Related Topics**

- [Migrating from Oracle ASM Filter Driver to Oracle ASMLib](../cwlin/migrating-from-asmfd-to-asmlib.md)
- [Oracle Automatic Storage Management Filter Driver (ASMFD) (Doc ID 2806979.1)](https://support.oracle.com/rs?type=doc&id=2806979.1)
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/create-diskgroups.md)

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
