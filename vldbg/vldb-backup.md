Backup and recovery is a crucial and important job for a DBA to protect business data.

As data storage grows larger each year, DBAs are continually challenged to ensure that critical data is backed up and that it can be recovered quickly and easily to meet business needs. Very large databases are unique in that they are large and data may come from many resources. OLTP and data warehouse systems have some distinct characteristics. Generally, the availability considerations for a very large OLTP system are no different from the considerations for a small OLTP system. Assuming a fixed allowed downtime, a large OLTP system requires more hardware resources than a small OLTP system.

This chapter proposes an efficient backup and recovery strategy for very large databases to reduce the overall resources necessary to support backup and recovery by using some special characteristics that differentiate data warehouses from OLTP systems.

This chapter contains the following sections:

- Data Warehouses

- Oracle Backup and Recovery

- Data Warehouse Backup and Recovery

- The Data Warehouse Recovery Methodology

### 9.1 Data Warehouses

A data warehouse is a system that is designed to support analysis and decision-making.

In a typical enterprise, hundreds or thousands of users may rely on the data warehouse to provide the information to help them understand their business and make better decisions. Therefore, availability is a key requirement for data warehousing. This chapter discusses one key aspect of data warehouse availability: the recovery of data after a data loss.

Before looking at the backup and recovery techniques in detail, it is important to discuss specific techniques for backup and recovery of a data warehouse. In particular, one legitimate question might be: Should a data warehouse backup and recovery strategy be just like that of every other database system?

A DBA should initially approach the task of data warehouse backup and recovery by applying the same techniques that are used in OLTP systems: the DBA must decide what information to protect and quickly recover when media recovery is required, prioritizing data according to its importance and the degree to which it changes. However, the issue that commonly arises for data warehouses is that an approach that is efficient and cost-effective for a 100 GB OLTP system may not be viable for a 10 TB data warehouse. The backup and recovery may take 100 times longer or require 100 times more storage.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/introduction-data-warehouse-concepts.md) for more information about data warehouses

#### 9.1.1 Data Warehouse Characteristics

There are several key differences between data warehouses and OLTP systems that have significant impacts on backup and recovery.

These differences are:

1.  A data warehouse is typically much larger than an OLTP system. Data warehouses over 10's of terabytes are not uncommon and the largest data warehouses grow to orders of magnitude larger. Thus, scalability is a particularly important consideration for data warehouse backup and recovery.

2.  A data warehouse often has lower availability requirements than an OLTP system. While data warehouses are critical to businesses, there is also a significant cost associated with the ability to recover multiple terabytes in a few hours compared to recovering in a day. Some organizations may determine that in the unlikely event of a failure requiring the recovery of a significant portion of the data warehouse, they may tolerate an outage of a day or more if they can save significant expenditures in backup hardware and storage.

3.  A data warehouse is typically updated through a controlled process called the ETL (Extract, Transform, Load) process, unlike in OLTP systems where users are modifying data themselves. Because the data modifications are done in a controlled process, the updates to a data warehouse are often known and reproducible from sources other than redo logs.

4.  A data warehouse contains historical information, and often, significant portions of the older data in a data warehouse are static. For example, a data warehouse may track five years of historical sales data. While the most recent year of data may still be subject to modifications (due to returns, restatements, and so on), the last four years of data may be entirely static. The advantage of static data is that it does not need to be backed up frequently.

These four characteristics are key considerations when devising a backup and recovery strategy that is optimized for data warehouses.

### 9.2 Oracle Backup and Recovery

In general, backup and recovery refers to the various strategies and procedures involved in protecting your database against data loss and reconstructing the database after any kind of data loss.

A backup is a representative copy of data. This copy can include important parts of a database such as the control file, archived redo logs, and data files. A backup protects data from application error and acts as a safeguard against unexpected data loss, by providing a way to restore original data.

This section contains the following topics:

- Physical Database Structures Used in Recovering Data

- Backup Type

- Backup Tools

#### 9.2.1 Physical Database Structures Used in Recovering Data

Before you begin to think seriously about a backup and recovery strategy, the physical data structures relevant for backup and recovery operations must be identified.

These components include the files and other structures that constitute data for an Oracle data store and safeguard the data store against possible failures. Three basic components are required for the recovery of Oracle Database:

- Data files

- Redo Logs

- Control Files

