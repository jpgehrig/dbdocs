Use one of three methods to check the state of the Oracle Data Dictionary for diagnosing upgrades and migrations.

### Running the `dbupgdiag.sql` Script

The `dbupgdiag.sql` script collects upgrade and migration diagnostic information about the current state of the data dictionary.

You can run the script in SQL\*Plus both before the upgrade on the source database, and after the upgrade on the upgraded database as the SYS user. Refer to My Oracle Support note 556610.1 for more information about using the `dbupgdiag.sql` script to collect upgrade and migrate diagnostic information.

### Running a SQL Query on DBA_REGISTERY

To show the current state of the dictionary, perform a SQL query similar to the following example:

    SQL> spool /tmp/regInvalid.out
    SQL> set echo on
    -- query registry
    SQL> set lines 80 pages 100
    SQL> select substr(comp_id,1,15) comp_id,substr(comp_name,1,30)
          comp_name,substr(version,1,10) version,status
    from dba_registry order by modified;

### Running a Query to Check for Invalid Objects

To query invalid objects, perform a SQL query similar to the following example:

    SQL> select owner, object_name, object_type from dba_invalid_objects order by owner, object_type;

After you have upgraded the database, and you have run `utlrp.sql`, this view query should return no rows.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=556610.1>

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrde-tasks.md)
