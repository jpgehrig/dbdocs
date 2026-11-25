## About Oracle Base Homes

Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the user-specific files, instance-specific files, and log files reside in a location known as the ORACLE_BASE_HOME.

In a read/write ORACLE_HOME, the ORACLE_BASE_HOME path is the same as the ORACLE_HOME directory. However, in a read-only ORACLE_HOME, the ORACLE_BASE_HOME directory is not co-located with ORACLE_HOME but is located at ORACLE_BASE/homes/HOME_NAME.

Where, HOME_NAME is the internal name for ORACLE_HOME.

For example, the networking directories `network/admin`, `network/trace`, and `network/log` are located in the ORACLE_BASE_HOME directory. In a read/write ORACLE_HOME the networking directories appear to be in ORACLE_HOME because ORACLE_BASE_HOME is co-located with ORACLE_HOME, whereas in a read-only ORACLE_HOME the networking directories are located in ORACLE_BASE/homes/HOME_NAME.

To print the ORACLE_BASE_HOME path, run the `orabasehome `command from the `$ORACLE_HOME/bin` directory:

    $ setenv ORACLE_HOME /u01/app/oracle/product/19.0.0/dbhome_1
    $ cd $ORACLE_HOME/bin
    $ ./orabasehome

For example:

    $ ./orabasehome
    /u01/app/oracle/homes/OraDB19Home1

Where, `/u01/app/oracle` is ORACLE_BASE and `OraDB19Home1` is HOME_NAME

**Parent topic:** [Evolution of Oracle Homes](understanding-read-only-oracle-homes.md)
