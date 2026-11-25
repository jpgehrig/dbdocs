## Before You Begin

This 5-minute tutorial shows you how to import tables with encrypted columns in a database that does not support the encrypted column feature as is the case in the Oracle Public Cloud environment.

### Background

In the Oracle Public Cloud environment, data is encrypted by default using Transparent Data Encryption (TDE) and the encrypted tablespace feature, but not the encrypted column feature. If an exported table holds encrypted columns, there must be a method to import the table and suppress the encryption clause associated with the table creation during the import operation.

### What Do You Need?

- Oracle Database 19c installed
- A database, either non-CDB or CDB with a PDB
- The [`tab.dmp`](files/tab.dmp) dump file. Download the dump file to the labs directory created on your server `/home/oracle/labs`

------------------------------------------------------------------------

## Display The Table Column ENCRYPT Attribute Before Import

Before importing the table without its `ENCRYPT` column attribute, verify that the table exported in the `/home/oracle/labs/tab.dmp` dump file has an encrypted column.

1.  Log in to a test non-CDB and create the directory to point to the location of the dump file.

        sqlplus system
        Enter password: password

        CREATE DIRECTORY dp AS '/home/oracle/labs';

        EXIT

2.  Generate the SQL file from the Data Pump export `/home/oracle/labs/tab.dmp` dump file by simulating an import into the non-CDB.

        impdp system DIRECTORY=dp DUMPFILE=tab.dmp SQLFILE=tabenc1 LOGFILE=enc.log
        Enter password: password

3.  Read the resulting SQL file.

        cat /home/oracle/labs/tabenc1.sql

        ...
        CREATE TABLE "TEST"."TABENC"
        ("C1" NUMBER, "LABEL" VARCHAR2(50 BYTE) ENCRYPT USING 'AES192' 'SHA-1')
         SEGMENT CREATION IMMEDIATE  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255
         NOCOMPRESS LOGGING
          STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
          PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
          BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
          TABLESPACE "SYSTEM" ;

    The `CREATE TABLE` command displays the `ENCRYPT` attribute of the `LABEL` column.

------------------------------------------------------------------------

## Import The Table Without The ENCRYPT Attribute

1.  Generate the SQL file from the Data Pump export `/home/oracle/labs/tab.dmp` dump file by simulating an import into the non-CDB omitting the `ENCRYPT` attribute of the `LABEL` column of the `TEST.TABENC` table into an encrypted tablespace such as `TEST`.

        impdp system DIRECTORY=dp DUMPFILE=tab.dmp SQLFILE=tabenc2 TRANSFORM=OMIT_ENCRYPTION_CLAUSE:Y REMAP_TABLESPACE=system:test LOGFILE=enc2.log
        Enter password: password

2.  Read the resulting SQL file.

        cat /home/oracle/labs/tabenc2.sql

        ...
        CREATE TABLE "TEST"."TABENC"
        ("C1" NUMBER, "LABEL" VARCHAR2(50 BYTE))
         SEGMENT CREATION IMMEDIATE  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255
         NOCOMPRESS LOGGING
          STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
          PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
          BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
          TABLESPACE "TEST" ;

    The `ENCRYPT` attribute of the `LABEL` column in the `TEST.TABENC` table is not set.

------------------------------------------------------------------------

## Clean Up the Environment

1.  Remove the dump file, the SQL files, and the log files.

        cd /home/oracle/labs

        rm tab.dmp  tabenc*.sql  enc*.log
