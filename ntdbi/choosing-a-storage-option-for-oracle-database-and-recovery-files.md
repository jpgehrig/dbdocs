## Choosing a Storage Option for Oracle Database and Recovery Files

Oracle Database files include data files, control files, redo log files, the server parameter file, and the password file.

For all installations, you must choose the storage option to use for Oracle Database files. During the database installation, you must choose the storage option to use for recovery files (the fast recovery area). You do not have to use the same storage option for each file type.

**Note:**

Database files and recovery files are supported on file systems and Oracle ASM.

The storage option that you choose for recovery files can be the same as or different to the option you choose for the data files. The recovery files must be placed on Oracle ASM if using Oracle ACFS; otherwise they can be placed on NTFS.

**Parent topic:** [Configuring Disk Storage for Oracle Data Files and Recovery Files](configuring-disk-storage-data-and-recovery-files.md)
