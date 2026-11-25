## Understanding Oracle Database Services on Windows

The following Oracle services are automatically started after installation when you create a database:

- `OracleService``SID` (Oracle Database service)

- `Oracle``HOMENAME``TNSListener` (Oracle Database listener service)

If you configured Oracle Automatic Storage Management, then the `OracleOHService` and `OracleASMService+ASM` services are listed as well. However, other services for networking or other individual components may not automatically start.

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
