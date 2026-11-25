Complete these tasks to prepare the target Oracle Database for use.

1.  Verify if the data has imported to the target database.

    Run the following queries on the source and target databases to check if data was exported and imported completely without any errors.

    To view all users that exist in the database:
        SQL> SELECT count(*) FROM dba_users;
        SQL> SELECT username, account_status FROM dba_users;

    To view the total number of objects in the database:

        SQL> SELECT count(*) FROM dba_objects;
        SQL> SELECT count(*), owner FROM dba_objects group by owner;

    To view a list of all the tables owned by the current user:

        SQL> SELECT count(*) FROM user_tables;
        SQL> SELECT count(*), tablespace_name FROM user_tables group by tablespace_name;

    To view the exact size in MBytes occupied by the object at the tablespace:

        SELECT owner, segment_name, segment_type, partition_name, ROUND(bytes/(1024*1024),2) SIZE_MB, tablespace_name
        FROM DBA_SEGMENTS
        WHERE SEGMENT_TYPE IN ('TABLE', 'TABLE PARTITION', 'TABLE SUBPARTITION',
        'INDEX', 'INDEX PARTITION', 'INDEX SUBPARTITION', 'TEMPORARY', 'LOBINDEX', 'LOBSEGMENT', 'LOB PARTITION')
        --AND TABLESPACE_NAME LIKE 'COSTE%'
        --AND SEGMENT_NAME LIKE 'P2010201%'
        --AND partition_name LIKE 'P20100201%'
        --AND segment_type = 'TABLE'
        --AND OWNER = 'TARGET_POC'
        --AND ROUND(bytes/(1024*1024),2) > 1000
        ORDER BY bytes DESC;

    To view the total space occupied in MBytes:

        SELECT tablespace_name, owner, segment_type "Object Type",
               COUNT(owner) "Number of Objects",
               ROUND(SUM(bytes) / 1024 / 1024, 2) "Total Size in MB"
        FROM   sys.dba_segments
        WHERE  tablespace_name IN ('MPIS')
        GROUP BY tablespace_name, owner, segment_type
        ORDER BY tablespace_name, owner, segment_type;

    To view the size of the database:

        SQL> SELECT a.data_size+b.temp_size+c.redo_size+d.controlfile_size "total_size in MB" FROM ( select
            sum(bytes)/1024/1024 data_size
            FROM dba_data_files ) a,
            (select nvl(sum(bytes),0)/1024/1024 temp_size
            FROM dba_temp_files) b,
            (select sum(bytes)/1024/1024 redo_size
            FROM sys.v_$log) c,
            (select sum(BLOCK_SIZE*FILE_SIZE_BLKS)/1024/1024 controlfile_size from v$controlfile) d;

2.  Switch transported tablespaces to `READ WRITE` mode at destination.

        SQL> ALTER TABLESPACE tablespace name READ WRITE;

3.  Revert tablespaces to `READ WRITE` mode at source.

        SQL> ALTER TABLESPACE tablespace name READ WRITE;

4.  Redirect applications to destination database.

    Create and start appropriate database services and/or network connectivity on the new destination database.

5.  Clean up the staging directories.

    Remove unneeded files from the source and destination hosts.

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
