Review this procedure to understand how to use the `postupgrade_fixups.sql` scripts for Non-CDB databases.

The postupgrade fixup scripts are generated when you run the Pre-Upgrade Information Tool (`preupgrade.jar`). Run the postupgrade scripts any time after completing an upgrade. For Non-CDB databases, the postupgrade fixup scripts provide general warnings, errors, and informational recommendations.

You can run the script either by using the `catcon.pl` utility, or by using SQL\*Plus.

The location of the postupgrade SQL scripts and log files depends on how you set output folders, or define the Oracle base environment variable. The postupgrade fixup scripts are placed in the same directory path as the preupgrade fixup scripts.

If you specify an output directory by using the `dir` option with the Pre-Upgrade Information Tool, then the output logs and files are placed under that directory in the file path /`cfgtoollogs/``dbunique_name``/preupgrade`, where `dbunique_name` is the name of your source Oracle Database. If you do not specify an output directory when you run the Pre-Upgrade Information Tool, then the output is directed to one of the following default locations:

- If you do not specify an output directory with `DIR`, but you have set an Oracle base environment variable, then the generated scripts and log files are created in the following file path:

  `Oracle-base``/cfgtoollogs/``dbunique_name``/preupgrade`

- If you do not specify an output directory, and you have not defined an Oracle base environment variable, then the generated scripts and log files are created in the following file path:

  `Oracle-home``/cfgtoollogs/``dbunique_name``/preupgrade`

The postupgrade fixup scripts that the Pre-Upgrade Information Tool creates depend on whether your source database is a Non-CDB database, or a CDB database:

- Non-CDB: `postupgrade_fixups.sql`

Example 10-4 Example of Spooling Postupgrade Fixup Results for a Non-CDB Oracle Database

Set the system to spool results to a log file so you can read the output. However, do not spool to the `admin` directory:

    SQL> SPOOL postupgrade.log
    SQL> @postupgrade_fixups.sql
    SQL> SPOOL OFF

Turn off the spooling of script results to the log file:

     SPOOL OFF

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
