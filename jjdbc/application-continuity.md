Application Continuity provides a general purpose, application-independent solution that enables recovery of work from an application perspective, after the occurrence of a planned or unplanned outage. The outage can be related to system, communication, or hardware following a repair, a configuration change, or a patch application.

The outages of the underlying software, hardware, communications, and storage layers can cause application execution to fail. In the worst cases, the middle-tier servers may need to be restarted to deal with the logon storms<sup>Foot 1</sup>. The Application Continuity feature helps to overcome such problems because it masks database outages to the application and end users are not exposed to such outages.

**Note:**

- You must use Transaction Guard for using this feature.

- Application Continuity is a feature of the Oracle JDBC Thin driver and is not supported by JDBC OCI driver.

This chapter discusses the JDBC aspect of Application Continuity in the following sections:

- About Configuring Oracle JDBC for Application Continuity for Java

- About Configuring Oracle Database for Application Continuity for Java

- Application Continuity Support for XA Data Source

- About Identifying Request Boundaries in Application Continuity for Java

- Support for Transparent Application Continuity

- Establishing the Initial State Before Application Continuity Replays

- About Delaying the Reconnection in Application Continuity for Java

- About Retaining Mutable Values in Application Continuity for Java

- Application Continuity Statistics

- About Disabling Replay in Application Continuity for Java

**Related Topics**

- [Transaction Guard for Java](transaction-guard.md)

### 28.1 About Configuring Oracle JDBC for Application Continuity for Java

You must use the `oracle.jdbc.replay.OracleDataSourceImpl`,`oracle.jdbc.replay.OracleConnectionPoolDataSourceImpl`, or `oracle.jdbc.replay.driver.OracleXADataSourceImpl` data source to obtain JDBC connections. You can use both `oracle.jdbc.replay.OracleDataSourceImpl` and `oracle.jdbc.replay.OracleConnectionPoolDataSourceImpl`in a standalone manner, or configure them as connection factories for a connection pool, such as Universal Connection Pool (UCP), or Oracle WebLogic Server connection pool.

Starting from Oracle Database 12c Release 2 (12.2.0.1), the JDBC Replay Driver provides a new data source, the XA Replay Data Source, which supports JDBC operations replay, and also works with both UCP data source and WebLogic Active GridLink single-pool data source for all the Oracle RAC features, including Fast Connection Failover, Runtime Connection Load-Balancing, and all types of RAC-instance affinities. For using this data source, your application must implement the `oracle.jdbc.replay.OracleXADataSource` interface. The actual data source implementation class is `oracle.jdbc.replay.driver.OracleXADataSourceImpl`. You can specify the implementation class to UCP data sources and Oracle WebLogic Server GridLink data source as a connection factory. The factory class for JNDI is `oracle.jdbc.replay.OracleXADataSourceFactory`.

**Note:**

- The XA replay data source does not provide a configurable replay mode. For enabling replay, you must use the replay data source and set `FAILOVER_TYPE` to `TRANSACTION` on the database service at the server side, if not set already.

- Starting from Oracle Database Release 18c, you can also set `FAILOVER_TYPE` to `AUTO` for using Transparent Application Continuity.

  **See Also:**

  [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)

- For enabling and disabling replay dynamically, you must use a separate API available on the replay connection proxy. The XA replay data source does not provide connection pooling. Any `getXAConnection` method call produces a new JDBC `XAConnection` proxy dynamically, which holds a new JDBC physical connection as the delegate. The delegate is an Oracle JDBC driver object.

