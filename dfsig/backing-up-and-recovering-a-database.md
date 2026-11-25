This chapter supplements the generic Oracle Database documentation set with information about backup and recovery. It includes the following topics:

- Backing Up an Oracle Database

- Restoring an Oracle Database

- About Using the Recovery Manager

Refer to the following Oracle manuals for detailed information about database backup and recovery:

- [Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md)

- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

- [Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md)

You can choose among many methods and Oracle tools for backup and recovery. You may use the Import and Export Utilities for logical backup and recovery. For physical backup and recovery you may use Recovery Manager (RMAN) or operating system utilities.

This chapter describes some BS2000 specific issues if you apply user-managed backup and recovery with SQL\*Plus and BS2000 utilities.

### 8.1 Backing Up an Oracle Database

You can use one of the following methods to back up an Oracle Database:

- Using BS2000 Utilities to Back Up an Oracle Database

- Performing Online Backup

#### 8.1.1 Using BS2000 Utilities to Back Up an Oracle Database

You can back up an Oracle database using BS2000 operating system utilities (for example, `ARCHIVE` or the `/COPY-FILE` command).

Use the following steps to back up an Oracle database:

1.  While the database is running, collect the names of all the files, which make up the Oracle database. You can determine the names of the log and database files by entering the following commands:
        /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
        * /NOLOG
        SQL> CONNECT / AS SYSDBA
        SQL> SELECT * FROM V$DATAFILE;
        SQL> SELECT * FROM V$LOGFILE;
2.  To ensure that all Oracle database files are synchronized at the time of the backup, shut down Oracle database using SQL\*Plus.
3.  Back up all the database files and log files using the BS2000 `ARCHIVE` utility or the BS2000 `/COPY-FILE` command. You should always back up all the files at the same time.
4.  Restart Oracle Database using SQL\*Plus.

#### 8.1.2 Performing Online Backup

You can perform an online backup of the database or individual tablespaces by using either:

- The BS2000 `ARCHIVE` utility together with Oracle Database `INSTALL.C.OPNBACK` utility.

- The BS2000 `PERCON` utility.

The `ARCHIVE` method is faster, and is described in this section.

Before you can perform an online (hot) backup of individual tablespaces, you must ensure that the `ARCHIVE` utility can back up open files.

The following BS2000 command ensures that `ARCHIVE` can back up open files:

    /START-EXECUTABLE $ORACINST.INSTALL.C.OPNBACK
    *filename

The `INSTALL.C.OPNBACK` utility calls the BS2000 macro `CATAL`, which sets the `OPNBACK` file attribute to `YES`. For the `CATAL` macro to work, the database must be shut down or the tablespace in question must be offline. You enter this command once for each file. For example, before adding it to a tablespace, not on the occasion of each backup.

You must never back up database files online without first setting the tablespace to backup mode. If you do not follow this step, then the resulting backup files are inconsistent. To perform an online backup of individual tablespaces or data files, use the following procedure:

1.  Enter the following command:
        SQL> ALTER TABLESPACE name BEGIN BACKUP;
2.  Back up the files of the tablespace using the BS2000 `ARCHIVE` utility. Ensure that the `OLS` parameter of `ARCHIVE` is set to `YES`.
3.  Enter the following command:
        SQL> ALTER TABLESPACE name END BACKUP;

**Note:**

The preceding SQL\*Plus commands operate on tablespaces, while the `ARCHIVE` utility operates on data files.

### 8.2 Restoring an Oracle Database

An Oracle Database can be restored offline from backups, using the following steps:

1.  Copy all the database files and the log files from the backup. You may use the BS2000 `ARCHIVE` utility or the BS2000 `/COPY-FILE` command. Files must be restored with their original name.
    To determine the name of all data files, query the `V$DATAFILE` table while the Oracle database is running. Enter the following command when the SQL prompt is displayed:

        SQL> SELECT FILE#,NAME FROM V$DATAFILE;

    The following is an example of the result that is displayed:

        FILE# NAME
        ------  -------------------------
        1      :pvs:$dbauserid.sid.DBS.DATABASE1.DBF
        2      :pvs:$dbauserid.sid.DBS.DATABASE2.DBF

        2 ROWS SELECTED.

    You can determine the name of the log files in a similar way:

        SQL> SELECT GROUP#,MEMBER FROM V$LOGFILE;

    The following is an example of the result that is displayed:

        GROUP#    MEMBER
        ------  -------------------------
        1      :pvs:$dbauserid.sid.DBS.LOG1.DBF
        2      :pvs:$dbauserid.sid.DBS.LOG2.DBF

        2 ROWS SELECTED.
2.  Under the DBA user ID, ensure that the `ORA``SID` environment variable identifies the Oracle database, which is to be restored.
3.  Use the SQL\*Plus `STARTUP` command to start the Oracle database.

### 8.3 About Using the Recovery Manager

In addition to the BS2000 utilities, you can also use Oracle Recovery Manager (RMAN) to back up and restore a database.

**See Also:**

"[Recovery Manager on BS2000](oracle-database-utilities.md)" for more information
