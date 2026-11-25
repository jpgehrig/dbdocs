Learn how to use Volume Shadow Copy Service (VSS) applications to back up and recover an Oracle Database.

- [Overview of Database Backup and Recovery with VSS](overview-of-database-backup-and-recovery-with-vss.md)
  Learn about the basic concepts and tasks involved in backup and recovery with component-based shadow copies.
- [Basic Concepts of Database Backup and Recovery with VSS](basic-concepts-of-database-backup-and-recovery-with-vss.md)
  VSS is an infrastructure on Windows server platforms that enables applications to create shadow copies.
- [Basic Steps of Backup and Recovery with VSS](basic-steps-of-backup-and-recovery-with-vss.md)
  Learn how to perform the basic steps of backup and recovery with VSS.
- [About Installing and Uninstalling the Oracle VSS Writer Service](about-installing-and-uninstalling-the-oracle-vss-writer-service.md)
  The Oracle VSS writer runs separately from the Oracle database instance. From the perspective of the database, the VSS writer is simply an OCI client.
- [About Backing Up a Database](about-backing-up-a-database.md)
  The technique for backing up a database depends on the archiving mode of the database and whether you are making a component-based or a volume-based backup.
- [About Restoring and Recovering a Database](about-restoring-and-recovering-a-database.md)
  Learn how to restore and recover VSS snapshots. As in the case of backups, the procedure depends on the archiving mode of the database and the type of snapshot that you are restoring.
- [About Integrating VSS with Third-Party Requester Applications](about-integrating-vss-with-third-party-requester-applications.md)
  Oracle VSS writer allows third-party requester applications to control the behavior of recovery and backup sessions.
- [About Duplicating a Database](about-duplicating-a-database.md)
  If your VSS shadow copies are transportable, then you can use these shadow copies to duplicate the primary database.
