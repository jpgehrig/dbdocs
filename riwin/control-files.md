## About Control Files

The database is configured with two control files that must be stored on shared storage.

Every database must have one unique control file; any additional control files configured for the database are identical copies of the original control file. If a control file becomes unusable, then the database instance fails when it attempts to access the damaged control file. By multiplexing (creating multiple copies of) a control file on different disks, the database can achieve redundancy and thereby avoid a single point of failure.

**See Also:**

- "[Overview of Control Files](../cncpt/physical-storage-structures.md)" in Oracle Database Concepts

- "[Managing Control Files](../admin/managing-control-files.md)" in Oracle Database Administrator's Guide

**Parent topic:** [Database Components Created Using Database Configuration Assistant](database-components-created-using-dbca.md)
