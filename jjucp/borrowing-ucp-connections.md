An application borrows connections using a pool-enabled data source. This section describes the following concepts about borrowing connections:

- Overview of Borrowing Connections from UCP

- Using the Pool-Enabled Data Source

- Using the Pool-Enabled XA Data Source

- Setting Connection Properties

- Using JNDI to Borrow a Connection

- About Connection Initialization Callback

**Note:**

The instructions in this section use a pool-enabled data source to implicitly create and start a connection pool.

### 3.1.1 Overview of Borrowing Connections from UCP

The UCP API provides two pool-enabled data sources, one for borrowing regular connections and one for borrowing XA connections. These data sources provide access to UCP JDBC connection pool functionality and include a set of `getConnection` methods that are used to borrow connections. The same pool features are included in both XA and non-XA UCP JDBC connection pools.

UCP JDBC connection pools maintain both available connections and borrowed connections. A connection is reused from the pool if an application requests to borrow a connection that matches an available connection. A new connection is created if no available connection in the pool match the requested connection. The number of available connections and borrowed connections are subjected to pool properties such as pool size, timeout intervals, and validation rules.

### 3.1.2 Using the Pool-Enabled Data Source

UCP provides a pool-enabled data source (`oracle.ucp.jdbc.PoolDataSource`) that is used to get connections to a database. The `oracle.ucp.jdbc.PoolDataSourceFactory` factory class provides a `getPoolDataSource()` method that creates the pool-enabled data source instance. For example:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

The pool-enabled data source requires a connection factory class in order to get an actual physical connection. The connection factory is typically provided as part of a JDBC driver and can be a data source itself. A UCP JDBC connection pool can use any JDBC driver to create physical connections that are then maintained by the pool. The `setConnectionFactoryClassName(String)` method is used to define the connection factory for the pool-enabled data source instance. The following example uses Oracle's `oracle.jdbc.pool.OracleDataSource` connection factory class included with the JDBC driver. If you are using a different vendor's JDBC driver, refer to the vendor's documentation for an appropriate connection factory class.

    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");

In addition to the connection factory class, a pool-enabled data source requires the URL, user name, and password that is used to connect to a database. A pool-enabled data source instance includes methods to set each of these properties. The following example uses an Oracle JDBC Thin driver syntax. If you are using a different vendor's JDBC driver, refer to the vendor's documentation for the appropriate URL syntax to use.

    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("user");
    pds.setPassword("password");

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/JDBC-getting-started.md) for detailed Oracle URL syntax usage.

Lastly, a pool-enabled data source provides a set of `getConnection` methods. The methods include:

- `getConnection()` : Returns a connection that is associated with the user name and password that was used to connect to the database.

- `getConnection(String username, String password)`: Returns a connection that is associated with the given user name and password.

- `getConnection(java.util.Properties labels)`: Returns a connection that matches a given label.

- `getConnection(String username, String password, java.util.Properties labels)` : Returns a connection that is associated with a given user name and password and that matches a given label.

An application uses the `getConnection` methods to borrow a connection handle from the pool that is of the type `java.sql.Connection`. If a connection handle is already in the pool that matches the requested connection (same URL, user name, and password) then it is returned to the application; or else, a new connection is created and a new connection handle is returned to the application. An example for both Oracle and MySQL are provided.

#### Oracle Example

The following example demonstrates borrowing a connection when using the JDBC Thin driver:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("<user>");
    pds.setPassword("<password>");

    Connection conn = pds.getConnection();

#### MySQL Example