The following code snippet illustrates the usage of `oracle.jdbc.replay.OracleDataSourceImpl` and `oracle.jdbc.replay.OracleConnectionPoolDataSourceImpl` in a standalone JDBC application:

    import java.sql.Connection;
    import javax.sql.PooledConnection;
    import oracle.jdbc.OracleConnection;
    import oracle.jdbc.replay.OracleDataSourceFactory;
    import oracle.jdbc.replay.OracleDataSource;
    import oracle.jdbc.replay.OracleConnectionPoolDataSource;

    ...
    {
    ......
    OracleDataSource rds = OracleDataSourceFactory.getOracleDataSource();
    rds.setUser(user);
    rds.setPassword(passwd);
    rds.setURL(url);
    ......  // Other data source configuration like callback, timeouts, etc.

    Connection conn = rds.getConnection();
    ((OracleConnection) conn).beginRequest();  // Explicit request begin
    ......  // JDBC calls protected by Application Continuity
    ((OracleConnection) conn).endRequest();  // Explicit request end
    conn.close();

    OracleConnectionPoolDataSource rcpds = OracleDataSourceFactory.getOracleConnectionPoolDataSource();
    rcpds.setUser(user);
    rcpds.setPassword(passwd);
    rcpds.setURL(url);
    ......  // other data source configuration like callback, timeouts, and so on

    PooledConnection pc = rcpds.getPooledConnection();
    Connection conn2 = pc.getConnection();  // Implicit request begin
    ......  // JDBC calls protected by Application Continuity
    conn2.close();  // Implicit request end
    ......

You must remember the following points while using the connection URL:

- Always use the thin driver in the connection URL.

- Always connect to a service. Never use `instance_name` or SID because these do not direct to known good instances and SID is deprecated.

- If the addresses in the `ADDRESS_LIST` at the client does not match the `REMOTE_LISTENER` setting for the database, then it does not connect showing `services cannot be found`. So, the addresses in the `ADDRESS_LIST` at the client must match the `REMOTE_LISTENER` setting for the database:

  - If `REMOTE_LISTENER` is set to the `SCAN_VIP`, then the `ADDRESS_LIST` uses `SCAN_VIP`

  - If `REMOTE_LISTENER` is set to the host VIPs, then the `ADDRESS_LIST` uses the same host VIPs

  - If `REMOTE_LISTENER` is set to both `SCAN_VIP` and host VIPs, then the `ADDRESS_LIST` uses `SCAN_VIP` and the same host VIPs

    **Note:**

    For Oracle clients prior to release 11.2, the `ADDRESS_LIST` must be upgraded to use SCAN, which means expanding the `ADDRESS_LIST `to three `ADDRESS` entries corresponding to the three SCAN IP addresses.

    If such clients connect to a database that is upgraded from an earlier release through Database Upgrade Assistant, then you must retain the `ADDRESS_LIST` of these clients set to the HOST VIPs. However, if `REMOTE_LISTENER` is changed to `ONLY SCAN`, or the clients are moved to a newly installed Oracle Database 12c Release 1, where `REMOTE_LISTENER` is `ONLY SCAN`, then they do not get a complete service map, and may not always be able to connect.

- Set `RETRY_COUNT`, `RETRY_DELAY`, `CONNECT_TIMEOUT`, and `TRANSPORT_CONNECT_TIMEOUT` parameters in the connection string. This is a general recommendation for configuring the JDBC thin driver connections, starting from Oracle Database Release 12.1.0.2. These settings improve acquiring new connections at runtime, at replay, and during work drains for planned outages.

  The `CONNECT_TIMEOUT` parameter is equivalent to the `SQLNET.OUTBOUND_CONNECT_TIMEOUT` parameter in the `sqlnet.ora` file and applies to the full connection. The `TRANSPORT_CONNECT_TIMEOUT` parameter applies as per the `ADDRESS` parameter. If the service is not registered for a failover or restart, then retrying is important when you use SCAN. For example, for using remote listeners pointing to SCAN addresses, you should use the following settings:

      jdbc:oracle:thin:@(DESCRIPTION =
       (TRANSPORT_CONNECT_TIMEOUT=3000)
       (RETRY_COUNT=20)(RETRY_DELAY=3)(FAILOVER=ON)
       (ADDRESS_LIST =(ADDRESS=(PROTOCOL=tcp)
        (HOST=CLOUD-SCANVIP.example.com)(PORT=5221))
       (CONNECT_DATA=(SERVICE_NAME=orcl)))

      REMOTE_LISTENERS=CLOUD-SCANVIP.example.com:5221

  Similarly, for using remote listeners pointing to VIPs at the database, you should use the following settings:

      jdbc:oracle:thin:@(DESCRIPTION =
      (TRANSPORT_CONNECT_TIMEOUT=3000)
      (CONNECT_TIMEOUT=60)(RETRY_COUNT=20)(RETRY_DELAY=3)(FAILOVER=ON)
       (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP1.example.com)(PORT=5221) )
      (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP2.example.com)(PORT=5221) )
       (ADDRESS=(PROTOCOL=tcp)(HOST=CLOUD-VIP3.example.com)(PORT=5221) ))
      (CONNECT_DATA=(SERVICE_NAME=orcl)))

      REMOTE_LISTENERS=CLOUD-VIP1.example.com:5221

  **See Also:**

  - [Oracle Database Net Services Reference](../netrf/index.md) for more information about local naming parameters

  - [Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md)

**Related Topics**

- [Data Sources and URLs](data-sources-and-URLs.md)

#### 28.1.1 Support for Concrete Classes with Application Continuity

Starting from Oracle Database Release 18c, JDBC driver supports the following concrete classes with Application Continuity:

- `oracle.sql.CLOB`

- `oracle.sql.NCLOB`

- `oracle.sql.BLOB`

- `oracle.sql.BFILE`

- `oracle.sql.STRUCT`

- `oracle.sql.REF`

- `oracle.sql.ARRAY`

### 28.2 About Configuring Oracle Database for Application Continuity for Java

You must have the following configuration for Oracle Database to use Application Continuity for Java:

- Use Oracle Database 12c Release 1 (12.1) or later

- If you are using Oracle Real Application Clusters (Oracle RAC) or Oracle Data Guard, then ensure that FAN is configured with Oracle Notification System (ONS) to communicate with Oracle WebLogic Server or the Universal Connection Pool (UCP)

- Use an application service for all database work. To create the service you must:

  - Run the `SRVCTL` command if you are using Oracle RAC

  - Use the `DBMS_SERVICE` package if you are not using Oracle RAC

- Set the required properties on the service for replay and load balancing. For example, set:

  - `aq_ha_notifications = TRUE` for enabling FAN notification

  - `FAILOVER_TYPE = TRANSACTION` or `FAILOVER_TYPE = AUTO` for using Application Continuity

  - `COMMIT_OUTCOME` = `TRUE` for enabling Transaction Guard

  - `REPLAY_INITIATION_TIMEOUT = 900` for setting the duration in seconds for which replay will occur

  - `FAILOVER_RETRIES = 30` for specifying the number of connection retries for each replay

  - `FAILOVER_DELAY = 10` for specifying the delay in seconds between connection retries

  - `GOAL = SERVICE_TIME`, if you are using Oracle RAC, then this is a recommended setting

  - `CLB_GOAL = LONG`, typically useful for closed workloads. If you are using Oracle RAC, then this is a recommended setting. For most of the other workloads, `SHORT` is the recommended setting.

