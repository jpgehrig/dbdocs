This section contains the following subsections:

- Overview of Fast Connection Failover

- What is Fast Connection Failover

- Fast Connection Failover Prerequisites

- Example of Fast Connection Failover Configuration

- Enabling Fast Connection Failover

- What is ONS

- Configuring the Connection URL

### 9.2.1 Overview of Fast Connection Failover

The Fast Connection Failover (FCF) feature is a Fast Application Notification (FAN) client implemented through the connection pool. The feature requires the use of an Oracle JDBC driver and high availability (HA) database configurations like Oracle RAC, Single Restart, or Active Data Guard.

**Note:**

This section describes only the steps that an application must perform when using FCF with Oracle RAC.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md) for more information

FCF is useful in the following scenarios:

- Unplanned Outages: FCF rapidly detects dead connections,, and then terminates and removes them from the pool. Connection removal relies on terminating the sever-socket connections rapidly to prevent the system from becoming nonresponsive. Borrowed and in-use connections are interrupted only for unplanned outages.

- Planned Outages: FCF does not interrupt and close the borrowed or in-use connections until work is done and control of the connection is returned to the pool.

- Fatal Connection Errors and Exceptions: FCF encapsulates fatal connection errors and exceptions into the `isValid` API for robust and efficient retries.

- Addition of New Nodes to the Cluster: FCF recognizes the new nodes that join an Oracle RAC cluster and places new connections on that node appropriately for delivering maximum quality of service to applications at run time. This facilitates middle-tier integration of Oracle RAC node joins and work-request routing from the application tier.

- Run-Time Work Requests: FCF distributes run-time work requests to all active Oracle RAC instances.

#### Unplanned Shutdown Scenarios

FCF supports unplanned shutdown scenarios by detecting and removing stale connections to an Oracle RAC cluster. Stale connections include connections that do not have a service available on any instance in an Oracle RAC cluster due to service-down and node-down events. Borrowed connections and available-but-stale connections are detected, and their network connection is severed before removing them from the pool. These removed connections are not replaced by the pool. Instead, the application must retry connections before performing any work with a connection.

**Note:**

Borrowed connections are immediately terminated and closed during unplanned shutdown scenarios. Any on-going transactions immediately receive an exception.

#### Planned Shutdown Scenarios

FCF supports planned shutdown scenarios where an Oracle RAC service can be gracefully shutdown. In such scenarios, stale borrowed connections are marked, and are terminated and removed after they are returned to the pool. Any on-going transactions do not see any difference and proceed to complete.

The primary difference between unplanned and planned shutdown scenarios is how borrowed connections are handled. Stale connections that are idle in the pool (not borrowed) are removed in the same manner as the unplanned shutdown scenario.

UCP also supports graceful connection draining from any planned-down Oracle RAC instance. Affected borrowed connections are removed smoothly over a grace period, instead of immediate removal upon their return to the pool. This helps in avoiding throughput impact and logon storms during any service relocation.

#### Oracle RAC Instance Rejoin and New Instance Scenarios

FCF supports scenarios where an Oracle RAC cluster adds instances that provide a service of interest. The instance may be new to the cluster or may have been restarted after a down event. In both cases, UCP recognizes the new instance and creates connections to the node as required.

**Related Topics**

- [Checking If a Connection Is Valid](validating-ucp-connections.md)
- Enabling Fast Connection Failover

### 9.2.2 What is Fast Connection Failover?

After Fast Connection Failover is enabled, the mechanism is automatic; no application intervention is needed. This section discusses how a connection failover is presented to an application and what steps the application takes to recover, in the following sections:

- What the Application Sees

- How FCF Works

#### 9.2.2.1 What the Application Sees

By the time an Oracle RAC service failure is propagated to the JDBC application, the database already rolls back the local transaction. The cache manager then cleans up all invalid connections. When an application holding an invalid connection tries to do work through that connection, it is possible to receive `SQLException, ORA-17008, Closed Connection`.

When an application receives a `Closed Connection` error message, it should do the following:

1.  Retry the connection request. This is essential, because the old connection is no longer open.

2.  Replay the transaction. All work done before the connection was closed has been lost.

**Note:**

The application should not try to roll back the transaction. The transaction was already rolled back in the database by the time the application received the exception.

#### 9.2.2.2 How FCF Works

