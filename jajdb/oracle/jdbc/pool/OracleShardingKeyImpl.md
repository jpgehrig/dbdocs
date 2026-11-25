Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyBuilderImpl.md)
- [Next Class](ShardingMetadata.md)

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

## Class OracleShardingKeyImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OracleShardingKeyImpl

<!-- -->

- All Implemented Interfaces:
  [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<[OracleShardingKey](../OracleShardingKey.md)\>, [OracleShardingKey](../OracleShardingKey.md)

  ------------------------------------------------------------------------



      public class OracleShardingKeyImpl
      extends Object
      implements OracleShardingKey

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                             |
    |-------------|---------------------------------------------------------------------------------------------------------|
    | `protected` | `OracleShardingKeyImpl``(`[`OracleShardingKeyBuilderImpl`](OracleShardingKeyBuilderImpl.md)` builder)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                             | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                                                         | `compareTo``(`[`OracleShardingKey`](../OracleShardingKey.md)` o)`<br>Used to compare two OracleShardingKey keys.                                                                                                                                                                                                                                                                                                                                                             |
    | `protected void`                                                                                                              | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | `static `[`List`](http://download.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)`<OracleShardingKeyImpl>` | `decodeKeys``(`[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` keysData, `[`ShardingMetadata`](ShardingMetadata.md)` metadata, boolean isSuperKey, boolean isKeyHigh)`<br>Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS.                                                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                               | `encodeKeyinB64Format``()`<br>Encodes the sharding key as per the standard Base 64 format to be added into the connect string during connection creation.                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                                     | `equals``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` otherObj)`<br>Compares this ShardingKey with the specified Object for equality                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                                                         | `hashCode``()`<br>Returns the hashcode for this sharding key object.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                                     | `isSuperShardingKey``()`<br>Checks if the the key is a super sharding key                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                                     | `isValid``(`[`ShardingMetadata`](ShardingMetadata.md)` metadata)`<br>Checks if this sharding key is valid for the sharded database represented by the metadata                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                                        | `markSuperShardingKey``(boolean isSuperShardingKey)`<br>Marks the key to be used as a super sharding key                                                                                                                                                                                                                                                                                                                                                                     |
    | `long`                                                                                                                        | `shardKeyOraHash``(`[`ShardingMetadata`](ShardingMetadata.md)` metadata)`<br>Computes the hash value of the Sharding key as per Oracle's internal hash function.                                                                                                                                                                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                               | `toString``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                               | `toString``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                                                                                                                                                                                                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleShardingKeyImpl

          protected OracleShardingKeyImpl(OracleShardingKeyBuilderImpl builder)

  <!-- -->

  - ### Method Detail

    - #### markSuperShardingKey

          public void markSuperShardingKey(boolean isSuperShardingKey)

      Marks the key to be used as a super sharding key
      Parameters:
      `isSuperShardingKey` - if the key is to be used as a super sharding key

    <!-- -->

    - #### isSuperShardingKey

          public boolean isSuperShardingKey()

      Checks if the the key is a super sharding key
      Returns:
      true if the key is a super sharding key

    <!-- -->

    - #### compareTo

          public int compareTo(OracleShardingKey o)

      Used to compare two OracleShardingKey keys. If the sharding keys are compound the corresponding sub-keys in two keys are compared.
      Specified by:
      [`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true#compareTo_T_) in interface [`Comparable`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)`<`[`OracleShardingKey`](../OracleShardingKey.md)`>`

      Parameters:
      `o` - ShardingKey to which this sharding key is to be compared.

      Returns:
      -1, 0 or 1 as this ShardingKey is less than, equal to, or greater than the sharding key that is passed in as a method parameter

    <!-- -->

    - #### toString

          public String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      Comma separated string format of the sub keys that are a part of this Sharding Key

      See Also:
      [`Object.toString()`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)

    <!-- -->

    - #### toString

          public String toString(Connection conn)
                          throws SQLException

      Parameters:
      `conn` - to be used to get the string value if there is a subkey of type oracle.sql.TIMESTAMPLTZ

      Returns:
      Comma separated string format of the sub keys that are a part of this Sharding Key

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### equals

          public boolean equals(Object otherObj)

      Compares this ShardingKey with the specified Object for equality
      Overrides:
      [`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `otherObj` - Object to which this sharding key is to be compared.

      Returns:
      true if and only if the specified Object is a OracleSharding key whose value is equal to this sharding key object.

      See Also:
      [`Object.equals(java.lang.Object)`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hashcode for this sharding key object. For compound keys the hash code is computed considering hash codes of each of its sub key.
      Overrides:
      [`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      hashcode value for this sharding key

      See Also:
      [`Object.hashCode()`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)

    <!-- -->

    - #### encodeKeyinB64Format

          public String encodeKeyinB64Format()
                                      throws SQLException

      Encodes the sharding key as per the standard Base 64 format to be added into the connect string during connection creation.
      Parameters:
      `metadata` - Metadata of the sharded database which needs to be accessed. needed

      Returns:
      Base 64 encoded sharding key

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### shardKeyOraHash

          public long shardKeyOraHash(ShardingMetadata metadata)

      Computes the hash value of the Sharding key as per Oracle's internal hash function.
      Parameters:
      `metadata` - sharded database metadata

      Returns:
      the hash value of the Sharding key

    <!-- -->

    - #### isValid

          public boolean isValid(ShardingMetadata metadata)

      Checks if this sharding key is valid for the sharded database represented by the metadata
      Parameters:
      `metadata` - Sharded database metadata to be used during the validation of this key

      Returns:
      true if the key is valid and conforms to the metadata

    <!-- -->

    - #### decodeKeys

          public static List<OracleShardingKeyImpl> decodeKeys(InputStream keysData,
                                                               ShardingMetadata metadata,
                                                               boolean isSuperKey,
                                                               boolean isKeyHigh)
                                                        throws SQLException

      Builds a list of sharding keys from the key data available as input stream from the database sharding metadata table LOCAL_CHUNKS.
      Parameters:
      `keysData` - Input stream containing the byte value of key or list of keys stored in the database table local_chunks

      `metadata` - Contains the sharding metadata information that is used to build the keys.

      `isSuperKey` - true if the keys to be constructed are super sharding keys,false otherwise

      `isKeyHigh` - true if the sharding keys to be constructed indicate the higher boundary if the sharding type is RANGE based

      Returns:
      List of sharding keys built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while building the keys.

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyBuilderImpl.md)
- [Next Class](ShardingMetadata.md)

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
