This chapter introduces you to Oracle Database backup and recovery with Oracle Recovery Manager (RMAN). After reading this chapter, you should be familiar with the basic concepts of Oracle Database backup and recovery operations, know how to implement a disk-based backup strategy, and perform simple repairs to database files.

This chapter contains the following sections:

- Overview of Database Backup and Recovery

- Database Backup and Recovery Concepts

- Configuring Your Database for Basic Backup and Recovery

- Backing Up Your Database

- Displaying Backup Reports

- Managing Backups

- Performing Oracle Advised Recovery

- Performing User-Directed Recovery

- Performing Backup and Recovery: Oracle By Example Series

**See Also:**

- [Oracle Database Backup and Recovery User's Guide](../bradv/introduction-backup-recovery.md) for information about using RMAN to perform advanced backup and recovery operations

- [Oracle Database Backup and Recovery Reference](../rcmrf/about-rman-commands.md) for the syntax and semantics of RMAN commands

### 9.1 Overview of Database Backup and Recovery

The focus in Oracle Database backup and recovery is on the physical backup of database files, which permits you to reconstruct your database.

Oracle Recovery Manager (RMAN), a command-line tool, is the method preferred by Oracle for efficiently backing up and recovering your Oracle database. The files protected by the backup and recovery facilities built into RMAN include data files, control files, server parameter files, and archived redo log files. With these files you can reconstruct your database. RMAN is designed to work intimately with the server, providing block-level corruption detection during backup and restore. RMAN optimizes performance and space consumption during backup with file multiplexing and backup set compression, and integrates with leading tape and storage media products. The backup mechanisms work at the physical level to protect against file damage, such as the accidental deletion of a data file or the failure of a disk drive. RMAN can also be used to perform point-in-time recovery to recover from logical failures when other techniques such as flashback cannot be used.

Logical backups, such as exporting database objects such as tables or tablespaces, are a useful supplement to physical backups, but cannot protect your whole database. An effective backup strategy must be based on physical backups.

The Oracle Database flashback features provide a range of physical and logical data recovery tools as efficient, easy-to-use alternatives to physical and logical backups. The flashback features enable you to reverse the effects of unwanted database changes without restoring data files from backup.

This section provides links to the following flashback features that are documented in [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-performing-flashback-dbpitr.md):

- [Oracle Flashback Table](../bradv/rman-performing-flashback-dbpitr.md), which enables you to revert a table to its contents at a time in the recent past

- [Oracle Flashback Drop](../bradv/rman-performing-flashback-dbpitr.md), which enables you to retrieve deleted (dropped) database tables

- [Oracle Flashback Database](../bradv/rman-performing-flashback-dbpitr.md), which enables you to revert the entire database to a past point in time

The first two features operate at the logical level, whereas the last feature operates at the physical level. None of the preceding features requires advance preparation such as creating logical exports to allow for retrieval of your lost data, but Oracle Flashback Database requires the advance preparation of enabling the feature. You can use all of the features while your database is available. [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-performing-flashback-dbpitr.md) discusses the flashback features of Oracle Database at greater length.

**Note:**

Oracle Flashback Database does not recover missing data files.

#### 9.1.1 Overview of Backing Up and Recovering CDBs and PDBs

When using the multitenant architecture, you can perform backup and recovery operations on a whole multitenant container database (CDB), the root, or one or more pluggable databases (PDBs).

The Oracle Recovery Manager (RMAN) commands used to backup and recover CDBs and PDBs are the same as those used for non-CDBs, with minor variations in the syntax. The backup and recovery operations performed on non-CDBs can also be performed on CDBs and PDBs. This includes the following:

- Full and incremental backups

- Complete and point-in-time recovery (PITR)

- Flashback Database

- Reporting operations (such as listing backups and cross-checking backups)

##### About Connecting to CDBs and PDBs

You can connect to the root in one of the following ways:

- Connect using operating system authentication

  You are connected to the root as the `SYS` user with the `SYSDBA` privilege.

- Connect locally as a common user

- Connect as a common user through Oracle Net Services

To connect as `TARGET` to a PDB, use one of the following techniques:

- Connect with a net service name that resolves to a database service for that PDB

- Connect locally as a common user or local user with the `SYSDBA` or `SYSBACKUP` privilege

**Note:**

Certain operations are not available when you connect directly to a PDB. See [Oracle Database Backup and Recovery User’s Guide](../bradv/starting-interacting-with-rman-client.md) for a list of these operations.

**See Also:**

The following sections in the Oracle Database Backup and Recovery User’s Guide provide detailed information about backing up and recovering PDBs:

- [Connecting as Target to the Root](../bradv/starting-interacting-with-rman-client.md)

- [Connecting as Target to a PDB](../bradv/starting-interacting-with-rman-client.md)

##### 9.1.1.1 Backup and Complete Recovery of CDBs

To perform backup and complete recovery operations on a whole multitenant container database (CDB), you connect as `TARGET` to the root.

The connection must be established as a common user with the `SYSDBA` or `SYSBACKUP` privilege.

After you connect to the root, the same commands that are used to perform operations on non-CDBs are used to perform backup and complete recovery on the entire CDB.

**See Also:**

The following sections in the Oracle Database Backup and Recovery User’s Guide provide detailed information about performing backup and complete recovery of CDBs:

- "[Backing Up a Whole CDB](../bradv/backing-up-database.md)"

- "[Performing Complete Recovery of a Whole CDB](../bradv/rman-complete-database-recovery.md)"

- "[Validating a Whole CDB](../bradv/validating-database-files-backups.md)"

- "[Reporting in CDBs](../bradv/reporting-rman-operations.md)"

##### 9.1.1.2 Backup and Complete Recovery of PDBs

You can perform backup and complete recovery operations on a single pluggable database (PDB) or on multiple PDBs.

##### Backups of PDBs

When relocating a PDB or cloning a non-CDB as a PDB, you may want to retain the use of preplugin backups. For preplugin backups to be usable in the destination CDB, metadata about the preplugin backups must be exported to the RMAN repository of the destination CDB.

The technique for making the backups usable depends on the type of operation:

- Creating a PDB by cloning a non-CDB

  When the non-CDB is opened in read/write mode, you must execute the `DBMS_PDB.EXPORTRMANBACKUP` procedure as the last step before cloning. When plugging in the non-CDB as a PDB to a destination CDB, the operation copies the backup metadata of the source non-CDB into the data dictionary of the destination CDB.

- Relocating a PDB to another CDB

  When you unplug the source PDB, the backup metadata is automatically exported. Therefore, you do not need to execute `DBMS_PDB.EXPORTRMANBACKUP`.

Preplugin backups are usable only on the destination CDB into which you plug in the source non-CDB or PDB.

**Note:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-backup-concepts.md) to learn about preplugin backups

- [Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md) to learn how to create a preplugin backup of the whole database

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PDB.md) to learn more about the `DBMS_PDB.EXPORTRMANBACKUP` procedure

##### Syntax for Backup Commands

Although the Oracle Recovery Manager (RMAN) commands are the same, the syntax used to perform operations on multiple PDBs contains some modifications.

To perform backup and complete recovery operations on a single PDB, you can connect as `TARGET` to either of the following containers:

- PDB

  In this case, use the same commands that you would use to backup or recover non-CDBs. For example, to back up a PDB, use the `BACKUP DATABASE` command.

- `CDB$ROOT`

  In this case, use the `PLUGGABLE DATABASE` clause in your RMAN commands. The following command backs up the PDB `hrpdb` when connected to the root:

      BACKUP PLUGGABLE DATABASE hrpdb;

  To perform backup and complete recovery operations on multiple PDBs using a single command, you must connect to the root. Use the `PLUGGABLE DATABASE` clause followed by the list of PDBs on which you want to perform the operation. The following example backs up the PDBs `hrpdb`, `salespdb`, and `invpdb` when connected to the root:

      BACKUP PLUGGABLE DATABASE hrpdb, salespdb, invpdb;

**See Also:**

The following sections in the Oracle Database Backup and Recovery User’s Guide provide detailed information about backing up and recovering PDBs:

- "[Connecting as Target to a PDB](../bradv/starting-interacting-with-rman-client.md)"

- "[Connecting as Target to the Root](../bradv/starting-interacting-with-rman-client.md)"

- "[Backing Up PDBs with RMAN](../bradv/backing-up-database.md)"

- "[Performing Complete Recovery of PDBs with RMAN](../bradv/rman-complete-database-recovery.md)"

- "[Validating PDBs](../bradv/validating-database-files-backups.md)"

- "[Reporting in PDBs](../bradv/reporting-rman-operations.md)"

##### 9.1.1.3 Point-in-Time Recovery in a Multitenant Environment

You can perform point-in-time recovery of the whole multitenant container database (CDB) or a particular pluggable database (PDB).

##### Point-in-Time Recovery of a CDB

To perform point-in-time recovery of a CDB, you must meet the following prerequisites:

- You must be logged in to the root container as a common user with the `SYSDBA` or `SYSBACKUP` privilege.

- The CDB must be mounted.

When performing the recovery operation, use the same commands that you use for non-CDBs.

##### Point-in-Time Recovery of a PDB

When a PDB is closed in an open or closed CDB, you can recover the PDB to a past point in time. The technique depends on the undo mode of the CDB. The following table describes the differences.

Table 9-1 Differences in Point-in-Time Recovery Techniques

| Undo Mode | Auxiliary Instance Used? | Connect as TARGET to ... | RMAN Commands to Use for Recovery                                                                                                                                                                                                                                                                                                                                                            |
|:----------|:-------------------------|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Shared    | Yes                      | CDB root                 | Include the `PLUGGABLE DATABASE` clause to specify the PDB that must be recovered.<br>RMAN uses an auxiliary destination to store temporary files created during recovery. If a fast recovery area has been configured, then it is used as the auxiliary destination. You can explicitly specify an auxiliary destination using the `AUXILIARY DESTINATION` clause in the `RECOVER` command. |
| Local     | No                       | CDB root or PDB          | When connected to the PDB, use the same commands that you use for non-CDBs. When connected to the root, include the `PLUGGABLE DATABASE` clause to specify the PDB that must be recovered.                                                                                                                                                                                                   |

**See Also:**

The following sections in the Oracle Database Backup and Recovery User’s Guide for more information about point-in-time recovery.

- "[Overview of Restore Points in a Multitenant Environment](../bradv/using-flasback-database-restore-points.md)"

- "[Creating CDB Restore Points](../bradv/using-flasback-database-restore-points.md)"

- "[Creating PDB Restore Points](../bradv/using-flasback-database-restore-points.md)"

- "[Performing Point-in-Time Recovery of CDBs and PDBs](../bradv/rman-performing-flashback-dbpitr.md)"

##### 9.1.1.4 Flashback Database in a Multitenant Environment

You can perform a Flashback Database operation for a whole multitenant container database (CDB) or for a particular pluggable (PDB).

RMAN uses an auxiliary destination to store temporary files created during point-in-time recovery. By default, the fast recovery area is used as the auxiliary destination. You can explicitly specify an auxiliary destination using the `AUXILIARY DESTINATION` clause in the `RECOVER` command.

##### Flashback of CDBs

To perform Flashback Database for a CDB, you must meet the following prerequisites:

- You must be connected to the root as a common user with the `SYSDBA` or `SYSBACKUP` privilege.

- The CDB must be mounted.

Specify the target point in time for the flashback operation using a CDB restore point, time expression, or SCN. A CDB restore point is accessible to every PDB within the CDB. However, the restore point does not reflect the PDB sub-incarnation of any of its PDBs.

