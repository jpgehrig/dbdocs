Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSourceImpl.md)
- [Next Class](PoolXADataSourceImpl.md)

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

## Interface PoolXADataSource

- All Superinterfaces:
  javax.sql.CommonDataSource, javax.sql.DataSource, [PoolDataSource](PoolDataSource.md), java.sql.Wrapper, javax.sql.XADataSource

  <!-- -->

  All Known Implementing Classes:
  [PoolXADataSourceImpl](PoolXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface PoolXADataSource
      extends PoolDataSource, javax.sql.XADataSource

  A Universal Connection Pool-enabled XA data source. See `PoolDataSource` for standard data source and connection pool properties that are supported.
  See Also:
  [`PoolDataSource`](PoolDataSource.md), [`UniversalConnectionPool`](../UniversalConnectionPool.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`UCP_ABANDONED_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_AFFINITY_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_CLASS_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_FACTORY_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_MAX_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_HARVEST_TRIGGER_COUNT`](PoolDataSource.md)`, `[`UCP_CONNECTION_INITIALIZATION_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_CALLBACK`](PoolDataSource.md)`, `[`UCP_CONNECTION_LABELING_HIGH_COST`](PoolDataSource.md)`, `[`UCP_CONNECTION_POOL_NAME`](PoolDataSource.md)`, `[`UCP_CONNECTION_PROPERTIES`](PoolDataSource.md)`, `[`UCP_CONNECTION_REPURPOSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_CONNECTION_VALIDATION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_CONNECTION_WAIT_TIMEOUT`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_FROM_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_DATA_SOURCE_NAME`](PoolDataSource.md)`, `[`UCP_DATABASE_NAME`](PoolDataSource.md)`, `[`UCP_DESCRIPTION`](PoolDataSource.md)`, `[`UCP_FAST_CONNECTION_FAILOVER_ENABLED`](PoolDataSource.md)`, `[`UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD`](PoolDataSource.md)`, `[`UCP_INACTIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_INITIAL_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_LOGIN_TIMEOUT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_COUNT`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTION_REUSE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SERVICE`](PoolDataSource.md)`, `[`UCP_MAX_CONNECTIONS_PER_SHARD`](PoolDataSource.md)`, `[`UCP_MAX_IDLE_TIME`](PoolDataSource.md)`, `[`UCP_MAX_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_MAX_STATEMENTS`](PoolDataSource.md)`, `[`UCP_MIN_POOL_SIZE`](PoolDataSource.md)`, `[`UCP_NETWORK_PROTOCOL`](PoolDataSource.md)`, `[`UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE`](PoolDataSource.md)`, `[`UCP_ONS_CONFIGURATION`](PoolDataSource.md)`, `[`UCP_PASSWORD`](PoolDataSource.md)`, `[`UCP_PDB_ROLES`](PoolDataSource.md)`, `[`UCP_PORT_NUMBER`](PoolDataSource.md)`, `[`UCP_PROPERTY_CYCLE`](PoolDataSource.md)`, `[`UCP_ROLE_NAME`](PoolDataSource.md)`, `[`UCP_SECONDS_TO_TRUST_IDLE_CONNECTION`](PoolDataSource.md)`, `[`UCP_SERVER_NAME`](PoolDataSource.md)`, `[`UCP_SERVICE_NAME`](PoolDataSource.md)`, `[`UCP_SHARDING_MODE`](PoolDataSource.md)`, `[`UCP_SQL_FOR_VALIDATE_CONNECTION`](PoolDataSource.md)`, `[`UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT`](PoolDataSource.md)`, `[`UCP_TIMEOUT_CHECK_INTERVAL`](PoolDataSource.md)`, `[`UCP_URL`](PoolDataSource.md)`, `[`UCP_USER`](PoolDataSource.md)`, `[`UCP_VALIDATE_CONNECTION_ON_BORROW`](PoolDataSource.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                               |
    |-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UCPXAConnectionBuilder`](UCPXAConnectionBuilder.md) | `createXAConnectionBuilder``()`<br>Creates a new XAConnectionBuilder instance.                                                                                                                                                                       |
    | `javax.sql.XAConnection`                              | `getXAConnection``()`<br>Obtains an XA connection from the embedded Universal Connection Pool instance.                                                                                                                                              |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.util.Properties labels)`<br>Obtains an XA connection from the embedded Universal Connection Pool instance, using the given connection labels.                                                                                |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.lang.String user, java.lang.String password)`<br>Obtains an XA connection from the embedded Universal Connection Pool instance, using the given user name and password.                                                      |
    | `javax.sql.XAConnection`                              | `getXAConnection``(java.lang.String username, java.lang.String password, java.util.Properties labels)`<br>Obtains an XA connection from the embedded Universal Connection Pool instance, using the given user name, password, and connection labels. |

    - ### Methods inherited from interface oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)

      [`createConnectionBuilder`](PoolDataSource.md)`, `[`createShardingKeyBuilder`](PoolDataSource.md)`, `[`getAbandonedConnectionTimeout`](PoolDataSource.md)`, `[`getAvailableConnectionsCount`](PoolDataSource.md)`, `[`getBorrowedConnectionsCount`](PoolDataSource.md)`, `[`getConnection`](PoolDataSource.md)`, `[`getConnection`](PoolDataSource.md)`, `[`getConnectionFactoryClassName`](PoolDataSource.md)`, `[`getConnectionFactoryProperties`](PoolDataSource.md)`, `[`getConnectionFactoryProperty`](PoolDataSource.md)`, `[`getConnectionHarvestMaxCount`](PoolDataSource.md)`, `[`getConnectionHarvestTriggerCount`](PoolDataSource.md)`, `[`getConnectionInitializationCallback`](PoolDataSource.md)`, `[`getConnectionLabelingHighCost`](PoolDataSource.md)`, `[`getConnectionPoolName`](PoolDataSource.md)`, `[`getConnectionProperties`](PoolDataSource.md)`, `[`getConnectionProperty`](PoolDataSource.md)`, `[`getConnectionRepurposeThreshold`](PoolDataSource.md)`, `[`getConnectionValidationTimeout`](PoolDataSource.md)`, `[`getConnectionWaitTimeout`](PoolDataSource.md)`, `[`getDatabaseName`](PoolDataSource.md)`, `[`getDataSourceName`](PoolDataSource.md)`, `[`getDescription`](PoolDataSource.md)`, `[`getFastConnectionFailoverEnabled`](PoolDataSource.md)`, `[`getHighCostConnectionReuseThreshold`](PoolDataSource.md)`, `[`getInactiveConnectionTimeout`](PoolDataSource.md)`, `[`getInitialPoolSize`](PoolDataSource.md)`, `[`getMaxConnectionReuseCount`](PoolDataSource.md)`, `[`getMaxConnectionReuseTime`](PoolDataSource.md)`, `[`getMaxConnectionsPerService`](PoolDataSource.md)`, `[`getMaxConnectionsPerShard`](PoolDataSource.md)`, `[`getMaxIdleTime`](PoolDataSource.md)`, `[`getMaxPoolSize`](PoolDataSource.md)`, `[`getMaxStatements`](PoolDataSource.md)`, `[`getMinPoolSize`](PoolDataSource.md)`, `[`getNetworkProtocol`](PoolDataSource.md)`, `[`getONSConfiguration`](PoolDataSource.md)`, `[`getPassword`](PoolDataSource.md)`, `[`getPdbRoles`](PoolDataSource.md)`, `[`getPortNumber`](PoolDataSource.md)`, `[`getPropertyCycle`](PoolDataSource.md)`, `[`getQueryTimeout`](PoolDataSource.md)`, `[`getRoleName`](PoolDataSource.md)`, `[`getSecondsToTrustIdleConnection`](PoolDataSource.md)`, `[`getServerName`](PoolDataSource.md)`, `[`getServiceName`](PoolDataSource.md)`, `[`getShardingMode`](PoolDataSource.md)`, `[`getSQLForValidateConnection`](PoolDataSource.md)`, `[`getStatistics`](PoolDataSource.md)`, `[`getTimeoutCheckInterval`](PoolDataSource.md)`, `[`getTimeToLiveConnectionTimeout`](PoolDataSource.md)`, `[`getURL`](PoolDataSource.md)`, `[`getUser`](PoolDataSource.md)`, `[`getValidateConnectionOnBorrow`](PoolDataSource.md)`, `[`reconfigureDataSource`](PoolDataSource.md)`, `[`registerConnectionAffinityCallback`](PoolDataSource.md)`, `[`registerConnectionInitializationCallback`](PoolDataSource.md)`, `[`registerConnectionLabelingCallback`](PoolDataSource.md)`, `[`removeConnectionAffinityCallback`](PoolDataSource.md)`, `[`removeConnectionLabelingCallback`](PoolDataSource.md)`, `[`setAbandonedConnectionTimeout`](PoolDataSource.md)`, `[`setConnectionFactoryClassName`](PoolDataSource.md)`, `[`setConnectionFactoryProperties`](PoolDataSource.md)`, `[`setConnectionFactoryProperty`](PoolDataSource.md)`, `[`setConnectionHarvestMaxCount`](PoolDataSource.md)`, `[`setConnectionHarvestTriggerCount`](PoolDataSource.md)`, `[`setConnectionLabelingHighCost`](PoolDataSource.md)`, `[`setConnectionPoolName`](PoolDataSource.md)`, `[`setConnectionProperties`](PoolDataSource.md)`, `[`setConnectionProperty`](PoolDataSource.md)`, `[`setConnectionRepurposeThreshold`](PoolDataSource.md)`, `[`setConnectionValidationTimeout`](PoolDataSource.md)`, `[`setConnectionWaitTimeout`](PoolDataSource.md)`, `[`setDatabaseName`](PoolDataSource.md)`, `[`setDataSourceName`](PoolDataSource.md)`, `[`setDescription`](PoolDataSource.md)`, `[`setFastConnectionFailoverEnabled`](PoolDataSource.md)`, `[`setHighCostConnectionReuseThreshold`](PoolDataSource.md)`, `[`setInactiveConnectionTimeout`](PoolDataSource.md)`, `[`setInitialPoolSize`](PoolDataSource.md)`, `[`setMaxConnectionReuseCount`](PoolDataSource.md)`, `[`setMaxConnectionReuseTime`](PoolDataSource.md)`, `[`setMaxConnectionsPerShard`](PoolDataSource.md)`, `[`setMaxIdleTime`](PoolDataSource.md)`, `[`setMaxPoolSize`](PoolDataSource.md)`, `[`setMaxStatements`](PoolDataSource.md)`, `[`setMinPoolSize`](PoolDataSource.md)`, `[`setNetworkProtocol`](PoolDataSource.md)`, `[`setONSConfiguration`](PoolDataSource.md)`, `[`setPassword`](PoolDataSource.md)`, `[`setPortNumber`](PoolDataSource.md)`, `[`setPropertyCycle`](PoolDataSource.md)`, `[`setQueryTimeout`](PoolDataSource.md)`, `[`setRoleName`](PoolDataSource.md)`, `[`setSecondsToTrustIdleConnection`](PoolDataSource.md)`, `[`setServerName`](PoolDataSource.md)`, `[`setShardingMode`](PoolDataSource.md)`, `[`setSQLForValidateConnection`](PoolDataSource.md)`, `[`setSSLContext`](PoolDataSource.md)`, `[`setTimeoutCheckInterval`](PoolDataSource.md)`, `[`setTimeToLiveConnectionTimeout`](PoolDataSource.md)`, `[`setTokenSupplier`](PoolDataSource.md)`, `[`setURL`](PoolDataSource.md)`, `[`setUser`](PoolDataSource.md)`, `[`setValidateConnectionOnBorrow`](PoolDataSource.md)`, `[`unregisterConnectionInitializationCallback`](PoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.DataSource

      `getConnection, getConnection`

    <!-- -->

    - ### Methods inherited from interface javax.sql.CommonDataSource

      `getLoginTimeout, getLogWriter, getParentLogger, setLoginTimeout, setLogWriter`

    <!-- -->

    - ### Methods inherited from interface java.sql.Wrapper

      `isWrapperFor, unwrap`

<!-- -->

- - ### Method Detail

    - #### getXAConnection

          javax.sql.XAConnection getXAConnection()
                                          throws java.sql.SQLException

      Obtains an XA connection from the embedded Universal Connection Pool instance. Each `XAConnection` object represents a physical database connection that can be used in a distributed transaction.
      Specified by:
      `getXAConnection` in interface `javax.sql.XADataSource`

      Returns:
      An `XAConnection` object that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### getXAConnection

          javax.sql.XAConnection getXAConnection(java.lang.String user,
                                                 java.lang.String password)
                                          throws java.sql.SQLException

      Obtains an XA connection from the embedded Universal Connection Pool instance, using the given user name and password. Each `XAConnection` object represents a physical database connection that can be used in a distributed transaction.
      Specified by:
      `getXAConnection` in interface `javax.sql.XADataSource`

      Parameters:
      `user` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      Returns:
      An `XAConnection` object that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### getXAConnection

          javax.sql.XAConnection getXAConnection(java.util.Properties labels)
                                          throws java.sql.SQLException

      Obtains an XA connection from the embedded Universal Connection Pool instance, using the given connection labels. Each `XAConnection` object represents a physical database connection that can be used in a distributed transaction.
      Parameters:
      `labels` - The requested connection labels.

      Returns:
      An `XAConnection` object, which represents a physical connection to a data source, that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### getXAConnection

          javax.sql.XAConnection getXAConnection(java.lang.String username,
                                                 java.lang.String password,
                                                 java.util.Properties labels)
                                          throws java.sql.SQLException

      Obtains an XA connection from the embedded Universal Connection Pool instance, using the given user name, password, and connection labels. Each `XAConnection` object represents a physical database connection that can be used in a distributed transaction.
      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `password` - The user's password.

      `labels` - The requested connection labels.

      Returns:
      An `XAConnection` object that can be used in a distributed transaction.

      Throws:
      `java.sql.SQLException` - if a database access error occurs.

    <!-- -->

    - #### createXAConnectionBuilder

          UCPXAConnectionBuilder createXAConnectionBuilder()

      Creates a new XAConnectionBuilder instance.
      Returns:
      The XAConnectionBuilder instance that was created

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSourceImpl.md)
- [Next Class](PoolXADataSourceImpl.md)

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
