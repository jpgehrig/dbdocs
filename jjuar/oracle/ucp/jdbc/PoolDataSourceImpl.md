Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSourceFactory.md)
- [Next Class](PoolXADataSource.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.ucp.jdbc

## Class PoolDataSourceImpl

- java.lang.Object

- - oracle.ucp.jdbc.PoolDataSourceImpl

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.sql.Wrapper, javax.naming.Referenceable, javax.naming.spi.ObjectFactory, javax.sql.CommonDataSource, javax.sql.DataSource, [PoolDataSource](PoolDataSource.md), [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)

  <!-- -->

  Direct Known Subclasses:
  [PoolXADataSourceImpl](PoolXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public class PoolDataSourceImpl
      extends java.lang.Object
      implements PoolDataSource, java.io.Serializable, javax.naming.Referenceable, javax.naming.spi.ObjectFactory, UniversalConnectionPoolAdapter

  A connection pool-aware data source. This DataSource uses the Universal Connection Pool to get a connection, creating a proxy to that connection, and returning the proxy to the client. When the client calls close on the connection proxy, the underlying physical connection is returned to the pool.
  Besides other data source properties, applications must set the connection factory class name. The connection factory class is a class that implements javax.sql.DataSource and does not implement its own connection pooling. The connection factory's getConnection(...) methods should return a physical JDBC connection to the database. For example, "oracle.jdbc.pool.OracleDataSource" is a valid connection factory class name.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                              | Field and Description            |
    |------------------------------------------------|----------------------------------|
    | `protected java.lang.Object`                   | `m_connectionFactory`            |
    | `protected java.lang.String`                   | `m_connectionFactoryClassName`   |
    | `protected oracle.ucp.jdbc.JDBCConnectionPool` | `m_cp`                           |
    | `static java.lang.String`                      | `SECRET_STORE_CONNECT`           |
    | `static java.lang.String`                      | `SECRET_STORE_DEFAULT_PASSWORD`  |
    | `static java.lang.String`                      | `SECRET_STORE_DEFAULT_USERNAME`  |
    | `static java.lang.String`                      | `SECRET_STORE_PASSWORD`          |
    | `static java.lang.String`                      | `SECRET_STORE_USERNAME`          |

    - ### Fields inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`UCP_ABANDONED_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_AFFINITY_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_CLASS_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_MAX_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_TRIGGER_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_INITIALIZATION_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_HIGH_COST`](PoolDataSource.md)`, `[`UCP_CONNECTION_POOL_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_REPURPOSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_CONNECTION_VALIDATION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_WAIT_TIMEOUT`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_FROM_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_NAME`](PoolDataSource.md)`, `[`UCP_DATABASE_NAME`](PoolDataSource.md)`, `[`UCP_DESCRIPTION`](PoolDataSource.md)`, `[`UCP_FAST_CONNECTION_FAILOVER_ENABLED`](PoolDataSource.md)`, `[`UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_INACTIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_INITIAL_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_LOGIN_TIMEOUT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_COUNT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SERVICE`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SHARD`](PoolDataSource.md)`, `[`UCP_MAX_IDLE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_MAX_STATEMENTS`](PoolDataSource.md)`, `[`UCP_MIN_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_NETWORK_PROTOCOL`](PoolDataSource.md)`, `[`UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE`](PoolDataSource.md)`, `[`UCP_ONS_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_PASSWORD`](PoolDataSource.md)`, `[`UCP_PDB_ROLES`](PoolDataSource.md)`, `[`UCP_PORT_NUMBER`](PoolDataSource.md)`, `[`UCP_PROPERTY_CYCLE`](PoolDataSource.md)`, `[`UCP_ROLE_NAME`](PoolDataSource.md)`, `[`UCP_SECONDS_TO_TRUST_IDLE_CONNECTION`](PoolDataSource.md)`, `[`UCP_SERVER_NAME`](PoolDataSource.md)`, `[`UCP_SERVICE_NAME`](PoolDataSource.md)`, `[`UCP_SHARDING_MODE`](PoolDataSource.md)`, `[`UCP_SQL_FOR_VALIDATE_CONNECTION`](PoolDataSource.md)`, `[`UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_TIMEOUT_CHECK_INTERVAL`](PoolDataSource.md)`, `[`UCP_URL`](PoolDataSource.md)`, `[`UCP_USER`](PoolDataSource.md)`, `[`UCP_VALIDATE_CONNECTION_ON_BORROW`](PoolDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `PoolDataSourceImpl``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                          | Method and Description                                                                                                                                                                                           |
    |----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UCPConnectionBuilder`](UCPConnectionBuilder.md)                          | `createConnectionBuilder``()`<br>Creates a new UCPConnectionBuilder instance.                                                                                                                                    |
    | `protected void`                                                           | `createPoolWithDefaultProperties``()`                                                                                                                                                                            |
    | [`UniversalConnectionPool`](../UniversalConnectionPool.md)                 | `createUniversalConnectionPool``()`<br>Creates a Universal Connection Pool instance using this adapter.                                                                                                          |
    | [`UniversalConnectionPoolMBean`](../admin/UniversalConnectionPoolMBean.md) | `createUniversalConnectionPoolMBean``()`<br>Creates a Universal Connection Pool MBean using this adapter.                                                                                                        |
    | `int`                                                                      | `getAbandonedConnectionTimeout``()`<br>Gets the abandoned connection timeout value.                                                                                                                              |
    | `int`                                                                      | `getAvailableConnectionsCount``()`<br>Gets the number of available connections in the pool.                                                                                                                      |
    | `int`                                                                      | `getBorrowedConnectionsCount``()`<br>Gets the number of borrowed connections from the pool.                                                                                                                      |
    | `java.sql.Connection`                                                      | `getConnection``()`<br>Attempts to obtain a database connection.                                                                                                                                                 |
    | `java.sql.Connection`                                                      | `getConnection``(java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                                                                                 |
    | `java.sql.Connection`                                                      | `getConnection``(java.lang.String username, java.lang.String password)`<br>Attempts to obtain a database connection.                                                                                             |
    | `java.sql.Connection`                                                      | `getConnection``(java.lang.String username, java.lang.String password, java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                           |
    | `java.lang.String`                                                         | `getConnectionFactoryClassName``()`<br>Gets the Connection Factory class name.                                                                                                                                   |
    | `java.util.Properties`                                                     | `getConnectionFactoryProperties``()`<br>Gets the connection factory properties that are set on this data source.                                                                                                 |
    | `java.lang.String`                                                         | `getConnectionFactoryProperty``(java.lang.String propertyName)`<br>Gets the specified connection factory property that are set on this data source.                                                              |
    | `int`                                                                      | `getConnectionHarvestMaxCount``()`<br>Gets the maximum number of connections that may be harvested when the connection harvesting occurs.                                                                        |
    | `int`                                                                      | `getConnectionHarvestTriggerCount``()`<br>Gets the number of available connections at which the connection pool's connection harvesting will occur.                                                              |
    | [`ConnectionInitializationCallback`](ConnectionInitializationCallback.md)  | `getConnectionInitializationCallback``()`<br>Obtains the registered connection initialization callback, if any.                                                                                                  |
    | `int`                                                                      | `getConnectionLabelingHighCost``()`<br>Obtains the cost value which identifies a connection as "high-cost" for connection labeling.                                                                              |
    | `java.lang.String`                                                         | `getConnectionPoolName``()`<br>Gets the connection pool name.                                                                                                                                                    |
    | `java.util.Properties`                                                     | `getConnectionProperties``()`<br>Gets the connection properties that are set on this data source.                                                                                                                |
    | `java.lang.String`                                                         | `getConnectionProperty``(java.lang.String propertyName)`<br>Gets the specified connection property that is set on this data source.                                                                              |
    | `int`                                                                      | `getConnectionRepurposeThreshold``()`<br>Gets the connection repurpose threshold for the pool.                                                                                                                   |
    | `int`                                                                      | `getConnectionValidationTimeout``()`<br>Connection validation timeout getter                                                                                                                                     |
    | `int`                                                                      | `getConnectionWaitTimeout``()`<br>Gets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                                 |
    | `java.lang.String`                                                         | `getDatabaseName``()`<br>Gets the database name.                                                                                                                                                                 |
    | `java.lang.String`                                                         | `getDataSourceName``()`<br>Gets the data source name.                                                                                                                                                            |
    | `java.lang.String`                                                         | `getDescription``()`<br>Gets the data source description.                                                                                                                                                        |
    | `boolean`                                                                  | `getFastConnectionFailoverEnabled``()`<br>Checks if Fast Connection Failover is enabled.                                                                                                                         |
    | `int`                                                                      | `getHighCostConnectionReuseThreshold``()`<br>Obtains the high-cost connection reuse threshold property value for connection labeling.                                                                            |
    | `int`                                                                      | `getInactiveConnectionTimeout``()`<br>Gets the inactive connection timeout.                                                                                                                                      |
    | `int`                                                                      | `getInitialPoolSize``()`<br>Gets the initial pool size.                                                                                                                                                          |
    | `int`                                                                      | `getLoginTimeout``()`<br>Gets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.                                         |
    | `java.io.PrintWriter`                                                      | `getLogWriter``()`                                                                                                                                                                                               |
    | `int`                                                                      | `getMaxConnectionReuseCount``()`<br>Gets the connection reuse count property.                                                                                                                                    |
    | `long`                                                                     | `getMaxConnectionReuseTime``()`<br>Gets the connection reuse time property.                                                                                                                                      |
    | `int`                                                                      | `getMaxConnectionsPerService``()`<br>Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.                                                                      |
    | `int`                                                                      | `getMaxConnectionsPerShard``()`<br>Gets the currently configured max connections that can be created per shard in a sharded database configuration.                                                              |
    | `int`                                                                      | `getMaxIdleTime``()`<br>Gets Idle timeout value.                                                                                                                                                                 |
    | `int`                                                                      | `getMaxPoolSize``()`<br>Gets the maximum number of connections that the connection pool will maintain.                                                                                                           |
    | `int`                                                                      | `getMaxStatements``()`<br>Gets the maximum number of statements that may be pooled or cached on a Connection.                                                                                                    |
    | `int`                                                                      | `getMinPoolSize``()`<br>Gets the minimum number of connections that the connection pool will maintain.                                                                                                           |
    | `java.lang.String`                                                         | `getNetworkProtocol``()`<br>Gets the datasource networkProtocol.                                                                                                                                                 |
    | `java.lang.Object`                                                         | `getObjectInstance``(java.lang.Object refObj, javax.naming.Name name, javax.naming.Context nameCtx, java.util.Hashtable env)`                                                                                    |
    | `java.lang.String`                                                         | `getONSConfiguration``()`<br>Returns the ONS configuration string that is used for remote ONS subscription, in the form specified in setONSConfiguration(String).                                                |
    | `java.util.logging.Logger`                                                 | `getParentLogger``()`                                                                                                                                                                                            |
    | `java.lang.String`                                                         | `getPassword``()`<br>Gets the Password for this data source.                                                                                                                                                     |
    | `java.util.Properties`                                                     | `getPdbRoles``()`<br>Gets the PDB roles specified for this datasource                                                                                                                                            |
    | `int`                                                                      | `getPortNumber``()`<br>Gets the database port number.                                                                                                                                                            |
    | `int`                                                                      | `getPropertyCycle``()`<br>Gets Property cycle in seconds.                                                                                                                                                        |
    | `int`                                                                      | `getQueryTimeout``()`<br>Gets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.                                                                       |
    | `javax.naming.Reference`                                                   | `getReference``()`                                                                                                                                                                                               |
    | `java.lang.String`                                                         | `getRoleName``()`<br>Gets the datasource role name.                                                                                                                                                              |
    | `int`                                                                      | `getSecondsToTrustIdleConnection``()`<br>Gets the seconds To Trust Idle Connection value.                                                                                                                        |
    | `java.lang.String`                                                         | `getServerName``()`<br>Gets the database server name.                                                                                                                                                            |
    | `java.lang.String`                                                         | `getServiceName``()`<br>Gets the service name set on this data source                                                                                                                                            |
    | `boolean`                                                                  | `getShardingMode``()`<br>Returns the mode of UCP when UCP is using a Sharded Database.                                                                                                                           |
    | `java.lang.String`                                                         | `getSQLForValidateConnection``()`<br>Gets the Value for SQLForValidateConnection property.                                                                                                                       |
    | `protected javax.net.ssl.SSLContext`                                       | `getSSLContext``()`<br>Returns SSL context associated with the datasource.                                                                                                                                       |
    | [`JDBCConnectionPoolStatistics`](JDBCConnectionPoolStatistics.md)          | `getStatistics``()`<br>Gets the statistics of the connection pool.                                                                                                                                               |
    | `int`                                                                      | `getTimeoutCheckInterval``()`<br>Gets the timeout check interval (in seconds).                                                                                                                                   |
    | `int`                                                                      | `getTimeToLiveConnectionTimeout``()`<br>Gets the maximum time (in seconds) a connection may remain in-use.                                                                                                       |
    | `java.lang.String`                                                         | `getURL``()`<br>Gets the URL for this data source.                                                                                                                                                               |
    | `java.lang.String`                                                         | `getUser``()`<br>Gets the user name for this data source.                                                                                                                                                        |
    | `boolean`                                                                  | `getValidateConnectionOnBorrow``()`<br>Returns whether or not a connection being borrowed should first be validated.                                                                                             |
    | `protected void`                                                           | `ilogFine``(java.util.logging.Logger logger, java.lang.Class cls, java.lang.reflect.Executable method, java.lang.Object receiver, java.lang.String message)`                                                     |
    | `protected void`                                                           | `ilogFinest``(java.util.logging.Logger logger, java.lang.Class cls, java.lang.reflect.Executable method, java.lang.Object receiver, java.lang.String message)`<br>Helpers for writing into log and logWriter     |
    | `protected void`                                                           | `ilogSevere``(java.util.logging.Logger logger, java.lang.Class cls, java.lang.reflect.Executable method, java.lang.Object receiver, java.lang.String message)`                                                   |
    | `protected void`                                                           | `ilogThrowing``(java.util.logging.Logger logger, java.lang.Class cls, java.lang.reflect.Executable method, java.lang.Object receiver, java.lang.Throwable throwable)`                                            |
    | `protected void`                                                           | `ilogWarning``(java.util.logging.Logger logger, java.lang.Class cls, java.lang.reflect.Executable method, java.lang.Object receiver, java.lang.String message)`                                                  |
    | `static boolean`                                                           | `isSetOnceProperty``(java.lang.String key)`<br>Authentication kays to enforce to be set up once per a single pool data source                                                                                    |
    | `boolean`                                                                  | `isWrapperFor``(java.lang.Class<?> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                   |
    | `void`                                                                     | `reconfigureDataSource``(java.util.Properties configuration)`<br>Reconfigures the data source.                                                                                                                   |
    | `void`                                                                     | `registerConnectionAffinityCallback``(`[`ConnectionAffinityCallback`](../ConnectionAffinityCallback.md)` cbk)`<br>Registers a ConnectionAffinityCallback on the connection pool.                                 |
    | `void`                                                                     | `registerConnectionInitializationCallback``(`[`ConnectionInitializationCallback`](ConnectionInitializationCallback.md)` cbk)`<br>Registers a connection initialization callback.                                 |
    | `void`                                                                     | `registerConnectionLabelingCallback``(`[`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)` cbk)`<br>Registers a ConnectionLabelingCallback with the underlying connection pool.                    |
    | `void`                                                                     | `removeConnectionAffinityCallback``()`<br>Removes the ConnectionAffinityCallback registered on the connection pool.                                                                                              |
    | `void`                                                                     | `removeConnectionLabelingCallback``()`<br>Removes the ConnectionLabelingCallback object registered with the underlying connection pool, if any.                                                                  |
    | `void`                                                                     | `setAbandonedConnectionTimeout``(int abandonedConnectionTimeout)`<br>Sets the abandoned connection timeout.                                                                                                      |
    | `void`                                                                     | `setConnectionFactoryClassName``(java.lang.String factoryClassName)`<br>Sets the Connection Factory class name.                                                                                                  |
    | `void`                                                                     | `setConnectionFactoryProperties``(java.util.Properties factoryProperties)`<br>Sets the connection factory properties on the connection factory.                                                                  |
    | `void`                                                                     | `setConnectionFactoryProperty``(java.lang.String name, java.lang.String value)`<br>Sets a connection factory property on the connection factory.                                                                 |
    | `void`                                                                     | `setConnectionHarvestMaxCount``(int connectionHarvestMaxCount)`<br>Sets the maximum number of connections that may be harvested when the connection harvesting occurs.                                           |
    | `void`                                                                     | `setConnectionHarvestTriggerCount``(int connectionHarvestTriggerCount)`<br>Sets the number of available connections at which the connection pool's connection harvesting will occur.                             |
    | `void`                                                                     | `setConnectionLabelingHighCost``(int highCost)`<br>Sets the cost value which identifies a connection as "high-cost" for connection labeling.                                                                     |
    | `void`                                                                     | `setConnectionPoolName``(java.lang.String connectionPoolName)`<br>Sets the connection pool name.                                                                                                                 |
    | `void`                                                                     | `setConnectionProperties``(java.util.Properties connectionProperties)`<br>Sets the connection properties on the connection factory.                                                                              |
    | `void`                                                                     | `setConnectionProperty``(java.lang.String name, java.lang.String value)`<br>Sets a connection property on the connection factory.                                                                                |
    | `void`                                                                     | `setConnectionRepurposeThreshold``(int threshold)`<br>Sets the connection repurpose threshold for the pool.                                                                                                      |
    | `void`                                                                     | `setConnectionValidationTimeout``(int connectionValidationTimeout)`<br>This property changes the connection validation timeout which is specified in seconds.                                                    |
    | `void`                                                                     | `setConnectionWaitTimeout``(int waitTimeout)`<br>Sets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                  |
    | `void`                                                                     | `setDatabaseName``(java.lang.String databaseName)`<br>Sets the database name.                                                                                                                                    |
    | `void`                                                                     | `setDataSourceName``(java.lang.String dataSourceName)`<br>Sets the data source name.                                                                                                                             |
    | `void`                                                                     | `setDescription``(java.lang.String description)`<br>Sets the data source description.                                                                                                                            |
    | `void`                                                                     | `setFastConnectionFailoverEnabled``(boolean failoverEnabled)`<br>Enables Fast Connection Failover (FCF) for the connection pool accessed using this pool-enabled data source.                                    |
    | `void`                                                                     | `setHighCostConnectionReuseThreshold``(int threshold)`<br>Sets the high-cost connection reuse threshold for connection labeling.                                                                                 |
    | `void`                                                                     | `setInactiveConnectionTimeout``(int inactivityTimeout)`<br>Sets the inactive connection timeout.                                                                                                                 |
    | `void`                                                                     | `setInitialPoolSize``(int initialPoolSize)`<br>Sets the initial pool size.                                                                                                                                       |
    | `void`                                                                     | `setLoginTimeout``(int seconds)`<br>Sets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.                              |
    | `void`                                                                     | `setLogWriter``(java.io.PrintWriter logWriter)`                                                                                                                                                                  |
    | `void`                                                                     | `setMaxConnectionReuseCount``(int maxConnectionReuseCount)`<br>Gets the connection reuse count property.                                                                                                         |
    | `void`                                                                     | `setMaxConnectionReuseTime``(long maxConnectionReuseTime)`<br>Gets the connection reuse time property.                                                                                                           |
    | `void`                                                                     | `setMaxConnectionsPerShard``(int maxConnectionsPerShard)`<br>Sets the max number of connections that can be created per shard in a sharded database configuration.                                               |
    | `void`                                                                     | `setMaxIdleTime``(int idleTime)`<br>Sets Idle timeout for available connections in the pool.                                                                                                                     |
    | `void`                                                                     | `setMaxPoolSize``(int maxPoolSize)`<br>Sets the maximum number of connections.                                                                                                                                   |
    | `void`                                                                     | `setMaxStatements``(int maxStatements)`<br>Sets the maximum number of statements that may be pooled or cached on a connection.                                                                                   |
    | `void`                                                                     | `setMinPoolSize``(int minPoolSize)`<br>Sets the minimum number of connections.                                                                                                                                   |
    | `void`                                                                     | `setNetworkProtocol``(java.lang.String networkProtocol)`<br>Sets the datasource networkProtocol.                                                                                                                 |
    | `void`                                                                     | `setONSConfiguration``(java.lang.String onsConfigStr)`<br>Sets the configuration string used for remote ONS subscription.                                                                                        |
    | `void`                                                                     | `setPassword``(java.lang.String password)`<br>Sets the password with which connections have to be obtained.                                                                                                      |
    | `void`                                                                     | `setPortNumber``(int portNumber)`<br>Sets the database port number.                                                                                                                                              |
    | `void`                                                                     | `setPropertyCycle``(int propertyCycle)`<br>Sets Property cycle in seconds.                                                                                                                                       |
    | `void`                                                                     | `setQueryTimeout``(int queryTimeout)`<br>Sets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.                                                       |
    | `void`                                                                     | `setRoleName``(java.lang.String roleName)`<br>Sets the datasource role name.                                                                                                                                     |
    | `void`                                                                     | `setSecondsToTrustIdleConnection``(int secondsToTrustIdleConnection)`<br>Sets the time in seconds to trust an idle connection to skip a validation test.                                                         |
    | `void`                                                                     | `setServerName``(java.lang.String serverName)`<br>Sets the database server name.                                                                                                                                 |
    | `void`                                                                     | `setShardingMode``(boolean shardingMode)`<br>This API changes the mode of UCP when UCP is using a Sharded Database.                                                                                              |
    | `void`                                                                     | `setSQLForValidateConnection``(java.lang.String SQLString)`<br>Sets the value(SQL) for SQLForValidateConnection property.                                                                                        |
    | `void`                                                                     | `setSSLContext``(javax.net.ssl.SSLContext sslContext)`<br>Specifies a `SSLContext` to use as a factory for SSLEngine objects that carry out the TLS protocol.                                                    |
    | `void`                                                                     | `setTimeoutCheckInterval``(int timeInterval)`<br>Sets the timeoutCheckInterval (in seconds).                                                                                                                     |
    | `void`                                                                     | `setTimeToLiveConnectionTimeout``(int timeToLiveConnectionTimeout)`<br>Sets the maximum time (in seconds) a connection may remain in-use.                                                                        |
    | `void`                                                                     | `setTokenSupplier``(java.util.function.Supplier<? extends oracle.jdbc.AccessToken> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`. |
    | `void`                                                                     | `setURL``(java.lang.String url)`<br>Sets the URL that the data source uses to obtain connections to the database.                                                                                                |
    | `void`                                                                     | `setUser``(java.lang.String user)`<br>Sets the user name with which connections have to be obtained.                                                                                                             |
    | `void`                                                                     | `setValidateConnectionOnBorrow``(boolean validateConnectionOnBorrow)`<br>Sets whether or not a connection being borrowed should first be validated.                                                              |
    | `void`                                                                     | `startPool``()`<br>This helper method gets all the pool properties for pool initialization, creates a pool and starts it.                                                                                        |
    | `static java.lang.Object`                                                  | `toBasicType``(java.lang.String value, java.lang.String type)`                                                                                                                                                   |
    | `void`                                                                     | `unregisterConnectionInitializationCallback``()`<br>Unregisters the connection initialization callback on this pool.                                                                                             |
    | `<T> T`                                                                    | `unwrap``(java.lang.Class<T> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`createShardingKeyBuilder`](PoolDataSource.md)

<!-- -->

- - ### Field Detail

    - #### SECRET_STORE_CONNECT

          public static final java.lang.String SECRET_STORE_CONNECT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECRET_STORE_USERNAME

          public static final java.lang.String SECRET_STORE_USERNAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECRET_STORE_PASSWORD

          public static final java.lang.String SECRET_STORE_PASSWORD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECRET_STORE_DEFAULT_USERNAME

          public static final java.lang.String SECRET_STORE_DEFAULT_USERNAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECRET_STORE_DEFAULT_PASSWORD

          public static final java.lang.String SECRET_STORE_DEFAULT_PASSWORD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### m_connectionFactoryClassName

          protected java.lang.String m_connectionFactoryClassName

    <!-- -->

    - #### m_connectionFactory

          protected java.lang.Object m_connectionFactory

    <!-- -->

    - #### m_cp

          protected transient oracle.ucp.jdbc.JDBCConnectionPool m_cp

  <!-- -->

  - ### Constructor Detail

    - #### PoolDataSourceImpl

          public PoolDataSourceImpl()

  <!-- -->

  - ### Method Detail

    - #### startPool

          public void startPool()
                         throws java.sql.SQLException

      This helper method gets all the pool properties for pool initialization, creates a pool and starts it.
      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### createPoolWithDefaultProperties

          protected void createPoolWithDefaultProperties()
                                                  throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createUniversalConnectionPool

          public UniversalConnectionPool createUniversalConnectionPool()
                                                                throws java.sql.SQLException

      Creates a Universal Connection Pool instance using this adapter. Pool and connection factory configuration properties should be set on this adapter prior to invoking this method.
      This method should not register the created pool instance with the Universal Connection Pool Manager. The method createConnectionPool on the UniversalConnectionPoolManager is responsible for that.

      This method is intended to be used in association with a UniversalConnectionPoolManager or MBean. Do not directly invoke this method from an instance of this class.

      Specified by:
      [`createUniversalConnectionPool`](../UniversalConnectionPoolAdapter.md) in interface [`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)

      Returns:
      The created Universal Connection Pool instance.

      Throws:
      `java.sql.SQLException` - If any error occurs during the process of connection pool creation.

      See Also:
      [`UniversalConnectionPoolManager`](../admin/UniversalConnectionPoolManager.md)

    <!-- -->

    - #### reconfigureDataSource

          public void reconfigureDataSource(java.util.Properties configuration)
                                     throws java.sql.SQLException

      Reconfigures the data source. This API can be only used to modify existing data source properties. To add a new data source to a running pool instance, use PoolDataSourceFactory's getPoolDataSource(Properties configuration) API instead. Only the following data source properties can be modified using this API: `user`, `password`, `description`, `serviceName`, `pdbRoles`.
      Specified by:
      [`reconfigureDataSource`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `configuration` - the configuration input

      Throws:
      `java.sql.SQLException` - If an error occurs while configuring the data source.

    <!-- -->

    - #### createUniversalConnectionPoolMBean

          public UniversalConnectionPoolMBean createUniversalConnectionPoolMBean()
                                                                          throws java.sql.SQLException

      Creates a Universal Connection Pool MBean using this adapter. If a Universal Connection Pool instance is not yet created, this method must first create a pool instance, in which case pool and connection factory configuration properties should be set on this adapter prior to invoking this method.
      This method should not register the created pool MBean with the MBean server. The operation createConnectionPool on the UniversalConnectionPoolManagerMBean is responsible for that.

      Specified by:
      [`createUniversalConnectionPoolMBean`](../UniversalConnectionPoolAdapter.md) in interface [`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)

      Returns:
      The created Universal Connection Pool MBean.

      Throws:
      `java.sql.SQLException` - If any error occurs during the process of connection pool creation.

      See Also:
      [`UniversalConnectionPoolManagerMBean`](../admin/UniversalConnectionPoolManagerMBean.md)

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()
                                            throws java.sql.SQLException

      Attempts to obtain a database connection.
      Specified by:
      `getConnection` in interface `javax.sql.DataSource`

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection(java.lang.String username,
                                                   java.lang.String password)
                                            throws java.sql.SQLException

      Attempts to obtain a database connection.
      Specified by:
      `getConnection` in interface `javax.sql.DataSource`

      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection(java.util.Properties labels)
                                            throws java.sql.SQLException

      Attempts to obtain a database connection with the requested connection labels.
      Specified by:
      [`getConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `labels` - The requested connection labels.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection(java.lang.String username,
                                                   java.lang.String password,
                                                   java.util.Properties labels)
                                            throws java.sql.SQLException

      Attempts to obtain a database connection with the requested connection labels.
      Specified by:
      [`getConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      `labels` - The requested connection labels.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getLogWriter

          public java.io.PrintWriter getLogWriter()
                                           throws java.sql.SQLException

      Specified by:
      `getLogWriter` in interface `javax.sql.CommonDataSource`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setLogWriter

          public void setLogWriter(java.io.PrintWriter logWriter)
                            throws java.sql.SQLException

      Specified by:
      `setLogWriter` in interface `javax.sql.CommonDataSource`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setLoginTimeout

          public void setLoginTimeout(int seconds)
                               throws java.sql.SQLException

      Sets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.
      Specified by:
      `setLoginTimeout` in interface `javax.sql.CommonDataSource`

      Parameters:
      `seconds` - timeout

      Throws:
      `java.sql.SQLException` - in case of negative value

    <!-- -->

    - #### getLoginTimeout

          public int getLoginTimeout()

      Gets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.
      Specified by:
      `getLoginTimeout` in interface `javax.sql.CommonDataSource`

      Returns:
      timeout in seconds

    <!-- -->

    - #### getUser

          public java.lang.String getUser()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the user name for this data source.
      Specified by:
      [`getUser`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      userName for this data source.

    <!-- -->

    - #### setUser

          public void setUser(java.lang.String user)
                       throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the user name with which connections have to be obtained.
      Specified by:
      [`setUser`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `user` - Username to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPassword

          public java.lang.String getPassword()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the Password for this data source.
      Specified by:
      [`getPassword`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      password for this data source.

    <!-- -->

    - #### setPassword

          public void setPassword(java.lang.String password)
                           throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the password with which connections have to be obtained.
      Specified by:
      [`setPassword`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `password` - Password to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getURL

          public java.lang.String getURL()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the URL for this data source.
      Specified by:
      [`getURL`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      URL for this data source.

    <!-- -->

    - #### setURL

          public void setURL(java.lang.String url)
                      throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the URL that the data source uses to obtain connections to the database.
      Specified by:
      [`setURL`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `url` - URL to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setServerName

          public void setServerName(java.lang.String serverName)
                             throws java.sql.SQLException

      Sets the database server name.
      Specified by:
      [`setServerName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `serverName` - Database server name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getServerName

          public java.lang.String getServerName()

      Gets the database server name.
      Specified by:
      [`getServerName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Database server name.

    <!-- -->

    - #### setPortNumber

          public void setPortNumber(int portNumber)
                             throws java.sql.SQLException

      Sets the database port number.
      Specified by:
      [`setPortNumber`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `portNumber` - Database port number to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPortNumber

          public int getPortNumber()

      Gets the database port number.
      Specified by:
      [`getPortNumber`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Database port number.

    <!-- -->

    - #### setDatabaseName

          public void setDatabaseName(java.lang.String databaseName)
                               throws java.sql.SQLException

      Sets the database name.
      Specified by:
      [`setDatabaseName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `databaseName` - Database name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDatabaseName

          public java.lang.String getDatabaseName()

      Gets the database name.
      Specified by:
      [`getDatabaseName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Database name.

    <!-- -->

    - #### setDataSourceName

          public void setDataSourceName(java.lang.String dataSourceName)
                                 throws java.sql.SQLException

      Sets the data source name.
      Specified by:
      [`setDataSourceName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `dataSourceName` - data source name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDataSourceName

          public java.lang.String getDataSourceName()

      Gets the data source name.
      Specified by:
      [`getDataSourceName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      data source name.

    <!-- -->

    - #### setDescription

          public void setDescription(java.lang.String description)
                              throws java.sql.SQLException

      Sets the data source description.
      Specified by:
      [`setDescription`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `description` - data source description to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDescription

          public java.lang.String getDescription()

      Gets the data source description.
      Specified by:
      [`getDescription`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      data source description.

    <!-- -->

    - #### setNetworkProtocol

          public void setNetworkProtocol(java.lang.String networkProtocol)
                                  throws java.sql.SQLException

      Sets the datasource networkProtocol.
      Specified by:
      [`setNetworkProtocol`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `networkProtocol` - datasource networkProtocol to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkProtocol

          public java.lang.String getNetworkProtocol()

      Gets the datasource networkProtocol.
      Specified by:
      [`getNetworkProtocol`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      datasource networkProtocol.

    <!-- -->

    - #### setRoleName

          public void setRoleName(java.lang.String roleName)
                           throws java.sql.SQLException

      Sets the datasource role name.
      Specified by:
      [`setRoleName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `roleName` - datasource role name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getRoleName

          public java.lang.String getRoleName()

      Gets the datasource role name.
      Specified by:
      [`getRoleName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      datasource role name.

    <!-- -->

    - #### setInitialPoolSize

          public void setInitialPoolSize(int initialPoolSize)
                                  throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the initial pool size. This is the number of connections that will be created and placed in the pool when the pool is started.
      The range of valid values is 0 to `Integer.MAX_VALUE`. It is illegal to set this to a value greater than the maximum pool size. Defaults to 0.

      Specified by:
      [`setInitialPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `initialPoolSize` - the initial pool size.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getInitialPoolSize

          public int getInitialPoolSize()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the initial pool size.
      Specified by:
      [`getInitialPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      the initial pool size.

    <!-- -->

    - #### setMinPoolSize

          public void setMinPoolSize(int minPoolSize)
                              throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the minimum number of connections. If the number of available connections + the number of connections in use \< the minimum then the connection is returned to the pool. Otherwise, the connection is closed.
      The range of valid values is 0 to `Integer.MAX_VALUE`. It is illegal to set this to a value greater than the maximum pool size. Defaults to 0.

      Specified by:
      [`setMinPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `minPoolSize` - The minimum number of connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMinPoolSize

          public int getMinPoolSize()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the minimum number of connections that the connection pool will maintain.
      Specified by:
      [`getMinPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The minimum number of connections.

    <!-- -->

    - #### setMaxPoolSize

          public void setMaxPoolSize(int maxPoolSize)
                              throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the maximum number of connections. The maximum number of connections includes the number of connections that are in use as well as the number of available connections.
      The range of valid values is 1 to `Integer.MAX_VALUE`. Defaults to `Integer.MAX_VALUE`.

      Specified by:
      [`setMaxPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `maxPoolSize` - The maximum number of connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxPoolSize

          public int getMaxPoolSize()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the maximum number of connections that the connection pool will maintain.
      Specified by:
      [`getMaxPoolSize`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The maximum number of connections.

    <!-- -->

    - #### getMaxConnectionsPerService

          public int getMaxConnectionsPerService()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.
      Specified by:
      [`getMaxConnectionsPerService`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The maximum number of connections that can be obtained to a particular service.

    <!-- -->

    - #### setInactiveConnectionTimeout

          public void setInactiveConnectionTimeout(int inactivityTimeout)
                                            throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the inactive connection timeout. This timeout determines how long an available connection remains in the connection pool before it is removed from the pool.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables inactive connection timeout processing.

      Specified by:
      [`setInactiveConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `inactivityTimeout` - The inactive connection timeout in seconds.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getInactiveConnectionTimeout

          public int getInactiveConnectionTimeout()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the inactive connection timeout.
      Specified by:
      [`getInactiveConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The inactivity timeout.

    <!-- -->

    - #### setConnectionWaitTimeout

          public void setConnectionWaitTimeout(int waitTimeout)
                                        throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the amount of time to wait (in seconds) for a used connection to be released by a client.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 3.

      Setting the value to 0 disables connection wait timeout processing.

      Specified by:
      [`setConnectionWaitTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `waitTimeout` - The amount of time to wait.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionWaitTimeout

          public int getConnectionWaitTimeout()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the amount of time to wait (in seconds) for a used connection to be released by a client. This only applies when the maximum number of connections has been borrowed from the connection pool. When a client tries to borrow a connection from the pool and all connections are in use, the connection pool waits for a connection to be released back to the pool.
      Specified by:
      [`getConnectionWaitTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The connection wait timeout.

    <!-- -->

    - #### setTimeToLiveConnectionTimeout

          public void setTimeToLiveConnectionTimeout(int timeToLiveConnectionTimeout)
                                              throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the maximum time (in seconds) a connection may remain in-use.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables time-to-live connection timeout processing.

      Specified by:
      [`setTimeToLiveConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `timeToLiveConnectionTimeout` - The maximum time (in seconds) a used connection may be active.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getTimeToLiveConnectionTimeout

          public int getTimeToLiveConnectionTimeout()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the maximum time (in seconds) a connection may remain in-use. When this timeout expires, the used connection is unconditionally returned to the connection pool. A value of 0 means that the feature is not enabled.
      Specified by:
      [`getTimeToLiveConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The maximum time (in seconds) a used connection may be active.

    <!-- -->

    - #### getAbandonedConnectionTimeout

          public int getAbandonedConnectionTimeout()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the abandoned connection timeout value.
      Specified by:
      [`getAbandonedConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The abandoned connection timeout.

    <!-- -->

    - #### setAbandonedConnectionTimeout

          public void setAbandonedConnectionTimeout(int abandonedConnectionTimeout)
                                             throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the abandoned connection timeout. This timeout determines how long a borrowed connection can remain unused before it is considered as abandoned and reclaimed by the connection pool.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables abandoned connection timeout.

      Specified by:
      [`setAbandonedConnectionTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `abandonedConnectionTimeout` - The value of how long a connection has not been used before it is abandoned (in seconds).

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setTimeoutCheckInterval

          public void setTimeoutCheckInterval(int timeInterval)
                                       throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the timeoutCheckInterval (in seconds). This interval specifies how often the timeout properties such as InactiveConnectionTimeout, AbandonedConnectionTimeout, and TimeToLiveConnectionTimeout are enforced.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 30.

      Setting the value to 0 disables all connection timeout processing.

      Specified by:
      [`setTimeoutCheckInterval`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `timeInterval` - The timeInterval (in seconds) between checks to enforce the timeout properties.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getTimeoutCheckInterval

          public int getTimeoutCheckInterval()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the timeout check interval (in seconds).
      Specified by:
      [`getTimeoutCheckInterval`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      timeInterval The `timeInterval` (in seconds) between checks to enforce the timeout properties.

    <!-- -->

    - #### setFastConnectionFailoverEnabled

          public void setFastConnectionFailoverEnabled(boolean failoverEnabled)
                                                throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Enables Fast Connection Failover (FCF) for the connection pool accessed using this pool-enabled data source. By default, FCF is disabled.
      Specified by:
      [`setFastConnectionFailoverEnabled`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `failoverEnabled` - `true` if Fast Connection Failover is enabled; `false` if not.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getFastConnectionFailoverEnabled

          public boolean getFastConnectionFailoverEnabled()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Checks if Fast Connection Failover is enabled.
      Specified by:
      [`getFastConnectionFailoverEnabled`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      `true` if Fast Connection Failover is enabled; `false` if not.

    <!-- -->

    - #### getConnectionFactoryClassName

          public java.lang.String getConnectionFactoryClassName()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the Connection Factory class name.
      Specified by:
      [`getConnectionFactoryClassName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Name of the connection factory class specified.

    <!-- -->

    - #### setConnectionFactoryClassName

          public void setConnectionFactoryClassName(java.lang.String factoryClassName)
                                             throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the Connection Factory class name. This is the connection factory used by the connection pool to create physical connections. Must be set for `PoolDataSource` to operate.
      Specified by:
      [`setConnectionFactoryClassName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `factoryClassName` - Connection factory class name for obtaining physical connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setMaxStatements

          public void setMaxStatements(int maxStatements)
                                throws java.sql.SQLException

      Sets the maximum number of statements that may be pooled or cached on a connection. This is used to enable the statement pooling.
      Specified by:
      [`setMaxStatements`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `maxStatements` - maximum number of statements to be pooled.

      Throws:
      `java.sql.SQLException` - Exception occurred during the process of setting maximum statements that may be pooled on a connection.

    <!-- -->

    - #### getMaxStatements

          public int getMaxStatements()

      Gets the maximum number of statements that may be pooled or cached on a Connection.
      Specified by:
      [`getMaxStatements`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The maximum number of statements that may be pooled or cached on a Connection.

    <!-- -->

    - #### setMaxIdleTime

          public void setMaxIdleTime(int idleTime)
                              throws java.sql.SQLException

      Sets Idle timeout for available connections in the pool.
      Specified by:
      [`setMaxIdleTime`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `idleTime` - Idle timeout value in seconds.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxIdleTime

          public int getMaxIdleTime()

      Gets Idle timeout value.
      Specified by:
      [`getMaxIdleTime`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Idle timeout.

    <!-- -->

    - #### setPropertyCycle

          public void setPropertyCycle(int propertyCycle)
                                throws java.sql.SQLException

      Sets Property cycle in seconds. This is the time interval between checks to enforce connection pool timeout properties.
      Specified by:
      [`setPropertyCycle`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `propertyCycle` - Time interval in seconds to enforce connection pool timeout properties.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPropertyCycle

          public int getPropertyCycle()

      Gets Property cycle in seconds.
      Specified by:
      [`getPropertyCycle`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      PropertyCycle value.

    <!-- -->

    - #### setConnectionPoolName

          public void setConnectionPoolName(java.lang.String connectionPoolName)
                                     throws java.sql.SQLException

      Sets the connection pool name. This property allows the user to specify a String value to name a connection pool instance.
      Specified by:
      [`setConnectionPoolName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connectionPoolName` - Name of connection pool.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionPoolName

          public java.lang.String getConnectionPoolName()

      Gets the connection pool name.
      Specified by:
      [`getConnectionPoolName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      connectionpoolName.

    <!-- -->

    - #### setValidateConnectionOnBorrow

          public void setValidateConnectionOnBorrow(boolean validateConnectionOnBorrow)
                                             throws java.sql.SQLException

      Sets whether or not a connection being borrowed should first be validated.
      Specified by:
      [`setValidateConnectionOnBorrow`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `validateConnectionOnBorrow` - Whether or not a connection being borrowed should first be validated.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getValidateConnectionOnBorrow

          public boolean getValidateConnectionOnBorrow()

      Returns whether or not a connection being borrowed should first be validated.
      Specified by:
      [`getValidateConnectionOnBorrow`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Whether or not a connection being borrowed should first be validated.

    <!-- -->

    - #### setSQLForValidateConnection

          public void setSQLForValidateConnection(java.lang.String SQLString)
                                           throws java.sql.SQLException

      Sets the value(SQL) for SQLForValidateConnection property. This is used in conjunction with the ValidateConnectionOnBorrow property. The SQL specified should be applicable to back end database and the JDBC driver configured.
      Specified by:
      [`setSQLForValidateConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `SQLString` - The SQL string used for connection validation.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getSQLForValidateConnection

          public java.lang.String getSQLForValidateConnection()

      Gets the Value for SQLForValidateConnection property.
      Specified by:
      [`getSQLForValidateConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      SQLForValidateConnection value.

    <!-- -->

    - #### getConnectionHarvestTriggerCount

          public int getConnectionHarvestTriggerCount()

      Gets the number of available connections at which the connection pool's connection harvesting will occur.
      Specified by:
      [`getConnectionHarvestTriggerCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The number of available connections at which the connection pool's connection harvesting will occur.

    <!-- -->

    - #### setConnectionHarvestTriggerCount

          public void setConnectionHarvestTriggerCount(int connectionHarvestTriggerCount)
                                                throws java.sql.SQLException

      Sets the number of available connections at which the connection pool's connection harvesting will occur.
      Specified by:
      [`setConnectionHarvestTriggerCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connectionHarvestTriggerCount` - The number of available connections at which the connection pool's connection harvesting will occur.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionHarvestMaxCount

          public int getConnectionHarvestMaxCount()

      Gets the maximum number of connections that may be harvested when the connection harvesting occurs. Note that it is possible that the number of connections that are harvested may be anywhere from 0 to the connectionHarvestMaxCount.
      Specified by:
      [`getConnectionHarvestMaxCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The maximum number of connections that may be harvested when the connection harvesting occurs.

    <!-- -->

    - #### setConnectionHarvestMaxCount

          public void setConnectionHarvestMaxCount(int connectionHarvestMaxCount)
                                            throws java.sql.SQLException

      Sets the maximum number of connections that may be harvested when the connection harvesting occurs.
      Specified by:
      [`setConnectionHarvestMaxCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connectionHarvestMaxCount` - the maximum number of connections that may be harvested when the connection harvesting occurs.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxConnectionReuseTime

          public long getMaxConnectionReuseTime()

      Gets the connection reuse time property.
      Specified by:
      [`getMaxConnectionReuseTime`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      connection reuse time (in seconds), 0 value means that the feature is disabled.

    <!-- -->

    - #### setMaxConnectionReuseTime

          public void setMaxConnectionReuseTime(long maxConnectionReuseTime)
                                         throws java.sql.SQLException

      Gets the connection reuse time property.
      Specified by:
      [`setMaxConnectionReuseTime`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connection` - reuse time (in seconds), 0 value means that the feature is disabled.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxConnectionReuseCount

          public int getMaxConnectionReuseCount()

      Gets the connection reuse count property.
      Specified by:
      [`getMaxConnectionReuseCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      connection reuse count, 0 value means that the feature is disabled.

    <!-- -->

    - #### setMaxConnectionReuseCount

          public void setMaxConnectionReuseCount(int maxConnectionReuseCount)
                                          throws java.sql.SQLException

      Gets the connection reuse count property.
      Specified by:
      [`setMaxConnectionReuseCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connection` - reuse count, 0 value means that the feature is disabled.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getAvailableConnectionsCount

          public int getAvailableConnectionsCount()

      Gets the number of available connections in the pool.
      Specified by:
      [`getAvailableConnectionsCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      AvailableConnectionsCount.

    <!-- -->

    - #### getBorrowedConnectionsCount

          public int getBorrowedConnectionsCount()

      Gets the number of borrowed connections from the pool.
      Specified by:
      [`getBorrowedConnectionsCount`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      BorrowedConnectionsCount.

    <!-- -->

    - #### getONSConfiguration

          public java.lang.String getONSConfiguration()
                                               throws java.sql.SQLException

      Returns the ONS configuration string that is used for remote ONS subscription, in the form specified in setONSConfiguration(String). This is used by Fast Connection Failover and Runtime Load Balancing.
      Specified by:
      [`getONSConfiguration`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The ONS configuration string used for remote ONS subscription.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setONSConfiguration

          public void setONSConfiguration(java.lang.String onsConfigStr)
                                   throws java.sql.SQLException

      Sets the configuration string used for remote ONS subscription. The parameter string closely resembles the content of the ONS configuration file "ons.config", and contains a list of "\<name\>=\<value\>" pairs separated by newline character '\n', where \<name\> can be one of "nodes", "walletfile", or "walletpassword". The parameter string should at least specify the ONS configuration attribute "nodes", as a list of host:port pairs separated by comma ','. SSL would be used when the "walletfile" attribute is specified as an Oracle wallet file.
      An example ONS configuration string:

             "nodes=host1:4200,host2:4200\nwalletfile=wfile\nwalletpassword=wpwd"


      This is used primarily by Fast Connection Failover and Runtime Load Balancing.

      Specified by:
      [`setONSConfiguration`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `onsConfigStr` - The configuration string for remote ONS subscription.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### registerConnectionLabelingCallback

          public void registerConnectionLabelingCallback(ConnectionLabelingCallback cbk)
                                                  throws java.sql.SQLException

      Registers a ConnectionLabelingCallback with the underlying connection pool.
      Specified by:
      [`registerConnectionLabelingCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `cbk` - The ConnectionLabelingCallback object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the pool.

    <!-- -->

    - #### removeConnectionLabelingCallback

          public void removeConnectionLabelingCallback()
                                                throws java.sql.SQLException

      Removes the ConnectionLabelingCallback object registered with the underlying connection pool, if any.
      Specified by:
      [`removeConnectionLabelingCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### registerConnectionAffinityCallback

          public void registerConnectionAffinityCallback(ConnectionAffinityCallback cbk)
                                                  throws java.sql.SQLException

      Registers a ConnectionAffinityCallback on the connection pool.
      Specified by:
      [`registerConnectionAffinityCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `cbk` - Affinity Callback object that must be registered.

      Throws:
      `java.sql.SQLException` - If callback registration fails.

    <!-- -->

    - #### removeConnectionAffinityCallback

          public void removeConnectionAffinityCallback()
                                                throws java.sql.SQLException

      Removes the ConnectionAffinityCallback registered on the connection pool.
      Specified by:
      [`removeConnectionAffinityCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### getStatistics

          public JDBCConnectionPoolStatistics getStatistics()

      Gets the statistics of the connection pool.
      Specified by:
      [`getStatistics`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The statistics of the connection pool.

    <!-- -->

    - #### getServiceName

          public java.lang.String getServiceName()

      Gets the service name set on this data source
      Specified by:
      [`getServiceName`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      service name on this data source

    <!-- -->

    - #### getConnectionProperties

          public java.util.Properties getConnectionProperties()

      Gets the connection properties that are set on this data source. Security sensitive values, like passwords, are omitted from the `Properties` object returned by this method.
      Specified by:
      [`getConnectionProperties`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Connection properties.

    <!-- -->

    - #### getConnectionProperty

          public java.lang.String getConnectionProperty(java.lang.String propertyName)

      Gets the specified connection property that is set on this data source. Security sensitive values, like passwords, are not returned by this method.
      Specified by:
      [`getConnectionProperty`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection property. Null if the property is not set, or is security sensitive.

    <!-- -->

    - #### setConnectionProperty

          public void setConnectionProperty(java.lang.String name,
                                            java.lang.String value)
                                     throws java.sql.SQLException

      Sets a connection property on the connection factory. This is used only for DataSource connection factories that also support connection properties; for example, the `oracle.jdbc.pool.OracleDataSource` in the Oracle JDBC driver.
      Specified by:
      [`setConnectionProperty`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `name` - The name of the connection property to be set on the connection factory class.

      `value` - The value of the connection property to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection property.

      See Also:
      `setConnectionFactoryProperties`

    <!-- -->

    - #### setConnectionProperties

          public void setConnectionProperties(java.util.Properties connectionProperties)
                                       throws java.sql.SQLException

      Sets the connection properties on the connection factory. This is used only for DataSource connection factories that also support connection properties; for example, the `oracle.jdbc.pool.OracleDataSource` in the Oracle JDBC driver.
      Specified by:
      [`setConnectionProperties`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connectionProperties` - Connection properties to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection properties.

      See Also:
      `setConnectionFactoryProperties`

    <!-- -->

    - #### getConnectionFactoryProperties

          public java.util.Properties getConnectionFactoryProperties()

      Gets the connection factory properties that are set on this data source.
      Specified by:
      [`getConnectionFactoryProperties`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Connection factory properties.

    <!-- -->

    - #### getConnectionFactoryProperty

          public java.lang.String getConnectionFactoryProperty(java.lang.String propertyName)

      Gets the specified connection factory property that are set on this data source.
      Specified by:
      [`getConnectionFactoryProperty`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection factory property. Null if the property is not set.

    <!-- -->

    - #### setConnectionFactoryProperty

          public void setConnectionFactoryProperty(java.lang.String name,
                                                   java.lang.String value)
                                            throws java.sql.SQLException

      Sets a connection factory property on the connection factory.
      For connection factories that implement `java.sql.Driver`, the connection factory property specified here will be assumed as a connection property.

      For DataSource connection factories, the property specified here will be assumed as a DataSource property.

      Specified by:
      [`setConnectionFactoryProperty`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `name` - The name of the connection factory property to be set on the connection factory class.

      `value` - The value of the connection factory property to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection factory property.

      `java.lang.IllegalArgumentException` - If the property name or value is invalid.

    <!-- -->

    - #### setConnectionFactoryProperties

          public void setConnectionFactoryProperties(java.util.Properties factoryProperties)
                                              throws java.sql.SQLException

      Sets the connection factory properties on the connection factory.
      For connection factories that implement `java.sql.Driver`, the connection factory properties specified here will be assumed as the connection properties.

      For DataSource connection factories, the properties specified here will be assumed as the DataSource properties.

      Specified by:
      [`setConnectionFactoryProperties`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `factoryProperties` - Connection factory properties to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection factory properties.

      `java.lang.IllegalArgumentException` - If factoryProperties is empty.

    <!-- -->

    - #### isSetOnceProperty

          public static boolean isSetOnceProperty(java.lang.String key)

      Authentication kays to enforce to be set up once per a single pool data source
      Parameters:
      `key` - to check

      Returns:
      true, if authentication key

    <!-- -->

    - #### toBasicType

          public static final java.lang.Object toBasicType(java.lang.String value,
                                                           java.lang.String type)

    <!-- -->

    - #### getReference

          public javax.naming.Reference getReference()
                                              throws javax.naming.NamingException

      Specified by:
      `getReference` in interface `javax.naming.Referenceable`

      Throws:
      `javax.naming.NamingException`

    <!-- -->

    - #### getObjectInstance

          public java.lang.Object getObjectInstance(java.lang.Object refObj,
                                                    javax.naming.Name name,
                                                    javax.naming.Context nameCtx,
                                                    java.util.Hashtable env)
                                             throws java.lang.Exception

      Specified by:
      `getObjectInstance` in interface `javax.naming.spi.ObjectFactory`

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isWrapperFor

          public boolean isWrapperFor(java.lang.Class<?> iface)
                               throws java.sql.SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      `isWrapperFor` in interface `java.sql.Wrapper`

      Parameters:
      `iface` - Requested interface.

      Returns:
      true If this implements the requested interface.

      Throws:
      `java.sql.SQLException` - If the argument is not an interface.

      Since:
      JDBC 4.0

    <!-- -->

    - #### unwrap

          public <T> T unwrap(java.lang.Class<T> iface)
                       throws java.sql.SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      `unwrap` in interface `java.sql.Wrapper`

      Parameters:
      `iface` - Requested interface.

      Returns:
      this If this implements the requested interface.

      Throws:
      `java.sql.SQLException` - If this does not implement the arg or the arg is not an interface.

      Since:
      JDBC 4.0

    <!-- -->

    - #### registerConnectionInitializationCallback

          public void registerConnectionInitializationCallback(ConnectionInitializationCallback cbk)
                                                        throws java.sql.SQLException

      Registers a connection initialization callback.
      Specified by:
      [`registerConnectionInitializationCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `cbk` - The `ConnectionInitializationCallback` object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the pool.

    <!-- -->

    - #### unregisterConnectionInitializationCallback

          public void unregisterConnectionInitializationCallback()
                                                          throws java.sql.SQLException

      Unregisters the connection initialization callback on this pool.
      Specified by:
      [`unregisterConnectionInitializationCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### getConnectionInitializationCallback

          public ConnectionInitializationCallback getConnectionInitializationCallback()

      Obtains the registered connection initialization callback, if any.
      Specified by:
      [`getConnectionInitializationCallback`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The registered `ConnectionInitializationCallback`, or null if there is no callback registered.

    <!-- -->

    - #### getConnectionLabelingHighCost

          public int getConnectionLabelingHighCost()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Obtains the cost value which identifies a connection as "high-cost" for connection labeling.
      Specified by:
      [`getConnectionLabelingHighCost`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The cost value that identifies a connection as "high-cost" for connection labeling.

      See Also:
      `setConnectionLabelingHighCost`

    <!-- -->

    - #### setConnectionLabelingHighCost

          public void setConnectionLabelingHighCost(int highCost)
                                             throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the cost value which identifies a connection as "high-cost" for connection labeling. Connection labeling uses the `cost(Properties, Properties)` method in ConnectionLabelingCallback to find a connection in the pool for a request. When this property is set, connections with a cost value equal to or greater than the property value are considered "high-cost" connections. The default value is Integer.MAX_VALUE.
      Specified by:
      [`setConnectionLabelingHighCost`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `highCost` - The cost value that identifies a connection as "high-cost" for connection labeling.

      Throws:
      `java.sql.SQLException` - If an exception occurs while setting the cost.

    <!-- -->

    - #### getConnectionRepurposeThreshold

          public int getConnectionRepurposeThreshold()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Gets the connection repurpose threshold for the pool. This property is used in cases when the connection pool is shared by multiple datasources connecting to the same database but using different services.Only when this threshold is reached the pool will try to repurpose connections between different services before trying to create new connections. This property is applicable only for multi-tenant databases.
      Specified by:
      [`getConnectionRepurposeThreshold`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      connection repurpose threshold property value currently set.

    <!-- -->

    - #### setConnectionRepurposeThreshold

          public void setConnectionRepurposeThreshold(int threshold)
                                               throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the connection repurpose threshold for the pool. This property is applicable only for multi-tenant databases.
      Specified by:
      [`setConnectionRepurposeThreshold`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `threshold` - connection repurpose threshold to set.

      Throws:
      `java.sql.SQLException` - If any exception occurs while setting the threshold.

      See Also:
      `getConnectionRepurposeThreshold`

    <!-- -->

    - #### getHighCostConnectionReuseThreshold

          public int getHighCostConnectionReuseThreshold()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Obtains the high-cost connection reuse threshold property value for connection labeling.
      Specified by:
      [`getHighCostConnectionReuseThreshold`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The high-cost connection reuse threshold property value currently set.

      See Also:
      `setConnectionLabelingHighCost`, `setHighCostConnectionReuseThreshold`

    <!-- -->

    - #### setHighCostConnectionReuseThreshold

          public void setHighCostConnectionReuseThreshold(int threshold)
                                                   throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Sets the high-cost connection reuse threshold for connection labeling. This property works together with the ConnectionLabelingHighCost property to determine when high-cost connections are reused for connection labeling. This property specifies a threshold of the number of total connections in the pool. If Connection Labeling finds all available connections are high-cost connections (i.e., the lowest cost value exceeds the ConnectionLabelingHighCost value), it checks this threshold to determine whether to reuse those connections. Only when this threshold is reached, Connection Labeling will try to reuse the high-cost connections in the pool to serve a labeled connection request. Otherwise, Connection Labeling picks a low-cost connection, a no-label connection available in the pool, or creates a brand-new physical connection to serve a labeled request. For example, if the property value is set to 10, Connection Labeling reuses high-cost connections when there are no low-cost connections available and the total connections reach 10. Note that any labeled connection with cost Integer.MAX_VALUE will not be reused. This is consistent with connection labeling behavior when this property and ConnectionLabelingHighCost are not set. A Connection Labeling callback must be registered at the same time for this property to take effect. The default value is 0, which is treated the same way as MinPoolSize.
      Specified by:
      [`setHighCostConnectionReuseThreshold`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `threshold` - The high-cost connection reuse threshold to set.

      Throws:
      `java.sql.SQLException` - If any exception occurs while setting the threshold.

    <!-- -->

    - #### getPdbRoles

          public java.util.Properties getPdbRoles()

      Gets the PDB roles specified for this datasource
      Specified by:
      [`getPdbRoles`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      roles key values pairs that correspond to the role names and password that are set for this datasource

      See Also:
      `setPdbRoles`

    <!-- -->

    - #### getSecondsToTrustIdleConnection

          public int getSecondsToTrustIdleConnection()

      Gets the seconds To Trust Idle Connection value. See property description in `setSecondsToTrustIdleConnection()`.
      Specified by:
      [`getSecondsToTrustIdleConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Seconds To Trust Idle Connection value.

    <!-- -->

    - #### setSecondsToTrustIdleConnection

          public void setSecondsToTrustIdleConnection(int secondsToTrustIdleConnection)
                                               throws java.sql.SQLException

      Sets the time in seconds to trust an idle connection to skip a validation test. It works in conjunction with `setValidateConnectionOnBorrow(boolean)`. When set to any positive value, a connection validation during the checkout is skipped if the connection was successfully used and returned to the pool within the time specified for secondsToTrustIdleConnection. Default value is set to 0 seconds which means that the feature is disabled.
      Specified by:
      [`setSecondsToTrustIdleConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `secondsToTrustIdleConnection` - The value of how long a connection can be trusted to skip connectionValidationOnBorrow

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createConnectionBuilder

          public UCPConnectionBuilder createConnectionBuilder()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Creates a new UCPConnectionBuilder instance.
      Specified by:
      [`createConnectionBuilder`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Connection builder that builds OracleConnection

      See Also:
      [`PoolDataSource.createConnectionBuilder()`](PoolDataSource.md)

    <!-- -->

    - #### getParentLogger

          public java.util.logging.Logger getParentLogger()
                                                   throws java.sql.SQLFeatureNotSupportedException

      Specified by:
      `getParentLogger` in interface `javax.sql.CommonDataSource`

      Returns:
      null

      Throws:
      `java.sql.SQLFeatureNotSupportedException`

      See Also:
      `CommonDataSource.getParentLogger()`

    <!-- -->

    - #### getQueryTimeout

          public int getQueryTimeout()

      Gets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.
      Specified by:
      [`getQueryTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The query timeout in seconds

    <!-- -->

    - #### setQueryTimeout

          public void setQueryTimeout(int queryTimeout)
                               throws java.sql.SQLException

      Sets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.
      Specified by:
      [`setQueryTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `queryTimeout` - in seconds

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxConnectionsPerShard

          public int getMaxConnectionsPerShard()

      Gets the currently configured max connections that can be created per shard in a sharded database configuration.
      Specified by:
      [`getMaxConnectionsPerShard`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      The configured max number of connections that can be created per shard.

    <!-- -->

    - #### setMaxConnectionsPerShard

          public void setMaxConnectionsPerShard(int maxConnectionsPerShard)
                                         throws java.sql.SQLException

      Sets the max number of connections that can be created per shard in a sharded database configuration. (Note: This configuration is not compatible with Sharded database configured with Oracle Golden gate)
      Specified by:
      [`setMaxConnectionsPerShard`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `maxConnectionsPerShard` - The max number of connections that can be created per shard

      Throws:
      `java.sql.SQLException` - if there is an any exception while setting this parameter

    <!-- -->

    - #### setShardingMode

          public void setShardingMode(boolean shardingMode)
                               throws java.sql.SQLException

      This API changes the mode of UCP when UCP is using a Sharded Database. By default UCP requires the caller to provide a sharding key for every connection request. When switching off the sharding mode, UCP behaves like a regular connection pool and all the sharding features are disabled so that a caller can request a connection without providing any sharding key.
      Specified by:
      [`setShardingMode`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `shardingMode` - Mode of UCP when using a Sharded Database.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getShardingMode

          public boolean getShardingMode()

      Returns the mode of UCP when UCP is using a Sharded Database. By default sharding mode is ON which means UCP requires the caller to provide a sharding key for every connection request.
      Specified by:
      [`getShardingMode`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Returns:
      Mode of UCP when using a Sharded Database.

    <!-- -->

    - #### setConnectionValidationTimeout

          public void setConnectionValidationTimeout(int connectionValidationTimeout)
                                              throws java.sql.SQLException

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      This property changes the connection validation timeout which is specified in seconds. Default is 15 seconds. This is the maximum time for connection validation operation. If not completed during this timeout, the connection is treated as invalid.
      Specified by:
      [`setConnectionValidationTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `connectionValidationTimeout` - timeout to validate connection

      Throws:
      `java.sql.SQLException` - if tiomeout is negative

      See Also:
      [`PoolDataSource.setConnectionValidationTimeout(int)`](PoolDataSource.md)

    <!-- -->

    - #### getConnectionValidationTimeout

          public int getConnectionValidationTimeout()

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Connection validation timeout getter
      Specified by:
      [`getConnectionValidationTimeout`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      See Also:
      [`PoolDataSource.getConnectionValidationTimeout()`](PoolDataSource.md)

    <!-- -->

    - #### setSSLContext

          public void setSSLContext(javax.net.ssl.SSLContext sslContext)

      Description copied from interface: [`PoolDataSource`](PoolDataSource.md)
      Specifies a `SSLContext` to use as a factory for SSLEngine objects that carry out the TLS protocol.
      The SSLContext must be initialized before setting it on PoolDataSource. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Specified by:
      [`setSSLContext`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `sslContext` - SSLContext instance to be used as an SSLEngine factory.

      See Also:
      [`PoolDataSource.setSSLContext(SSLContext)`](PoolDataSource.md)

    <!-- -->

    - #### getSSLContext

          protected javax.net.ssl.SSLContext getSSLContext()

      Returns SSL context associated with the datasource.
      Returns:

    <!-- -->

    - #### setTokenSupplier

          public final void setTokenSupplier(java.util.function.Supplier<? extends oracle.jdbc.AccessToken> tokenSupplier)
                                      throws java.sql.SQLException

      Sets a supplier function that generates an access token when creating a connection with this `DataSource`. The supplier function is invoked each time this `DataSource` creates a connection. Instances of `AccessToken` that are output by the supplier must represent a token type that is supported by Oracle Database for client authentication. The supplier must be thread safe.

      It is invalid to configure this `DataSource` with both a token supplier and with a user name or password. If invocations of `setUser(String)`, `setPassword(String)`, `setConnectionProperties(java.util.Properties)`, or `setConnectionProperty(String, String)` have configured this `DataSource` with a user name or password, and an invocation of this method has also configured a token supplier, then a `SQLException` indicating an invalid configuration is thrown when creating a connection with this datasource.

      Note that `AccessToken.createJsonWebTokenCache(Supplier)` can be called to create a thread safe `Supplier` that caches tokens from a user defined `Supplier`.

      Specified by:
      [`setTokenSupplier`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Parameters:
      `tokenSupplier` - Token supplying function. Not `null`.

      Throws:
      `java.lang.NullPointerException` - If the `tokenSupplier` is null.

      `java.sql.SQLException` - if unable to set property value

    <!-- -->

    - #### ilogFinest

          protected void ilogFinest(java.util.logging.Logger logger,
                                    java.lang.Class cls,
                                    java.lang.reflect.Executable method,
                                    java.lang.Object receiver,
                                    java.lang.String message)

      Helpers for writing into log and logWriter

    <!-- -->

    - #### ilogFine

          protected void ilogFine(java.util.logging.Logger logger,
                                  java.lang.Class cls,
                                  java.lang.reflect.Executable method,
                                  java.lang.Object receiver,
                                  java.lang.String message)

    <!-- -->

    - #### ilogWarning

          protected void ilogWarning(java.util.logging.Logger logger,
                                     java.lang.Class cls,
                                     java.lang.reflect.Executable method,
                                     java.lang.Object receiver,
                                     java.lang.String message)

    <!-- -->

    - #### ilogSevere

          protected void ilogSevere(java.util.logging.Logger logger,
                                    java.lang.Class cls,
                                    java.lang.reflect.Executable method,
                                    java.lang.Object receiver,
                                    java.lang.String message)

    <!-- -->

    - #### ilogThrowing

          protected void ilogThrowing(java.util.logging.Logger logger,
                                      java.lang.Class cls,
                                      java.lang.reflect.Executable method,
                                      java.lang.Object receiver,
                                      java.lang.Throwable throwable)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSourceFactory.md)
- [Next Class](PoolXADataSource.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2022, Oracle and/or its affiliates.
