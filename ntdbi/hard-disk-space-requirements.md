## Hard Disk Space Requirements

Learn about the system requirements for Windows platforms that use the NT File System (NTFS).

Oracle strongly recommends that you install the Oracle database home (Oracle database binaries, trace files, and so on) on Oracle ACFS or NTFS.

The database files themselves must be placed on Oracle ASM if using Oracle ACFS; otherwise they can be placed on NTFS. Usage of Oracle ACFS and Oracle ASM or NTFS is recommended to ensure security of these files.

The NTFS system requirements are accurate than the hard disk values reported by the Oracle Universal Installer Summary window. The Summary window does not include accurate values for disk space, the space required to create a database, or the size of compressed files that are expanded on the hard drive.

The hard disk requirements for Oracle Database components include 32 MB to install Java Runtime Environment (JRE) and Oracle Universal Installer on the partition where the operating system is installed. If sufficient space is not detected, then the installation fails and an error message appears.

The following table lists the disk space requirements on NTFS for Windows x64. The starter database requires 720 MB of disk space.

The values in this table include the starter database.

Table 2-2 Windows x64 Minimum Disk Space Requirements on NTFS

| Installation Type  | TEMP Space | SYSTEM_DRIVE:\\ Program Files\Oracle\Inventory | Oracle Home | Data Files \* | Total         |
|:-------------------|:-----------|:-----------------------------------------------|:------------|:--------------|:--------------|
| Enterprise Edition | 595 MB     | 53.00 MB                                       | 6.50 GB     | 4.38 GB \*\*  | 10.88 GB \*\* |
| Standard Edition 2 | 595 MB     | 53.00 MB                                       | 6.00 GB     | 4.24 GB \*\*  | 10.24 GB \*\* |

\* Refers to the contents of the `admin, cfgtoollogs, flash_recovery_area`, and `oradata` directories in the `ORACLE_BASE` directory.

\*\* This size can be higher depending on the installation options selected, such as languages or additional components. If you choose to install Oracle Database with customized backups enabled, then include at least 2 GB extra for data file disk space.

**Parent topic:** [Oracle Database Minimum Hardware Requirements](oracle-database-minimum-hardware-requirements.md)
