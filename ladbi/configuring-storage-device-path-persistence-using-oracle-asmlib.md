## Configuring Storage Device Path Persistence Using Oracle ASMLIB

To use Oracle ASMLIB to configure Oracle ASM devices, complete the following tasks:

**Note:**

To create a database during the installation using the Oracle ASM library driver, you must choose an installation method that runs ASMCA in interactive mode. You must also change the disk discovery string to `ORCL:*`.

Oracle ASMLIB is not supported on IBM:Linux on System z and Linux for Arm (aarch64).

- [About Oracle ASM with Oracle ASMLIB](about-oracle-asm-with-oracle-asmlib.md)
  Oracle ASMLIB maintains permissions and disk labels that are persistent on the storage device, so that the label is available even after an operating system upgrade.
- [Installing and Configuring Oracle ASMLIB Software](installing-and-configuring-oracle-asmlib-software.md)
  Review this information to install and configure the Oracle Automatic Storage Management library driver software manually.
- [Configuring Disk Devices to Use Oracle ASMLIB](configuring-disk-devices-to-use-oracle-asmlib.md)
  Configure disk devices to use in an Oracle Automatic Storage Management disk group.
- [Administering Oracle ASMLIB and Disks](administering-oracle-asmlib-and-disks.md)
  Review this information to administer the Oracle Automatic Storage Management library driver and disks.
- [Deinstalling Oracle ASMLIB On Oracle Database](deinstalling-oracle-asmlib-on-oracle-database.md)
  If Oracle ASM library driver (Oracle ASMLIB) is installed but you do not use it for device path persistence, then deinstall Oracle ASMLIB:

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
