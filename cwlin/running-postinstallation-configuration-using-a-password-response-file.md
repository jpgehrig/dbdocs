## Running Postinstallation Configuration Using a Password Response File

Complete this procedure to run configuration assistants with the `configToolAllCommands` script.

1.  Create a password response file as described in Creating a Password File.
2.  Change directory to `$ORACLE_HOME/cfgtoollogs`.
3.  Run the configuration script using the following syntax:
        configToolAllCommands RESPONSE_FILE=/path/name.properties

    For example:

        $ ./configToolAllCommands RESPONSE_FILE=/home/oracle/pwdrsp.properties

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-configtoolallcommands-script.md)
