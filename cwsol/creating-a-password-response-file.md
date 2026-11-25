You can create a password response file and use it with configuration assistants to perform silent installation.

Perform the following steps to create a password response file:

1.  Create a response file that has a name of the format filename.`properties`, for example:
        $ touch pwdrsp.properties
2.  Open the file with a text editor, and cut and paste the sample password file contents, as shown in the examples, modifying as needed.
3.  Change permissions to secure the password response file. For example:
        $ ls -al pwdrsp.properties
        -rw------- 1 oracle oinstall 0 Apr 30 17:30 pwdrsp.properties

Example A-4 Password response file for Oracle Grid Infrastructure (`grid` user)

    grid.crs|S_ASMPASSWORD=password
    grid.crs|S_OMSPASSWORD=password
    grid.crs|S_BMCPASSWORD=password
    grid.crs|S_ASMMONITORPASSWORD=password

If you do not have a BMC card, or you do not want to enable IPMI, then leave the `S_BMCPASSWORD` input field blank.

Example A-5 Password response file for Oracle Grid Infrastructure for a Standalone Server (`oracle` user)

    oracle.crs|S_ASMPASSWORD=password
    oracle.crs|S_OMSPASSWORD=password
    oracle.crs|S_ASMMONITORPASSWORD=password

Example A-6 Password response file for Oracle Database (`oracle` user)

This example provides a template for a password response file to use with the database configuration assistants.

    oracle.server|S_SYSPASSWORD=password
    oracle.server|S_SYSTEMPASSWORD=password
    oracle.server|S_EMADMINPASSWORD=password
    oracle.server|S_DBSNMPPASSWORD=password
    oracle.server|S_ASMSNMPPASSWORD=password
    oracle.server|S_PDBADMINPASSWORD=password

If you do not want to enable Oracle Enterprise Manager for management, then leave those password fields blank.

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-configtoolallcommands-script.md)