##### 9.2.1.1 Data files

Oracle Database consists of one or more logical storage units called tablespaces. Each tablespace in Oracle Database consists of one or more files called data files, which are physical files located on or attached to the host operating system in which Oracle Database is running.

The data in a database is collectively stored in the data files that constitute each tablespace of the database. The simplest Oracle Database would have one tablespace, stored in one data file. Copies of the data files of a database are a critical part of any backup strategy. The sheer size of the data files is the main challenge from a VLDB backup and recovery perspective.

##### 9.2.1.2 Redo Logs

Redo logs record all changes made to a database's data files.

With a complete set of redo logs and an older copy of a data file, Oracle can reapply the changes recorded in the redo logs to re-create the database at any point between the backup time and the end of the last redo log. Each time data is changed in Oracle Database, that change is recorded in the online redo log first, before it is applied to the data files.

Oracle Database requires at least two online redo log groups. In each group, there is at least one online redo log member, an individual redo log file where the changes are recorded. At intervals, Oracle Database rotates through the online redo log groups, storing changes in the current online redo log while the groups not in use can be copied to an archive location, where they are called archived redo logs (or, collectively, the archived redo log). For high availability reasons, production systems should always use multiple online redo members per group, preferably on different storage systems. Preserving the archived redo log is a major part of your backup strategy, as it contains a record of all updates to data files. Backup strategies often involve copying the archived redo logs to disk or tape for longer-term storage.

##### 9.2.1.3 Control Files

The control file contains a crucial record of the physical structures of the database and their status.

Several types of information stored in the control file are related to backup and recovery:

- Database information required to recover from failures or to perform media recovery

- Database structure information, such as data file details

- Redo log details

- Archived log records

- A record of past RMAN backups

Oracle Database data file recovery process is in part guided by status information in the control file, such as the database checkpoints, current online redo log file, and the data file header checkpoints. Loss of the control file makes recovery from a data loss much more difficult. The control file should be backed up regularly, to preserve the latest database structural changes, and to simplify recovery.

#### 9.2.2 Backup Type

Backups are divided into physical backups and logical backups.

- Physical backups are backups of the physical files used in storing and recovering your database, such as data files, control files, and archived redo logs. Ultimately, every physical backup is a copy of files storing database information to some other location, whether on disk or offline storage, such as tape.

- Logical backups contain logical data (for example, tables or stored procedures) extracted from a database with Oracle Data Pump (export/import) utilities. The data is stored in a binary file that can be imported into Oracle Database.

Physical backups are the foundation of any backup and recovery strategy. Logical backups are a useful supplement to physical backups in many circumstances but are not sufficient protection against data loss without physical backups.

Reconstructing the contents of all or part of a database from a backup typically involves two phases: retrieving a copy of the data file from a backup, and reapplying changes to the file since the backup, from the archived and online redo logs, to bring the database to the desired recovery point in time. To restore a data file or control file from backup is to retrieve the file from the backup location on tape, disk, or other media, and make it available to Oracle Database. To recover a data file, is to take a restored copy of the data file and apply to it the changes recorded in the database's redo logs. To recover a whole database is to perform recovery on each of its data files.

#### 9.2.3 Backup Tools

Oracle Database provides several tools to manage backup and recovery of Oracle Databases.

Each tool gives you a choice of several basic methods for making backups. The methods include:

- Oracle Recovery Manager (RMAN)

  RMAN reduces the administration work associated with your backup strategy by maintaining an extensive record of metadata about all backups and needed recovery-related files. In restore and recovery operations, RMAN uses this information to eliminate the need for the user to identify needed files. RMAN is efficient, supporting file multiplexing and parallel streaming, and verifies blocks for physical and (optionally) logical corruptions, on backup and restore.

  Backup activity reports can be generated using `V$BACKUP` views.

- Oracle Data Pump

  Oracle Data Pump provides high speed, parallel, bulk data and metadata movement of Oracle Database contents. This utility makes logical backups by writing data from Oracle Database to operating system files. This data can later be imported into Oracle Database.

- User-Managed Backups

  The database is backed up manually by executing commands specific to your operating system.

##### 9.2.3.1 Oracle Recovery Manager (RMAN)

Oracle Recovery Manager (RMAN), a command-line is the Oracle-preferred method for efficiently backing up and recovering Oracle Database.