Under Fast Connection Failover, each connection in the cache maintains a mapping to a service, instance, database, and host name.

When a database generates an Oracle RAC event, that event is forwarded to the JVM in which JDBC is running. A daemon thread inside the JVM receives the Oracle RAC event and passes it on to the Connection Cache Manager. The Connection Cache Manager then throws SQL exceptions to the applications affected by the Oracle RAC event.

A typical failover scenario may work like the following:

1.  A database instance fails, leaving several stale connections in the cache.

2.  The Oracle RAC mechanism in the database generates an Oracle RAC event which is sent to the JVM containing JDBC.

3.  The daemon thread inside the JVM finds all the connections affected by the Oracle RAC event, notifies them of the closed connection through SQL exceptions, and rolls back any open transactions.

4.  Each individual connection receives a SQL exception and must retry.

### 9.2.3 Fast Connection Failover Prerequisites

Fast Connection Failover is available under the following circumstances:

- The Universal Connection Pool is enabled.

  Fast Connection Failover works in conjunction with the JDBC connection caching mechanism. This helps applications manage connections to ensure high availability.

- The application uses service names to connect to the database.

  The application cannot use service identifiers.

- The underlying database has Oracle Database 12c Release 1 (12.1) or later Real Application Clusters (Oracle RAC) capability or Oracle Data Guard configured with either single instance Databases or Oracle RAC.

  If failover events are not propagated, then connection failover cannot occur.

- Oracle Notification Service (ONS) is configured and available on the node where JDBC is running.

  JDBC depends on ONS to propagate database events and notify JDBC of them.

- The Java Virtual Machine (JVM) in which your JDBC instance is running must have `oracle.ons.oraclehome` set to point to your `ORACLE_HOME`.

### 9.2.4 Example of Fast Connection Failover Configuration

The following example demonstrates a connection pool that uses the FCF feature. FCF is configured through a pool-enabled data source. The example includes enabling FCF, configuring the Oracle Notification Service (ONS) and configuring a connection URL. These topics are discussed after the example.

The `isValid` method of the `oracle.ucp.jdbc.ValidConnection` interface is typically used in conjunction with the FCF feature and is used to check if a borrowed connection is still usable after an SQL exception has been thrown due to an Oracle RAC down event. For example:

    try {  conn = pds.getConnection;  ...}catch (SQLException sqlexc)
    {
       if (conn == null || !((ValidConnection) conn).isValid())

       // take the appropriate action

    ...
    conn.close();
    }

Example 9-1 Fast Connection Failover Configuration Example

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionPoolName("FCFSamplePool");
    pds.setFastConnectionFailoverEnabled(true);
    pds.setONSConfiguration("nodes=racnode1:4200,racnode2:4200\nwalletfile=
    /oracle11/onswalletfile");
    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL("jdbc:oracle:thin@(DESCRIPTION= "+
       "(LOAD_BALANCE=on)"+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=racnode1) (PORT=1521))"+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=racnode2) (PORT=1521))"+
       "(CONNECT_DATA=(SERVICE_NAME=service_name)))");
    ...

**Related Topics**

- [Checking If a Connection Is Valid](validating-ucp-connections.md)

### 9.2.5 Enabling Fast Connection Failover

The FCF pool property is used to enable and disable FCF. FCF is disabled by default. The following example demonstrates enabling FCF as shown in Example 9-1.

    pds.setFastConnectionFailoverEnabled(true);

**Note:**

Starting from Oracle Database 12c Release 1 (12.1.0.2), UCP supports the `oracle.ucp.PlannedDrainingPeriod` system property. It specifies the grace time period (in integer seconds) over which the pool smoothly drains the borrowed connections affected by a planned shut down. Draining starts when the same Database service becomes available on another instance different from the one that is going down.

When this property is not set, or set to `0`, then the pool closes any affected borrowed connection immediately when it is returned to the pool.

#### Querying Fast Connection Failover Status

An application determines if Fast Connection Failover is enabled by calling `OracleDataSource.getFastConnectionFailoverEnabled`, which returns `true` if failover is enabled, `false` otherwise.

**Note:**

FCF must also be enabled to use run-time connection load balancing and connection affinity. These features are discussed later in this chapter.

### 9.2.6 What is ONS?

