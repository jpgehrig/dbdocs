Workload management includes load balancing, enabling clients for Oracle Real Application Clusters (Oracle RAC), distributed transaction processing, and services.

This chapter includes the following topics:

- Connection Load Balancing

- Load Balancing Advisory

- Enabling Clients for Oracle RAC

- Distributed Transaction Processing in Oracle RAC

- Automatic Workload Repository

- Measuring Performance by Service Using the Automatic Workload Repository

- Automatic Workload Repository Service Thresholds and Alerts

- Using Oracle Services

- Service Deployment Options

- Administering Services

- Global Services

- Connecting to a Service: An Example

### Connection Load Balancing

Oracle Net Services provides the ability to distribute client connections across the instances in an Oracle RAC configuration.

There are two types of load balancing that you can implement: client-side and server-side load balancing. Client-side load balancing distributes the connection requests across the listeners, independently at each client. With server-side load balancing, the SCAN listener directs a connection request to the best instance currently providing the service, based on the `-clbgoal` and `-rlbgoal` settings for the service.

The SCAN listener is aware of the HTTP protocol so that it can redirect HTTP clients to the appropriate handler, which can reside on different nodes in the cluster than the node on which the SCAN listener resides.

In an Oracle RAC database, client connections should use both types of connection load balancing.

- Server-Side Load Balancing

- Generic Database Clients

- Client-Side Load Balancing

- Client-Side Connection Configuration for Older Clients

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/identifying-and-accessing-database.md)

#### Server-Side Load Balancing

When you create an Oracle RAC database with DBCA, it automatically:

- Configures and enables server-side load balancing

- Creates a sample client-side load balancing connection definition in the `tnsnames.ora` file on the server

The Oracle Clusterware Database Agent is responsible for managing the `LISTENER_NETWORKS` parameter.

**Note:**

Note: If you set the `REMOTE_LISTENER` parameter manually, then set this parameter to `scan_name``:``scan_port`.

FAN, Fast Connection Failover, and the load balancing advisory depend on an accurate connection load balancing configuration that includes setting the connection load balancing goal for the service. You can use a goal of either `LONG` or `SHORT` for connection load balancing. These goals have the following characteristics:

- SHORT: Use the `SHORT` connection load balancing method for applications that use run-time load balancing. When using connection pools that are integrated with Load Balancing Advisory, set the `CLB_GOAL` to `SHORT`. The following example modifies the service known as `oltpapp`, using SRVCTL to set the connection load balancing goal to `SHORT`:

      $ srvctl modify service -db db_unique_name -service oltpapp -clbgoal SHORT

- LONG: Use the `LONG` connection load balancing method if run-time load balancing is not required. This is typical for batch operations. `LONG` is the default connection load balancing goal. The following is an example of modifying a service, `batchconn`, using SRVCTL to define the connection load balancing goal for long-lived sessions:

      $ srvctl modify service -db db_unique_name -service batchconn -clbgoal LONG

#### Generic Database Clients

Oracle Net Services enables you to add the `CONNECT_TIMEOUT`, `RETRY_COUNT`, and `TRANSPORT_CONNECT_TIMEOUT` parameters to the `tnsnames.ora` connection string.

For example, when using SCAN addresses for the remote listeners at the database:

    jdbc:oracle:thin:@(DESCRIPTION =
     (TRANSPORT_CONNECT_TIMEOUT=3)(CONNECT_TIMEOUT=60)
     (RETRY_COUNT=3)(FAILOVER=ON)
     (ADDRESS_LIST =(ADDRESS=(PROTOCOL=tcp)
      (HOST=CLOUD-SCANVIP.example.com)(PORT=5221))
     (CONNECT_DATA=(SERVICE_NAME=orcl)))
    Remote_listeners=CLOUD-SCANVIP.example.com:5221

For example, when using remote listeners pointing to VIPs at the database:

    jdbc:oracle:thin:@(DESCRIPTION =
     (TRANSPORT_CONNECT_TIMEOUT=3)
     (CONNECT_TIMEOUT=60)(RETRY_COUNT=20)
     (RETRY_DELAY=3)(FAILOVER=ON)
     (ADDRESS_LIST=
     (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP1)(PORT=1521) )
     (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP2)(PORT=1521) )
     (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP3)(PORT=1521) ))
     (CONNECT_DATA=(SERVICE_NAME=GOLD)))

The value of these parameters is expressed in seconds. In the preceding examples, Oracle Net waits for 60 seconds for each full connection to receive a response, after which it assumes that a failure occurred and retries the next address in the `ADDRESS_LIST`. Oracle Net retries the address list 3 times before it returns a failure message to the client. The `TRANSPORT_CONNECT_TIMEOUT` parameter establishes the time to wait to establish a TCP connection to the database server.

For SCAN, Oracle Net Services tries all three addresses (returned by the SCAN address) before returning a failure to the client. EZConnect with SCAN includes this connection failover feature.

This behavior is called Oracle Net connection failover. If an error is returned from a chosen address in the list, then Oracle Net Services tries the next address in the list until it is either successful or it has exhausted all addresses in its list.

#### Client-Side Connection Configuration for Older Clients

In addition to client-side load balancing, Oracle Net Services include connection failover. If an error is returned from the chosen address in the list, Oracle Net Services tries the next address in the list until it is either successful or it has exhausted all addresses in its list. For SCAN, Oracle Net Services tries all three addresses before returning a failure to the client. EZConnect with SCAN includes this connection failover feature.

To increase availability, you can specify a timeout that specifies how long Oracle Net waits for a response from the listener before returning an error. The method of setting this timeout parameter depends on the type of client access. Oracle Net maintains these parameters for backward compatibility.

This section includes the following topics:

- JDBC-Thin Clients

- OCI Clients

##### JDBC-Thin Clients

You can avoid delays by setting the `oracle.net.ns.SQLnetDef.TCP_CONNTIMEOUT_STR` property, as follows:

    Properties prop = new Properties ();
    prop.put (oracle.net.ns.SQLnetDef.TCP_CONNTIMEOUT_STR,
    "" + (1 * 1000)); // 1 second
    dbPools[ poolIndex ].setConnectionProperties ( prop );

The parameter value is specified in milliseconds. Therefore, it is possible to reduce the timeout to 500Ms if the application retries connecting.

##### OCI Clients

For OCI clients, create a local `sqlnet.ora` file on the client side.

Configure the connection timeout in this file by adding the following line:

    sqlnet.outbound_connect_timeout = number_of_seconds

The granularity of the timeout value for the OCI client is in seconds. The `sqlnet.ora` file affects all connections using this client.

**Note:**

Do not configure the connection timeout in the `sqlnet.ora` file on the server.

**Related Topics**

- [Oracle Call Interface Programmer's Guide](../lnoci/instant-client.md)

#### Client-Side Load Balancing

Client-side load balancing is defined in your client connection definition (`tnsnames.ora` file, for example) by setting the parameter `LOAD_BALANCE=ON`. When you set this parameter to `ON`, Oracle Database randomly selects an address in the address list, and connects to that node's listener. This balances client connections across the available SCAN listeners in the cluster.

If you configured SCAN for connection requests, then client-side load balancing is not relevant for those clients that support SCAN access. When clients connect using SCAN, Oracle Net automatically balances the load of client connection requests across the three IP addresses you defined for the SCAN, unless you are using EZConnect.

The SCAN listener redirects the connection request to the local listener of the instance that is least loaded (if `-clbgoal` is set to `SHORT`) and provides the requested service. When the listener receives the connection request, the listener connects the user to an instance that the listener knows provides the requested service. To see what services a listener supports, run the `lsnrctl services` command.

When clients connect using SCAN, Oracle Net automatically load balances client connection requests across the three IP addresses you defined for the SCAN, unless you are using EZConnect.

If you are using clients that do not support SCAN (for example, the client version is pre-Oracle Database 11g release 2 (11.2)), then, to use SCAN you must change the client `tnsnames.ora` to include the SCAN VIPs, and set `LOAD_BALANCE=ON` to balance requests across the VIPs. For example:

    Sales.example.com=(DESCRIPTION=
      (ADDRESS_LIST=(LOAD_BALANCE=ON)(FAILOVER=ON)
        (ADDRESS=(PROTOCOL=TCP)(HOST=172.22.67.192)(PORT=1521))
        (ADDRESS=(PROTOCOL=TCP)(HOST=172.22.67.193)(PORT=1521))
        (ADDRESS=(PROTOCOL=TCP)(HOST=172.22.67.194)(PORT=1521)))
        (CONNECT_DATA=(SERVICE_NAME=salesservice.example.com))
      )

**Note:**

If your database is not Oracle Database 11g release 2 (11.2), or later, and you want to use SCAN, then you must add SCAN VIPs to the `REMOTE_LISTENER` parameter to enable correct listener cross-registration.

**Related Topics**

- [Oracle Database Reference](../refrn/REMOTE_LISTENER.md)

### Load Balancing Advisory

This section describes the load balancing advisory under the following topics:

- Overview of the Load Balancing Advisory

- Configuring Your Environment to Use the Load Balancing Advisory

- Load Balancing Advisory FAN Events

- Monitoring Load Balancing Advisory FAN Events

#### Overview of the Load Balancing Advisory

Load balancing distributes work across all of the available Oracle RAC database instances. Oracle recommends that applications use connection pools with persistent connections that span the instances that offer a particular service. When using persistent connections, connections are created infrequently and exist for a long duration. Work comes into the system with high frequency, borrows these connections, and exists for a relatively short duration. The load balancing advisory provides advice about how to direct incoming work to the instances that provide the optimal quality of service for that work. This minimizes the need to relocate the work later.

By using the Load Balancing Advisory and run-time connection load balancing goals, feedback is built in to the system. Work is routed to provide the best service times globally, and routing responds gracefully to changing system conditions. In a steady state, the system approaches equilibrium with improved throughput across all of the Oracle RAC instances.

Standard architectures that can use the load balancing advisory include connection load balancing, transaction processing monitors, application servers, connection concentrators, hardware and software load balancers, job schedulers, batch schedulers, and message queuing systems. All of these applications can allocate work.

The load balancing advisory is deployed with key Oracle clients, such as a listener, the JDBC universal connection pool, OCI session pool, Oracle WebLogic Server Active GridLink for Oracle RAC, and the ODP.NET Connection Pools. Third-party applications can also subscribe to load balancing advisory events by using JDBC and Oracle RAC FAN API or by using callbacks with OCI.

#### Configuring Your Environment to Use the Load Balancing Advisory

You can configure your environment to use the load balancing advisory by defining service-level goals for each service for which you want to enable load balancing.

Configuring a service-level goal enables the load balancing advisory and the publishing of FAN load balancing events for that service. There are two types of service-level goals for run-time connection load balancing:

- `SERVICE_TIME`: Attempts to direct work requests to instances according to response time. Load balancing advisory data is based on elapsed time for work done in the service plus available bandwidth to the service. An example for the use of `SERVICE_TIME` is for workloads such as internet shopping where the rate of demand changes. The following example shows how to set the goal to `SERVICE_TIME` for connections using the `online` service:

      $ srvctl modify service -db db_unique_name -service online
        -rlbgoal SERVICE_TIME -clbgoal SHORT

- `THROUGHPUT`: Attempts to direct work requests according to throughput. The load balancing advisory is based on the rate that work is completed in the service plus available bandwidth to the service. An example for the use of `THROUGHPUT` is for workloads such as batch processes, where the next job starts when the last job completes. The following example shows how to set the goal to `THROUGHPUT` for connections using the `sjob` service:

      $ srvctl modify service -db db_unique_name -service sjob
        -rlbgoal THROUGHPUT -clbgoal LONG

Setting the run-time connection load balancing goal to `NONE` disables load balancing for the service. You can see the goal settings for a service in the data dictionary by querying the `DBA_SERVICES`, `V$SERVICES`, and `V$ACTIVE_SERVICES` views. You can also review the load balancing settings for a service using Oracle Enterprise Manager.

**Related Topics**

- Administering Services

#### Load Balancing Advisory FAN Events

The load balancing advisory FAN events provide metrics for load balancing algorithms.

The easiest way to take advantage of these events is to use the run-time connection load balancing feature of an Oracle integrated client such as JDBC, Universal Connection Pool (or the deprecated Implicit Connection Cache), ODP.NET Connection Pools, OCI session pools, or Oracle WebLogic Server Active GridLink for Oracle RAC. Other client applications can take advantage of FAN programatically by using the Oracle RAC FAN API to subscribe to FAN events and execute event-handling actions upon receipt. Table 5-1 describes the load balancing advisory FAN event parameters.

**See Also:**

Oracle Database JDBC Developer’s Guide for more information about the Oracle RAC FAN API

Table 5-1 Load Balancing Advisory FAN Events

| Parameter    | Description                                                                                                                                                                         |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `VERSION`    | Version of the event record. Used to identify release changes.                                                                                                                      |
| `EVENT_TYPE` | A load balancing advisory event is always of the `SERVICEMETRICS` event type.                                                                                                       |
| `SERVICE`    | The service name; matches the value of `NAME` in `DBA_SERVICES`.                                                                                                                    |
| `DATABASE`   | The unique database supporting the service; matches the initialization parameter value for `DB_UNIQUE_NAME`, which defaults to the value of the initialization parameter `DB_NAME`. |
| `INSTANCE`   | The name of the instance that supports the service; matches the `ORACLE_SID` value.                                                                                                 |
| `PERCENT`    | The percentage of work requests to send to this database instance.                                                                                                                  |
| `FLAG`       | Indication of the service quality relative to the service goal. Valid values are `GOOD`, `VIOLATING`, `NO DATA`, and `BLOCKED`.                                                     |
| `TIMESTAMP`  | The local time zone to use when ordering notification events.                                                                                                                       |

**Note:**

The `INSTANCE`, `PERCENT`, and `FLAG` event parameters are generated for each instance offering the service. Each set of instance data is enclosed within braces (`{}`).

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/Oracle-RAC-FAN-API.md)

