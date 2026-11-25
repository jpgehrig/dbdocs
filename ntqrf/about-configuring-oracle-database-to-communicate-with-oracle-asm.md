Oracle Databases that use Oracle Automatic Storage Management (Oracle ASM) and the databases that are managed by Oracle Grid infrastructure must use Windows native authentication, which is enabled by default.

To ensure that it is, check that the `sqlnet.ora` file, by default located in `ORACLE_HOME``\network\admin`, has NTS enabled. For example:

    sqlnet.authentication_services=(NTS)

**See Also:**

[About Windows Authentication Protocols](about-windows-authentication-protocols.md)

**Parent topic:** [Oracle Net Services Configuration on Windows](net-services-configuration-on-windows.md)