FCF relies on the Oracle Notification Service (ONS) to propagate database events between the connection pool and the Oracle RAC database. At run time, the connection pool must be able to setup an ONS environment. ONS (`ons.jar`) is included as part of the Oracle Client software. ONS can be configured using either remote configuration or client-side ONS daemon configuration. Remote configuration is the preferred configuration for standalone client applications. This section discusses the following topics:

- Overview of ONS Configuration File

- Remote Configuration of ONS

- Configuration of Client-Side ONS Daemon

#### 9.2.6.1 Overview of ONS Configuration File

ONS configuration is controlled by the ONS configuration file, `ORACLE_HOME``/opmn/conf/ons.config`. This file tells the ONS daemon how it should behave. Configuration information within `ons.config` is defined in simple name and value pairs.

Some parameters in the `ons.config` file are required and some are optional. Table 9-2 lists the required ONS configuration parameters and Table 9-3 lists the optional ONS configuration parameters. ONS must be refreshed after updating the `ons.config` file.

Table 9-2 Required ONS Configuration Parameters

| Parameter    | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `localport`  | Specifies the port that ONS binds to on the local host interface to talk to local clients.<br>For example, `localport=4100`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `remoteport` | Specifies the port that ONS binds to on all interfaces for talking to other ONS daemons.<br>For example, `remoteport=4200`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `nodes`      | Specifies a list of other ONS daemons to talk to. Node values are given as a comma-delimited list of either host names or IP addresses plus ports. The port value that is given is the remote port that each ONS instance is listening on. In order to maintain an identical file on all nodes, the `host:port` of the current ONS node can also be listed in the nodes list. It will be ignored when reading the list.<br>For example, `nodes=myhost.example.com:4200,123.123.123.123:4200`<br>The nodes listed in the nodes line correspond to the individual nodes in the Oracle RAC instance. Listing the nodes ensures that the middle-tier node can communicate with the Oracle RAC nodes. At least one middle-tier node and one node in the Oracle RAC instance must be configured to see one another. As long as one node on each side is aware of the other, all nodes are visible. You need not list every single cluster and middle-tier node in the ONS configuration file of each Oracle RAC node. In particular, if one ONS configuration file cluster node is aware of the middle tier, then all nodes in the cluster are aware of it. |

Table 9-3 Optional ONS Configuration Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `logcomp`    | Specifies the ONS components to log. The format is as follows:<br>`<component>[<subcomponent>,...];<component>[<subcomponent>,...];...`<br>If no subcomponents need to be specified, then do not include the brackets (\[\]) after the component name. To exclude messages from a subcomponent, precede the subcomponent name with an exclamation mark (!). For example, to exclude messages from the `topology` subcomponent, you use the following format:<br>`[all,!topology]`<br>Note that before specifying a subcomponent from which you want to exclude messages, you must first ensure that the subcomponent includes the messages.<br>Following are the valid values for components:<br>• `internal`<br>• `ons`<br>If you specify the component as `internal`, then there are no valid values for subcomponent. If you specify the component as `ons`, then you can specify the following values for subcomponent:<br>• `all`: Specifies all messages<br>• `ons`: ONS local information<br>• `listener`: ONS listener information<br>• `discover`: ONS discover (server or multicast) information<br>• `servers`: ONS remote servers currently up and connected to the cluster<br>• `topology`: ONS current cluster wide server connection topology<br>• `server`: ONS remote server connection information<br>• `client`: ONS client connection information<br>• `connect`: ONS generic connection information<br>• `subscribe`: ONS client subscription information<br>• `message`: ONS notification receiving and processing information<br>• `deliver`: ONS notification delivery information<br>• `special`: ONS special notification processing<br>• `internal`: ONS internal resource information<br>• `secure`: ONS SSL operation information<br>• `workers`: ONS worker threads<br>The following example shows that you want to log messages for all the subcomponents under `ons`, except the `secure` subcomponent:<br>`logcomp=ons[all,!secure]` |
| `logfile`    | Specifies a log file that ONS should use for logging messages. The default value for log file is `$ORACLE_HOME/opmn/logs/ons.log`.<br>For example, `logfile=/private/oraclehome/opmn/logs/myons.log`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `walletfile` | Specifies the wallet file used by the Oracle Secure Sockets Layer (SSL) to store SSL certificates. If a wallet file is specified to ONS, then it uses SSL when communicating with other ONS instances and require SSL certificate authentication from all ONS instances that try to connect to it. This means that if you want to turn on SSL for one ONS instance, then you must turn it on for all instances that are connected. This value should point to the directory where your `ewallet.p12` file is located.<br>For example, `walletfile=/private/oraclehome/opmn/conf/ssl.wlt/default`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `useocr`     | Specifies the value, reserved for use on the server-side, to indicate ONS whether it should store all Oracle RAC nodes and port numbers in Oracle Cluster Registry (OCR) instead of the ONS configuration file or not. A value of `useocr=on` is used to store all Oracle RAC nodes and port numbers in Oracle Cluster Registry (OCR).<br>Do not use this option on the client-side.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `allowgroup` | Specifies the ONS setting to indicate the user group connecting to the `localport`. When set to `true`, ONS allows users within the same OS group to connect to its local port. When set to `false`, ONS only allows the same user running the ONS daemon to access its local port. The default value of this parameter is `false`. When using remote ONS configuration, there is no need to set this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

