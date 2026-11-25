Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev](../admin/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.ucp.jdbc

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.ucp.jdbc.[PoolDataSourceFactory](PoolDataSourceFactory.md)
  - oracle.ucp.jdbc.[PoolDataSourceImpl](PoolDataSourceImpl.md) (implements javax.naming.spi.ObjectFactory, oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md), javax.naming.Referenceable, java.io.Serializable, oracle.ucp.[UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md))
    - oracle.ucp.jdbc.[PoolXADataSourceImpl](PoolXADataSourceImpl.md) (implements javax.naming.spi.ObjectFactory, oracle.ucp.jdbc.[PoolXADataSource](PoolXADataSource.md), javax.naming.Referenceable, java.io.Serializable, oracle.ucp.[UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md))

## Interface Hierarchy

- javax.sql.CommonDataSource
  - javax.sql.DataSource (also extends java.sql.Wrapper)
    - oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)
      - oracle.ucp.jdbc.[PoolXADataSource](PoolXADataSource.md) (also extends javax.sql.XADataSource)
  - javax.sql.XADataSource
    - oracle.ucp.jdbc.[PoolXADataSource](PoolXADataSource.md) (also extends oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md))
- oracle.ucp.jdbc.[ConnectionInitializationCallback](ConnectionInitializationCallback.md)
- oracle.ucp.[ConnectionLabelingCallback](../ConnectionLabelingCallback.md)
  - oracle.ucp.jdbc.[ConnectionLabelingCallback](ConnectionLabelingCallback.md)
- oracle.ucp.jdbc.[ConnectionWithAbandonedTimeout](ConnectionWithAbandonedTimeout.md)
- oracle.ucp.jdbc.[ConnectionWithTimeToLiveTimeout](ConnectionWithTimeToLiveTimeout.md)
- oracle.ucp.jdbc.[HarvestableConnection](HarvestableConnection.md)
- oracle.ucp.jdbc.[LabelableConnection](LabelableConnection.md)
- oracle.ucp.jdbc.[UCPConnectionBuilder](UCPConnectionBuilder.md)
- oracle.ucp.jdbc.[UCPXAConnectionBuilder](UCPXAConnectionBuilder.md)
- oracle.ucp.[UniversalConnectionPoolStatistics](../UniversalConnectionPoolStatistics.md)
  - oracle.ucp.jdbc.[JDBCConnectionPoolStatistics](JDBCConnectionPoolStatistics.md)
- oracle.ucp.jdbc.[ValidConnection](ValidConnection.md)
- java.sql.Wrapper
  - javax.sql.DataSource (also extends javax.sql.CommonDataSource)
    - oracle.ucp.jdbc.[PoolDataSource](PoolDataSource.md)
      - oracle.ucp.jdbc.[PoolXADataSource](PoolXADataSource.md) (also extends javax.sql.XADataSource)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev](../admin/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
