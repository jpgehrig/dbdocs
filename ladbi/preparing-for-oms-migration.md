## Preparing for the OMS Migration

Create and mount an Oracle Memory Speed (OMS) file system before you start the migration.

1.  Start the OMS daemon by running `$ORACLE_HOME/bin/oms_daemon`.
        #export ORACLE_SID="test"
        #$ORACLE_HOME/bin/oms_daemon
2.  Identify the DAX-capable XFS file system. Create an OMS file system on this DAX-capable PMEM storage using the `omsfscmds` utility.
3.  Mount the OMS file system you created in a unique database mount point directory such as `$ORACLE_BASE/oradata/$ORACLE_SID`.
4.  Shut down the instance.
5.  Enable the OMS ODM library on the database instance.
        $ cd $ORACLE_HOME/rdbms/lib
        $ make -f ins_rdbms.mk oms_on
6.  If Oracle Managed File (OMF) is in use, then set the DB_CREATE_FILE_DEST parameter to the OMS mount directory. DB_CREATE_FILE_DEST specifies the default location for the Oracle Managed data files. If an Oracle parameter file is in use, then set DB_CREATE_FILE_DEST in the parameter file.
    If you want to create an online redo log files on OMS, then set the db_create_online_log_dest_1 parameter to the OMS mount directory. This allows any new redo log file that you add to the database to be created on OMS storage.
7.  Start the database instance. If `spfile` is in use, then set the db_create_file_dest and db_create_online_log_dest_n in the SP file:
        SQL> alter system set db_create_file_dest=’OMS_MOUNT_DIR’ scope=both;
        SQL> alter system set db_create_online_log_dest_1=’OMS_MOUNT_DIR’ scope=both;

    Here, OMS_MOUNT_DIR is the directory path where you mounted the OMS file system.

**Related Topics**

- [About the OMS Daemon](about-oms-daemon.md)
- [Deploying Oracle Database with Oracle Memory Speed](deploying-database-oms.md)

**Parent topic:** [Migrating Oracle Database to Oracle Memory Speed](migrating-db-to-oms.md)
