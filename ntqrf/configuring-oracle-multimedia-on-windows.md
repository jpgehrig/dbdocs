Use this procedure to configure Oracle Multimedia.

If you are creating and configuring a database manually, then you can configureOracle Multimedia as follows:

1.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
2.  Connect to Oracle Database with account `SYSDBA`:
        SQL> CONNECT /AS SYSDBA
3.  Start the database (if necessary):
        SQL> STARTUP
4.  Run the script `ordinst.sql`:
        SQL> ORACLE_HOME\ord\admin\ordinst.sql SYSAUX SYSAUX
5.  Run the script `iminst.sql`:
        SQL> ORACLE_HOME\ord\im\admin\catim.sql
6.  Exit SQL\*Plus:
        SQL> EXIT

    **Note:**

    If you manually copy your Oracle8i `listener.ora` and `tnsnames.ora` files into your Oracle Database network directory, then you must modify network configuration files `tnsnames.ora` and `listener.ora` on your server to enable calls to work and Oracle Multimedia to function properly.

    **See Also:**

    [Oracle Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

**Parent topic:** [About Oracle Multimedia on Windows](about-oracle-multimedia-on-windows.md)
