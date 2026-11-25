## Relinking Oracle Database Client Binaries After Installation

After an Oracle Database Client installation, if required, you can modify the binaries using the `relink as_installed` option.

For example, you might want to relink the Oracle Database Client binaries every time you apply an operating system patch or after an operating system upgrade.

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

1.  Login as the Oracle Database Client owner user (`oracle`).
2.  Set the ORACLE_HOME environment variable
        $ ORACLE_HOME=/u01/app/oracle/product/19.0.0/client_1
3.  Go to the `$ORACLE_HOME/bin` directory:
        $ cd $ORACLE_HOME/bin
4.  Run the `relink` script with the `as_installed` option to relink the binaries.
        $ ./relink as_installed

    The relinking is complete and the log files are generated under the `$ORACLE_HOME/install` directory.

**Parent topic:** [Installing Oracle Database Client](installing-oracle-database-client.md)