RMAN is designed to work intimately with the server, providing block-level corruption detection during backup and recovery. RMAN optimizes performance and space consumption during backup with file multiplexing and backup set compression, and integrates with leading tape and storage media products with the supplied Media Management Library (MML) API.

RMAN takes care of all underlying database procedures before and after backup or recovery, freeing dependency on operating system and SQL\*Plus scripts. It provides a common interface for backup tasks across different host operating systems, and offers features not available through user-managed methods, such as data file and tablespace-level backup and recovery, parallelization of backup and recovery data streams, incremental backups, automatic backup of the control file on database structural changes, backup retention policy, and detailed history of all backups.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for more information about RMAN

##### 9.2.3.2 Oracle Data Pump

Physical backups can be supplemented by using the Oracle Data Pump (export/import) utilities to make logical backups of data.

Logical backups store information about the schema objects created for a database. Oracle Data Pump loads data and metadata into a set of operating system files that can be imported on the same system or moved to another system and imported there.

The dump file set is made up of one or more disk files that contain table data, database object metadata, and control information. The files are written in a binary format. During an import operation, the Data Pump Import utility uses these files to locate each database object in the dump file set.

##### 9.2.3.3 User-Managed Backups

If you do not want to use Recovery Manager, you can use operating system commands, such as the UNIX `dd` or `tar` commands, to make backups.

To create a user-managed online backup, the database must manually be placed into hot backup mode. Hot backup mode causes additional write operations to the online log files, increasing their size.

Backup operations can also be automated by writing scripts. You can make a backup of the entire database immediately, or back up individual tablespaces, data files, control files, or archived logs. An entire database backup can be supplemented with backups of individual tablespaces, data files, control files, and archived logs.

Operating system commands or third-party backup software can perform database backups. Conversely, the third-party software must be used to restore the backups of the database.

### 9.3 Data Warehouse Backup and Recovery

Data warehouse recovery is similar to that of an OLTP system.

However, a data warehouse may not require all of the data to be recovered from a backup, or for a complete failure, restoring the entire database before user access can commence. An efficient and fast recovery of a data warehouse begins with a well-planned backup.

The next several sections help you to identify what data should be backed up and guide you to the method and tools that enable you to recover critical data in the shortest amount of time.

This section contains the following topics:

- Recovery Time Objective (RTO)

- Recovery Point Objective (RPO)

#### 9.3.1 Recovery Time Objective (RTO)

A Recovery Time Objective (RTO) is the time duration in which you want to be able to recover your data.

Your backup and recovery plan should be designed to meet RTOs your company chooses for its data warehouse. For example, you may determine that 5% of the data must be available within 12 hours, 50% of the data must be available after a complete loss of the database within 2 days, and the remainder of the data be available within 5 days. In this case you have two RTOs. Your total RTO is 7.5 days.

To determine what your RTO should be, you must first identify the impact of the data not being available. To establish an RTO, follow these four steps:

1.  Analyze and identify: Understand your recovery readiness, risk areas, and the business costs of unavailable data. In a data warehouse, you should identify critical data that must be recovered in the n days after an outage.

2.  Design: Transform the recovery requirements into backup and recovery strategies. This can be accomplished by organizing the data into logical relationships and criticality.

3.  Build and integrate: Deploy and integrate the solution into your environment to back up and recover your data. Document the backup and recovery plan.

4.  Manage and evolve: Test your recovery plans at regular intervals. Implement change management processes to refine and update the solution as your data, IT infrastructure, and business processes change.

#### 9.3.2 Recovery Point Objective (RPO)

A Recovery Point Objective, or RPO, is the maximum amount of data that can be lost before causing detrimental harm to the organization.

RPO indicates the data loss tolerance of a business process or an organization in general. This data loss is often measured in terms of time, for example, 5 hours or 2 days worth of data loss. A zero RPO means that no committed data should be lost when media loss occurs, while a 24 hour RPO can tolerate a day's worth of data loss.

This section contains the following topics:

- More Data Means a Longer Backup Window

- Divide and Conquer

##### 9.3.2.1 More Data Means a Longer Backup Window

The most obvious characteristic of the data warehouse is the size of the database.

This can be upward of 100's of terabytes. Hardware is the limiting factor to a fast backup and recovery. However, today's tape storage continues to evolve to accommodate the amount of data that must be offloaded to tape (for example, advent of Virtual Tape Libraries which use disks internally with the standard tape access interface). RMAN can fully use, in parallel, all available tape devices to maximize backup and recovery performance.