##### Flashback of PDBs

When a PDB is closed and the CDB is open, you can perform a flashback database operation for this PDB using the `FLASHBACK DATABASE` command. Performing a Flashback Database operation on a particular PDB modifies only data files related to that PDB. The other PDBs in the CDB are not impacted and are available for use. Note that a PDB restore point is accessible only to the PDB in which it is defined and can be used for operations only on this PDB.

Table 9-2 Differences in Flashback Techniques

| CDB Undo Mode | Auxiliary Instance Used? | Connect as TARGET to ... | Commands                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------|:-------------------------|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Shared        | Yes                      | CDB root                 | Use the `FLASHBACK PLUGGABLE DATABASE` command. You can only flash back to a clean PDB restore point.<br>RMAN uses an auxiliary destination to store temporary files created during flashback. If a fast recovery area has been configured, then it is used as the auxiliary destination. You can explicitly specify an auxiliary destination using the `AUXILIARY DESTINATION` clause in the `FLASHBACK PLUGGABLE DATABASE` command. |
| Local         | No                       | CDB root or PDB          | Use the `FLASHBACK PLUGGABLE DATABASE` command. You can specify the target point in time for the flashback operation using a CDB restore point, PDB restore point, time expression, or target SCN.                                                                                                                                                                                                                                    |

**See Also:**

The following sections in the Oracle Database Backup and Recovery User’s Guide for more information about flashback of CDBs and PDBs:

- "[Overview of Restore Points in a Multitenant Environment](../bradv/using-flasback-database-restore-points.md)"

- "[Creating CDB Restore Points](../bradv/using-flasback-database-restore-points.md)"

- "[Creating PDB Restore Points](../bradv/using-flasback-database-restore-points.md)"

- "[Performing a Flashback Database Operation for a Whole CDB](../bradv/rman-performing-flashback-dbpitr.md)"

- "[Performing a Flashback Database Operation for PDBs](../bradv/rman-performing-flashback-dbpitr.md)"

### 9.2 Database Backup and Recovery Concepts

To back up your database means to make copies of your data files, control file, and archived redo log files (if your database runs in `ARCHIVELOG` mode). Restoring a database means copying the physical files that comprise the database from a backup medium, typically disk or tape, to their original or to new locations. Database recovery is the process of updating database files restored from a backup with the changes made to the database after the backup by applying incremental backups and redo logs to the restored files.

This section contains the following topics:

- ARCHIVELOG and NOARCHIVELOG Mode

- RMAN Repository

- Image Copies and Backup Sets

- Full Backups and Incremental Backups

- Consistent and Inconsistent Backups

- Media Recovery

- Fast Recovery Area

**See Also:**

- "Backing Up Your Database"

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-architecture.md) for an overview of Oracle Recovery Manager (RMAN) architecture

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-backup-concepts.md) for more conceptual details about RMAN backups

#### 9.2.1 ARCHIVELOG and NOARCHIVELOG Mode

One of the important decisions you need to make as a DBA is to determine if the database must be run in `ARCHIVELOG` mode or `NOARCHIVELOG` mode. The mode you choose depends on your availability and reliability requirements. It also impacts the type of backup and recovery operations that you can perform.

In `NOARCHIVELOG` mode, the filled redo log groups that become inactive can be reused. This mode protects the database against instance failure, but not against media failure. In `ARCHIVELOG` mode, filled groups of redo logs are archived. This mode protects the database from both instance and media failure, but may require additional hardware resources.

**See Also:**

For a detailed discussion about `ARCHIVELOG` and `NOARCHIVELOG` mode, see [Oracle Database Administrator’s Guide](../admin/managing-archived-redo-log-files.md)

#### 9.2.2 RMAN Repository

Oracle Recovery Manager (RMAN) maintains a record of database files and backups for each database on which it performs operations. This metadata is called the RMAN repository. When you request recovery of a database, RMAN uses the repository metadata to choose the most efficient backups needed for this restore and recovery.

The primary location for the RMAN repository for a database is its control file. The importance of this metadata for RMAN is one more reason why protecting your control file is a vital part of your backup strategy. In some installations, a second copy of the RMAN repository is stored in a schema called the recovery catalog. The recovery catalog is located in a separate database and can store metadata for multiple target databases.

It is recommended that you use a recovery catalog. Because a recovery catalog stores metadata history for longer than the control file, you can perform a recovery that goes further back in time than the history in the control file. Also, if the target control file and all backups are lost, then the RMAN metadata in the recovery catalog can be used.

**See Also:**

For more information about creating and managing a recovery catalog, see [Oracle Database Backup and Recovery User’s Guide](../bradv/managing-recovery-catalog.md)

#### 9.2.3 Image Copies and Backup Sets

Database backups created by Oracle Recovery Manager (RMAN) are stored as image copies or backup sets.

Image copies are exact byte-for-byte copies of files. You can create an image copy by copying a file at the operating system level. Unlike copying files at the operating system level, however, image copies created through RMAN are recorded in the RMAN repository so that RMAN can use these copies during database restore operations and recovery. RMAN can restore files only if they are recorded in the RMAN repository. RMAN can create image copies only on disk.

Backup sets are logical entities produced by the RMAN `BACKUP` command. This command can produce one or more backup sets on disk or tape devices. Although image copies cannot use all RMAN features, their advantages are that you can apply incremental backups to them (synthetic full backups) and you can use them directly in place without first copying them, for very fast restores.

Each backup set contains one or more physical files called backup pieces. A backup piece stores the backup of one or more database files in a compact RMAN-specific format. One advantage of backup sets is that RMAN uses unused block compression to save space in backing up data files. Only those blocks in the data files that have been used to store data are included in the backup set. Backup sets can also be compressed, encrypted, sent to tape, and use advanced unused-space compression that is not available with datafile copies.

#### 9.2.4 Full Backups and Incremental Backups

A full backup of a data file includes all used blocks of the data file. A full backup can be either an image copy or backup set.

An incremental backup copies only those blocks in a data file that change between backups. A level 0 incremental backup, which copies all blocks in the data file, is used as a starting point for an incremental backup strategy.

A level 1 incremental backup copies only images of blocks that have changed since the previous level 0 or level 1 incremental backup. Level 1 backups can be cumulative, in which case all blocks changed since the most recent level 0 backup are included, or differential, in which case only blocks changed since the most recent level 0 or level 1 incremental backup are included.

Incremental backups at level 0 can be either backup sets or image copies, but incremental backups at level 1 can only be backup sets.

A typical incremental strategy makes level 1 backups at regular intervals such as once each day.

During recovery, Oracle Recovery Manager (RMAN) will automatically apply both incremental backups and redo logs as required, to recover the database to the exact point in time desired.

#### 9.2.5 Consistent and Inconsistent Backups

A backup is either consistent or inconsistent. To make a consistent backup, your database must have been shut down cleanly and remain closed for the duration of the backup. All committed changes are written to the data files during the shut down process, so the data files are in a transaction-consistent state. When you restore your data files from a consistent backup, you can open the database immediately.

If the database is in `ARCHIVELOG` mode, then you can make inconsistent backups that are recoverable using archived redo log files. Open database backups are inconsistent because the online redo log files contain changes not yet applied to the data files. The online redo log files must be archived and then backed up with the data files to ensure recoverability.

Despite the name, an inconsistent backup is as robust a form of backup as a consistent backup. The advantage of making inconsistent backups is that you can back up your database while the database is open for updates.

#### 9.2.6 Media Recovery

If you restore the archived redo log files and data files, then you must perform media recovery before you can open the database. Any database transactions in the archived redo log files not reflected in the data files are applied to the data files, bringing them to a transaction-consistent state before the database is opened.

Media recovery requires a control file, data files (typically restored from backup), and online and archived redo log files containing changes since the time the data files were backed up. Media recovery is most often used to recover from media failure, such as the loss of a file or disk, or a user error, such as the deletion of the contents of a table.

Media recovery can be a complete recovery or a point-in-time recovery. Complete recovery can apply to individual datafiles, tablespaces, or the entire database. Point-in-time recovery applies to the whole database (and also sometimes to individual tablespaces, with automation help from Oracle Recover Manager (RMAN)).

In a complete recovery, you restore backup data files and apply all changes from the archived and online redo log files to the data files. The database is returned to its state at the time of failure and can be opened with no loss of data.

In a point-in-time recovery, you return a database to its contents at a user-selected time in the past. You restore a backup of data files created before the target time and a complete set of archived redo log files from backup creation through the target time. Recovery applies changes between the backup time and the target time to the data files. All changes after the target time are discarded.

RMAN enables you to perform both a complete and a point-in-time recovery of your database. However, this documentation focuses on complete recovery.

**See Also:**

- "Performing User-Directed Recovery"

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-performing-flashback-dbpitr.md) for more detailed information about point-in-time recovery

#### 9.2.7 Fast Recovery Area

To simplify the management of backup and recovery files, you can create a fast recovery area for your database. The fast recovery area is an Oracle-managed directory, file system, or Oracle Automatic Storage Management disk group that provides a centralized storage location for backup and recovery files. Oracle creates archived logs and flashback logs in the fast recovery area. Oracle Recovery Manager (RMAN) can store its backup sets and image copies in the fast recovery area, and it uses it when restoring files during media recovery. The fast recovery area also acts as a disk cache for tape.

Oracle Database automatically manages this storage, deleting files that are no longer needed. Periodically copying backups to tape frees space in the fast recovery area for other files.

When you issue the RMAN `BACKUP` command without specifying a backup destination, RMAN automatically backs up to the fast recovery area if it is configured.

Oracle recommends that you configure a fast recovery area to simplify backup management. Except as noted, this documentation assumes the use of a recovery area.

**See Also:**

- "Planning Space Usage and Location for the Fast Recovery Area"

- "Configuring the Fast Recovery Area"

### 9.3 Configuring Your Database for Basic Backup and Recovery

This section explains how to set up your database to take advantage of Oracle suggested backup strategies.

To take maximum advantage of Oracle Database features that automatically manage backup and recovery files and operations, configure your database as follows:

- Use a fast recovery area, which automates storage management for most backup-related files, and specify it as an archived redo log file destination.

- Run the database in `ARCHIVELOG` mode so you can perform online backups and have data recovery options such as complete and point-in-time media recovery.

You must also set several policies governing which files are backed up, what format is used to store backups on disk, and when files become eligible for deletion.

In a multitenant environment, you must connect to the root and configure backup and recovery settings for the whole multitenant container database (CDB). These settings are applicable to the root and to all pluggable databases (PDBs) in the CDB.

This section contains the following topics:

- Planning Space Usage and Location for the Fast Recovery Area

- Configuring Users to Perform Backup and Recovery

- Connecting to the Target Database Using RMAN

- Configuring Recovery Settings

- Configuring Backup Settings

#### 9.3.1 Planning Space Usage and Location for the Fast Recovery Area

Oracle recommends placing the fast recovery area on a separate storage device from the working set of database files. Otherwise, the storage device becomes a single point of failure for your database.

The amount of storage space to allocate for the fast recovery area depends on the size and activity levels of your database and on your recovery objectives. Your objectives dictate what kinds of backups you use, when you make them, and how long to keep them.

This section contains the following topics:

- About the Backup Retention Policy and the Fast Recovery Area

- About the Fast Recovery Area Size

##### 9.3.1.1 About the Backup Retention Policy and the Fast Recovery Area

Space management in the fast recovery area is governed by a backup retention policy. A retention policy determines when files are obsolete, meaning that they are no longer needed to meet your data recovery objectives.

