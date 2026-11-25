This procedure explains how to recover from the loss of all multiplexed control files.

To recover from the loss of all control files:

1.  Ensure that the database is in `NOMOUNT` state or can be started in `NOMOUNT` state by the Oracle VSS writer.
2.  Select the component named `Control File` from a VSS snapshot.
3.  Restore the component containing the lost control file.
    The Oracle VSS writer automatically mounts the database with the restored control files. If only the control file must be recovered, then the VSS requester application can ask the Oracle writer to perform complete recovery.
4.  Restore and recover other database components if necessary.
5.  Open the database with the `RESETLOGS` option.

**Parent topic:** [About Restoring and Recovering a Database in ARCHIVELOG Mode](about-restoring-and-recovering-a-database-in-archivelog-mode.md)
