Oracle recommends that you run the `utlrp.sql` script after you install, patch, or upgrade a database, to identify and recompile invalid objects.

The `utlrp.sql` script recompiles all invalid objects. Run the script immediately after installation, to ensure that users do not encounter invalid objects.

1.  Start SQL\*Plus:
        sqlplus "/ AS SYSDBA"
2.  Run the `utlrp.sql` script, where `Oracle_home` is the Oracle home path:
        SQL> @Oracle_home/rdbms/admin/utlrp.sql

The `utlrp.sql` script automatically recompiles invalid objects in either serial or parallel recompilation, based on both the number of invalid objects, and on the number of CPUs available. CPUs are calculated using the number of CPUs (cpu_count) multiplied by the number of threads for each CPU (parallel_threads_per_cpu). On Oracle Real Application Clusters (Oracle RAC), this number is added across all Oracle RAC nodes.

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
