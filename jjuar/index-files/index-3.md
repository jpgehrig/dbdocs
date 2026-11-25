Skip navigation links

- [Overview](../overview-summary.md)
- Package
- Class
- Use
- [Tree](../overview-tree.md)
- [Deprecated](../deprecated-list.md)
- Index
- [Help](../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Letter](index-2.md)
- [Next Letter](index-4.md)

<!-- -->

- [Frames](../index.md)
- No Frames

<!-- -->

- [All Classes](../allclasses-noframe.md)

[A](index-1.md) [B](index-2.md) C [D](index-4.md) [E](index-5.md) [F](index-6.md) [G](index-7.md) [H](index-8.md) [I](index-9.md) [J](index-10.md) [L](index-11.md) [M](index-12.md) [N](index-13.md) [O](index-14.md) [P](index-15.md) [R](index-16.md) [S](index-17.md) [T](index-18.md) [U](index-19.md) [V](index-20.md) 

## C

[cleanup()](../oracle/ucp/ConnectionHarvestingCallback.md) - Method in interface oracle.ucp.[ConnectionHarvestingCallback](../oracle/ucp/ConnectionHarvestingCallback.md)
Cleans up a connection being harvested before the connection is returned to the connection pool.

[close()](../oracle/ucp/UniversalPooledConnection.md) - Method in interface oracle.ucp.[UniversalPooledConnection](../oracle/ucp/UniversalPooledConnection.md)
TODO document close connection

[closeConnection(Object)](../oracle/ucp/ConnectionFactoryAdapter.md) - Method in interface oracle.ucp.[ConnectionFactoryAdapter](../oracle/ucp/ConnectionFactoryAdapter.md)
Closes the given connection.

[closeConnection(UniversalPooledConnection)](../oracle/ucp/UniversalConnectionPool.md) - Method in interface oracle.ucp.[UniversalConnectionPool](../oracle/ucp/UniversalConnectionPool.md)
Closes the pooled connection.

[configure(Properties, Object)](../oracle/ucp/ConnectionLabelingCallback.md) - Method in interface oracle.ucp.[ConnectionLabelingCallback](../oracle/ucp/ConnectionLabelingCallback.md)
Configures the selected connection for a borrowing request before returning the connection to the application.

[ConnectionAffinityCallback](../oracle/ucp/ConnectionAffinityCallback.md) - Interface in [oracle.ucp](../oracle/ucp/package-summary.md)
The callback interface for the Oracle RAC affinity features.

[ConnectionAffinityCallback.AffinityPolicy](../oracle/ucp/ConnectionAffinityCallback.AffinityPolicy.md) - Enum in [oracle.ucp](../oracle/ucp/package-summary.md)
The Enum AffinityPolicy.

[ConnectionFactoryAdapter](../oracle/ucp/ConnectionFactoryAdapter.md) - Interface in [oracle.ucp](../oracle/ucp/package-summary.md)
The connection factory adapter is responsible for creating and closing connections for a specific resource (such as, JDBC or JCA).

[ConnectionHarvestingCallback](../oracle/ucp/ConnectionHarvestingCallback.md) - Interface in [oracle.ucp](../oracle/ucp/package-summary.md)
The callback interface for the connection harvesting support.

[ConnectionInitializationCallback](../oracle/ucp/jdbc/ConnectionInitializationCallback.md) - Interface in [oracle.ucp.jdbc](../oracle/ucp/jdbc/package-summary.md)
This callback allows applications and frameworks to initialize connections retrieved from Universal Connection Pool using common actions, before the connections are put to use.

[ConnectionLabelingCallback](../oracle/ucp/ConnectionLabelingCallback.md) - Interface in [oracle.ucp](../oracle/ucp/package-summary.md)
The callback interface for connection labeling support.

[ConnectionLabelingCallback](../oracle/ucp/jdbc/ConnectionLabelingCallback.md) - Interface in [oracle.ucp.jdbc](../oracle/ucp/jdbc/package-summary.md)
New callback interface for connection labeling support.

[ConnectionRetrievalInfo](../oracle/ucp/ConnectionRetrievalInfo.md) - Interface in [oracle.ucp](../oracle/ucp/package-summary.md)
The connection retrieval info object is used by the connection factory adapter to create connections.

[ConnectionWithAbandonedTimeout](../oracle/ucp/jdbc/ConnectionWithAbandonedTimeout.md) - Interface in [oracle.ucp.jdbc](../oracle/ucp/jdbc/package-summary.md)
Interface supporting abandoned connection timeout handling for JDBC `java.sql.Connections`.

[ConnectionWithTimeToLiveTimeout](../oracle/ucp/jdbc/ConnectionWithTimeToLiveTimeout.md) - Interface in [oracle.ucp.jdbc](../oracle/ucp/jdbc/package-summary.md)
Interface supporting time-to-live connection timeout handling for JDBC `java.sql.Connections`.

[cost(Properties, Properties)](../oracle/ucp/ConnectionLabelingCallback.md) - Method in interface oracle.ucp.[ConnectionLabelingCallback](../oracle/ucp/ConnectionLabelingCallback.md)
Projects the cost of configuring connections considering label-matching differences.

