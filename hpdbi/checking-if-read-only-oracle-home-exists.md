Run the `orabasehome` command to determine if your Oracle home is a read/write or read-only Oracle home.

If the output of the `orabasehome` command is the same as \$ORACLE_HOME, then your Oracle home is in read/write mode. If the output displays the path `ORACLE_BASE/homes/HOME_NAME`, then your Oracle home is in read-only mode.

1.  Set the ORACLE_HOME environment variable:
    Bourne, Bash or Korn shell:

        $ ORACLE_HOME=/u01/app/oracle/product/19.0.0/dbhome_1
        $ export ORACLE_HOME

    C shell:

        % setenv ORACLE_HOME /u01/app/oracle/product/19.0.0/dbhome_1
2.  Go to the `bin` directory and run the `orabasehome` command:
        $ cd $ORACLE_HOME/bin
        $ ./orabasehome
        /u01/app/oracle/homes/OraDB19Home1

    In this example, the Oracle home is in read-only mode.

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes.md)