- Do not use the database service, that is, the default service corresponding to the `DB_NAME` or `DB_UNIQUE_NAME`. This service is reserved for Oracle Enterprise Manager and for DBAs. Oracle does not recommend the use of the database service for high availability because this service cannot be:

  - Enabled and disabled

  - Relocated on Oracle RAC

  - Switched over to Oracle Data Guard

**See Also:**

[Oracle Database Development Guide ](../racad/ensuring-application-continuity.md)for more information on the operation and usage of Application Continuity.

### 28.3 Application Continuity Support for XA Data Source

Oracle Database 12c Release 2 (12.2.0.1) introduced a new feature that enhances Application Continuity with support for Oracle XA data source (`javax.sql.XADataSource`), which is similar to non-XA data source (`javax.sql.DataSource`). Both JDBC and Java Transaction API (JTA) allow a JDBC connection to interchangeably participate in local and global/XA transactions. However, many customer applications obtain connections from an XA data source, but use these connections to perform only local transactions. With the new feature, Application Continuity also covers applications that are using XA-capable data sources but with local transactions, including local transactions that are promotable to global/XA transactions. So, the benefits of Application Continuity, such as, failover and forward-recovery are extended to these applications.

**Note:**

You must use Transaction Guard 12.2 for using this feature.

Whenever an underlying physical connection participates in a global/XA transaction, or engages in any XA operation, replay is disabled on that connection. All other XA operations function normally, but the application does not get Application Continuity protection.

Once replay is disabled on a connection for the above reasons, it remains disabled until the next request begins. Switching from global/XA transaction to local transaction mode does not automatically reenable replay on a connection.

The following code snippet illustrates how replay is supported for local transactions, and disabled for XA transaction, when the connections are obtained from `OracleXADataSource`:

    import javax.transaction.xa.*;
    import oracle.jdbc.replay.OracleXADataSource;
    import oracle.jdbc.replay.OracleXADataSourceFactory;
    import oracle.jdbc.replay.ReplayableConnection;

    OracleXADataSource xards = OracleXADataSourceFactory.getOracleXADataSource();
    xards.setURL(connectURL);
    xards.setUser(<user_name>);
    xards.setPassword(<password>);
    XAConnection xaconn = xards.getXAConnection();

    // Implicit request begins
    Connection conn = xaconn.getConnection();

    /* Local transaction case */
    // Request-boundary detection OFF
    ((ReplayableConnection) conn).beginRequest();
    conn.setAutoCommit(false);
    PreparedStatement pstmt=conn.prepareStatement(“select cust_first_name,cust_last_name from customers where customer_id=1");
    ResultSet rs=pstmt.executeQuery();

    // Outage happens at this point
    // Replay happens at this point
    rs.next();
    rs.close();
    pstmt.close();
    ((ReplayableConnection) conn).endRequest();
    ...

    /* Global/XA transaction case */
    ((ReplayableConnection) conn).beginRequest();
    conn.setAutoCommit(false);
    XAResource xares = xaconn.getXAResource();
    Xid xid = createXid();

    // Replay is disabled here
    xares.start(xid, XAResource.TMNOFLAGS);
    conn.prepareStatement(“INSERT INTO TEST_TAB VALUES(200, 'another new record')”);

    // outage happens at this point
    try {

    //No replay here and throws exception
    conn.executeUpdate();
    }

    // sqlrexc.getNextException() shows the reason for the replay failure
    catch (SQLRecoverableException sqlrexc) {

        …...
    }

### 28.4 About Identifying Request Boundaries in Application Continuity for Java

A Request is a unit of work on a physical connection to Oracle Database that is protected by Application Continuity. Request demarcation varies with specific use-case scenarios. A request begins when a connection is borrowed from the Universal Connection Pool (UCP) or WebLogic Server connection pool, and ends when this connection is returned to the connection pool.

The JDBC driver provides explicit request boundary declaration APIs `beginRequest` and `endRequest` in the `oracle.jdbc.OracleConnection` interface. These APIs enable applications, frameworks, and connection pools to indicate to the JDBC Replay Driver about demarcation points, where it is safe to release the call history, and to enable replay if it had been disabled by a prior request. At the end of the request, the JDBC Replay Driver purges the recorded history on the connection, where the API is called. This helps to further conserve memory consumption for applications that use the same connections for an extended period of time without returning them to the pool.

For the connection pool to work, the application must get connections when needed, and release connections when not in use. This scales better and provides request boundaries transparently. The APIs have no impact on the applications other than improving resource consumption, recovery, and load balancing performance. These APIs do not involve altering a connection state by calling any JDBC method, SQL, or PL/SQL. An error is returned if an attempt is made to begin or end a request while a local transaction is open.

### 28.5 Support for Transparent Application Continuity

Oracle Database Release 18c introduced the Transparent Application Continuity feature, which is a functional mode of Application Continuity. Transparent Application Continuity transparently tracks and records session and transactional state, so that a database session can be recovered following recoverable outages. This is performed safely and without the need for any knowledge of the application or application code changes. Transparency is achieved by using a state-tracking infrastructure that categorizes session state usage as an application issues user calls. This feature enables the driver to detect and inject possible request boundaries, which are known as implicit request boundaries. For an implicit request boundary:

- No objects are open

- Cursors are returned to the driver statement cache

- No transactions are open

The session state in such a case is known to be restorable. The driver either closes the current capture and starts a new event, or enables capture if there had been a disabling event. On the next call to the server, the server verifies and, if applicable, creates a request boundary, where there was previously no explicit boundary.

To use Transparent Application Continuity, you must set the server-side service attribute `FAILOVER_TYPE` on the database service to `AUTO`.

Support for implicit request helps to reduce application failover recovery time and optimizes Application Continuity. Using Transparent Application Continuity, the server and the drivers can track transaction and session state usage. However, this feature should be used with caution for applications that change server session states during a request. The JDBC Thin driver provides the `oracle.jdbc.enableImplicitRequests` property to turn off implicit requests, if needed. This property can be set at the system level, which applies to all connections, or at the connection level, which applies to a particular connection. By default, the value of this property is `true`, which means that support for implicit request is enabled.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)

