## Configuring Oracle Database to Communicate with Oracle Automatic Storage Management

On Windows, Oracle Database installations that use Oracle Automatic Storage Management must use Windows native authentication.

By default, Windows native authentication is enabled. To ensure that Windows native authentication is enabled, check the `sqlnet.ora` file, which by default is located in `ORACLE_HOME``\network\admin`, and ensure that it has NTS enabled. For example:

    sqlnet.authentication_services=(NTS)

**Parent topic:** [Configuring Oracle Components](configuring-oracle-components.md)
