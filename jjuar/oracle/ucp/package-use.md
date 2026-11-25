Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Uses of Package oracle.ucp

- **Packages that use [oracle.ucp](package-summary.md)**

  | Package                | Description                                                                                                       |
  |------------------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp             | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.admin       | Defines interfaces for administering Universal Connection Pool instances, including JMX support.                  |
  | oracle.ucp.jdbc        | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |
  | oracle.ucp.jdbc.oracle | Includes various runtime statistics for the Universal Connection Pool that are specific to Oracle JDBC resources. |

- **Classes in [oracle.ucp](package-summary.md) used by [oracle.ucp](package-summary.md)**

  | Class and Description                                                                                                                                                    |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AbandonedConnectionTimeoutCallback](class-use/AbandonedConnectionTimeoutCallback.md)<br>The callback interface for the abandoned connection timeout feature.            |
  | [ConnectionAffinityCallback](class-use/ConnectionAffinityCallback.md)<br>The callback interface for the Oracle RAC affinity features.                                    |
  | [ConnectionAffinityCallback.AffinityPolicy](class-use/ConnectionAffinityCallback.AffinityPolicy.md)<br>The Enum AffinityPolicy.                                          |
  | [ConnectionHarvestingCallback](class-use/ConnectionHarvestingCallback.md)<br>The callback interface for the connection harvesting support.                               |
  | [ConnectionLabelingCallback](class-use/ConnectionLabelingCallback.md)<br>The callback interface for connection labeling support.                                         |
  | [ConnectionRetrievalInfo](class-use/ConnectionRetrievalInfo.md)<br>The connection retrieval info object is used by the connection factory adapter to create connections. |
  | [TimeToLiveConnectionTimeoutCallback](class-use/TimeToLiveConnectionTimeoutCallback.md)<br>The callback interface for the time-to-live (TTL) connection timeout feature. |
  | [UniversalConnectionPool](class-use/UniversalConnectionPool.md)<br>A connection pool that pools any type of connection (called a physical connection).                   |
  | [UniversalConnectionPoolException](class-use/UniversalConnectionPoolException.md)<br>This exception is the base exception for Universal Connection Pool exceptions.      |
  | [UniversalConnectionPoolLifeCycleState](class-use/UniversalConnectionPoolLifeCycleState.md)<br>Type-safe Life Cycle values for the connection pool.                      |
  | [UniversalConnectionPoolStatistics](class-use/UniversalConnectionPoolStatistics.md)<br>Various runtime statistics for the Universal Connection Pool.                     |
  | [UniversalPooledConnection](class-use/UniversalPooledConnection.md)<br>The `UniversalPooledConnection` is the actual object that is pooled by the connection pool.       |
  | [UniversalPooledConnectionStatus](class-use/UniversalPooledConnectionStatus.md)<br>Describes the status of a pooled connection.                                          |

- **Classes in [oracle.ucp](package-summary.md) used by [oracle.ucp.admin](admin/package-summary.md)**

  | Class and Description                                                                                                                                               |
  |---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [UniversalConnectionPool](class-use/UniversalConnectionPool.md)<br>A connection pool that pools any type of connection (called a physical connection).              |
  | [UniversalConnectionPoolAdapter](class-use/UniversalConnectionPoolAdapter.md)<br>Universal Connection Pool Adapter interface.                                       |
  | [UniversalConnectionPoolException](class-use/UniversalConnectionPoolException.md)<br>This exception is the base exception for Universal Connection Pool exceptions. |
  | [UniversalConnectionPoolLifeCycleState](class-use/UniversalConnectionPoolLifeCycleState.md)<br>Type-safe Life Cycle values for the connection pool.                 |

- **Classes in [oracle.ucp](package-summary.md) used by [oracle.ucp.jdbc](jdbc/package-summary.md)**

  | Class and Description                                                                                                                                                    |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AbandonedConnectionTimeoutCallback](class-use/AbandonedConnectionTimeoutCallback.md)<br>The callback interface for the abandoned connection timeout feature.            |
  | [ConnectionAffinityCallback](class-use/ConnectionAffinityCallback.md)<br>The callback interface for the Oracle RAC affinity features.                                    |
  | [ConnectionHarvestingCallback](class-use/ConnectionHarvestingCallback.md)<br>The callback interface for the connection harvesting support.                               |
  | [ConnectionLabelingCallback](class-use/ConnectionLabelingCallback.md)<br>The callback interface for connection labeling support.                                         |
  | [TimeToLiveConnectionTimeoutCallback](class-use/TimeToLiveConnectionTimeoutCallback.md)<br>The callback interface for the time-to-live (TTL) connection timeout feature. |
  | [UniversalConnectionPool](class-use/UniversalConnectionPool.md)<br>A connection pool that pools any type of connection (called a physical connection).                   |
  | [UniversalConnectionPoolAdapter](class-use/UniversalConnectionPoolAdapter.md)<br>Universal Connection Pool Adapter interface.                                            |
  | [UniversalConnectionPoolStatistics](class-use/UniversalConnectionPoolStatistics.md)<br>Various runtime statistics for the Universal Connection Pool.                     |

- **Classes in [oracle.ucp](package-summary.md) used by [oracle.ucp.jdbc.oracle](jdbc/oracle/package-summary.md)**

  | Class and Description                                                                                                                                |
  |------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [UniversalConnectionPoolStatistics](class-use/UniversalConnectionPoolStatistics.md)<br>Various runtime statistics for the Universal Connection Pool. |

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
