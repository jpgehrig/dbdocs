Enabling a system to take advantage of the new extended data types requires specific upgrade actions.

Oracle Database 12c introduced `MAX_STRING_SIZE` to control the maximum size of `VARCHAR2`, `NVARCHAR2`, and `RAW` data types in SQL. Setting `MAX_STRING_SIZE = EXTENDED` enables the 32767 byte limit introduced in Oracle Database 12c.

To be able to set `MAX_STRING_SIZE = EXTENDED`, you must set the `COMPATIBLE` initialization parameter to `12.0.0.0` or higher

In addition, you must run the script `utl32k.sql` script while the database is open in upgrade mode so that you invalidate and recompile objects that are affected by the change in data type sizes. For example:

    CONNNECT SYS / AS SYSDBA
    SHUTDOWN IMMEDIATE;
    STARTUP UPGRADE;
    ALTER SYSTEM SET max_string_size=extended;
    START $ORACLE_HOME/rdbms/admin/utl32k.sql
    SHUTDOWN IMMEDIATE;
    STARTUP;

**Caution:**

You can change the value of `MAX_STRING_SIZE` from `STANDARD` to `EXTENDED`. However, you cannot change the value of `MAX_STRING_SIZE` from `EXTENDED` to `STANDARD`. By setting `MAX_STRING_SIZE = EXTENDED`, you are taking an explicit action that can introduce application incompatibility in your database.

**See Also:**

[Oracle Database Reference](../refrn/MAX_STRING_SIZE.md) for complete information about `MAX_STRING_SIZE`, including recommendations and procedures

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