Starting from Oracle Database Release 19c, if you set the value of the `FAILOVER_TYPE` service attribute to `AUTO`, then the Oracle JDBC driver implicitly begins a request on each new physical connection created through the replay data source. With this feature, applications using third-party connection pools can use Transparent Application Continuity (TAC) easily, without making any code change to inject request boundaries.

This implicit `beginRequest` applies only to the replay data source, and only to the physical connections created during runtime, when TAC is enabled. The driver does not implicitly begin a request after each reconnection during replay attempts (that is, a `beginRequest` is not implicitly injected during a replay connection) or in manual Application Continuity mode, where the `FAILOVER_TYPE` service attribute is set to `TRANSACTION`.

If you want to turn off this feature explicitly, you can set the value of the Java system property `oracle.jdbc.beginRequestAtConnectionCreation` to `false.` The default value of this property is `true`.

**Related Topics**

- About Enabling FAILOVER_RESTORE

### 28.6 Establishing the Initial State Before Application Continuity Replays

Non-transactional session state (NTSS) is state of a database session that exists outside database transactions and is not protected by recovery. For applications that use stateful requests, the non-transactional state is re-established as the rebuilt session.

For applications that set state only at the beginning of a request, or for stateful applications that gain performance benefits from using connections with a preset state, one among the following callback options are provided:

- No Callback

- Connection Labeling

- Connection Initialization Callback

- About Enabling FAILOVER_RESTORE

#### 28.6.1 No Callback

In this scenario, the application builds up its own state during each request.

#### 28.6.2 Connection Labeling

This scenario is applicable only to Universal Connection Pool (UCP) and Oracle WebLogic server. The application can be modified to take advantage of the preset state on connections. Connection Labeling APIs determine how well a connection matches, and use a callback to populate the gap when a connection is borrowed.

**See Also:**

[Oracle Universal Connection Pool Developer’s Guide](../jjucp/application-continuity-using-ucp.md)

#### 28.6.3 Connection Initialization Callback

In this scenario, the replay driver uses an application callback to set the initial state of the session during runtime and replay. The JDBC replay driver provides an optional connection initialization callback interface as well as methods for registering and unregistering such callbacks.

When registered, the initialization callback is executed at each successful reconnection following a recoverable error. An application is responsible for ensuring that the initialization actions are the same as that on the original connection before failover. If the callback invocation fails, then replay is disabled on that connection.

This section discusses initialization callbacks in the following sections:

- Creating an Initialization Callback

- Registering an Initialization Callback

- Removing or Unregistering an Initialization Callback

##### 28.6.3.1 Creating an Initialization Callback

To create a JDBC connection initialization callback, an application implements the `oracle.jdbc.replay.ConnectionInitializationCallback` interface. One callback is allowed for every instance of the `oracle.jdbc.replay.OracleDataSource` interface.

**Note:**

This callback is only invoked during failover, after a successful reconnection.

##### Example

The following code snippet demonstrates a simple initialization callback implementation:

    import oracle.jdbc.replay.ConnectionInitializationCallback;
    class MyConnectionInitializationCallback implements ConnectionInitializationCallback
    {
        public MyConnectionInitializationCallback()
        {
            ...
        }
        public void initialize(java.sql.Connection connection) throws SQLException
        {
            // Reset the state for the connection, if necessary (like ALTER SESSION)
            ...
        }
     }

For applications using an XA data source, the connection initialization callback is registered on the XA replay data source. The callback is executed every time when both of the following happen:

- A connection is borrowed from the connection pool.

- The replay XA data source gets a new physical connection at failover.

**Note:**

The connection initialization must be idempotent. If the connection is already initialized, then it must not repeat itself. This enables applications to reestablish session initial starting point after a failover and before the starting of replay. The callback execution must leave an open local transaction without committing it or rolling it back. If this is violated, an exception is thrown.

If a callback invocation fails, replay is disabled on that connection. For example, an application embeds the set up phase for a connection in this callback.

##### 28.6.3.2 Registering an Initialization Callback

Use the following method that the JDBC Replay Driver provides in the `oracle.jdbc.replay.OracleDataSource` interface for registering a connection initialization callback:

    registerConnectionInitializationCallback(ConnectionInitializationCallback cbk)

One callback is allowed for every instance of the `OracleDataSource` interface.

