## Before You Begin

This 15-minute tutorial shows you how to create and load partitions in in-memory hybrid partitioned table.

### Background

Oracle Database 18c enables the population of data from external tables into the In-Memory column store (IM column store). This allows the population of data that is not stored in Oracle Database but in source data files. Nevertheless, the population must be completed manually by executing the `DBMS_INMEMORY.POPULATE` procedure.

In Oracle Database 19c, querying an in-memory enabled external table automatically initiates the population of the external data into the IM column store.

### What Do You Need?

- Oracle Database 19c installed
- A CDB and a PDB
- Tablespaces created in the PDB for internal partitions of the hybrid partitioned table
- Source data files for external partitions of the hybrid partitioned table: [`cent19.dat`](files/CENT19/cent19.dat) and ` `[`cent20.dat`](files/CENT20/cent20.dat). Download the .dat files to the labs directory created on your server in their respective subdirectories, `/home/oracle/labs/CENT19` and `/home/oracle/labs/CENT20`.
- The ` `[`create_inmem_hybrid_table.sql`](files/create_inmem_hybrid_table.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`.
- The ` `[`insert_select.sql`](files/insert_select.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`.

------------------------------------------------------------------------

## Configure the IM Column Store Size

1.  Set the IM column store size to 800M.

        sqlplus / AS SYSDBA

        ALTER SYSTEM SET inmemory_SIZE = 800M SCOPE=SPFILE;

2.  Restart the instance and open the database.

        SHUTDOWN IMMEDIATE

        STARTUP

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

------------------------------------------------------------------------

## Create the Tablespaces for the Internal Partitions

In this section, you create two tablespaces to store data of the internal partitions. One of the two tablespaces will be the default tablespace for internal partitions.

1.  Log in to the PDB as ` SYSTEM`.

        CONNECT system@PDB1
        Enter password: password

2.  Create the tablespaces ` TS1 ` and ` TS2 ` to store internal partitions of the hybrid partitioned table.

        CREATE TABLESPACE ts1 DATAFILE '/u02/app/oracle/oradata/ORCL/pdb1/ts1.dbf' SIZE 100M;

        CREATE TABLESPACE ts2 DATAFILE '/u02/app/oracle/oradata/ORCL/pdb1/ts2.dbf' SIZE 100M;

------------------------------------------------------------------------

## Create the Logical Directories for the External Partitions

In this section, you create the logical directories to store the source data files for external partitions.

1.  Create the logical directory ` CENT18` to store the source data file ` cent18.dat ` for the ` CENT18 ` external partition.

        CREATE DIRECTORY cent18 AS '/home/oracle/labs/CENT18';

2.  Create the logical directory ` CENT19` to store the source data file ` cent19.dat ` for the ` CENT19 ` external partition.

        CREATE DIRECTORY cent19 AS '/home/oracle/labs/CENT19';

3.  Create the logical directory ` CENT20` to store the source data file ` cent20.dat ` for the ` CENT20 ` external partition.

        CREATE DIRECTORY cent20 AS '/home/oracle/labs/CENT20';

------------------------------------------------------------------------

## Create the In-Memory Hybrid Partitioned Table

1.  Create the user that owns the in-memory hybrid partitioned table.

        CREATE USER hypt IDENTIFIED BY password;

2.  Grant the read and write privileges on the directories that store the source data files to the table owner.

        GRANT read, write ON DIRECTORY cent18 TO hypt;

        GRANT read, write ON DIRECTORY cent19 TO hypt;

        GRANT read, write ON DIRECTORY cent20 TO hypt;

3.  Grant the `CREATE SESSION`, `CREATE TABLE`, and `UNLIMITED TABLESPACE` privileges to the table owner.

        GRANT create session, create table, unlimited tablespace TO hypt;

4.  Execute the ` `[`create_inmem_hybrid_table.sql`](files/create_inmem_hybrid_table.sql) SQL script to create the `HYPT_INMEM_TAB` hybrid partitioned table with the following attributes:

    - The table is partitioned by range on the `TIME_ID` column.
    - The default tablespace for internal partitions is `TS1`.
    - The default tablespace for external partitions is `CENT20`.
    - The fields in the records of the external files are separated by comma ','.
    - The table is partitioned into five parts:
      - Three external partitions: `CENT18` is empty for the moment; `CENT19` has the `cent19.dat` file stored in a directory other than the default, `CENT19`; `CENT20` has the `cent20.dat` file stored in the default directory.
      - Two internal partitions: `Y2000` is stored in tablespace `TS2` and `PMAX` is stored in the default tablespace `TS1`.

    <!-- -->

        @/home/oracle/labs/create_inmem_hybrid_table.sql

5.  Find the partitions that are defined as in-memory segments.

        SELECT partition_name, inmemory, inmemory_compression FROM dba_tab_partitions
        WHERE  table_name = 'HYPT_INMEM_TAB';

        PARTITION_NAME INMEMORY INMEMORY_COMPRESS
        -------------- -------- -----------------
        CENT18         DISABLED
        CENT19         DISABLED
        CENT20         DISABLED
        PMAX           ENABLED  FOR QUERY HIGH
        Y2000          ENABLED  FOR QUERY HIGH

    Only internal partitions are defined as in-memory segments.

------------------------------------------------------------------------

## Insert Data Into the Partitions

1.  Execute the ` `[`insert_select.sql`](files/insert_select.sql) SQL script to insert rows into the different partitions of the table and query the table.

        @/home/oracle/labs/insert_select.sql

    The execution of the query on the table rows automatically populates the data into the IM column store.

2.  Verify which partitions are populated into the IM column store.

        SELECT segment_name, partition_name, tablespace_name, populate_status
        FROM   v$im_segments;

        SEGMENT_NAME   PARTITION_NAME TABLESPACE_NAME POPULATE_STAT
        -------------- -------------- --------------- -------------
        HYPT_INMEM_TAB PMAX           TS1                 COMPLETED
        HYPT_INMEM_TAB Y2000          TS2                 COMPLETED

    Only the partitions defined as in-memory segments are populated into the IM column store, and thus the internal partitions.

------------------------------------------------------------------------

## Determine How Data In Internal And External Partitions Is Accessed

1.  Display the execution plan for a query on all rows in the table.

        EXPLAIN PLAN FOR SELECT * FROM hypt.hypt_inmem_tab;

        SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY);

        PLAN_TABLE_OUTPUT
        ----------------------------------------------------------------------------------------------------------------------
        | Id  | Operation                               | Name           | Rows| Bytes| Cost (%CPU)| Time     | Pstart| Pstop|
        ----------------------------------------------------------------------------------------------------------------------
        |   0 | SELECT STATEMENT                        |                | 368K| 7917K|   778  (11)| 00:00:01 |       |      |
        |   1 |  PARTITION RANGE ALL                    |                | 368K| 7917K|   778  (11)| 00:00:01 |     1 |     5|
        |   2 |   TABLE ACCESS HYBRID PART INMEMORY FULL| HYPT_INMEM_TAB | 368K| 7917K|   778  (11)| 00:00:01 |     1 |     5|
        |   3 |    TABLE ACCESS INMEMORY FULL           | HYPT_INMEM_TAB |     |      |            |          |     1 |     5|
        -----------------------------------------------------------------------------------------------------------------------

