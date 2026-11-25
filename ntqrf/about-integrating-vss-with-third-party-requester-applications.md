Oracle VSS writer allows third-party requester applications to control the behavior of recovery and backup sessions.

Third-party requester applications use VSS API `setBackupOptions` or `setRestoreOptions` to pass an appropriate string to the writer. The writer uses `getBackupOptions` or `getRestoreOptions` to get the string set from the requester to perform the pre or post backup and restore actions.

- [Running Writer Control Commands](running-writer-control-commands.md)
  The writer control commands are applicable to all the restored components during the postrestore phase.
- [Controlling Commands for Database or All Tablespaces Component](controlling-commands-for-database-or-all-tablespaces-component.md)
  The `POST_WTRCMD=UNTIL_SNAPSHOT` command instructs the writer to perform recovery to the snapshot creation time.

**Parent topic:** [Performing Database Backup and Recovery with VSS](performing-database-backup-and-recovery-with-vss.md)
