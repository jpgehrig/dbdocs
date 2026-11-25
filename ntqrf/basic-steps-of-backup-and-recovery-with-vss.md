Learn how to perform the basic steps of backup and recovery with VSS.

The Oracle VSS writer is installed automatically as part of the database.

In the most typical backup scenario, you select the `Oracle Database` component in your VSS-enabled application and create a shadow copy. The shadow copy contains the database files, control files, and server parameter file. If the database is in `ARCHIVELOG` mode, then you can create the shadow copy when the database is open or closed; otherwise, only when closed.

In a typical recovery scenario, you select the `Oracle Database` component in your VSS-enabled application and restore it. Afterward, you can open the database either in read-only mode or with the `RESETLOGS` option. The Oracle VSS writer also supports applications that perform point-in-time recovery.

To restore a subset of database files, you can select individual components and restore them. The Oracle VSS writer performs the appropriate actions automatically in the postrestore phase so that the file can be used (or brought online) at the end of restore operation. For example, if you select a data file component for restore, then the writer automatically recovers the data file by using RMAN.

[About Installing and Uninstalling the Oracle VSS Writer Service](about-installing-and-uninstalling-the-oracle-vss-writer-service.md)

[About Backing Up a Database](about-backing-up-a-database.md)

[About Restoring and Recovering a Database](about-restoring-and-recovering-a-database.md)

**Parent topic:** [Performing Database Backup and Recovery with VSS](performing-database-backup-and-recovery-with-vss.md)
