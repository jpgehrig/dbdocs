## Recompiling Invalid Objects on Windows Systems

Run the `utlrp.sql` script after you install, patch, or upgrade a database, to identify, and recompile invalid objects.

The `utlrp.sql` script recompiles all invalid objects, including packages, procedures, and types. Run the script immediately after installation, to ensure that users do not encounter invalid objects.

1.  Log in as an Administrator user, or as the Oracle Home user.
2.  Start SQL\*Plus and log in as a SYSDBA user:
    1.  Click Start.
    2.  Select Programs (or All Programs).
    3.  Select Oracle - HOME_NAME.
    4.  Select Application Development.
    5.  Select SQL\*Plus.
3.  Run the `utlrp.sql` script, where Oracle_home is the Oracle home path:
        SQL> @Oracle_home\rdbms\admin\utlrp.sql

The `utlrp.sql` script automatically recompiles invalid objects in either serial or parallel recompilation, based on the number of invalid objects, and on the number of CPUs available. CPUs are calculated using the number of CPUs (cpu_count) multiplied by the number of threads for each CPU (parallel_threads_per_cpu). On Oracle Real Application Clusters (Oracle RAC), this number is added across all Oracle RAC nodes.

**Parent topic:** [Oracle Database Postinstallation Tasks](oracle-database-postinstallation-tasks.md)