Essentially, the time required to back up a large database can be derived from the minimum throughput among: production disk, host bus adapter (HBA) and network to tape devices, and tape drive streaming specifications \* the number of tape drives. The host CPU can also be a limiting factor to overall backup performance, if RMAN backup encryption or compression is used. Backup and recovery windows can be adjusted to fit any business requirements, given adequate hardware resources.

##### 9.3.2.2 Divide and Conquer

In a data warehouse, there may be times when the database is not being fully used.

While this window of time may be several contiguous hours, it is not enough to back up the entire database. You may want to consider breaking up the database backup over several days. RMAN enables you to specify how long a given backup job is allowed to run. When using `BACKUP` `DURATION`, you can choose between running the backup to completion as quickly as possible and running it more slowly to minimize the load the backup may impose on your database.

In the following example, RMAN backs up all database files that have not been backed up in the last 7 days first, runs for 4 hours, and reads the blocks as fast as possible.

    BACKUP DATABASE NOT BACKED UP SINCE 'sysdate - 7'
      PARTIAL DURATION 4:00 MINIMIZE TIME;

Each time this RMAN command is run, it backs up the data files that have not been backed up in the last 7 days first. You do not need to manually specify the tablespaces or data files to be backed up each night. Over the course of several days, all of your database files are backed up.

While this is a simplistic approach to database backup, it is easy to implement and provides more flexibility in backing up large amounts of data. During recovery, RMAN may point you to multiple different storage devices to perform the restore operation. Consequently, your recovery time may be longer.

### 9.4 The Data Warehouse Recovery Methodology

Devising a backup and recovery strategy can be a complicated and challenging task.

When you have hundreds of terabytes of data that must be protected and recovered for a failure, the strategy can be very complex. This section contains several best practices that can be implemented to ease the administration of backup and recovery.

This section contains the following topics:

- Best Practice 1: Use ARCHIVELOG Mode

- Best Practice 2: Use RMAN

- Best Practice 3: Use Block Change Tracking

- Best Practice 4: Use RMAN Multisection Backups

- Best Practice 5: Leverage Read-Only Tablespaces

- Best Practice 6: Plan for NOLOGGING Operations in Your Backup/Recovery Strategy

- Best Practice 7: Not All Tablespaces Should Be Treated Equally

#### 9.4.1 Best Practice 1: Use ARCHIVELOG Mode

Archived redo logs are crucial for recovery when no data can be lost because they constitute a record of changes to the database.

Oracle Database can be run in either of two modes:

- `ARCHIVELOG`

  Oracle Database archives the filled online redo log files before reusing them in the cycle.

- `NOARCHIVELOG`

  Oracle Database does not archive the filled online redo log files before reusing them in the cycle.

Running the database in `ARCHIVELOG` mode has the following benefits:

- The database can be recovered from both instance and media failure.

- Backups can be performed while the database is open and available for use.

- Oracle Database supports multiplexed archive logs to avoid any possible single point of failure on the archive logs.

- More recovery options are available, such as the ability to perform tablespace point-in-time recovery (TSPITR).

- Archived redo logs can be transmitted and applied to the physical standby database, which is an exact replica of the primary database.

Running the database in `NOARCHIVELOG` mode has the following consequences:

- The database can be backed up only while it is closed after a clean shutdown.

- Typically, the only media recovery option is to restore the whole database to the point-in-time in which the full or incremental backups were made, which can result in the loss of recent transactions.

##### 9.4.1.1 Is Downtime Acceptable?

It is important to design a backup plan to minimize database interruptions.

Oracle Database backups can be made while the database is open or closed. Planned downtime of the database can be disruptive to operations, especially in global enterprises that support users in multiple time zones, up to 24-hours per day.

Depending on the business, some enterprises can afford downtime. If the overall business strategy requires little or no downtime, then the backup strategy should implement an online backup. The database never needs to be taken down for a backup. An online backup requires the database to be in `ARCHIVELOG` mode.

Given the size of a data warehouse (and consequently the amount of time to back up a data warehouse), it is generally not viable to make an offline backup of a data warehouse, which would be necessitated if one were using `NOARCHIVELOG` mode.