#### Monitoring Load Balancing Advisory FAN Events

You can use the following query against the internal queue table for load balancing advisory FAN events to monitor load balancing advisory events generated for an instance:

    SET PAGES 60 COLSEP '|' LINES 132 NUM 8 VERIFY OFF FEEDBACK OFF
    COLUMN user_data HEADING "AQ Service Metrics" FORMAT A60 WRAP
    BREAK ON service_name SKIP 1
    SELECT
     TO_CHAR(enq_time, 'HH:MI:SS') Enq_time, user_data
     FROM sys.sys$service_metrics_tab
     ORDER BY 1 ;

The results of this query contain rows similar to the following:

    02:56:05|SYS$RLBTYP('hr', 'VERSION=1.0 database=sales service=hr
       { {instance=sales_4 percent=38 flag=GOOD aff=TRUE}{instance=sales_1
       percent=62 flag=GOOD aff=TRUE} } timestamp=2012-07-16 07:56:05')

Following is an example of a load balancing advisory event for the `lba_serv` service offered on two instances (`orcl1` and `orcl2`), as captured from Oracle Notification Service using the Oracle RAC FAN API:

    Notification Type: database/event/servicemetrics/lba_serv.example.com
       VERSION=1.0 database=orcl service=lba_serv.example.com { {instance=orcl2
       percent=50 flag=UNKNOWN aff=FALSE}{instance=orcl1 percent=50 flag=UNKNOWN
       aff=FALSE} } timestamp=2012-07-06 13:19:12

**Note:**

The `SERVICMETRICS` events are not visible through the FAN callout mechanism.

### Enabling Clients for Oracle RAC

Oracle has integrated FAN with many of the common client application environments that are used to connect to Oracle RAC databases. Therefore, the easiest way to use FAN is to use an integrated Oracle Client.

The following sections discuss how FAN is integrated with Oracle Clients and how to enable FAN events for the several specific client development environments:

- Overview of Oracle Integrated Clients and FAN

- Enabling JDBC-Thin Clients for Fast Connection Failover

- Enabling JDBC Clients for Run-time Connection Load Balancing

- Configuring JDBC-Thin Clients for Application Continuity for Java

- Configuring JDBC-Thin Clients for Transaction Guard

- Enabling OCI Clients for Fast Connection Failover

- Enabling OCI Clients for Run-time Connection Load Balancing

- Configuring OCI Clients to use Transaction Guard

- Enabling ODP.NET Clients to Receive FAN High Availability Events

- Enabling ODP.NET Clients to Receive FAN Load Balancing Advisory Events

- Configuring ODP.NET Clients to use Transaction Guard

#### Overview of Oracle Integrated Clients and FAN

The overall goals of FAN are to enable end-to-end, lights-out recovery of applications and load balancing based on real transaction performance.

Applications use the FAN high availability (HA) events to achieve very fast detection of failures, balancing of connection pools following failures, and distribution of connections again when the failed components are repaired.

The FAN events carrying load balancing advice help connection pools consistently deliver connections to available instances that provide the best service. FAN HA is integrated with the JDBC-thin and OCI drivers. FAN HA and FAN load balancing are both integrated with the JDBC Universal Connection Pool (and the deprecated Implicit Connection Cache), the OCI session pools, the ODP.NET connection pool, and Oracle WebLogic Server Active GridLink for Oracle RAC.

Due to the integration with FAN, Oracle integrated clients are more aware of the current status of an Oracle RAC cluster. This prevents client connections from waiting or trying to connect to instances or services that are no longer available. When instances start, Oracle RAC uses FAN to notify the connection pool so that the connection pool can create connections to the recently started instance and take advantage of the additional resources that this instance provides.

Oracle client drivers that are integrated with FAN can:

- Remove terminated connections immediately when a service is declared `DOWN` at an instance, and immediately when nodes are declared `DOWN`

- Report errors to clients immediately when Oracle Database detects the `NOT RESTARTING` state, instead of making the client wait while the service repeatedly attempts to restart

Oracle connection pools that are integrated with FAN can:

- Balance connections across all of the Oracle RAC instances when a service starts; this is preferable to directing the sessions that are defined for the connection pool to the first Oracle RAC instance that supports the service

- Balance work requests at run time using load balancing advisory events

The use of client drivers or connection pools and FAN requires that you properly configure the Oracle Notification Service to deliver the FAN events to the clients. In addition, for load balancing, configure database connection load balancing across all of the instances that provide the services used by the connection pool. Oracle recommends that you configure both client-side and server-side load balancing with Oracle Net Services. If you use Oracle DBCA to create your database, then both client-side and server-side load balancing are configured by default.

**Related Topics**

- Connection Load Balancing
- [Fast Application Notification](ensuring-application-continuity.md)

#### Enabling JDBC-Thin Clients for Fast Connection Failover

Enabling Fast Connection Failover (FCF) for Universal Connection Pool and Oracle WebLogic Server Active GridLink for Oracle RAC enables the use of FAN HA and load balancing advisory events.

For Universal Connection Pool to use FAN, your application can use the JDBC development environment for either JDBC OCI or JDBC Thin clients. The Java Database Connectivity Oracle Call Interface (JDBC/OCI) driver connection pooling functionality is part of the JDBC-thin client. This functionality is provided by the `OracleOCIConnectionPool` class.

To enable FCF for the JDBC-thin client, call the method `setFastConnectionFailoverEnabled(true)` of the `OracleDataSource` class in the `oracle.jdbc.pool` package before making the first `getConnection()` request. When you enable FCF for the JDBC-thin client, the failover property applies to every connection in the connection pool. Enabling FCF with JDBC-thin driver or JDBC/OCI clients enables the connection pool to receive and react to all FAN events.

JDBC application developers can programmatically integrate with FAN by using a set of APIs introduced in Oracle Database 11g release 2 (11.2). The Oracle RAC FAN APIs enable application code to receive and respond to FAN event notifications sent by Oracle RAC in the following ways:

- Listening for Oracle RAC service down, service up, and node down events

- Listening for load balancing advisory events and responding to them

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/Oracle-RAC-FAN-API.md)

##### Oracle Notification Service for JDBC-Thin Clients

FCF relies on Oracle Notification Service to propagate database events between the connection pool and the Oracle RAC database. At run time, the connection pool must be able to setup an Oracle Notification Service environment. Oracle Notification Service (`ons.jar`) is included as part of the Oracle Client software. Oracle Notification Service can be configured using either remote configuration or client-side Oracle Notification Service daemon configuration. Remote Oracle Notification Service subscription offers the following advantages:

- Support for an All Java mid-tier software

- An Oracle Notification Service daemon is not necessary on the client system, so you do not have to manage this process

- Simple configuration by way of a `DataSource` property

##### Configuring FCF for JDBC/OCI and JDBC-Thin Driver Clients

You can enable FCF for Universal Connection Pool or Implicit Connection Cache.

Oracle recommends using the Universal Connection Pool for Java because the Implicit Connection Cache is deprecated. You can also use Oracle WebLogic Server Active GridLink for Oracle RAC.

This procedure explains how to enable FCF for JDBC. For JDBC/OCI clients, if you enable FCF, then do not use the method used with Oracle Database 11g release 2 (11.2) of enabling FAN for OCI clients (setting `notification` to TRUE on the service), and do not configure TAF, either on the client or for the service. You can also configure Application Continuity and Transaction Guard.

To enable FCF, you must first enable the Universal Connection Pool, as described in the following procedure:

1.  Create the connection pool and set `setFastConnectionFailoverEnabled(true)`.

    The following example creates a connection pool and enables FCF. The `ucp.jar` library must be included in the classpath of an application to use this example.

        PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
        pds.setFastConnectionFailoverEnabled(true);

2.  Determine the ports to use for Oracle Notification Service remote subscriptions.

    Use the following command to view the Oracle Notification Service configuration on each node that is running Oracle Clusterware as in the following example:

        srvctl config nodeapps -onsonly

    The output of this command lists the local and remote ports configured for Oracle Notification Service.

    **Note:**

    Oracle Notification Service configuration should have been automatically completed during the Oracle Clusterware installation.