For using an XA Data Source, use the `registerConnectionInitializationCallback(ConnectionInitializationCallback cbk)` method in the `oracle.jdbc.replay.OracleXADataSource` interface.

##### 28.6.3.3 Removing or Unregistering an Initialization Callback

Use the following method that the JDBC Replay Driver provides in the `oracle.jdbc.replay.OracleDataSource` interface for unregistering a connection initialization callback:

    unregisterConnectionInitializationCallback(ConnectionInitializationCallback cbk)

For using an XA Data Source, use the `unregisterConnectionInitializationCallback(ConnectionInitializationCallback cbk)` method in the `oracle.jdbc.replay.OracleXADataSource` interface.

#### 28.6.4 About Enabling FAILOVER_RESTORE

`FAILOVER_RESTORE` service attribute was introduced in Oracle Database 12c Release 2 (12.2.0.1). Setting `FAILOVER_RESTORE` to `LEVEL1` automatically restores the common initial state before replaying a request. By default, the value of the `FAILOVER_RESTORE` attribute is set to `NONE`, which means that it is disabled.

Starting from Oracle Database Release 18c, you can also set the value of this attribute to `AUTO`. Also, if you set the value of the `FAILOVER_TYPE` attribute to `AUTO`, then `FAILOVER_RESTORE` is set to `AUTO` automatically. You cannot change the value of `FAILOVER_RESTORE` to anything else as long as `FAILOVER_TYPE` is set to `AUTO`. When `FAILOVER_RESTORE` is set to `AUTO`, then the common initial state is also set. As far as session state restore is concerned, this setting provides the same function as `FAILOVER_RESTORE` set to `LEVEL1`.

**See Also:**

[Oracle® Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)

**Note:**

For Application Continuity for Java available with Oracle Database Release 18c, the following initial states are supported for `FAILOVER_RESTORE`:

- `NLS_CALENDAR`

- `NLS_CURRENCY`

- `NLS_DATE_FORMAT`

- `NLS_DATE_LANGUAGE`

- `NLS_DUAL_CURRENCY`

- `NLS_ISO_CURRENCY`

- `NLS_LANGUAGE`

- `NLS_LENGTH_SEMANTICS`

- `NLS_NCHAR_CONV_EXCP`

- `NLS_NUMERIC_CHARACTER`

- `NLS_SORT`

- `NLS_TERRITORY`

- `NLS_TIME_FORMAT`

- `NLS_TIME_TZ_FORMAT`

- `NLS_TIMESTAMP_FORMAT`

- `NLS_TIMESTAMP_TZ_FORMAT`

- `TIME_ZONE (OCI, ODP.NET 12201)`

- `CURRENT_SCHEMA `

- `MODULE`

- `ACTION`

- `CLIENT_ID`

- `ECONTEXT_ID`

- `ECONTEXT_SEQ`

- `DB_OP`

- `AUTOCOMMIT` states (Java and SQL\*Plus)

- `CONTAINER` (PDB) and `SERVICE` for OCI and ODP.NET

In Oracle Database Release 19c, the following additional initial states are supported for `FAILOVER_RESTORE`:

- `ERROR_ON_OVERLAP_TIME`
- `EDITION`
- `SQL_TRANSLATION_PROFILE`
- `ROW ARCHIVAL VISIBILITY`
- `ROLEs`
- `CLIENT_INFO`

**Note:**

For Oracle Database Release 19c, `FAILOVER_RESTORE` is automatically enabled in Transparent Application Continuity (TAC) mode.

The following states are excluded from the auto-restoration option because they are not supported by the Thin driver:

- `NLS_COMP`

- `CALL_COLLECT_TIME`

For many applications, enabling `FAILOVER_RESTORE` is sufficient to automatically restore the initial state required for AC replay, without the use of a callback. If your application requires any initial state that is not mentioned in the preceding list, or if the application prefers explicit control over setting the initial state, then the application must use a callback, either connection labeling or an initialization callback. When a callback is configured, it overrides the initial states restored by `FAILOVER_RESTORE`, in case the latter is enabled at the same time.

### 28.7 About Delaying the Reconnection in Application Continuity for Java

By default, when JDBC Replay Driver initiates a failover, the driver attempts to recover the in-flight work at an instance where the service is available. For doing this, the driver must first reestablish a good connection to a working instance. This reconnection can take some time if the database or the instance needs to be restarted before the service is relocated and published. So, the failover should be delayed until the service is available from another instance or database.

You must use the `FAILOVER_RETRIES` and `FAILOVER_DELAY` parameters to sustain the delay because maximum delay is calculated as `FAILOVER_RETRIES` multiplied by `FAILOVER_DELAY`. These parameters can work well in conjunction with a planned outage, for example, an outage that may make a service unavailable for several minutes. While setting the `FAILOVER_DELAY` and `FAILOVER_RETRIES` parameters, check the value of the `REPLAY_INITIAITION_TIMEOUT` parameter first. The default value for this parameter is 900 seconds. A high value for the `FAILOVER_DELAY` parameter can cause replay to be canceled.

| Parameter Name     | Possible Value                 | Default Value |
|:-------------------|:-------------------------------|:--------------|
| `FAILOVER_RETRIES` | Positive integer zero or above | 30            |
| `FAILOVER_DELAY`   | Time in seconds                | 10            |

#### 28.7.1 Configuration Examples Related to Application Continuity for Java