2.  Display the execution plan for a query on the rows of one of the internal partition in the table.

        EXPLAIN PLAN FOR SELECT * FROM hypt.hypt_inmem_tab PARTITION (PMAX);

        SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY);
        PLAN_TABLE_OUTPUT
        ----------------------------------------------------------------------------------------------------------
        | Id  | Operation                   | Name           | Rows | Bytes| Cost (%CPU)| Time    | Pstart| Pstop|
        ----------------------------------------------------------------------------------------------------------
        |   0 | SELECT STATEMENT            |                | 82171| 1765K|    25  (56)| 00:00:01|       |      |
        |   1 |  PARTITION RANGE SINGLE     |                | 82171| 1765K|    25  (56)| 00:00:01|     5 |     5|
        |   2 |   TABLE ACCESS INMEMORY FULL| HYPT_INMEM_TAB | 82171| 1765K|    25  (56)| 00:00:01|     5 |     5|
        ----------------------------------------------------------------------------------------------------------

3.  Display the execution plan for a query on the rows of one of the external partition in the table.

        EXPLAIN PLAN FOR SELECT * FROM hypt.hypt_inmem_tab PARTITION (CENT19);

        SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY);

        PLAN_TABLE_OUTPUT
        ----------------------------------------------------------------------------------------------------------
        | Id  | Operation                   | Name           | Rows | Bytes| Cost (%CPU)| Time    | Pstart| Pstop|
        ----------------------------------------------------------------------------------------------------------
        |   0 | SELECT STATEMENT            |                |  8169|  175K|    31   (7)| 00:00:01|       |      |
        |   1 |  PARTITION RANGE SINGLE     |                |  8169|  175K|    31   (7)| 00:00:01|     2 |     2|
        |   2 |   EXTERNAL TABLE ACCESS FULL| HYPT_INMEM_TAB |  8169|  175K|    31   (7)| 00:00:01|     2 |     2|
        ----------------------------------------------------------------------------------------------------------

    According to the type of partition accessed and the number of partitions accessed at the same time, the operation shows either `EXTERNAL TABLE ACCESS FULL` (external partitions, not `INMEMORY`), `TABLE ACCESS INMEMORY FULL` (internal partitions, `INMEMORY`) or `HYBRID PART INMEMORY FULL` (both internal and external partitions).

------------------------------------------------------------------------

## Clean Up the Environment

1.  Drop the in-memory hybrid partitioned `HYPT.HYPT_INMEM_TAB` table.

        DROP TABLE hypt.hypt_inmem_tab PURGE;

2.  Quit the session.

        EXIT
