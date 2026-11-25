Use this procedure to restore a component-based backup.

To restore a component-based backup:

1.  Use a third-party VSS requester to select the `Oracle Database` component.
    The Oracle VSS writer automatically restores the data files and mounts the database.
2.  Open the database with the `RESETLOGS` option.

**Parent topic:** [Restoring a Database in NOARCHIVELOG Mode](restoring-a-database-in-noarchivelog.md)
