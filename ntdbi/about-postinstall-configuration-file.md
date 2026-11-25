## About the Postinstallation Configuration File

When you run a silent or a response file installation, you provide information about your servers in a response file that you otherwise provide manually during a graphical user interface installation.

However, the response file does not contain passwords for user accounts that configuration assistants require after software installation is complete. The configuration assistants are started with a script called `configToolAllCommands`. You can run this script in the response file mode by using a password response file. The script uses the passwords to run the configuration tools in succession to complete the configuration.

If you keep the password file to use for clone installations, then Oracle strongly recommends that you store it in a secure location. In addition, if you must stop an installation to fix an error, you can run the configuration assistants using `configToolAllCommands` and a password response file.

The `configToolAllCommands` password response file consists of the following syntax options:

- internal_component_name is the name of the component that the configuration assistant configures

- variable_name is the name of the configuration file variable

- value is the desired value of the configuration.

The command syntax is as follows:

internal_component_name\|variable_name=value

For example:

    oracle.crs|S_ASMPASSWORD=PassWord

Oracle strongly recommends that you maintain security with a password response file:

- Permissions on the response file must be set to 600.

- The owner of the response file must be the installation owner user, with the group set to the central inventory (oraInventory) group.

**Parent topic:** [Postinstallation Configuration Using Response File Created During Installation](postinstallation-configuration-using-response-file-created-during-installation.md)
