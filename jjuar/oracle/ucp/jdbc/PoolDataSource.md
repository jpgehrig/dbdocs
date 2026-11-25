Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](LabelableConnection.md)
- [Next Class](PoolDataSourceFactory.md)

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

## Interface PoolDataSource

- All Superinterfaces:
  javax.sql.CommonDataSource, javax.sql.DataSource, java.sql.Wrapper

  <!-- -->

  All Known Subinterfaces:
  [PoolXADataSource](PoolXADataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [PoolDataSourceImpl](PoolDataSourceImpl.md), [PoolXADataSourceImpl](PoolXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface PoolDataSource
      extends javax.sql.DataSource

  A connection pool-aware data source interface. `PoolDataSource` uses Universal Connection Pool internally. See setters for pool properties and their default values.
  See Also:
  [`UniversalConnectionPool`](../UniversalConnectionPool.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                       |
    |---------------------------|---------------------------------------------|
    | `static java.lang.String` | `UCP_ABANDONED_CONNECTION_TIMEOUT`          |
    | `static java.lang.String` | `UCP_CONNECTION_AFFINITY_CALLBACK`          |
    | `static java.lang.String` | `UCP_CONNECTION_FACTORY_CLASS_NAME`         |
    | `static java.lang.String` | `UCP_CONNECTION_FACTORY_PROPERTIES`         |
    | `static java.lang.String` | `UCP_CONNECTION_HARVEST_MAX_COUNT`          |
    | `static java.lang.String` | `UCP_CONNECTION_HARVEST_TRIGGER_COUNT`      |
    | `static java.lang.String` | `UCP_CONNECTION_INITIALIZATION_CALLBACK`    |
    | `static java.lang.String` | `UCP_CONNECTION_LABELING_CALLBACK`          |
    | `static java.lang.String` | `UCP_CONNECTION_LABELING_HIGH_COST`         |
    | `static java.lang.String` | `UCP_CONNECTION_POOL_NAME`                  |
    | `static java.lang.String` | `UCP_CONNECTION_PROPERTIES`                 |
    | `static java.lang.String` | `UCP_CONNECTION_REPURPOSE_THRESHOLD`        |
    | `static java.lang.String` | `UCP_CONNECTION_VALIDATION_TIMEOUT`         |
    | `static java.lang.String` | `UCP_CONNECTION_WAIT_TIMEOUT`               |
    | `static java.lang.String` | `UCP_DATA_SOURCE_FROM_CONFIGURATION`        |
    | `static java.lang.String` | `UCP_DATA_SOURCE_NAME`                      |
    | `static java.lang.String` | `UCP_DATABASE_NAME`                         |
    | `static java.lang.String` | `UCP_DESCRIPTION`                           |
    | `static java.lang.String` | `UCP_FAST_CONNECTION_FAILOVER_ENABLED`      |
    | `static java.lang.String` | `UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD`  |
    | `static java.lang.String` | `UCP_INACTIVE_CONNECTION_TIMEOUT`           |
    | `static java.lang.String` | `UCP_INITIAL_POOL_SIZE`                     |
    | `static java.lang.String` | `UCP_LOGIN_TIMEOUT`                         |
    | `static java.lang.String` | `UCP_MAX_CONNECTION_REUSE_COUNT`            |
    | `static java.lang.String` | `UCP_MAX_CONNECTION_REUSE_TIME`             |
    | `static java.lang.String` | `UCP_MAX_CONNECTIONS_PER_SERVICE`           |
    | `static java.lang.String` | `UCP_MAX_CONNECTIONS_PER_SHARD`             |
    | `static java.lang.String` | `UCP_MAX_IDLE_TIME`                         |
    | `static java.lang.String` | `UCP_MAX_POOL_SIZE`                         |
    | `static java.lang.String` | `UCP_MAX_STATEMENTS`                        |
    | `static java.lang.String` | `UCP_MIN_POOL_SIZE`                         |
    | `static java.lang.String` | `UCP_NETWORK_PROTOCOL`                      |
    | `static java.lang.String` | `UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE`   |
    | `static java.lang.String` | `UCP_ONS_CONFIGURATION`                     |
    | `static java.lang.String` | `UCP_PASSWORD`                              |
    | `static java.lang.String` | `UCP_PDB_ROLES`                             |
    | `static java.lang.String` | `UCP_PORT_NUMBER`                           |
    | `static java.lang.String` | `UCP_PROPERTY_CYCLE`                        |
    | `static java.lang.String` | `UCP_ROLE_NAME`                             |
    | `static java.lang.String` | `UCP_SECONDS_TO_TRUST_IDLE_CONNECTION`      |
    | `static java.lang.String` | `UCP_SERVER_NAME`                           |
    | `static java.lang.String` | `UCP_SERVICE_NAME`                          |
    | `static java.lang.String` | `UCP_SHARDING_MODE`                         |
    | `static java.lang.String` | `UCP_SQL_FOR_VALIDATE_CONNECTION`           |
    | `static java.lang.String` | `UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT`       |
    | `static java.lang.String` | `UCP_TIMEOUT_CHECK_INTERVAL`                |
    | `static java.lang.String` | `UCP_URL`                                   |
    | `static java.lang.String` | `UCP_USER`                                  |
    | `static java.lang.String` | `UCP_VALIDATE_CONNECTION_ON_BORROW`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Default Methods](javascript:show(16);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                                                                           |
    |---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UCPConnectionBuilder`](UCPConnectionBuilder.md)                         | `createConnectionBuilder``()`<br>Creates a new UCPConnectionBuilder instance.                                                                                                                                    |
    | `default oracle.jdbc.OracleShardingKeyBuilder`                            | `createShardingKeyBuilder``()`<br>Creates a new OracleShardingKeyBuilder instance                                                                                                                                |
    | `int`                                                                     | `getAbandonedConnectionTimeout``()`<br>Gets the abandoned connection timeout value.                                                                                                                              |
    | `int`                                                                     | `getAvailableConnectionsCount``()`<br>Gets the number of available connections in the pool.                                                                                                                      |
    | `int`                                                                     | `getBorrowedConnectionsCount``()`<br>Gets the number of borrowed connections from the pool.                                                                                                                      |
    | `java.sql.Connection`                                                     | `getConnection``(java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                                                                                 |
    | `java.sql.Connection`                                                     | `getConnection``(java.lang.String username, java.lang.String password, java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                           |
    | `java.lang.String`                                                        | `getConnectionFactoryClassName``()`<br>Gets the Connection Factory class name.                                                                                                                                   |
    | `java.util.Properties`                                                    | `getConnectionFactoryProperties``()`<br>Gets the connection factory properties that are set on this data source.                                                                                                 |
    | `java.lang.String`                                                        | `getConnectionFactoryProperty``(java.lang.String propertyName)`<br>Gets the specified connection factory property that are set on this data source.                                                              |
    | `int`                                                                     | `getConnectionHarvestMaxCount``()`<br>Gets the maximum number of connections that may be harvested when the connection harvesting occurs.                                                                        |
    | `int`                                                                     | `getConnectionHarvestTriggerCount``()`<br>Gets the number of available connections below which the connection pool's connection harvesting will occur.                                                           |
    | [`ConnectionInitializationCallback`](ConnectionInitializationCallback.md) | `getConnectionInitializationCallback``()`<br>Obtains the registered connection initialization callback, if any.                                                                                                  |
    | `int`                                                                     | `getConnectionLabelingHighCost``()`<br>Obtains the cost value which identifies a connection as "high-cost" for connection labeling.                                                                              |
    | `java.lang.String`                                                        | `getConnectionPoolName``()`<br>Gets the connection pool name.                                                                                                                                                    |
    | `java.util.Properties`                                                    | `getConnectionProperties``()`<br>Gets the connection properties that are set on this data source.                                                                                                                |
    | `java.lang.String`                                                        | `getConnectionProperty``(java.lang.String propertyName)`<br>Gets the specified connection property that are set on this data source.                                                                             |
    | `int`                                                                     | `getConnectionRepurposeThreshold``()`<br>Gets the connection repurpose threshold for the pool.                                                                                                                   |
    | `int`                                                                     | `getConnectionValidationTimeout``()`<br>Connection validation timeout getter                                                                                                                                     |
    | `int`                                                                     | `getConnectionWaitTimeout``()`<br>Gets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                                 |
    | `java.lang.String`                                                        | `getDatabaseName``()`<br>Gets the database name.                                                                                                                                                                 |
    | `java.lang.String`                                                        | `getDataSourceName``()`<br>Gets the data source name.                                                                                                                                                            |
    | `java.lang.String`                                                        | `getDescription``()`<br>Gets the data source description.                                                                                                                                                        |
    | `boolean`                                                                 | `getFastConnectionFailoverEnabled``()`<br>Checks if Fast Connection Failover is enabled.                                                                                                                         |
    | `int`                                                                     | `getHighCostConnectionReuseThreshold``()`<br>Obtains the high-cost connection reuse threshold property value for connection labeling.                                                                            |
    | `int`                                                                     | `getInactiveConnectionTimeout``()`<br>Gets the inactive connection timeout.                                                                                                                                      |
    | `int`                                                                     | `getInitialPoolSize``()`<br>Gets the initial pool size.                                                                                                                                                          |
    | `int`                                                                     | `getMaxConnectionReuseCount``()`<br>Gets the maximum connection reuse count property value.                                                                                                                      |
    | `long`                                                                    | `getMaxConnectionReuseTime``()`<br>Gets the maximum connection reuse time property value.                                                                                                                        |
    | `int`                                                                     | `getMaxConnectionsPerService``()`<br>Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.                                                                      |
    | `int`                                                                     | `getMaxConnectionsPerShard``()`<br>Gets the currently configured max connections that can be created per shard from this connection pool.                                                                        |
    | `int`                                                                     | `getMaxIdleTime``()`<br>Gets the maximum idle time.                                                                                                                                                              |
    | `int`                                                                     | `getMaxPoolSize``()`<br>Gets the maximum number of connections that the connection pool will maintain.                                                                                                           |
    | `int`                                                                     | `getMaxStatements``()`<br>Gets the maximum number of statements that may be pooled or cached on a Connection.                                                                                                    |
    | `int`                                                                     | `getMinPoolSize``()`<br>Gets the minimum number of connections that the connection pool will maintain.                                                                                                           |
    | `java.lang.String`                                                        | `getNetworkProtocol``()`<br>Gets the data source network protocol.                                                                                                                                               |
    | `java.lang.String`                                                        | `getONSConfiguration``()`<br>Returns the ONS configuration string that is used for remote ONS subscription in the form specified in `setONSConfiguration(String)`.                                               |
    | `java.lang.String`                                                        | `getPassword``()`<br>Gets the Password for this data source.                                                                                                                                                     |
    | `java.util.Properties`                                                    | `getPdbRoles``()`<br>Gets the PDB roles specified for this datasource                                                                                                                                            |
    | `int`                                                                     | `getPortNumber``()`<br>Gets the database port number.                                                                                                                                                            |
    | `int`                                                                     | `getPropertyCycle``()`<br>Gets the property cycle in seconds.                                                                                                                                                    |
    | `int`                                                                     | `getQueryTimeout``()`<br>Gets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.                                                                       |
    | `java.lang.String`                                                        | `getRoleName``()`<br>Gets the data source role name.                                                                                                                                                             |
    | `int`                                                                     | `getSecondsToTrustIdleConnection``()`<br>Gets the seconds To Trust Idle Connection value.                                                                                                                        |
    | `java.lang.String`                                                        | `getServerName``()`<br>Gets the database server name.                                                                                                                                                            |
    | `java.lang.String`                                                        | `getServiceName``()`<br>Gets the service name set on this data source                                                                                                                                            |
    | `boolean`                                                                 | `getShardingMode``()`<br>Returns the mode of UCP when UCP is using a Sharded Database.                                                                                                                           |
    | `java.lang.String`                                                        | `getSQLForValidateConnection``()`<br>Gets the value of the `SQLForValidateConnection` property.                                                                                                                  |
    | [`JDBCConnectionPoolStatistics`](JDBCConnectionPoolStatistics.md)         | `getStatistics``()`<br>Gets the statistics of the connection pool.                                                                                                                                               |
    | `int`                                                                     | `getTimeoutCheckInterval``()`<br>Gets the timeout check interval (in seconds).                                                                                                                                   |
    | `int`                                                                     | `getTimeToLiveConnectionTimeout``()`<br>Gets the maximum time (in seconds) a connection may remain in-use.                                                                                                       |
    | `java.lang.String`                                                        | `getURL``()`<br>Gets the URL for this data source.                                                                                                                                                               |
    | `java.lang.String`                                                        | `getUser``()`<br>Gets the user name for this data source.                                                                                                                                                        |
    | `boolean`                                                                 | `getValidateConnectionOnBorrow``()`<br>Returns whether or not a connection being borrowed should first be validated.                                                                                             |
    | `void`                                                                    | `reconfigureDataSource``(java.util.Properties configuration)`<br>Reconfigures the data source.                                                                                                                   |
    | `void`                                                                    | `registerConnectionAffinityCallback``(`[`ConnectionAffinityCallback`](../ConnectionAffinityCallback.md)` cbk)`<br>Registers a connection affinity callback on the connection pool.                               |
    | `void`                                                                    | `registerConnectionInitializationCallback``(`[`ConnectionInitializationCallback`](ConnectionInitializationCallback.md)` cbk)`<br>Registers a connection initialization callback.                                 |
    | `void`                                                                    | `registerConnectionLabelingCallback``(`[`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)` cbk)`<br>Registers a connection labeling callback with the underlying connection pool.                  |
    | `void`                                                                    | `removeConnectionAffinityCallback``()`<br>Removes the `ConnectionAffinityCallback` object registered on the connection pool.                                                                                     |
    | `void`                                                                    | `removeConnectionLabelingCallback``()`<br>Removes the `ConnectionLabelingCallback` object registered with the underlying connection pool, if any.                                                                |
    | `void`                                                                    | `setAbandonedConnectionTimeout``(int abandonedConnectionTimeout)`<br>Sets the abandoned connection timeout.                                                                                                      |
    | `void`                                                                    | `setConnectionFactoryClassName``(java.lang.String factoryClassName)`<br>Sets the Connection Factory class name.                                                                                                  |
    | `void`                                                                    | `setConnectionFactoryProperties``(java.util.Properties factoryProperties)`<br>Sets the connection factory properties on the connection factory.                                                                  |
    | `void`                                                                    | `setConnectionFactoryProperty``(java.lang.String name, java.lang.String value)`<br>Sets a connection factory property on the connection factory.                                                                 |
    | `void`                                                                    | `setConnectionHarvestMaxCount``(int connectionHarvestMaxCount)`<br>Sets the maximum number of connections that may be harvested when the connection harvesting occurs.                                           |
    | `void`                                                                    | `setConnectionHarvestTriggerCount``(int connectionHarvestTriggerCount)`<br>Sets the number of available connections below which the connection pool's connection harvesting will occur.                          |
    | `void`                                                                    | `setConnectionLabelingHighCost``(int highCost)`<br>Sets the cost value which identifies a connection as "high-cost" for connection labeling.                                                                     |
    | `void`                                                                    | `setConnectionPoolName``(java.lang.String connectionpoolName)`<br>Sets the connection pool name.                                                                                                                 |
    | `void`                                                                    | `setConnectionProperties``(java.util.Properties connectionProperties)`<br>Sets the connection properties on the connection factory.                                                                              |
    | `void`                                                                    | `setConnectionProperty``(java.lang.String name, java.lang.String value)`<br>Sets a connection property on the connection factory.                                                                                |
    | `void`                                                                    | `setConnectionRepurposeThreshold``(int threshold)`<br>Sets the connection repurpose threshold for the pool.                                                                                                      |
    | `void`                                                                    | `setConnectionValidationTimeout``(int connectionValidationTimeout)`<br>This property changes the connection validation timeout which is specified in seconds.                                                    |
    | `void`                                                                    | `setConnectionWaitTimeout``(int waitTimeout)`<br>Sets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                  |
    | `void`                                                                    | `setDatabaseName``(java.lang.String databaseName)`<br>Sets the database name.                                                                                                                                    |
    | `void`                                                                    | `setDataSourceName``(java.lang.String dataSourceName)`<br>Sets the data source name.                                                                                                                             |
    | `void`                                                                    | `setDescription``(java.lang.String description)`<br>Sets the data source description.                                                                                                                            |
    | `void`                                                                    | `setFastConnectionFailoverEnabled``(boolean failoverEnabled)`<br>Enables Fast Connection Failover (FCF) for the connection pool accessed using this pool-enabled data source.                                    |
    | `void`                                                                    | `setHighCostConnectionReuseThreshold``(int threshold)`<br>Sets the high-cost connection reuse threshold for connection labeling.                                                                                 |
    | `void`                                                                    | `setInactiveConnectionTimeout``(int inactivityTimeout)`<br>Sets the inactive connection timeout.                                                                                                                 |
    | `void`                                                                    | `setInitialPoolSize``(int initialPoolSize)`<br>Sets the initial pool size.                                                                                                                                       |
    | `void`                                                                    | `setMaxConnectionReuseCount``(int maxConnectionReuseCount)`<br>Sets the maximum connection reuse count property.                                                                                                 |
    | `void`                                                                    | `setMaxConnectionReuseTime``(long maxConnectionReuseTime)`<br>Sets the maximum connection reuse time property.                                                                                                   |
    | `void`                                                                    | `setMaxConnectionsPerShard``(int maxConnectionsPerShard)`<br>Sets the max number of connections that can be created per shard from this connection pool.                                                         |
    | `void`                                                                    | `setMaxIdleTime``(int idleTime)`<br>Sets the maximum idle time for available connections in the pool.                                                                                                            |
    | `void`                                                                    | `setMaxPoolSize``(int maxPoolSize)`<br>Sets the maximum number of connections.                                                                                                                                   |
    | `void`                                                                    | `setMaxStatements``(int maxStatements)`<br>Sets the maximum number of statements that may be pooled or cached on a connection.                                                                                   |
    | `void`                                                                    | `setMinPoolSize``(int minPoolSize)`<br>Sets the minimum number of connections.                                                                                                                                   |
    | `void`                                                                    | `setNetworkProtocol``(java.lang.String networkProtocol)`<br>Sets the data source network protocol.                                                                                                               |
    | `void`                                                                    | `setONSConfiguration``(java.lang.String onsConfigStr)`<br>Sets the configuration string used for remote ONS subscription.                                                                                        |
    | `void`                                                                    | `setPassword``(java.lang.String pd)`<br>Sets the password with which connections have to be obtained.                                                                                                            |
    | `void`                                                                    | `setPortNumber``(int portNumber)`<br>Sets the database port number.                                                                                                                                              |
    | `void`                                                                    | `setPropertyCycle``(int propertyCycle)`<br>Sets the property cycle in seconds.                                                                                                                                   |
    | `void`                                                                    | `setQueryTimeout``(int queryTimeout)`<br>Sets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.                                                       |
    | `void`                                                                    | `setRoleName``(java.lang.String roleName)`<br>Sets the data source role name.                                                                                                                                    |
    | `void`                                                                    | `setSecondsToTrustIdleConnection``(int secondsToTrustIdleConnection)`<br>Sets the time in seconds to trust an idle connection to skip a validation test.                                                         |
    | `void`                                                                    | `setServerName``(java.lang.String serverName)`<br>Sets the database server name.                                                                                                                                 |
    | `void`                                                                    | `setShardingMode``(boolean shardingMode)`<br>This API changes the mode of UCP when UCP is using a Sharded Database.                                                                                              |
    | `void`                                                                    | `setSQLForValidateConnection``(java.lang.String SQLString)`<br>Sets the value of the `SQLForValidateConnection` property.                                                                                        |
    | `void`                                                                    | `setSSLContext``(javax.net.ssl.SSLContext sslContext)`<br>Specifies a `SSLContext` to use as a factory for SSLEngine objects that carry out the TLS protocol.                                                    |
    | `void`                                                                    | `setTimeoutCheckInterval``(int timeInterval)`<br>Sets the timeoutCheckInterval (in seconds).                                                                                                                     |
    | `void`                                                                    | `setTimeToLiveConnectionTimeout``(int timeToLiveConnectionTimeout)`<br>Sets the maximum time (in seconds) a connection may remain in-use.                                                                        |
    | `void`                                                                    | `setTokenSupplier``(java.util.function.Supplier<? extends oracle.jdbc.AccessToken> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`. |
    | `void`                                                                    | `setURL``(java.lang.String url)`<br>Sets the URL that the data source uses to obtain connections to the database.                                                                                                |
    | `void`                                                                    | `setUser``(java.lang.String userName)`<br>Sets the user name with which connections have to be obtained.                                                                                                         |
    | `void`                                                                    | `setValidateConnectionOnBorrow``(boolean validateConnectionOnBorrow)`<br>Sets whether or not a connection being borrowed should first be validated.                                                              |
    | `void`                                                                    | `unregisterConnectionInitializationCallback``()`<br>Unregisters the connection initialization callback on this pool.                                                                                             |

    - ### Methods inherited from interface javax.sql.DataSource

      `getConnection, getConnection`

    <!-- -->

    - ### Methods inherited from interface javax.sql.CommonDataSource

      `getLoginTimeout, getLogWriter, getParentLogger, setLoginTimeout, setLogWriter`

    <!-- -->

    - ### Methods inherited from interface java.sql.Wrapper

      `isWrapperFor, unwrap`

<!-- -->

- - ### Field Detail

    - #### UCP_USER

          static final java.lang.String UCP_USER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_URL

          static final java.lang.String UCP_URL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_PASSWORD

          static final java.lang.String UCP_PASSWORD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_SERVER_NAME

          static final java.lang.String UCP_SERVER_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_PORT_NUMBER

          static final java.lang.String UCP_PORT_NUMBER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_DATABASE_NAME

          static final java.lang.String UCP_DATABASE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_DATA_SOURCE_NAME

          static final java.lang.String UCP_DATA_SOURCE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_DESCRIPTION

          static final java.lang.String UCP_DESCRIPTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_NETWORK_PROTOCOL

          static final java.lang.String UCP_NETWORK_PROTOCOL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_ROLE_NAME

          static final java.lang.String UCP_ROLE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_FACTORY_CLASS_NAME

          static final java.lang.String UCP_CONNECTION_FACTORY_CLASS_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_PROPERTIES

          static final java.lang.String UCP_CONNECTION_PROPERTIES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_FACTORY_PROPERTIES

          static final java.lang.String UCP_CONNECTION_FACTORY_PROPERTIES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_VALIDATE_CONNECTION_ON_BORROW

          static final java.lang.String UCP_VALIDATE_CONNECTION_ON_BORROW

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_SQL_FOR_VALIDATE_CONNECTION

          static final java.lang.String UCP_SQL_FOR_VALIDATE_CONNECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_POOL_NAME

          static final java.lang.String UCP_CONNECTION_POOL_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_INITIAL_POOL_SIZE

          static final java.lang.String UCP_INITIAL_POOL_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MIN_POOL_SIZE

          static final java.lang.String UCP_MIN_POOL_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_POOL_SIZE

          static final java.lang.String UCP_MAX_POOL_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE

          static final java.lang.String UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_ABANDONED_CONNECTION_TIMEOUT

          static final java.lang.String UCP_ABANDONED_CONNECTION_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT

          static final java.lang.String UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_INACTIVE_CONNECTION_TIMEOUT

          static final java.lang.String UCP_INACTIVE_CONNECTION_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_IDLE_TIME

          static final java.lang.String UCP_MAX_IDLE_TIME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_TIMEOUT_CHECK_INTERVAL

          static final java.lang.String UCP_TIMEOUT_CHECK_INTERVAL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_PROPERTY_CYCLE

          static final java.lang.String UCP_PROPERTY_CYCLE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_STATEMENTS

          static final java.lang.String UCP_MAX_STATEMENTS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_WAIT_TIMEOUT

          static final java.lang.String UCP_CONNECTION_WAIT_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_CONNECTION_REUSE_TIME

          static final java.lang.String UCP_MAX_CONNECTION_REUSE_TIME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_CONNECTION_REUSE_COUNT

          static final java.lang.String UCP_MAX_CONNECTION_REUSE_COUNT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_HARVEST_TRIGGER_COUNT

          static final java.lang.String UCP_CONNECTION_HARVEST_TRIGGER_COUNT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_HARVEST_MAX_COUNT

          static final java.lang.String UCP_CONNECTION_HARVEST_MAX_COUNT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_FAST_CONNECTION_FAILOVER_ENABLED

          static final java.lang.String UCP_FAST_CONNECTION_FAILOVER_ENABLED

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_ONS_CONFIGURATION

          static final java.lang.String UCP_ONS_CONFIGURATION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_SECONDS_TO_TRUST_IDLE_CONNECTION

          static final java.lang.String UCP_SECONDS_TO_TRUST_IDLE_CONNECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_CONNECTIONS_PER_SERVICE

          static final java.lang.String UCP_MAX_CONNECTIONS_PER_SERVICE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_LOGIN_TIMEOUT

          static final java.lang.String UCP_LOGIN_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_SERVICE_NAME

          static final java.lang.String UCP_SERVICE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_PDB_ROLES

          static final java.lang.String UCP_PDB_ROLES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_AFFINITY_CALLBACK

          static final java.lang.String UCP_CONNECTION_AFFINITY_CALLBACK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_INITIALIZATION_CALLBACK

          static final java.lang.String UCP_CONNECTION_INITIALIZATION_CALLBACK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_LABELING_CALLBACK

          static final java.lang.String UCP_CONNECTION_LABELING_CALLBACK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_LABELING_HIGH_COST

          static final java.lang.String UCP_CONNECTION_LABELING_HIGH_COST

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_REPURPOSE_THRESHOLD

          static final java.lang.String UCP_CONNECTION_REPURPOSE_THRESHOLD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD

          static final java.lang.String UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_DATA_SOURCE_FROM_CONFIGURATION

          static final java.lang.String UCP_DATA_SOURCE_FROM_CONFIGURATION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_MAX_CONNECTIONS_PER_SHARD

          static final java.lang.String UCP_MAX_CONNECTIONS_PER_SHARD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_SHARDING_MODE

          static final java.lang.String UCP_SHARDING_MODE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UCP_CONNECTION_VALIDATION_TIMEOUT

          static final java.lang.String UCP_CONNECTION_VALIDATION_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getInitialPoolSize

          int getInitialPoolSize()

      Gets the initial pool size.
      Returns:
      the initial pool size.

    <!-- -->

    - #### setInitialPoolSize

          void setInitialPoolSize(int initialPoolSize)
                           throws java.sql.SQLException

      Sets the initial pool size. This is the number of connections that will be created and placed in the pool when the pool is started.
      The range of valid values is 0 to `Integer.MAX_VALUE`. It is illegal to set this to a value greater than the maximum pool size. Defaults to 0.

      Parameters:
      `initialPoolSize` - the initial pool size.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMinPoolSize

          int getMinPoolSize()

      Gets the minimum number of connections that the connection pool will maintain.
      Returns:
      The minimum number of connections.

    <!-- -->

    - #### setMinPoolSize

          void setMinPoolSize(int minPoolSize)
                       throws java.sql.SQLException

      Sets the minimum number of connections. If the number of available connections + the number of connections in use \< the minimum then the connection is returned to the pool. Otherwise, the connection is closed.
      The range of valid values is 0 to `Integer.MAX_VALUE`. It is illegal to set this to a value greater than the maximum pool size. Defaults to 0.

      Parameters:
      `minPoolSize` - The minimum number of connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxPoolSize

          int getMaxPoolSize()

      Gets the maximum number of connections that the connection pool will maintain.
      Returns:
      The maximum number of connections.

    <!-- -->

    - #### setMaxPoolSize

          void setMaxPoolSize(int maxPoolSize)
                       throws java.sql.SQLException

      Sets the maximum number of connections. The maximum number of connections includes the number of connections that are in use as well as the number of available connections.
      The range of valid values is 1 to `Integer.MAX_VALUE`. Defaults to `Integer.MAX_VALUE`.

      Parameters:
      `maxPoolSize` - The maximum number of connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getInactiveConnectionTimeout

          int getInactiveConnectionTimeout()

      Gets the inactive connection timeout.
      Returns:
      The inactivity timeout.

    <!-- -->

    - #### setInactiveConnectionTimeout

          void setInactiveConnectionTimeout(int inactivityTimeout)
                                     throws java.sql.SQLException

      Sets the inactive connection timeout. This timeout determines how long an available connection remains in the connection pool before it is removed from the pool.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables inactive connection timeout processing.

      Parameters:
      `inactivityTimeout` - The inactive connection timeout in seconds.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getAbandonedConnectionTimeout

          int getAbandonedConnectionTimeout()

      Gets the abandoned connection timeout value.
      Returns:
      The abandoned connection timeout.

    <!-- -->

    - #### setAbandonedConnectionTimeout

          void setAbandonedConnectionTimeout(int abandonedConnectionTimeout)
                                      throws java.sql.SQLException

      Sets the abandoned connection timeout. This timeout determines how long a borrowed connection can remain unused before it is considered as abandoned and reclaimed by the connection pool.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables abandoned connection timeout.

      Parameters:
      `abandonedConnectionTimeout` - The value of how long a connection has not been used before it is abandoned (in seconds).

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionWaitTimeout

          int getConnectionWaitTimeout()

      Gets the amount of time to wait (in seconds) for a used connection to be released by a client. This only applies when the maximum number of connections has been borrowed from the connection pool. When a client tries to borrow a connection from the pool and all connections are in use, the connection pool waits for a connection to be released back to the pool.
      Returns:
      The connection wait timeout.

    <!-- -->

    - #### setConnectionWaitTimeout

          void setConnectionWaitTimeout(int waitTimeout)
                                 throws java.sql.SQLException

      Sets the amount of time to wait (in seconds) for a used connection to be released by a client.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 3.

      Setting the value to 0 disables connection wait timeout processing.

      Parameters:
      `waitTimeout` - The amount of time to wait.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getTimeToLiveConnectionTimeout

          int getTimeToLiveConnectionTimeout()

      Gets the maximum time (in seconds) a connection may remain in-use. When this timeout expires, the used connection is unconditionally returned to the connection pool. A value of 0 means that the feature is not enabled.
      Returns:
      The maximum time (in seconds) a used connection may be active.

    <!-- -->

    - #### setTimeToLiveConnectionTimeout

          void setTimeToLiveConnectionTimeout(int timeToLiveConnectionTimeout)
                                       throws java.sql.SQLException

      Sets the maximum time (in seconds) a connection may remain in-use.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Setting the value to 0 disables time-to-live connection timeout processing.

      Parameters:
      `timeToLiveConnectionTimeout` - The maximum time (in seconds) a used connection may be active.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setTimeoutCheckInterval

          void setTimeoutCheckInterval(int timeInterval)
                                throws java.sql.SQLException

      Sets the timeoutCheckInterval (in seconds). This interval specifies how often the timeout properties such as InactiveConnectionTimeout, AbandonedConnectionTimeout, and TimeToLiveConnectionTimeout are enforced.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 30.

      Setting the value to 0 disables all connection timeout processing.

      Parameters:
      `timeInterval` - The timeInterval (in seconds) between checks to enforce the timeout properties.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getTimeoutCheckInterval

          int getTimeoutCheckInterval()

      Gets the timeout check interval (in seconds).
      Returns:
      timeInterval The `timeInterval` (in seconds) between checks to enforce the timeout properties.

    <!-- -->

    - #### setFastConnectionFailoverEnabled

          void setFastConnectionFailoverEnabled(boolean failoverEnabled)
                                         throws java.sql.SQLException

      Enables Fast Connection Failover (FCF) for the connection pool accessed using this pool-enabled data source. By default, FCF is disabled.
      Parameters:
      `failoverEnabled` - `true` if Fast Connection Failover is enabled; `false` if not.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getFastConnectionFailoverEnabled

          boolean getFastConnectionFailoverEnabled()

      Checks if Fast Connection Failover is enabled.
      Returns:
      `true` if Fast Connection Failover is enabled; `false` if not.

    <!-- -->

    - #### getConnectionFactoryClassName

          java.lang.String getConnectionFactoryClassName()

      Gets the Connection Factory class name.
      Returns:
      Name of the connection factory class specified.

    <!-- -->

    - #### setConnectionFactoryClassName

          void setConnectionFactoryClassName(java.lang.String factoryClassName)
                                      throws java.sql.SQLException

      Sets the Connection Factory class name. This is the connection factory used by the connection pool to create physical connections. Must be set for `PoolDataSource` to operate.
      Parameters:
      `factoryClassName` - Connection factory class name for obtaining physical connections.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setMaxStatements

          void setMaxStatements(int maxStatements)
                         throws java.sql.SQLException

      Sets the maximum number of statements that may be pooled or cached on a connection. This is used to enable the statement pooling.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Parameters:
      `maxStatements` - maximum number of statements to be pooled.

      Throws:
      `java.sql.SQLException` - Exception occurred during the process of setting maximum statements that may be pooled on a connection.

    <!-- -->

    - #### getMaxStatements

          int getMaxStatements()

      Gets the maximum number of statements that may be pooled or cached on a Connection.
      Returns:
      m_maxStatements maximum number of statements that may be pooled or cached on a Connection.

    <!-- -->

    - #### setMaxIdleTime

          void setMaxIdleTime(int idleTime)
                       throws java.sql.SQLException

      Sets the maximum idle time for available connections in the pool. This has the same effect as setting the inactive connection timeout.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 0.

      Parameters:
      `idleTime` - Maximum idle time in seconds.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxIdleTime

          int getMaxIdleTime()

      Gets the maximum idle time.
      Returns:
      The maximum idle time.

    <!-- -->

    - #### setPropertyCycle

          void setPropertyCycle(int propertyCycle)
                         throws java.sql.SQLException

      Sets the property cycle in seconds. This is the time interval between checks to enforce connection pool timeout properties. This has the same effect as setting `timeoutCheckInterval`.
      The range of valid values is 0 to `Integer.MAX_VALUE`. Defaults to 30.

      Parameters:
      `propertyCycle` - Time interval in seconds to enforce connection pool timeout properties.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPropertyCycle

          int getPropertyCycle()

      Gets the property cycle in seconds.
      Returns:
      The PropertyCycle value.

    <!-- -->

    - #### setConnectionPoolName

          void setConnectionPoolName(java.lang.String connectionpoolName)
                              throws java.sql.SQLException

      Sets the connection pool name. This property allows the user to specify a String value to name a connection pool instance.
      If not set, the pool name will be automatically generated.

      Parameters:
      `connectionpoolName` - Name of the connection pool.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionPoolName

          java.lang.String getConnectionPoolName()

      Gets the connection pool name.
      Returns:
      The connection pool name.

    <!-- -->

    - #### setURL

          void setURL(java.lang.String url)
               throws java.sql.SQLException

      Sets the URL that the data source uses to obtain connections to the database.
      Parameters:
      `url` - URL to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getURL

          java.lang.String getURL()

      Gets the URL for this data source.
      Returns:
      URL for this data source.

    <!-- -->

    - #### setUser

          void setUser(java.lang.String userName)
                throws java.sql.SQLException

      Sets the user name with which connections have to be obtained.
      Parameters:
      `userName` - Username to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getUser

          java.lang.String getUser()

      Gets the user name for this data source.
      Returns:
      userName for this data source.

    <!-- -->

    - #### setPassword

          void setPassword(java.lang.String pd)
                    throws java.sql.SQLException

      Sets the password with which connections have to be obtained.
      Parameters:
      `pd` - Password to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPassword

          java.lang.String getPassword()

      Gets the Password for this data source.
      Returns:
      password for this data source.

    <!-- -->

    - #### setServerName

          void setServerName(java.lang.String serverName)
                      throws java.sql.SQLException

      Sets the database server name.
      Parameters:
      `serverName` - Database server name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getServerName

          java.lang.String getServerName()

      Gets the database server name.
      Returns:
      Database server name.

    <!-- -->

    - #### setPortNumber

          void setPortNumber(int portNumber)
                      throws java.sql.SQLException

      Sets the database port number.
      Parameters:
      `portNumber` - Database port number to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPortNumber

          int getPortNumber()

      Gets the database port number.
      Returns:
      Database port number.

    <!-- -->

    - #### setDatabaseName

          void setDatabaseName(java.lang.String databaseName)
                        throws java.sql.SQLException

      Sets the database name.
      Parameters:
      `databaseName` - Database name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDatabaseName

          java.lang.String getDatabaseName()

      Gets the database name.
      Returns:
      Database name.

    <!-- -->

    - #### setDataSourceName

          void setDataSourceName(java.lang.String dataSourceName)
                          throws java.sql.SQLException

      Sets the data source name.
      Parameters:
      `dataSourceName` - data source name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDataSourceName

          java.lang.String getDataSourceName()

      Gets the data source name.
      Returns:
      data source name.

    <!-- -->

    - #### setDescription

          void setDescription(java.lang.String description)
                       throws java.sql.SQLException

      Sets the data source description.
      Parameters:
      `description` - data source description to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDescription

          java.lang.String getDescription()

      Gets the data source description.
      Returns:
      data source description.

    <!-- -->

    - #### setNetworkProtocol

          void setNetworkProtocol(java.lang.String networkProtocol)
                           throws java.sql.SQLException

      Sets the data source network protocol.
      Parameters:
      `networkProtocol` - data source network protocol to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkProtocol

          java.lang.String getNetworkProtocol()

      Gets the data source network protocol.
      Returns:
      data source network protocol.

    <!-- -->

    - #### setRoleName

          void setRoleName(java.lang.String roleName)
                    throws java.sql.SQLException

      Sets the data source role name.
      Parameters:
      `roleName` - data source role name to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getRoleName

          java.lang.String getRoleName()

      Gets the data source role name.
      Returns:
      data source role name.

    <!-- -->

    - #### setValidateConnectionOnBorrow

          void setValidateConnectionOnBorrow(boolean validateConnectionOnBorrow)
                                      throws java.sql.SQLException

      Sets whether or not a connection being borrowed should first be validated. Defaults to `false`.
      Parameters:
      `validateConnectionOnBorrow` - Whether or not a connection being borrowed should first be validated.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getValidateConnectionOnBorrow

          boolean getValidateConnectionOnBorrow()

      Returns whether or not a connection being borrowed should first be validated.
      Returns:
      Whether or not a connection being borrowed should first be validated.

    <!-- -->

    - #### setSQLForValidateConnection

          void setSQLForValidateConnection(java.lang.String SQLString)
                                    throws java.sql.SQLException

      Sets the value of the `SQLForValidateConnection` property. This is a SQL command used in conjunction with the `ValidateConnectionOnBorrow` property. The SQL specified should be applicable to the backend database and the JDBC driver configured. Defaults to `null`.
      Parameters:
      `SQLString` - The SQL string used for connection validation.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getSQLForValidateConnection

          java.lang.String getSQLForValidateConnection()

      Gets the value of the `SQLForValidateConnection` property.
      Returns:
      The SQLForValidateConnection property value.

    <!-- -->

    - #### getConnectionHarvestTriggerCount

          int getConnectionHarvestTriggerCount()

      Gets the number of available connections below which the connection pool's connection harvesting will occur. For example, if the value is set to 10, then connection harvesting will occur when the number of available connections drops to 10.
      Returns:
      The number of available connections below which the connection pool's connection harvesting will occur.

    <!-- -->

    - #### setConnectionHarvestTriggerCount

          void setConnectionHarvestTriggerCount(int connectionHarvestTriggerCount)
                                         throws java.sql.SQLException

      Sets the number of available connections below which the connection pool's connection harvesting will occur.
      The range of valid values is 0 to `maxPoolSize`. Defaults to `Integer.MAX_VALUE`.

      Setting the value to `Integer.MAX_VALUE` disables connection harvesting.

      Parameters:
      `connectionHarvestTriggerCount` - The number of available connections below which the connection pool's connection harvesting will occur.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionHarvestMaxCount

          int getConnectionHarvestMaxCount()

      Gets the maximum number of connections that may be harvested when the connection harvesting occurs. Note that it is possible that the number of connections that are harvested may be anywhere from 0 to the `connectionHarvestMaxCount`.
      Returns:
      The maximum number of connections that may be harvested when the connection harvesting occurs.

    <!-- -->

    - #### setConnectionHarvestMaxCount

          void setConnectionHarvestMaxCount(int connectionHarvestMaxCount)
                                     throws java.sql.SQLException

      Sets the maximum number of connections that may be harvested when the connection harvesting occurs.
      The range of valid values is 1 to `maxPoolSize`. Defaults to 1.

      Parameters:
      `connectionHarvestMaxCount` - the maximum number of connections that may be harvested when the connection harvesting occurs.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getAvailableConnectionsCount

          int getAvailableConnectionsCount()
                                    throws java.sql.SQLException

      Gets the number of available connections in the pool.
      Returns:
      `AvailableConnectionsCount`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBorrowedConnectionsCount

          int getBorrowedConnectionsCount()
                                   throws java.sql.SQLException

      Gets the number of borrowed connections from the pool.
      Returns:
      `BorrowedConnectionsCount`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getONSConfiguration

          java.lang.String getONSConfiguration()
                                        throws java.sql.SQLException

      Returns the ONS configuration string that is used for remote ONS subscription in the form specified in `setONSConfiguration(String)`. This is used by Fast Connection Failover and Runtime Connection Load Balancing.
      Returns:
      The ONS configuration string used for remote ONS subscription.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setONSConfiguration

          void setONSConfiguration(java.lang.String onsConfigStr)
                            throws java.sql.SQLException

      Sets the configuration string used for remote ONS subscription. The parameter string closely resembles the content of the ONS configuration file (`ons.config`). The string contains a list of `name=value` pairs separated by a newline character (\n). The name can be one of `nodes`, `walletfile`, or `walletpassword`. The parameter string should at least specify the ONS configuration `nodes` attribute as a list of `host:port` pairs separated by a comma. SSL would be used when the `walletfile` attribute is specified as an Oracle wallet file.
      An example ONS configuration string:

             "nodes=host1:4200,host2:4200\nwalletfile=wfile\nwalletpassword=wpwd"


      This is used primarily by Fast Connection Failover and Runtime Load Balancing.

      Parameters:
      `onsConfigStr` - The configuration string for remote ONS subscription.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnection

          java.sql.Connection getConnection(java.util.Properties labels)
                                     throws java.sql.SQLException

      Attempts to obtain a database connection with the requested connection labels.
      Parameters:
      `labels` - The requested connection labels.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          java.sql.Connection getConnection(java.lang.String username,
                                            java.lang.String password,
                                            java.util.Properties labels)
                                     throws java.sql.SQLException

      Attempts to obtain a database connection with the requested connection labels.
      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      `labels` - The requested connection labels.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### registerConnectionLabelingCallback

          void registerConnectionLabelingCallback(ConnectionLabelingCallback cbk)
                                           throws java.sql.SQLException

      Registers a connection labeling callback with the underlying connection pool.
      Parameters:
      `cbk` - The `ConnectionLabelingCallback` object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the pool.

    <!-- -->

    - #### removeConnectionLabelingCallback

          void removeConnectionLabelingCallback()
                                         throws java.sql.SQLException

      Removes the `ConnectionLabelingCallback` object registered with the underlying connection pool, if any.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### registerConnectionAffinityCallback

          void registerConnectionAffinityCallback(ConnectionAffinityCallback cbk)
                                           throws java.sql.SQLException

      Registers a connection affinity callback on the connection pool.
      Parameters:
      `cbk` - Affinity Callback object that must be registered.

      Throws:
      `java.sql.SQLException` - If callback registration fails.

    <!-- -->

    - #### removeConnectionAffinityCallback

          void removeConnectionAffinityCallback()
                                         throws java.sql.SQLException

      Removes the `ConnectionAffinityCallback` object registered on the connection pool.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### getConnectionProperties

          java.util.Properties getConnectionProperties()

      Gets the connection properties that are set on this data source.
      Returns:
      Connection properties.

    <!-- -->

    - #### getConnectionProperty

          java.lang.String getConnectionProperty(java.lang.String propertyName)

      Gets the specified connection property that are set on this data source.
      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection property. Null if the property is not set.

    <!-- -->

    - #### setConnectionProperty

          void setConnectionProperty(java.lang.String name,
                                     java.lang.String value)
                              throws java.sql.SQLException

      Sets a connection property on the connection factory. This is used only for DataSource connection factories that also support connection properties; for example, the `oracle.jdbc.pool.OracleDataSource` in the Oracle JDBC driver.
      Parameters:
      `name` - The name of the connection property to be set on the connection factory class.

      `value` - The value of the connection property to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection property.

      See Also:
      `setConnectionFactoryProperties`

    <!-- -->

    - #### setConnectionProperties

          void setConnectionProperties(java.util.Properties connectionProperties)
                                throws java.sql.SQLException

      Sets the connection properties on the connection factory. This is used only for DataSource connection factories that also support connection properties; for example, the `oracle.jdbc.pool.OracleDataSource` in the Oracle JDBC driver.
      Parameters:
      `connectionProperties` - Connection properties to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection properties.

      See Also:
      `setConnectionFactoryProperties`

    <!-- -->

    - #### getConnectionFactoryProperties

          java.util.Properties getConnectionFactoryProperties()

      Gets the connection factory properties that are set on this data source.
      Returns:
      Connection factory properties.

    <!-- -->

    - #### getConnectionFactoryProperty

          java.lang.String getConnectionFactoryProperty(java.lang.String propertyName)

      Gets the specified connection factory property that are set on this data source.
      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection factory property. Null if the property is not set.

    <!-- -->

    - #### setConnectionFactoryProperty

          void setConnectionFactoryProperty(java.lang.String name,
                                            java.lang.String value)
                                     throws java.sql.SQLException

      Sets a connection factory property on the connection factory.
      For connection factories that implement `java.sql.Driver`, the connection factory property specified here will be assumed as a connection property.

      For DataSource connection factories, the property specified here will be assumed as a DataSource property.

      Parameters:
      `name` - The name of the connection factory property to be set on the connection factory class.

      `value` - The value of the connection factory property to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection factory property.

      `java.lang.IllegalArgumentException` - If the property name or value is invalid.

    <!-- -->

    - #### setConnectionFactoryProperties

          void setConnectionFactoryProperties(java.util.Properties factoryProperties)
                                       throws java.sql.SQLException

      Sets the connection factory properties on the connection factory.
      For connection factories that implement `java.sql.Driver`, the connection factory properties specified here will be assumed as the connection properties.

      For DataSource connection factories, the properties specified here will be assumed as the DataSource properties.

      Parameters:
      `factoryProperties` - Connection factory properties to be set on the connection factory class.

      Throws:
      `java.sql.SQLException` - If any exception occurred while setting the connection factory properties.

      `java.lang.IllegalArgumentException` - If factoryProperties is empty.

    <!-- -->

    - #### getMaxConnectionReuseTime

          long getMaxConnectionReuseTime()

      Gets the maximum connection reuse time property value. See property description in `setMaxConnectionReuseTime()`.
      Returns:
      Maximum connection reuse time (in seconds).

    <!-- -->

    - #### setMaxConnectionReuseTime

          void setMaxConnectionReuseTime(long maxConnectionReuseTime)
                                  throws java.sql.SQLException

      Sets the maximum connection reuse time property. This property specifies the maximum time any connection can potentially be reused after which the pool removes and closes a connection. The value is specified in seconds and must be greater than 0. For example, if the specified value is 3600 seconds, then when a connection is in existence for more than 3600 seconds, the connection is closed and removed from the pool. Connections are closed gracefully after they are returned to the pool and the specified property value has been exceeded. Default is 0, which means this feature is not enabled.
      Parameters:
      `maxConnectionReuseTime` - Maximum connection reuse time (in seconds).

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxConnectionReuseCount

          int getMaxConnectionReuseCount()

      Gets the maximum connection reuse count property value. See property description in `setMaxConnectionReuseCount()`.
      Returns:
      Maximum connection reuse count.

    <!-- -->

    - #### setMaxConnectionReuseCount

          void setMaxConnectionReuseCount(int maxConnectionReuseCount)
                                   throws java.sql.SQLException

      Sets the maximum connection reuse count property. This property specifies the maximum number of times any connection can be reused after which the pool removes and closes a connection. The value must be greater than 0 for this feature to be enabled. For example, if the specified value is 100, then when a connection is reused or borrowed 100 times from the pool, it is closed and removed from the pool. Connections are closed gracefully after they are returned to the pool and the property value has been exceeded. Default is 0, which means this feature is not enabled.
      Parameters:
      `maxConnectionReuseCount` - Maximum connection reuse count.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getStatistics

          JDBCConnectionPoolStatistics getStatistics()

      Gets the statistics of the connection pool.
      Returns:
      The statistics of the connection pool.

    <!-- -->

    - #### registerConnectionInitializationCallback

          void registerConnectionInitializationCallback(ConnectionInitializationCallback cbk)
                                                 throws java.sql.SQLException

      Registers a connection initialization callback.
      Parameters:
      `cbk` - The `ConnectionInitializationCallback` object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the pool.

    <!-- -->

    - #### unregisterConnectionInitializationCallback

          void unregisterConnectionInitializationCallback()
                                                   throws java.sql.SQLException

      Unregisters the connection initialization callback on this pool.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

    <!-- -->

    - #### getConnectionInitializationCallback

          ConnectionInitializationCallback getConnectionInitializationCallback()

      Obtains the registered connection initialization callback, if any.
      Returns:
      The registered `ConnectionInitializationCallback`, or null if there is no callback registered.

    <!-- -->

    - #### getConnectionLabelingHighCost

          int getConnectionLabelingHighCost()

      Obtains the cost value which identifies a connection as "high-cost" for connection labeling.
      Returns:
      The cost value that identifies a connection as "high-cost" for connection labeling.

      See Also:
      `setConnectionLabelingHighCost`

    <!-- -->

    - #### setConnectionLabelingHighCost

          void setConnectionLabelingHighCost(int highCost)
                                      throws java.sql.SQLException

      Sets the cost value which identifies a connection as "high-cost" for connection labeling. Connection labeling uses the `cost(Properties, Properties)` method in ConnectionLabelingCallback to find a connection in the pool for a request. When this property is set, connections with a cost value equal to or greater than the property value are considered "high-cost" connections. The default value is Integer.MAX_VALUE.
      Parameters:
      `highCost` - The cost value that identifies a connection as "high-cost" for connection labeling.

      Throws:
      `java.sql.SQLException` - If an exception occurs while setting the cost.

    <!-- -->

    - #### getHighCostConnectionReuseThreshold

          int getHighCostConnectionReuseThreshold()

      Obtains the high-cost connection reuse threshold property value for connection labeling.
      Returns:
      The high-cost connection reuse threshold property value currently set.

      See Also:
      `setConnectionLabelingHighCost`, `setHighCostConnectionReuseThreshold`

    <!-- -->

    - #### setHighCostConnectionReuseThreshold

          void setHighCostConnectionReuseThreshold(int threshold)
                                            throws java.sql.SQLException

      Sets the high-cost connection reuse threshold for connection labeling. This property works together with the ConnectionLabelingHighCost property to determine when high-cost connections are reused for connection labeling. This property specifies a threshold of the number of total connections in the pool. If Connection Labeling finds all available connections are high-cost connections (i.e., the lowest cost value exceeds the ConnectionLabelingHighCost value), it checks this threshold to determine whether to reuse those connections. Only when this threshold is reached, Connection Labeling will try to reuse the high-cost connections in the pool to serve a labeled connection request. Otherwise, Connection Labeling picks a low-cost connection, a no-label connection available in the pool, or creates a brand-new physical connection to serve a labeled request. For example, if the property value is set to 10, Connection Labeling reuses high-cost connections when there are no low-cost connections available and the total connections reach 10. Note that any labeled connection with cost Integer.MAX_VALUE will not be reused. This is consistent with connection labeling behavior when this property and ConnectionLabelingHighCost are not set. A Connection Labeling callback must be registered at the same time for this property to take effect. The default value is 0, which is treated the same way as MinPoolSize.
      Parameters:
      `threshold` - The high-cost connection reuse threshold to set.

      Throws:
      `java.sql.SQLException` - If any exception occurs while setting the threshold.

    <!-- -->

    - #### createConnectionBuilder

          UCPConnectionBuilder createConnectionBuilder()

      Creates a new UCPConnectionBuilder instance.
      Type Parameters:
      `S` - Connection type for this ConnectionBuilder

      `B` - Builder type to use

      Returns:
      The OracleConnectionBuilder instance that was created

    <!-- -->

    - #### createShardingKeyBuilder

          default oracle.jdbc.OracleShardingKeyBuilder createShardingKeyBuilder()

      Creates a new OracleShardingKeyBuilder instance
      Returns:
      The OracleShardingKeyBuilder instance that was created

    <!-- -->

    - #### getConnectionRepurposeThreshold

          int getConnectionRepurposeThreshold()

      Gets the connection repurpose threshold for the pool. This property is used in cases when the connection pool is shared by multiple datasources connecting to the same database but using different services.Only when this threshold is reached the pool will try to repurpose connections between different services before trying to create new connections. This property is applicable only for multi-tenant databases.
      Returns:
      connection repurpose threshold property value currently set.

    <!-- -->

    - #### setConnectionRepurposeThreshold

          void setConnectionRepurposeThreshold(int threshold)
                                        throws java.sql.SQLException

      Sets the connection repurpose threshold for the pool. This property is applicable only for multi-tenant databases.
      Parameters:
      `threshold` - connection repurpose threshold to set.

      Throws:
      `java.sql.SQLException` - If any exception occurs while setting the threshold.

      See Also:
      `getConnectionRepurposeThreshold`

    <!-- -->

    - #### getPdbRoles

          java.util.Properties getPdbRoles()

      Gets the PDB roles specified for this datasource
      Returns:
      roles key values pairs that correspond to the role names and password that are set for this datasource

      See Also:
      `setPdbRoles`

    <!-- -->

    - #### getServiceName

          java.lang.String getServiceName()

      Gets the service name set on this data source
      Returns:
      service name on this data source

    <!-- -->

    - #### getSecondsToTrustIdleConnection

          int getSecondsToTrustIdleConnection()

      Gets the seconds To Trust Idle Connection value.
      Returns:
      The seconds To Trust Idle Connection.

    <!-- -->

    - #### setSecondsToTrustIdleConnection

          void setSecondsToTrustIdleConnection(int secondsToTrustIdleConnection)
                                        throws java.sql.SQLException

      Sets the time in seconds to trust an idle connection to skip a validation test. It works in conjunction with `setValidateConnectionOnBorrow(boolean)`. When set to any positive value, a connection validation during the checkout is skipped if the connection was successfully used and returned to the pool within the time specified for secondsToTrustIdleConnection. Default value is set to 0 seconds which means that the feature is disabled.
      Parameters:
      `secondsToTrustIdleConnection` - The value of how long a connection can be trusted to skip connectionValidationOnBorrow

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### reconfigureDataSource

          void reconfigureDataSource(java.util.Properties configuration)
                              throws java.sql.SQLException

      Reconfigures the data source. This API can be only used to modify existing data source properties. To add a new data source to a running pool instance, use PoolDataSourceFactory's getPoolDataSource(Properties configuration) API instead. Only the following data source properties can be modified using this API: `user`, `password`, `description`, `serviceName`, `pdbRoles`.
      Parameters:
      `configuration` - the configuration input

      Throws:
      `java.sql.SQLException` - If an error occurs while configuring the data source.

    <!-- -->

    - #### getMaxConnectionsPerService

          int getMaxConnectionsPerService()

      Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.
      Returns:
      The maximum number of connections that can be obtained to a particular service.

    <!-- -->

    - #### getQueryTimeout

          int getQueryTimeout()

      Gets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.
      Returns:
      The query timeout in seconds

    <!-- -->

    - #### setQueryTimeout

          void setQueryTimeout(int queryTimeout)
                        throws java.sql.SQLException

      Sets the number of seconds the driver will wait for a Statement object to execute to the given number of seconds.
      Parameters:
      `queryTimeout` - in seconds

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxConnectionsPerShard

          int getMaxConnectionsPerShard()

      Gets the currently configured max connections that can be created per shard from this connection pool.
      Returns:
      The configured max number of connections that can be created per shard.

    <!-- -->

    - #### setMaxConnectionsPerShard

          void setMaxConnectionsPerShard(int maxConnectionsPerShard)
                                  throws java.sql.SQLException

      Sets the max number of connections that can be created per shard from this connection pool. (Note: This property is applicable to Sharded databases only. It should not be used when the Sharded database is configured with Oracle Golden Gate)
      Parameters:
      `maxConnectionsPerShard` - The max number of connections that can be created per shard

      Throws:
      `java.sql.SQLException` - if there is an any exception while setting this parameter

    <!-- -->

    - #### setShardingMode

          void setShardingMode(boolean shardingMode)
                        throws java.sql.SQLException

      This API changes the mode of UCP when UCP is using a Sharded Database. By default UCP requires the caller to provide a sharding key for every connection request. When switching off the sharding mode, UCP behaves like a regular connection pool and all the sharding features are disabled so that a caller can request a connection without providing any sharding key.
      Parameters:
      `shardingMode` - Mode of UCP when using a Sharded Database.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getShardingMode

          boolean getShardingMode()

      Returns the mode of UCP when UCP is using a Sharded Database. By default sharding mode is ON which means UCP requires the caller to provide a sharding key for every connection request.
      Returns:
      Mode of UCP when using a Sharded Database.

    <!-- -->

    - #### setConnectionValidationTimeout

          void setConnectionValidationTimeout(int connectionValidationTimeout)
                                       throws java.sql.SQLException

      This property changes the connection validation timeout which is specified in seconds. Default is 15 seconds. This is the maximum time for connection validation operation. If not completed during this timeout, the connection is treated as invalid.
      Parameters:
      `connectionValidationTimeout` - timeout to validate connection

      Throws:
      `java.sql.SQLException` - if tiomeout is negative

    <!-- -->

    - #### getConnectionValidationTimeout

          int getConnectionValidationTimeout()

      Connection validation timeout getter

    <!-- -->

    - #### setSSLContext

          void setSSLContext(javax.net.ssl.SSLContext sslContext)

      Specifies a `SSLContext` to use as a factory for SSLEngine objects that carry out the TLS protocol.
      The SSLContext must be initialized before setting it on PoolDataSource. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Parameters:
      `sslContext` - SSLContext instance to be used as an SSLEngine factory.

    <!-- -->

    - #### setTokenSupplier

          void setTokenSupplier(java.util.function.Supplier<? extends oracle.jdbc.AccessToken> tokenSupplier)
                         throws java.sql.SQLException

      Sets a supplier function that generates an access token when creating a connection with this `DataSource`. The supplier function is invoked each time this `DataSource` creates a connection. Instances of `AccessToken` that are output by the supplier must represent a token type that is supported by Oracle Database for client authentication. The supplier must be thread safe.

      It is invalid to configure this `DataSource` with both a token supplier and with a user name or password. If invocations of `setUser(String)`, `setPassword(String)`, `setConnectionProperties(java.util.Properties)`, or `setConnectionProperty(String, String)` have configured this `DataSource` with a user name or password, and an invocation of this method has also configured a token supplier, then a `SQLException` indicating an invalid configuration is thrown when creating a connection with this datasource.

      Note that `AccessToken.createJsonWebTokenCache(Supplier)` can be called to create a thread safe `Supplier` that caches tokens from a user defined `Supplier`.

      Parameters:
      `tokenSupplier` - Token supplying function. Not `null`.

      Throws:
      `java.lang.NullPointerException` - If the `tokenSupplier` is null.

      `java.sql.SQLException` - if unable to set property value

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](LabelableConnection.md)
- [Next Class](PoolDataSourceFactory.md)

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
