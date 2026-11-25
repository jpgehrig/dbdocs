Describes how to back up a 32-bit Oracle home database.

To back up:

1.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
2.  Connect to the database instance as `SYSDBA`:
        SQL> CONNECT / AS SYSDBA;
3.  Create a `.trc` file to use as a template to re-create the control files on the 64-bit computer:
        SQL> ALTER DATABASE BACKUP CONTROLFILE TO TRACE;
4.  Shut down the database:
        SQL> SHUTDOWN IMMEDIATE;
5.  Perform a full offline backup of the database.

**See Also:**

[Oracle Database Backup and Recovery User's Guide](../bradv/introduction-backup-recovery.md) for an overview of backup and recovery solutions

**Parent topic:** [Overview of Database Migration from a 32-Bit Windows Computer](overview-of-database-migration-from-a-32-bit-windows-computer.md)
