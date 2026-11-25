## Hard Disk Space Requirements

Oracle strongly recommends that you install the Oracle database home (Oracle database binaries, trace files, and so on) on Oracle Automatic Storage Management Cluster File System (Oracle ACFS) or New Technology File System (NTFS).

The database files must be placed on Oracle Automatic Storage Management (Oracle ASM) if using Oracle ACFS or on NTFS. Oracle recommends usage of Oracle ACFS and Oracle ASM or NTFS to ensure security of these files.

The NTFS system requirements listed are more accurate than the hard disk values reported by the Oracle Universal Installer Summary window. The Summary window does not include accurate values for disk space, the space required to create a database, or the size of compressed files that are expanded on the hard drive.

The hard disk requirements for Oracle Database Client components includes space to install Java Runtime Environment (JRE) and Oracle Universal Installer on the partition where the operating system is installed. If sufficient space is not available, the installation fails and an error message appears.

The following table lists the disk space requirements on NTFS. The values in this table include the starter database.

Table 2-2 Windows x64 Disk Space Requirements on NTFS

| Installation Type                 | TEMP Space | Directory:\\ Program Files\Oracle\Inventory | Oracle Home | Total      |
|:----------------------------------|:-----------|:--------------------------------------------|:------------|:-----------|
| Instant Client                    | 136 MB     | 166 KB                                      | 361 MB      | 485 MB     |
| Administrator                     | 140 MB     | 1.6 MB                                      | 1.85 GB     | 1635 MB    |
| Runtime                           | 130 MB     | 1.55 MB                                     | 1.35 GB     | 1235 MB    |
| Custom (all components installed) | 145 MB     | 2.0 MB \*                                   | 1.86 GB \*  | 1635 MB \* |

\* Disk space requirements vary, depending on the components selected.

**Note:**

If you want to configure only the Instant Client Light component of Instant Client, then you need 30–32 MB of disk space to store the related files.

**Related Topics**

- [Configuring Instant Client Light](configuring-instant-client-light.md)

**Parent topic:** [Oracle Database Client Minimum Hardware Requirements](oracle-database-client-minimum-hardware-requirements.md)