The `ons.config` file allows blank lines and comments on lines that begin with the number sign (`#`).

#### 9.2.6.2 Remote Configuration of ONS

UCP supports remote configuration of ONS through the `ONSConfiguration` pool property. The `ONSConfiguration` pool property value is a string that closely resembles the content of the `ons.config` file. The string contains a list of `name=value` pairs separated by a new line character (`\n`). You can set this pool property in the following two ways:

- The name can be one of the following: `nodes`, `walletfile`, or `walletpassword`. The parameter string should at least specify the ONS configuration `nodes` attribute as a list of `host:port` pairs separated by a comma. SSL is used when the `walletfile` attribute is specified as an Oracle wallet file.

  The following example demonstrates an ONS configuration string as shown in Example 9-1:

      ...
      pds.setONSConfiguration("nodes=racnode1:4200,racnode2:4200\nwalletfile=/oracle11/onswalletfile");
      ...

- The name can be only `propertiesfile`. The value is the location of an ONS-specific Java properties file. This file must contain the `oracle.ons.nodes` property, and one or both of the following ONS Java properties:

  - `oracle.ons.walletfile`

  - `oracle.ons.walletpassword`

    The following example illustrates such an `ONSConfiguration` string:

        pds.setONSConfiguration("propertiesfile=/usr/ons/ons.properties");

    The following is an example of the content of the Java properties `ons.properties` file:

        oracle.ons.nodes=racnode1:4200,racnode2:4200
        oracle.ons.walletfile=/oracle11/onswalletfile

**Note:**

The parameters in the configuration string must match those for the Oracle RAC Database. In addition, if you are using Oracle Application Server, then you must configure ONS using procedures that are applicable to the server.

For standalone Java applications, you must configure ONS using the `setONSConfiguration` method. However, if your application meets the following requirements, then you no longer need to call the `setONSConfiguration` method for enabling FCF:

- Your application is using Oracle Database 12c Release 1 (12.1) or later UCP and Oracle RAC Database 12c Release 1 (12.1) or later

- Your application does not require ONS wallet or keystore

#### 9.2.6.3 Configuration of Client-Side ONS Daemon

Client-side ONS daemon configuration is typical of applications that run on a middle-tier server such as the Oracle Application Server. Clients in this scenario directly configure ONS by updating the `ons.config` file. The location of the file may be different depending on the platform. Example 9-2 demonstrates an `ons.config` file for Example 9-1:

**Note:**

For client-side ONS daemon configuration, if the operating system (OS) user that starts the connection pool and the OS user that starts the client-side daemon are different, then they both must belong to the same OS group. Also, the value of the `allowgroup` parameter must be set to `true` in the `ons.config` file.

After configuring ONS, you start the ONS daemon with the `onsctl` command. You must make sure that an ONS daemon is running at all times.

##### Using the onsctl Command

After configuring, use `ORACLE_HOME``/opmn/bin/onsctl` to start, stop, reconfigure, and monitor the ONS daemon. Table 9-4 is a summary of the commands that `onsctl` supports.

Table 9-4 onsctl Commands

