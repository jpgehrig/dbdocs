Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnectionBuilderImpl.md)
- [Next Class](OracleShardingKeyImpl.md)

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

## Class OracleShardingKeyBuilderImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OracleShardingKeyBuilderImpl

<!-- -->

- All Implemented Interfaces:
  [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md)

  ------------------------------------------------------------------------



      public class OracleShardingKeyBuilderImpl
      extends Object
      implements OracleShardingKeyBuilder

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description         |
    |-------------------------------------|
    | `OracleShardingKeyBuilderImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                   |
    |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleShardingKeyImpl`](OracleShardingKeyImpl.md) | `build``()`<br>Builds the sharding key with the sub keys provided and their default metadata.                                                                                                                                                                                                                            |
    | `OracleShardingKeyBuilderImpl`                      | `oraHash``(long oraHash)`<br>Used to build the shard key with the known ORA HASH value.                                                                                                                                                                                                                                  |
    | `OracleShardingKeyBuilderImpl`                      | `subkey``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` subkey, `[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` subkeyType)`<br>This method is called to include a subkey into a sharding key object being built. |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleShardingKeyBuilderImpl

          public OracleShardingKeyBuilderImpl()

  <!-- -->

  - ### Method Detail

    - #### subkey

          public OracleShardingKeyBuilderImpl subkey(Object subkey,
                                                     SQLType subkeyType)

      This method is called to include a subkey into a sharding key object being built. The order in which subkey method is called is important as it indicates the order of placement of the subkey within the sharding key.
      Specified by:
      [`subkey`](../OracleShardingKeyBuilder.md) in interface [`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md)

      Parameters:
      `subkey` - contains the object that needs to be part of sharding sub key

      `subkeyType` - sub-key data type which can be specified using one of the types from java.sql.JDBCType or oracle.jdbc.OracleType

      Returns:
      this builder object

      See Also:
      [`OracleShardingKeyBuilder.subkey(java.lang.Object, java.sql.SQLType)`](../OracleShardingKeyBuilder.md)

    <!-- -->

    - #### oraHash

          public OracleShardingKeyBuilderImpl oraHash(long oraHash)

      Used to build the shard key with the known ORA HASH value. This is used to optimize sharding key comparisons for hash based sharding.
      Parameters:
      `oraHash` - the known ORA HASH value for the shard key that is being built.

      Returns:
      this builder object

    <!-- -->

    - #### build

          public OracleShardingKeyImpl build()

      Builds the sharding key with the sub keys provided and their default metadata. The sharding key object built is immutable. The build() method can be called only once on a builder object, subsequent attempts to call build() will result in IllegalStateException.
      Specified by:
      [`build`](../OracleShardingKeyBuilder.md) in interface [`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md)

      Returns:
      returns the new sharding key object that is built

      See Also:
      [`OracleShardingKeyBuilder.build()`](../OracleShardingKeyBuilder.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnectionBuilderImpl.md)
- [Next Class](OracleShardingKeyImpl.md)

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
