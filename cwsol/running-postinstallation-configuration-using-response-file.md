You can use a response file to complete postinstallation tasks on one or more servers simultaneously.

Complete this procedure to run configuration assistants with the `executeConfigTools` command and a response file.

1.  Edit the response file and specify the required passwords for your configuration. You can use the response file created during installation, located at `$ORACLE_HOME/install/response/`product_timestamp.rsp. For example:
    For Oracle Database (`oracle` user)

        oracle.install.asm.SYSASMPassword=password
        oracle.install.config.emAdminPassword=password

    For Oracle Grid Infrastructure (`grid` user)

        grid.install.asm.SYSASMPassword=password
        grid.install.config.emAdminPassword=password
2.  Change directory to the Oracle home containing the installation software. For example:
    For Oracle Grid Infrastructure:

        cd Grid_home

    Where, Grid_home is the path to the Oracle Grid Infrastructure home directory `/u01/app/19.0.0/grid`

    For Oracle Database:

        cd $ORACLE_HOME
3.  Run the configuration script using the following syntax:
    For Oracle Grid Infrastructure:

        $ ./gridSetup.sh -executeConfigTools -responseFile Grid_home/install/response/product_timestamp.rsp

    For Oracle Database:

        $ ./runInstaller -executeConfigTools -responseFile $ORACLE_HOME/install/response/product_timestamp.rsp

    For Oracle Database, you can also run the response file located in the directory `$ORACLE_HOME/inventory/response/`:

        $ ./runInstaller -executeConfigTools -responseFile $ORACLE_HOME/inventory/response/db_install.rsp

    The postinstallation configuration tool runs the installer in the graphical user interface mode, displaying the progress of the postinstallation configuration. Specify the` [-silent]` option to run the postinstallation configuration in the silent mode.

    For example, for Oracle Grid Infrastructure:

        $ ./gridSetup.sh -executeConfigTools -responseFile /u01/app/19.0.0/grid/response/grid_2016-01-09_01-03-36PM.rsp [-silent]

    For Oracle Database:

        $ ./runInstaller -executeConfigTools -responseFile /u01/app/oracle/product/19.0.0/dbhome_1/inventory/response/db_2016-01-09_01-03-36PM.rsp [-silent]

**Parent topic:** [Postinstallation Configuration Using Response File Created During Installation](postinstallation-configuration-using-response-file-created-during-installation.md)
