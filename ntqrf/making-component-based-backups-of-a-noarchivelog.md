For an Oracle database in `NOARCHIVELOG` mode, the only supported component-based VSS snapshot is of `Oracle Database` when the type is full, default, or copy.

To back up the database by component:

1.  Start a SQL\*Plus session on the target database and place the database in a consistent state. For example, enter the following commands:
        SHUTDOWN
        STARTUP MOUNT
2.  Use a third-party VSS requester to select the `Oracle Database` component.
3.  Create a volume-based VSS snapshot.
    Oracle VSS writer includes the server parameter file, control file, and data files in the snapshot. The online redo logs are not included in the snapshot.

**Parent topic:** [About Backing Up a Database in NOARCHIVELOG Mode](about-backing-up-a-database-in-noarchivelog-mode.md)
