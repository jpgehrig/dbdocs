## Creating a Password Response File

Use these steps to create a password response file for use with the `configToolAllCommands` script..

1.  Create a response file that has a name of the format `filename``.properties`.
2.  Open the file with a text editor, and cut and paste the sample password file contents, as shown in the example below, modifying as needed.
3.  If the file is stored on a volume formatted for Windows New Technology File System (NTFS), then modify the security permissions to secure the file.

Example A-4 Sample Password response file for Oracle Grid Infrastructure Installation

Oracle Grid Infrastructure requires passwords for Oracle Automatic Storage Management Configuration Assistant (ASMCA), and for Intelligent Platform Management Interface Configuration Assistant (IPMICA) if you have a baseboard management controller (BMC) card and you want to enable this feature. Also, if you specified an Oracle Home user for the Oracle Grid Infrastructure installation, you must specify the password as the Windows Service user password. Provide the following response file:

    oracle.crs|S_ASMPASSWORD=password
    oracle.crs|S_OMSPASSWORD=password
    oracle.crs|S_ASMMONITORPASSWORD=password
    oracle.crs|S_BMCPASSWORD=password
    oracle.crs|S_WINSERVICEUSERPASSWORD=password

If you do not have a BMC card, or you do not want to enable Intelligent Platform Management Interface (IPMI), then leave the `S_BMCPASSWORD` input field blank.

**Note:**

If you are upgrading Oracle ASM 11g Release 1 or earlier releases, then you only need to provide the input field for `oracle.assistants.asm|S_ASMMONITORPASSWORD`.

Example A-5 Sample Password response file for Oracle Real Application Clusters

Oracle Database configuration requires the SYS, SYSTEM, and DBSNMP passwords for use with Database Configuration Assistant (DBCA). The `S_ASMSNMPPASSWORD` response is necessary only if the database is using Oracle ASM for storage. Similarly, the `S_PDBADMINPASSWORD` password is necessary only if you create a multitenant container database (CDB) with one or more pluggable databases (PDBs). Also, if you selected to configure Oracle Enterprise Manager Cloud Control, then you must provide the password for the Oracle software installation owner for `S_EMADMINPASSWORD`, similar to the following example, where the phrase password represents the password string:

    oracle.server|S_SYSPASSWORD=password
    oracle.server|S_SYSTEMPASSWORD=password
    oracle.server|S_DBSNMPPASSWORD=password
    oracle.server|S_PDBADMINPASSWORD=password
    oracle.server|S_EMADMINPASSWORD=password
    oracle.server|S_ASMSNMPPASSWORD=password
    oracle.server|S_WINSERVICEUSERPASSWORD=password

If you do not want to enable Oracle Enterprise Manager for Oracle ASM, then leave those password fields blank.

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstall-config-using-configtoolallcommands-script.md)
