## About Listener Configuration for an Oracle RAC Database

An Oracle Database receives connection requests through the local listener.

The local listener brokers a client request, handing off the request to the server. The listener is configured with a protocol address, and clients configured with the same protocol address can send connection requests to the listener. When a connection is established, the client and Oracle database communicate directly with one another.

The local listener, or default listener, is located in the Grid home when you have Oracle Grid Infrastructure installed. Local listeners are configured to respond to database connection requests, and to non-database connection requests, such as external procedures or Oracle XML Database (XDB) requests. When the database starts, the Database Agent process (`oraagent`, previously known as `racgimon`) sets the LOCAL_LISTENER parameter to a connect descriptor that does not require an Oracle Net service name. The value for LOCAL_LISTENER is computed to be the endpoints of the Grid home listeners.

You can configure multiple Oracle Database listeners, each with a unique name, in one `listener.ora` file. Multiple listener configurations for database listeners are possible because each of the top-level configuration parameters has a suffix of the listener name or is the listener name itself. To configure a database to register with multiple local listeners, you must manually modify the LOCAL_LISTENER parameter.

**Note:**

Oracle recommends running only one listener for each node in most customer environments.

For an Oracle RAC database, the database parameter REMOTE_LISTENER identifies the SCAN listeners. The database registers with the local and SCAN listeners by using the connect description information contained in these parameters. Oracle Database 11g Release 2 and later instances only register with SCAN listeners as remote listeners. Upgraded databases register with SCAN listeners as remote listeners, and also continue to register with all node listeners.

**Caution:**

Do not modify the `REMOTE_REGISTRATION_ADDRESS` parameter for your Oracle RAC deployment. The `REMOTE_REGISTRATION_ADDRESS` parameter is set by default to protect against TNS poisoning. Refer to [Oracle Database Net Services Reference](../netrf/oracle-net-listener-parameters-in-listener-ora.md) for more information about `REMOTE_REGISTRATION_ADDRESS` parameter.

The REMOTE_LISTENER parameter for an Oracle RAC database is always set to the SCAN address. For example, if the SCAN for the cluster is `myscan`, and the GNS subdomain for the cluster is `mycluster.example.com`, then the REMOTE_LISTENER parameter has the following value:

    myscan.mycluster.example.com:1521

**Note:**

Do not set the REMOTE_LISTENER parameter for an Oracle RAC database to an Oracle Net alias that has a single address that uses the SCAN for the host name (`HOST=``scan`).

**Parent topic:** [Oracle Net Services Configuration for Oracle RAC Databases](oracle-net-services-configuration-for-oracle-rac-databases.md)
