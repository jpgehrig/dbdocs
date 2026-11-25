Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../dcn/package-summary.md)
- [Next Package](../replay/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.pool

A package of connection cache and pooling related classes.

See: Description

- **Interface Summary**

  | Interface                                                         | Description                                                                                                                                                                |
  |-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleConnectionCache](OracleConnectionCache.md)                 | An OracleConnectionCache is an interface one needs to implement if they like to reuse OracleConnectionEventListener and implement their own version of Connection Caching. |
  | [OracleConnectionCacheCallback](OracleConnectionCacheCallback.md) | Deprecated<br>Use Oracle Universal Connection Pool instead.                                                                                                                |

- **Class Summary**

  | Class                                                                     | Description                                                                                                 |
  |---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
  | [OracleConnectionBuilderImpl](OracleConnectionBuilderImpl.md)             | Oracle Implementation class for Connection Builder                                                          |
  | [OracleConnectionCacheManager](OracleConnectionCacheManager.md)           | Deprecated<br>Use Oracle Universal Connection Pool instead.                                                 |
  | [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md)       | A DataSource object is a factory for Connection objects.                                                    |
  | [OracleDataSource](OracleDataSource.md)                                   | A DataSource object is a factory for Connection objects.                                                    |
  | [OracleDataSourceFactory](OracleDataSourceFactory.md)                     | A factory for creating an Oracle datasource.                                                                |
  | [OracleOCIConnectionPool](OracleOCIConnectionPool.md)                     | A type-2 driver connection pool.                                                                            |
  | [OraclePooledConnection](OraclePooledConnection.md)                       | An OraclePooledConnection object is a connection object that provides hooks for connection pool management. |
  | [OraclePooledConnectionBuilderImpl](OraclePooledConnectionBuilderImpl.md) | Oracle Implementation class for Connection Builder                                                          |
  | [OracleShardingKeyBuilderImpl](OracleShardingKeyBuilderImpl.md)           |                                                                                                             |
  | [OracleShardingKeyImpl](OracleShardingKeyImpl.md)                         |                                                                                                             |
  | [ShardingMetadata](ShardingMetadata.md)                                   | Holds the Sharded Database metadata that is required during encoding and decoding of sharding keys.         |
  | [ShardingMetadata.SubKeyMetadata](ShardingMetadata.SubKeyMetadata.md)     | Holds the shard sub key metadata information extracted from the database.                                   |

- **Enum Summary**

  | Enum                                                              | Description                                                                                                           |
  |-------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
  | [ShardingMetadata.ShardingType](ShardingMetadata.ShardingType.md) | Enum to hold the different sharding methods supported for shard keys and shard groups in the Oracle sharded database. |

## Package oracle.jdbc.pool Description

A package of connection cache and pooling related classes.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../dcn/package-summary.md)
- [Next Package](../replay/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
