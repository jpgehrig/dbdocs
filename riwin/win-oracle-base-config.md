## About Oracle Base Config

Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the configuration files reside in a location known as ORACLE_BASE_CONFIG.

In a read/write ORACLE_HOME, the ORACLE_BASE_CONFIG path is the same as the ORACLE_HOME path because it is located at ORACLE_HOME. However, in a read-only ORACLE_HOME, the ORACLE_BASE_CONFIG path is the same as ORACLE_BASE.

`ORACLE_BASE_CONFIG\dbs` contains the configuration files for ORACLE_HOME. Each file in the `dbs` directory contains ORACLE_SID so that the directory can be shared by many different ORACLE_SIDs.

To print the ORACLE_BASE_CONFIG path, run the `orabaseconfig` command from the `%ORACLE_HOME%\bin` directory:

    C:\> set ORACLE_HOME C:\app\oracle\product\19.0.0\dbhome_1
    C:\> cd %ORACLE_HOME%\bin
    orabaseconfig

For example:

    orabaseconfig
    C:\> C:\app\oracle

Where, `C:\app\oracle` is ORACLE_BASE.

**Parent topic:** [Evolution of Oracle Homes](win-evolution-oracle-homes.md)