3.  Configure the remote Oracle Notification Service subscription.

    When using the Universal Connection Pool, an application calls `setONSConfiguration` for an `OracleDataSource` instance and specifies the nodes and port numbers to use. The port numbers used for each node are the same as the remote port displayed for each node in Step 2, as shown in the following example. The `ons.jar` library must be included in the classpath of an application to use this example.

        pds.setONSConfiguration("nodes=racnode1:6200,racnode2:6200");

    Applications that use remote Oracle Notification Service configuration must set the `oracle.ons.oraclehome` system property to the location of `ORACLE_HOME` before starting the application, for example:

        java -Doracle.ons.oraclehome=$ORACLE_HOME ...

4.  Configure the connection URL.

    A connection factory's connection URL must use the service name syntax when using FCF. The service name is used to map the connection pool to the service. The following example demonstrates configuring the connection URL:

        pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
        pds.setURL("jdbc:oracle:thin@//SCAN_name:service_name");...

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)
- [Oracle Universal Connection Pool Developer’s Guide](../jjucp/fast-connection-failover.md)

#### Enabling JDBC Clients for Run-time Connection Load Balancing

Run-time connection load balancing requires the use of an Oracle JDBC driver and an Oracle RAC database.

Oracle JDBC Universal Connection Pool and Oracle WebLogic Server Active GridLink for Oracle RAC leverage the load balancing functionality provided by an Oracle RAC database.

The Universal Connection Pool and Oracle WebLogic Server Active GridLink for Oracle RAC are integrated to take advantage of Load Balancing Advisory information. Oracle introduced the Universal Connection Pool for JDBC in Oracle Database 11g release 11.1.0.7.0. Consequently, Oracle deprecated the existing JDBC connection pool, the Implicit Connection Cache, which was introduced in Oracle Database 10g release 1 for use with Oracle RAC databases. In addition to Oracle Database 12c, you can also use the Universal Connection Pool with Oracle Database 10g or Oracle Database 11g.

Run-time connection load balancing requires that FCF is enabled and configured properly. In addition, the Oracle RAC load balancing advisory must be configured with service-level goals for each service used by the connection pool. The connection load balancing goal should be set to `SHORT`, for example:

    srvctl modify service -db db_unique_name -service service_name
       -rlbgoal SERVICE_TIME -clbgoal SHORT

**Related Topics**

- Configuring FCF for JDBC/OCI and JDBC-Thin Driver Clients
- [Oracle Universal Connection Pool Developer’s Guide](../jjucp/fast-connection-failover.md)

#### Configuring JDBC-Thin Clients for Application Continuity for Java

The Replay data source (`oracle.jdbc.replay.OracleDataSource`) is a JDBC-thin data source that Application Continuity requires for Java.

This data source serves as the connection factory that produces new physical JDBC connections, for both Universal Connection Pool and Oracle WebLogic Server Active GridLink for Oracle RAC data sources. The JDBC replay driver maintains a history of calls during a client conversation with Oracle Database 12c, in collaboration with Oracle Database. Following any outage of the session caused by a loss of database service, planned or unplanned, under the direction of the database, the JDBC replay driver attempts to rebuild the non-transactional and transactional database session states, so that the outage appears as a delayed execution.

To use Application Continuity for Java and the JDBC replay driver, you must use an Oracle Database 12c client and connect to an Oracle Database 12c database. Application Continuity for Java is supported in the following configurations:

- JDBC applications using Oracle JDBC Replay data source and using neither Universal Connection Pool or Oracle WebLogic Server Active GridLink—typical third-party, JDBC-based connection pools

- JDBC applications using Universal Connection Pool data sources—standalone or third-party application servers configured to use a Universal Connection Pool data source

- JDBC applications using only Oracle WebLogic Server Active GridLink but not Universal Connection Pool data sources—typical Oracle WebLogic Server J2EE cases

##### To configure JDBC-thin clients to use the JDBC Replay Driver:

1.  Ensure that you are using an application that is certified for replay.

2.  Use SRVCTL to create a service for use by the application, if one does not already exist. Set the `-failovertype` parameter to `TRANSACTION` and the `-commit_outcome` parameter to `TRUE` for this service.

3.  Configure the connection element using the `PoolDataSource` object, as shown in the following example:

        PoolDataSource rds = PoolDataSourceFactory.getPoolDataSource();
        rds.setConnnectionPoolName("replayExample");
        rds.setONSConfiguration("nodes=racnode1:4200,racnode2:4200");
        rds.setFastConnectionFailoverEnabled(true);
        rds.setConnectionFactoryClassName("oracle.jdbc.replay.OracleDataSourceImpl");

        Connection conn = rds.getConnection();

4.  When connecting to the database, use a URL that can access all instances offering the service.

**Related Topics**

- [About Application Continuity](ensuring-application-continuity.md)
- Creating Services for Application Continuity and Transaction Guard
- Configuring FCF for JDBC/OCI and JDBC-Thin Driver Clients
- [Oracle Database JDBC Developer’s Guide](../jjdbc/application-continuity.md)
- [Oracle Universal Connection Pool Developer’s Guide](../jjucp/intro.md)

**See Also:**

Oracle Database JDBC Developer’s Guide for information about configuring Transaction Guard without enabling Application Continuity

#### Configuring JDBC-Thin Clients for Transaction Guard

Transaction Guard provides a protocol and a generic tool for applications to use for at-most-once processing in case of planned and unplanned outages.

Applications use the logical transaction ID to determine the outcome of the last transaction open in a database session following an outage. Without Transaction Guard, end users or applications that attempt to retry operations following outages can cause logical corruption by committing duplicate transactions or committing transactions out of order.

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/application-continuity.md)
- [Oracle Database Development Guide](../adfns/transaction-guard.md)
- [Oracle Call Interface Programmer's Guide](../lnoci/high-availability-in-oci.md)

#### Enabling OCI Clients for Fast Connection Failover

OCI clients can enable FCF by registering to receive notifications for Oracle RAC high availability FAN events and responding when events occur. Using FCF improves the session failover response time in OCI applications and also removes connections to nonfunctioning instances from connection and session pools. FCF can be used in OCI applications that also use TAF, OCI drivers (including your own connection pools), OCI connection pool, and OCI session pools. FAN is posted over the Oracle Notification Service for both high availability and load balancing events.

To use FCF, you must use a service with FAN enabled. FAN is published over Oracle Notification Service. Client applications can also register callbacks that are used whenever an event occurs. This reduces the time that it takes to detect a connection failure.

During `DOWN` event processing, OCI:

- Terminates affected connections at the client and returns an error

- Removes connections from the OCI connection pool and the OCI session pool—the session pool maps each session to a physical connection in the connection pool, and there can be multiple sessions for each connection

- Fails over the connection if you have configured TAF. If TAF is not configured, then the client only receives an error if the instance it is connected to fails.

If your application is using TAF, then you must enable the TAF properties for the service using SRVCTL or Oracle Enterprise Manager. Configure your OCI client applications to connect to an Oracle RAC database using the configured service.

**Note:**

OCI does not manage `UP` events.

##### Configuring FCF for OCI Clients

OCI applications must connect to an Oracle RAC instance to enable HA event notification. Furthermore, these applications must perform the following steps to configure FCF for an OCI client:

1.  Configure the service for your OCI connection pool to enable FAN, connection load balancing, and run-time connection load balancing, as shown in the following example:

        $ srvctl modify service -db crm -service ociapp.example.com -notification TRUE

2.  Link the application with a thread library.

3.  After linking with the thread library, the applications can register a callback that is invoked whenever a FAN event occurs.

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)
- [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md)

#### Enabling OCI Clients for Run-time Connection Load Balancing

As of Oracle Database 12c, OCI session pooling enables multiple threads of an application to use a dynamically managed set of pre-created database sessions.

In connection pooling, the pool element is a connection, but in session pooling, the pool element is a session. Oracle Database continually reuses the sessions in the session pool to form nearly permanent channels to the instances, thus saving the overhead of creating and closing sessions every time applications need them.

Run-time connection load balancing is enabled by default in an Oracle Database 11g release 11.1, or later, client communicating with a server of Oracle Database 10g release 10.2, or later. For Oracle RAC environments, session pools use service metrics received from the Oracle RAC load balancing advisory<sup>Foot 1</sup> through Fast Application Notification (FAN) events to balance application session requests. The work requests coming into the session pool can be distributed across the instances of Oracle RAC offering a service, using the current service performance.

##### Configuring OCI Clients to Receive Load Balancing Advisory FAN Events

For Oracle RAC environments, session pools use service metrics received from the Oracle RAC load balancing advisory through Fast Application Notification (FAN) events to balance application session requests. To enable your application to receive the service metrics based on the service time, ensure that you configure FAN, the load balancing advisory goal (`-rlbgoal` parameter), and the connection load balancing goal (`-clbgoal` parameter) for a service that is used by the session pool, as shown in the following example:

    $ srvctl modify service -db crm -service ociapp.example.com -rlbgoal SERVICE_TIME
      -clbgoal SHORT -notification TRUE

**Related Topics**

- [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md)

#### Configuring OCI Clients to use Transaction Guard

OCI supports FAN messages and Transaction Guard. FAN is designed to quickly notify an OCI-based application of outages at the node, database, instance, service, and public network levels.

Once notified of the failure, an application can leverage Transaction Guard to reliably determine the outcome of the last in-flight transaction.

Transaction Guard avoids the costs of ambiguous errors that lead to user frustration, customer support calls, and lost opportunities. Transaction Guard is safer and performs better, with lower overheads, than home grown solutions for a known outcome.

**Related Topics**

- [Fast Application Notification](ensuring-application-continuity.md)
- Enabling Clients for Oracle RAC
- [Oracle Call Interface Programmer's Guide](../lnoci/user-defined-callback-functions.md)

#### Enabling ODP.NET Clients to Receive FAN High Availability Events

ODP.NET connection pools can subscribe to FAN HA notifications that indicate when nodes, services, and service members are down.

After a `DOWN` event, Oracle Database cleans up sessions in the connection pool that go to the instance and ODP.NET proactively removes connections that are no longer valid. ODP.NET establishes additional connections to existing Oracle RAC instances if the removal of invalid connections reduces the total number of connections to below the value for the `Min Pool Size` parameter.

When connecting to Oracle Database 12c and later, ODP.NET uses Oracle Notification Service, rather than Advanced Queuing.

Enable Fast Connection Failover for ODP.NET connection pools by subscribing to FAN high availability events. To enable Fast Connection Failover, include "`HA Events=true`" and "`pooling=true`" (the default value) in the connection string, as shown in the following example where `user_name` is the name of the database user and `password` is the password for that user:

    con.ConnectionString =
       "User Id=user_name;Password=password;Data Source=odpnet;" +
       "Min Pool Size=10;Connection Lifetime=120;Connection Timeout=60;" +
       "HA Events=true;Incr Pool Size=5;Decr Pool Size=2";

**Related Topics**

- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featConnecting.md)
- [Fast Application Notification](ensuring-application-continuity.md)

