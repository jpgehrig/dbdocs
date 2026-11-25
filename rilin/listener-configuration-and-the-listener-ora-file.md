## Listener Configuration and the listener.ora File

In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage Oracle listeners for Oracle Databases.

**Note:**

If you enable GNS, then you do not have to manually configure the listener.

- [Local Listener for an Oracle RAC Database](local-listener-for-an-oracle-rac-database.md)
  The local listener, or default listener, is located in the Grid home when you have Oracle Grid Infrastructure installed. The `listener.ora` file is located in the `Grid_home``/network/admin` directory.
- [Remote Listeners for an Oracle RAC Database](remote-listeners-for-an-oracle-rac-database.md)
  A remote listener is a listener residing on one computer that redirects connections to a database instance on another computer. For example, SCAN listeners are remote listeners.
- [Managing Multiple Listeners for an Oracle RAC Database](managing-multiple-listeners-for-an-oracle-rac-database.md)
  Review to understand how to use `SRVCTL` and `TNS_ADMIN` to manage listeners
- [How Oracle Database Uses the Listener File (listener.ora)](how-oracle-database-uses-the-listener-file-listener-ora.md)
  The `listener.ora` file is the configuration file for a listener. It can include the protocol addresses it is accepting connection requests on, a list of the database and other services it is listening for, and control parameters used by the listener.

**Parent topic:** [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
