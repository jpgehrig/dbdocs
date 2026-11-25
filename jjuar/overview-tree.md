Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- Tree
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

# Hierarchy For All Packages

Package Hierarchies:

- [oracle.ucp](oracle/ucp/package-tree.md),
- [oracle.ucp.admin](oracle/ucp/admin/package-tree.md),
- [oracle.ucp.jdbc](oracle/ucp/jdbc/package-tree.md),
- [oracle.ucp.jdbc.oracle](oracle/ucp/jdbc/oracle/package-tree.md),
- [oracle.ucp.util.logging](oracle/ucp/util/logging/package-tree.md)

## Class Hierarchy

- java.lang.Object
  - java.util.logging.Formatter
    - oracle.ucp.util.logging.[UCPFormatter](oracle/ucp/util/logging/UCPFormatter.md)
  - oracle.ucp.jdbc.[PoolDataSourceFactory](oracle/ucp/jdbc/PoolDataSourceFactory.md)
  - oracle.ucp.jdbc.[PoolDataSourceImpl](oracle/ucp/jdbc/PoolDataSourceImpl.md) (implements javax.naming.spi.ObjectFactory, oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md), javax.naming.Referenceable, java.io.Serializable, oracle.ucp.[UniversalConnectionPoolAdapter](oracle/ucp/UniversalConnectionPoolAdapter.md))
    - oracle.ucp.jdbc.[PoolXADataSourceImpl](oracle/ucp/jdbc/PoolXADataSourceImpl.md) (implements javax.naming.spi.ObjectFactory, oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md), javax.naming.Referenceable, java.io.Serializable, oracle.ucp.[UniversalConnectionPoolAdapter](oracle/ucp/UniversalConnectionPoolAdapter.md))
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.ucp.[UniversalConnectionPoolException](oracle/ucp/UniversalConnectionPoolException.md)
        - oracle.ucp.[NoAvailableConnectionsException](oracle/ucp/NoAvailableConnectionsException.md)
  - oracle.ucp.[UniversalConnectionPoolLifeCycleState](oracle/ucp/UniversalConnectionPoolLifeCycleState.md)
  - oracle.ucp.admin.UniversalConnectionPoolManagerBase (implements oracle.ucp.admin.[UniversalConnectionPoolManager](oracle/ucp/admin/UniversalConnectionPoolManager.md))
    - oracle.ucp.admin.[UniversalConnectionPoolManagerImpl](oracle/ucp/admin/UniversalConnectionPoolManagerImpl.md)
  - oracle.ucp.[UniversalPooledConnectionStatus](oracle/ucp/UniversalPooledConnectionStatus.md)

## Interface Hierarchy

- oracle.ucp.[AbandonedConnectionTimeoutCallback](oracle/ucp/AbandonedConnectionTimeoutCallback.md)
- java.lang.AutoCloseable
  - java.io.Closeable
    - oracle.ucp.[UniversalPooledConnection](oracle/ucp/UniversalPooledConnection.md)
  - oracle.ucp.[UniversalPooledConnection](oracle/ucp/UniversalPooledConnection.md)
- javax.sql.CommonDataSource
  - javax.sql.DataSource (also extends java.sql.Wrapper)
    - oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md)
      - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends javax.sql.XADataSource)
    - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md), javax.sql.XADataSource)
  - oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md)
    - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends javax.sql.XADataSource)
  - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md), javax.sql.XADataSource)
  - javax.sql.XADataSource
    - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md))
- oracle.ucp.[ConnectionAffinityCallback](oracle/ucp/ConnectionAffinityCallback.md)
- oracle.ucp.[ConnectionFactoryAdapter](oracle/ucp/ConnectionFactoryAdapter.md)
- oracle.ucp.[ConnectionHarvestingCallback](oracle/ucp/ConnectionHarvestingCallback.md)
- oracle.ucp.jdbc.[ConnectionInitializationCallback](oracle/ucp/jdbc/ConnectionInitializationCallback.md)
- oracle.ucp.[ConnectionLabelingCallback](oracle/ucp/ConnectionLabelingCallback.md)
  - oracle.ucp.jdbc.[ConnectionLabelingCallback](oracle/ucp/jdbc/ConnectionLabelingCallback.md)
- oracle.ucp.[ConnectionRetrievalInfo](oracle/ucp/ConnectionRetrievalInfo.md)
- oracle.ucp.jdbc.[ConnectionWithAbandonedTimeout](oracle/ucp/jdbc/ConnectionWithAbandonedTimeout.md)
- oracle.ucp.jdbc.[ConnectionWithTimeToLiveTimeout](oracle/ucp/jdbc/ConnectionWithTimeToLiveTimeout.md)
- oracle.ucp.jdbc.[HarvestableConnection](oracle/ucp/jdbc/HarvestableConnection.md)
- oracle.ucp.jdbc.[LabelableConnection](oracle/ucp/jdbc/LabelableConnection.md)
- oracle.ucp.[TimeToLiveConnectionTimeoutCallback](oracle/ucp/TimeToLiveConnectionTimeoutCallback.md)
- oracle.ucp.jdbc.[UCPConnectionBuilder](oracle/ucp/jdbc/UCPConnectionBuilder.md)
- oracle.ucp.jdbc.[UCPXAConnectionBuilder](oracle/ucp/jdbc/UCPXAConnectionBuilder.md)
- oracle.ucp.[UniversalConnectionPool](oracle/ucp/UniversalConnectionPool.md)
- oracle.ucp.[UniversalConnectionPoolAdapter](oracle/ucp/UniversalConnectionPoolAdapter.md)
- oracle.ucp.admin.[UniversalConnectionPoolManager](oracle/ucp/admin/UniversalConnectionPoolManager.md)
- oracle.ucp.admin.[UniversalConnectionPoolManagerMBean](oracle/ucp/admin/UniversalConnectionPoolManagerMBean.md)
- oracle.ucp.admin.[UniversalConnectionPoolMBean](oracle/ucp/admin/UniversalConnectionPoolMBean.md)
- oracle.ucp.[UniversalConnectionPoolStatistics](oracle/ucp/UniversalConnectionPoolStatistics.md)
  - oracle.ucp.jdbc.[JDBCConnectionPoolStatistics](oracle/ucp/jdbc/JDBCConnectionPoolStatistics.md)
    - oracle.ucp.jdbc.oracle.[OracleJDBCConnectionPoolStatistics](oracle/ucp/jdbc/oracle/OracleJDBCConnectionPoolStatistics.md)
  - oracle.ucp.jdbc.oracle.[OracleJDBCConnectionPoolStatistics](oracle/ucp/jdbc/oracle/OracleJDBCConnectionPoolStatistics.md)
- oracle.ucp.jdbc.[ValidConnection](oracle/ucp/jdbc/ValidConnection.md)
- java.sql.Wrapper
  - javax.sql.DataSource (also extends javax.sql.CommonDataSource)
    - oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md)
      - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends javax.sql.XADataSource)
    - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md), javax.sql.XADataSource)
  - oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md)
    - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends javax.sql.XADataSource)
  - oracle.ucp.jdbc.[PoolXADataSource](oracle/ucp/jdbc/PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](oracle/ucp/jdbc/PoolDataSource.md), javax.sql.XADataSource)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.ucp.[ConnectionAffinityCallback.AffinityPolicy](oracle/ucp/ConnectionAffinityCallback.AffinityPolicy.md)

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- Tree
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
