## Net Services Profile File (sqlnet.ora)

Oracle Universal Installer starts Oracle Net Configuration Assistant (NETCA) after the database software is installed. NETCA creates the Oracle Net Services profile, or the `sqlnet.ora` file.

In an Oracle Grid Infrastructure installation, the `sqlnet.ora` file is located in the `Grid_home``\network\admin` directory by default.

For the local listener for the Oracle RAC database instance, the default location of the `sqlnet.ora` file is `%ORACLE_HOME%\network\admin` directory. In this directory there is a default `sqlnet.ora` file. Also, you can find a sample `sqlnet.ora` file in the subdirectory `sample`.

During installation of the Oracle RAC software, NETCA creates the following entries in the `sqlnet.ora` file, where `%ORACLE_BASE%` is the path to the Oracle base directory for the Oracle RAC installation:

    NAMES.DIRECTORY_PATH=(TNSNAMES, EZCONNECT)
    ADR_BASE =%ORACLE_BASE%

The `AUTHENTICATION_SERVICES` parameter (not shown in the above example) specifies the method by which users are authenticated for database access. The value `NTS` indicates that Microsoft Windows native authentication should be used to authorize access to the database. Oracle Databases that use Oracle Automatic Storage Management (Oracle ASM) and the databases that are managed by Oracle Grid infrastructure must use Windows native authentication, which is enabled by default.

The parameter `NAMES.DIRECTORY_PATH` specifies the priority order of the naming methods to use to resolve connect identifiers to connect descriptors. The `ADR_BASE` parameter specifies the base directory into which tracing and logging incidents are stored when Automatic Diagnostic Repository (ADR) is enabled for the database.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md) for more information about the `sqlnet.ora` file

- [Oracle Database Concepts](../cncpt/topics-for-database-administrators-and-developers.md) for more information about authentication

- [Oracle Database Client Installation Guide for Microsoft Windows](../ntcli/index.md) for more information about configuring clients for database connectivity

- [Oracle Database Administrator's Guide](../admin/diagnosing-and-resolving-problems.md) for more information about ADR

**Parent topic:** [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
