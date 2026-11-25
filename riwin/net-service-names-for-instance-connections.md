## Net Service Names for Instance Connections

Clients that connect to a particular instance of the database use the net service name for the instance.

Example 6-4 Example Net Service Name Entry for an Instance Connection

In this example, the connect identifier is the same as the instance name, `mycluster1.example.com`. The connect descriptor uses the SCAN to locate the instance within the cluster. Clients connecting to the net service name `mycluster1.example.com` are connected to the `mycluster1` database instance of the `mycluster` database. Oracle Clusterware resolves that connection to the cluster node on which the instance is running. The specific cluster node on which the instance is running is invisible to the client.

    mycluster1.example.com=
      (DESCRIPTION=
        (ADDRESS=(PROTOCOL=TCP)(HOST=myscan.mycluster.example.com)(PORT=1521))
        (CONNECT_DATA=
          (SERVICE_NAME=mycluster.example.com)
          (INSTANCE_NAME=mycluster1)
        )
      )

**Parent topic:** [Net Service Names Created by DBCA](net-service-names-created-by-dbca.md)
