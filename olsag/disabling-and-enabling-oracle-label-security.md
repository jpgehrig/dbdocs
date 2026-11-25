You can disable and enable Oracle Label Security as necessary.

**Note:**

Oracle does not support the deinstallation of Oracle Label Security.

- When You Must Disable Oracle Label Security
  You may need to disable Oracle Label Security to perform upgrade tasks or correct erroneous configurations.
- Disabling Oracle Label Security
  If Oracle Database Vault has been enabled, then do not disable Oracle Label Security.
- Enabling Oracle Label Security
  You can enable Oracle Label Security in SQL\*Plus.

**Parent topic:** [Appendixes](part4.md)

### A.1 When You Must Disable Oracle Label Security

You may need to disable Oracle Label Security to perform upgrade tasks or correct erroneous configurations.

Another reason for disabling Oracle Label Security is if you want to test an application without enforcing Oracle Label Security. You can reenable Oracle Label Security after you complete the tasks.

**Related Topics**

- [Checking if Oracle Label Security Has Been Registered and Enabled](getting-started-with-oracle-label-security.md)

**Parent topic:** Disabling and Enabling Oracle Label Security

### A.2 Disabling Oracle Label Security

If Oracle Database Vault has been enabled, then do not disable Oracle Label Security.

See [Oracle Database Vault Administrator's Guide](../dvadm/index.md) to find if Database Vault has been enabled.

To disable Oracle Label Security:

1.  Log into the database instance as user `SYS` or a user who has been granted the `LBAC_DBA` role.
    For example:

        sqlplus psmith_ols -- Or, psmith_ols@hrpdb for the hrpdb pluggable database (PDB)
        Enterp password: password
2.  Run the following procedure:
        EXEC LBACSYS.OLS_ENFORCEMENT.DISABLE_OLS;
3.  Restart the database.
    For example:

        CONNECT SYS AS SYSOPER
        Enter password: password

        SHUTDOWN IMMEDIATE
        STARTUP
4.  For Oracle Real Application Cluster (Oracle RAC) environment or a multitenant environment, repeat these steps for each Oracle RAC node or PDB on which you enabled Oracle Label Security.

**Parent topic:** Disabling and Enabling Oracle Label Security

### A.3 Enabling Oracle Label Security

You can enable Oracle Label Security in SQL\*Plus.

1.  Log into the database instance as user `SYS` or a user who has been granted the `LBAC_DBA` role.
    For example:

        sqlplus psmith_ols -- Or, psmith_ols@hrpdb for the hrpdb PDB
        Enterp password: password
2.  Run the following procedure:
        EXEC LBACSYS.OLS_ENFORCEMENT.ENABLE_OLS;
3.  Restart the database.
    For example:

        CONNECT SYS AS SYSOPER
        Enter password: password

        SHUTDOWN IMMEDIATE
        STARTUP
4.  For Oracle Real Application Cluster (Oracle RAC) environment or a multitenant environment, repeat these steps for each Oracle RAC node or PDB on which you disabled Oracle Label Security.

**Parent topic:** Disabling and Enabling Oracle Label Security
