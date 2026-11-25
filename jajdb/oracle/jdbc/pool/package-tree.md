Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev](../dcn/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.jdbc.pool

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - oracle.jdbc.pool.[OracleConnectionBuilderImpl](OracleConnectionBuilderImpl.md) (implements oracle.jdbc.[OracleConnectionBuilder](../OracleConnectionBuilder.md))
  - oracle.jdbc.pool.[OracleConnectionCacheManager](OracleConnectionCacheManager.md)
  - oracle.jdbc.pool.[OracleDataSource](OracleDataSource.md) (implements oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md), javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.pool.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (implements oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md))
    - oracle.jdbc.pool.[OracleOCIConnectionPool](OracleOCIConnectionPool.md)
  - oracle.jdbc.pool.[OracleDataSourceFactory](OracleDataSourceFactory.md) (implements javax.naming.spi.[ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true))
  - oracle.jdbc.pool.[OraclePooledConnection](OraclePooledConnection.md) (implements oracle.jdbc.datasource.[OraclePooledConnection](../datasource/OraclePooledConnection.md), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - oracle.jdbc.pool.[OraclePooledConnectionBuilderImpl](OraclePooledConnectionBuilderImpl.md) (implements oracle.jdbc.[OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md))
  - oracle.jdbc.pool.[OracleShardingKeyBuilderImpl](OracleShardingKeyBuilderImpl.md) (implements oracle.jdbc.[OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md))
  - oracle.jdbc.pool.[OracleShardingKeyImpl](OracleShardingKeyImpl.md) (implements oracle.jdbc.[OracleShardingKey](../OracleShardingKey.md))
  - oracle.jdbc.pool.[ShardingMetadata](ShardingMetadata.md)
  - oracle.jdbc.pool.[ShardingMetadata.SubKeyMetadata](ShardingMetadata.SubKeyMetadata.md) (implements java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<T\>)

## Interface Hierarchy

- javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)
  - javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true) (also extends java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true))
    - oracle.jdbc.pool.[OracleConnectionCache](OracleConnectionCache.md)
- oracle.jdbc.pool.[OracleConnectionCacheCallback](OracleConnectionCacheCallback.md)
- java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)
  - javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true) (also extends javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true))
    - oracle.jdbc.pool.[OracleConnectionCache](OracleConnectionCache.md)

## Enum Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<E\> (implements java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<T\>, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.pool.[ShardingMetadata.ShardingType](ShardingMetadata.ShardingType.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev](../dcn/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
