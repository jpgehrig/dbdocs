Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ShardingMetadata.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyImpl.md)
- [Next Class](ShardingMetadata.ShardingType.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.pool

## Class ShardingMetadata

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.ShardingMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class ShardingMetadata
      extends Object

  Holds the Sharded Database metadata that is required during encoding and decoding of sharding keys. The metadata is normally populated after the first connection to the database is established. The metadata object is designed to be immutable once created.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`ShardingMetadata.ShardingType`](ShardingMetadata.ShardingType.md)<br>Enum to hold the different sharding methods supported for shard keys and shard groups in the Oracle sharded database. |
    | `static class `   | [`ShardingMetadata.SubKeyMetadata`](ShardingMetadata.SubKeyMetadata.md)<br>Holds the shard sub key metadata information extracted from the database.                                         |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description       |
    |-------------------|-----------------------------|
    | `static int`      | `SHARDING_KEY_LEVEL`        |
    | `static int`      | `SUPER_SHARDING_KEY_LEVEL`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ShardingMetadata``(int version, `[`ShardingMetadata.ShardingType`](ShardingMetadata.ShardingType.md)` shardingType, `[`ShardingMetadata.ShardingType`](ShardingMetadata.ShardingType.md)` superShardingType, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](ShardingMetadata.SubKeyMetadata.md)`> keyColumns, `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](ShardingMetadata.SubKeyMetadata.md)`> superKeyColumns)`<br>Constructs an immutable object with all the metadata information. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                        | Method and Description            |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](ShardingMetadata.SubKeyMetadata.md)`>` | `getShardingKeyColumns``()`       |
    | [`ShardingMetadata.ShardingType`](ShardingMetadata.ShardingType.md)                                                                                                      | `getShardingType``()`             |
    | [`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<`[`ShardingMetadata.SubKeyMetadata`](ShardingMetadata.SubKeyMetadata.md)`>` | `getSuperShardingKeyColumns``()`  |
    | [`ShardingMetadata.ShardingType`](ShardingMetadata.ShardingType.md)                                                                                                      | `getSuperShardingType``()`        |
    | `int`                                                                                                                                                                    | `getVersion``()`                  |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### SUPER_SHARDING_KEY_LEVEL

          public static final int SUPER_SHARDING_KEY_LEVEL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SHARDING_KEY_LEVEL

          public static final int SHARDING_KEY_LEVEL

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ShardingMetadata

          public ShardingMetadata(int version,
                                  ShardingMetadata.ShardingType shardingType,
                                  ShardingMetadata.ShardingType superShardingType,
                                  List<ShardingMetadata.SubKeyMetadata> keyColumns,
                                  List<ShardingMetadata.SubKeyMetadata> superKeyColumns)

      Constructs an immutable object with all the metadata information.
      Parameters:
      `version` - version of the metadata object being built

      `shardingType` - sharding type in the database

      `superShardingType` - super sharding type in the database

      `keyColumns` - sub key column metadata for sharding sub keys on the database

      `superKeyColumns` - sub key column metadata for sub keys of the super sharding key on the database

  <!-- -->

  - ### Method Detail

    - #### getVersion

          public int getVersion()

      Returns:
      version of this metadata

    <!-- -->

    - #### getShardingType

          public ShardingMetadata.ShardingType getShardingType()

      Returns:
      sharding type in the metadata

    <!-- -->

    - #### getSuperShardingType

          public ShardingMetadata.ShardingType getSuperShardingType()

      Returns:
      super sharding type in the metadata

    <!-- -->

    - #### getShardingKeyColumns

          public List<ShardingMetadata.SubKeyMetadata> getShardingKeyColumns()

      Returns:
      list of sharding sub key column metadata

    <!-- -->

    - #### getSuperShardingKeyColumns

          public List<ShardingMetadata.SubKeyMetadata> getSuperShardingKeyColumns()

      Returns:
      list of super sharding sub key columns metadata

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ShardingMetadata.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyImpl.md)
- [Next Class](ShardingMetadata.ShardingType.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
