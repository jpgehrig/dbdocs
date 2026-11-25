## How to Show the Current State of the Oracle Data Dictionary

To check the state of the Oracle Data Dictionary for diagnosing upgrades and migrations, use one of three methods.

Example 6-1 Run the `dbupgdiag.sql` Script

The `dbupgdiag.sql` script collects diagnostic information about the status of the database, either before or after the upgrade. Download the script from My Oracle Support note 556610, and run the script as the database `SYS` user. The script generates the diagnostic information in a readable format, in a log file with the name file `db_upg_diag_``sid``_``timestamp``.log`, where `sid` is the Oracle system identifier for the database, and `timestamp` is the time that the file is generated.

For example, where you download and place the script in the directory `/u01/dbupgdiag-script`:

    /u01/dbupdiag-script/ $ sqlplus / as sysdba
    sql> alter session set nls_language='American';
    sql> @dbupgdiag.sql
    sql> exit

You can run the script in SQL\*Plus both before the upgrade on the source database, and after the upgrade on the upgraded database. For more information about the script, refer to the instructions and the output example file in My Oracle Support Note 556610.1.

Example 6-2 Run a SQL Query on DBA_REGISTRY

To show the current state of the dictionary, perform a SQL query similar to the following example:

    SQL> spool /tmp/regInvalid.out
    SQL> set echo on
    -- query registry
    SQL> set lines 80 pages 100
    SQL> select substr(comp_id,1,15) comp_id,substr(comp_name,1,30)
          comp_name,substr(version,1,10) version_full,status
    from dba_registry order by comp_id;

Example 6-3 Run SQL Queries to Check for Invalid Objects

To check for invalid objects, you can perform SQL queries, similar to the following examples:

1.  This query list all the invalid objects in the database:

        SQL> select owner, object_name, object_type from dba_invalid_objects order by owner, object_type, object_name;

2.  After you have upgraded the database, and you have run `utlrp.sql`, Oracle-maintained objects should be valid.

    To check to ensure Oracle-maintained objects are valid, enter the following query:

        SQL> select owner, object_name, object_type from sys.dba_invalid_objects where oracle_maintained='Y';

3.  To list any invalid application objects in the database, enter the following query:

        SQL> select owner, object_name, object_type from sys.dba_invalid_objects where oracle_maintained='N';

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=556610.1>

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)
