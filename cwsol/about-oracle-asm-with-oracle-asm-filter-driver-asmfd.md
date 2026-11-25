During Oracle Grid Infrastructure installation, you can choose to install and configure Oracle Automatic Storage Management Filter Driver (Oracle ASMFD). Oracle ASMFD helps prevent corruption in Oracle ASM disks and files within the disk group.

Oracle ASM Filter Driver (Oracle ASMFD) rejects write I/O requests that are not issued by Oracle software. This write filter helps to prevent users with administrative privileges from inadvertently overwriting Oracle ASM disks, thus preventing corruption in Oracle ASM disks and files within the disk group. For disk partitions, the area protected is the area on the disk managed by Oracle ASMFD, assuming the partition table is left untouched by the user.

Oracle ASMFD simplifies the configuration and management of disk devices by eliminating the need to rebind disk devices used with Oracle ASM each time the system is restarted.

If Oracle ASMLIB exists on your Linux system, then deinstall Oracle ASMLIB before installing Oracle Grid Infrastructure, so that you can choose to install and configure Oracle ASMFD during an Oracle Grid Infrastructure installation.

**Caution:**

When you configure Oracle ASM, including Oracle ASMFD, do not modify or erase the contents of the Oracle ASM disks, or modify any files, including the configuration files.

**Note:**

Oracle ASMFD is supported on Linux x86–64 and Oracle Solaris operating systems.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/administer-filter-driver.md)

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMFD](configuring-storage-device-path-persistence-using-oracle-asmfd.md)
