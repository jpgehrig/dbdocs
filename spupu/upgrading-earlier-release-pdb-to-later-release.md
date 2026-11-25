Open PDBs in `UPGRADE` mode use the Parallel Upgrade Utility to carry out the upgrade of the earlier-release PDB to the release level of the CDB.

1.  If needed, switch to the PDB that you want to upgrade. For example, enter the following command to switch to the PDB `salespdb`:

        SQL> ALTER SESSION SET CONTAINER=salespdb;

2.  Open the PDB in UPGRADE mode.

        SQL> ALTER PLUGGABLE DATABASE OPEN UPGRADE;

3.  Upgrade the PDB using the Parallel Upgrade Utility command (`catctl.pl`, or the shell utility `dbupgrade`).

    When you upgrade a PDB, you use the commands you normally use with the Parallel Upgrade Utility. However, you also add the option `-c ``PDBname` to specify which PDB you are upgrading. Capitalize the name of your PDB as shown in the following example using the PDB named `salespdb`:

        $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catctl.pl -d  \
        $ORACLE_HOME/rdbms/admin -c 'salespdb' -l $ORACLE_BASE catupgrd.sql

4.  Review results.

    The default file path for the logs is in the path `Oracle_base``/cfgtoollogs/``dbname``/``upgradedatetime`, where `Oracle_base` is the Oracle base path, `dbname` is the database name, and `upgradedatetime` is the date and time for the upgrade. The date and time strings are in the character string format YYYYMMDDHHMMSC, in which YYYY designates the year, MM designates the month, DD designates the day, HH designates the hour, MM designates the minute, and SC designates the second.

    For example:

        $ORACLE_BASE/cfgtoollogs/salespdb/upgrade20181015120001/upg_summary.log

5.  Log in to SQL\*Plus, and open the PDB to execute post-upgrade fixups, and to recompile the `INVALID` objects in the database:

        SQL> STARTUP;
        SQL> ALTER SESSION SET CONTAINER=salespdb;

6.  Use the utility `catcon.pl` to run the script `postupgrade_fixups.sql`:

        $ORACLE_HOME/perl/bin/perl catcon.pl –c 'salespdb' -n 1 -e -b postfixups -d '''.''' /tmp/cfgtoollogs/salespdb/preupgrade/postupgrade_fixups.sql

7.  Use the utility `catcon.pl` to run `utlrp.sql` from the `$ORACLE_HOME/rdbms/admin` directory:

        $ORACLE_HOME/perl/bin/perl catcon.pl –c 'salespdb'-n 1 -e -b comp -d '''.''' utlrp.sql

    The script recompiles `INVALID` objects in the database, and places a log file in the current directory with the name `comp0.log`.

**Parent topic:** [Upgrading Pluggable Databases Sequentially](upgrading-pluggable-databases-sequentially.md)
