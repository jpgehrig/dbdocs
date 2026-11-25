## About the Postinstallation Configuration File

When you run a silent or response file installation, you provide information about your servers in a response file that you otherwise provide manually during a graphical user interface installation.

However, the response file does not contain passwords for user accounts that configuration assistants require after software installation is complete. The configuration assistants are started with a script called `configToolAllCommands`. You can run this script in response file mode by using a password response file. The script uses the passwords to run the configuration tools in succession to complete configuration.

If you keep the password file to use for clone installations, then Oracle strongly recommends that you store the password file in a secure location. In addition, if you have to stop an installation to fix an error, then you can run the configuration assistants using `configToolAllCommands` and a password response file.

The `configToolAllCommands` password response file has the following syntax options:

- `oracle.crs` for Oracle Grid Infrastructure components or `oracle.server` for Oracle Database components that the configuration assistants configure

- variable_name is the name of the configuration file variable

- value is the desired value to use for configuration.

The command syntax is as follows:

`internal_component_name|variable_name=value`

For example:

    oracle.crs|S_ASMPASSWORD=PassWord

The database configuration assistants require the SYS, SYSTEM, and DBSNMP passwords for use with Oracle DBCA. You may need to specify the following additional passwords, depending on your system configuration:

- If the database is using Oracle Automatic Storage Management (Oracle ASM) for storage, then you must specify a password for the `S_ASMSNMPPASSWORD` variable. If you are not using Oracle ASM, then leave the value for this password variable blank.

- If you create a multitenant container database (CDB) with one or more pluggable databases (PDBs), then you must specify a password for the `S_PDBADMINPASSWORD` variable. If you are not using Oracle ASM, then leave the value for this password variable blank.

Oracle strongly recommends that you maintain security with a password response file:

- Permissions on the response file should be set to 600.

- The owner of the response file should be the installation owner user, with the group set to the central inventory (`oraInventory`) group.

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-the-configtoolallcommands-script.md)
