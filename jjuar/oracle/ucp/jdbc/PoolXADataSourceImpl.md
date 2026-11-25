Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolXADataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolXADataSource.md)
- [Next Class](UCPConnectionBuilder.md)

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

## Class PoolXADataSourceImpl

- java.lang.Object

- - [oracle.ucp.jdbc.PoolDataSourceImpl](PoolDataSourceImpl.md)

  - - oracle.ucp.jdbc.PoolXADataSourceImpl

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.sql.Wrapper, javax.naming.Referenceable, javax.naming.spi.ObjectFactory, javax.sql.CommonDataSource, javax.sql.DataSource, javax.sql.XADataSource, [PoolDataSource](PoolDataSource.md), [PoolXADataSource](PoolXADataSource.md), [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)

  ------------------------------------------------------------------------



      public class PoolXADataSourceImpl
      extends PoolDataSourceImpl
      implements PoolXADataSource, java.io.Serializable, javax.naming.Referenceable, javax.naming.spi.ObjectFactory, UniversalConnectionPoolAdapter

  A connection pool-aware data source. This DataSource uses the Universal Connection Pool to get an XAconneciton, creating a proxy to that connection, and returning the proxy to the client. When the client calls close on the XAConnection proxy, the underlying physical connection is usually returned to the pool. Also see the proxy factory.
  Besides other data source properties, applications must set the connection factory class name. The connection factory class is a class that implements javax.sql.XADataSource and does not implement its own connection pooling. The connection factory's getXAConnection(...) methods should return a physical XAConnection to the database. For example, "oracle.jdbc.xa.client.OracleXADataSource" is a valid connection factory class name.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.ucp.jdbc.[PoolDataSourceImpl](PoolDataSourceImpl.md)

      [`m_connectionFactory`](PoolDataSourceImpl.md)`, `[`m_connectionFactoryClassName`](PoolDataSourceImpl.md)`, `[`m_cp`](PoolDataSourceImpl.md)`, `[`SECRET_STORE_CONNECT`](PoolDataSourceImpl.md)`, `[`SECRET_STORE_DEFAULT_PASSWORD`](PoolDataSourceImpl.md)`, `[`SECRET_STORE_DEFAULT_USERNAME`](PoolDataSourceImpl.md)`, `[`SECRET_STORE_PASSWORD`](PoolDataSourceImpl.md)`, `[`SECRET_STORE_USERNAME`](PoolDataSourceImpl.md)

    <!-- -->

    - ### Fields inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`UCP_ABANDONED_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_AFFINITY_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_CLASS_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_MAX_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_TRIGGER_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_INITIALIZATION_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_HIGH_COST`](PoolDataSource.md)`, `[`UCP_CONNECTION_POOL_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_REPURPOSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_CONNECTION_VALIDATION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_WAIT_TIMEOUT`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_FROM_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_NAME`](PoolDataSource.md)`, `[`UCP_DATABASE_NAME`](PoolDataSource.md)`, `[`UCP_DESCRIPTION`](PoolDataSource.md)`, `[`UCP_FAST_CONNECTION_FAILOVER_ENABLED`](PoolDataSource.md)`, `[`UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_INACTIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_INITIAL_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_LOGIN_TIMEOUT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_COUNT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SERVICE`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SHARD`](PoolDataSource.md)`, `[`UCP_MAX_IDLE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_MAX_STATEMENTS`](PoolDataSource.md)`, `[`UCP_MIN_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_NETWORK_PROTOCOL`](PoolDataSource.md)`, `[`UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE`](PoolDataSource.md)`, `[`UCP_ONS_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_PASSWORD`](PoolDataSource.md)`, `[`UCP_PDB_ROLES`](PoolDataSource.md)`, `[`UCP_PORT_NUMBER`](PoolDataSource.md)`, `[`UCP_PROPERTY_CYCLE`](PoolDataSource.md)`, `[`UCP_ROLE_NAME`](PoolDataSource.md)`, `[`UCP_SECONDS_TO_TRUST_IDLE_CONNECTION`](PoolDataSource.md)`, `[`UCP_SERVER_NAME`](PoolDataSource.md)`, `[`UCP_SERVICE_NAME`](PoolDataSource.md)`, `[`UCP_SHARDING_MODE`](PoolDataSource.md)`, `[`UCP_SQL_FOR_VALIDATE_CONNECTION`](PoolDataSource.md)`, `[`UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_TIMEOUT_CHECK_INTERVAL`](PoolDataSource.md)`, `[`UCP_URL`](PoolDataSource.md)`, `[`UCP_USER`](PoolDataSource.md)`, `[`UCP_VALIDATE_CONNECTION_ON_BORROW`](PoolDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `PoolXADataSourceImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                              |
    |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                      | `createPoolWithDefaultProperties``()`                                                                                                                                                                                                               |
    | [`UCPXAConnectionBuilder`](UCPXAConnectionBuilder.md) | `createXAConnectionBuilder``()`<br>Creates a new XAConnectionBuilder instance.                                                                                                                                                                      |
    | `java.sql.Connection`                                 | `getConnection``()`<br>Attempts to obtain a database connection.                                                                                                                                                                                    |
    | `java.sql.Connection`                                 | `getConnection``(java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                                                                                                                    |
    | `java.sql.Connection`                                 | `getConnection``(java.lang.String username, java.lang.String password)`<br>Attempts to obtain a database connection.                                                                                                                                |
    | `java.sql.Connection`                                 | `getConnection``(java.lang.String username, java.lang.String password, java.util.Properties labels)`<br>Attempts to obtain a database connection with the requested connection labels.                                                              |
    | `javax.sql.XAConnection`                              | `getXAConnection``()`<br>Obtains an XAConnection from the embedded Universal Connection Pool instance.                                                                                                                                              |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.util.Properties labels)`<br>Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given connection labels.                                                                                |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.lang.String user, java.lang.String password)`<br>Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given user name and password.                                                      |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.lang.String username, java.lang.String password, java.util.Properties labels)`<br>Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given user name, password, and connection labels. |

    - ### Methods inherited from class oracle.ucp.jdbc.[PoolDataSourceImpl](PoolDataSourceImpl.md)

      [`createConnectionBuilder`](PoolDataSourceImpl.md)`, `[`createUniversalConnectionPool`](PoolDataSourceImpl.md)`, `[`createUniversalConnectionPoolMBean`](PoolDataSourceImpl.md)`, `[`getAbandonedConnectionTimeout`](PoolDataSourceImpl.md)`, `[`getAvailableConnectionsCount`](PoolDataSourceImpl.md)`, `[`getBorrowedConnectionsCount`](PoolDataSourceImpl.md)`, `[`getConnectionFactoryClassName`](PoolDataSourceImpl.md)`, `[`getConnectionFactoryProperties`](PoolDataSourceImpl.md)`, `[`getConnectionFactoryProperty`](PoolDataSourceImpl.md)`, `[`getConnectionHarvestMaxCount`](PoolDataSourceImpl.md)`, `[`getConnectionHarvestTriggerCount`](PoolDataSourceImpl.md)`, `[`getConnectionInitializationCallback`](PoolDataSourceImpl.md)`, `[`getConnectionLabelingHighCost`](PoolDataSourceImpl.md)`, `[`getConnectionPoolName`](PoolDataSourceImpl.md)`, `[`getConnectionProperties`](PoolDataSourceImpl.md)`, `[`getConnectionProperty`](PoolDataSourceImpl.md)`, `[`getConnectionRepurposeThreshold`](PoolDataSourceImpl.md)`, `[`getConnectionValidationTimeout`](PoolDataSourceImpl.md)`, `[`getConnectionWaitTimeout`](PoolDataSourceImpl.md)`, `[`getDatabaseName`](PoolDataSourceImpl.md)`, `[`getDataSourceName`](PoolDataSourceImpl.md)`, `[`getDescription`](PoolDataSourceImpl.md)`, `[`getFastConnectionFailoverEnabled`](PoolDataSourceImpl.md)`, `[`getHighCostConnectionReuseThreshold`](PoolDataSourceImpl.md)`, `[`getInactiveConnectionTimeout`](PoolDataSourceImpl.md)`, `[`getInitialPoolSize`](PoolDataSourceImpl.md)`, `[`getLoginTimeout`](PoolDataSourceImpl.md)`, `[`getLogWriter`](PoolDataSourceImpl.md)`, `[`getMaxConnectionReuseCount`](PoolDataSourceImpl.md)`, `[`getMaxConnectionReuseTime`](PoolDataSourceImpl.md)`, `[`getMaxConnectionsPerService`](PoolDataSourceImpl.md)`, `[`getMaxConnectionsPerShard`](PoolDataSourceImpl.md)`, `[`getMaxIdleTime`](PoolDataSourceImpl.md)`, `[`getMaxPoolSize`](PoolDataSourceImpl.md)`, `[`getMaxStatements`](PoolDataSourceImpl.md)`, `[`getMinPoolSize`](PoolDataSourceImpl.md)`, `[`getNetworkProtocol`](PoolDataSourceImpl.md)`, `[`getObjectInstance`](PoolDataSourceImpl.md)`, `[`getONSConfiguration`](PoolDataSourceImpl.md)`, `[`getParentLogger`](PoolDataSourceImpl.md)`, `[`getPassword`](PoolDataSourceImpl.md)`, `[`getPdbRoles`](PoolDataSourceImpl.md)`, `[`getPortNumber`](PoolDataSourceImpl.md)`, `[`getPropertyCycle`](PoolDataSourceImpl.md)`, `[`getQueryTimeout`](PoolDataSourceImpl.md)`, `[`getReference`](PoolDataSourceImpl.md)`, `[`getRoleName`](PoolDataSourceImpl.md)`, `[`getSecondsToTrustIdleConnection`](PoolDataSourceImpl.md)`, `[`getServerName`](PoolDataSourceImpl.md)`, `[`getServiceName`](PoolDataSourceImpl.md)`, `[`getShardingMode`](PoolDataSourceImpl.md)`, `[`getSQLForValidateConnection`](PoolDataSourceImpl.md)`, `[`getSSLContext`](PoolDataSourceImpl.md)`, `[`getStatistics`](PoolDataSourceImpl.md)`, `[`getTimeoutCheckInterval`](PoolDataSourceImpl.md)`, `[`getTimeToLiveConnectionTimeout`](PoolDataSourceImpl.md)`, `[`getURL`](PoolDataSourceImpl.md)`, `[`getUser`](PoolDataSourceImpl.md)`, `[`getValidateConnectionOnBorrow`](PoolDataSourceImpl.md)`, `[`ilogFine`](PoolDataSourceImpl.md)`, `[`ilogFinest`](PoolDataSourceImpl.md)`, `[`ilogSevere`](PoolDataSourceImpl.md)`, `[`ilogThrowing`](PoolDataSourceImpl.md)`, `[`ilogWarning`](PoolDataSourceImpl.md)`, `[`isSetOnceProperty`](PoolDataSourceImpl.md)`, `[`isWrapperFor`](PoolDataSourceImpl.md)`, `[`reconfigureDataSource`](PoolDataSourceImpl.md)`, `[`registerConnectionAffinityCallback`](PoolDataSourceImpl.md)`, `[`registerConnectionInitializationCallback`](PoolDataSourceImpl.md)`, `[`registerConnectionLabelingCallback`](PoolDataSourceImpl.md)`, `[`removeConnectionAffinityCallback`](PoolDataSourceImpl.md)`, `[`removeConnectionLabelingCallback`](PoolDataSourceImpl.md)`, `[`setAbandonedConnectionTimeout`](PoolDataSourceImpl.md)`, `[`setConnectionFactoryClassName`](PoolDataSourceImpl.md)`, `[`setConnectionFactoryProperties`](PoolDataSourceImpl.md)`, `[`setConnectionFactoryProperty`](PoolDataSourceImpl.md)`, `[`setConnectionHarvestMaxCount`](PoolDataSourceImpl.md)`, `[`setConnectionHarvestTriggerCount`](PoolDataSourceImpl.md)`, `[`setConnectionLabelingHighCost`](PoolDataSourceImpl.md)`, `[`setConnectionPoolName`](PoolDataSourceImpl.md)`, `[`setConnectionProperties`](PoolDataSourceImpl.md)`, `[`setConnectionProperty`](PoolDataSourceImpl.md)`, `[`setConnectionRepurposeThreshold`](PoolDataSourceImpl.md)`, `[`setConnectionValidationTimeout`](PoolDataSourceImpl.md)`, `[`setConnectionWaitTimeout`](PoolDataSourceImpl.md)`, `[`setDatabaseName`](PoolDataSourceImpl.md)`, `[`setDataSourceName`](PoolDataSourceImpl.md)`, `[`setDescription`](PoolDataSourceImpl.md)`, `[`setFastConnectionFailoverEnabled`](PoolDataSourceImpl.md)`, `[`setHighCostConnectionReuseThreshold`](PoolDataSourceImpl.md)`, `[`setInactiveConnectionTimeout`](PoolDataSourceImpl.md)`, `[`setInitialPoolSize`](PoolDataSourceImpl.md)`, `[`setLoginTimeout`](PoolDataSourceImpl.md)`, `[`setLogWriter`](PoolDataSourceImpl.md)`, `[`setMaxConnectionReuseCount`](PoolDataSourceImpl.md)`, `[`setMaxConnectionReuseTime`](PoolDataSourceImpl.md)`, `[`setMaxConnectionsPerShard`](PoolDataSourceImpl.md)`, `[`setMaxIdleTime`](PoolDataSourceImpl.md)`, `[`setMaxPoolSize`](PoolDataSourceImpl.md)`, `[`setMaxStatements`](PoolDataSourceImpl.md)`, `[`setMinPoolSize`](PoolDataSourceImpl.md)`, `[`setNetworkProtocol`](PoolDataSourceImpl.md)`, `[`setONSConfiguration`](PoolDataSourceImpl.md)`, `[`setPassword`](PoolDataSourceImpl.md)`, `[`setPortNumber`](PoolDataSourceImpl.md)`, `[`setPropertyCycle`](PoolDataSourceImpl.md)`, `[`setQueryTimeout`](PoolDataSourceImpl.md)`, `[`setRoleName`](PoolDataSourceImpl.md)`, `[`setSecondsToTrustIdleConnection`](PoolDataSourceImpl.md)`, `[`setServerName`](PoolDataSourceImpl.md)`, `[`setShardingMode`](PoolDataSourceImpl.md)`, `[`setSQLForValidateConnection`](PoolDataSourceImpl.md)`, `[`setSSLContext`](PoolDataSourceImpl.md)`, `[`setTimeoutCheckInterval`](PoolDataSourceImpl.md)`, `[`setTimeToLiveConnectionTimeout`](PoolDataSourceImpl.md)`, `[`setTokenSupplier`](PoolDataSourceImpl.md)`, `[`setURL`](PoolDataSourceImpl.md)`, `[`setUser`](PoolDataSourceImpl.md)`, `[`setValidateConnectionOnBorrow`](PoolDataSourceImpl.md)`, `[`startPool`](PoolDataSourceImpl.md)`, `[`toBasicType`](PoolDataSourceImpl.md)`, `[`unregisterConnectionInitializationCallback`](PoolDataSourceImpl.md)`, `[`unwrap`](PoolDataSourceImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`createConnectionBuilder`](PoolDataSource.md)`, `[`createShardingKeyBuilder`](PoolDataSource.md)`, `[`getAbandonedConnectionTimeout`](PoolDataSource.md)`, `[`getAvailableConnectionsCount`](PoolDataSource.md)`, `[`getBorrowedConnectionsCount`](PoolDataSource.md)`, `[`getConnectionFactoryClassName`](PoolDataSource.md)`, `[`getConnectionFactoryProperties`](PoolDataSource.md)`, `[`getConnectionFactoryProperty`](PoolDataSource.md)`, `[`getConnectionHarvestMaxCount`](PoolDataSource.md)`, `[`getConnectionHarvestTriggerCount`](PoolDataSource.md)`, `[`getConnectionInitializationCallback`](PoolDataSource.md)`, `[`getConnectionLabelingHighCost`](PoolDataSource.md)`, `[`getConnectionPoolName`](PoolDataSource.md)`, `[`getConnectionProperties`](PoolDataSource.md)`, `[`getConnectionProperty`](PoolDataSource.md)`, `[`getConnectionRepurposeThreshold`](PoolDataSource.md)`, `[`getConnectionValidationTimeout`](PoolDataSource.md)`, `[`getConnectionWaitTimeout`](PoolDataSource.md)`, `[`getDatabaseName`](PoolDataSource.md)`, `[`getDataSourceName`](PoolDataSource.md)`, `[`getDescription`](PoolDataSource.md)`, `[`getFastConnectionFailoverEnabled`](PoolDataSource.md)`, `[`getHighCostConnectionReuseThreshold`](PoolDataSource.md)`, `[`getInactiveConnectionTimeout`](PoolDataSource.md)`, `[`getInitialPoolSize`](PoolDataSource.md)`, `[`getMaxConnectionReuseCount`](PoolDataSource.md)`, `[`getMaxConnectionReuseTime`](PoolDataSource.md)`, `[`getMaxConnectionsPerService`](PoolDataSource.md)`, `[`getMaxConnectionsPerShard`](PoolDataSource.md)`, `[`getMaxIdleTime`](PoolDataSource.md)`, `[`getMaxPoolSize`](PoolDataSource.md)`, `[`getMaxStatements`](PoolDataSource.md)`, `[`getMinPoolSize`](PoolDataSource.md)`, `[`getNetworkProtocol`](PoolDataSource.md)`, `[`getONSConfiguration`](PoolDataSource.md)`, `[`getPassword`](PoolDataSource.md)`, `[`getPdbRoles`](PoolDataSource.md)`, `[`getPortNumber`](PoolDataSource.md)`, `[`getPropertyCycle`](PoolDataSource.md)`, `[`getQueryTimeout`](PoolDataSource.md)`, `[`getRoleName`](PoolDataSource.md)`, `[`getSecondsToTrustIdleConnection`](PoolDataSource.md)`, `[`getServerName`](PoolDataSource.md)`, `[`getServiceName`](PoolDataSource.md)`, `[`getShardingMode`](PoolDataSource.md)`, `[`getSQLForValidateConnection`](PoolDataSource.md)`, `[`getStatistics`](PoolDataSource.md)`, `[`getTimeoutCheckInterval`](PoolDataSource.md)`, `[`getTimeToLiveConnectionTimeout`](PoolDataSource.md)`, `[`getURL`](PoolDataSource.md)`, `[`getUser`](PoolDataSource.md)`, `[`getValidateConnectionOnBorrow`](PoolDataSource.md)`, `[`reconfigureDataSource`](PoolDataSource.md)`, `[`registerConnectionAffinityCallback`](PoolDataSource.md)`, `[`registerConnectionInitializationCallback`](PoolDataSource.md)`, `[`registerConnectionLabelingCallback`](PoolDataSource.md)`, `[`removeConnectionAffinityCallback`](PoolDataSource.md)`, `[`removeConnectionLabelingCallback`](PoolDataSource.md)`, `[`setAbandonedConnectionTimeout`](PoolDataSource.md)`, `[`setConnectionFactoryClassName`](PoolDataSource.md)`, `[`setConnectionFactoryProperties`](PoolDataSource.md)`, `[`setConnectionFactoryProperty`](PoolDataSource.md)`, `[`setConnectionHarvestMaxCount`](PoolDataSource.md)`, `[`setConnectionHarvestTriggerCount`](PoolDataSource.md)`, `[`setConnectionLabelingHighCost`](PoolDataSource.md)`, `[`setConnectionPoolName`](PoolDataSource.md)`, `[`setConnectionProperties`](PoolDataSource.md)`, `[`setConnectionProperty`](PoolDataSource.md)`, `[`setConnectionRepurposeThreshold`](PoolDataSource.md)`, `[`setConnectionValidationTimeout`](PoolDataSource.md)`, `[`setConnectionWaitTimeout`](PoolDataSource.md)`, `[`setDatabaseName`](PoolDataSource.md)`, `[`setDataSourceName`](PoolDataSource.md)`, `[`setDescription`](PoolDataSource.md)`, `[`setFastConnectionFailoverEnabled`](PoolDataSource.md)`, `[`setHighCostConnectionReuseThreshold`](PoolDataSource.md)`, `[`setInactiveConnectionTimeout`](PoolDataSource.md)`, `[`setInitialPoolSize`](PoolDataSource.md)`, `[`setMaxConnectionReuseCount`](PoolDataSource.md)`, `[`setMaxConnectionReuseTime`](PoolDataSource.md)`, `[`setMaxConnectionsPerShard`](PoolDataSource.md)`, `[`setMaxIdleTime`](PoolDataSource.md)`, `[`setMaxPoolSize`](PoolDataSource.md)`, `[`setMaxStatements`](PoolDataSource.md)`, `[`setMinPoolSize`](PoolDataSource.md)`, `[`setNetworkProtocol`](PoolDataSource.md)`, `[`setONSConfiguration`](PoolDataSource.md)`, `[`setPassword`](PoolDataSource.md)`, `[`setPortNumber`](PoolDataSource.md)`, `[`setPropertyCycle`](PoolDataSource.md)`, `[`setQueryTimeout`](PoolDataSource.md)`, `[`setRoleName`](PoolDataSource.md)`, `[`setSecondsToTrustIdleConnection`](PoolDataSource.md)`, `[`setServerName`](PoolDataSource.md)`, `[`setShardingMode`](PoolDataSource.md)`, `[`setSQLForValidateConnection`](PoolDataSource.md)`, `[`setSSLContext`](PoolDataSource.md)`, `[`setTimeoutCheckInterval`](PoolDataSource.md)`, `[`setTimeToLiveConnectionTimeout`](PoolDataSource.md)`, `[`setTokenSupplier`](PoolDataSource.md)`, `[`setURL`](PoolDataSource.md)`, `[`setUser`](PoolDataSource.md)`, `[`setValidateConnectionOnBorrow`](PoolDataSource.md)`, `[`unregisterConnectionInitializationCallback`](PoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.CommonDataSource

      `getLoginTimeout, getLogWriter, getParentLogger, setLoginTimeout, setLogWriter`

    <!-- -->

    - ### Methods inherited from interface java.sql.Wrapper

      `isWrapperFor, unwrap`

    <!-- -->

    - ### Methods inherited from interface javax.naming.Referenceable

      `getReference`

    <!-- -->

    - ### Methods inherited from interface javax.naming.spi.ObjectFactory

      `getObjectInstance`

    <!-- -->

    - ### Methods inherited from interface oracle.ucp.[UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)

      [`createUniversalConnectionPool`](../UniversalConnectionPoolAdapter.md)`, `[`createUniversalConnectionPoolMBean`](../UniversalConnectionPoolAdapter.md)

<!-- -->

- - ### Constructor Detail

    - #### PoolXADataSourceImpl

          public PoolXADataSourceImpl()

  <!-- -->

  - ### Method Detail

    - #### createPoolWithDefaultProperties

          protected void createPoolWithDefaultProperties()
                                                  throws java.sql.SQLException

      Overrides:
      [`createPoolWithDefaultProperties`](PoolDataSourceImpl.md) in class [`PoolDataSourceImpl`](PoolDataSourceImpl.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()
                                            throws java.sql.SQLException

      Description copied from class: [`PoolDataSourceImpl`](PoolDataSourceImpl.md)
      Attempts to obtain a database connection.
      Specified by:
      `getConnection` in interface `javax.sql.DataSource`

      Overrides:
      [`getConnection`](PoolDataSourceImpl.md) in class [`PoolDataSourceImpl`](PoolDataSourceImpl.md)

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection(java.lang.String username,
                                                   java.lang.String password)
                                            throws java.sql.SQLException

      Description copied from class: [`PoolDataSourceImpl`](PoolDataSourceImpl.md)
      Attempts to obtain a database connection.
      Specified by:
      `getConnection` in interface `javax.sql.DataSource`

      Overrides:
      [`getConnection`](PoolDataSourceImpl.md) in class [`PoolDataSourceImpl`](PoolDataSourceImpl.md)

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

      Description copied from class: [`PoolDataSourceImpl`](PoolDataSourceImpl.md)
      Attempts to obtain a database connection with the requested connection labels.
      Specified by:
      [`getConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Overrides:
      [`getConnection`](PoolDataSourceImpl.md) in class [`PoolDataSourceImpl`](PoolDataSourceImpl.md)

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

      Description copied from class: [`PoolDataSourceImpl`](PoolDataSourceImpl.md)
      Attempts to obtain a database connection with the requested connection labels.
      Specified by:
      [`getConnection`](PoolDataSource.md) in interface [`PoolDataSource`](PoolDataSource.md)

      Overrides:
      [`getConnection`](PoolDataSourceImpl.md) in class [`PoolDataSourceImpl`](PoolDataSourceImpl.md)

      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      `labels` - The requested connection labels.

      Returns:
      A Connection to the database.

      Throws:
      `java.sql.SQLException` - if a database-access error occurs.

    <!-- -->

    - #### getXAConnection

          public javax.sql.XAConnection getXAConnection()
                                                 throws java.sql.SQLException

      Obtains an XAConnection from the embedded Universal Connection Pool instance. Each XAConnection represents a physical database connection can be used in a distributed transaction.
      Specified by:
      `getXAConnection` in interface `javax.sql.XADataSource`

      Specified by:
      [`getXAConnection`](PoolXADataSource.md) in interface [`PoolXADataSource`](PoolXADataSource.md)

      Returns:
      an `XAConnection` object, which represents a physical connection to a data source, that can be used in a distributed transaction

      Throws:
      `java.sql.SQLException` - if a database access error occurs

    <!-- -->

    - #### getXAConnection

          public javax.sql.XAConnection getXAConnection(java.lang.String user,
                                                        java.lang.String password)
                                                 throws java.sql.SQLException

      Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given user name and password. Each XAConnection represents a physical database connection can be used in a distributed transaction.
      Specified by:
      `getXAConnection` in interface `javax.sql.XADataSource`

      Specified by:
      [`getXAConnection`](PoolXADataSource.md) in interface [`PoolXADataSource`](PoolXADataSource.md)

      Parameters:
      `user` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      Returns:
      an `XAConnection` object, which represents a physical connection to a data source, that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### getXAConnection

          public javax.sql.XAConnection getXAConnection(java.util.Properties labels)
                                                 throws java.sql.SQLException

      Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given connection labels. Each XAConnection represents a physical database connection can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](PoolXADataSource.md) in interface [`PoolXADataSource`](PoolXADataSource.md)

      Parameters:
      `labels` - The requested connection labels.

      Returns:
      an `XAConnection` object, which represents a physical connection to a data source, that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### getXAConnection

          public javax.sql.XAConnection getXAConnection(java.lang.String username,
                                                        java.lang.String password,
                                                        java.util.Properties labels)
                                                 throws java.sql.SQLException

      Obtains an XAConnection from the embedded Universal Connection Pool instance, using the given user name, password, and connection labels. Each XAConnection represents a physical database connection can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](PoolXADataSource.md) in interface [`PoolXADataSource`](PoolXADataSource.md)

      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      `labels` - The requested connection labels.

      Returns:
      an `XAConnection` object, which represents a physical connection to a data source, that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### createXAConnectionBuilder

          public UCPXAConnectionBuilder createXAConnectionBuilder()

      Description copied from interface: [`PoolXADataSource`](PoolXADataSource.md)
      Creates a new XAConnectionBuilder instance.
      Specified by:
      [`createXAConnectionBuilder`](PoolXADataSource.md) in interface [`PoolXADataSource`](PoolXADataSource.md)

      Returns:
      Connection builder that builds OracleXAConnection

      See Also:
      `oracle.ucp.jdbc.PoolDataSource#createXAConnectionBuilder()`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolXADataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolXADataSource.md)
- [Next Class](UCPConnectionBuilder.md)

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