Retention policies can be based on redundancy of backups or on a recovery window (period of time).

When using a policy based on redundancy, you specify how many full or level 0 backups of each data file and control file that Oracle Recovery Manager (RMAN) keeps. If the number of full or level 0 backups for a specific data file or control file exceeds the redundancy setting, then RMAN considers the extra backups as obsolete.

When using a recovery policy based on a period of time (or window), you specify a time interval in days. Files are obsolete only when they are no longer needed for complete recovery or point-in-time recovery to a system change number (SCN) within the window. Therefore, a recovery retention policy based on a window is recommended.

The default retention policy is a redundancy of 1. Even after files in the fast recovery area are obsolete, they are typically not deleted until space is needed for new files. If space permits, files recently moved to tape remain on disk to avoid restoring them from tape for a recovery. The automatic deletion of obsolete files and files moved to tape from the fast recovery area makes it a convenient archiving destination. Other destinations require manual deletion of logs.

**See Also:**

- "Configuring Backup Policy Settings"

- [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-basic.md) for examples of configuring a redundancy-based policy.

##### 9.3.1.2 About the Fast Recovery Area Size

As a general rule, the larger the fast recovery area, the more useful it is. [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-basic.md) explains how to size the fast recovery area. Ideally, the fast recovery area should be large enough for copies of the data files, control files, online redo log files, and archived redo log files needed to recover the database, and also the copies of these backup files that are kept based on the retention policy.

If your backup strategy includes incremental backups, then add enough space to the fast recovery area for these files. If you can move some backups to tape, then you can reduce the size of the fast recovery area. Note that retrieving files from tape causes longer database restore operations and recovery times.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/maintaining-rman-backups.md) for information about handling a full fast recovery area

#### 9.3.2 Configuring Users to Perform Backup and Recovery

This section describes the credentials required to perform backup and recovery and how to grant the `SYSBACKUP` privilege to database users.

- Credentials Required to Perform Backup and Recovery

- Granting the SYSBACKUP Privilege

##### 9.3.2.1 Credentials Required to Perform Backup and Recovery

To perform backup and recovery tasks with Oracle Recovery Manager (RMAN), you must connect to the target database as a user with the `SYSDBA` or `SYSBACKUP` administrative privilege. The `SYSBACKUP` privilege encompasses all the privileges required to back up and recover the database. Those privileges are a subset of the privileges included in the `SYSDBA` administrative privilege.

The following types of users have the `SYSBACKUP` privilege.

- The `SYSBACKUP` user.

  When you install the database, the `SYSBACKUP` user, with the `SYSBACKUP` privilege, is created automatically.

- Database users to whom you grant the `SYSBACKUP` privilege.

- Database host users who are members of the OSBACKUPDBA operating system group—for operating system authentication.

  The OSBACKUPDBA group is assigned to a specific operating system group during database installation. For example, on UNIX and Linux systems, the `backupdba` group is typically designated as the OSBACKUPDBA group. Host users in this group can connect to the target database using operating system authentication; they do not need to be defined as a database user.

For the Oracle suggested backup strategy described in this documentation, you use operation system authentication. Consult your operating system documentation for instructions for creating host users and adding them to the OSBACKUPDBA group.

**Note:**

In previous releases, you needed the `SYSDBA` administrative privilege to perform backup and recovery tasks. Starting with Oracle Database 12c, it is recommended that you use the `SYSBACKUP` administrative privilege for backup and recovery operations.

Oracle recommends that you do not use the `SYSBACKUP` user. Instead, create a user and grant the `SYSBACKUP` privilege to that user.

**See Also:**

- "[Starting SQL\*Plus and Connecting to the Database](getting-started-with-database-administration.md)" for more information about operating system authentication

- "Granting the SYSBACKUP Privilege"

##### 9.3.2.2 Granting the SYSBACKUP Privilege

As a database administrator, you can grant the `SYSBACKUP` privilege to any database user. When you do so, an entry is made for that user in the password file.

##### To grant the SYSBACKUP privilege to an existing user:

1.  Log into Oracle Enterprise Manager Database Express (EM Express) as user `SYS`. Be sure to select the `as` `sysdba` check box on the Login page.
    See "[Accessing the Database Home Page](getting-started-with-database-administration.md)."
2.  From the Security menu, select Users.
3.  On the Users page, click the name of the user to whom you want to grant the privilege.
4.  On the Account Summary page, in the Privileges tab, click Edit.
5.  In the Alter Privileges dialog box, scroll to the `SYSBACKUP` privilege in the left-hand list, select it, and then click the Right-Arrow (\>) button.
    The `SYSBACKUP` privilege appears in the right-hand list.
6.  Click OK.

**See Also:**

- "[Example: Granting Privileges and Roles to a User Account](administering-user-accounts-and-security.md)"

- "[Password File](managing-database-storage-structures.md)"

#### 9.3.3 Connecting to the Target Database Using RMAN

To perform backup or recovery operations or to configure backup and recovery settings, you must start the Oracle Recovery Manager (RMAN) client and connect to the target database. A target database is the Oracle database that must be backed up or restored using RMAN. Connections to the target database require the `SYSDBA` or `SYSBACKUP` administrative privilege.

##### To connect to the target database:

1.  Open a command window.
2.  Ensure that the `ORACLE_SID` environment variable is set to the system identifier (SID) of the database.
        $ ORACLE_SID=prod; export ORACLE_SID
3.  Do one of the following:
    - To connect as a database user who was granted the `SYSBACKUP` privilege, enter the following command:

          rman target '"username as sysbackup"'

      The single and double quotes are required. Enter the user's password when prompted.

    - To connect with operating system authentication, ensure that you are logged in to the database host as a user who is in the OSBACKUPDBA group (typically the `backupdba` group on UNIX and Linux systems), and enter the following command:

          rman target /

      When you do not explicitly specify `SYSDBA` or `SYSBACKUP`, you are connected to the target database with the `SYSDBA` privilege.

**Note:**

You can start RMAN on one database host and connect to a target database on another host. This is known as connecting to a remote database, and it requires that:

- You supply a net service name in the connect string.

- Your user name be entered in the password file of the remote database to connect as `SYSBACKUP`.

Connecting to a remote database is outside the scope of this documentation. For more information, see [Oracle Database Backup and Recovery User’s Guide](../bradv/starting-interacting-with-rman-client.md)

**See Also:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/starting-interacting-with-rman-client.md) for information about connecting to multitenant container databases (CDBs) and pluggable databases (PDBs)

- [Oracle Database Backup and Recovery User’s Guide](../bradv/starting-interacting-with-rman-client.md) for more information about connecting to the target database

- "Configuring Users to Perform Backup and Recovery"

- "[Client Connections](configuring-the-network-environment.md)" for information about net service names.

#### 9.3.4 Configuring Recovery Settings

This section explains how to configure settings used for instance recovery, media recovery, and fast recovery. It includes the following topics:

- Configuring the Fast Recovery Area

- Enabling Archiving of Redo Log Files

- Enabling Flashback Database

##### 9.3.4.1 Configuring the Fast Recovery Area

If you did not specify a location for the fast recovery area during installation, the installation process automatically configures a fast recovery area in the Oracle base directory. Oracle recommends, however, that the fast recovery area be located on a separate storage device from the database files.

You can modify the following initialization parameters to relocate the fast recovery area and to adjust its size:

- `DB_RECOVERY_FILE_DEST`

  Specifies the location of the fast recovery area. This can be a file system directory or an Oracle Automatic Storage Management (Oracle ASM) disk group, but not a raw disk.

- `DB_RECOVERY_FILE_DEST_SIZE`

  Specifies the size of the fast recovery area, in bytes.

The `DB_RECOVERY_FILE_DEST_SIZE` parameter must be set before the `DB_RECOVERY_FILE_DEST` parameter.

You can set these parameters without having to shut down and restart the database. In an Oracle Real Application Clusters (Oracle RAC) database, all instances must have the same values for these initialization parameters. The location must be on a cluster file system, Oracle ASM, or a shared directory.

##### To configure the fast recovery area:

Assume that you want to want to place the fast recovery area in the directory `/u02/oracle/fra` and you want its size to have an upper limit of 10 GB.

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Specify the size of the fast recovery area using the following command:
        ALTER SYSTEM SET DB_RECOVERY_FILE_DEST_SIZE = 10G;
3.  Specify the location of the fast recovery area using the following command:
        ALTER SYSTEM SET DB_RECOVERY_FILE_DEST = '/u02/oracle/fra';

**See Also:**

- "Fast Recovery Area"

- "About the Fast Recovery Area Size"

##### 9.3.4.2 Enabling Archiving of Redo Log Files

To back up the database while it is open, or to be able to perform complete or point-in-time media recovery, you must enable the archiving of redo log files. To do so, you place the database in `ARCHIVELOG` mode. You can determine if archiving of redo logs is enabled for the target database using the following query:

    SELECT LOG_MODE FROM V$DATABASE;

If you do not specify a destination to which the database should write archived log files, the database writes them to the fast recovery area. You can specify a different destination, or you can specify that multiple copies of each archived log file be written, each to a different destination. Redundant copies help ensure that archived log files are always available in the event of a failure at one of the destinations.

The following procedure assumes that you want to place archived log files in the directory `/u02/oracle/logfiles`, and redundant copies of archived log file in the directory `/u03/oracle/logfiles`. The redundant copies are optional.

**WARNING:**

You must ensure that there is sufficient disk space at all times for archived log file destinations. If the database encounters a disk full error as it attempts to archive a log file, a fatal error occurs and the database stops responding. You can check the alert log for a disk full message.

##### To enable archiving of redo log files:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Shut down the database.
        SHUTDOWN IMMEDIATE;
3.  Back up the database.
    It is recommended that you always back up a database before making any major change to the database.

    See "Performing a Whole Database Backup."
4.  Start the instance and mount the database (do not open the database). To enable archiving, the database must be mounted but not open.
        STARTUP MOUNT;
5.  Enter the following command to set the first archived log file destination:
        ALTER SYSTEM SET LOG_ARCHIVE_DEST_1 = 'LOCATION=/u02/oracle/logfiles';

    **Note:**

    The directory must exist.
6.  (Optional) Enter the following command to set the second archived log file destination:
        ALTER SYSTEM SET LOG_ARCHIVE_DEST_2 = 'LOCATION=/u03/oracle/logfiles';
7.  Change the database archiving mode and then open the database for normal operations.
        ALTER DATABASE ARCHIVELOG;
        ALTER DATABASE OPEN;
8.  Shutdown the database.
        SHUTDOWN IMMEDIATE;
9.  Back up the database.
    Because changing the archiving mode updates the control file, it is recommended that you create a new backup.

    See "Performing a Whole Database Backup."
10. Start up the database normally.
        STARTUP;

**Note:**

You cannot use backups from before the switch to `ARCHIVELOG` mode to restore and recover the database to a point in time after the switch. Thus, if you do not immediately make a backup after switching, then you are running your database without a valid backup. See "Performing and Scheduling Backups Using RMAN" to learn how to make database backups.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-archived-redo-log-files.md) for more information about setting initialization parameters for archived log file destinations

- "Media Recovery"

- "[Monitoring General Database State and Workload](monitoring-and-tuning-the-database.md)" for information about the alert log

##### 9.3.4.3 Enabling Flashback Database

To revert the entire database to a prior point in time, you can either revert the entire database to a prior point in time by restoring a backup and doing point-in-time recovery, or you can enable Flashback Database. When you enable Flashback Database, the database generates flashback logs in the fast recovery area. These logs are used to flash back the database to a specified time. During usual operation, the database occasionally logs images of data blocks to the flashback logs. The database automatically creates, deletes, and resizes flashback logs.