This section provides configuration examples for service creation and modification in the following subsections:

- Creating Services on Oracle RAC

- Modifying Services on Single-Instance Databases

##### 28.7.1.1 Creating Services on Oracle RAC

If you are using Oracle RAC or Oracle RAC One, then use the `SRVCTL` command to create and modify services in the following way:

##### For Transparent Application Continuity

You can create services that use Transparent Application Continuity, as follows:

For policy-managed databases:

    $ srvctl add service -db codedb -service GOLD -serverpool ora.Srvpool -clbgoal SHORT -rlbgoal SERVICE_TIME -failover_restore AUTO -failoverretry 30
    -failoverdelay 10 -commit_outcome TRUE -failovertype AUTO -replay_init_time 1800 -retention 86400  -notification TRUE

For administrator-managed databases:

    $ srvctl add service -db codedb -service GOLD -preferred serv1 -available serv2 -clbgoal SHORT -rlbgoal SERVICE_TIME -failover_restore AUTO
    -failoverretry 30 -failoverdelay 10 -commit_outcome TRUE -failovertype AUTO -replay_init_time 1800 -retention 86400 -notification TRUE

##### For Manual Application Continuity

You can create services that use manual Application Continuity, as follows:

For policy-managed databases:

    $ srvctl add service -db codedb -service GOLD -serverpool ora.Srvpool -clbgoal SHORT -rlbgoal SERVICE_TIME -failover_restore LEVEL1 -failoverretry 30
    -failoverdelay 10 -commit_outcome TRUE -failovertype TRANSACTION -replay_init_time 1800 -retention 86400 -notification TRUE

For administrator-managed databases:

    $ srvctl add service -db codedb -service GOLD -preferred serv1 -available serv2 -clbgoal SHORT -rlbgoal SERVICE_TIME -failover_restore LEVEL1
    -failoverretry 30 -failoverdelay 10 -commit_outcome TRUE -failovertype TRANSACTION -replay_init_time 1800 -retention 86400 -notification TRUE

##### 28.7.1.2 Modifying Services on Single-Instance Databases

If you are using a single-instance database, then use the `DBMS_SERVICE` package to modify services in the following way:

    declare
    params dbms_service.svc_parameter_array;
    begin
    params('FAILOVER_TYPE'):='TRANSACTION';
    params('REPLAY_INITIATION_TIMEOUT'):=1800;
    params('RETENTION_TIMEOUT'):=604800;
    params('FAILOVER_DELAY'):=10;
    params('FAILOVER_RETRIES'):=30;
    params('commit_outcome'):='true';
    params('aq_ha_notifications'):='true';
    dbms_service.modify_service('[your service]',params);
    end;
    /

### 28.8 About Retaining Mutable Values in Application Continuity for Java

A mutable object is a variable, function return value, or other structure that returns a different value each time that it is called. For example, `Sequence.NextVal`, `SYSDATE`, `SYSTIMESTAMP`, and `SYS_GUID`. To retain the function results for named functions at replay, the DBA must grant `KEEP` privileges to the user who invokes the function. This security restriction is imposed to ensure that it is valid for replay to save and restore function results for code that is not owned by that user.

**See Also:**

[Oracle Database Development Guide](../racad/ensuring-application-continuity.md)

#### 28.8.1 Grant and Revoke Interface

You can work with mutables values by using the standard `GRANT` and `REVOKE` interfaces in the following way:

- Dates and SYS_GUID Syntax

- Sequence Syntax

- GRANT ALL Statement

- Rules for Grants on Mutable Values

##### 28.8.1.1 Dates and SYS_GUID Syntax

The `DATE_TIME` and `SYS_GUID` syntax is as follows:

    GRANT [KEEP DATE TIME|SYSGUID]..[to USER}
    REVOKE [KEEP DATE TIME | KEEP SYSGUID] … [from USER]

For example, for EBS standard usage with original dates

    Grant KEEP DATE TIME,  KEEP SYSGUID  to [custom user];
    Grant KEEP DATE TIME,  KEEP SYSGUID  to [apps user];

##### 28.8.1.2 Sequence Syntax

The Sequence syntax can be of the following types:

- Owned Sequence Syntax

- Others Sequence Syntax

##### Owned Sequence Syntax

    ALTER SEQUENCE [sequence object] [KEEP|NOKEEP];

This command retains the original values of `sequence.nextval` for replaying, so that the keys match after replay. Most applications need to retain the sequence values at replay. The `ALTER SYNTAX` is only for owned sequences.

##### Others Sequence Syntax

    GRANT KEEP SEQUENCE..[to USER] on [sequence object];
    REVOKE  KEEP SEQUENCE … [from USER]  on [sequence object];

For example, use the following command for EBS standard usage with original sequence values:

    Grant KEEP SEQUENCE  to [apps user] on [sequence object];
    Grant KEEP SEQUENCE  to [custom user] on [sequence object];

##### 28.8.1.3 GRANT ALL Statement

The `GRANT ALL` statement grants `KEEP` privilege on all the objects of a user. However, it excludes mutable values, that is, mutable values require explicit grants.

##### 28.8.1.4 Rules for Grants on Mutable Values

Follow these rules while granting privileges on mutable objects:

- If a user has `KEEP` privilege granted on mutables values, then the objects inherit mutable access when the `SYS_GUID`, `SYSDATE`, and `SYSTIMESTAMP` functions are called.

