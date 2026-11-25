ORA-09275
Connect internal is not a valid DBA connection

Cause: `CONNECT INTERNAL` is no longer supported for DBA connections.

Action: If NTS is enabled, you can connect to the database as `CONNECT / AS SYSDBA` or `CONNECT / AS SYSOPER.` If NTS is not enabled, you can connect as `CONNECT SYS AS SYSDBA`. You can also connect as an existing user with the appropriate password.

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