Use the following command to check if Flashback Database is enabled for your target database:

    SELECT FLASHBACK_ON FROM V$DATABASE;

##### To enable Flashback Database:

1.  Ensure that you configure a fast recovery area and that the database is running in `ARCHIVELOG` mode.
2.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
3.  Optionally, specify the length of the desired flashback window (in minutes) by setting the `DB_FLASHBACK_RETENTION_TARGET` initialization parameter.
    The default value for this parameter is 1440 minutes, which is one day. The following command specifies that the flashback window must be 3 days.

        ALTER SYSTEM SET DB_FLASHBACK_RETENTION_TARGET=4320;
4.  Enable the Flashback Database feature for the whole database using the following command:
        ALTER DATABASE FLASHBACK ON;

You can also execute the commands in this section by connecting to the target database using SQL\*Plus instead of RMAN.

**See Also:**

- "Configuring the Fast Recovery Area"

- "Enabling Archiving of Redo Log Files"

- "Rewinding a Database Using Oracle Flashback Database"

- [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-basic.md) for more details about configuring a fast recovery area

#### 9.3.5 Configuring Backup Settings

You can configure several backup-related settings and policies. For example, you can determine how backups are stored, which data is backed up, and how long backups are retained. You can also configure settings to optimize backup performance.

This section contains the following topics:

- Configuring Backup Device Settings

- Configuring Backup Policy Settings

- Configuring Automatic Backups for the Control File and Server Parameter File

- Enabling Block Change Tracking

##### 9.3.5.1 Configuring Backup Device Settings

For disk-based backups, you can configure the default format for backups, the location on disk where backups are stored, whether backup tasks run in parallel, and whether backups are compressed.

For tape backups, you can configure settings such as the number of tape drives and whether backups are compressed. On most platforms, you must integrate a media manager with the Oracle database to use sequential media for storage.

You can use Oracle Secure Backup, which supports both database and file system backups to tape, as your media manager. Oracle Secure Backup provides the same services for Oracle Recovery Manager (RMAN) as other third-party SBT interfaces. This section assumes that you make only disk backups.

Use the RMAN `CONFIGURE` command to configure backup device settings such as the default backup type, disk location to which database files are backed up, and parallelism. Use the RMAN `SHOW ALL` command to view the currently configured settings.

##### To configure backup device settings:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Specify that the default device used to store backups is disk. The following command directs RMAN to store backups to disk.
        CONFIGURE DEFAULT DEVICE TYPE TO DISK;
3.  Specify that the backups must be stored on disk in the form of backup sets. Also set the parallelism to 1.
        CONFIGURE DEVICE TYPE DISK BACKUP TYPE TO BACKUPSET PARALLELISM 1;

    Backups on disk can be stored in the form of backup sets or image copies. Image copies are exact copies of database files. They are not stored in an RMAN-specific format and can be used as-is to perform recovery. Backup sets use an RMAN-specific format. With backup sets, RMAN uses unused block compression to save space by backing up only the blocks that contain data. RMAN can also encrypt backups and create incremental backups.

**See Also:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-backup-concepts.md) for more information about image copies and backup sets

- [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-basic.md) for information about setting tape as the default device

##### 9.3.5.2 Configuring Backup Policy Settings

You can set the backup policies that govern control file and server parameter file backups, tablespaces to exclude from an entire database backup, and the backup retention policy.

##### To configure the backup policy settings:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Configure RMAN to automatically backup the control files and the server parameter as described in "Configuring Automatic Backups for the Control File and Server Parameter File".
3.  Configure backup optimization to save space in the fast recovery area. Optimization excludes unchanged files, such as read-only files and offline data files, that were previously backed up.
        CONFIGURE BACKUP OPTIMIZATION ON;
4.  Configure the retention policy to specify how long the backups and archived redo logs must be retained for media recovery.
    The following command specifies that the backups and archived logs must be retained for 31 days.

        CONFIGURE RETENTION POLICY TO RECOVERY WINDOW OF 31 DAYS;
5.  Specify that archived logs can be automatically deleted only when they have been backed up to tape or are obsolete based on the retention policy by using the following command.
        CONFIGURE ARCHIVELOG DELETION POLICY TO NONE;
6.  Enable block change tracking as described in "Enabling Block Change Tracking".
7.  Optionally, specify the tablespaces that must be excluded from backups.
    Excluding certain tablespaces from backups, such as read-only tablespaces or tablespaces that contain temporary or test data, enables you to save space.

    The following command excludes the tablespace `example` from backups.

        CONFIGURE EXCLUDE FOR TABLESPACE example;

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-basic.md) for information about other methods of configuring the retention policy

##### 9.3.5.3 Configuring Automatic Backups for the Control File and Server Parameter File

You can configure Oracle Recovery Manager (RMAN) to automatically backup the control file and server parameter file with every backup. This is referred to as an autobackup. The server parameter file and control file are critical to the database and RMAN. Creating automatic backups of the control file enables RMAN to recover the database even if the current control file and server parameter file are lost. The control file and server parameter file are relatively small compared to typical data files and, therefore, backing them up frequently results in relatively little storage overhead.

If the database runs in `ARCHIVELOG` mode, then an autobackup is also taken whenever the database structure metadata in the control file changes.

**Note:**

For multitenant container databases (CDBs), the control file and server parameter file autobackups are performed by default.

##### To configure automatic backups for the control file and server parameter file:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Enter the following command:
        CONFIGURE CONTROLFILE AUTOBACKUP ON;

RMAN uses a default format to assign names for these backups.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/getting-started-rman.md) for more information about configuring the format for backups

##### 9.3.5.4 Enabling Block Change Tracking

Block changing tracking improves the performance of incremental backups by recording changed blocks in the block change tracking file. During an incremental backup, instead of scanning all data blocks to identify which blocks have changed, RMAN uses this file to identify the changed blocks that need to be backed up.

You can enable block change tracking when the database is either open or mounted. This section assumes that you intend to create the block change tracking file as an Oracle Managed File in the database area, which is where the database maintains active database files such as data files, control files, and online redo log files.

To determine if block change tracking is enabled, check the `STATUS` and `FILENAME` columns in the `V$BLOCK_CHANGE_TRACKING` view, using the following statement from the SQL or RMAN prompt:

    SELECT status, filename FROM V$BLOCK_CHANGE_TRACKING;

##### To enable block change tracking:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Determine the current location of the database data files by submitting the following query:
        RMAN> SELECT NAME FROM V$DATAFILE;

        NAME
        -----------------------------------------------
        /u01/app/oracle/oradata/orcl/system01.dbf
        /u01/app/oracle/oradata/orcl/example01.dbf
        /u01/app/oracle/oradata/orcl/sysaux01.dbf
        /u01/app/oracle/oradata/orcl/undotbs01.dbf
        /u01/app/oracle/oradata/orcl/users01.dbf

    In this example, the query results show that data files are stored in the file system in the directory /u01/app/oracle/oradata/orcl. Data files might also be stored in an Oracle Automatic Storage Management disk group.
3.  Set the `DB_CREATE_FILE_DEST` initialization parameter to specify the location where new database files, including the block change tracking file, must be stored. You can specify the same directory shown in query results from the previous step, with the final portion of the path—the database SID—stripped, as shown in the following example, or designate a new directory. Any directory that you specify must have the write permission for the Oracle software owner.
    The following command specifies that new database files must be stored in the directory /u01/app/oracle/oradata/:

        ALTER SYSTEM SET DB_CREATE_FILE_DEST = '/u01/app/oracle/oradata';
4.  Enable block change tracking for the database using the following command:
        ALTER DATABASE ENABLE BLOCK CHANGE TRACKING;

**See Also:**

- [Oracle Database Reference](../refrn/V-BLOCK_CHANGE_TRACKING.md) for more information about the `V$BLOCK_CHANGE_TRACKING` view.

- [Oracle Database Reference](../refrn/DB_CREATE_FILE_DEST.md) for more information about the `DB_CREATE_FILE_DEST` initialization parameter

### 9.4 Backing Up Your Database

This section describes how to back up your database with Oracle Recovery Manager (RMAN). The Oracle suggested strategy for disk-only backups provides efficient daily backup of the database. This strategy enables you to quickly return your database to its state at any point during the previous 24 hours. For more flexible backup options, see [Oracle Database Backup and Recovery User's Guide](../bradv/introduction-backup-recovery.md).

This section contains the following topics:

- Additional Backup Concepts

- Performing and Scheduling Backups Using RMAN

- Displaying Backups Stored in the RMAN Repository

- Validating Backups and Testing Your Backup Strategy

**See Also:**

"Database Backup and Recovery Concepts"

#### 9.4.1 Additional Backup Concepts

This section includes topics about incrementally updated backups and backup tags.

- Incrementally Updated Backups: Rolling Forward Image Copies of Data Files

- Backup Tags

##### 9.4.1.1 Incrementally Updated Backups: Rolling Forward Image Copies of Data Files

Oracle Recovery Manager (RMAN) enables you to apply level 1 incremental backups to an older image copy of your data files. You can roll forward the copy to the point in time of the most recent level 1 incremental backup. All blocks changed since the image copy was created are overwritten with their new contents as of the time of the last level 1 incremental backup. The effect is to roll forward the file in time, so that its contents are equivalent, for the purposes of database recovery, to an image copy of the data file made at the time of the last incremental level 1 backup.

Incorporating incrementally updated backups into your backup strategy shortens expected recovery times. Media recovery to the present time or to a point in time in the recent past can begin at the time of the last level 1 backup applied, rather than at the time of the last full database backup.

**See Also:**

"Using the Oracle Suggested Backup Strategy"

##### 9.4.1.2 Backup Tags

A tag is a text string that identifies a backup, either uniquely or as part of a group of backups. All Oracle Recovery Manager (RMAN) backups, including incremental backups, are labeled with a tag. For example, if you performed a full database backup every Saturday, then you could use the tag `FULL_SAT` to identify this backup.

You can use tags to refer to specific backups in RMAN commands. For example, you could issue a command to move the latest `FULL_SAT` backup to tape. If you do not specify a tag, then RMAN creates a unique tag automatically.

Because you can use tags to refer to different groups of backups, you can create different routines in your backup strategy that do not interfere with each other. When you schedule a backup job and give the job a name, the job name is the tag.

#### 9.4.2 Performing and Scheduling Backups Using RMAN

Oracle Recovery Manager (RMAN) enables you to perform the different types of backups that are required by your backup strategy. This section discusses creating a whole database backup.

You can also individually back up data files, control files, and archived redo log files. You can use some advanced RMAN features such as encrypting backups. For more information about these topics, see [Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md).

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md) for information about backing up multitenant conainer databases (CDBs) and pluggable databases (PDBs)

This section contains the following topics:

- Performing a Whole Database Backup

- Using the Oracle Suggested Backup Strategy

- About the Oracle Suggested Backup Strategy and Retention

- Scheduling Miscellaneous Backup Tasks

##### 9.4.2.1 Performing a Whole Database Backup

Whole backups of a database include the complete contents of all data files of the database, plus the control file, archived redo log files, and server parameter file. With these files, you can perform a complete recovery.

While whole database backups can be an important element in your overall backup strategy, they are also a required step in some situations, such as when you enable or disable `ARCHIVELOG` mode (see "Configuring Recovery Settings"). This section explains how to make whole database backups, both offline and online, to disk. Typically, you want to perform online backups to maximize database availability.

