## Restarting the Upgrade from a Specific Phase that Failed Using -p

Use this option to complete an upgrade after fixing errors.

You can run the Parallel Upgrade Utility (`catctl.pl`, or the shell scripts `dbupgrade` or `dbupgrade.cmd`) with the `-p` option to rerun an upgrade and skip upgrade phases that already have run successfully. You can also rerun the upgrade on one phase to test the fix for failed phases.

To determine the phase number to restart, examine the upgrade log to identify where the first error occurred, and in what phase. You can then fix the cause of the error, and test the fix or rerun the upgrade to completion.

- Reviewing CDB Log Files for Failed Phases
  Identify your log file location, and review the CDB and PDB log files.
- Procedure for Finding and Restarting Multitenant Upgrades from a Failed Phase
  To restart a multitenant upgrade from a failed phase, first identify which PDB created the error and then search its appropriate log file for the error.

**Parent topic:** [Rerunning Upgrades for Oracle Database](rerunning-upgrades-oracle-database.md)

### Reviewing CDB Log Files for Failed Phases

Identify your log file location, and review the CDB and PDB log files.

The location of the Automatic Diagnostic Repository (ADR) and the diagnostic log files created by the upgrade scripts can vary, depending on your environment variables and parameter settings.

You can set log file paths when you run the Parallel Upgrade Utility (`catctl`) by setting the `-l` option to define a log file path.

Log files for CDB\$ROOT (CDBs) can span from `catupgrd0...catupgrd7.log`. Log files for pluggable databases (PDBs) are identified by the PDB container name (`dbname`), and span from `catupgrdp``dbname``0...catupgrdp``dbname``7.log`.

**Parent topic:** Restarting the Upgrade from a Specific Phase that Failed Using -p

### Procedure for Finding and Restarting Multitenant Upgrades from a Failed Phase

To restart a multitenant upgrade from a failed phase, first identify which PDB created the error and then search its appropriate log file for the error.

To identify the PDB that caused a multitenant upgrade failure, look at the upgrade summary report, or review catupgrd0.log; this log contains the upgrade summary report at the end of the file.

Use this procedure to check each log file looking for errors.

1.  Locate log files with errors.
    For example:

    Linux and Unix

        $ grep -i 'error at line' catupgrd*.log

    Windows

        C:\> find /I "error at line" catupgrd*.log

    The `grep` or `find` command displays the filenames of log files in which an error is found.
2.  Check each log file that has an error and identify where the first error occurred. Use the text editor of your choice to review each log file. Search for the first occurrence of the phrase `error at line`'. When you find the phrase, then search backwards from the error (reverse search) for `PHASE_TIME___START`.
    For example:

        PHASE_TIME___START 15 15-01-16 08:49:41

    The number after `PHASE_TIME___START` is the phase number where the error has occurred. In this example, the phase number is 15.

    Each log file can have an error in it. Repeat checking for the phrase `PHASE_TIME___START`, and identify the phase number with errors for each log file that contains an error, and identify the log file that contains the lowest phase number.

    The log file that contains the lowest phase number is restart phase number, which is the phase number from which you restart the upgrade.

    For example:

        catupgrd0.log error occurred in phase 15:

        PHASE_TIME___START 15 15-01-16 08:49:41

        catupgrd1.log error occurred in phase 19:

        PHASE_TIME___START 19 15-01-16 08:50:01

    In this example, the restart phase number is 15. Ensure that you identify the first error seen in all the log files, so that you can restart the upgrade from that phase.
3.  Restart the upgrade from the failed phase by changing directory to the running the Parallel Upgrade Utility (`catctl.pl`, which you can run from the command line using `dbupgrade` on Linux and Unix, and `dbupgrade.cmd` on Windows). Use the `-p` flag to indicate that you want to restart the upgrade from a phase, and provide the restart phase number. In multitenant databases, also use the `-c` flag using the syntax `-c '``PDBname``'`, where `PDBname` is the name of the PDB where the failure occurred.
    For example:

    Non-CDB Oracle Database on a Linux or UNIX system:

        cd $ORACLE_HOME/bin
        dbupgrade -p 15

    PDB in a multitenant Oracle Database (CDB) on a Windows system:

        cd $ORACLE_HOME/bin
        dbupgrade -p 15 -c 'PDB1'

    In both examples, the upgrade is restarted from phase 15, identified with the `-p` flag. In the multitenant example, the PDB with the error is identified with the `-c` flag.
    In these examples, the upgrade starts from phase 15 and runs to the end of the upgrade.
4.  (Optional) You can also run the phase that contained an error by specifying a stop phase, using the `-P` flag. Using a stop phase allows the upgrade to just rerun that phase in which the error occurred. You can determine quickly if the error is fixed by running it on the phase with the error, without running the entire upgrade.
    For example, using the Perl script Parallel Upgrade Utility command option:

        cd $ORACLE_HOME/rdbms/admin
        $ORACLE_HOME/perl/bin/perl catctl.pl -p 15 -P 15 -c 'PDB1'

    After you confirm that the error is fixed in the phase with the error, you can then resume the upgrade after that phase.
    For example, if you have confirmed that the error in phase 15 of your multitenant database upgrade of PDB1 is fixed, then you can use the following command on Linux and Unix systems to continue the upgrade at phase 16:

        cd $ORACLE_HOME/bin dbupgrade -p 16 -c 'PDB1'

**Parent topic:** Restarting the Upgrade from a Specific Phase that Failed Using -p
