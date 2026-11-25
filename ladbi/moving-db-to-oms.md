## Moving the Entire Database to OMS

Use RMAN to move the entire database to Oracle Memory Speed (OMS) if the number of data files are large or if you want to move `root` PDB files.

To migrate your entire database:

1.  Backup your database.
2.  Restore the file on OMS and recover the database.

Before you start the database backup:

- If you have any read-only transportable tablespaces with the COMPATIBLE initialization parameter set to less than 11.0.0, then make any read-only transportable tablespaces read/write for RMAN backup to work on the tablespaces.

- If you have a physical standby database, then stop any running managed recovery:

      SQL> ALTER DATABASE RECOVER MANAGED STANDBY DATABASE CANCEL;

1.  Start the RMAN session and connect to the database that you want to migrate. Perform a `level 0` copy of the database in OMS storage.
        RUN
        {
                  ALLOCATE CHANNEL dev1 DEVICE TYPE DISK;
                  ALLOCATE CHANNEL dev2 DEVICE TYPE DISK;
                  ALLOCATE CHANNEL dev3 DEVICE TYPE DISK;
                  ALLOCATE CHANNEL dev4 DEVICE TYPE DISK;
                  BACKUP AS COPY
                       INCREMENTAL LEVEL 0
                       DATABASE
                       FORMAT 'oms_mount_path/%U'
                      TAG 'ORA_OMS_MIGRATION';
        }

    The format clause specifies oms_mount_path/%U, which corresponds to the OMS file system that you will use for storing the database.
2.  If you are not using an SPFILE, then create an SPFILE in the OMS storage using the current PFILE.
        SQL> CREATE SPFILE='oms_mount_path/spfilesid.ora' FROM PFILE='?/dbs/initsid.ora';
3.  Archive the current online redo logs and back up the server parameter file `SPFILE`.
        RMAN> SQL "ALTER SYSTEM ARCHIVE LOG CURRENT";
        RMAN> BACKUP AS BACKUPSET SPFILE;
        RMAN> SHUTDOWN IMMEDIATE;
4.  If the database uses change tracking or Flashback Database, then disable these features before you shut down the database instance.
        RMAN> SQL "ALTER DATABASE DISABLE BLOCK CHANGE TRACKING";
        RMAN> SQL "ALTER DATABASE FLASHBACK OFF";

    You have now created a full copy of the database and the instance is shut down.
5.  To start the database instance and switch to the RMAN copy in OMS storage, create a `SPFILE` in the OMS storage area.
        RMAN> STARTUP MOUNT;
        RMAN> RESTORE SPFILE TO 'oms_mount_path/spfilesid.ora';
        RMAN> SHUTDOWN IMMEDIATE;

    Where oms_mount_path is the mount path to the OMS storage and sid is the SID of the instance.
6.  Set the Oracle Managed Files (OMF) parameters to point to the OMS mount path.
        SQL> STARTUP FORCE NOMOUNT;
        SQL> ALTER SYSTEM SET DB_CREATE_FILE_DEST='oms_mount_path' SID='*';
        SQL> ALTER SYSTEM SET DB_RECOVERY_FILE_DEST='oms_mount_path' SID='*';
7.  Migrate the control files to OMS, set the control file location to the OMS path, and restore the control file from the original non-OMS location.
        SQL> STARTUP FORCE NOMOUNT;
        SQL> ALTER SYSTEM SET CONTROL_FILES='oms_mount_path' SCOPE=SPFILE SID='*';
8.  Restore the control file.
        RMAN> STARTUP FORCE NOMOUNT;
        RMAN> RESTORE CONTROLFILE FROM 'original_cf_name';
        RMAN> ALTER DATABASE MOUNT;

    In this example, original_cf_name is a control file name in the initialization parameter file before migration.
9.  Migrate the data files to the OMS copy using RMAN `SWITCH DATABASE`.
        SWITCH DATABASE TO COPY;
        RUN
        {
        ALLOCATE CHANNEL dev1 DEVICE TYPE DISK;
        ALLOCATE CHANNEL dev2 DEVICE TYPE DISK;
        ALLOCATE CHANNEL dev3 DEVICE TYPE DISK;
        ALLOCATE CHANNEL dev4 DEVICE TYPE DISK;
        RECOVER DATABASE;
        }
10. Enable change tracking or Flashback Database, if the database uses these features.
        SQL> ALTER DATABASE ENABLE BLOCK CHANGE TRACKING USING FILE 'oms_mount_path';
        SQL> ALTER DATABASE FLASHBACK ON;
11. Place the database in its normal operation mode to use OMS.
    - If the database is a primary database, then open it using:

          SQL> ALTER DATABASE OPEN;

    - If the database is a standby database, then resume managed recovery mode:

          SQL> ALTER DATABASE RECOVER MANAGED STANDBY DATABASE;
12. If you want to migrate any tempfiles to OMS, then drop the existing tempfiles and add a new temp file in the OMS mount path.
        SQL> ALTER DATABASE TEMPFILE 'tempfile_name' DROP;
        SQL> ALTER TABLESPACE temp_tbs_name ADD TEMPFILE;

    In this example, the name of the tempfile in the original storage is tempfile_name. The name of the temporary tablespace is temp_tbs_name.

To migrate online redo logs to the OMS location, see [Adding Redo Log Files to OMS](adding-redo-to-oms.md)

**Parent topic:** [Migrating Oracle Database to Oracle Memory Speed](migrating-db-to-oms.md)
