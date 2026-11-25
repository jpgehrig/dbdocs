## Running Postinstallation Configuration Using a Response File

Complete this procedure to run configuration assistants configuration with the `-executeConfigTools` command.

1.  Edit the response file and specify the required passwords for your configuration. You can use the response file created during installation, located at `Oracle_home``\install\response\``product``_``timestamp``.rsp`. For example, for Oracle Grid Infrastructure:
        oracle.install.asm.SYSASMPassword=password
        oracle.install.config.emAdminPassword=password
2.  Change directory to the Oracle home containing the installation software. For example, for Oracle Grid Infrastructure:
        cd Grid_home
3.  Run the configuration script using the following syntax:
    For Oracle Grid Infrastructure:

        setup.exe -executeConfigTools -responsefile Grid_home\install\response\product_timestamp.rsp

    For Oracle Database:
        setup.exe -executeConfigTools -responseFile Oracle_home\install\response\product_timestamp.rsp

    For Oracle Database, you can also edit and use the response file located in the directory `Oracle_home``\inventory\response\`:

        setup.exe -executeConfigTools -responseFile Oracle_home\inventory\response\db_install.rsp

    The postinstallation configuration tool runs the installer in the graphical user interface mode, displaying the progress of the postinstallation configuration.

    Specify the `[-silent]` option to run the postinstallation configuration in the silent mode.

    For example, for Oracle Grid Infrastructure:

        setup.exe -executeConfigTools -responseFile Grid_home\install\response\grid_2016-09-09_01-03-36PM.rsp -silent

    For Oracle Database:

        setup.exe -executeConfigTools -responseFile Oracle_home\inventory\response\db_2016-09-09_01-03-36PM.rsp -silent

**Parent topic:** [Postinstallation Configuration Using Response File Created During Installation](postinstallation-configuration-using-the-installer.md)