- If the `KEEP` privilege on mutable values on a sequence object is revoked, then SQL or PL/SQL blocks using that object will not allow mutable collection or application for that sequence.

- If granted privileges are revoked between runtime and failover, then the mutable values that are collected are not applied for replay.

- If new privileges are granted between runtime and failover, mutable values are not collected and these values are not applied for replay.

### 28.9 Application Continuity Statistics

The JDBC Replay Driver supports the following statistics for an application using Application Continuity:

- Total number of requests

- Total number of completed requests

- Total number of calls

- Total number of protected calls

- Total number of calls affected by outages

- Total number of calls triggering replay

- Total number of calls affected by outages during replay

- Total number of successful replay

- Total number of failed replay

- Total number of disabled replay

- Total number of replay attempts

All these metrics are available both on a per-connection basis and across-connections basis. You can use the following methods for obtaining these statistics:

- `getReplayStatistics(StatisticsReportType)`

  Use the `oracle.jdbc.replay.ReplayableConnection.getReplayStatistics(StatisticsReportType)` method to obtain the snapshot statistics. The argument to this method is an enum type also defined in the same `ReplayableConnection` interface. To obtain statistics across connections, it is best calling this method after the main application logic. Applications can either use any `oracle.jdbc.replay.ReplayableConnection` that is still open, or open a new connection to the same data source. This applies to applications using both UCP and WLS data sources, and applications that directly use the replay data source.

- `getReplayStatistics()`

  Use the `oracle.jdbc.replay.OracleDataSource.getReplayStatistics()` method to obtain across-connection statistics. This applies only to applications that directly use replay data source.

Both methods return an `oracle.jdbc.replay.ReplayStatistics` object, from which you can retrieve individual replay metrics. The following is a sample output that prints a ReplayStatistics object as String:

    AC Statistics:
    ===============================================
    TotalRequests = 1
    TotalCompletedRequests = 1
    TotalCalls = 19
    TotalProtectedCalls = 19
    ===============================================
    TotalCallsAffectedByOutages = 3
    TotalCallsTriggeringReplay = 3
    TotalCallsAffectedByOutagesDuringReplay = 0
    ===============================================
    SuccessfulReplayCount = 3
    FailedReplayCount = 0
    ReplayDisablingCount = 0
    TotalReplayAttempts = 3
    ===============================================

If you want to clear the accumulated replay statistics per connection or for all connections, then you can use the following methods:

- `oracle.jdbc.replay.ReplayableConnection.clearReplayStatistics(ReplayableConnection.StatisticsReportType reportType)`

- `oracle.jdbc.replay.OracleDataSource.clearReplayStatistics()`

**Note:**

All statistics reflect only updates since the latest clearing.

### 28.10 About Disabling Replay in Application Continuity for Java

This section describes the following concepts:

- How to Disable Replay

- When to Disable Replay

- Diagnostics and Tracing

#### 28.10.1 How to Disable Replay

If any application module uses a design that is unsuitable for replay, then the disable replay API disables replay on a per request basis. Disabling replay can be added to the callback or to the main code by using the `disableReplay` method of the `oracle.jdbc.replay.ReplayableConnection` interface. For example:

    if (connection instanceof oracle.jdbc.replay.ReplayableConnection)
    {
        (( oracle.jdbc.replay.ReplayableConnection)connection).disableReplay();

    }

Disabling replay does not alter the connection state by reexecuting any JDBC method, SQL or PL/SQL. When replay is disabled using the disable replay API, both recording and replay are disabled until that request ends. There is no API to reenable replay because it is invalid to reestablish the database session with time gaps in a replayed request. This ensures that replay runs only if a complete history of needed calls has been recorded.

#### 28.10.2 When to Disable Replay

By default, the JDBC replay driver replays following a recoverable error. The disable replay API can be used in the entry point of application modules that are unable to lose the database sessions and recover. For example, if the application uses the `UTL_SMTP` package and does not want messages to be repeated, then the `disableReplay` API affects only the request that needs to be disabled. All other requests continue to be replayed.

The following are scenarios to consider before configuring an application for replay:

- Application Calls External PL/SQL Actions that Should not Be Repeated

- Application Synchronizes Independent Sessions

- Application Uses Time at the Middle-tier in the Execution Logic

- Application assumes that ROWIds do not change

- Application Assumes that Side Effects Execute Once

- Application Assumes that Location Values Do not Change

##### 28.10.2.1 Application Calls External Systems that Should not Be Repeated

During replay, autonomous transactions and external systems (like PL/SQL calls or Java calls) can have side effects that are separate from the main transaction. These side effects are replayed unless you specify otherwise and leave persistent results behind. These side effects include writing to an external table, sending email, forking sessions out of PL/SQL or Java, transferring files, accessing external URLs, and so on. For example, in case of PL/SQL messaging, suppose, you walk away in-between some work without committing and the session times out. Now, if you issue a `Ctrl+C` command, then the foreground of a component fails. When you resubmit the work, then this side effect can also be repeated.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for more information about potential side effects of Application Continuity

You must make a conscious decision about whether to enable replay for external actions or not. For example, you can consider the following situations where this decision is important:

- Using the `UTL_HTTP` package to issue a SOA call

- Using the `UTL_SMTP` package to send a message

- Using the `UTL_URL` package to access a web site

