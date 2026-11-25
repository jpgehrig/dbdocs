Use these examples to help you understand how to run the `deinstall` command.

Run `deinstall` from the `$ORACLE_HOME/deinstall` directory. The deinstallation starts without prompting you for the Oracle home path.

    $ ./deinstall

You can generate a deinstallation response file by running `deinstall` with the `-checkonly` flag. Alternatively, you can use the response file template located at `$ORACLE_HOME/deinstall/response/deinstall.rsp.tmpl`. If you have a response file, then use the optional flag `-paramfile` to provide a path to the response file.

In the following example, the `deinstall` command is in the path`/u01/app/oracle/product/19.0.0/dbhome_1/deinstall`. It uses a response file called `my_db_paramfile.tmpl` in the software owner location `/home/usr/oracle`:

    $ cd /u01/app/oracle/product/19.0.0/dbhome_1/deinstall
    $ ./deinstall -paramfile /home/usr/oracle/my_db_paramfile.tmpl

To remove the Oracle Grid Infrastructure home, use the `deinstall` command in the Oracle Grid Infrastructure home.

In this example, the Oracle Grid Infrastructure home is `/u01/app/oracle/product/19.0.0/grid`

    $ cd  /u01/app/oracle/product/19.0.0/grid/deinstall
    $ ./deinstall -paramfile /home/usr/oracle/my_grid_paramfile.tmpl

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