The following example demonstrates borrowing a connection when using the Connector/J JDBC driver from MySQL:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionFactoryClassName("com.mysql.jdbc.jdbc2.optional.
       MysqlDataSource");
    pds.setURL("jdbc:mysql://host:3306/dbname");
    pds.setUser("<user>");
    pds.setPassword("<password>");

    Connection conn = pds.getConnection();

### 3.1.3 Using the Pool-Enabled XA Data Source

UCP provides a pool-enabled XA data source (`oracle.ucp.jdbc.PoolXADataSource`) that is used to get XA connections that can be enlisted in a distributed transaction. UCP JDBC XA pools have the same features as non-XA UCP JDBC pools. The `oracle.ucp.jdbc.PoolDataSourceFactory` factory class provides a `getPoolXADataSource()` method that creates the pool-enabled XA data source instance. For example:

    PoolXADataSource  pds = PoolDataSourceFactory.getPoolXADataSource();

A pool-enabled XA data source instance, like a non-XA data source instance, requires the connection factory, URL, user name, and password in order to get an actual physical connection. These properties are set in the same way as a non-XA data source instance (see above). However, an XA-specific connection factory class is required to get XA connections. The XA connection factory is typically provided as part of a JDBC driver and can be a data source itself. The following example uses Oracle's `oracle.jdbc.xa.client.OracleXADataSource` XA connection factory class included with the JDBC driver. If a different vendor's JDBC driver is used, refer to the vendor's documentation for an appropriate XA connection factory class.

    pds.setConnectionFactoryClassName("oracle.jdbc.xa.client.OracleXADataSource");
    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("user");
    pds.setPassword("password");

Lastly, a pool-enabled XA data source provides a set of `getXAConnection` methods that are used to borrow a connection handle from the pool that is of the type `javax.sql.XAConnection`. The `getXAConnection` methods are the same as the `getConnection` methods previously described. The following example demonstrates borrowing an XA connection.

    PoolXADataSource  pds = PoolDataSourceFactory.getPoolXADataSource();

    pds.setConnectionFactoryClassName("oracle.jdbc.xa.client.OracleXADataSource");
    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("<user>");
    pds.setPassword("<password>");

    XAConnection conn = pds.getXAConnection();

**Related Topics**

- [Labeling Connections in UCP](labeling-ucp-connections.md)

### 3.1.4 Setting Connection Properties

Oracle's connection factories support properties that configure connections with specific features. UCP pool-enabled data sources provide the `setConnectionProperties(Properties)` method, which is used to set properties on a given connection factory. The following example demonstrates setting connection properties for Oracle's JDBC driver. If you are using a JDBC driver from a different vendor, then refer to the vendor-specific documentation to check whether setting properties in this manner is supported and what properties are available:

    Properties connProps = new Properties();
    connProps.put("fixedString", false);
    connProps.put("remarksReporting", false);
    connProps.put("restrictGetTables", false);
    connProps.put("includeSynonyms", false);
    connProps.put("defaultNChar", false);
    connProps.put("AccumulateBatchResult", false);

    pds.setConnectionProperties(connProps);

The UCP JDBC connection pool does not remove connections that are already created if `setConnectionProperties` is called after the pool is created and in use.

**See Also:**

[Oracle Database JDBC Java API Reference](../jajdb/index.md) for a detailed list of supported properties to configure the connection. For example, to set the auto-commit mode, you can use the `OracleConnection.CONNECTION_PROPERTY_AUTOCOMMIT` property.

### 3.1.5 Using JNDI to Borrow a Connection

A connection can be borrowed from a connection pool by performing a JNDI look up for a pool-enabled data source and then calling `getConnection()` on the returned object. The pool-enabled data source must first be bound to a JNDI context and a logical name. This assumes that an application includes a Service Provider Interface (SPI) implementation for a naming and directory service where object references can be registered and located.

The following example uses Sun's file system JNDI service provider, which can be downloaded from the JNDI software download page:

[`http://www.oracle.com/technetwork/java/index.html`](http://www.oracle.com/technetwork/java/index.html)

The example demonstrates creating an initial context and then performing a lookup for a pool-enabled data source that is bound to the name `MyPooledDataSource`. The object returned is then used to borrow a connection from the connection pool.

    Hashtable env = new Hashtable();
    env.put(Context.INITIAL_CONTEXT_FACTORY,
       "com.sun.jndi.fscontext.RefFSContextFactory");
    env.put(Context.PROVIDER_URL, "file:/tmp");

    ctx = new InitialContext(env);

    PoolDataSource jpds = (PoolDataSource)ctx.lookup(MyPooledDataSource);
    Connection conn = jpds.getConnection();

In the example, `MyPoolDataSource` must be bound to the context. For example:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("<user>");
    pds.setPassword("<password>");

    ctx.bind(MyPooledDataSource, pds);

### 3.1.6 About Connection Initialization Callback

The Connection Initialization Callback enables applications and frameworks to initialize connections retrieved from Universal Connection Pool. It is executed at every connection checkout from the pool, as well as at each successful reconnection during failover.

This section discusses initialization callbacks in the following sections:

- Overview of Connection Initialization Callback

- Creating an Initialization Callback

- Registering an Initialization Callback

- Removing or Unregistering an Initialization Callback

#### 3.1.6.1 Overview of Connection Initialization Callback

If an application cannot use connection labeling because it cannot be changed, then the connection initialization callback is provided for such an application.

When registered, the initialization callback is executed every time a connection is borrowed from the pool and at each successful reconnection following a recoverable error. Using the same callback at both run time and replay ensures that exactly the same initialization, which was used when the original session was established, is reestablished at run time. If the callback invocation fails, then replay is disabled on that connection.

#### 3.1.6.2 Creating an Initialization Callback

To create a UCP connection initialization callback, an application implements the `oracle.ucp.jdbc.ConnectionInitializationCallback` interface. This interface has the following method:

    void initialize(java.sql.Connection connection) throws SQLException;

**Note:**

- One callback is created for every connection pool.

- This callback is not used if a labeling callback is registered for the connection pool.

##### Example

The following example demonstrates how to create a simple initialization callback:

    import oracle.ucp.jdbc.ConnectionInitializationCallback;
    class MyConnectionInitializationCallback implements ConnectionInitializationCallback
    {
      public MyConnectionInitializationCallback()
      {
        ...
      }
      public void initialize(java.sql.Connection connection) throws SQLException
      {
         // Reset the state for the connection, if necessary (like ALTER SESSION)
      }
    }

#### 3.1.6.3 Registering an Initialization Callback

UCP provides the `registerConnectionInitializationCallback` method in the `oracle.ucp.jdbc.PoolDataSource` interface for registering a connection initialization callback.

    public void registerConnectionInitializationCallback (ConnectionInitializationCallback cbk) throws SQLException;

One callback may be registered on each connection pool instance.

#### 3.1.6.4 Removing or Unregistering an Initialization Callback

UCP provides the `unregisterConnectionInitializationCallback` method in the `oracle.ucp.jdbc.PoolDataSource` interface for unregistering a connection initialization callback.

    public void unregisterConnectionInitializationCallback (ConnectionInitializationCallback cbk) throws SQLException;

**See Also:**

[Oracle Universal Connection Pool Java API Reference](../jjuar/index.md) for more information
