Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKey.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleSavepoint.md)
- [Next Class](OracleShardingKeyBuilder.md)

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

## Interface OracleShardingKey

- All Superinterfaces:
  [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleShardingKey\>

  <!-- -->

  All Known Implementing Classes:
  [OracleShardingKeyImpl](pool/OracleShardingKeyImpl.md)

  ------------------------------------------------------------------------



      public interface OracleShardingKey
      extends Comparable<OracleShardingKey>

  Interface used to indicate that this object represents a Oracle Sharding Key. A `OracleShardingKey` instance is only guaranteed to be compatible with the oracle data source instance that it was derived from. A `OracleShardingKey` is created using [`OracleShardingKeyBuilder`](OracleShardingKeyBuilder.md).
  The following example illustrates the use of [`OracleShardingKeyBuilder`](OracleShardingKeyBuilder.md) to create a `OracleShardingKey`:


          OracleDataSource ods = new oracle.jdbc.pool.OracleDataSource();

          OracleShardingKey shardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("Customer_Name_XYZ", JDBCType.VARCHAR)
                 .subkey(94002, JDBCType.NUMERIC)
                 .build();



  A `OracleShardingKey` may also be used for specifying a `superShardingKey`. Databases that support composite Sharding may use a `superShardingKey` to specify a additional level of partitioning within the Shard.

  The following example illustrates the use of [`OracleShardingKeyBuilder`](OracleShardingKeyBuilder.md) to create a `superShardingKey` for an eastern region with a `OracleShardingKey` specified for the Pittsburgh branch office:


          OracleDataSource ods = new oracle.pool.OracleDataSource();
          OracleShardingKey superShardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("EASTERN_REGION", JDBCType.VARCHAR)
                 .build();
          OracleShardingKey shardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("PITTSBURGH_BRANCH", JDBCType.VARCHAR)
                 .build();
          OracleConnection conn = ods.createConnectionBuilder()
                                     .superShardingKey(superShardingKey)
                                     .shardingKey(shardingKey)
                                     .build();



  Since:
  12.2

<!-- -->

- - ### Method Summary

    - ### Methods inherited from interface java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)

      [`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true#compareTo_T_)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleShardingKey.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleSavepoint.md)
- [Next Class](OracleShardingKeyBuilder.md)

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