#### Enabling ODP.NET Clients to Receive FAN Load Balancing Advisory Events

When connecting to Oracle Database 12c and later, ODP.NET uses Oracle Notification Service, rather than Advanced Queuing.

Use the following procedure to enable ODP.NET clients or applications to receive FAN load balancing advisory events:

1.  Enable Oracle Notification Service notifications by using SRVCTL, and set the run-time load balancing goal, as shown in the following example:

        $ srvctl modify service -db crm -service odpapp.example.com
          -notification TRUE -clbgoal LONG -rlbgoal SERVICE_TIME

2.  Ensure Oracle Notification Service (ONS) is configured for FAN events including run-time load balancing advice.

3.  To take advantage of load balancing events with ODP.NET connection pools, set the load balancing attribute in the ConnectionString to `TRUE` (the default is `FALSE`). You can do this at connect time. This only works if you are using connection pools, or when the pooling attribute is set to `TRUE` which is the default.

    The following example demonstrates how to configure the ConnectionString to enable load balancing, where `user_name` is the name of the user and `password` is the password:

        con.ConnectionString =
          "User Id=user_name;Password=password;Data Source=odpapp;" +
          "Min Pool Size=10;Connection Lifetime=120;Connection Timeout=60;" +
          "Load Balancing=true;Incr Pool Size=5;Decr Pool Size=2";

**Note:**

ODP.NET does not support connection redistribution when a node starts (UP events). However, if you have enabled failover on the server-side, then ODP.NET can migrate connections to newly available instances.

**Related Topics**

- [srvctl modify service](server-control-utility-reference.md)
- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featConnecting.md)
- [Fast Application Notification](ensuring-application-continuity.md)

#### Configuring ODP.NET Clients to use Transaction Guard

ODP.NET supports FAN messages and Transaction Guard. FAN is designed to quickly notify an ODP.NET-based application of outages at the node, database, instance, service, and public network levels.

Once notified of the failure, an application can leverage Transaction Guard to reliably determine the outcome of the last in-flight transaction.

Transaction Guard avoids the costs of ambiguous errors that lead to user frustration, customer support calls, and lost opportunities. Transaction Guard is safer and performs better, with lower overheads, than home grown solutions for a known outcome.

**Related Topics**

- [Fast Application Notification](ensuring-application-continuity.md)
- Administering Services
- Creating Services for Application Continuity and Transaction Guard
- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/intro.md)

### Distributed Transaction Processing in Oracle RAC

The X/Open Distributed Transaction Processing (DTP) architecture defines a standard architecture or interface that enables multiple application programs (APs) to share resources provided by multiple, and possibly different, resource managers (RMs). It coordinates the work between APs and RMs into global transactions.

The following sections discuss how Oracle RAC supports global (XA) transactions and DTP processing:

- Overview of XA Transactions and Oracle RAC

- Using Global Transactions and XA Affinity for XA Transactions

- Using Services with XA Transactions on Oracle RAC

- Configuring Services for XA Applications

- Relocating Services in Administrator-Managed Databases

#### Overview of XA Transactions and Oracle RAC

A global (XA) transaction can span Oracle RAC instances by default, allowing any application that uses the Oracle XA library to take full advantage of the Oracle RAC environment to enhance the availability and scalability of the application.

GTXn background processes support XA transactions in an Oracle RAC environment. The `GLOBAL_TXN_PROCESSES` initialization parameter, which is set to `1` by default, specifies the initial number of GTXn background processes for each Oracle RAC instance. Use the default value for this parameter clusterwide to allow distributed transactions to span multiple Oracle RAC instances. Using the default value allows the units of work performed across these Oracle RAC instances to share resources and act as a single transaction (that is, the units of work are tightly coupled). It also allows 2PC requests to be sent to any node in the cluster.

Before Oracle RAC 11g release 1 (11.1), the way to achieve tight coupling in Oracle RAC was to use distributed transaction processing (DTP) services, that is, services whose cardinality (one) ensured that all tightly-coupled branches landed on the same instance—regardless of whether load balancing was enabled. If the XA application does not use suspend and resume on the same transaction branch, and does not issue savepoints that span branches, then tightly coupled XA transactions no longer require the special type of singleton services to be deployed on Oracle RAC databases. If your application cannot determine whether a transaction branch has been suspended and resumed, then the application must continue to use DTP services or preferably use XA affinity.

XA affinity (placing all branches of the same XA transaction at the same Oracle RAC instance) is a requirement when suspending and resuming the same XA branch or if using savepoints across branches. It also provides much better performance because different transactions can be balanced. XA affinity is available with Oracle WebLogic Server Active GridLink for Oracle RAC, JDBC Universal Connection Pool, and Oracle Tuxedo. XA affinity is also standard for RedHat JBoss, IBM WebSphere, and IBM Liberty.

**Note:**

Transaction Processing monitors with XA work best when using services with one preferred instance and many available instances. Oracle does not recommend using the DTP setting for Oracle Database 11g release 1 (11.1) and later.

**Related Topics**

- Using Global Transactions and XA Affinity for XA Transactions
- [Oracle Database Reference](../refrn/GLOBAL_TXN_PROCESSES.md)

#### Using Global Transactions and XA Affinity for XA Transactions

To provide improved application performance with distributed transaction processing (DTP) in Oracle RAC, you can take advantage of XA affinity.

Using XA affinity, you can direct all branches of a distributed transaction to a single instance in the cluster. To implement XA affinity you can use an application server that provides XA affinity, such as WebLogic Server and Universal Connection Pool. If your application server does not have XA affinity, then you can also use singleton services across Oracle RAC.

Connection pools at the application server tier that load balance across multiple connections to an Oracle RAC database use XA affinity to ensure that all tightly-coupled branches of a global distributed transaction run on only one Oracle RAC instance. When using a connection pool with XA affinity, your services using XA can span Oracle RAC. This is also true in distributed transaction environments using protocols such as X/Open Distributed Transaction Processing or the Microsoft Distributed Transaction Coordinator.

To enhance the performance of distributed transactions, use services with one preferred instance. A singleton service runs on one Oracle RAC instance at time in an Oracle RAC database. This service still allows draining for maintenance, so has better high-availability characteristics than an older DTP service. To load balance across the cluster, it is better to have several groups of smaller application servers with each group directing its transactions to a single service, or set of services, than it is to have one or two larger application servers. Using singleton services, global distributed transactions performed through the services have their tightly-coupled branches running on a single Oracle RAC instance. This has the following benefits:

- The changes are available locally within one Oracle RAC instance when tightly coupled branches need information about changes made by each other

- Relocation and failover of services are fully supported using global transactions

- By using more singleton services than there are Oracle RAC instances, Oracle Database can balance the load by services across all of the Oracle RAC database instances

**Note:**

Oracle does not recommend using the DTP setting for Oracle Database 11g release 1 (11.1) and later.

#### Using Services with XA Transactions on Oracle RAC

Most applications using XA on Oracle RAC can use uniform or (all preferred) services with XA affinity provided by the connection pool or transaction processing monitor.

The application may also use singleton services to provide XA affinity.

When using singleton services, to leverage all of the instances in a cluster, create one or more singleton services for each Oracle RAC instance that hosts distributed transactions. Choose different services for application servers to balance the workload among the Oracle RAC database instances. Because all of the branches of a distributed transaction are on one instance, you can leverage all of the instances to balance the load of many distributed transaction processing (DTP) transactions through multiple singleton services, thereby maximizing application throughput.

If you add or delete nodes from your cluster database, then you may have to identify and relocate services to ensure that you maintain optimum performance levels. Using singleton services, current work can complete. If you use DTP services, then current work is terminated.

You only need to use DTP services for XA applications that suspend and resume the same branch. When you are using DTP, the same approach applies as that for singletons, but you cannot drain the work when relocating services.

#### Configuring Services for XA Applications

To create distributed transaction processing (DTP) services for distributed transaction processing, perform the following steps:

1.  Create a singleton service using Oracle Enterprise Manager or SRVCTL.

    For an administrator-managed database, define only one instance as the preferred instance. You can have as many available instances as you want, for example:

        $ srvctl add service -db crm -service xa_01.example.com -preferred RAC01
          -available RAC02,RAC03

    For a policy-managed database, specify the server pool to use, and set the cardinality of the service to `SINGLETON`, for example:

        $ srvctl add service -db crm -service xa_01.example.com -serverpool mypool
          -cardinality SINGLETON

