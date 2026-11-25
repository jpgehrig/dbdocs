## Performing Postinstallation Configuration Using a Response File

To run configuration assistants with the `configToolAllCommands` script in silent mode or response file mode, perform these steps.

1.  Change directory to `%ORACLE_HOME%\cfgtoollogs`.
2.  Run the configuration script using the following syntax:
        configToolAllCommands RESPONSE_FILE=\path\name.properties

    or

        setup.exe -executeConfigTools -responseFile responsefile_location -silent -debug

Example A-6 Running Configuration Assistants in Response File Mode

Assume you created a password response file in the `C:\users\oracle\db` directory with a name of `cfg_db.properties`. To run the configuration assistants in response file mode to configure the Oracle software after installation, enter commands similar to the following:

    C:\> cd %ORACLE_HOME%\cfgtoollogs
    C:\..\cfgtoollogs> configToolAllCommands RESPONSE_FILE=C:\users\oracle\db\cfg
    _db.properties

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-a-script.md)
