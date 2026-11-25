Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKey.md)
- [Next Class](OracleSQLPermission.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.jdbc

## Interface OracleShardingKeyBuilder

- All Known Implementing Classes:
  [OracleShardingKeyBuilderImpl](pool/OracleShardingKeyBuilderImpl.md)

  ------------------------------------------------------------------------



      public interface OracleShardingKeyBuilder

  A builder created from a `OracleDataSource` or `OracleXADataSource` or `OracleConnectionPoolDataSource` object, used to create a [`OracleShardingKey`](OracleShardingKey.md) with sub-keys of supported data types.
  The following example illustrates the use of `OracleShardingKeyBuilder` to create a [`OracleShardingKey`](OracleShardingKey.md):


          OracleDataSource ods = new oracle.jdbc.pool.OracleDataSource();

          OracleShardingKey shardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("Customer_Name_XYZ", JDBCType.VARCHAR)
                 .subkey(94002, JDBCType.NUMERIC)
                 .build();



  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                                                                                                                                |
    |---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleShardingKey`](OracleShardingKey.md) | `build``()`<br>Builds the Sharding key.                                                                                                                                                                                                                                                                               |
    | `OracleShardingKeyBuilder`                  | `subkey``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` key, `[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` subkeyType)`<br>This method is called to include a subkey into a sharding Key object being built. |

<!-- -->

- - ### Method Detail

    - #### subkey

          OracleShardingKeyBuilder subkey(Object key,
                                          SQLType subkeyType)

      This method is called to include a subkey into a sharding Key object being built. The order in which subkey method is called is important as it indicates the order of placement of the subkey within the sharding key.
      Parameters:
      `key` - contains the sharding sub-key object.

      `subkeyType` - sharding sub-key data type.

      Returns:
      this `OracleShardingKeyBuilder` object

    <!-- -->

    - #### build

          OracleShardingKey build()
                           throws SQLException

      Builds the Sharding key.
      Returns:
      new `OracleShardingKey` object that is built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error while building the Sharding key.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKeyBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKey.md)
- [Next Class](OracleSQLPermission.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
