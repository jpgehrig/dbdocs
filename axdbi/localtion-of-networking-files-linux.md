Learn about the search order and location of networking files like `sqlnet.ora`, `tnsnames.ora`, or `listener.ora` in a read-only Oracle home.

The networking directories `network/admin`, `network/trace`, and `network/log` are located in the ORACLE_BASE_HOME directory. In a read/write ORACLE_HOME the networking directories appear to be in ORACLE_HOME because ORACLE_BASE_HOME is co-located with ORACLE_HOME, whereas in a read-only ORACLE_HOME the networking directories are located in `ORACLE_BASE/homes/HOME_NAME`.

### tnsnames.ora

The order for checking the `tnsnames.ora` file in a read-only Oracle home is:

1.  The directory specified by the `TNS_ADMIN` environment variable.
2.  The `/etc` directory.
3.  The `ORACLE_BASE_HOME/network/admin` directory.
4.  The `ORACLE_HOME/network/admin` directory.

### sqlnet.ora

The order for checking the `sqlnet.ora` file in a read-only Oracle home is:

1.  The directory specified by the `TNS_ADMIN` environment variable.
2.  The `ORACLE_BASE_HOME/network/admin` directory.
3.  The `ORACLE_HOME/network/admin` directory.

### Password Files

The search order for password files for Oracle homes is `ORACLE_BASE_CONFIG/dbs` followed by `ORACLE_HOME/dbs`. This helps prioritize to search for the password file outside of ORACLE_HOME when read-only Oracle home is enabled.

**Related Topics**

- [Overview of Local Naming Parameters](../netrf/local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** [Evolution of Oracle Homes](understanding-read-only-oracle-homes.md)
