To help to assure good performance, use this procedure to gather dictionary statistics after completing your upgrade.

Oracle recommends that you gather dictionary statistics both before and after upgrading the database, because Data Dictionary tables are modified and created during the upgrade. With Oracle Database 12c release 2 (12.2) and later releases, you gather statistics as a manual procedure after the upgrade, when you bring the database up in normal mode.

- Non-CDB Oracle Database: Oracle recommends that you use the `DBMS_STATS.GATHER_DICTIONARY_STATS` procedure to gather these statistics. For example, enter the following SQL statement:

      SQL> EXEC DBMS_STATS.GATHER_DICTIONARY_STATS;

- CDB: Oracle recommends that you use `catcon` to gather Data Dictionary statistics across the entire multitenant architecture

  To gather dictionary statistics for all PDBs in a container database, use the following syntax

  `$ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -b gatherstats -- --x"exec dbms_stats.gather_dictionary_stats"`

  To gather dictionary statistics on a particular PDB, use syntax similar to the following:

      $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -c
      'SALES1' -b gatherstats -- --x"exec dbms_stats.gather_dictionary_stats"

  In the preceding example the `-c SALES1` option specifies a PDB inclusion list for the command that you run, specifying the database named `SALES1`. The option ` -b gatherstats` specifies the base name for the logs. The option `--x` specifies the SQL command that you want to execute. The SQL command itself is inside the quotation marks.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md)

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
