## Managing Multiple Listeners for an Oracle RAC Database

In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage the Oracle listeners for the databases.

- Use the `lsnrctl` executable located in the Grid home to administer Oracle Database 19c local and SCAN listeners.
  Do not attempt to use the `lsnrctl` executables from Oracle home locations for earlier releases, because they cannot be used with Oracle Database 19c.
- Use SRVCTL and the `setenv` command to modify the value of `TNS_ADMIN` for each listener.
  For listeners not managed by Oracle Clusterware, you can use a nondefault location for the `listener.ora` file by setting the `TNS_ADMIN` environment variable or registry value to point to the directory that contains the Oracle Net Services configuration files.

**Parent topic:** [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
