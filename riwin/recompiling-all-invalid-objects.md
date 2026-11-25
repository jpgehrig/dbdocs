## Recompiling All Invalid Objects

Identify and recompile invalid objects on the CDB and PDBs using the `catcon` utility to run `utlrp.sql` after you install, patch, or upgrade a database.

**Note:**

If you upgraded using the AutoUpgrade utility, then AutoUpgrade automatically takes care of this task during the upgrade. You do not need to perform this task.

Oracle recommends that you use the `catcon.pl` utility to run `utlrp.sql` on all containers in your container database (CDB). The `utlrp.sql` script recompiles all invalid objects. Run the script immediately after installation, to ensure that users do not encounter invalid objects.

1.  Change directory to `Oracle_home``/rdbms/admin`. For example
        $ cd $ORACLE_HOME/rdbms/admin
2.  Use the `catcon.pl` script in the Oracle home to run `utlrp.sql`. For example:
        $ORACLE_HOME/perl/bin/perl catcon.pl --n 1 --e --b utlrp --d '''.''' utlrp.sql

    Note the following conditions of this use case:

    - `--n` parameter: is set to 1, so the script runs each PDB recompilation in sequence.

    - `--e` parameter: turns echo on.

    - `--b` parameter: Sets the log file base name. It is set to `utlrp`.

Expect a time delay for the serial recompilation of PDBs to complete. Depending on the number of PDBs that you are upgrading, the recompilation can extend significantly beyond the time required for the upgrade scripts to complete.

The `utlrp.sql` script automatically recompiles invalid objects in either serial or parallel recompilation, based on both the number of invalid objects, and on the number of CPUs available. CPUs are calculated using the number of CPUs (cpu_count) multiplied by the number of threads for each CPU (parallel_threads_per_cpu). On Oracle Real Application Clusters (Oracle RAC), this number is added across all Oracle RAC nodes.

For more information about catcon utility syntax and options, refer to Oracle Multitenant Administrator's Guide.

**Related Topics**

- [Syntax and Parameters for catcon.pl](../multi/administering-a-cdb-with-sql-plus.md)

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