##### To perform a whole database backup when the database is open:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."

2.  Ensure that your database is in `ARCHIVELOG` mode as described in "Enabling Archiving of Redo Log Files."

    You can make online backups only if your database is running in `ARCHIVELOG` mode.

3.  Back up the database, along with archived redo logs by using the following command:

        BACKUP DATABASE PLUS ARCHIVELOG;

This backup is created on the default device that you configured for storing backups. If you did not configure a default device, then the backup is created in the fast recovery area. RMAN uses a default format while naming the backup sets that comprise the backup.

##### To perform a whole database backup when the database is closed:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Shut down the database and then mount the database using the following commands.
        SHUTDOWN IMMEDIATE;
        STARTUP MOUNT;
3.  Back up the database using the following command:
        BACKUP DATABASE;

    While backing up a database that is closed, you need not back up the archived log files because the database is in a consistent state at the time of backup. Therefore, no media recovery is required if you restore the database from this backup.
4.  Open the database after the backup is complete.
        ALTER DATABASE OPEN;

**See Also:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md) for information about performing backups of multitenant container databases (CDBs) and pluggable databases (PDBs)

- "Displaying Backup Reports"

- "Fast Recovery Area"

##### 9.4.2.2 Using the Oracle Suggested Backup Strategy

The Oracle suggested backup strategy is a scheduled disk backup strategy that protects your data and provides efficient recoverability to any point in the user-specified recovery window (time period). It leverages the incrementally updated backup features to provide faster backups than whole database backups, and faster recoverability than is possible by applying multiple incremental backups to the last full backup.

After reading the introductory "About the Oracle Suggested Backup Strategy" topic, complete the following tasks described in this section to schedule a daily backup that implements the Oracle suggested backup strategy:

- Task 1 - Preparing to Use the Oracle Suggested Backup Strategy

- Task 2 - Creating the Backup Script—UNIX and Linux

- Task 3 - Testing the Backup Script

- Task 4 - Scheduling the Daily Backup—UNIX and Linux

**See Also:**

"Incrementally Updated Backups: Rolling Forward Image Copies of Data Files"

###### 9.4.2.2.1 About the Oracle Suggested Backup Strategy

The Oracle suggested backup strategy is based on incrementally updated backups. This strategy starts with an image copy of each data file and then rolls forward the image copies each day by applying an incremental level 1 backup.

For each data file, the strategy calls for backups as follows:

- At the beginning of day 1 of the strategy (the time the first scheduled job actually runs), Oracle Recovery Manager (RMAN) creates an incremental level 0 image copy. It contains the data file contents at the beginning of day 1.

  If a recovery is required, then the archived redo log files from day 1 can be used to recover to any point during day 1.

- At the beginning of day 2, RMAN creates a differential incremental level 1 backup that contains the blocks changed during day 1.

  If a recovery is required, then RMAN can apply this incremental level 1 to roll forward the level 0 backup to the beginning of day 2. RMAN can use archived redo log files to recover to any point during day 2.

- At the beginning of each day n for day 3 and onward, RMAN applies the level 1 backup from the beginning of day n-1 to the level 0 backup. This action brings the data file copy to its state at the beginning of day n-1. Then, RMAN creates a new level 1 backup that contains the blocks changed during day n-1.

  If a recovery is required, then RMAN can apply this incremental level 1 backup to the data file rolled forward on day n-1 to the beginning of day n. RMAN can use archived redo log files to recover the database to any point during day n.

In this Oracle suggested backup strategy, the data file image copies and the level 1 incremental backups share the same tag. You can safely implement other backup strategies without interfering with the Oracle suggested backup strategy.

Oracle suggested backup strategies also use tape backups in addition to disk backups, but these are beyond the scope of this section.

###### 9.4.2.2.2 Task 1 - Preparing to Use the Oracle Suggested Backup Strategy

To use the Oracle suggested backup strategy, ensure that:

- The database is in `ARCHIVELOG` mode.

- The fast recovery area size is configured, or a default device for storing backups is configured.

- You have added a database host user to the OSBACKUPDBA operating system group, for operating system authentication.

  **See Also:**

  "Configuring Your Database for Basic Backup and Recovery"

###### 9.4.2.2.3 Task 2 - Creating the Backup Script—UNIX and Linux

This backup script implements the Oracle suggested backup strategy, enabling quick recovery to any time in the preceding 24 hours. This script can be used to back up a non-CDB or a whole multitenant container database (CDB).

To create the backup script for UNIX and Linux:

- Start a text editor and create and save a file with the following contents. Save the file in a directory that is accessible to the Oracle Database software and on which the Oracle software owner has the read permission.

  **Note:**

  In the following script, substitute the correct values for your installation for the `ORACLE_HOME` and `ORACLE_SID` environment variables.

      #!/bin/sh
      export ORACLE_HOME=/u01/app/oracle/product/11.2.0/dbhome_1
      export ORACLE_SID=orcl
      PATH=$ORACLE_HOME/bin:$PATH
      rman <<EOF
      connect target /
      RUN {
       ALLOCATE CHANNEL disk_iub DEVICE TYPE DISK;
       RECOVER COPY OF DATABASE WITH TAG daily_iub;
       BACKUP INCREMENTAL LEVEL 1 FOR RECOVER OF COPY WITH TAG daily_iub DATABASE;
      }
      exit
      EOF

###### 9.4.2.2.4 Task 3 - Testing the Backup Script

It is recommended that you run the script manually, to check for errors, before scheduling it. Your manual run of the script will start day one of the strategy, creating an incremental level 0 image copy of all datafiles.

To test the backup script:

1.  Log in to the database host as a user who is a member of the OSBACKUPDBA operating system group (typically the `backupdba` group).
2.  In a command window, enter the following command:
        full-script-path

    where `full-script-path` is the full path and file name of the script you created in Task 2.

    For example, if your script is in the file /u01/app/oracle/rman/daily_backup.sh, then enter this command:

        /u01/app/oracle/rman/daily_backup.sh

The script starts Oracle Recovery Manager (RMAN), which starts the backup. The output from RMAN includes warning messages similar to the following:

    ...
    no copy of datafile 1 found to recover
    no copy of datafile 2 found to recover
    ...
    no parent backup or copy of datafile 1 found
    no parent backup or copy of datafile 2 found
    ...

These messages are normal for the first run of the script.

**Note:**

For the second run of the script, the output includes only these warning messages:

    no copy of datafile 1 found to recover
    no copy of datafile 2 found to recover
    ...

Again, these messages are normal. For the third and subsequent script runs, no further warning messages are output.

###### 9.4.2.2.5 Task 4 - Scheduling the Daily Backup—UNIX and Linux

The following procedure uses the `cron` utility to schedule daily database backups at 2:00 a.m.

To schedule the Oracle-suggested disk backup strategy:

1.  Ensure that you are logged in to the database host as a user who is a member of the OSBACKUPDBA operating system group (typically the `backupdba` group).
    The `cron` job will run as this host user.
2.  Start a text editor, and create and save a file with the following contents into your home directory. Name the file .crontab. (Note the period at the front of the file name.)
        MAILTO=first.last@example.com
        # MI HH DD MM DAY CMD
          00  2  *  *  *  full-script-path

    where `full-script-path` is the full path and file name of the script you created in Task 2.

    For example, if the script is in the file /u01/app/oracle/rman/daily_backup.sh, then the .crontab file must contain:

        MAILTO=first.last@example.com
        # MI HH DD MM DAY CMD
          00  2  *  *  *  /u01/app/oracle/rman/daily_backup.sh

    **Note:**

    Supply the desired e-mail address in the `MAILTO` line. This line is optional. Content written to stdout by the `cron` job is e-mailed to this address at the completion of the job.
3.  In a command window, change directory to your home directory and enter the following command:
        crontab .crontab

    This creates a crontab file for this user from the contents of .crontab.

    **Caution:**

    The existing crontab file for this user is overwritten. If you want to preserve the contents of this file and add this new job, use this command, which enables you to edit the existing file:

        crontab -e
4.  (Optional) Check the contents of the crontab file for this user with the following command:
        crontab -l

        MAILTO=first.last@example.com
        # MI HH DD MM DAY CMD
          00  2  *  *  *  /u01/app/oracle/rman/daily_backup.sh

**See Also:**

Your operating system documentation for a description of the crontab command and crontab files

##### 9.4.2.3 About the Oracle Suggested Backup Strategy and Retention

When using the Oracle suggested backup strategy, the retention is dictated by the recovery and not by the configured retention. In order to get retention beyond 24 hours, you must change the RECOVER statement to something like:

    RECOVER COPY OF DATABASE WITH TAG 'ORA_OEM_LEVEL_0' UNTIL TIME "SYSDATE-4";

The configured retention is not honored for either the retention or obsolete settings. So when using the Oracle suggested backup strategy, Oracle recommends that the default setting remains unchanged to avoid confusion:

    CONFIGURE RETENTION POLICY TO REDUNDANCY 1; # default

##### 9.4.2.4 Scheduling Miscellaneous Backup Tasks

In addition to implementing the Oracle suggested backup strategy described in "Using the Oracle Suggested Backup Strategy," you can use customized backup strategies that back up certain parts of your database. Customized strategies include backing up selected tablespaces, datafiles, and archived redo logs. Create a script that contains the commands required to implement your customized backup task and then schedule this backup task using the `cron` utility.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md) for information about performing customized backups

#### 9.4.3 Displaying Backups Stored in the RMAN Repository

Use the `LIST` command to view information about backups stored in the Oracle Recovery Manager (RMAN) repository. The information includes backups of data files, individual tablespaces, archived redo log files, and control files. You can also use this command to display information about expired and obsolete backups.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/reporting-rman-operations.md) for more information about the `LIST` command

The syntax used to display backups of multitenant container databases (CDBs) and pluggable databases (PDBs), which has minor variations from that used for non-CDBs, is described in [Oracle Database Backup and Recovery User’s Guide](../bradv/reporting-rman-operations.md).

##### To display all backups:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."

2.  Use the `LIST` command to display a summary of all the backups, both backup sets and image copies.

        LIST BACKUP SUMMARY;

        List of Backups
        ===============
        Key     TY LV S Device Type Completion Time #Pieces #Copies Compressed Tag
        ------- -- -- - ----------- --------------- ------- ------- ---------- ---
        12      B  F  A DISK        28-MAR-12       1       1       NO         TAG20120328T051810
        13      B  F  A DISK        28-MAR-12       1       1       NO         TAG20120328T051811
        14      B  F  A DISK        28-MAR-12       1       1       NO         TAG20120328T051921
        15      B  F  A DISK        28-MAR-12       1       1       NO         TAG20120328T051936
        16      B  F  A DISK        28-MAR-12       1       1       NO         TAG20120328T052241

