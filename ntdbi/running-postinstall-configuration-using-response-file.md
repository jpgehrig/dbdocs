## Running Postinstallation Configuration Using Response File

Use this procedure to run postinstallation configuration using response file.

To run configuration assistants with the `executeConfigTools` script:

1.  Create a response file using the syntax filename.properties. For example:

        C:\> copy nul cfgrsp.properties

2.  Open the file with a text editor, and cut and paste the password template, modifying as needed.

3.  Secure the cfgrsp.properties file by changing permissions in Properties page. Right-click the file to open the Properties page. Select the Security tab, click the Edit button, select a group or user, then select Deny check box against Read permissions to remove read access for unwanted users.

4.  Change directory to `ORACLE_HOME\cfgtoollogs`

5.  Before running `configToolAllCommands`, rename it using the following command:

    `copy configToolAllCommands configToolAllCommands.bat`

6.  Run the configuration script using the following syntax:

    `configToolAllCommands.bat RESPONSE_FILE=\path\name.properties`

    for example:

        C:\> configToolAllCommands.bat RESPONSE_FILE=C:\oracle\cfgrsp.properties

Example C-1 Password response file for Oracle Grid Infrastructure for a Standalone Server

Oracle Grid Infrastructure requires passwords for Oracle Automatic Storage Management Configuration Assistant (ASMCA), and for Intelligent Platform Management Interface Configuration Assistant (IPMICA) if you have a BMC card and you want to enable this feature. Provide the following response file:

    oracle.crs|S_ASMPASSWORD=password
    oracle.crs|S_ASMMONITORPASSWORD=password
    oracle.crs|S_OMSPASSWORD=password
    oracle.crs|S_BMCPASSWORD=password
    oracle.crs|S_WINSERVICEUSERPASSWORD=password

Example C-2 Password response file for Oracle Database

Oracle Database configuration requires the `SYS`, `SYSTEM`, and `DBSNMP` passwords for use with Database Configuration Assistant (DBCA). The `S_ASMSNMPPASSWORD` password is necessary only if the database is using Oracle ASM for storage. Similarly, the `S_PDBADMINPASSWORD` password is necessary only if you create a multitenant container database (CDB) with one or more pluggable databases (PDBs). Also, if you select configure Oracle Enterprise Manager, then provide the password for the Oracle software installation owner for the `S_EMADMINPASSWORD` password.

    oracle.server|S_SYSPASSWORD=password
    oracle.server|S_SYSTEMPASSWORD=password
    oracle.server|S_DBSNMPPASSWORD=password
    oracle.server|S_PDBADMINPASSWORD=password
    oracle.server|S_EMADMINPASSWORD=password
    oracle.server|S_ASMSNMPPASSWORD=password

If you do not want to enable Oracle Enterprise Manager or Oracle ASM, then leave those password fields blank.

**Parent topic:** [Postinstallation Configuration Using Response File Created During Installation](postinstallation-configuration-using-response-file-created-during-installation.md)
