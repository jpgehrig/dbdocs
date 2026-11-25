## Creating a Password Response File

Use these steps to create a password response file for use with the configuration assistants.

1.  Create a response file that has a name of the format `filename``.properties`.
2.  Open the file with a text editor, and cut and paste the sample password file contents, as shown in the example below, modifying as needed.
3.  If the file is stored on a volume formatted for Windows New Technology File System (NTFS), then modify the security permissions to secure the file.

Example A-5 Sample Password Response File for Oracle RAC Databases

This example provides a template for a password response file to use with the database configuration assistants.

    oracle.install.db.config.starterdb.password.SYS=password
    oracle.install.db.config.starterdb.password.SYSTEM=password
    oracle.install.db.config.starterdb.password.DBSNMP=password
    oracle.install.db.config.starterdb.password.PDBADMIN=password
    oracle.install.db.config.starterdb.emAdminPassword=password
    oracle.install.db.config.asm.ASMSNMPPassword=password
    oracle.install.db.config.OracleHomeUserPassword=password

If you do not want to enable access for Oracle Enterprise Manager or Oracle ASM, then leave those password fields blank.

**Parent topic:** [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstallation-configuration-using-a-script.md)
