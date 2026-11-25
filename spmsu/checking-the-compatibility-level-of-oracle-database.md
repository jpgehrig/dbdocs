Use this SQL query to check that the compatibility level of your database corresponds to the value of the COMPATIBLE initialization parameter:

    SQL> SELECT name, value FROM v$parameter
             WHERE name = 'compatible';

**Parent topic:** [Checking Compatibility Before Upgrading Oracle Database](getting-started.md)
