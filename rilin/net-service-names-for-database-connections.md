## Net Service Names for Database Connections

Clients that connect to any instance of Oracle RAC use the SCAN in the connect descriptor. You can also use net service names to connect to Oracle RAC.

If you use DBCA to create an Oracle RAC database that is a multitenant container database (CDB), then DBCA creates a database service that has the same name as the database. The default database service created by DBCA enables Oracle Enterprise Manager to discover an Oracle RAC database, and should not be used for client connections. Clients that use this database service can connect to any database instance for the Oracle RAC CDB. However, if you use DBCA to add a pluggable database (PDB) to an existing CDB, then DBCA does not create a database service for the new PDB.

The net service name does not require a fully qualified domain name for the server on which a database, database instance, or listener runs. SCANs are resolved by the DNS or GNS, which returns three addresses to the client. The client then submits connection requests to each address in succession until a connection is made.

Example 6-2 Example Net Service Name Entry for a Database Connection

This example shows a connect descriptor that is used in a `tnsnames.ora` file. The connect identifier in this case is the same as the cluster domain, `mycluster.example.com`. Instead of specifying the address for an individual server, Virtual Internet Protocol (VIP) address, or a cluster node name, the connect descriptor uses the SCAN, which is `myscan.mycluster.example.com`.

    mycluster.example.com =
      (DESCRIPTION =
        (ADDRESS = (PROTOCOL = TCP)(HOST = host=myscan.mycluster.example.com)
          (PORT = 1522))
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = myApp)
        )
      )

Oracle Clusterware resolves connection requests that use the net service name `mycluster.example.com` to any of the database instances of the `mycluster` database that run the `myApp` database service. The specific cluster node on which the instance is running is invisible to the client.

**Parent topic:** [Net Service Names Created by DBCA](net-service-names-created-by-dbca.md)