#### 9.4.2 Best Practice 2: Use RMAN

Many data warehouses, which were developed on earlier releases of Oracle Database, may not have integrated RMAN for backup and recovery.

However, just as there are many reasons to leverage `ARCHIVELOG` mode, there is a similarly compelling list of reasons to adopt RMAN. Consider the following:

1.  Trouble-free backup and recovery

2.  Corrupt block detection

3.  Archive log validation and management

4.  Block Media Recovery (BMR)

5.  Easily integrates with Media Managers

6.  Backup and restore optimization

7.  Backup and restore validation

8.  Downtime-free backups

9.  Incremental backups

10. Extensive reporting

#### 9.4.3 Best Practice 3: Use Block Change Tracking

Enabling block change tracking allows incremental backups to be completed faster, by reading and writing only the changed blocks since the last full or incremental backup.

For data warehouses, this can be extremely helpful if the database typically undergoes a low to medium percentage of changes.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for more information about block change tracking

#### 9.4.4 Best Practice 4: Use RMAN Multisection Backups

With the advent of big file tablespaces, data warehouses have the opportunity to consolidate a large number of data files into fewer, better managed data files.

For backing up very large data files, RMAN provides multisection backups as a way to parallelize the backup operation within the file itself, such that sections of a file are backed up in parallel, rather than backing up on a per-file basis.

For example, a one TB data file can be sectioned into ten 100 GB backup pieces, with each section backed up in parallel, rather than the entire one TB file backed up as one file. The overall backup time for large data files can be dramatically reduced.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for more information about configuring multisection backups

#### 9.4.5 Best Practice 5: Leverage Read-Only Tablespaces

An important issue facing a data warehouse is the sheer size of a typical data warehouse. Even with powerful backup hardware, backups may still take several hours.

One important consideration in improving backup performance is minimizing the amount of data to be backed up. Read-only tablespaces are the simplest mechanism to reduce the amount of data to be backed up in a data warehouse. Even with incremental backups, both backup and recovery are faster if tablespaces are set to read-only.

The advantage of a read-only tablespace is that data must be backed up only one time. If a data warehouse contains five years of historical data and the first four years of data can be made read-only, then theoretically the regular backup of the database would back up only 20% of the data. This can dramatically reduce the amount of time required to back up the data warehouse.

Most data warehouses store their data in tables that have been range-partitioned by time. In a typical data warehouse, data is generally active for a period ranging anywhere from 30 days to one year. During this period, the historical data can still be updated and changed (for example, a retailer may accept returns up to 30 days beyond the date of purchase, so that sales data records could change during this period). However, after data reaches a certain age, it is often known to be static.

By taking advantage of partitioning, users can make the static portions of their data read-only. Currently, Oracle supports read-only tablespaces rather than read-only partitions or tables. To take advantage of the read-only tablespaces and reduce the backup window, a strategy of storing constant data partitions in a read-only tablespace should be devised. Here are two strategies for implementing a rolling window:

1.  When the data in a partition matures to the point where it is entirely static, implement a regularly scheduled process to move the partition from the current read-write tablespace to a tablespace that can then be made read-only.

2.  Create a series of tablespaces, each containing a small number of partitions, and regularly modify a tablespace from read-write to read-only as the data in that tablespace ages.

One consideration is that backing up data is only half the recovery process. If you configure a tape system so that it can back up the read-write portions of a data warehouse in 4 hours, the corollary is that a tape system might take 20 hours to recover the database if a complete recovery is necessary when 80% of the database is read-only.

#### 9.4.6 Best Practice 6: Plan for NOLOGGING Operations in Your Backup/Recovery Strategy

In general, a high priority for a data warehouse is performance. Not only must the data warehouse provide good query performance for online users, but the data warehouse must also be efficient during the extract, transform, and load (ETL) process so that large amounts of data can be loaded in the shortest amount of time. One common optimization used by data warehouses is to execute bulk-data operations using the `NOLOGGING` mode.

The database operations that support `NOLOGGING` modes are direct-path load and insert operations, index creation, and table creation. When an operation runs in `NOLOGGING` mode, data is not written to the redo log (or more precisely, only a small set of metadata is written to the redo log). This mode is widely used within data warehouses and can improve the performance of bulk data operations by up to 50%.

