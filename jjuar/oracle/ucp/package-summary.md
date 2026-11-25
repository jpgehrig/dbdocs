Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Package
- [Next Package](admin/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Package oracle.ucp

Includes both required and optional callback interfaces that are used to implement connection pool features.

See: Description

- **Interface Summary**

  | Interface                                                                     | Description                                                                                                                        |
  |-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
  | [AbandonedConnectionTimeoutCallback](AbandonedConnectionTimeoutCallback.md)   | The callback interface for the abandoned connection timeout feature.                                                               |
  | [ConnectionAffinityCallback](ConnectionAffinityCallback.md)                   | The callback interface for the Oracle RAC affinity features.                                                                       |
  | [ConnectionFactoryAdapter](ConnectionFactoryAdapter.md)                       | The connection factory adapter is responsible for creating and closing connections for a specific resource (such as, JDBC or JCA). |
  | [ConnectionHarvestingCallback](ConnectionHarvestingCallback.md)               | The callback interface for the connection harvesting support.                                                                      |
  | [ConnectionLabelingCallback](ConnectionLabelingCallback.md)                   | The callback interface for connection labeling support.                                                                            |
  | [ConnectionRetrievalInfo](ConnectionRetrievalInfo.md)                         | The connection retrieval info object is used by the connection factory adapter to create connections.                              |
  | [TimeToLiveConnectionTimeoutCallback](TimeToLiveConnectionTimeoutCallback.md) | The callback interface for the time-to-live (TTL) connection timeout feature.                                                      |
  | [UniversalConnectionPool](UniversalConnectionPool.md)                         | A connection pool that pools any type of connection (called a physical connection).                                                |
  | [UniversalConnectionPoolAdapter](UniversalConnectionPoolAdapter.md)           | Universal Connection Pool Adapter interface.                                                                                       |
  | [UniversalConnectionPoolStatistics](UniversalConnectionPoolStatistics.md)     | Various runtime statistics for the Universal Connection Pool.                                                                      |
  | [UniversalPooledConnection](UniversalPooledConnection.md)                     | The `UniversalPooledConnection` is the actual object that is pooled by the connection pool.                                        |

- **Class Summary**

  | Class                                                                             | Description                                          |
  |-----------------------------------------------------------------------------------|------------------------------------------------------|
  | [UniversalConnectionPoolLifeCycleState](UniversalConnectionPoolLifeCycleState.md) | Type-safe Life Cycle values for the connection pool. |
  | [UniversalPooledConnectionStatus](UniversalPooledConnectionStatus.md)             | Describes the status of a pooled connection.         |

- **Enum Summary**

  | Enum                                                                                      | Description              |
  |-------------------------------------------------------------------------------------------|--------------------------|
  | [ConnectionAffinityCallback.AffinityPolicy](ConnectionAffinityCallback.AffinityPolicy.md) | The Enum AffinityPolicy. |

- **Exception Summary**

  | Exception                                                               | Description                                                                             |
  |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
  | [NoAvailableConnectionsException](NoAvailableConnectionsException.md)   | An exception indicating that there are no available connections in the connection pool. |
  | [UniversalConnectionPoolException](UniversalConnectionPoolException.md) | This exception is the base exception for Universal Connection Pool exceptions.          |

## Package oracle.ucp Description

Includes both required and optional callback interfaces that are used to implement connection pool features. These callback interfaces include:

- `ConnectionAffinityCallback` interface is a callback required by the Oracle RAC affinity features. It allows the Universal Connection Pool to establish and retrieve connection affinity contexts. The interface also allows applications to inform the connection pool of their choice of the connection affinity policy.
- `ConnectionLabelingCallback` interface is a callback required by the connection labeling feature. It is used to define how the connection pool selects labeled connections and allows the selected connection to be configured before it is returned to an application.
- `ConnectionHarvestingCallback` interface is an optional callback for the connection harvesting feature. It allows applications to perform customized cleanup tasks when a connection is harvested by the pool.
- `AbandonedConnectionTimeoutCallback` interface is an optional callback for the abandoned connection timeout feature. It allows applications to provide customized handling for abandoned connections.
- `TimeToLiveConnectionTimeoutCallback` interface is an optional callback for the time-to-live (TTL) connection timeout feature. It allows applications to provide customized handling for TTL timed-out connections.

This package also includes the connection pool itself that pools any type of connection (called a physical connection).
There are several key objects that make up the connection pool:

- The physical pool itself - the physical pool maintains pooled connection that can be borrowed from the pool, returned to the pool, or closed and
   not returned to the pool. The pool keeps track of the connections that are available (so that they can be borrowed) and connections that are in use (so they can be reaped if it is determined that they are no longer valid).
- The connection factory adapter - the connection pool must rely on another entity to create and close connections because connection pools can pool any type of connection. This is the responsibility of the connection factory adapter. A connection factory adapter is tied to a specific resource (JDBC, JCA, LDAP, and so forth).  When the connection pool needs to create a new connection, it asks the connection factory adapter to do so. The returned connection is placed inside a `UniversalPooledConnection` object that is then placed into the connection pool. When the connection pool closes a connection, it hands the connection to the connection factory adapter which then closes the connection.
- The pooled connection - each pooled connection in the connection pool is an instance of `UniversalPooledConnection`. The pooled connection decorates a physical connection (created by the connection factory adapter) which can be borrowed.
- The connection retrieval info object - is used by the connection factory adapter to create connections. It contains resource-specific information that the connection factory adapter uses to create connections. For example, the JDBC connection retrieval info object maintains the user and password that are used to create a connection from a JDBC resource. The JCA connection retrieval information object maintains the Subject and JCA `ConnectionRequestInfo` object.

The connection pool provides some properties for users to customize the pool's behavior, such as (see `UniversalConnectionPool`):

- minPoolSize - the minimum number of connections that the pool maintains.
- maxPoolSize - the maximum number of connections that the pool maintains.
- initialPoolSize - the initial number of connections in the pool.

The connection pool maintains some statistics such as (see `UniversalConnectionPoolStatistics`):

- The number of connections that are in use (borrowed) at any given time.
- The number of connections that are available (not in use) at any given time.
- The number of physical connections created by the resource.
- The number of physical connections closed by the resource.

A connection pool has a lifecycle. See `UniversalConnectionPoolLifeCycleState` for details.

## Related Documentation

For overviews, tutorials, examples, guides, and tool documentation, see:

- Oracle Universal Connection Pool for JDBC Developer's Guide



Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Package
- [Next Package](admin/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
