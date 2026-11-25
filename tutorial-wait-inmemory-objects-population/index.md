## Before You Begin

This 15-minute tutorial shows you how to allow applications to take better advantage of the complete population of the tables into the In-Memory Column Store (IMCS).

### Background

Before Oracle Database 19c, applications could access in-memory tables that might not be fully populated into the IMCS. The methods used to ensure that the in-memory tables are populated into the IMCS are either querying the tables or executing the `DBMS_INMEMORY.POPULATE` procedure.

Oracle Database 19c introduces the `DBMS_INMEMORY_ADMIN.POPULATE_WAIT` function. Executing this function returns a value that indicates the status of the eligible object’s population.

The possible values are:

- - 0: All in-memory segments are fully populated.
  - 1: Not all in-memory segments are fully populated due to IMCS lack of space.
  - 2: There are no segments to populate.
  - 3: The IMCS size is configured to 0.

You can write a wrapper package that invokes the function at startup. Based on the value returned, the package can start the application’s services, send some messages to the application tier, or even open the database if it was opened in restricted mode.

### What Do You Need?

- Oracle Database 19c installed
- A database, either non-CDB or CDB with a PDB
- The ` `[`im_tables.sh`](files/im_tables.sh) shell script. Download the shell script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`inmemory_size.sql`](files/inmemory_size.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`create_im_tables.sql`](files/create_im_tables.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`load_im_tables.sql`](files/load_im_tables.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`create_pdb1.sql`](files/create_pdb1.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`create_oe_user.sql`](files/create_oe_user.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`alter_oe.sql`](files/alter_oe.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`startup.sql`](files/startup.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`shutdown.sql`](files/shutdown.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`
- The ` `[`control_customer.ctl`](files/control_customer.ctl), ` `[`control_date.ctl`](files/control_date.ctl), ` `[`control_lineorder.ctl`](files/control_lineorder.ctl), ` `[`control_lineorder2.ctl`](files/control_lineorder2.ctl), ` `[`control_part.ctl`](files/control_part.ctl), and ` `[`control_supplier.ctl`](files/control_supplier.ctl) SQL\*Loader control files. Download the control files to the labs directory created on your server `/home/oracle/labs`
- The ` `[`customer.tbl`](files/customer.tbl), ` `[`date.tbl`](files/date.tbl), ` `[`lineorder.tbl`](files/lineorder.tbl), ` `[`lineorder2.tbl`](files/lineorder2.tbl), ` `[`part.tbl`](files/part.tbl), and ` `[`supplier.tbl`](files/supplier.tbl) SQL\*Loader data files. Download the data files to the labs directory created on your server `/home/oracle/labs`

------------------------------------------------------------------------

## Configure the IMCS And Create The In-Memory Tables

1.  Execute the `/home/oracle/labs/im_tables.sh` shell script to set the IMCS size to 800 MB and to create the in-memory tables, `OE.CUSTOMER`, `OE.LINEORDER`, `OE.DATE_DIM`, `OE.SUPPLIER`, and `OE.PART`. Update the users and keystore passwords in the shell and SQL scripts if necessary.

        /home/oracle/labs/im_tables.sh

2.  Verify that the IMCS is set to 800 MB.

        sqlplus / AS SYSDBA

        SHOW PARAMETER INMEMORY_SIZE
        NAME                        TYPE        VALUE
        --------------------------- ----------- ---------------------
        inmemory_size               big integer 800M

3.  Display the population status of the in-memory tables.

        SELECT segment_name, bytes, inmemory_size, bytes_not_populated, populate_status
        FROM   v$im_segments;
         2
        no rows selected

    In-memory tables are not populated into the IMCS because the on-demand population has not been requested.

------------------------------------------------------------------------

## Wait For In-Memory Segments To Be Populated

1.  In another session, session2, log in as `SYSTEM` in `PDB1`. Execute the function to get information about the status of the population of in-memory tables at the percentage of 100.

        sqlplus system@PDB1
        Enter password: password

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT(PRIORITY=>'NONE', PERCENTAGE=>100, TIMEOUT => 180) POP_STATUS
        FROM   dual;
         2
        POP_STATUS
        ----------
                 1

    After some time, the code returned from the function is 1, which means that the in-memory objects are not fully populated into the IMCS because of the lack of space in the in-memory column store.

2.  Quit session2.

        EXIT

3.  Verify this assumption in session1.

        CONNECT system@PDB1
        Enter password: password

        SELECT segment_name, bytes, inmemory_size, bytes_not_populated, populate_status
        FROM   v$im_segments;

    Read the result from the ` `[`result1`](files/result1.txt) text file.

4.  In session1, increase the IMCS size to 1 GB and the `SGA_TARGET` to 1.5 GB.

        CONNECT / AS SYSDBA

        ALTER SYSTEM SET inmemory_size=1G SCOPE=SPFILE;

        ALTER SYSTEM SET sga_target=1500M SCOPE=SPFILE;

5.  Restart the instance and database.

        SHUTDOWN IMMEDIATE

        STARTUP

6.  If necessary, open the CDB root keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password CONTAINER=ALL;

7.  Open the pluggable database.

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

8.  In session2, reconnect as `SYS`. If necessary, open the PDB keystore.

        sqlplus sys@PDB1 AS SYSDBA
        Enter password: password

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password;

9.  Execute the function that waits until in-memory tables are populated into the IMCS to the specified percentage of 100.

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT('NONE', 100, 180) POP_STATUS FROM dual;

        POP_STATUS
        ----------
                 0

    The query does not give any result until the population of the segments is 100% complete. When the population is complete, the return code is 0. The code returned means that the all in-memory objects are fully populated into the IMCS. You can therefore allow your application to query the tables, because you know that the tables queried are fully populated into the IMCS. A wrapper package invoking the function at instance startup would be beneficial.

10. Observe the population progress in session1.

        SELECT segment_name, bytes, inmemory_size, bytes_not_populated, populate_status
        FROM   v$im_segments;

    Read the result from the ` `[`result2`](files/result2.txt) text file.

------------------------------------------------------------------------

## Wait For In-Memory Segments To Be Populated With Other Return Codes

1.  In session2, execute the `/home/oracle/labs/alter_oe.sql` SQL script that modifies the in-memory attribute of the `OE` tables.

        @/home/oracle/labs/alter_oe.sql

2.  Quit session2.

        EXIT

3.  In session1, restart `PDB1` so that `OE` tables are no longer populated into the IMCS.

        ALTER PLUGGABLE DATABASE pdb1 CLOSE;

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

4.  In session2, reconnect as `SYS`, and if necessary, open the PDB keystore.

        sqlplus sys@PDB1 AS SYSDBA
        Enter password: password

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password;

    Then execute the function that waits until in-memory tables are populated into the IMCS to the specified percentage of 100 and a timeout set to one minute.

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT('NONE', 100, 60) POP_STATUS FROM dual;

        POP_STATUS
        ----------
                 2

5.  Observe the population progress in session1.

        SELECT segment_name, bytes, inmemory_size, bytes_not_populated, populate_status
        FROM   v$im_segments;
         2
        no rows selected

    The code returned from the function is 2, which means that there are no in-memory objects populated yet. This is the normal behavior because the script applied the `NO INMEMORY` attribute to the tables.

------------------------------------------------------------------------

## Display Meaningful Messages Returned By The Function

You do not necessarily know the different return codes meaning. You can retrieve more meaningful messages from the function.

1.  In session1, execute the function after setting the output to `ON`.

        SET SERVEROUTPUT ON

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT('NONE', 100, 60) POP_STATUS FROM dual;

    Read the result from the ` `[`result3`](files/result3.txt) text file. The message is more meaningful than the return code error.

2.  In session2, update the priority `NONE` to `HIGH` for two of the in-memory tables.

        ALTER TABLE oe.lineorder INMEMORY PRIORITY HIGH;

        ALTER TABLE oe.date_dim INMEMORY PRIORITY HIGH;

3.  Quit session2.

        EXIT

4.  In session1, restart `PDB1`.

        ALTER PLUGGABLE DATABASE pdb1 CLOSE;

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

5.  In session2, reconnect as `SYS` and if necessary, open the PDB keystore.

        sqlplus sys@PDB1 AS SYSDBA
        Enter password: password

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password;

    Then execute the function that waits until in-memory tables are populated into the IMCS to the specified percentage of 100 and a timeout set to one minute.

        SET SERVEROUTPUT ON

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT('HIGH', 100, 60) POP_STATUS FROM dual;

    Read the result from the ` `[`result4`](files/result4.txt) text file. The message is more meaningful than the return code error.

6.  Quit session2.

        EXIT

------------------------------------------------------------------------

## Clean Up The Environment

1.  In session1, reset the IMCS size to 0.

        ALTER SYSTEM SET inmemory_size=0 SCOPE=SPFILE;

2.  Restart the database instance.

        SHUTDOWN

        STARTUP

3.  If necessary, open the CDB root keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password CONTAINER=ALL;

4.  Open `PDB1`.

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

5.  Verify the return status of the function after the cleanup completed.

        SET SERVEROUTPUT ON

        SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT('HIGH', 100, 60) POP_STATUS FROM dual;

        POP_STATUS
        ----------
                 3

        POPULATE ERROR, INMEMORY_SIZE=0

    The message is more meaningful than the return code error 3.

6.  Connect to `PDB1` as `SYS`, and if necessary, open the PDB keystore.

        CONNECT sys@PDB1 AS SYSDBA
        Enter password: password

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password;

7.  Drop the `OE` schema.

        DROP USER oe CASCADE;

8.  Quit session1.

        EXIT

------------------------------------------------------------------------
