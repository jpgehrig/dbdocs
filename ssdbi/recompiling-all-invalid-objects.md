After you install, patch, or upgrade a database, recompile invalid objects on the CDB and PDBs with a recompilation driver script.

Oracle provides the recompilation scripts `utlrp.sql`, `utlprp.sql`, and `utlprpom.sql`. These scripts are located in the `Oracle_home``/rdbms/admin` directory.

**Note:**

Starting with AutoUpgrade 23.1, when you run the AutoUpgrade utility, AutoUpgrade runs the `utlprpom.sql` script, and does not run `utlrp.sql`. When AutoUpgrade is used for upgrades to Oracle Database 12c Release 2 (12.2.0.1) and later releases, AutoUpgrade only recompiles invalid objects owned by Oracle-maintained schemas. Because database upgrades do not need to touch user objects, AutoUpgrade maintains this policy when it recompiles invalid objects.

After installing a database, recomplile all invalid objects;

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

After patching or upgrading a database, there is more than one approach you can use to recompile invalid Oracle-owned and user-owned objects:

Recompile all invalid objects (the invalid objects in both Oracle and user schemas) by using `utlrp.sql` or `utlprp.sql`.

If time is a factor and the type of invalid objects is predominately application owned, then you can recompile Oracle-owned invalid objects first, and defer recompiling application-owned invalid objects to a later time. To recompile invalid objects in Oracle schemas, use `utlprpom.sql`. To recompile the remaining invalid objects, use `utlrp.sql` or `utlprp.sql`.

**Note:**

When you use either `utlprp.sql` or `utlprpom.sql`, note that both scripts require you to define the degree of parallelism that the script should use, or determine the number of parallel recompile jobs to use.

The script uses syntax as follows, where `base` is the base name you want to have given to log files, `N` is the number of PDBs on which you want to run recompilation jobs in parallel (degrees of parallelism), `script.sql` is the Oracle recompilation script you chose to use, and `P` is the number of PDBs on which you want to run in parallel:

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -b base -d $ORACLE_HOME/rdbms/admin
              -n N -l /tmp script.sql '--pP'

Suppose you are running recompilation in a CDB using the log file base name `recomp`, with a degrees of parallelism setting of 3 jobs per PDB container, the script you choose to use is `utlprp.sql`, and you want to recompile across at most 10 PDBs at a time. In that case, the syntax you use to run the recompile operation is similar to the following,

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -b recomp -d $ORACLE_HOME/rdbms/admin -n 10 -l /tmp utlprp.sql '--p3'

**Related Topics**

- [Syntax and Parameters for catcon.pl](../multi/administering-a-cdb-with-sql-plus.md)

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
