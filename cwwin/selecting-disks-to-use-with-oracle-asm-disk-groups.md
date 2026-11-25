## Selecting Disks to use with Oracle ASM Disk Groups

If you are sure that a suitable disk group does not exist on the system, then install or identify appropriate disk devices to add to a new disk group.

Use the following guidelines when identifying appropriate disk devices:

- All of the devices in an Oracle ASM disk group should be the same size and have the same performance characteristics.

- Do not specify multiple partitions on a single physical disk as a disk group device. Oracle ASM expects each disk group device to be on a separate physical disk.

- Nonshared logical partitions are not supported with Oracle RAC. To use logical partitions for your Oracle RAC database, you must use shared logical volumes created by a logical volume manager such as `diskpart.exe`.

- Although you can specify a logical volume as a device in an Oracle ASM disk group, Oracle does not recommend their use because it adds a layer of complexity that is unnecessary with Oracle ASM. In addition, Oracle RAC requires a cluster logical volume manager in case you decide to use a logical volume with Oracle ASM and Oracle RAC.

**Related Topics**

- [Preliminary Shared Disk Preparation](preliminary-shared-disk-preparation.md)
- [Configuring Disk Partitions on Shared Storage](configuring-disk-partitions-on-shared-storage.md)

**Parent topic:** [Preparing Your System to Use Oracle ASM for Shared Storage](preparing-your-system-to-use-oracle-asm-for-shared-storage.md)
