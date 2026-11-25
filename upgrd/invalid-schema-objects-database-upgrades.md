## About Invalid Schema Objects and Database Upgrades

Run `utlrp.sql` to validate invalid objects as part of your upgrade test plan.

After database upgrades, release changes can result in invalid schema objects in the upgraded database. Typically, invalid objects fix themselves as they are accessed or run. However, Oracle recommends that you recompile invalid objects in the database as part of your patching and upgrade procedure, so that you resolve issues with invalid objects, and any required dependencies, before users encounter these invalid objects.

Object validation is an operation that checks the Oracle Database Data Definition Language (DDL) statements. These statements are used to define the database structure or schema. Validating DDL statements can take time to complete. The following is a list of some common factors that can affect object validation time:

- Number of invalid objects

- CPU types

- Processor speeds

- System loads

- Available physical memory

The `utlrp.sql` command recompiles all objects in an invalid state, including packages, procedures, and types. It is located in the `$ORACLE_HOME/rdbms/admin` directory. The `utlrp.sql` script automatically runs in serial or in parallel recompilation, based on the number of CPUs available (identified by the parameter cpu_count), multiplied by the number of threads for each CPU ( identified by the parameter parallel_threads_per_cpu). On Oracle Real Application Clusters systems (Oracle RAC), the number of parallel threads is added across all Oracle RAC nodes.

Run the command either as the SYS user, or as another user account that is granted the SYSDBA system privileges.

Oracle recommends that you run the `utlrp.sql` command in the earlier release Oracle Database to recompile any existing invalid objects in your database. Particularly ensure that SYS and SYSTEM user schema invalid objects are updated. During upgrade tests, run `utlrp.sql` in the upgraded Oracle Database as part of your upgrade test plan, so that you can include planning for recompilation time as part of your upgrade. Recompilation time is proportional to the number of invalid objects in the database. If the upgrade results in a large number of invalid objects, then `utlrp.sql` can take a significant amount of time to run.

**Parent topic:** [Compatibility and Interoperability Between Oracle Database Releases](compatibility-interoperability-between-database-releases.md)