2.  Set the DTP parameter (`-dtp`) for the service to `TRUE` (the default value is `FALSE)`. You can use Oracle Enterprise Manager or SRVCTL to modify the DTP property of the singleton service. The following example shows how to modify the `xa_01.example.com` service using SRVCTL:

        $ srvctl modify service -db crm -service xa_01.example.com -dtp TRUE

    **Note:**

    If the application does require DTP services, then use the `-dtp` parameter. If not, then use the preceding example with no `-dtp` parameter.

**Related Topics**

- [srvctl add service](server-control-utility-reference.md)
- [srvctl modify service](server-control-utility-reference.md)

#### Relocating Services in Administrator-Managed Databases

Beginning with Oracle Real Application Clusters 11g release 1 (11.1), global transactions and XA affinity replace the need for distributed transaction processing (DTP) services.

Most XA deployments should be using global transactions with XA affinity for improved load balancing and flexibility rather than the DTP attribute.

If services migrate to other instances, then you might have to force the relocation of the service back to the preferred instance after it is restarted to evenly re-balance the load on all of the available hardware. You can use data from the `GV$ACTIVE_SERVICES` view to determine whether you need to relocate the DTP service.

### Oracle RAC Sharding

Oracle RAC Sharding creates an affinity between table partitions and Oracle RAC instances, and routes database requests that specify a partitioning key to the instance that logically holds the corresponding partition.

Oracle routes database requests to Oracle RAC instances in such a way that each instance always gets requests for a disjoint subset of rows in the database, which creates affinity of rows with instances. The affinity leads to higher Oracle RAC performance and scalability because of improved cache locality and reduced inter-node synchronization and block pings.

Sharding for Oracle RAC affinity uses client and server-side support for key-based routing, which is part of the Oracle Database sharding. An application that supplies a sharding key in the database using the same API implemented for sharding support in Oracle connection pools (such as Universal Connection Pool, OCI), in the same way it is done for sharding, utilizes key-based routing and, by doing so, enables Oracle RAC affinity.

Application changes that are required to supply the sharding key, do not have to affect all modules of the application. Changes can only be applied to a few frequently processed database requests. Requests that do not provide the sharding key in the connect string are routed based on the load-balancing policy. Keyless requests do not have any negative impact on data affinity because of the explicit ownership assignment of data objects to instances.

**Note:**

Oracle only supports Oracle RAC affinity for partitioned tables. You can partition a table using any supported method without making changes to the database schema to enable this feature and then run the `ALTER SYSTEM ENABLE AFFINITY` command.

If you want to make changes to your applications to take advantage of affinity-enabling routing, then you may also take advantage of sharding when data is distributed across multiple independent databases. You can later move to distributed sharding if you require extreme scalability or fault isolation.

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-SYSTEM.md)
- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)
- [Using Oracle Sharding](../shard/architecture-and-concepts1.md)
- [Oracle Database JDBC Developer’s Guide](../jjdbc/database-sharding.md)
- [Oracle Call Interface Programmer's Guide](../lnoci/oci-interface-for-using-shards.md)

### Automatic Workload Repository

The Automatic Workload Repository (AWR) collects, processes, and maintains performance statistics for the database.

The gathered data can be displayed in both reports and views. If you use services with your database, then AWR tracks metrics at the service level.

Metrics can be measured against a variety of units, including time, transactions, or database calls. For example, the number of database calls per second is a metric. Server generated alerts can be placed on these metrics when they exceed or fail to meet user-specified thresholds. The database or system administrator can then respond, for example, by:

- Using the Oracle Database Resource Manager to configure the service level for one service to have priorities relative to other services

- Stopping overloaded processes

- Modifying a service level requirement

- Implementing recovery scenarios in response to service quality changes

Using AWR metrics and performance alerts enables you to maintain continued service availability despite service level changes. It also enables you to measure the quality of service provided by the database services.

The AWR ensures that the Oracle Clusterware workload management framework and the database resource manager have persistent and global representations of performance data. This information helps Oracle Database schedule job classes by service and to assign priorities to consumer groups. If necessary, you can rebalance workloads manually with either Oracle Enterprise Manager or SRVCTL. You can also disconnect a series of sessions, but leave the service running.

**Note:**

Oracle does not recommend using the DBMS_SERVICE package for use with services used by an Oracle RAC database. Use SRVCTL or Oracle Enterprise Manager to create database services for Oracle RAC.

**Related Topics**

- [Oracle Database 2 Day + Performance Tuning Guide](../tdppt/resolving-performance-degradation-over-time.md)
- [Oracle Database Performance Tuning Guide](../tgdba/comparing-database-performance-over-time.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SERVICE.md)

### Measuring Performance by Service Using the Automatic Workload Repository

Services add a new dimension for performance tuning because workloads are visible and measurable, and therefore resource consumption and wait times are attributable by application.

Tuning by using "service and SQL" replaces tuning by "session and SQL" in the majority of systems where all sessions are anonymous and shared.

The AWR maintains performance statistics that include information about response time, throughput, resource consumption, and wait events for all services and work that a database performs. Oracle Database also maintains metrics, statistics, wait events, wait classes, and SQL-level traces for services. You can optionally augment these statistics by defining modules within your application to monitor certain statistics. You can also define the actions within those modules that business critical transactions should run in response to particular statistical values.

Enable module and action monitoring using the `DBMS_MONITOR ` PL/SQL package. For example, for connections that use the `erp` service, the following command enables monitoring for the `exceptions pay` action in the `payroll` module:

    EXECUTE DBMS_MONITOR.SERV_MOD_ACT_STAT_ENABLE(SERVICE_NAME => 'ERP',
       MODULE_NAME=> 'PAYROLL', ACTION_NAME => 'EXCEPTIONS PAY');

For connections that use the `erp` service, the following command enables monitoring for all actions in the `payroll` module:

    EXECUTE DBMS_MONITOR.SERV_MOD_ACT_STAT_ENABLE(SERVICE_NAME => 'ERP',
       MODULE_NAME=> 'PAYROLL', ACTION_NAME => NULL);

Use the `DBA_ENABLED_AGGREGATIONS` view to verify that you have enabled monitoring for application modules and actions.

Statistics aggregation and tracing by service are global in scope for Oracle RAC databases. In addition, these statistic aggregations are persistent across instance restarts and service relocations for both Oracle RAC and noncluster Oracle databases.

The service, module, and action names are visible in `V$SESSION`, `V$ACTIVE_SESSION_HISTORY`, and `V$SQL` views. The call times and performance statistics are visible in `V$SERVICE_STATS`, `V$SERVICE_EVENT`, `V$SERVICE_WAIT_CLASS`, `V$SERVICEMETRIC`, and `V$SERVICEMETRIC_HISTORY`. When you enable statistics collection for an important transaction, you can see the call speed for each service, module, and action name at each database instance using the `V$SERV_MOD_ACT_STATS` view.

The following sample SQL\*Plus script provides service quality statistics for a five second interval. You can use these service quality statistics to monitor the quality of a service, to direct work, and to balance services across Oracle RAC instances:

    SET PAGESIZE 60 COLSEP '|' NUMWIDTH 8 LINESIZE 132 VERIFY OFF FEEDBACK OFF
    COLUMN service_name FORMAT A20 TRUNCATED HEADING 'Service'
    COLUMN begin_time HEADING 'Begin Time' FORMAT A10
    COLUMN end_time HEADING 'End Time' FORMAT A10
    COLUMN instance_name HEADING 'Instance' FORMAT A10
    COLUMN service_time HEADING 'Service Time|mSec/Call' FORMAT 999999999
    COLUMN throughput HEADING 'Calls/sec'FORMAT 99.99
    BREAK ON service_name SKIP 1
    SELECT
        service_name
      , TO_CHAR(begin_time, 'HH:MI:SS') begin_time
      , TO_CHAR(end_time, 'HH:MI:SS') end_time
      , instance_name
      , elapsedpercall  service_time
      ,  callspersec  throughput
    FROM
        gv$instance i
      , gv$active_services s
      , gv$servicemetric m
    WHERE s.inst_id = m.inst_id
      AND s.name_hash = m.service_name_hash
      AND i.inst_id = m.inst_id
      AND m.group_id = 10
    ORDER BY
       service_name
     , i.inst_id
     , begin_time ;

### Automatic Workload Repository Service Thresholds and Alerts

Service level thresholds enable you to compare actual service levels against required levels of service. This provides accountability for the delivery or the failure to deliver an agreed service level. The end goal is a predictable system that achieves service levels. There is no requirement to perform as fast as possible with minimum resource consumption; the requirement is to meet the quality of service.

AWR enables you to explicitly specify two performance thresholds for each service: the response time for calls (`ELAPSED_TIME_PER_CALL`), and the CPU time for calls (`CPU_TIME_PER_CALL`). The response time threshold indicates that the elapsed time for each user call for each service should not exceed a certain value, and the CPU time for calls threshold indicates that the time spent using the CPU for each call for each service should not exceed a certain value. Response time is a fundamental measure that reflects all delays and faults that might be blocking the call from running on behalf of the user. Response time can also indicate differences in node power across the nodes of an Oracle RAC database.

You must set these thresholds on each instance of an Oracle RAC database. The elapsed time and CPU time are calculated as the moving average of the elapsed, server-side call time. The AWR monitors the elapsed time and CPU time and publishes AWR alerts when the performance exceeds the thresholds. You can schedule actions using Oracle Enterprise Manager jobs for these alerts, or you can schedule actions to occur programmatically when the alert is received. You can respond to these alerts by changing the priority of a job, stopping overloaded processes, or by relocating, starting or stopping a service. This permits you to maintain service availability despite changes in demand.

This section includes the following topics:

- Example of Services and Thresholds Alerts

- Enable Service\_ Module\_ and Action Monitoring

#### Example of Services and Thresholds Alerts

In this scenario, you need to check the thresholds for the payroll service. You can use the AWR report to get this information. You should compare the results from reports run over several successive intervals during which time the system is running optimally. For example, assume that for servers accessed by a payroll application, the AWR report runs each Thursday during the peak usage times of 1:00 p.m. to 5:00 p.m. The AWR report contains the response time, or elapsed database time, and the CPU consumption time, or CPU time, for calls for each server, including the `payroll` service. The AWR report also provides a breakdown of the work done and the wait times that are contributing to the response times.

Using `DBMS_MONITOR`, you set a warning threshold for the elapsed time per call for the `payroll` service at 0.5 seconds (500000 microseconds). You also set a critical threshold for the elapsed time per call for the `payroll` service at 0.75 seconds (750000 microseconds).

In this example, thresholds are added for the `payroll` service as follows:

    EXECUTE DBMS_SERVER_ALERT.SET_THRESHOLD(
    METRICS_ID => DBMS_SERVER_ALERT.ELAPSED_TIME_PER_CALL
    , warning_operator => DBMS_SERVER_ALERT.OPERATOR_GE
    , warning_value => '500000'
    , critical_operator => DBMS_SERVER_ALERT.OPERATOR_GE
    , critical_value => '750000'
    , observation_period => 30
    , consecutive_occurrences => 5
    , instance_name => NULL
    , object_type => DBMS_SERVER_ALERT.OBJECT_TYPE_SERVICE
    , object_name => 'payroll');

You can verify the threshold configuration is set on all the instances using the following `SELECT` statement:

    SELECT METRICS_NAME, INSTANCE_NAME, WARNING_VALUE, CRITICAL_VALUE,
    OBSERVATION_PERIOD FROM dba_thresholds ;

#### Enable Service, Module, and Action Monitoring

You can enable performance data tracing for important modules and actions within each service. The performance statistics are available in the `V$SERV_MOD_ACT_STATS` view. For example, you might decide to set the following:

- For the `ERP` service, enable monitoring for the `exceptions pay` action in the `payroll` module.

- For the `ERP` service, enable monitoring for the all actions in the `payroll` module.

- For the `HOT_BATCH` service, enable monitoring for all actions in the `posting` module.

The following commands show how to enable the module and action monitoring for the services:

    EXECUTE DBMS_MONITOR.SERV_MOD_ACT_STAT_ENABLE(service_name => 'erp', module_name=>
     'payroll', action_name => 'exceptions pay');
    EXECUTE DBMS_MONITOR.SERV_MOD_ACT_STAT_ENABLE(service_name => 'erp', module_name=>
     'payroll');
    EXECUTE DBMS_MONITOR.SERV_MOD_ACT_STAT_ENABLE(service_name => 'hot_batch',
    module_name =>'posting');

To verify monitoring is enabled for the service, module, and actions, use the following `SELECT` statement:

    COLUMN AGGREGATION_TYPE FORMAT A21 TRUNCATED HEADING 'AGGREGATION'
    COLUMN PRIMARY_ID FORMAT A20 TRUNCATED HEADING 'SERVICE'
    COLUMN QUALIFIER_ID1 FORMAT A20 TRUNCATED HEADING 'MODULE'
    COLUMN QUALIFIER_ID2 FORMAT A20 TRUNCATED HEADING 'ACTION'
    SELECT * FROM DBA_ENABLED_AGGREGATIONS ;

The output is similar to the following:

    AGGREGATION            SERVICE                MODULE        ACTION
    ------------           --------------------   ----------    -------------
    SERVICE_MODULE_ACTION  erp                    payroll       exceptions pay
    SERVICE_MODULE         erp                    payroll
    SERVICE_MODULE         hot_batch              posting

### Using Oracle Services

To manage workloads or a group of applications, you can define services that you assign to a particular application or to a subset of an application's operations. You can also group work by type under services. For example, online users can use one service, while batch processing can use another and reporting can use yet another service to connect to the database.

Oracle recommends that all users who share a service have the same service level requirements. You can define specific characteristics for services and each service can represent a separate unit of work. There are many options that you can take advantage of when using services. Although you do not have to implement these options, using them helps optimize application performance.

### Service Deployment Options

This section describes the following service deployment topics:

- Service Usage in an Oracle RAC Database

- Service Characteristics

- Default Service Connections

- Restricted Service Registration

#### Service Usage in an Oracle RAC Database

Services provide location transparency. A service name can identify multiple database instances, and an instance can belong to multiple services. Several database features use services for an Oracle RAC database:

This section includes the following topics:

- Oracle Clusterware Resources for a Service

- Database Resource Manager Consumer Group Mappings for Services

- Performance Monitoring by Service with AWR

- Parallel Operations and Services

- Oracle GoldenGate and Oracle RAC

##### Oracle Clusterware Resources for a Service

Resource profiles are automatically created when you define a service. A resource profile describes how Oracle Clusterware should manage the service and which instance the service should failover to if the preferred instance stops. Resource profiles also define service dependencies for the instance and the database. Due to these dependencies, if you stop a database, then the instances and services are automatically stopped in the correct order.

##### Database Resource Manager Consumer Group Mappings for Services

Services are integrated with Oracle Resource Manager, which enables you to restrict the resources that users use to connect to an instance by using a service. Oracle Resource Manager enables you to map a consumer group to a service so that users who connect to an instance using that service are members of the specified consumer group. Oracle Resource Manager operates at an instance level.

##### Performance Monitoring by Service with AWR

The metric data generated by Automatic Workload Repository (AWR) is organized into various groups, such as event, event class, session, service, and tablespace metrics. Typically, you view the AWR data using Oracle Enterprise Manager or AWR reports.

**Related Topics**

- [Oracle Database Performance Tuning Guide](../tgdba/comparing-database-performance-over-time.md)

##### Parallel Operations and Services

By default, in an Oracle RAC environment, a SQL statement processed in parallel can run across all of the nodes in the cluster.

For this cross-node or inter-node parallel processing to perform well, the interconnect in the Oracle RAC environment must be sized appropriately because inter-node parallel processing may result in a lot of interconnect traffic. To limit inter-node parallel processing, you can control parallel processing in an Oracle RAC environment using the `PARALLEL_FORCE_LOCAL` initialization parameter. By setting this parameter to `TRUE`, the parallel processing servers can only run on the same Oracle RAC node where the SQL statement was started.

Services are used to limit the number of instances that participate in a parallel SQL operation. When the default database service is used, the parallel SQL operation can run on all available instances. You can create any number of services, each consisting of one or more instances. When a parallel SQL operation is started, the parallel processing servers are only spawned on instances which offer the specified service used in the initial database connection.

`PARALLEL_INSTANCE_GROUP` is an Oracle RAC parameter that, when used with services, lets you restrict parallel query operations to a limited number of instances.To restrict parallel query operations to a limited number of instances, set the `PARALLEL_INSTANCE_GROUP` initialization parameter to the name of a service. This does not affect other parallel operations such as parallel recovery or the processing of `GV$` queries.

##### Oracle GoldenGate and Oracle RAC

Oracle GoldenGate takes advantage of Oracle RAC features.

When Oracle GoldenGate is configured in an Oracle RAC environment, each queue table has an owning instance. If the instance that hosts a queue table fails, another instance in the Oracle RAC database becomes the owning instance for the queue table, allowing Oracle GoldenGate to continue operating.

Also, on an Oracle RAC database, a service is created for each buffered queue. This service always runs on the owner instance of the destination queue and follows the ownership of this queue if the ownership switches because of instance startup, instance shutdown, and so on. This service is used by queue-to-queue propagations.

#### Service Characteristics

When you create new services for your database, you should define the automatic workload management characteristics for each service. The characteristics of a service include:

- Service Name

- Service Edition

- Service Management Policy

- Database Role for a Service

- Instance Preference

- Server Pool Assignment

- Load Balancing Advisory Goal for Run-time Connection Load Balancing

- Connection Load Balancing Goal

- Distributed Transaction Processing

- [Failing Over OCI Clients with TAF](ensuring-application-continuity.md)

##### Service Name

The service name is used by clients to connect to one or more instances.

Each service has a service name. The service name must be unique throughout your system.

The service name must meet the following qualifications:

- The name must consist of alphanumeric characters (a-z, A-Z, 0-9), underscore (\_), and hyphen (-).
- The service domain portion of the name must consist of alphanumeric characters (a-z, A-Z, 0-9), underscore (\_), dollar sign (\$), number sign (#), period (.), and hyphen (-)
- A domain qualified service name is of the form service_name.service_domain.
- You cannot create a service with the same name as the database default service, which is db_unique_name.db_domain.

##### Service Edition

Edition-based redefinition of database objects enables you to upgrade an application's objects while these objects are in use. You can set the edition attribute of a database service when you create it, or modify an existing service to set the edition. When you set the service edition, connections that use this service use this edition as the initial session edition. If the service does not specify the edition name, then the initial session edition is the database default edition.

You can set the service edition using SRVCTL, as follows:

    $ srvctl modify service –db hr –s crmsrv –edition e2

##### Service Management Policy

When you use Oracle Clusterware to manage your database, you can configure startup options for each individual database service when you add the service using the `srvctl add service` command with the `-policy` parameter.

If you set the management policy for a service to `AUTOMATIC` (the default), then the service starts automatically when you start the database with SRVCTL. If you set the management policy to `MANUAL`, then the service does not automatically start, and you must manually start it with SRVCTL. A `MANUAL` setting does not prevent Oracle Clusterware from monitoring the service when it is running and restarting it if a failure occurs. Before Oracle RAC 11g release 2 (11.2), all services worked as though they were defined with a `MANUAL` management policy.

Using CRSCTL to stop and restart Oracle Clusterware is treated as a failure and the service is restarted if it was previously running.

**Note:**

When you use automatic services in an administrator-managed database, during planned database startup, services may start on the first instances to start rather than their preferred instances, provided that the started instances are in the (combined) preferred and available services list.

**Related Topics**

- [srvctl add service](server-control-utility-reference.md)

##### Database Role for a Service

If you configured Oracle Data Guard in your environment, then you can define a role for services when you add or modify a service using SRVCTL and the `-role` parameter with the appropriate command.

When you specify a role for a service, Oracle Clusterware automatically starts the service only when the database role matches the role you specified for the service. Valid roles are `PRIMARY`, `PHYSICAL_STANDBY`, `LOGICAL_STANDBY`, and `SNAPSHOT_STANDBY` and you can specify more than one role for a service.

**Note:**

The service role only controls automatic startup of services. Using SRVCTL to manually start a service will succeed even if the roles do not match.

Redo Apply (physical standby database) can run on all or some standby instances that you can configure. This enables Redo Apply performance to scale, if necessary, by adding additional standby instances.

If multiple databases in the cluster offer the same service name, then Oracle RAC balances connections to that service across all such databases. This is useful for standby and active Oracle Data Guard databases, but if you want client connections to a service to be directed to a particular database, then the service name must be unique within the cluster (not offered by any other database).

**Related Topics**

- [Oracle Data Guard Concepts and Administration](../sbydb/configuring-data-guard-standby-databases-in-oracle-RAC.md)

##### Instance Preference

When you define a service for an administrator-managed database, you define which instances normally support that service using SRVCTL with the `-preferred` parameter.

These are known as the preferred instances. You can also define other instances to support a service if the service's preferred instance fails using SRVCTL with the `-available` parameter. These are known as available instances.

When you specify preferred instances, you are specifying the number of instances on which a service normally runs. This is the maximum cardinality of the service. Oracle Clusterware attempts to ensure that the service always runs on the number of instances for which you have configured the service. Afterward, due to either instance failure or planned service relocations, a service may be running on an available instance.

If an instance fails, then, because Oracle Clusterware interprets the preferred and available lists as ordered lists, you have some control to which available instance Oracle Clusterware relocates the services, if there are multiple instances in the lists. During a planned operation, however, you can manually direct the service to any instance in either the preferred or the available list not currently offering the service.

When a service moves to an available instance, Oracle Database does not automatically move the service back to the preferred instance when the preferred instance restarts because:

- The service is running on the desired number of instances.
- Maintaining the service on the current instance provides a higher level of service availability.
- Not moving the service back to the initial preferred instance prevents a second outage.

Starting with Oracle Database release 19.3, if you specify `yes` for the `-failback` attribute of a service, then, after failing over to an available instance when the last preferred instance went down, the service transfers back to a preferred instance when one becomes available. For earlier releases, you can automate fail back to the preferred instance by using FAN callouts.

**Related Topics**

- [Tools for Administering Oracle RAC](administering-database-instances-and-cluster-databases.md)

##### Service Co-location

Oracle RAC routes clients with the same `COLOCATION_TAG` to the same database instance, when possible.

Co-location of sessions on the same instance can help decrease inter-instance communication and increase performance for workloads that benefit from being executed in the same instance. You configure the `COLOCATION_TAG` in the `CONNECT_DATA` parameter of the TNS connect string used by the service as described in Oracle Database Net Services Reference.

**Related Topics**

- [COLOCATION_TAG](../netrf/local-naming-parameters-in-tns-ora-file.md)

##### Server Pool Assignment

When you define services for a policy-managed database, you assign the service to a server pool in which the database is hosted using SRVCTL with the `-serverpool` parameter.

You can define the service as either `UNIFORM` (running on all instances in the server pool) or `SINGLETON` (running on only one instance in the server pool) using the `-cardinality` parameter. For singleton services, Oracle RAC chooses on which instance in the server pool the service is active. If that instance fails, then the service fails over to another instance in the server pool. A service can only run in one server pool and Oracle recommends that every server pool has at least one service.

**Note:**

Oracle Database Quality of Service Management (Oracle Database QoS Management) manages singleton services in a server pool, if the maximum size of that server pool is one.

**Related Topics**

- [Tools for Administering Oracle RAC](administering-database-instances-and-cluster-databases.md)

##### Load Balancing Advisory Goal for Run-time Connection Load Balancing

With run-time connection load balancing, applications can use load balancing advisory events to provide better service to users. Oracle JDBC, Oracle Universal Connection Pool for Java, OCI session pool, ODP.NET, and Oracle WebLogic Server Active GridLink for Oracle RAC clients are automatically integrated to take advantage of load balancing advisory events. The load balancing advisory informs the client about the current service level that an instance is providing for a service. To enable the load balancing advisory, use SRVCTL with the `-rlbgoal` parameter when creating or modifying the service.

The load balancing advisory also recommends how much of the workload should be sent to that instance. The goal determines whether connections are made to the service based on best service quality (how efficiently a single transaction completes) or best throughput (how efficiently a complete job or long-running query completes).

##### Connection Load Balancing Goal

Oracle Net Services provides connection load balancing to enable you to spread user connections across all of the instances that are supporting a service.

For each service, you can use SRVCTL to define the method you want the listener to use for load balancing by setting the connection load balancing goal, specified with the `-clbgoal` parameter. Connections are classified as `LONG` (such as connection pools and SQL\*FORMS), which tells the listener to use session count, or `SHORT`, which tells the listener to use response-time or throughput statistics.

If load balancing advisory is enabled (the `-rlbgoal` parameter does not equal `NONE`), then connection load balancing attempts to use load balancing advisory (whether load balancing goal is set to `SHORT` or `LONG`). If load balancing is set to `SHORT`, then it uses the `GOODNESS` value of a service to try to prevent all connection requests from going to one instance. If load balancing is set to `LONG`, then it uses `run queue length` if the service is singleton, or `session count` if the service is uniform. A singleton service runs on only one server instance in the server pool, however a uniform service runs on all server instances in the server pool.

##### Distributed Transaction Processing

[Oracle XA](glossary.md) applications have unique requirements. Oracle provides global transactions across Oracle RAC. For best performance, use XA affinity (all branches at the same instance) for most transactions, and global transactions when needed. You can use XA affinity with connection pools, such as Universal Connection Pools and WebLogic Server. You can also use singleton services that you create using SRVCTL. Use SRVCTL, as well, to set the distributed transaction processing parameter (`-dtp`) to `TRUE` if you are suspending and resuming the same Oracle XA branch. Do not use this in general, however, because it does not offer rolling planned maintenance.

**Related Topics**

- Distributed Transaction Processing in Oracle RAC
- [srvctl add service](server-control-utility-reference.md)

#### Default Service Connections

Your Oracle RAC database includes an Oracle database service identified by `DB_UNIQUE_NAME`, if set, or `DB_NAME` or `PDB_NAME`, if not. This default service is always available on all instances in an Oracle RAC environment, unless an instance is in restricted mode. You cannot alter this service or its properties. Additionally, the database supports the following two internal services:

- `SYS$BACKGROUND` is used by the background processes only

- `SYS$USERS` is the default service for user sessions that are not associated with any application service

All of these services are used for internal management. You cannot stop or disable any of these internal services to do planned outages or to failover to Oracle Data Guard. Do not use these services for client connections.

**Note:**

You can explicitly manage only the services that you create. If a feature of the database creates an internal service, you cannot manage it using the information in this chapter.

#### Restricted Service Registration

This feature allows listener registration only from local IP addresses, by default, and provides the ability to configure and dynamically update a set of IP addresses or subnets from which registration requests are allowed by the listener.

Security is a high priority to all enterprises, and network security and controlling access to the database is a critical component of overall security endeavours. Database Instance registration with a listener succeeds only when the request originates from a valid node. The network administrator can specify a list of valid nodes, excluded nodes, or disable valid node checking. The list of valid nodes explicitly lists the nodes and subnets that can register with the database. The list of excluded nodes explicitly lists the nodes that cannot register with the database. The control of dynamic registration results in increased manageability and security of Oracle RAC deployments.

By default, valid node checking for registration (VNCR) is enabled. In the default configuration, the listener accepts registration requests only from the nodes that are in the subnet of the SCAN listener and have access to the private network. Non-SCAN listeners only accept registration from instances on the local node. You must manually include remote nodes or nodes outside the subnet of the SCAN listener on the list of valid nodes by using the `registration_invited_nodes_``alias` parameter in the `listener.ora` file or by modifying the SCAN listener using SRVCTL, as follows:

    $ srvctl modify scan_listener -invitednodes node_list -invitedsubnets subnet_list

**Note:**

Starting with Oracle Grid Infrastructure 12c, for a SCAN listener, if the `VALID_NODE_CHECKING_REGISTRATION_``listener_name` and `REGISTRATION_INVITED_NODES_``listener_name` parameters are set in the `listener.ora` file, then the listener agent overwrites these parameters.

If you use the SRVCTL utility to set the `invitednodes` and `invitedsubnets` values, then the listener agent automatically sets `VALID_NODE_CHECKING_REGISTRATION_``listener_name` to SUBNET and sets `REGISTRATION_INVITED_NODES_``listener_name` to the specified list in the `listener.ora` file.

For other listeners managed by CRS, the listener agent sets `VALID_NODE_CHECKING_REGISTRATION_``listener_name` in the `listener.ora` file only if it is not already set in the `listener.ora` file. The SRVCTL utility does not support setting the `invitednodes` and `invitedsubnets` values for a non-SCAN listener. The listener agent does not update `REGISTRATION_INVITED_NODES_``listener_name` in the `listener.ora` file for a non SCAN listener.

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md)

### Administering Services

You can create and administer services with Oracle Enterprise Manager and the SRVCTL utility. The following sections describe how to perform service-related tasks using these tools:

This section includes the following topics:

- Overview of Service Administration

- Administering Services with Oracle Enterprise Manager

- Administering Services with SRVCTL

**Note:**

You can also use the DBMS_SERVICE package to create or modify services and service attributes, but SRVCTL will override any settings made using this package. The DBMS_SERVICE package is not recommended for use with services used by an Oracle RAC database, nor when Oracle Restart is used, nor when Oracle Clusterware is managing a single-instance database.

#### Overview of Service Administration

When you create and administer services, you are dividing the work that your database performs into manageable units.

The goal of using services is to achieve optimal utilization of your database infrastructure. You can create and deploy services based on business requirements. Oracle Database can measure the performance for each service. Using the `DBMS_MONITOR` package, you can define both the application modules within a service and the individual actions for a module and monitor thresholds for these actions, enabling you to manage workloads to deliver capacity on demand.

When you create new services for your database, you should define the automatic workload management characteristics for each service, as described in "Service Characteristics".

**See Also:**

Oracle Database Quality of Service Management User's Guide if you are using Oracle Database QoS Management with your Oracle cluster for details on how to configure the database services

In addition to creating services, you can:

- Delete a service. You can delete services that you created. However, you cannot delete or modify the properties of the default database service that Oracle Database created.

- Check the status of a service. A service can be assigned different roles among the available instances. In a complex database with many services, you may not remember the details of every service. Therefore, you may have to check the status on an instance or service basis. For example, you may have to know the status of a service for a particular instance before you make modifications to that instance or to the Oracle home from which it runs.

- Start or stop a service for a database or an instance. A service must be started before it can be used for client connections to that instance. If you shut down your database, for example, by running the SRVCTL command `srvctl stop database -db` `db_unique_name` where `db_unique_name` is the name of the database you want to stop, then Oracle Database stops all services for that database. Depending on the service management policy, you may have to manually restart the services when you start the database. Both the `srvctl stop database` and `srvctl stop service` commands accept the `-force` option to forcibly disconnect connections. To drain sessions for planned outages do not use the `-force` option.

  **Note:**

  If Oracle Database QoS Management is enabled for the Oracle RAC database, then the services are automatically restarted after they are stopped.

- Map a service to a consumer group. You can map services to Resource Manager Consumer groups to limit the amount of resources that services can use in an instance. You must create the consumer group and then map the service to the consumer group.

- Enable or disable a service for a database or an instance. By default, Oracle Clusterware attempts to restart a service automatically after failures. You can prevent this behavior by disabling a service. Disabling a service is useful when you must perform database or instance maintenance, such as when you are performing an upgrade and you want to prevent connection requests from succeeding.

- Relocate a service to a different instance. You can move a service from one instance to another instance to re-balance workloads, for example, after adding or deleting cluster nodes.

**Note:**

- When you use services, do not set a value for the `SERVICE_NAMES` parameter; Oracle Database controls the setting for this parameter for the services that you create and for the default database service. The service features that this chapter describes are not directly related to the features that Oracle Database provides when you set `SERVICE_NAMES`. In addition, setting a value for this parameter may override some benefits of using services.

- Service status information must be obtained from SRVCTL or from the service-related database views, such as `dba_services`.

- If you specify a service using the `DISPATCHERS` initialization parameter, it overrides any service in the `SERVICE_NAMES` parameter, and cannot be managed. (For example, stopping the service with a SRVCTL command does not stop users connecting with the service.)

**Related Topics**

- Enabling Clients for Oracle RAC
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md)

