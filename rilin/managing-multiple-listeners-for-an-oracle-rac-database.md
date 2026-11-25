## Managing Multiple Listeners for an Oracle RAC Database

Review to understand how to use `SRVCTL` and `TNS_ADMIN` to manage listeners

To administer Oracle Database 19c local and SCAN listeners using the `lsnrctl` command, set your ORACLE_HOME environment variable to the path for the Grid home. Do not attempt to use the `lsnrctl` commands from Oracle home locations for earlier releases, because they cannot be used with Oracle Database 19c.

For listeners not managed by Oracle Clusterware, you can use a non-default location for the `listener.ora` file by setting the TNS_ADMIN environment variable or registry value to point to the directory that contains the Oracle Net Services configuration files. To use a non-default location for a listener managed by Oracle Clusterware, you must use `SRVCTL` and the `setenv` command to modify the value of TNS_ADMIN for each listener.

**Parent topic:** [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
