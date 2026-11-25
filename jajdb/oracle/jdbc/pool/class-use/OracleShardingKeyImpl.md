Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKeyImpl.md)
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

## Uses of Class oracle.jdbc.pool.OracleShardingKeyImpl

- **Packages that use [OracleShardingKeyImpl](../OracleShardingKeyImpl.md)**

  | Package          | Description                                                |
  |------------------|------------------------------------------------------------|
  | oracle.jdbc.pool | A package of connection cache and pooling related classes. |
  | oracle.jdbc.xa   | Provides classes that implement the JDBC XA APIs.          |

- - ### Uses of [OracleShardingKeyImpl](../OracleShardingKeyImpl.md) in [oracle.jdbc.pool](../package-summary.md)

    **Methods in [oracle.jdbc.pool](../package-summary.md) that return [OracleShardingKeyImpl](../OracleShardingKeyImpl.md)**

    | Modifier and Type                                      | Method and Description                                                                                                                                           |
    |--------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleShardingKeyBuilderImpl.[`build`](../OracleShardingKeyBuilderImpl.md)`()`<br>Builds the sharding key with the sub keys provided and their default metadata. |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleShardingKeyBuilderImpl.[`build`](../OracleShardingKeyBuilderImpl.md)`()`<br>Builds the sharding key with the sub keys provided and their default metadata. |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleConnectionBuilderImpl.[`getShardingKey`](../OracleConnectionBuilderImpl.md)`()`                                                                            |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OraclePooledConnectionBuilderImpl.[`getShardingKey`](../OraclePooledConnectionBuilderImpl.md)`()`                                                                |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OraclePooledConnectionBuilderImpl.[`getShardingKey`](../OraclePooledConnectionBuilderImpl.md)`()`                                                                |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleConnectionBuilderImpl.[`getShardingKey`](../OracleConnectionBuilderImpl.md)`()`                                                                            |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleConnectionBuilderImpl.[`getSuperShardingKey`](../OracleConnectionBuilderImpl.md)`()`                                                                       |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OraclePooledConnectionBuilderImpl.[`getSuperShardingKey`](../OraclePooledConnectionBuilderImpl.md)`()`                                                           |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OraclePooledConnectionBuilderImpl.[`getSuperShardingKey`](../OraclePooledConnectionBuilderImpl.md)`()`                                                           |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleConnectionBuilderImpl.[`getSuperShardingKey`](../OracleConnectionBuilderImpl.md)`()`                                                                       |

    **Methods in [oracle.jdbc.pool](../package-summary.md) that return types with arguments of type [OracleShardingKeyImpl](../OracleShardingKeyImpl.md)**

    | Modifier and Type                                                                                                                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md)`>` | OracleShardingKeyImpl.[`decodeKeys`](../OracleShardingKeyImpl.md)`(`[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` keysData, `[`ShardingMetadata`](../ShardingMetadata.md)` metadata, boolean isSuperKey, boolean isKeyHigh)`<br>Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS. |
    | `static `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md)`>` | OracleShardingKeyImpl.[`decodeKeys`](../OracleShardingKeyImpl.md)`(`[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` keysData, `[`ShardingMetadata`](../ShardingMetadata.md)` metadata, boolean isSuperKey, boolean isKeyHigh)`<br>Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS. |

  - ### Uses of [OracleShardingKeyImpl](../OracleShardingKeyImpl.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Methods in [oracle.jdbc.xa](../../xa/package-summary.md) that return [OracleShardingKeyImpl](../OracleShardingKeyImpl.md)**

    | Modifier and Type                                      | Method and Description                                                                                |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleXAConnectionBuilderImpl.[`getShardingKey`](../../xa/OracleXAConnectionBuilderImpl.md)`()`       |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleXAConnectionBuilderImpl.[`getShardingKey`](../../xa/OracleXAConnectionBuilderImpl.md)`()`       |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleXAConnectionBuilderImpl.[`getSuperShardingKey`](../../xa/OracleXAConnectionBuilderImpl.md)`()`  |
    | [`OracleShardingKeyImpl`](../OracleShardingKeyImpl.md) | OracleXAConnectionBuilderImpl.[`getSuperShardingKey`](../../xa/OracleXAConnectionBuilderImpl.md)`()`  |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKeyImpl.md)
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