#### Administering Services with Oracle Enterprise Manager

The Cluster Managed Database Services page is the master page for beginning all tasks related to services.

Access this page, as follows:

1.  In Oracle Enterprise Manager, go to the Cluster Database Home page.

    **See Also:**

    Oracle Database 2 Day DBA for details on logging in to Oracle Enterprise Manager.

2.  From the Availability menu, select Cluster Managed Database Services to display the Cluster Managed Database Services page.

3.  Enter or confirm the credentials for the Oracle RAC database and host operating system and click Continue to display the Cluster Managed Database Services page.

From the Cluster Managed Database Services page you can drill down to perform the following tasks:

- View a list of services for the cluster

- View the instances on which each service is currently running

- View the server pool and nodes offering the service in a policy-managed environment

- View the status for each service

- Create or edit a service

- Start or stop a service

- Enable or disable a service

- Perform instance-level tasks for a service

- Delete a service

**Note:**

You must have `SYSDBA` credentials to access a cluster database. Cluster Managed Database Services does not permit you to connect as anything other than `SYSDBA`.

**Related Topics**

- [Oracle Database 2 Day DBA](../admqs/getting-started-with-database-administration.md)

**See Also:**

Oracle Enterprise Manager online help for more information about administering services with Oracle Enterprise Manager