However, the tradeoff is that a `NOLOGGING` operation cannot be recovered using conventional recovery mechanisms, because the necessary data to support the recovery was never written to the log file. Moreover, subsequent operations to the data upon which a `NOLOGGING` operation has occurred also cannot be recovered even if those operations were not using `NOLOGGING` mode. Because of the performance gains provided by `NOLOGGING` operations, it is generally recommended that data warehouses use `NOLOGGING` mode in their ETL process.

The presence of `NOLOGGING` operations must be taken into account when devising the backup and recovery strategy. When a database is relying on `NOLOGGING` operations, the conventional recovery strategy (of recovering from the latest tape backup and applying the archived log files) is no longer applicable because the log files are not able to recover the `NOLOGGING` operation.

The first principle to remember is, do not make a backup when a `NOLOGGING` operation is occurring. Oracle Database does not currently enforce this rule, so DBAs must schedule the backup jobs and the ETL jobs such that the `NOLOGGING` operations do not overlap with backup operations.

There are two approaches to backup and recovery in the presence of `NOLOGGING` operations: ETL or incremental backups. If you are not using `NOLOGGING` operations in your data warehouse, then you do not have to choose either option: you can recover your data warehouse using archived logs. However, the options may offer some performance benefits over an archive log-based approach for a recovery. You can also use flashback logs and guaranteed restore points to flashback your database to a previous point in time.

This section contains the following topics:

- Extract, Transform, and Load

- The Extract, Transform, and Load Strategy

- Incremental Backup

- The Incremental Approach

- Flashback Database and Guaranteed Restore Points

##### 9.4.6.1 Extract, Transform, and Load

The ETL process uses several Oracle features and a combination of methods to load (re-load) data into a data warehouse.

These features consist of:

- Transportable tablespaces

  Transportable tablespaces allow users to quickly move a tablespace across Oracle Databases. It is the most efficient way to move bulk data between databases. Oracle Database provides the ability to transport tablespaces across platforms. If the source platform and the target platform are of different endianness, then RMAN converts the tablespace being transported to the target format.

- SQL\*Loader

  SQL\*Loader loads data from external flat files into tables of Oracle Database. It has a powerful data parsing engine that puts little limitation on the format of the data in the data file.

- Data Pump (export/import)

  Oracle Data Pump enables high-speed movement of data and metadata from one database to another. This technology is the basis for the Oracle Data Pump Export and Data Pump Import utilities.

- External tables

  The external tables feature is a complement to existing SQL\*Loader functionality. It enables you to access data in external sources as if it were in a table in the database. External tables can also be used with the Data Pump driver to export data from a database, using `CREATE` `TABLE` `AS` `SELECT` `*` `FROM`, and then import data into Oracle Database.

##### 9.4.6.2 The Extract, Transform, and Load Strategy

One approach is to take regular database backups and also store the necessary data files to re-create the ETL process for that entire week.

In the event where a recovery is necessary, the data warehouse could be recovered from the most recent backup. Then, instead of rolling forward by applying the archived redo logs (as would be done in a conventional recovery scenario), the data warehouse could be rolled forward by rerunning the ETL processes. This paradigm assumes that the ETL processes can be easily replayed, which would typically involve storing a set of extract files for each ETL process.

A sample implementation of this approach is to make a backup of the data warehouse every weekend, and then store the necessary files to support the ETL process each night. At most, 7 days of ETL processing must be reapplied to recover a database. The data warehouse administrator can easily project the length of time to recover the data warehouse, based upon the recovery speeds from tape and performance data from previous ETL runs.

Essentially, the data warehouse administrator is gaining better performance in the ETL process with `NOLOGGING` operations, at a price of slightly more complex and a less automated recovery process. Many data warehouse administrators have found that this is a desirable trade-off.

One downside to this approach is that the burden is on the data warehouse administrator to track all of the relevant changes that have occurred in the data warehouse. This approach does not capture changes that fall outside of the ETL process. For example, in some data warehouses, users may create their own tables and data structures. Those changes are lost during a recovery.

This restriction must be conveyed to the end-users. Alternatively, one could also mandate that end-users create all private database objects in a separate tablespace, and during recovery, the DBA could recover this tablespace using conventional recovery while recovering the rest of the database using the approach of rerunning the ETL process.

##### 9.4.6.3 Incremental Backup

A more automated backup and recovery strategy in the presence of `NOLOGGING` operations uses RMAN's incremental backup capability.

