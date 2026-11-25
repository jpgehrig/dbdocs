## Before You Begin

This 15-minute tutorial shows you how to handle operations on the metadata and data of Oracle-managed and user-managed tablespaces when the Transparent Data Encryption (TDE) keystore is closed.

### Background

In Oracle Database 18c, you must close the TDE keystore to disallow operations on encrypted tablespaces. The behavior when the keystore is closed does not depend on the type of tablespace being accessed. Operations on user-managed tablespaces or Oracle-managed tablespaces like ` SYSTEM, SYSAUX, UNDO,` and `TEMP` tablespaces raise the `ORA-28365 "wallet is not open"` error.

### What Do You Need?

- Oracle Database 19c installed
- A container database (CDB): ` ORCL `with ` PDB1`

------------------------------------------------------------------------

## Prepare the CDB to Use TDE

1.  Log in to `ORCL` as ` SYS` with the ` SYSDBA` administrative privilege.

        sqlplus / AS SYSDBA

2.  Create the keystore for the CDB in `/u02/app/oracle/admin/ORCL/tde_wallet`.

        mkdir -p /u02/app/oracle/admin/ORCL/tde_wallet

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE '/u02/app/oracle/admin/ORCL/tde_wallet/' IDENTIFIED BY password;

3.  Open the keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password CONTAINER=ALL;

4.  Set the TDE master encryption key.

        ADMINISTER KEY MANAGEMENT SET KEY IDENTIFIED BY password WITH BACKUP CONTAINER=ALL;

5.  Create a user-managed tablespace.

        CREATE TABLESPACE omtbs DATAFILE '/u02/app/oracle/oradata/ORCL/omts01.dbf' SIZE 10M;

6.  Check that the tablespaces are not encrypted.

        SELECT tablespace_name, encrypted FROM dba_tablespaces;

        TABLESPACE_NAME   ENC
        ----------------- ---
        SYSTEM            NO
        SYSAUX            NO
        UNDOTBS1          NO
        TEMP              NO
        USERS             NO
        OMTBS             NO

------------------------------------------------------------------------

## Encrypt Oracle-managed and User-managed Tablespaces

In this section, you close the keystore and see which operations on Oracle-managed tablespaces and user-managed tablespaces can be handled on the metadata and data.

1.  Close the keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE IDENTIFIED BY password CONTAINER = ALL;

2.  Switch one of the Oracle-managed tablespaces to encryption.

        ALTER TABLESPACE system ENCRYPTION USING 'AES192' ENCRYPT;
        ALTER TABLESPACE system ENCRYPTION USING 'AES192' ENCRYPT
        *
        ERROR at line 1:
        ORA-28365: wallet is not open

3.  Switch one of the user-managed tablespaces to encryption.

        ALTER TABLESPACE omtbs ENCRYPTION USING 'AES192' ENCRYPT;
        ALTER TABLESPACE omtbs ENCRYPTION USING 'AES192' ENCRYPT
        *
        ERROR at line 1:
        ORA-28365: wallet is not open

4.  Open the keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password CONTAINER = ALL;

5.  Switch one of the Oracle-managed tablespaces to encryption.

        ALTER TABLESPACE system ENCRYPTION USING 'AES192' ENCRYPT;

6.  Switch one of the user-managed tablespaces to encryption.

        ALTER TABLESPACE omtbs ENCRYPTION USING 'AES192' ENCRYPT;

7.  Check that the tablespaces are encrypted.

        SELECT tablespace_name, encrypted FROM dba_tablespaces;

        TABLESPACE_NAME   ENC
        ----------------- ---
        SYSTEM            YES
        SYSAUX            NO
        UNDOTBS1          NO
        TEMP              NO
        USERS             NO
        OMTBS             YES

------------------------------------------------------------------------

## Handle Encrypted Data in Oracle-managed and User-managed Tablespaces When Keystore is Closed

1.  Close the keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE IDENTIFIED BY password CONTAINER = ALL;

2.  Change the encryption algorithm in `SYSTEM` tablespace.

        ALTER TABLESPACE system ENCRYPTION USING 'AES128' ENCRYPT;
        ALTER TABLESPACE system ENCRYPTION USING 'AES128' ENCRYPT
        *
        ERROR at line 1:
        ORA-28365: wallet is not open

3.  Change the encryption algorithm in `OMTBS` tablespace.

        ALTER TABLESPACE omtbs ENCRYPTION USING 'AES128' ENCRYPT;
        ALTER TABLESPACE omtbs ENCRYPTION USING 'AES128' ENCRYPT
        *
        ERROR at line 1:
        ORA-28365: wallet is not open

4.  Create a table and insert data in the tablespace `SYSTEM`.

        CREATE TABLE system.test (c NUMBER, C2 CHAR(4)) TABLESPACE system;

        INSERT INTO system.test VALUES (1,'Test');

        COMMIT;

5.  Create a table and insert data in the tablespace `OMTBS`.

        CREATE TABLE system.test2 (c NUMBER, C2 CHAR(4)) TABLESPACE omtbs;
        CREATE TABLE system.test2
        *
        ERROR at line 1:
        ORA-28365: wallet is not open

------------------------------------------------------------------------

## Clean Up the Environment

1.  Open the keystore.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password CONTAINER = ALL;

2.  Drop the `SYSTEM.TEST` table.

        DROP TABLE system.test;

3.  Drop the user-managed tablespace.

        DROP TABLESPACE omtbs INCLUDING CONTENTS AND DATAFILES;

4.  Decrypt the Oracle-managed tablespaces.

        ALTER TABLESPACE system ENCRYPTION DECRYPT;

5.  Quit the session.

        EXIT