#### Administering Services with SRVCTL

When you create a service using SRVCTL, you must start the service with a separate SRVCTL command.

However, you may later have to manually stop or restart the service. You may also have to disable the service to prevent automatic restarts, to manually relocate the service, or obtain status information about the service. The following sections explain how to use SRVCTL to perform the following administrative tasks:

- Creating Services with SRVCTL

- Creating Services for Application Continuity and Transaction Guard

- Starting and Stopping Services with SRVCTL

- Enabling and Disabling Services with SRVCTL

- Relocating Services with SRVCTL

- Obtaining the Status of Services with SRVCTL

- Obtaining the Configuration of Services with SRVCTL

##### Creating Services with SRVCTL

To create a service with SRVCTL, use the `srvctl add service` command on the command line.

**Related Topics**

- [srvctl add service](server-control-utility-reference.md)

##### Creating Services for Application Continuity and Transaction Guard

To configure services for Application Continuity, when you create a service using SRVCTL, set the `-failovertype` parameter to `TRANSACTION` and `-commit_outcome` to `TRUE`.

When using Application Continuity and Transaction Guard with your applications, you must configure a service. This section describes how to configure these application services depending on the functionality you plan to implement.

##### Creating Services for Application Continuity

Additionally, you can set values for these other service parameters for Application Continuity and load balancing:

