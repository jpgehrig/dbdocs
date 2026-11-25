## Adding Redo Log Files to OMS

To achieve best redo performance, Oracle recommends that you add all members of a redo group to storage with similar characteristics. For Oracle Memory Speed (OMS) file system, adding all the members of the redo group to OMS provides efficient redo log write times.

To add new redo log file members in OMS and drop the existing non-OMS redo files, perform these steps:

1.  Identify all the existing redo group numbers configured by querying `v$log`.
        SQL> SELECT GROUP#, ARCHIVED, STATUS FROM V$LOG;
2.  Add a new log group with a new log member in the OMS location.
        SQL> ALTER DATABASE ADD LOGFILE 'OMS_MOUNT_PATH/oms_redolog_2.rdo';

    This statement adds a new log group number, which can be verified by querying `v$log`.
3.  If your database is set up with OMF and db_create_online_log_dest_1 parameter is already set to point to OMS, then add the log file without specifying a log file name.
        SQL> ALTER DATABASE ADD LOGFILE;

    Query `v$logfile` to identify the new group number and log file added to the database. The block size for new members located on OMS will be 4k.
4.  (Optional) If Oracle Managed Files (OMF) for redo log is enabled in your database, then change db_create_online_log_dest_1 to point to the OMS mount path specified in step 3.
        SQL> alter system set db_create_online_log_dest_1=’OMS_MOUNT_DIR’ scope=both;
5.  After you add the new redo log file in OMS, drop the non-OMS redo log file from the list in V\$LOG.
    **Note:**

    Before you drop the log file, ensure that the status is set to `INACTIVE`.

Example 8-6 Script for Moving Online Redo Logs

    SET SERVEROUTPUT ON;

    DECLARE

    CURSOR rlc IS

    SELECT GROUP# GRP, THREAD# THR, BYTES, 'NO' SRL
    FROM V$LOG
    UNION

    SELECT GROUP# GRP, THREAD# THR, BYTES, 'YES' SRL
    FROM V$STANDBY_LOG
    ORDER BY 1;

    stmt VARCHAR2(2048);

    BEGIN
    FOR rlcRec IN rlc LOOP

    IF (rlcRec.srl = 'YES') THEN
    stmt := 'ALTER DATABASE ADD STANDBY LOGFILE THREAD ' ||
    rlcRec.thr || ' SIZE ' || rlcRec.bytes;
    EXECUTE IMMEDIATE stmt;
    stmt := 'ALTER DATABASE DROP STANDBY LOGFILE GROUP ' || rlcRec.grp;
    EXECUTE IMMEDIATE stmt;
    ELSE
    stmt := 'ALTER DATABASE ADD LOGFILE THREAD ' ||
    rlcRec.thr || ' SIZE ' || rlcRec.bytes;
    EXECUTE IMMEDIATE stmt;

    BEGIN
    stmt := 'ALTER DATABASE DROP LOGFILE GROUP ' || rlcRec.grp;
    DBMS_OUTPUT.PUT_LINE(stmt);
    EXECUTE IMMEDIATE stmt;
    EXCEPTION
    WHEN OTHERS THEN
    EXECUTE IMMEDIATE 'ALTER SYSTEM SWITCH LOGFILE';
    EXECUTE IMMEDIATE 'ALTER SYSTEM CHECKPOINT GLOBAL';
    EXECUTE IMMEDIATE stmt;
    END;

    END IF;

    END LOOP;

    END;

    /

See [Oracle Database Administrator’s Guide](../admin/managing-the-redo-log.md) for more information about managing redo logs.

**Parent topic:** [Migrating Oracle Database to Oracle Memory Speed](migrating-db-to-oms.md)
