Use this SQL query to find the COMPATIBLE initialization parameter value set for your database.

    SQL> SELECT name, value FROM v$parameter
             WHERE name = 'compatible';

**Parent topic:** [Checking Compatibility Before Upgrading Oracle Database](getting-started.md)
