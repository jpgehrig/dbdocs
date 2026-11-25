Use this procedure to prevent data loss.

**Note:**

If anything goes wrong while operating the new database without a backup, then you must repeat the database creation procedure. Back up your database now to prevent loss of data.

To back up the new database:

1.  Shut down the database instance and stop the service:
        C:\> oradim -SHUTDOWN -SID prod -SHUTTYPE srvc,inst -SHUTMODE immediate

    **Note:**

    Although `ORADIM` returns the prompt immediately, you must wait for the database and the service to stop completely before continuing to Step 2. Wait until the Control Panel indicates service `OracleServicePROD` has stopped. If you do not do this, then the backup is useless because it was taken while data was being written to data files.
2.  Back up database files using the tool of your choice.
    Database files consist of the initialization parameter file, control files, online redo log files, and data files.

    When the backup is complete, you can start the database again, create users and objects, if necessary, make any other changes, and use the database.

    Back up the database after making any significant changes, such as switching into the archiving mode or adding a tablespace or a data file.

    **See Also:**

    - [Oracle Database Concepts](../cncpt/concepts-for-database-administrators.md)

    - [Oracle Database Backup and Recovery User's Guide](../bradv/introduction-backup-recovery.md)

    - [Oracle Database 2 Day DBA](../admqs/performing-backup-and-recovery.md)

**Note:**

Do not store database files on a compressed drive. This can result in write errors and a decreased performance.

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