Incremental backups provide the capability to back up only the changed blocks since the previous backup. Incremental backups of data files capture data changes on a block-by-block basis, rather than requiring the backup of all used blocks in a data file. The resulting backup sets are generally smaller and more efficient than full data file backups, unless every block in the data file is changed.

When you enable block change tracking, Oracle Database tracks the physical location of all database changes. RMAN automatically uses the change tracking file to determine which blocks must be read during an incremental backup. The block change tracking file is approximately 1/30000 of the total size of the database.

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for more information about block change tracking and how to enable it

##### 9.4.6.4 The Incremental Approach

A typical backup and recovery strategy using this approach is to back up the data warehouse every weekend, and then take incremental backups of the data warehouse every night following the completion of the ETL process.

Incremental backups, like conventional backups, must not be run concurrently with `NOLOGGING` operations. To recover the data warehouse, the database backup would be restored, and then each night's incremental backups would be reapplied.

Although the `NOLOGGING` operations were not captured in the archive logs, the data from the `NOLOGGING` operations is present in the incremental backups. Moreover, unlike the previous approach, this backup and recovery strategy can be managed using RMAN.

##### 9.4.6.5 Flashback Database and Guaranteed Restore Points

Flashback Database is a fast, continuous point-in-time recovery method to repair widespread logical errors.

Flashback Database relies on additional logging, called flashback logs, which are created in the fast recovery area and retained for a user-defined time interval according to the recovery needs. These logs track the original block images when they are updated.

When a Flashback Database operation is executed, just the block images corresponding to the changed data are restored and recovered, versus traditional data file restore where all blocks from the backup must be restored before recovery can start. Flashback logs are created proportionally to redo logs.

For very large and active databases, it may not be feasible to keep all needed flashback logs for continuous point-in-time recovery. However, there may be a requirement to create a specific point-in-time snapshot (for example, right before a nightly batch job) for logical errors during the batch run. For this scenario, guaranteed restore points can be created without enabling flashback logging.

When the guaranteed restore points are created, flashback logs are maintained just to satisfy Flashback Database to the guaranteed restore points and no other point in time, thus saving space. For example, guaranteed restore points can be created followed by a nologging batch job. As long as there are no previous nologging operations within the last hour of the creation time of the guaranteed restore points, Flashback Database to the guaranteed restore points undoes the nologging batch job. To flash back to a time after the nologging batch job finishes, then create the guaranteed restore points at least one hour away from the end of the batch job.

Estimating flashback log space for guaranteed restore points in this scenario depends on how much of the database changes over the number of days you intend to keep guaranteed restore points. For example, to keep guaranteed restore points for 2 days and you expect 100 GB of the database to change, then plan for 100 GB for the flashback logs. The 100 GB refers to the subset of the database changed after the guaranteed restore points are created and not the frequency of changes.

#### 9.4.7 Best Practice 7: Not All Tablespaces Should Be Treated Equally

Not all of the tablespaces in a data warehouse are equally significant from a backup and recovery perspective.

Database administrators can use this information to devise more efficient backup and recovery strategies when necessary. The basic granularity of backup and recovery is a tablespace, so different tablespaces can potentially have different backup and recovery strategies.

On the most basic level, temporary tablespaces never need to be backed up (a rule which RMAN enforces). Moreover, in some data warehouses, there may be tablespaces dedicated to scratch space for users to store temporary tables and incremental results. These tablespaces are not explicit temporary tablespaces but are essentially functioning as temporary tablespaces. Depending upon the business requirements, these tablespaces may not need to be backed up and restored; instead, for a loss of these tablespaces, the users would re-create their own data objects.

In many data warehouses, some data is more important than other data. For example, the sales data in a data warehouse may be crucial and in a recovery situation this data must be online as soon as possible. But, in the same data warehouse, a table storing clickstream data from the corporate website may be much less critical to businesses. The business may tolerate this data being offline for a few days or may even be able to accommodate the loss of several days of clickstream data if there is a loss of database files. In this scenario, the tablespaces containing sales data must be backed up often, while the tablespaces containing clickstream data need to be backed up only once every week or two weeks.

While the simplest backup and recovery scenario is to treat every tablespace in the database the same, Oracle Database provides the flexibility for a DBA to devise a backup and recovery scenario for each tablespace as needed.
