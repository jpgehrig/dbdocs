Oracle ASM File Access Control restricts the access of files to specific Oracle ASM clients that connect as` SYSDBA`.

An Oracle ASM client is a database, which is identified by the name of the user that owns the database instance home. Oracle ASM File Access Control uses this user name to identify a database. Oracle ASM File Access Control restricts access based on the operating system and effective user identification number of a database owner.

- [Creation of New User Groups and Users for Separation of Database Administration Duties](creation-of-new-user-groups-and-users-for-separation-of-database-administration.md)
  Oracle Database 19c provides access control to separate the roles on Windows.
- [About Disk Group User Replacement](about-disk-group-user-replacement.md)
  The identity of an Oracle ASM user can be changed from one operating system user to another operating system user.
- [About Changing File Access Control While the File is Open](about-changing-file-access-control.md)
  Oracle Database 19c enables users to change the ownership, permissions, or group membership of a file even while the file is open.

**Parent topic:** [Overview of Oracle Database on Windows Architecture](overview-of-oracle-database-on-windows-architecture.md)
