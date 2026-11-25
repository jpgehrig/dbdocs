## Before You Begin

This 15-minute tutorial shows you how to use Database Configuration Assistant (DBCA) to relocate a remote pluggable database (PDB) into a container database (CDB).

### Background

In Oracle Database 18c, relocating a remote PDB requires several commands to be executed.

### What Do You Need?

- Oracle Database 19c installed
- Two CDBs: ` ORCL `with ` PDB1 ` and ` CDB19`, both in archivelog mode. You can use the [dbca.sh](files/dbca.sh) shell script to create `CDB19`. Download the shell script to the labs directory created on your server `/home/oracle/labs`. Replace the password in the shell script by your own complex password. PDB relocation PDB and remote PDB clone operations with DBCA do not support Oracle Managed Files (OMF) enabled CDB. Verify that the PDB to be cloned does not use OMF.
- `HR ` schema installed in ` PDB1 ` as an example of application tables. If you want to use the ` HR.EMPLOYEES ` table, use the [hr.sql.](files/hr.sql) Download the SQL script to the labs directory created on your server ` /home/oracle/labs. ` In the script, update the password of the user connected to the database.

------------------------------------------------------------------------

## Prepare the PDB Before Relocation

1.  Log in to ` PDB1 ` in ` ORCL` as ` SYSTEM`.

        sqlplus system@PDB1
        Enter password: password

2.  Use the [hr.sql](files/hr.sql) script to create the `HR ` user and `EMPLOYEES` table in `PDB1`.

        @/home/oracle/labs/hr.sql

3.  Verify that `PDB1 ` contains the `HR.EMPLOYEES `table.

        SELECT count(*) FROM hr.employees;

          COUNT(*)
        ----------
               107

4.  Connect to `ORCL` as `SYS`.

        CONNECT sys@ORCL AS SYSDBA
        Enter password: password

5.  Create a common user in `ORCL`, used in the database link automatically created in `CDB19` to connect to `ORCL` during the relocation operation.

        CREATE USER c##remote_user IDENTIFIED BY password CONTAINER=ALL;

6.  Grant the privileges.

        GRANT create session, create pluggable database, sysoper TO c##remote_user CONTAINER=ALL;

7.  Quit the session.

        EXIT

------------------------------------------------------------------------

## Use DBCA to Relocate a Remote PDB

In this section, you use DBCA in silent mode to relocate` PDB1` from `ORCL` as `PDB1_IN_CDB19` in `CDB19`.

1.  If `CDB19` does not exist, launch the `/home/oracle/labs/dbca.sh` shell script. The script creates the CDB with no PDB. In the script, update the password of the user connected to the database.

        /home/oracle/labs/dbca.sh

2.  Launch DBCA in silent mode to relocate `PDB1` from `ORCL` as `PDB1_IN_CDB19` in `CDB19`.

        dbca -silent -relocatePDB -remotePDBName PDB1 -remoteDBConnString ORCL -sysDBAUserName SYSTEM -sysDBAPassword password  -remoteDBSYSDBAUserName SYS -remoteDBSYSDBAUserPassword password  -dbLinkUsername c##remote_user -dbLinkUserPassword  password  -sourceDB CDB19 -pdbName PDB1_IN_CDB19

        Prepare for db operation
        Prepare for db operation
        50% complete
        Create pluggable database using relocate PDB operation
        100% complete
        Pluggable database "PDB1_IN_CDB19" plugged successfully.
        Look at the log file "/u01/app/oracle/cfgtoollogs/dbca/CDB19/PDB1_IN_CDB19/CDB19.log" for further details.

------------------------------------------------------------------------

## Check that the PDB Is Relocated

1.  Connect to `CDB19` as `SYS`. Check that `PDB1` is relocated in `CDB19`.

        sqlplus sys@CDB19 AS SYSDBA
        Enter password: password

        SHOW PDBS

            CON_ID CON_NAME                       OPEN MODE  RESTRICTED
        ---------- ------------------------------ ---------- ----------
                 2 PDB$SEED                       READ ONLY  NO
                 3 PDB1_IN_CDB19                  READ WRITE NO

2.  Check that `PDB1_IN_CDB19 ` contains the `HR.EMPLOYEES ` table as in `PDB1`.

        CONNECT hr@PDB1_IN_CDB19
        Enter password: password

        SELECT count(*) FROM employees;

          COUNT(*)
        ----------
               107

3.  Connect to `ORCL` as `SYS`. Check that `PDB1` does not exist anymore in `ORCL`.

        CONNECT sys@ORCL AS SYSDBA
        Enter password: password

        SHOW PDBS

            CON_ID CON_NAME                       OPEN MODE  RESTRICTED
        ---------- ------------------------------ ---------- ----------
                 2 PDB$SEED                       READ ONLY  NO

------------------------------------------------------------------------

## Clean Up the PDB Relocated

1.  Connect to `CDB19` as `SYS`.

        CONNECT sys@CDB19 AS SYSDBA
        Enter password: password

2.  Close `PDB1_In_CDB19`.

        ALTER PLUGGABLE DATABASE pdb1_in_cdb19 CLOSE;

3.  Drop `PDB1_IN_CDB19`.

        DROP PLUGGABLE DATABASE pdb1_in_cdb19 INCLUDING DATAFILES;

4.  Quit the session.

        EXIT
