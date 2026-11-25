## About the Postinstallation Configuration File

The configuration assistants are started with a script called `configToolAllCommands`.

When you perform an installation using silent mode or response file mode, you provide information about your servers in a response file that you otherwise provide manually using a graphical user interface. However, the response file does not contain passwords for user accounts that configuration assistants require after software installation is complete. To run the configuration assistants after the installation completes in silent mode, you must run the `configToolAllCommands` script and provide the passwords used by the assistants in a password file.

You can run the `configToolAllCommands` script in silent mode by using a password response file. The script uses the passwords in the file to run the configuration tools in succession to complete the software configuration. If you keep the password file to use when cloning installations, then Oracle strongly recommends that you store the password file in a secure location.

You can also use the password file to restart a failed installation. If you stop an installation to fix an error, then you can rerun the configuration assistants using `configToolAllCommands` and a password response file.

The `configToolAllCommands` password response file has the following options:

- `oracle.crs` for Oracle Grid Infrastructure components or `oracle.server` for Oracle Database components that the configuration assistants configure.

- variable_name is the name of the configuration file variable.

- value is the desired value to use for configuration.

The command syntax is as follows:

    internal_component_name|variable_name=value

For example, to set the password for the SYS user of Oracle ASM:

    oracle.crs|S_ASMPASSWORD=PassWord

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-a-script.md)