##### To display selected backups:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Use the `LIST BACKUP` or `LIST COPY` command to display the specified backups, both backup sets and image copies.
    - For example, to list the backups of a particular datafile:

          LIST BACKUP OF DATAFILE 3;
          LIST COPY OF DATAFILE '/orcl/oradata/trgt/system01.dbf';

    - To display backups sorted by the type of database file:

          LIST BACKUP BY FILE;

          List of Datafile Backups
          ========================
          File Key     TY LV S Ckp SCN    Ckp Time  #Pieces #Copies Compressed Tag
          ---- ------- -  -- - ---------- --------- ------- ------- ---------- ---
          1    14      B  F  A 723546     28-MAR-12 1       1       NO         TAG20120328T051921
          2    14      B  F  A 723546     28-MAR-12 1       1       NO         TAG20120328T051921
          3    14      B  F  A 723546     28-MAR-12 1       1       NO         TAG20120328T051921
          4    14      B  F  A 723546     28-MAR-12 1       1       NO         TAG20120328T051921
          5    14      B  F  A 723546     28-MAR-12 1       1       NO         TAG20120328T051921

          List of Control File Backups
          ===========================
          CF Ckp SCN Ckp Time  BS Key  S #Pieces #Copies Compressed Tag
          ---------- --------- ------- - ------- ------- ---------- ---
          723835     28-MAR-12 16      A 1       1       NO         TAG20120328T052241
          723557     28-MAR-12 15      A 1       1       NO         TAG20120328T051936
          723490     28-MAR-12 13      A 1       1       NO         TAG20120328T051811

#### 9.4.4 Validating Backups and Testing Your Backup Strategy

As part of your backup strategy, you should periodically check whether your backups are intact and can be used to meet your recoverability objectives. You can validate your backups in the following ways:

You can validate your backups in the following ways:

- Select specific backup sets or image copies in Oracle Recovery Manager (RMAN) and validate them. This technique indicates if a backup exists and can be restored. For this form of validation, use the steps described in "Validating Selected Backups."

- Specify database files and let RMAN select backups to use when restoring those files, as it would for an actual restore operation. This technique ensures that your available backups are sufficient to restore the database. For this form of validation, use the steps described in "Validating Backups for Restore Operations."

  **Note:**

  Validating backups stored on tape can be time-consuming because the entire backup is read from tape.

You can perform both forms of validation using RMAN. You should incorporate both forms of validation into your backup strategy to ensure that your recoverability goals are met by your available backups.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/validating-database-files-backups.md) for information about validating backups of multitenant container databases (CDBs) and pluggable databases (PDBs)

##### 9.4.4.1 Validating Selected Backups

Validating specific backups checks whether these backups exist and can be restored. It does not test whether the set of available backups meet your recoverability goals. For example, image copies of data files for several tablespaces from your database may exist, each of which can be validated. If there are some tablespaces for which no valid backups exist, however, then you cannot restore and recover the database.

##### To validate selected backups:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Validate the required backup.
    The following `VALIDATE` command validates the datafile `users_02.dbf`.

        VALIDATE DATAFILE '/ora112/oradata/users_02.dbf';

        Starting validate at 27-MAR-12
        using channel ORA_DISK_1
        channel ORA_DISK_1: starting validation of datafile
        channel ORA_DISK_1: specifying datafile(s) for validation
        input datafile file number=00020
        name=/ora112/oradata/users_02.dbf
        channel ORA_DISK_1: validation complete, elapsed time: 00:00:01

        List of Datafiles
        =================
        File Status Marked Corrupt Empty Blocks Blocks Examined High SCN
        ---- ------ -------------- ------------ --------------- ----------
        20   OK     0              248          256             618976

        File Name: /ora112/oradata/users_02.dbf
        Block Type Blocks Failing Blocks Processed
          ---------- -------------- ----------------
          Data       0              0
          Index      0              0
          Other      0              8

        Finished validate at 27-MAR-12

When you suspect that one or more backup pieces in a backup set are missing or have been damaged, use the `VALIDATE BACKUPSET` command to validate the backup set.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/validating-database-files-backups.md) for more information about validating backups

##### 9.4.4.2 Validating Backups for Restore Operations

You can test whether a sufficient set of backups exists that can be used to restore the specified database files. After you specify which tablespaces to restore and, possibly, a time as of which to restore them, Oracle Recovery Manager (RMAN) selects a set of backups that contain the needed data. RMAN reads the selected backups in their entirety to confirm that they are not corrupt, but does not produce output files.

Validating the restoration of files tests whether the file can be restored given the available backups, but it does not test whether all backups of the specified object are valid.

##### To verify whether specified database files can be restored:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Run the `RESTORE … VALIDATE` command to determine if the required database files can be restored.
    - To determine if the whole database can be restored:

          RESTORE VALIDATE DATABASE;

          Starting restore at 29-MAR-12
          using target database control file instead of recovery catalog
          allocated channel: ORA_DISK_1
          channel ORA_DISK_1: SID=129 device type=DISK
          channel ORA_DISK_1: scanning datafile copy /ade/b/191802369/oracle/work/orcva/RDBMS/datafile/o1_mf_tbs_3_7q60nj4y_.dbf
          channel ORA_DISK_1: starting validation of datafile backup set
          channel ORA_DISK_1: reading from backup piece /ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120328T051921_7q60g9oc_.bkp
          channel ORA_DISK_1: piece handle=/ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120328T051921_7q60g9oc_.bkp tag=TAG20120328T051921
          channel ORA_DISK_1: restored backup piece 1
          channel ORA_DISK_1: validation complete, elapsed time: 00:00:04
          Finished restore at 29-MAR-12

    - To determine if a specified tablespace can be restored:

          RESTORE TABLESPACE example VALIDATE;

          Starting restore at 29-MAR-12
          using channel ORA_DISK_1
          channel ORA_DISK_1: starting validation of datafile backup set
          channel ORA_DISK_1: reading from backup piece /ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120328T051921_7q60g9oc_.bkp
          channel ORA_DISK_1: piece handle=/ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120328T051921_7q60g9oc_.bkp tag=TAG20120328T051921
          channel ORA_DISK_1: restored backup piece 1
          channel ORA_DISK_1: validation complete, elapsed time: 00:00:01
          Finished restore at 29-MAR-12

    - To determine if a datafile can be restored to a specified SCN:

          RESTORE DATAFILE 1 VALIDATE UNTIL SCN 23456;

          Starting restore at 29-MAR-12
          using channel ORA_DISK_1
          channel ORA_DISK_1: starting validation of datafile backup set
          channel ORA_DISK_1: reading from backup piece /ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120330T044454_7qc75qyd_.bkp
          channel ORA_DISK_1: piece handle=/ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_03_28/o1_mf_nnndf_TAG20120330T044454_7qc75qyd_.bkp tag=TAG20120330T044454
          channel ORA_DISK_1: restored backup piece 1
          channel ORA_DISK_1: validation complete, elapsed time: 00:00:03
          Finished restore at 29-MAR-12

**See Also:**

- [Oracle Database Concepts](../cncpt/concepts-for-database-administrators.md) for datafile recovery concepts

- [Oracle Database Backup and Recovery User’s Guide](../bradv/validating-database-files-backups.md) to learn how to use the `RESTORE` `...` `VALIDATE` command

### 9.5 Displaying Backup Reports

Backup reports contain summary and detailed information about past backup jobs run by Oracle Recovery Manager (RMAN). The view `V$RMAN_BACKUP_JOB_DETAILS` contains information about backup jobs run by RMAN. This view contains information such as the time taken for the backup, when a job started and finished, and what type of backup was performed, and the status of the backup job.

#### To display backup reports:

Use the following query to display the backup job history.

    SELECT SESSION_KEY,INPUT_TYPE,STATUS,START_TIME,END_TIME,ELAPSED_SECONDS/3600 hrs
    FROM V$RMAN_BACKUP_JOB_DETAILS;

    SESSION_KEY INPUT_TYPE    STATUS                  START_TIM END_TIME         HRS
    ----------- ------------- ----------------------- --------- --------- ----------
              8 DB FULL       FAILED                  27-MAR-12 27-MAR-12 1.64666666
             50 DB FULL       COMPLETED               28-MAR-12 28-MAR-12 .243055555
             69 DB FULL       COMPLETED               30-MAR-12 05-APR-12 147.176388

`SESSION_KEY` is the unique key for the RMAN session in which the backup job occurred.

### 9.6 Managing Backups

As part of a backup strategy, you must manage database backups. A related task is managing the record of those backups in the Oracle Recovery Manager (RMAN) repository. RMAN simplifies these tasks.

In a multitenant environment, you can manage backups for the whole multitenant container database (CDB) or for one or more pluggable databases (PDBs). The steps in this section are applicable to CDBs and PDBs, with minor modifications. To manage backups for the whole CDB, connect to the root and use the steps described in this section. To manage backups of a single PDB, connect to that PDB and use the steps described in this section. To manage backups of multiple PDBs using one command, connect to the root and use the `PLUGGABLE DATABASE` clause followed by a list of PDBs.

This section contains the following topics:

- About Backup Management

- Cross-Checking Backups

- Deleting Expired Backups

- Marking Backups as Available or Unavailable

- Deleting Obsolete Backups

- Monitoring Fast Recovery Area Space Usage

#### 9.6.1 About Backup Management

An essential part of a backup and recovery strategy is managing backups after you create them. Backup management includes deleting obsolete backups and performing periodic checks to ensure that backups are available and usable.

A backup recorded in the Oracle Recovery Manager (RMAN) repository has one of the following status values:

- Available, meaning that the backup is still present on disk or tape, as recorded in the repository

- Expired, meaning that the backup no longer exists on disk or tape, but is still listed in the repository

- Unavailable, meaning that the backup is temporarily not available for data recovery operations (because, for example, it is stored on a tape that is stored offsite or on a disk that is currently not mounted)

Backups can also be obsolete. An obsolete backup is, based on the currently configured retention policy, no longer needed to satisfy data recovery goals.

Maintenance tasks that you can perform in RMAN include the following:

- Viewing details about your backups

- Cross-checking your repository, which means checking whether backups listed in the repository exist and are accessible, and marking as expired any backups not accessible at the time of the cross-check

- Deleting the record of expired backups from your RMAN repository

- Deleting obsolete backups from the repository and from the backup media

- Validating backups to ensure that a given backup is available and not corrupted

**Note:**

If a backup no longer exists, then immediately delete the backup record from the RMAN repository. Without an accurate record of available backups, you may discover that you no longer have complete backups of your database when you must perform a recovery.

Some tasks, such as periodic cross-checks of your backups, should be among the regularly scheduled components of your backup strategy.

If you use a fast recovery area for backup storage, then many maintenance activities are reduced or eliminated. The automatic storage space management mechanisms delete backups and other files as needed, thereby satisfying storage space demands for ongoing database operations without compromising the retention policy. However, you must monitor space usage in the fast recovery area to ensure that it is large enough to contain backups and other recovery-related files.

#### 9.6.2 Cross-Checking Backups

Cross-checking a backup synchronizes the physical reality of backups with their logical records in the Oracle Recovery Manager (RMAN) repository. For example, if a backup on disk was deleted with an operating system command, then a cross-check detects this condition. After the cross-check, the RMAN repository correctly reflects the state of the backups.

Backups to disk are listed as available if they are still on disk in the location listed in the RMAN repository, and if they have no corruption in the file header. Backups on tape are listed as available if they are still on tape. The file headers on tape are not checked for corruption. Backups that are missing or corrupt are listed as expired.

##### To cross-check individual files:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."

2.  Display a summary of the existing backups to determine which backup you want to cross-check.

        LIST BACKUP SUMMARY;

3.  Identify the backup that you want to cross-check from the output of the previous `LIST` command.

4.  Cross-check the identified file using the `CROSSCHECK` command.

    - To cross-check the backup set 1345:

          CROSSCHECK BACKUPSET 1345;

          using channel ORA_DISK_1
          crosschecked backup piece: found to be 'AVAILABLE'
          backup piece handle=/ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_04_05/o1_mf_annnn_TAG20120405T075520_7qvdlrsl_.bkp RECID=1345 STAMP=779788520
          Crosschecked 1 objects

    - To cross-check the data files 1 and 5:

          CROSSCHECK DATAFILECOPY 1,5;