- `-replay_init_time`: Specifies how long, in seconds, you allow replay to start. Oracle recommends that you choose a value based on how long you will allow replay to be initiated. The default value is 300 seconds.

- `-retention`: Specifies the time (in seconds) that the commit outcome information is stored in the database. The default value is 86400 (1 day).

- `-session_state`: After a COMMIT has executed, if the state was changed in that transaction, then it is not possible to replay the transaction to reestablish that state if the session is lost. When configuring Application Continuity, the applications are categorized depending on whether the session state after the initial setup is dynamic or static, and then whether it is correct to continue past a COMMIT operation within a request.

  - Dynamic: (default) A session has a dynamic state if the session state changes are not fully encapsulated by the initialization, and cannot be fully captured in a callback at failover. Once the first transaction in a request commits, failover is internally disabled until the next request begins. This is the default mode that almost all applications should use for requests.

  - Static: (special—on request) A session has a static state if all session state changes, such as NLS settings and PL/SQL package state, can be repeated in an initialization callback. This setting is used only for database diagnostic applications that do not change session state. Do not specify `STATIC` if there are any non-transactional state changes in the request that cannot be reestablished by a callback. If you are unsure what state to specify, use `DYNAMIC`.

- `-failoverretry`: Number of connection retries for each connection attempt; recommended value is 30.

- `-failoverdelay`: Delay in seconds between each connection attempt; recommended value is 10.

- `-notification`: FAN is highly recommended—set this value to `TRUE` to enable FAN for OCI and ODP.Net clients.

- `-clbgoal`: For connection load balancing, use `SHORT` when using run-time load balancing.

- `-rlbgoal`: For run-time load balancing, set to `SERVICE_TIME`.

To create a service for Application Continuity for a policy-managed Oracle RAC database, use a command similar to the following, where `racdb` is the name of your Oracle RAC database, `app2` is the name of the service you are modifying, and `Svrpool1` is the name of the server pool in which the service is offered:

    $ srvctl add service -db racdb -service app2 -serverpool Srvpool1
      -failovertype TRANSACTION -commit_outcome TRUE -replay_init_time 1800
      -retention 86400 -notification TRUE -rlbgoal SERVICE_TIME -clbgoal SHORT
      -failoverretry 30 -failoverdelay 10

You can use SRVCTL to modify an existing service for Application Continuity, similar to the following command, where `racdb` is the name of your Oracle RAC database, and `app1` is the name of the service you are modifying:

    $ srvctl modify service -db racdb -service app1 -clbgoal SHORT
      -rlbgoal SERVICE_TIME -failoverretry 30 -failoverdelay 10
      -failovertype TRANSACTION -commit_outcome TRUE -replay_init_time 1800
      -retention 86400 -notification TRUE

##### Creating Services for Transaction Guard

To enable Transaction Guard, but not Application Continuity, create the service using SRVCTL and set only `-commit_outcome TRUE`.

You can use SRVCTL to modify an existing service to enable Transaction Guard, similar to the following command, where `racdb` is the name of your Oracle RAC database, and `app2` is the name of the service you are modifying:

    $ srvctl modify service -db racdb -service app2 -commit_outcome TRUE
      -retention 86400 -notification TRUE

In the preceding example, the `-retention` parameter specifies how long, in seconds, to maintain the history. Additionally the `–notification` parameter is set to `TRUE`, enabling FAN events.

To use Transaction Guard, a DBA must grant permission, as follows:

    GRANT EXECUTE ON DBMS_APP_CONT;

**Related Topics**

- [Oracle Database Development Guide](../adfns/transaction-guard.md)

##### Starting and Stopping Services with SRVCTL

For applications to connect using a server, the service must be started. If you stop a service, then it is temporarily unavailable, but is still subject to automatic restart and failover.

Enter the following SRVCTL syntax at the command line to start or stop a service:

    $ srvctl start service -db db_unique_name [-service service_name_list]
        [-instance inst_name] [-startoption start_options]

    $ srvctl stop service -db db_unique_name -service service_name_list
        [-instance inst_name] [-startoption start_options]

##### Enabling and Disabling Services with SRVCTL

If you disable a service, then Oracle Clusterware does not consider the service for automatic startup, failover, or restart. You might disable a service when performing application maintenance, to ensure the service is not accidentally restarted by Oracle Clusterware until your maintenance operations are complete. To make the service available for normal operation again, you enable the service.

Use the following SRVCTL syntax from the command line to enable and disable services:

    $ srvctl enable service -db db_unique_name -service service_name_list
        [-instance inst_name]

    $ srvctl disable service -db db_unique_name -service service_name_list
        [-instance inst_name]

##### Relocating Services with SRVCTL

Run the `srvctl relocate service` command from the command line to relocate a service. You might use this command when a service has failed over to an available instance, but you want to move it back to the preferred instance after that instance is restarted.

The following command relocates the `crm` service from instance `apps1` to instance `apps3`:

    $ srvctl relocate service -db apps -service crm -oldinst apps1 -newinst apps3

The following command relocates the `crm` service from `node1` to `node3` using node syntax:

    $ srvctl relocate service -db apps -service crm -currentnode node1
        -targetnode node3

##### Obtaining the Status of Services with SRVCTL

Run the `srvctl status service` command from the command line to obtain the status of a service. For example, the following command returns the status of the services that are running on the `apps` database:

    $ srvctl status service -db apps

    Service erp is running on nodes: apps02,apps03
    Service hr is running on nodes: apps02,apps03
    Service sales is running on nodes: apps01,apps04

##### Obtaining the Configuration of Services with SRVCTL

Run the `srvctl config service` command from the command line to obtain the high availability configuration of a service. For example, the following command returns the configuration of the `erp` service that is running on the `apps` database:

    $ srvctl config service -db apps -service erp

    Service name: erp
    Service is enabled
    Server pool: pool1
    Cardinality: 1
    Disconnect: false
    Service role: PRIMARY
    Management policy: AUTOMATIC
    DTP transaction: false
    AQ HA notifications: true
    Global: false
    Commit Outcome: true
    Failover type: TRANSACTION
    Failover method: NONE
    TAF failover retries: 30
    TAF failover delay: 10
    Connection Load Balancing Goal: LONG
    Runtime Load Balancing Goal: SERVICE_TIME
    TAF policy specification: NONE
    Edition:
    Pluggable database name:
    Maximum lag time: ANY
    SQL Translation Profile:
    Retention: 86400 seconds
    Replay Initiation Time: 1800 seconds
    Session State Consistency: STATIC
    Preferred instances: apps
    Available instances:

### Global Services

Oracle RAC supports database services and enables service-level workload management across instances in a single cluster.

Global services provide dynamic load balancing, failover, and centralized service management for a set of replicated databases that offer common services. The set of databases may include Oracle RAC and non-clustered Oracle databases interconnected by Oracle Data Guard, Oracle GoldenGate, or any other replication technology.

When you create and use global services, the following workload management features are available:

- Ability to specify preferred and available databases for a global service

- Handling of replication lag

- Geographical affinity between clients and servers

- Connection load balancing

- Run-time load balancing

- Inter-database service failover

- Fast connection failover

- Connect-time failover

- Application Continuity

- Transaction Guard

- Backward compatibility with existing clients

**Note:**

You can manage instance placement of a global service within an Oracle RAC database with SRVCTL but you can only manage other global service attributes with GDSCTL.

**Related Topics**

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/global-data-services-config.md)

### Service-Oriented Buffer Cache Access

Service-oriented buffer cache access improves performance by managing data with the service to which the data belongs.

Access of an object, over time, through a service is mapped and persisted to the database, and this information can be used to improve performance. Blocks that are accessed through the service are cached in the instances where the services are running and, more importantly, the information is not cached where the services are not running.

This information can also be used to pre-warm the cache prior to a service starting. The service start-up can be triggered either by instance start-up or by service relocation. Service-oriented buffer cache access provides consistent performance to any user of that service because the blocks that the service user accesses are cached in the new relocated instance.

### Connecting to a Service: An Example

The following example illustrates how to create a service and then gives several examples of connecting to that service using different client methods.

In this example the service is enabled for run-time load balancing, as follows:

- Service Name: `HR.example.com`

  - Running on database named CRM

  - The system consists of 4 nodes

- Specifying `SERVICE_TIME` as the value for the `-rlbgoal` parameter

- SCAN address of the listener is `rws3010104-scan.example.com`

- Listener port is 1585

The service has a cardinality of two, but if needed, can be offered by any of the CRM database instances. The service configuration is as follows:

- Preferred Instances: CRM1, CRM2

- Available Instances: CRM3, CRM4

- Specifying `SHORT` as the value for the `-clbgoal` parameter

The application using this service takes advantage of Application Continuity, so you must set `-failovertype` and `-commit_outcome`. Use the default retention parameters, but set a 10 second delay between connection attempts, and up to 40 retries before failing to get a connection.

#### Creating the HR Service Using SRVCTL

Create the HR service using SRVCTL, as follows:

    $ srvctl add service –db CRM –service HR.example.com –preferred CRM1,CRM2
      –available CRM3,CRM4 –clbgoal SHORT –failovertype TRANSACTION
      –commit_outcome TRUE –failoverdelay 10 –failoverretry 40

Start the `HR.example.com` service, as follows:

    $ srvctl start service –db CRM –service HR.example.com

The service is now be available on up to two instances, and CRM1 and CRM2 are the preferred instances.

#### Connecting to the HR Service from a JDBC Application

The application that connects to the HR service, in this example, is a JDBC application using the JDBC Universal Connection Pool with the JDBC thin driver.

In this example, a URL is constructed specifying the thin-style service name format for the database specifier. Fast Connection Failover is enabled, and remote Oracle Notification Service is configured, where the Oracle Notification Service daemon on the cluster listens on port 6200.

    //import packages and register the driver
    import java.sql.Connection;
    import java.sql.SQLException;
    import java.sql.Statement;
    import oracle.ucp.jdbc.PoolDataSourceFactory;
    import oracle.ucp.jdbc.PoolDataSource;

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    //set the connection properties on the data source.
    pds.setConnectionPoolName("FCFPool");
    pds.setFastConnectionFailoverEnabled(true);
    pds.setONSConfiguration("nodes=rws3010104-scan.example.com:6200");
    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL("jdbc:oracle:thin:@//rws3010104-scan.example.com:1585/HR.example.com");
    pds.setUser("HR");
    pds.setPassword("hr");


    //Override any pool properties.
    pds.setInitialPoolSize(5);

    //Get a database connection from the datasource.

    Connection conn = pds.getConnection();

    // do some work

    //return connection to pool
    conn.close();
    conn=null

**Related Topics**

- [Oracle Universal Connection Pool Developer’s Guide](../jjucp/intro.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

Run-time connection load balancing is basically routing work requests to sessions in a session pool that can best serve the work. It comes into effect when selecting a session from an existing session pool. Thus, run-time connection load balancing is a very frequent activity.
