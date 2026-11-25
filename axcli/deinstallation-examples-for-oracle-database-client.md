Use these examples to help you understand how to run the `deinstall` command.

You can run `deinstall` from the `$ORACLE_HOME/deinstall` directory. The deinstallation starts without prompting you for the Oracle home path.

    $ ./deinstall

If you have a response file, then use the optional flag `-paramfile` to provide a path to the response file.

You can generate a deinstallation response file by running the `deinstall` command with the `-checkonly` flag. Alternatively, you can use the response file template located at `$ORACLE_HOME/deinstall/response/deinstall.rsp.tmpl.`

In the following example, the `deinstall` command is in the path`/u01/app/oracle/product/19.0.0/client_1/deinstall`. It uses a response file called `my_db_paramfile.tmpl` in the software owner location `/home/usr/oracle`:

    $ cd /u01/app/oracle/product/19.0.0/client_1/deinstall
    $ ./deinstall -paramfile /home/usr/oracle/my_db_paramfile.tmpl

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
