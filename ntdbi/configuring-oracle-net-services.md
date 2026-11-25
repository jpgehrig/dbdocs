## Configuring Oracle Net Services

Describes how to configure Oracle Net Services.

If you have a previous release of Oracle software installed on this system, you can copy information from the Oracle Net `tnsnames.ora` and `listener.ora` configuration files from the previous release to the corresponding files for the new release.

**Note:**

The default location for the `tnsnames.ora` and `listener.ora` files is the `ORACLE_BASE\ORACLE_HOME``\network\admin\` directory.

### Modifying the listener.ora File

If you are upgrading from a previous release of Oracle Database, Oracle recommends that you use the current release of Oracle Net listener instead of the listener from the previous release.

If you have referenced the previous Oracle home directory names in the static listener information, then these directory names must be modified before the `listener.ora` file can be used in the 19c environment.

To use the listener from the current release, you must copy static service information from the `listener.ora` file from the previous release to the version of that file used by the new release.

For any database instances earlier than release 8.0.3, add static service information to the `listener.ora` file. Oracle Database releases later than release 8.0.3 do not require static service information.

### Modifying the tnsnames.ora File

Unless you are using a central `tnsnames.ora` file, copy Oracle Net service names and connect descriptors from the previous release `tnsnames.ora` file to the version of that file used by the new release.

If necessary, you can also add the connection information for additional database instances to the new file.

**Parent topic:** [Configuring Oracle Components](configuring-oracle-components.md)
