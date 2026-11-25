Connections can be validated using pool properties when the connection is borrowed, and also programmatically using the `ValidConnection` interface. Both approaches are detailed in this section. Invalid connections can affect application performance and availability.

### 3.3.1 Validating When Borrowing

A connection can be validated by executing a SQL statement on a connection when the connection is borrowed from the connection pool. Two connection pool properties are used in conjunction in order to enable connection validation:

- `setValidateConnectionOnBorrow(boolean):` Specifies whether or not connections are validated when the connection is borrowed from the connection pool. The method enables validation for every connection that is borrowed from the pool. A value of `false` means no validation is performed. The default value is `false`.

- `setSQLForValidateConnection(String): `Specifies the SQL statement that is executed on a connection when it is borrowed from the pool.

**Note:**

The `setSQLForValidateConnection` property is not recommended when using an Oracle JDBC driver. UCP performs an internal ping when using an Oracle JDBC driver. The mechanism is faster than executing an SQL statement and is overridden if this property is set. Instead, set the `setValidateConnectionOnBorrow` property to `true` and do not include the `setSQLForValidateConnection` property.

The following example demonstrates validating a connection when borrowing the connection from the pool. The example uses Connector/J JDBC driver from MySQL:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionFactoryClassName("com.mysql.jdbc.jdbc2.optional.
       MysqlDataSource");
    pds.setURL("jdbc:mysql://host:3306/mysql");
    pds.setUser("<user>");
    pds.setPassword("<password>");

    pds.setValidateConnectionOnBorrow(true);
    pds.setSQLForValidateConnection("select * from mysql.user");

    Connection conn = pds.getConnection();

**See Also:**

Minimizing Connection Request Delay

### 3.3.2 Minimizing Connection Validation with setSecondsToTrustIdleConnection() Method

In UCP, when you set the value of the `setValidateConnectionOnBorrow(boolean)` method to `true`, then each connection is validated during the checkout. This validation may incur significant overhead in applications that checkout database connections frequently.

To minimize the impact of frequent connection validation, you can now set the` setSecondsToTrustIdleConnection(int)` method with an appropriate value to trust recently-used or recently-tested database connections. Setting this value skips the connection validation test and improves application performance significantly.

The following table describes the new methods available in Oracle Database 19c Release for using this feature:

| Method                                                              | Description                                                                                                                                       |
|:--------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `setSecondsToTrustIdleConnection(int secondsToTrustIdleConnection)` | Sets the time in seconds to trust a recently-used or recently-tested database connection and skip the validation test during connection checkout. |
| `getSecondsToTrustIdleConnection()`                                 | Retrieves the value that was set using the `setSecondsToTrustIdleConnection(int)` method.                                                         |

When you set the `setSecondsToTrustIdleConnection(int)` method to a positive value, then the connection validation is skipped, if the connection was used within the time specified in the `secondsToTrustIdleConnection(int)` method. The default value is 0 seconds, which means that the feature is disabled.

**Note:**

The `setSecondsToTrustIdleConnection(int)` method works only if the `setValidateConnectionOnBorrow(boolean)` method is set to `true`. If you set the `setSecondsToTrustIdleConnection(int)` method to a non-zero value, without setting the `setValidateConnectionOnBorrow(boolean)` method to `true`, then UCP throws the following exception:

    Invalid seconds to trust idle connection value or usage.

### 3.3.3 Checking If a Connection Is Valid

The `oracle.ucp.jdbc.ValidConnection` interface provides two methods: `isValid` and `setInvalid`. The `isValid` method returns whether or not a connection is usable and the `setInvalid` method is used to indicate that a connection should be removed from the pool instance.

The `isValid` method is used to check if a connection is still usable after an SQL exception has been thrown. This method can be used at any time to check if a borrowed connection is valid. The method is particularly useful in combination with a retry mechanism, such as the Fast Connection Failover actions that are triggered after a down event of Oracle RAC.

**Note:**

- The `isValid` method checks with the pool instance and Oracle JDBC driver to determine whether a connection is still valid. The `isValid` method results in a round-trip to the database only if both the pool and the driver report that a connection is still valid. The round-trip is used to check for database failures that are not immediately discovered by the pool or the driver.

- Starting from Oracle Database Release 18c, there is a new variant of the `isValid` method that sends an empty packet to the database unlike the older version of the method that uses a ping-pong protocol and makes a full round-trip to the database.

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/JDBC-getting-started.md)

The `isValid` method is also helpful when used in conjunction with the connection timeout and connection harvesting features. These features may return a connection to the pool while a connection is still held by an application. In such cases, the `isValid` method returns `false`, allowing the application to get a new connection.

The following example demonstrates using the `isValid` method:

    try {  conn = poolDataSouorce.getConnection  ...}catch (SQLException sqlexc)
    {
       if (conn == null || !((ValidConnection) conn).isValid())

       // take the appropriate action

    ...
    conn.close();
    }

For XA applications, before calling the `isValid()` method, you must cast any `XAConnection` that is obtained from `PoolXADataSource` to a `ValidConnection`. If you cast a `Connection` that is obtained by calling the `XAConnection.getConnection()` method to `ValidConnecion`, then it may throw an exception.

**Related Topics**

- [Using Oracle RAC Features](using-Oracle-RAC-features.md)
- [Removing Connections from UCP](removing-connections.md)
