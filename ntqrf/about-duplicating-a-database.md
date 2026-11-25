If your VSS shadow copies are transportable, then you can use these shadow copies to duplicate the primary database.

In the context of this chapter, duplication refers to the creation of a new database out of the shadow copies for a different database. A duplicate database created from shadow copies can either be a nonstandby database or a standby database for use in a Data Guard environment. Note that RMAN duplication, which makes use of the `DUPLICATE` command, is a different procedure.

- [Creating a Nonstandby Database from Shadow Copies](creating-a-nonstandby-database-from-shadow-copies.md)
  Use this procedure to create a nonstandby database from shadow copies.
- [Creating a Standby Database From Shadow Copies](creating-a-standby-database-from-shadow-copies.md)
  Use this procedure to create a standby database from shadow copies.

**Parent topic:** [Performing Database Backup and Recovery with VSS](performing-database-backup-and-recovery-with-vss.md)
