## Oracle Configuration Manager Postinstallation Configuration for Oracle RAC

If you have installed Oracle Configuration Manager, then you must run a script to create a database account to collect database configuration collections.

You must create this database account in both Connected and Disconnected modes. The database account stores the PL/SQL procedures that collect the configuration information, and the account owns the database management system (DBMS) job that performs the collection. After the account has been set up, the account is locked because login privileges are no longer required.

- Run the script `installCCRSQL.exe`.
  The script `installCCRSQL.exe` creates an Oracle Configuration Manager user and loads the PL/SQL procedure into the database defined by the `ORACLE_SID` environment variable. For Oracle RAC, you must run the database script against only one instance, such as the local instance on which you performed the installation. However, Oracle Configuration Manager must be installed in all instance homes.

  You can also specify the database SID by using the `-s` option in the command line, as in the following example, where the SID is `orcl`:

      %ORACLE_HOME%/ccr/admin/scripts/installCCRSQL.exe collectconfig -s orcl

  By default, the connection to the database is through OS authentication, "`/as sysdba`." To specify a different SYSDBA user and password, you can use these options:

  `-r ``SYSDBA-USER`: The login name of the SYSDBA user

  `-p ``SYSDBA-PASSWORD`: The password for the SYSDBA user

  **Note:**

  - If you specify the user name without specifying the password (with the `-p` parameter), then the script prompts you to enter the password.

  - If you specify only the password without specifying the user name, then the script uses the user SYS by default.

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
