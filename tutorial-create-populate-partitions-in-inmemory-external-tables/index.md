## Before You Begin

This 15-minute tutorial shows you how to create and populate in-memory external tables.

### Background

Oracle Database 18c enables the population of data from external tables into the In-Memory column store (IM column store). This allows the population of data that is not stored in Oracle Database but in source data files. Nevertheless, the population must be completed manually by executing the `DBMS_INMEMORY.POPULATE` procedure.

In Oracle Database 19c, querying an in-memory enabled external table automatically initiates the population of the external data into the IM column store.

### What Do You Need?

- Oracle Database 19c installed
- A CDB and a PDB
- The source data file for the external table:  ` `[`cent20.dat`](files/CENT20/cent20.dat). Download the .dat file to the labs directory created on your server in its associated subdirectory, `/home/oracle/labs/CENT20`

------------------------------------------------------------------------

## Configure the IM Column Store Size

1.  Log in to the CDB root as `SYS`.

        sqlplus / AS SYSDBA

        ALTER SYSTEM SET inmemory_SIZE = 800M SCOPE=SPFILE;

2.  Restart the instance and open the database.

        SHUTDOWN IMMEDIATE

        STARTUP

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

## Create the Logical Directories for the External Source Files

In this section, you create the logical directory to store the source data files for external data files of the external table.

1.  Log in to the PDB as ` SYSTEM`.

        CONNECT system@PDB1
        Enter password: password

2.  Create the logical directory ` CENT20` to store the source data file ` cent20.dat ` for the ` CENT20 ` external source data file.

        CREATE DIRECTORY cent20 AS '/home/oracle/labs/CENT20';

------------------------------------------------------------------------

## Create the In-Memory External Table

1.  Create the user that owns the in-memory hybrid partitioned table.

        CREATE USER hypt IDENTIFIED BY password;

2.  Grant the read and write privileges on the directory that stores the source data file, to the table owner.

        GRANT read, write ON DIRECTORY cent20 TO hypt;

3.  Grant the `CREATE SESSION`, `CREATE TABLE`, and `UNLIMITED TABLESPACE` privileges to the table owner.

        GRANT create session, create table, unlimited tablespace TO hypt;

4.  Create the in-memory external table `INMEM_EXT_TAB` with the following attributes:

    - The table is partitioned by range on the `TIME_ID` column.
    - The default tablespace for external source data files is `CENT20`.
    - The fields in the records of the external files are separated by comma ','.
    - The in-memory compression is `FOR CAPACITY HIGH`.

    <!-- -->

        CREATE TABLE hypt.inmem_ext_tab (history_event NUMBER, time_id DATE)
           ORGANIZATION EXTERNAL
              (TYPE ORACLE_LOADER DEFAULT DIRECTORY cent20
               ACCESS PARAMETERS  (FIELDS TERMINATED BY ',')
               LOCATION ('cent20.dat'))
           INMEMORY MEMCOMPRESS FOR CAPACITY HIGH;

5.  Display the in-memory attributes of the external table.

        SELECT * FROM dba_external_tables WHERE owner='HYPT';

    Read the result from the ` `[`table_attributes`](files/table_attributes.txt) text file.

------------------------------------------------------------------------

## Query the In-Memory External Table

1.  Query the table. Queries of in-memory external tables must have the `QUERY_REWRITE_INTEGRITY` initialization parameter set to `stale_tolerated`.

        ALTER SESSION SET query_rewrite_integrity=stale_tolerated;

        SELECT * FROM hypt.inmem_ext_tab ORDER BY 1;

    Read the result from the ` `[`result1`](files/result1.txt) text file.

2.  Verify that the data is populated into the IM column store.

        SELECT segment_name, tablespace_name, populate_status
        FROM   v$im_segments;

        SEGMENT_NAME   TABLESPACE_NAME          POPULATE_STAT
        -------------- ------------------------ -------------
        INMEM_EXT_TAB  SYSTEM                   COMPLETED

    Querying the in-memory external table initiates the population into the IM column store in the same way that it does for an internal table. Executing the `DBMS_INMEMORY.POPULATE` procedure is not required.

------------------------------------------------------------------------

## Find How Data In In-Memory External Table Is Accessed

1.  Display the execution plan for a query on the in-memory external table with a degree of parallelism of 2.

        EXPLAIN PLAN FOR SELECT /*+ PARALLEL(2) */ * FROM hypt.inmem_ext_tab;

        SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY);

    Read the result from the ` `[`result2`](files/result2.txt) text file. The `EXTERNAL TABLE ACCESS INMEMORY FULL` operation shows that the external data was accessed from the IM column store after having been populated automatically during the query.

------------------------------------------------------------------------

## Clean Up the Environment

1.  Drop the external table `HYPT.INMEM_EXT_TAB`.

        DROP TABLE hypt.inmem_ext_tab PURGE;

2.  Quit the session.

        EXIT
