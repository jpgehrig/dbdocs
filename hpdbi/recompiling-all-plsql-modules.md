Run the `utlrp.sql` script after you install, patch, or upgrade a database, to identify and recompile invalid PL/SQL modules.

The `utlrp.sql` script recompiles all PL/SQL modules, including packages, procedures, and types. Recompiling the modules corrects any invalid objects created during installation.

1.  Log in as the `oracle` user.
2.  Use the `oraenv` or `coraenv` script to set the environment for the database where you want to run the `utlrp.sql` script:
    - Bourne, Bash, or Korn shell:

          $ . /usr/local/bin/oraenv

    - C shell:

          % source /usr/local/bin/coraenv

    When prompted, provide the system identifier (SID) for the database.
3.  Start SQL\*Plus as SYSDBA.
    For example:
        $ sqlplus / AS SYSDBA
4.  Start the database in restricted mode and run the `utlrp.sql `script.
    For example:
        SQL> STARTUP RESTRICT
        SQL> @$ORACLE_HOME/rdbms/admin/utlrp.sql

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
