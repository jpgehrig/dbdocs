## Deploying the Oracle Memory Speed File System

Learn how to deploy the Oracle Memory Speed (OMS) file system on your persistent memory (PMEM) storage devices with a single-instance Oracle Database.

To use your single-instance Oracle Database with OMS, perform the following steps:

1.  Set-up the hardware and operating system components.
2.  Set-up the OMS file system.
3.  Deploy Oracle Database with OMS.

- [About Oracle Memory Speed](about-oms.md)
  Oracle recommends that you use Oracle Database with the Oracle Memory Speed (OMS) file system to fully utilize the potential of persistent memory (PMEM) devices safely in data centers.
- [Requirements and Guidelines for Oracle Memory Speed](guidelines-oms.md)
  Review these requirements and guidelines before you deploy Oracle Memory Speed (OMS) as your file system.
- [Setting-Up Hardware and Operating System Components for OMS](setting-up-hardware-oms.md)
  Verify if HugePages is available, configure the PMEM device, and create and mount a DAX-capable file system on the device.
- [Setting-Up the Oracle Memory Speed File System](setting-up-oms-filesystem.md)
  After configuring the system components, set up the Oracle Memory Speed (OMS) file system by creating and mounting the file system.
- [Deploying Oracle Database with Oracle Memory Speed](deploying-database-oms.md)
  Learn the steps to use Oracle Memory Speed (OMS) in Oracle Database.
- [omsfscmds Command Reference](omsfscmds_reference.md)
  Use the various `omsfscmds` commands to perform basic file system operations, such as `mkfs`, `mount`, and `umount`.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