Use the `disableReplay` API if you do not want such external actions to be replayed.

##### 28.10.2.2 Application Synchronizes Independent Sessions

You can configure an application for replay if the application synchronizes independent sessions using volatile entities that are held until commit, rollback, or session loss. In this case, the application synchronizes multiple sessions connected to several data sources that are otherwise inter-dependent using resources such as a database lock. This synchronization may be fine if the application is only serializing these sessions and understands that any session may fail. However, if the application assumes that a lock or any other volatile resource held by one data source implies exclusive access to data on the same or a separate data source from other connections, then this assumption may be invalidated when replaying.

During replay, the driver is not aware that the sessions are dependent on one session holding a lock or other volatile resource. You can also use pipes, buffered queues, stored procedures taking a resource (such as a semaphore, device, or socket) to implement the synchronization that are lost by failures.

**Note:**

The `DBMS_LOCK` does not replay in the restricted version.

##### 28.10.2.3 Application Uses Time at the Middle-tier in the Execution Logic

In this case, the application uses the wall clock at the middle-tier as part of the execution logic. The JDBC replay driver does not repeat the middle-tier time logic, but uses the database calls that execute as part of this logic. For example, an application using middle-tier time may assume that a statement executed at Time T1 is not reexecuted at Time T2, unless the application explicitly does so.

##### 28.10.2.4 Application assumes that ROWIds do not change

If an application caches ROWIDs, then access to these ROWIDs may be invalidated due to database changes. Although a ROWID uniquely identifies a row in a table, a ROWID may change its value in the following situations:

- The underlying table is reorganized

- An index is created on the table

- The underlying table is partitioned

- The underlying table is migrated

- The underlying table is exported and imported using EXP/IMP/DUL

- The underlying table is rebuilt using Golden Gate or Logical Standby or other replication technology

- The database of the underlying table is flashed back or restored

It is bad practice for an application to store ROWIDs for later use as the corresponding row may either not exist or contain completely different data.

##### 28.10.2.5 Application Assumes that Side Effects Execute Once

In this case, the following are replayed during a replay:

- Autonomous transactions

- Opening of back channels separate to the main transaction side effects

Examples of back channels separate to the main transaction include writing to an external table, sending email, forking sessions out of PL/SQL or Java, writing to output files, transferring files, and writing exception files. Any of these actions leave persistent side effects in the absence of replay. Back channels can leave persistent results behind. For example, if a user leaves a transaction midway without committing and the session times out, then the user presses Ctrl+C, the foreground or any component fails. If the user resubmits work, then the side effects can be repeated.

##### 28.10.2.6 Application Assumes that Location Values Do not Change

`SYSCONTEXT` options comprise a location-independent set such as National Language Support (NLS) settings, `ISDBA`, `CLIENT_IDENTIFIER`, `MODULE`, and `ACTION`, and a location-dependent set that uses physical locators. Typically, an application does not use the physical identifier, except in testing environments. If physical locators are used in mainline code, then the replay finds the mismatch and rejects it. However, it is fine to use physical locators in callbacks.

##### Example

    select
        sys_context('USERENV','DB_NAME')
        ,sys_context('USERENV','HOST')
        ,sys_context('USERENV','INSTANCE')
        ,sys_context('USERENV','IP_ADDRESS')
        ,sys_context('USERENV','ISDBA')
        ,sys_context('USERENV','SESSIONID')
        ,sys_context('USERENV','TERMINAL')
        ,sys_context('USERENV',ID')
    from dual

#### 28.10.3 Diagnostics and Tracing

The JDBC Replay driver supports standard JDK logging. Logging is enabled using the Java command-line `-Djava.util.logging.config.file=<file>` option. Log level is controlled with the `oracle.jdbc.internal.replay.level` attribute in the log configuration file. For example:

    oracle.jdbc.internal.replay.level = FINER|FINEST

where, `FINER` produces external APIs and `FINEST` produces large volumes of trace. You must use `FINEST` only under supervision.

If you use the `java.util.logging.XMLFormatter` class to format a log record, then the logs are more readable but larger. If you are using replay with FAN enabled on UCP or WebLogic Server, then you should also enable FAN-processing logging.

**See Also:**

[Oracle Universal Connection Pool for JDBC Developer's Guide](../jjucp/logging-in-ucp.md)

##### 28.10.3.1 Writing Replay Trace to Console

Following is the example of a configuration file for logging configuration.

    oracle.jdbc.internal.replay.level = FINER
    handlers = java.util.logging.ConsoleHandler
    java.util.logging.ConsoleHandler.level = ALL
    java.util.logging.ConsoleHandler.formatter = java.util.logging.XMLFormatter

##### 28.10.3.2 Writing Replay Trace to a File

Following is the example of a `properties` file for logging configuration.

    oracle.jdbc.internal.replay.level = FINEST

    # Output File Format (size, number and style)
    # count: Number of output files to cycle through, by appending an integer to the base file name:
    # limit: Limiting size of output file in bytes
    handlers = java.util.logging.FileHandler
    java.util.logging.FileHandler.pattern = [file location]/replay_%U.trc
    java.util.logging.FileHandler.limit = 500000000
    java.util.logging.FileHandler.count = 1000
    java.util.logging.FileHandler.formatter = java.util.logging.XMLFormatter

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

"A Logon storm is a sudden increase in the number of client connection requests."