[createConnection(ConnectionRetrievalInfo)](../oracle/ucp/ConnectionFactoryAdapter.md) - Method in interface oracle.ucp.[ConnectionFactoryAdapter](../oracle/ucp/ConnectionFactoryAdapter.md)
Creates a connection.

[createConnectionBuilder()](../oracle/ucp/jdbc/PoolDataSource.md) - Method in interface oracle.ucp.jdbc.[PoolDataSource](../oracle/ucp/jdbc/PoolDataSource.md)
Creates a new UCPConnectionBuilder instance.

[createConnectionBuilder()](../oracle/ucp/jdbc/PoolDataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolDataSourceImpl](../oracle/ucp/jdbc/PoolDataSourceImpl.md)
 

[createConnectionPool(UniversalConnectionPoolAdapter)](../oracle/ucp/admin/UniversalConnectionPoolManager.md) - Method in interface oracle.ucp.admin.[UniversalConnectionPoolManager](../oracle/ucp/admin/UniversalConnectionPoolManager.md)
Creates a connection pool instance based on specified UCP Adapter.

[createConnectionPool(UniversalConnectionPoolAdapter)](../oracle/ucp/admin/UniversalConnectionPoolManagerMBean.md) - Method in interface oracle.ucp.admin.[UniversalConnectionPoolManagerMBean](../oracle/ucp/admin/UniversalConnectionPoolManagerMBean.md)
Creates a connection pool instance based on specified UCP Adapter.

[createPooledConnection(Object, ConnectionRetrievalInfo)](../oracle/ucp/ConnectionFactoryAdapter.md) - Method in interface oracle.ucp.[ConnectionFactoryAdapter](../oracle/ucp/ConnectionFactoryAdapter.md)
Creates a UniversalPooledConnection object.

[createPoolWithDefaultProperties()](../oracle/ucp/jdbc/PoolDataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolDataSourceImpl](../oracle/ucp/jdbc/PoolDataSourceImpl.md)
 

[createPoolWithDefaultProperties()](../oracle/ucp/jdbc/PoolXADataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolXADataSourceImpl](../oracle/ucp/jdbc/PoolXADataSourceImpl.md)
 

[createShardingKeyBuilder()](../oracle/ucp/jdbc/PoolDataSource.md) - Method in interface oracle.ucp.jdbc.[PoolDataSource](../oracle/ucp/jdbc/PoolDataSource.md)
Creates a new OracleShardingKeyBuilder instance

[createUniversalConnectionPool()](../oracle/ucp/jdbc/PoolDataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolDataSourceImpl](../oracle/ucp/jdbc/PoolDataSourceImpl.md)
Creates a Universal Connection Pool instance using this adapter.

[createUniversalConnectionPool()](../oracle/ucp/UniversalConnectionPoolAdapter.md) - Method in interface oracle.ucp.[UniversalConnectionPoolAdapter](../oracle/ucp/UniversalConnectionPoolAdapter.md)
Creates a Universal Connection Pool instance using this adapter.

[createUniversalConnectionPoolMBean()](../oracle/ucp/jdbc/PoolDataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolDataSourceImpl](../oracle/ucp/jdbc/PoolDataSourceImpl.md)
Creates a Universal Connection Pool MBean using this adapter.

[createUniversalConnectionPoolMBean()](../oracle/ucp/UniversalConnectionPoolAdapter.md) - Method in interface oracle.ucp.[UniversalConnectionPoolAdapter](../oracle/ucp/UniversalConnectionPoolAdapter.md)
Creates a Universal Connection Pool MBean using this adapter.

[createXAConnectionBuilder()](../oracle/ucp/jdbc/PoolXADataSource.md) - Method in interface oracle.ucp.jdbc.[PoolXADataSource](../oracle/ucp/jdbc/PoolXADataSource.md)
Creates a new XAConnectionBuilder instance.

[createXAConnectionBuilder()](../oracle/ucp/jdbc/PoolXADataSourceImpl.md) - Method in class oracle.ucp.jdbc.[PoolXADataSourceImpl](../oracle/ucp/jdbc/PoolXADataSourceImpl.md)
 

[A](index-1.md) [B](index-2.md) C [D](index-4.md) [E](index-5.md) [F](index-6.md) [G](index-7.md) [H](index-8.md) [I](index-9.md) [J](index-10.md) [L](index-11.md) [M](index-12.md) [N](index-13.md) [O](index-14.md) [P](index-15.md) [R](index-16.md) [S](index-17.md) [T](index-18.md) [U](index-19.md) [V](index-20.md) 

Skip navigation links

- [Overview](../overview-summary.md)
- Package
- Class
- Use
- [Tree](../overview-tree.md)
- [Deprecated](../deprecated-list.md)
- Index
- [Help](../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Letter](index-2.md)
- [Next Letter](index-4.md)

<!-- -->

- [Frames](../index.md)
- No Frames

<!-- -->

- [All Classes](../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
