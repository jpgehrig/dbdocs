Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ShardingMetadata.SubKeyMetadata.md)
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

## Uses of Class oracle.jdbc.pool.ShardingMetadata.SubKeyMetadata

- **Packages that use [ShardingMetadata.SubKeyMetadata](../ShardingMetadata.SubKeyMetadata.md)**

  | Package          | Description                                                |
  |------------------|------------------------------------------------------------|
  | oracle.jdbc.pool | A package of connection cache and pooling related classes. |

- - ### Uses of [ShardingMetadata.SubKeyMetadata](../ShardingMetadata.SubKeyMetadata.md) in [oracle.jdbc.pool](../package-summary.md)

    **Methods in [oracle.jdbc.pool](../package-summary.md) that return types with arguments of type [ShardingMetadata.SubKeyMetadata](../ShardingMetadata.SubKeyMetadata.md)**

    | Modifier and Type                                                                                                                                                           | Method and Description                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`>` | ShardingMetadata.[`getShardingKeyColumns`](../ShardingMetadata.md)`()`       |
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`>` | ShardingMetadata.[`getShardingKeyColumns`](../ShardingMetadata.md)`()`       |
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`>` | ShardingMetadata.[`getSuperShardingKeyColumns`](../ShardingMetadata.md)`()`  |
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`>` | ShardingMetadata.[`getSuperShardingKeyColumns`](../ShardingMetadata.md)`()`  |

    **Methods in [oracle.jdbc.pool](../package-summary.md) with parameters of type [ShardingMetadata.SubKeyMetadata](../ShardingMetadata.SubKeyMetadata.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                   |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | ShardingMetadata.SubKeyMetadata.[`compareTo`](../ShardingMetadata.SubKeyMetadata.md)`(`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)` o)`<br>Method used to defined natural ordering for the sub key column info based on the column index. |
    | `int`             | ShardingMetadata.SubKeyMetadata.[`compareTo`](../ShardingMetadata.SubKeyMetadata.md)`(`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)` o)`<br>Method used to defined natural ordering for the sub key column info based on the column index. |

    **Constructor parameters in [oracle.jdbc.pool](../package-summary.md) with type arguments of type [ShardingMetadata.SubKeyMetadata](../ShardingMetadata.SubKeyMetadata.md)**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ShardingMetadata`](../ShardingMetadata.md)`(int version, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` shardingType, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` superShardingType, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> keyColumns, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> superKeyColumns)`<br>Constructs an immutable object with all the metadata information. |
    | [`ShardingMetadata`](../ShardingMetadata.md)`(int version, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` shardingType, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` superShardingType, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> keyColumns, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> superKeyColumns)`<br>Constructs an immutable object with all the metadata information. |
    | [`ShardingMetadata`](../ShardingMetadata.md)`(int version, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` shardingType, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` superShardingType, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> keyColumns, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> superKeyColumns)`<br>Constructs an immutable object with all the metadata information. |
    | [`ShardingMetadata`](../ShardingMetadata.md)`(int version, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` shardingType, `[`ShardingMetadata.ShardingType`](../ShardingMetadata.ShardingType.md)` superShardingType, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> keyColumns, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](../ShardingMetadata.SubKeyMetadata.md)`> superKeyColumns)`<br>Constructs an immutable object with all the metadata information. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ShardingMetadata.SubKeyMetadata.md)
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
