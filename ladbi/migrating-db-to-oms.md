## Migrating Oracle Database to Oracle Memory Speed

Starting with Oracle Database 19c Release Update (19.12) you can migrate your database files to Oracle Memory Speed (OMS) storage using SQL and RMAN commands.

Before you start the migration of the database files, create an OMS file system, mount it, and enable OMS on the database instance.

- [Preparing for the OMS Migration](preparing-for-oms-migration.md)
  Create and mount an Oracle Memory Speed (OMS) file system before you start the migration.
- [Adding Redo Log Files to OMS](adding-redo-to-oms.md)
  To achieve best redo performance, Oracle recommends that you add all members of a redo group to storage with similar characteristics. For Oracle Memory Speed (OMS) file system, adding all the members of the redo group to OMS provides efficient redo log write times.
- [Moving Data Files to OMS](moving-datafiles-to-oms.md)
  Use this procedure if you want to move selected data files to Oracle Memory Speed (OMS) storage.
- [Moving the Entire Database to OMS](moving-db-to-oms.md)
  Use RMAN to move the entire database to Oracle Memory Speed (OMS) if the number of data files are large or if you want to move `root` PDB files.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
