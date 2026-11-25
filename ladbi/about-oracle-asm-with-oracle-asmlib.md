## About Oracle ASM with Oracle ASMLIB

Oracle ASMLIB maintains permissions and disk labels that are persistent on the storage device, so that the label is available even after an operating system upgrade.

The Oracle Automatic Storage Management library driver simplifies the configuration and management of block disk devices by eliminating the need to rebind block disk devices used with Oracle Automatic Storage Management (Oracle ASM) each time the system is restarted.

With Oracle ASMLIB, you define the range of disks you want to have made available as Oracle ASM disks. Oracle ASMLIB maintains permissions and disk labels that are persistent on the storage device, so that the label is available even after an operating system upgrade.

**Note:**

If you configure disks using Oracle ASMLIB, then you must change the disk discovery string to `ORCL:*`. If the diskstring is set to `ORCL:*`, or is left empty (""), then the installer discovers these disks.

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
