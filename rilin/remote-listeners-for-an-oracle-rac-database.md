## Remote Listeners for an Oracle RAC Database

A remote listener is a listener residing on one computer that redirects connections to a database instance on another computer. For example, SCAN listeners are remote listeners.

**Caution:**

Do not modify the `REMOTE_REGISTRATION_ADDRESS` parameter for your Oracle RAC deployment. The `REMOTE_REGISTRATION_ADDRESS` parameter is set by default to protect against TNS poisoning. Refer to [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for more information about `REMOTE_REGISTRATION_ADDRESS` parameter.

In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage the Oracle listeners for the databases.

**Related Topics**

- [Net Service Names and the tnsnames.ora File](net-service-names-and-the-tnsnames-ora-file.md)

**See Also:**

- Net Service Names and the tnsnames.ora for more information about listener associations defined in the `tnsnames.ora` file

- [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for more information about the `listener.ora` file

- [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for an overview of listeners

**Parent topic:** [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
