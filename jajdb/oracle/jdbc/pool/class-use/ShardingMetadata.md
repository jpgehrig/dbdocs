Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ShardingMetadata.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Class oracle.jdbc.pool.ShardingMetadata

- **Packages that use [ShardingMetadata](../ShardingMetadata.md)**

  | Package          | Description                                                |
  |------------------|------------------------------------------------------------|
  | oracle.jdbc.pool | A package of connection cache and pooling related classes. |

- - ### Uses of [ShardingMetadata](../ShardingMetadata.md) in [oracle.jdbc.pool](../package-summary.md)

    **Methods in [oracle.jdbc.pool](../package-summary.md) with parameters of type [ShardingMetadata](../ShardingMetadata.md)**

    | Modifier and Type                                                                                                                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md)`>` | OracleShardingKeyImpl.[`decodeKeys`](../OracleShardingKeyImpl.md)`(`[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` keysData, `[`ShardingMetadata`](../ShardingMetadata.md)` metadata, boolean isSuperKey, boolean isKeyHigh)`<br>Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS. |
    | `static `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md)`>` | OracleShardingKeyImpl.[`decodeKeys`](../OracleShardingKeyImpl.md)`(`[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` keysData, `[`ShardingMetadata`](../ShardingMetadata.md)` metadata, boolean isSuperKey, boolean isKeyHigh)`<br>Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS. |
    | `boolean`                                                                                                                                                        | OracleShardingKeyImpl.[`isValid`](../OracleShardingKeyImpl.md)`(`[`ShardingMetadata`](../ShardingMetadata.md)` metadata)`<br>Checks if this sharding key is valid for the sharded database represented by the metadata                                                                                                                                                                                                        |
    | `boolean`                                                                                                                                                        | OracleShardingKeyImpl.[`isValid`](../OracleShardingKeyImpl.md)`(`[`ShardingMetadata`](../ShardingMetadata.md)` metadata)`<br>Checks if this sharding key is valid for the sharded database represented by the metadata                                                                                                                                                                                                        |
    | `long`                                                                                                                                                           | OracleShardingKeyImpl.[`shardKeyOraHash`](../OracleShardingKeyImpl.md)`(`[`ShardingMetadata`](../ShardingMetadata.md)` metadata)`<br>Computes the hash value of the Sharding key as per Oracle's internal hash function.                                                                                                                                                                                                      |
    | `long`                                                                                                                                                           | OracleShardingKeyImpl.[`shardKeyOraHash`](../OracleShardingKeyImpl.md)`(`[`ShardingMetadata`](../ShardingMetadata.md)` metadata)`<br>Computes the hash value of the Sharding key as per Oracle's internal hash function.                                                                                                                                                                                                      |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ShardingMetadata.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
