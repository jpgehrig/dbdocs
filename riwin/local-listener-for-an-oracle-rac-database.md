## Local Listener for an Oracle RAC Database

The local listener, or default listener, is located in the Grid home when you have Oracle Grid Infrastructure installed.

The `listener.ora` file is located in the `Grid_home``\network\admin` directory. If needed, you can edit the `listener.ora` file for the Grid home listeners to define listener parameters for node and SCAN listeners. Do not modify the endpoints because these are automatically managed by the listener agent.

During Oracle Database creation, the `LOCAL_LISTENER` parameter is automatically configured to point to the local listener for the database. You can set a value manually for `LOCAL_LISTENER`. If you modify the value of the `LOCAL_LISTENER` parameter, then the Database Agent process does not automatically update this value. Oracle recommends that you leave the parameter unset so that the Database Agent process can maintain it automatically. If you do not set `LOCAL_LISTENER`, then the Database Agent process automatically updates the database associated with the local listener in the Grid home, even when the ports or IP address of that listener are changed.

**See Also:**

- "[Net Service Names and the tnsnames.ora File](net-service-names-and-the-tnsnames-ora-file.md)" for more information about listener associations defined in the `tnsnames.ora` file

- [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for more information about the `listener.ora` file

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for information about registering information with a local listener

**Parent topic:** [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