##### To cross-check all files:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  To crosscheck all backup sets, use the following command:
        CROSSCHECK BACKUP;

**Note:**

Cross-checking all backups in the RMAN repository may take a long time, especially for tape backups. A cross-check of all files, unlike cross-checking individual files, is handled as a scheduled job.

**See Also:**

[Oracle Database Backup and Recovery Reference](../rcmrf/CROSSCHECK.md) for the syntax used to cross-check backups of multitenant container databases (CDBs) and pluggable databases (PDBs)

#### 9.6.3 Deleting Expired Backups

Deleting expired backups removes from the Oracle Recovery Manager (RMAN) repository those backups that are listed as `EXPIRED`. Expired backups are those found to be inaccessible during a cross-check. No attempt is made to delete the files containing the backup from disk or tape; this action updates only the RMAN repository.

**See Also:**

[Oracle Database Backup and Recovery Reference](../rcmrf/DELETE.md) for the syntax used to delete expired backups of multitenant container databases (CDBs) and pluggable databases (PDBs)

##### To delete expired backups:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Optionally, cross-check backup sets by using the following command:
        CROSSCHECK BACKUPSET;

    Cross-checking backups before you delete expired backups provides RMAN with up-to-date information about which backups are expired.
3.  Delete expired backups using the following command:
        DELETE EXPIRED BACKUP;

    The expired backup sets and image copies are deleted from the RMAN repository.

#### 9.6.4 Marking Backups as Available or Unavailable

If one or more specific backups are unavailable because of a temporary condition, such as a disk drive that is temporarily offline or a tape stored offsite, then you can mark those backups as unavailable. Oracle Recovery Manager (RMAN) does not use unavailable backups to restore or recover data.

**Note:**

Backups stored in the fast recovery area cannot be marked as unavailable.

RMAN keeps the record of unavailable backups in the RMAN repository and does not delete backups listed as unavailable when you delete expired backups. If the unavailable backups become accessible again, then you can mark them as available.

**See Also:**

[Oracle Database Backup and Recovery Reference](../rcmrf/CHANGE.md) for the syntax used for multitenant container databases (CDBs) and pluggable databases (PDBs)

##### To mark backups as available or unavailable:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Optionally, cross-check backup sets by using the following command:
        CROSSCHECK BACKUP;

    Cross-checking backups before you delete expired backups provides RMAN with up-to-date information about which backups are expired.
3.  Display a summary of the available backups.
        LIST BACKUP SUMMARY;

        List of Backups
        ===============
        Key TY LV S Device Type Completion Time #Pieces #Copies Compressed Tag
        ------- -- -- - ----------- --------------- ------- ------- ---------- ---
        1 B A A DISK 24-FEB-07 1 1 NO TAG20070427T115348
        3 B A A DISK 24-MAR-07 1 1 NO TAG20070427T115452
        4 B F A DISK 24-APR-07 1 1 NO TAG20070427T115456
4.  From the output of the `LIST` command, identify the backup that you want to make available or unavailable. Use the value displayed in the Key column to identify a backup set.
5.  Change the status of the identified backup to unavailable by using the `CHANGE` command.
    The following command marks the backup set 4 unavailable:

        CHANGE BACKUPSET 4 UNAVAILABLE;

        changed backup piece available
        backup piece handle=/ade/b/191802369/oracle/work/orcva/RDBMS/backupset/2012_04_05/o1_mf_annnn_TAG20120405T075520_7qvdlrsl_.bkp RECID=23 STAMP=779788520
        Changed 1 objects to AVAILABLE status

    To mark the backup set 4 available, use the following command:

        CHANGE BACKUPSET 4 AVAILABLE;

#### 9.6.5 Deleting Obsolete Backups

This section explains how to delete obsolete backups, which are those no longer needed by the configured retention policy. If you use a fast recovery area as your only disk-based backup destination, then you never have to delete obsolete backups from disk. The fast recovery area keeps files as specified by the retention policy, and deletes them only when space is needed.

**See Also:**

[Oracle Database Backup and Recovery Reference](../rcmrf/DELETE.md) for the syntax used to delete obsolete backups of CDBs and PDBs

##### To delete obsolete backups:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Delete all obsolete backups, including backup sets and image copies, using the following command:
        DELETE OBSOLETE;

    RMAN displays the list of obsolete backups and asks for confirmation about deleting the listed backups.

#### 9.6.6 Monitoring Fast Recovery Area Space Usage

It is important to monitor space usage in the fast recovery area to ensure that it is large enough to contain backups and other recovery-related files. Oracle Database provides two views to monitor fast recovery area space usage, `V$RECOVERY_FILE_DEST` and `V$RECOVERY_AREA_USAGE`.

Use the `V$RECOVERY_FILE_DEST` view to obtain the following information about the fast recovery area: total number of files, current location, disk quota, space in use, and space reclaimable by deleting files. The space details are in bytes. Querying `V$RECOVERY_FILE_DEST` produces the following output.

    SELECT * FROM V$RECOVERY_FILE_DEST;

    NAME         SPACE_LIMIT SPACE_USED SPACE_RECLAIMABLE NUMBER_OF_FILES
    -------------- ----------- ---------- ----------------- ---------------
    /mydisk/rcva 5368709120  109240320  256000            28

The `V$RECOVERY_AREA_USAGE` view contains the percentage of disk quota used by different type of files, and the percentage of space that can be reclaimed by deleting files that are obsolete, redundant, or backed up to tape. Querying the `V$RECOVER_AREA_USAGE` view produces the following output.

    SELECT * FROM V$RECOVERY_AREA_USAGE;

    FILE_TYPE    PERCENT_SPACE_USED  PERCENT_SPACE_RECLAIMABLE  NUMBER_OF_FILES
    ------------ ------------------  -------------------------  ---------------
    CONTROLFILE        0                  0                         0
    ONLINELOG          2                  0                         22
    ARCHIVELOG         4.05              2.01                       31
    BACKUPPIECE        3.94              3.86                       8
    IMAGECOPY         15.64              10.43                      66
    FLASHBACKLOG       .08                0                         1

**See Also:**

"Configuring Your Database for Basic Backup and Recovery"

### 9.7 Performing Oracle Advised Recovery

The Oracle advised recovery feature uses Data Recovery Advisor, which is an Oracle Database feature that automatically diagnoses data failures, determines and presents appropriate repair options, and performs repairs if requested by the user. By providing a centralized tool for automated data repair, Data Recovery Advisor improves the manageability and reliability of an Oracle database.

**Note:**

Data Recovery Advisor can only be used to diagnose and repair failures in multitenant container databases (CDBs). It is not supported for pluggable databases (PDBs).

RMAN provides a command-line interface to the Data Recovery Advisor. You can use following RMAN commands to diagnose and repair data failures for the Oracle Database, including for Oracle RAC databases:

- `LIST FAILURE`

  Use this command to view problem statements for failures and the effect of these failures on database operations. Each failure is identified by a failure number.

- `ADVISE FAILURE`

  Use this command to view repair options, including both automated and manual repair options.

- `REPAIR FAILURE`

  Use this command to automatically repair failures listed by the most recent `ADVISE FAILURE` command.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/diagnosing-repairing-failures-dra.md) for information about altering the status or priority of a failure by using the `CHANGE FAILURE` command

This section contains the following topics:

- About Data Recovery Advisor

- Using Data Recovery Advisor

#### 9.7.1 About Data Recovery Advisor

In the context of Data Recovery Advisor, a health check is a diagnostic procedure run by the Health Monitor to assess the state of the database or its components. Health checks are invoked reactively when an error occurs. You can also invoke checks manually.

A **failure** is a persistent data corruption detected by a health check. Failures are usually detected reactively. A database operation involving corrupted data results in an error, which automatically invokes a health check in the database. The check searches the database for failures related to the error. If failures are diagnosed, then they are recorded in the Automatic Diagnostic Repository (ADR).

You can use Data Recovery Advisor to generate repair advice and repair failures only after failures have been detected by the database and stored in ADR. Data Recovery Advisor can report on and repair failures such as inaccessible files, physical and logical block corruptions, and I/O failures. Every failure has a failure priority: CRITICAL, HIGH, or LOW. Every failure also has a failure status of OPEN or CLOSED.

You can also use Data Recovery Advisor to view repair options. A **repair** is an action that fixes one or more failures. Examples of repairs include block media recovery, data file media recovery, and Oracle Flashback Database. Typically, Data Recovery Advisor presents both automated and manual repair options. If appropriate, you can choose an automated repair option in order to perform a repair. In this case, Data Recovery Advisor verifies the repair success, and closes the relevant repaired failures.

#### 9.7.2 Using Data Recovery Advisor

The recovery process begins when you either suspect or discover a failure. You can discover failures in many ways, including error messages, alerts, trace files, and health checks. You can then use Data Recovery Advisor to gain information and advice about failures and repair them automatically.

This section describes a scenario in which you use Data Recovery Advisor to repair a corrupted block.

##### To use the Oracle advised recovery strategy to automatically repair failures:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
    In a multitenant environment, connect to the root as a common user with the `SYSDBA` or `SYSBACKUP` privilege.
2.  List all the failures know to the Data Recovery Advisor by running the following command:
        LIST FAILURE;

        List of Database Failures
        =========================
        Failure ID Priority Status Time Detected Summary
        ---------- -------- ------ ------------- --------
        142        HIGH     OPEN   23-APR-07     One or more non-system datafiles are
                                                 missing
        101        HIGH     OPEN   23-APR-07     Datafile 1: '/disk1/oradata/prod/
                                                 system01.dbf' contains one or more
                                                 corrupt blocks

    Wherever possible, RMAN consolidates failures while displaying the result of the `LIST FAILURE` command. For example, if a data file contains multiple block failures, the `LIST FAILURE` command consolidates and displays the repair options.

    **See Also:**

    [Oracle Database Backup and Recovery User’s Guide](../bradv/diagnosing-repairing-failures-dra.md) for information about using the `LIST FAILURE ... DETAIL` command to display failures individually
3.  If you suspect that some failures that have not been automatically diagnosed by the database exist, then check for corrupt blocks and missing data files by using the following command:
        VALIDATE DATABASE;

    If a problem is detected during the validation, then RMAN triggers the execution of a failure assessment
4.  Determine repair options, both automatic and manual, by using the following command:
        ADVISE FAILURE;
5.  Fix the failures by using the following command:
        REPAIR FAILURE;

    Automated repairs are performed by the Data Recovery Advisor. In certain cases, such as when no backups exist for a lost control file, the only repair option possible is the manual option.

### 9.8 Performing User-Directed Recovery

User-Directed Recovery enables you to use flashback features and perform restore operations and recovery procedures. For example, you can do the following:

- Repair unwanted changes to database objects with the logical flashback features

- Rewind the entire database with Oracle Flashback Database

- Completely restore and recover the database

- Perform point-in-time recovery of the database or selected tablespaces

- Perform block media recovery of data files that have corrupted blocks

You can determine which parts of the database must be restored and recovered, including detecting situations such as corrupted database files before they affect database operations.

This section contains a few typical recovery examples so that you can become familiar with the performing whole database or object-level recovery using Oracle Recovery Manager (RMAN). Use the `RESTORE` and `RECOVER` commands to perform whole database or object-level recovery.

This section contains the following topics:

- Rewinding a Table Using Oracle Flashback Table

- Recovering a Dropped Table Using Oracle Flashback Drop

- Rewinding a Database Using Oracle Flashback Database

- Restoring and Recovering the Database

#### 9.8.1 Rewinding a Table Using Oracle Flashback Table

