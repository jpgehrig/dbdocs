## Remote Listeners for an Oracle RAC Database

A remote listener is a listener residing on one computer that redirects connections to a database instance on another computer.

For example, SCAN listeners are remote listeners. In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage the Oracle listeners for the databases.

**See Also:**

- "[Net Service Names and the tnsnames.ora File](net-service-names-and-the-tnsnames-ora-file.md)" for more information about listener associations defined in the `tnsnames.ora` file

- [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for more information about the `listener.ora` file

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for information about registering information with a remote listener

**Parent topic:** [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
