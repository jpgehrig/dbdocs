## Deinstallation Examples for Oracle Database

Use these examples to help you understand how to run the `deinstall` command.

Run `deinstall` from the `ORACLE_HOME\deinstall` directory. The deinstallation starts without prompting you for the Oracle home path.

You can generate a deinstallation response file by running `deinstall` with the `-checkonly ` flag. Alternatively, you can use the response file template located at `DRIVE_LETTER`:\\ `ORACLE_HOME/deinstall/response/deinstall.rsp.tmpl`.

In the following example, the `deinstall` command is in the path `C:\app\oracle\product\19.0.0\dbhome_1\deinstall`, and it uses a response file in the software owner location `C:\Documents and Settings\oracle\:`

    DRIVE_LETTER:\> cd \app\oracle\product\19.0.0\dbhome_1\deinstall\
    DRIVE_LETTER:\> deinstall.bat -paramfile %HOMEPATH%\my_db_paramfile.tmpl

For the grid infrastructure home, use (`deinstall.bat`) in the Oracle Grid Infrastructure home. In this example, the Oracle Grid Infrastructure home is `C:\app\oracle\product\19.0.0\grid`

    DRIVE_LETTER:\> cd \app\oracle\product\19.0.0\grid\deinstall\
    DRIVE_LETTER:\> deinstall.bat -paramfile %HOMEPATH%\my_grid_paramfile.tmpl

- [Downgrading Oracle Restart](downgrading-oracle-restart.md)
  Use this procedure to deconfigure and downgrade Oracle Restart, or to troubleshoot Oracle Restart installation errors.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
