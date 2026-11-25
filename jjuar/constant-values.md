Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-files/index-1.md)
- [Help](help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Constant Field Values

## Contents

- oracle.ucp.\*

## oracle.ucp.\*

- **oracle.ucp.[UniversalConnectionPoolLifeCycleState](oracle/ucp/UniversalConnectionPoolLifeCycleState.md)**

  | Modifier and Type                      | Constant Field                                                                    | Value        |
  |----------------------------------------|-----------------------------------------------------------------------------------|--------------|
  | `public static final java.lang.String` | [`LIFE_CYCLE_FAILED_DESC`](oracle/ucp/UniversalConnectionPoolLifeCycleState.md)   | `"Failed"`   |
  | `public static final java.lang.String` | [`LIFE_CYCLE_RUNNING_DESC`](oracle/ucp/UniversalConnectionPoolLifeCycleState.md)  | `"Running"`  |
  | `public static final java.lang.String` | [`LIFE_CYCLE_STARTING_DESC`](oracle/ucp/UniversalConnectionPoolLifeCycleState.md) | `"Starting"` |
  | `public static final java.lang.String` | [`LIFE_CYCLE_STOPPED_DESC`](oracle/ucp/UniversalConnectionPoolLifeCycleState.md)  | `"Stopped"`  |
  | `public static final java.lang.String` | [`LIFE_CYCLE_STOPPING_DESC`](oracle/ucp/UniversalConnectionPoolLifeCycleState.md) | `"Stopping"` |

- **oracle.ucp.[UniversalPooledConnectionStatus](oracle/ucp/UniversalPooledConnectionStatus.md)**

  | Modifier and Type                      | Constant Field                                                                   | Value                                                  |
  |----------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------|
  | `public static final java.lang.String` | [`STATUS_BAD_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md)               | `"Bad"`                                                |
  | `public static final java.lang.String` | [`STATUS_CLOSE_ON_RETURN_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md)   | `"Close connection when returned to pool"`             |
  | `public static final java.lang.String` | [`STATUS_CLOSED_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md)            | `"Closed"`                                             |
  | `public static final java.lang.String` | [`STATUS_NORMAL_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md)            | `"Normal"`                                             |
  | `public static final java.lang.String` | [`STATUS_RECONNECTING_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md)      | `"Reconnecting"`                                       |
  | `public static final java.lang.String` | [`STATUS_REPLACE_ON_RETURN_DESC`](oracle/ucp/UniversalPooledConnectionStatus.md) | `"Close and replace connection when returned to pool"` |

<!-- -->

- **oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md)**

  | Modifier and Type                      | Constant Field                                                                  | Value                                |
  |----------------------------------------|---------------------------------------------------------------------------------|--------------------------------------|
  | `public static final java.lang.String` | [`UCP_ABANDONED_CONNECTION_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)         | `"abandonedConnectionTimeout"`       |
  | `public static final java.lang.String` | [`UCP_CONNECTION_AFFINITY_CALLBACK`](oracle/ucp/jdbc/PoolDataSource.md)         | `"connectionAffinityCallback"`       |
  | `public static final java.lang.String` | [`UCP_CONNECTION_FACTORY_CLASS_NAME`](oracle/ucp/jdbc/PoolDataSource.md)        | `"connectionFactoryClassName"`       |
  | `public static final java.lang.String` | [`UCP_CONNECTION_FACTORY_PROPERTIES`](oracle/ucp/jdbc/PoolDataSource.md)        | `"connectionFactoryProperties"`      |
  | `public static final java.lang.String` | [`UCP_CONNECTION_HARVEST_MAX_COUNT`](oracle/ucp/jdbc/PoolDataSource.md)         | `"connectionHarvestMaxCount"`        |
  | `public static final java.lang.String` | [`UCP_CONNECTION_HARVEST_TRIGGER_COUNT`](oracle/ucp/jdbc/PoolDataSource.md)     | `"connectionHarvestTriggerCount"`    |
  | `public static final java.lang.String` | [`UCP_CONNECTION_INITIALIZATION_CALLBACK`](oracle/ucp/jdbc/PoolDataSource.md)   | `"connectionInitializationCallback"` |
  | `public static final java.lang.String` | [`UCP_CONNECTION_LABELING_CALLBACK`](oracle/ucp/jdbc/PoolDataSource.md)         | `"connectionLabelingCallback"`       |
  | `public static final java.lang.String` | [`UCP_CONNECTION_LABELING_HIGH_COST`](oracle/ucp/jdbc/PoolDataSource.md)        | `"connectionLabelingHighCost"`       |
  | `public static final java.lang.String` | [`UCP_CONNECTION_POOL_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                 | `"connectionPoolName"`               |
  | `public static final java.lang.String` | [`UCP_CONNECTION_PROPERTIES`](oracle/ucp/jdbc/PoolDataSource.md)                | `"connectionProperties"`             |
  | `public static final java.lang.String` | [`UCP_CONNECTION_REPURPOSE_THRESHOLD`](oracle/ucp/jdbc/PoolDataSource.md)       | `"connectionRepurposeThreshold"`     |
  | `public static final java.lang.String` | [`UCP_CONNECTION_VALIDATION_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)        | `"connectionValidationTimeout"`      |
  | `public static final java.lang.String` | [`UCP_CONNECTION_WAIT_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)              | `"connectionWaitTimeout"`            |
  | `public static final java.lang.String` | [`UCP_DATA_SOURCE_FROM_CONFIGURATION`](oracle/ucp/jdbc/PoolDataSource.md)       | `"dataSourceFromConfiguration"`      |
  | `public static final java.lang.String` | [`UCP_DATA_SOURCE_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                     | `"dataSourceName"`                   |
  | `public static final java.lang.String` | [`UCP_DATABASE_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"databaseName"`                     |
  | `public static final java.lang.String` | [`UCP_DESCRIPTION`](oracle/ucp/jdbc/PoolDataSource.md)                          | `"description"`                      |
  | `public static final java.lang.String` | [`UCP_FAST_CONNECTION_FAILOVER_ENABLED`](oracle/ucp/jdbc/PoolDataSource.md)     | `"fastConnectionFailoverEnabled"`    |
  | `public static final java.lang.String` | [`UCP_HIGH_COST_CONNECTION_REUSE_THRESHOLD`](oracle/ucp/jdbc/PoolDataSource.md) | `"highCostConnectionReuseThreshold"` |
  | `public static final java.lang.String` | [`UCP_INACTIVE_CONNECTION_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)          | `"inactiveConnectionTimeout"`        |
  | `public static final java.lang.String` | [`UCP_INITIAL_POOL_SIZE`](oracle/ucp/jdbc/PoolDataSource.md)                    | `"initialPoolSize"`                  |
  | `public static final java.lang.String` | [`UCP_LOGIN_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"loginTimeout"`                     |
  | `public static final java.lang.String` | [`UCP_MAX_CONNECTION_REUSE_COUNT`](oracle/ucp/jdbc/PoolDataSource.md)           | `"maxConnectionReuseCount"`          |
  | `public static final java.lang.String` | [`UCP_MAX_CONNECTION_REUSE_TIME`](oracle/ucp/jdbc/PoolDataSource.md)            | `"maxConnectionReuseTime"`           |
  | `public static final java.lang.String` | [`UCP_MAX_CONNECTIONS_PER_SERVICE`](oracle/ucp/jdbc/PoolDataSource.md)          | `"maxConnectionsPerService"`         |
  | `public static final java.lang.String` | [`UCP_MAX_CONNECTIONS_PER_SHARD`](oracle/ucp/jdbc/PoolDataSource.md)            | `"maxConnectionsPerShard"`           |
  | `public static final java.lang.String` | [`UCP_MAX_IDLE_TIME`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"maxIdleTime"`                      |
  | `public static final java.lang.String` | [`UCP_MAX_POOL_SIZE`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"maxPoolSize"`                      |
  | `public static final java.lang.String` | [`UCP_MAX_STATEMENTS`](oracle/ucp/jdbc/PoolDataSource.md)                       | `"maxStatements"`                    |
  | `public static final java.lang.String` | [`UCP_MIN_POOL_SIZE`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"minPoolSize"`                      |
  | `public static final java.lang.String` | [`UCP_NETWORK_PROTOCOL`](oracle/ucp/jdbc/PoolDataSource.md)                     | `"networkProtocol"`                  |
  | `public static final java.lang.String` | [`UCP_NTH_RETURNED_CONNECTION_TO_VALIDATE`](oracle/ucp/jdbc/PoolDataSource.md)  | `"nthReturnedConnectionToValidate"`  |
  | `public static final java.lang.String` | [`UCP_ONS_CONFIGURATION`](oracle/ucp/jdbc/PoolDataSource.md)                    | `"onsConfiguration"`                 |
  | `public static final java.lang.String` | [`UCP_PASSWORD`](oracle/ucp/jdbc/PoolDataSource.md)                             | `"password"`                         |
  | `public static final java.lang.String` | [`UCP_PDB_ROLES`](oracle/ucp/jdbc/PoolDataSource.md)                            | `"pdbRoles"`                         |
  | `public static final java.lang.String` | [`UCP_PORT_NUMBER`](oracle/ucp/jdbc/PoolDataSource.md)                          | `"portNumber"`                       |
  | `public static final java.lang.String` | [`UCP_PROPERTY_CYCLE`](oracle/ucp/jdbc/PoolDataSource.md)                       | `"propertyCycle"`                    |
  | `public static final java.lang.String` | [`UCP_ROLE_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                            | `"roleName"`                         |
  | `public static final java.lang.String` | [`UCP_SECONDS_TO_TRUST_IDLE_CONNECTION`](oracle/ucp/jdbc/PoolDataSource.md)     | `"secondsToTrustIdleConnection"`     |
  | `public static final java.lang.String` | [`UCP_SERVER_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                          | `"serverName"`                       |
  | `public static final java.lang.String` | [`UCP_SERVICE_NAME`](oracle/ucp/jdbc/PoolDataSource.md)                         | `"serviceName"`                      |
  | `public static final java.lang.String` | [`UCP_SHARDING_MODE`](oracle/ucp/jdbc/PoolDataSource.md)                        | `"shardingMode"`                     |
  | `public static final java.lang.String` | [`UCP_SQL_FOR_VALIDATE_CONNECTION`](oracle/ucp/jdbc/PoolDataSource.md)          | `"sqlForValidateConnection"`         |
  | `public static final java.lang.String` | [`UCP_TIME_TO_LIVE_CONNECTION_TIMEOUT`](oracle/ucp/jdbc/PoolDataSource.md)      | `"timeToLiveConnectionTimeout"`      |
  | `public static final java.lang.String` | [`UCP_TIMEOUT_CHECK_INTERVAL`](oracle/ucp/jdbc/PoolDataSource.md)               | `"timeoutCheckInterval"`             |
  | `public static final java.lang.String` | [`UCP_URL`](oracle/ucp/jdbc/PoolDataSource.md)                                  | `"url"`                              |
  | `public static final java.lang.String` | [`UCP_USER`](oracle/ucp/jdbc/PoolDataSource.md)                                 | `"user"`                             |
  | `public static final java.lang.String` | [`UCP_VALIDATE_CONNECTION_ON_BORROW`](oracle/ucp/jdbc/PoolDataSource.md)        | `"validateConnectionOnBorrow"`       |

- **oracle.ucp.jdbc.[PoolDataSourceImpl](oracle/ucp/jdbc/PoolDataSourceImpl.md)**

  | Modifier and Type                      | Constant Field                                                           | Value                                       |
  |----------------------------------------|--------------------------------------------------------------------------|---------------------------------------------|
  | `public static final java.lang.String` | [`SECRET_STORE_CONNECT`](oracle/ucp/jdbc/PoolDataSourceImpl.md)          | `"oracle.security.client.connect_string"`   |
  | `public static final java.lang.String` | [`SECRET_STORE_DEFAULT_PASSWORD`](oracle/ucp/jdbc/PoolDataSourceImpl.md) | `"oracle.security.client.default_password"` |
  | `public static final java.lang.String` | [`SECRET_STORE_DEFAULT_USERNAME`](oracle/ucp/jdbc/PoolDataSourceImpl.md) | `"oracle.security.client.default_username"` |
  | `public static final java.lang.String` | [`SECRET_STORE_PASSWORD`](oracle/ucp/jdbc/PoolDataSourceImpl.md)         | `"oracle.security.client.password"`         |
  | `public static final java.lang.String` | [`SECRET_STORE_USERNAME`](oracle/ucp/jdbc/PoolDataSourceImpl.md)         | `"oracle.security.client.username"`         |

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-files/index-1.md)
- [Help](help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