Oracle Flashback Table enables you to rewind one or more tables back to their contents at a previous time without affecting other database objects. Thus, you can recover from logical data corruptions such as table rows added or deleted accidentally. Unlike point-in-time recovery, the database remains available during the flashback operation.

For this example, you use Flashback Table on the `employees` table in the `hr` schema. Assume that an erroneous update shortly after October 23, 2005 at 15:30:00 has changed the `lastname` column for all employees to an empty string, and you must return the original `lastname` values to the table.

This section contains the following topics:

- Enabling Row Movement on a Table

- Performing a Flashback Table Operation

##### 9.8.1.1 Enabling Row Movement on a Table

Before you can use Flashback Table, you must ensure that row movement is enabled on the table to be flashed back, or returned to a previous state. Row movement indicates that rowids will change after the flashback occurs. This restriction exists because if rowids before the flashback were stored by an application, then there is no guarantee that the rowids will correspond to the same rows after the flashback.

##### To enable row movement on a table:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Enable row movement for all the objects that you want to rewind using Flashback Table.
    The following command enables row movement for the `hr.employees` table.

        ALTER TABLE hr.employees ENABLE ROW MOVEMENT;

    For this example, you must also enable row movement on the tables `hr.jobs` and `hr.departments.`

##### 9.8.1.2 Performing a Flashback Table Operation

In this example, you rewind the `hr.employees` table and its dependent tables to a previous point in time.

##### To perform the Flashback Table operation:

1.  Connect Oracle Recovery Manager (RMAN) to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Determine whether the table that you intend to flash back has dependencies on other tables.
    Use the following SQL query to determine the dependencies for the `hr.employees`:

        SELECT other.owner, other.table_name
            FROM sys.all_constraints this, sys.all_constraints other
            WHERE this.owner = 'HR'
              AND this.table_name = 'EMPLOYEES'
              AND this.r_owner = other.owner
              AND this.r_constraint_name = other.constraint_name
              AND this.constraint_type='R';

        OWNER                          TABLE_NAME
        ------------------------------ ------------------------------
        HR                             EMPLOYEES
        HR                             JOBS
        HR                             DEPARTMENTS
3.  Ensure that row movement is enabled for the table that you want to flash back and its dependent tables.
    In this example, row movement must be enabled for the tables `hr.employees`, `hr.jobs`, and `hr.departments` using the steps described in "Enabling Row Movement on a Table."
4.  Identify the time, SCN, or restore point to which you want to return the table.
    In this example, we assume that the rows were accidentally inserted 5 minutes ago. Therefore, you must rollback to a timestamp that is 5 minutes before the current time.

    **Note:**

    If you do not know the time at which the unwanted changes occurred, you can use the Oracle Flashback Version Query to review all recent changes to the target table. Use of this feature is beyond the scope of this documentation.
5.  Verify that enough undo data exists to rewind the table to the specified target.
    Use the following query to determine how long undo data is being retained:

        SELECT NAME, VALUE/60 MINUTES_RETAINED
            FROM V$PARAMETER
            WHERE NAME = 'undo_retention';

        NAME             MINUTES_RETAINED
        ---------------  ----------------
        undo_retention               15
6.  Use the `FLASHBACK TABLE` statement to perform a flashback operation for the required tables.
    The following SQL statements return the tables `hr.employees`, `hr.jobs`, and `hr.departments` to the specified time:

        FLASHBACK TABLE hr.employees TO TIMESTAMP TO_TIMESTAMP('2012-03-27 09:30:00', 'YYYY-MM-DD HH:MI:SS');

        FLASHBACK TABLE hr.jobs TO TIMESTAMP TO_TIMESTAMP('2012-03-27 09:30:00', 'YYYY-MM-DD HH:MI:SS');

        FLASHBACK TABLE hr.departments TO TIMESTAMP TO_TIMESTAMP('2012-03-27 09:30:00', 'YYYY-MM-DD HH:MI:SS');

**See Also:**

- "Rewinding a Table Using Oracle Flashback Table"

- "Performing Oracle Advised Recovery"

#### 9.8.2 Recovering a Dropped Table Using Oracle Flashback Drop

Oracle Flashback Drop enables you to reverse the effects of dropping (deleting) a table, returning the dropped table to the database along with dependent objects such as indexes and triggers. This feature stores dropped objects in a recycle bin, from which they can be retrieved until the recycle bin is purged, either explicitly or because space is needed.

As with Flashback Table, you can use Flashback Drop while the database is open. Also, you can perform the flashback without undoing changes in objects not affected by the Flashback Drop operation. Flashback Table is more convenient than forms of media recovery that require taking the database offline and restoring files from backup.

**Note:**

For a table to be recoverable using Flashback Drop, it must reside in a locally managed tablespace. Also, you cannot recover tables in the `SYSTEM` tablespaces with Flashback Drop, regardless of the tablespace type.

This section contains the following topics:

- Dropping a Table

- Retrieving a Dropped Table

##### 9.8.2.1 Dropping a Table

For the purpose of learning about Flashback Drop, you will create a new table named `reg_hist` and then drop it. The database places the table in the recycle bin so that it can be retrieved with the Flashback Drop feature.

##### To create and then drop a table:

1.  Connect SQL\*Plus to the `hr` schema.
2.  Create table `reg_hist` based on the existing `REGIONS` table in the `hr` schema by using the following command:
        CREATE TABLE reg_hist as SELECT * FROM REGIONS;
3.  Drop the `reg_hist` table using the following command:
        DROP TABLE REG_HIST;

    Because Flashback is enabled for the database, the dropped table is stored in the recycle bin.
4.  Display the tables in the `hr` schema.
        SELECT * FROM TAB;

        TNAME                          TABTYPE  CLUSTERID
        ------------------------------ ------- ----------
        BIN$ANbliLHaSiu02xI+zbvDvQ==$0  TABLE
        COUNTRIES                       TABLE
        DEPARTMENTS                     TABLE
        EMPLOYEES                       TABLE
        EMP_DETAILS_VIEW                VIEW
        JOBS                            TABLE
        JOB_HISTORY                     TABLE
        LOCATIONS                       TABLE
        REGIONS                         TABLE

        9 rows selected.

    The first name displayed in the command output, beginning with 'BIN', is the table that you just dropped. Because Flashback Database is enabled, the deleted table is still in the recycle bin and is therefore displayed in the command output.

##### 9.8.2.2 Retrieving a Dropped Table

The following procedure retrieves `reg_hist` from the recycle bin. This section assumes that you created and then dropped the `reg_hist` table, as described in "Dropping a Table."

##### To perform the Flashback Drop operation:

1.  Connect SQL\*Plus to the `hr` schema and obtain the name of the dropped table in the recycle bin.
        SHOW RECYCLEBIN;

        ORIGINAL NAME  RECYCLEBIN NAME                OBJECT TYPE   DROP TIME
        -------------- ------------------------------ ------------  -----------
        REG_HIST       BIN$ANbliLHaSiu02xI+zbvDvQ==$0  TABLE      2012-03-26:16:51:54
2.  Retrieve the dropped table using the `FLASHBACK TABLE … TO BEFORE DROP` command.
    The following command performs a flashback of the `HR.REG_HIST` table.

        FLASHBACK TABLE HR.REG_HIST TO BEFORE DROP;

    **Note:**

    When a table is retrieved from the recycle bin, all the dependent objects for the table that are in the recycle bin are retrieved with it. They cannot be retrieved separately.
3.  If the retrieved table had referential constraints before it was placed in the recycle bin, then re-create them.
    This step must be performed manually because the recycle bin does not preserve referential constraints on a table.

#### 9.8.3 Rewinding a Database Using Oracle Flashback Database

Unlike the other flashback features, Oracle Flashback Database operates at a physical level. When you use Flashback Database, your current data files revert to their contents at a previous time. The result is similar to database point-in-time recovery, but Flashback Database can be much faster because it does not require you to restore and recover data files. Also, Flashback Database requires limited application of redo data as compared to media recovery.

Flashback Database uses flashback logs to access previous versions of data blocks and also uses some data in the archived redo log files. To have the option of using Flashback Database to repair your database, you must have configured the database to generate flashback logs as explained in "Configuring Recovery Settings."

**Note:**

You can use the Oracle Recovery Manager (RMAN) `FLASHBACK DATABASE` command to rewind the entire multitenant container database (CDB) only, not individual pluggable databases (PDBs).

##### To perform a Flashback Database operation:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Identify the desired SCN, restore point, or point in time to which the flashback database must be performed. This example rewinds the database to a specified point in time.
    **See Also:**

    [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-performing-flashback-dbpitr.md) for information about how to determine the SCN and then flashback the database to this SCN
3.  Shut down the database consistently, ensure that it is not opened by any instance, and then mount the database.
        SHUTDOWN IMMEDIATE;
        STARTUP MOUNT;
4.  Flash back the database to the desired time.
    In this example, you need to flashback the entire database to the time specified in the `TIME` clause.

        FLASHBACK DATABASE to TIME "TO_DATE('03/20/12','MM/DD/YY')";
5.  Open the database read-only and run some queries to verify the database contents.
    The following command opens the database in read-only mode:

        ALTER DATABASE OPEN READ ONLY;
6.  After confirming that the state of the database is as expected, make the database available for updates by opening it with the `RESETLOGS` option.
        SHUTDOWN IMMEDIATE;
        STARTUP MOUNT;
        ALTER DATABASE OPEN RESETLOGS;

#### 9.8.4 Restoring and Recovering the Database

This section demonstrates how to restore and recover the entire database using Oracle Recovery Manager (RMAN). This example assumes that you are restoring and recovering your database after the loss of one or more data files, but you still have a usable server parameter file and control file. You can also use RMAN to restore a lost server parameter file or control file.

##### To restore and recover the entire database:

1.  Connect RMAN to the target database as described in "Connecting to the Target Database Using RMAN."
2.  Ensure that the database is mounted, but not open.
        SHUTDOWN IMMEDIATE;
        STARTUP MOUNT;
3.  Restore the database using the following command:
        RESTORE DATABASE;

    The data files from the RMAN backup are restored to their default locations.
4.  Recover the database using the `RECOVER` command.
        RECOVER DATABASE;
5.  Open the database using the following command:
        ALTER DATABASE OPEN;

**See Also:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-complete-database-recovery.md) for information about recovering multitenant container databases (CDBs) and pluggable databases (PDBs)

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-recovery-advanced.md) for instructions for recovering a database when the control file and server parameter file are available only on backup

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-complete-database-recovery.md) for information about restoring data files to a location that is different from the default location

### 9.9 Performing Backup and Recovery: Oracle By Example Series

Oracle By Example (OBE) has a series on the Oracle Database 2 Day DBA guide. This OBE series steps you through the tasks in this section, and includes annotated screenshots.

The series consists of the following tutorials:

1.  Connect to the Target Database

2.  Configure Recovery Settings

3.  Configure Backup Settings

4.  Perform and Schedule Backups

5.  Manage Backups

6.  Use Oracle Recovery Advisor to Repair Failures

7.  Rewind a Table Using Oracle Flashback Table

8.  Recover a Dropped Table Using Oracle Flashback Drop

The above tutorials can be accessed in two ways:

- To see a clickable list of the above tutorials, go to [Perform Database Backup and Recovery Operations Series](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_obe_backrec).

- For seamless navigation through the tutorial series, access the following link:

  [Perform Database Backup and Recovery Operations](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_lp_backrec)

  You can navigate across the tutorials by clicking the \> button at the bottom of the pane.
