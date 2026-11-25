## Before You Begin

This 15-minute tutorial shows you how to create a hybrid partitioned table with both internal and external partitions and manage the internal and external partitions.

### Background

Oracle Database 12c allows partitions of a partitioned table to be created either as internal partitions in the database in Oracle data files or in external sources as external partitions.

Oracle Database 19c allows a partitioned table to hold both internal partitions and external partitions. These partitioned tables are called hybrid partitioned tables.

### What Do You Need?

- Oracle Database 19c installed
- A database, either non-CDB or CDB with a PDB
- Tablespaces created in the non-CDB or PDB for internal partitions of hybrid partitioned tables
- Source data files for external partitions of hybrid partitioned tables: ` `[`cent17.dat,`](files/CENT17/cent17.dat)` `[`cent19.dat,`](files/CENT19/cent19.dat) and ` `[`cent20.dat`](files/CENT20/cent20.dat). Download the .dat files to the labs directory created on your server in their respective subdirectories, `/home/oracle/labs/CENT17`, `/home/oracle/labs/CENT19`, and `/home/oracle/labs/CENT20`
- The ` `[`create_hybrid_table.sql`](files/create_hybrid_table.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`insert.sql`](files/insert.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`insert2.sql`](files/insert2.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`

------------------------------------------------------------------------

## Create the Tablespaces for the Internal Partitions

In this section, you create two tablespaces to store data of the internal partitions, one of the two tablespaces to be the default tablespace for internal partitions.

1.  Log in to the PDB as ` SYSTEM`.

        sqlplus system@PDB1
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

## Create the Hybrid Partitioned Table

1.  Create the user that owns the hybrid partitioned table.

        CREATE USER hypt IDENTIFIED BY password;

2.  Grant the read and write privileges on the directories that store the source data files to the table owner.

        GRANT read, write ON DIRECTORY cent18 TO hypt;

        GRANT read, write ON DIRECTORY cent19 TO hypt;

        GRANT read, write ON DIRECTORY cent20 TO hypt;

3.  Grant the `CREATE SESSION`, `CREATE TABLE` and `UNLIMITED TABLESPACE` privileges to the table owner.

        GRANT create session, create table, unlimited tablespace TO hypt;

4.  Execute the ` `[`create_hybrid_table.sql`](files/create_hybrid_table.sql) SQL script to create the `HYPT_TAB` hybrid partitioned table with the following attributes:

    - The table is partitioned by range on the `TIME_ID` column.
    - The default tablespace for internal partitions is `TS1`.
    - The default tablespace for external partitions is `CENT20`.
    - The fields in the records of the external files are separated by ','.
    - The table is partitioned into five parts:
      - Three external partitions: `CENT18` is empty for the moment; `CENT19` has the `cent19.dat` file stored in another directory than the default, `CENT19`; `CENT20` has the `cent20.dat` file stored in the default directory.
      - Two internal partitions: `Y2000` is stored in tablespace `TS2` and `PMAX` is stored in the default tablespace `TS1`.

    <!-- -->

        @/home/oracle/labs/create_hybrid_table.sql

------------------------------------------------------------------------

## Insert Data Into the Partitions

1.  Insert rows into the internal partitions of the table. Execute the ` `[`insert.sql`](files/insert.sql) SQL script.

        @/home/oracle/labs/insert.sql

2.  Insert a row for the date of 12 August 1997.

        INSERT INTO hypt.hypt_tab VALUES (41, to_date('12.08.1997', 'dd.mm.yyyy'));
        INSERT INTO hypt.hypt_tab
                         *
        ERROR at line 1:
        ORA-14466: Data in a read-only partition or subpartition cannot be modified.

    The data can be inserted into the external partition only via the external source data file.

3.  Insert the data for the date of 12 August 1997 into the appropriate external source data file.

        host echo "41,12-Aug-1997" >> /home/oracle/labs/CENT20/cent20.dat

4.  Verify that the row is readable from the appropriate external partition `CENT20`.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (cent20) ORDER BY 1;

    Read the result from the ` `[`result1`](files/result1.txt) text file.

5.  Append another record into the external source data file `CENT19`.

        host echo "42,12-Aug-1997" >> /home/oracle/labs/CENT19/cent19.dat

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (cent19) ORDER BY 1;

    Read the result from the ` `[`result2`](files/result2.txt) text file. Observe that the row is readable from the external partition `CENT19` although the row should be stored in another partition. There is no control on the `TIME_ID` of the records inserted as rows into the external partitions, as it is the case for rows inserted into internal partitions.

6.  Use an text editor to remove the record inserted into `/home/oracle/labs/CENT19/cent19.dat`.

7.  Query the rows of the five partitions.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (cent18) ORDER BY 1;
        no rows selected

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (cent19) ORDER BY 1;

    Read the result from the ` `[`result3`](files/result3.txt) text file.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (cent20) ORDER BY 1;

    Read the result from the ` `[`result1`](files/result1.txt) text file.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (y2000) ORDER BY 1;

    Read the result from the ` `[`result4`](files/result4.txt) text file.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.hypt_tab PARTITION (pmax) ORDER BY 1;

        HISTORY_EVENT TO_CHAR(TIME_ID,'DD-
        ------------- --------------------
                   29 12-AUG-2018
                   30 15-SEP-2017

------------------------------------------------------------------------

## List the Partitions of the Hybrid Partitioned Table

1.  Distinguish the partitioned tables from the hybrid partitioned tables. Verify the existence of the hybrid partitioned table in the `DBA_EXTERNAL_TABLES` view and its associated partitions from the `DBA_TAB_PARTITIONS` view.

        SELECT * FROM dba_external_tables WHERE owner = 'HYPT';

    Read the result from the ` `[`hypt_table`](files/hypt_table.txt) text file.

        SELECT partition_name, high_value FROM dba_tab_partitions
        WHERE  table_name = 'HYPT_TAB' ORDER BY 1;

    Read the result from the ` `[`partitions`](files/partitions.txt) text file.

------------------------------------------------------------------------

## Add and Remove External Partitions

In this section, you add an external partition to the internal partitioned table `HYPT.PART_TAB` for the 17th century. The external file ` `[`cent17.dat`](files/CENT17/cent17.dat) source data file storing historic events of the 17th century is stored in the directory `/home/oracle/labs/CENT17`.

1.  Drop the hybrid partitioned table.

        DROP TABLE hypt.hypt_tab;

2.  Create another partitioned table with internal partitions only.

        CREATE TABLE hypt.part_tab (history_event NUMBER , time_id DATE) TABLESPACE ts1
           PARTITION BY RANGE (time_id)
           (PARTITION cent18 VALUES LESS THAN (TO_DATE('01-Jan-1800','dd-MON-yyyy')) ,
            PARTITION cent19 VALUES LESS THAN (TO_DATE('01-Jan-1900','dd-MON-yyyy')) ,
            PARTITION cent20 VALUES LESS THAN (TO_DATE('01-Jan-2000','dd-MON-yyyy')) ,
            PARTITION y2000 VALUES LESS THAN  (TO_DATE('01-Jan-2001','dd-MON-yyyy'))
                      TABLESPACE ts2,
            PARTITION pmax VALUES LESS THAN (MAXVALUE));

3.  Execute the ` `[`insert2.sql`](files/insert2.sql) SQL script to insert rows into the internal partitions of the `PART_TAB` table.

        @/home/oracle/labs/insert2.sql

4.  Display the rows in the table.

        SELECT * FROM hypt.part_tab ORDER BY 1;

    Read the result from the ` `[`result5`](files/result5.txt) text file.

5.  Create the logical directory for the `/home/oracle/lab/CENT17` directory.

        CREATE DIRECTORY cent17 AS '/home/oracle/labs/CENT17';

6.  Grant the read and write privileges on the directory to HYPT.

        GRANT read, write ON DIRECTORY cent17 TO hypt;

7.  Define the external parameters for all external partitions that might be added to the `HYPT.PART_TAB ` table.

        ALTER TABLE hypt.part_tab
            ADD EXTERNAL PARTITION ATTRIBUTES
               (TYPE ORACLE_LOADER
                DEFAULT DIRECTORY cent17
                ACCESS PARAMETERS
                 (FIELDS TERMINATED BY ','
                  (history_event , time_id DATE 'dd-MON-yyyy'))
                  REJECT LIMIT UNLIMITED
                 );

8.  Split the first partition to a partition limit that will be the high limit of the partition added.

        ALTER TABLE hypt.part_tab
               SPLIT PARTITION cent18 AT (TO_DATE('01-Jan-1700','dd-MON-yyyy'))
               INTO (PARTITION cent17 EXTERNAL LOCATION ('cent17.dat'),
                     PARTITION cent18);

9.  Read the rows of the external partition.

        SELECT history_event, TO_CHAR(time_id, 'dd-MON-yyyy')
        FROM   hypt.part_tab PARTITION (cent17) ORDER BY 1;

    Read the result from the ` `[`result6`](files/result6.txt) text file.

10. The partition storing 17th century historic events is no longer required. Remove the external parameters for the hybrid partitioned that was added to the `HYPT.PART_TAB` table.

        ALTER TABLE hypt.part_tab DROP EXTERNAL PARTITION ATTRIBUTES();
        ALTER TABLE hypt.part_tab DROP EXTERNAL PARTITION ATTRIBUTES()
        *
        ERROR at line 1:
        ORA-14354: operation not supported for a hybrid-partitioned table

    External partitions must be dropped first before you can remove external attributes at the table level.

11. Drop the external partition from the `HYPT.PART_TAB` table. Because there is one external partition left, the attributes for the external partitions cannot be removed from the hybrid partitioned table.

        ALTER TABLE hypt.part_tab DROP PARTITION cent17;

12. Remove the external parameters for the hybrid partitioned `HYPT.PART_TAB` table.

        ALTER TABLE hypt.part_tab DROP EXTERNAL PARTITION ATTRIBUTES();

------------------------------------------------------------------------

## Clean Up the Environment

1.  Drop the hybrid partitioned `HYPT.PART_TAB` table.

        DROP TABLE hypt.part_tab PURGE;

2.  Quit the session.

        EXIT
