## Configuring Oracle Database Security Settings

Use Oracle Database Configuration Assistant (DBCA) commands to change security settings after installation.

To enable or disable the database security configuration after installation, you must use command-line Oracle Database Configuration Assistant (DBCA) options. By design, the DBCA graphical user interface (GUI) does not have the option to enable or disable secure configuration. For example, to enable the security settings after installation, use a command of the following form, where `myRACdb1.example.com` is the either the name of the local database instance, or the value set for the initialization parameter `DB_UNIQUE_NAME`:

    dbca –configureDatabase –sourceDB myRACdb1.example.com -SID
    –enableSecurityConfiguration true

**Parent topic:** [Product-Specific Postinstallation Tasks](product-specific-postinstallation-tasks.md)