| Command    | Effect                                                                          | Output                                |
|:-----------|:--------------------------------------------------------------------------------|:--------------------------------------|
| `start`    | Starts the ONS daemon                                                           | `onsctl: ons started`                 |
| `stop`     | Stops the ONS daemon                                                            | `onsctl: shutting down ons daemon...` |
| `ping`     | Verifies whether or not the ONS daemon is running                               | `ons is running ...`                  |
| `reconfig` | Triggers a reload of the ONS configuration without shutting down the ONS daemon |                                       |
| `help`     | Prints a help summary message for onsctl                                        |                                       |
| `detailed` | Prints a detailed help message for onsctl                                       |                                       |

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-linux-and-unix-systems.md)

**Note:**

- The Java Virtual Machine (JVM), in which your JDBC instance is running, must have the `oracle.ons.oraclehome` system property set to the location of `ORACLE_HOME` before starting the application. For example:

      java -Doracle.ons.oraclehome=$ORACLE_HOME ...

- Oracle recommends remote configuration of ONS for UCP.

**Note:**

In Oracle RAC 12.1.0.2.0, by default, server installation requires the value of the `walletfile` ONS parameter to be set, and enforces the use of SSL for all ONS connections.

If you have a UCP application that is already using the `walletfile` parameter in the ONS remote configuration string or local configuration file, then the only requirement is that, for the same topology, the wallet file on the client side must have the same content as the wallet file on the server side. You can make a copy of the server-side file and make it available on the client side.

For UCP applications that are using Oracle RAC features without setting the `walletfile` parameter, you must perform one of the following:

- Add the walletfile parameter setting to the ONS remote configuration string or local configuration file, as shown in Example 9-1. Keep in mind that, for the same topology, the wallet file on the client side must have the same content as the wallet file on the Oracle RAC server side.

- Run the following command to remove the `walletfile` parameter setting from both client and server ONS configuration string and the local configuration file:

      srvctl modify nodeapps -clientdata

For secure communication, the ONS auto-configuration in Oracle RAC 12.1.x no longer works when Oracle RAC 12.1.0.2.0 is first installed or patched. Applications have to use explicit ONS configuration (remote or local) instead, and make one of the changes previously discussed.

Example 9-2 Example of a Sample ons.config File

    # This is an example ons.config file
    #
    # The first three values are required
    localport=4100
    remoteport=4200
    nodes=racnode1.example.com:4200,racnode2.example.com:4200

### 9.2.7 Configuring the Connection URL

The connection URL of a connection factory must use the service name syntax when using FCF. The service name is used to map the connection pool to the service. In addition, the factory class must be an Oracle factory class. The following example demonstrates configuring the connection URL as shown in Example 9-1:

    ...
    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL("jdbc:oracle:thin@//host:port/service_name");
    ...

**Note:**

An exception is thrown if a service identifier (SID) is specified for the connection URL when FCF is enabled.

The following examples demonstrate valid connection URL syntax when connecting to an Oracle RAC database. Examples for both the Oracle JDBC thin and Oracle OCI driver are included. Notice that the URL can be used to explicitly enable load balancing among Oracle RAC nodes:

#### Valid Connection URL Usage

    pds.setURL("jdbc:oracle:thin@//host:port/service_name");

    pds.setURL("jdbc:oracle:thin@//cluster-alias:port/service_name");

    pds.setURL("jdbc:oracle:thin:@(DESCRIPTION= "+
       "(LOAD_BALANCE=on)"+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=host1)(PORT=1521))"+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=host2)(PORT=1521))"+
       "(CONNECT_DATA=(SERVICE_NAME=service_name)))");

    pds.setURL("jdbc:oracle:thin:@(DESCRIPTION= "+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=cluster_alias) (PORT=1521)) "+
       "(CONNECT_DATA=(SERVICE_NAME=service_name)))");

    pds.setURL("jdbc:oracle:oci:@TNS_ALIAS");

    pds.setURL("jdbc:oracle:oci:@(DESCRIPTION= "+
       "(LOAD_BALANCE=on) "+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=host1) (PORT=1521)) "+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=host2)(PORT=1521)) "+
       "(CONNECT_DATA=(SERVICE_NAME=service_name)))");

    pds.setURL("jdbc:oracle:oci:@(DESCRIPTION= "+
       "(ADDRESS=(PROTOCOL=TCP)(HOST=cluster_alias) (PORT=1521)) "+
       "(CONNECT_DATA=(SERVICE_NAME=service_name)))");
