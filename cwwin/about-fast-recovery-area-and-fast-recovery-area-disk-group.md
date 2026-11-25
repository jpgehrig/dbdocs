## About the Fast Recovery Area and the Fast Recovery Area Disk Group

The fast recovery area is a unified storage location for all Oracle Database files related to recovery.

Database administrators can define the `DB_RECOVERY_FILE_DEST` parameter to the path for the fast recovery area to enable on-disk backups, and rapid recovery of data. Enabling rapid backups for recent data can reduce requests to system administrators to retrieve backup tapes for recovery operations.

When you enable the fast recovery area in the database initialization parameter file, all RMAN backups, archive logs, control file automatic backups, and database copies are written to the fast recovery area. RMAN automatically manages files in the fast recovery area by deleting obsolete backups and archive files that are no longer required for recovery.

To use a fast recovery area in Oracle RAC, you must place it on an Oracle ASM disk group, a cluster file system, or on a shared directory that is configured through Direct network file system (NFS) for each Oracle RAC instance. In other words, the fast recovery area must be shared among all of the instances of an Oracle RAC database. Oracle Clusterware files and Oracle Database files can be placed on the same disk group as fast recovery area files. However, Oracle recommends that you create a separate fast recovery area disk group to reduce storage device contention.

The fast recovery area is enabled by setting the parameter `DB_RECOVERY_FILE_DEST` to the same value on all instances. The size of the fast recovery area is set with the parameter `DB_RECOVERY_FILE_DEST_SIZE`. As a general rule, the larger the fast recovery area, the more useful it becomes. For ease of use, Oracle recommends that you create a fast recovery area disk group on storage devices that can contain at least three days of recovery information. Ideally, the fast recovery area should be large enough to hold a copy of all of your data files and control files, the online redo logs, and the archived redo log files needed to recover your database using the data file backups kept under your retention policy.

Multiple databases can use the same fast recovery area. For example, assume you have created one fast recovery area disk group on disks with 150 gigabyte (GB) of storage, shared by three different databases. You can set the size of the fast recovery area for each database depending on the importance of each database. For example, if `test1` is your least important database, you might set `DB_RECOVERY_FILE_DEST_SIZE` to 30 GB. For the `products` database, which is of greater importance, you might set `DB_RECOVERY_FILE_DEST_SIZE` to 50 GB. For the `orders`, which has the greatest importance, you might set `DB_RECOVERY_FILE_DEST_SIZE` to 70 GB.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/create-diskgroups.md) for information on how to create a disk group for data and a disk group for the fast recovery area

**Parent topic:** [Create a Fast Recovery Area Disk Group](create-a-fast-recovery-area-disk-group.md)
