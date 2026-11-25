## Running Postinstallation Configuration Using a Script and Response Files

You can run the postinstallation configuration assistants with the `configToolAllCommands` script.

1.  Create a password response file using the format filename.properties for the file name, as described in [Creating a Password Response File](creating-a-password-response-file.md).
2.  Change directory to `Oracle_home``\cfgtoollogs`, and run the configuration script using the following syntax:
        configToolAllCommands RESPONSE_FILE=\path\filename.properties

    For example:

        C:\..\cfgtoollogs> configToolAllCommands RESPONSE_FILE=C:\users\oracle\grid\cfgrsp.properties

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstall-config-using-configtoolallcommands-script.md)
