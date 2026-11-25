Use this procedure to restore a volume-based backup.

To restore a volume-based backup:

1.  Use a third-party VSS requester to select the volumes where the data files, control files, and server parameter file are physically located.
2.  Restore all volumes where data files and logs are located.
3.  Open the database with the `RESETLOGS` option.

**Parent topic:** [Restoring a Database in NOARCHIVELOG Mode](restoring-a-database-in-noarchivelog.md)
