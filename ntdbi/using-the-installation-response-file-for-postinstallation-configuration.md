## Using the Installation Response File for Postinstallation Configuration

Starting with Oracle Database 12c release 2 (12.2), you can use the response file created during installation to also complete postinstallation configuration.

Run the installer with the `-executeConfigTools` option to configure configuration assistants after installing Oracle Grid Infrastructure or Oracle Database. You can use the response file located at `%ORACLE_HOME%\install\response\grid_``timestamp``.rsp` to obtain the passwords required to run the configuration tools. You must update the response file with the required passwords before running the `-executeConfigTools` command.

Oracle strongly recommends that you maintain security with a password response file. The owner of the response file must be the installation owner user.

Example C-3 Response File Passwords for Oracle Grid Infrastructure

    oracle.install.crs.config.ipmi.bmcPassword=password
    oracle.install.asm.SYSASMPassword=GRID_HOME\gridSetup.bat -executeConfigTools -responseFile %ORACLE_HOME%\install\response\grid_time_stamp.rsporacle.install.asm.monitorPassword=password
    oracle.install.config.emAdminPassword=password
    oracle.install.OracleHomeUserPassword=password

If you do not have a BMC card, or you do not want to enable IPMI, then leave the `ipmi.bmcPassword` input field blank.

If you do not want to enable Oracle Enterprise Manager for management, then leave the `emAdminPassword` password field blank.

If you did not specify an Oracle Home user for the Oracle Grid Infrastructure installation, then leave the `OracleHomeUserPassword` field blank.

Example C-4 Response File Passwords for Oracle Grid Infrastructure for a Standalone Server (Oracle Restart)

    oracle.install.asm.SYSASMPassword=password
    oracle.install.asm.monitorPassword=password
    oracle.install.config.emAdminPassword=password
    oracle.install.OracleHomeUserPassword=password

If you do not want to enable Oracle Enterprise Manager for management, then leave the `emAdminPassword` password field blank.

If you did not specify an Oracle Home user for the Oracle Grid Infrastructure for a Standalone Server (Oracle Restart) installation, then leave the `OracleHomeUserPassword` field blank.

Example C-5 Response File Passwords for Oracle Database

This example illustrates the passwords to specify for use with the database configuration assistants.

    oracle.install.db.config.starterdb.password.SYS=password
    oracle.install.db.config.starterdb.password.SYSTEM=password
    oracle.install.db.config.starterdb.password.DBSNMP=password
    oracle.install.db.config.starterdb.password.PDBADMIN=password
    oracle.install.db.config.starterdb.emAdminPassword=password
    oracle.install.db.config.asm.ASMSNMPPassword=password
    oracle.install.OracleHomeUserPassword=password

You can also specify `oracle.install.db.config.starterdb.password.ALL=``password` to use the same password for all database users.

Oracle Database configuration assistants require the SYS, SYSTEM, and DBSNMP passwords for use with Oracle Database Configuration Assistant (DBCA). Specify the following passwords, depending on your system configuration:

- If the database uses Oracle ASM for storage, then you must specify a password for the `ASMSNMPPassword` variable. If you are not using Oracle ASM, then leave the value for this password variable blank.

- If you create a multitenant container database (CDB) with one or more pluggable databases (PDBs), then you must specify a password for the `PDBADMIN` variable. If you are not using Oracle ASM, then leave the value for this password variable blank.

- If you did not specify an Oracle Home user for the Oracle Database installation, then leave the `OracleHomeUserPassword` field blank.

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](advance.md)
