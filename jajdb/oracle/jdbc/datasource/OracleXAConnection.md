Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnection.md)
- [Next Class](OracleXADataSource.md)

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

oracle.jdbc.datasource

## Interface OracleXAConnection

- All Superinterfaces:
  [OraclePooledConnection](OraclePooledConnection.md), [PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true), [XAConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [OracleXAConnection](../xa/OracleXAConnection.md), [OracleXAConnection](../xa/client/OracleXAConnection.md), [OracleXAHeteroConnection](../xa/client/OracleXAHeteroConnection.md)

  ------------------------------------------------------------------------



      public interface OracleXAConnection
      extends XAConnection, OraclePooledConnection

  This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    - ### Methods inherited from interface javax.sql.[XAConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true)

      [`getXAResource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true#getXAResource__)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OraclePooledConnection](OraclePooledConnection.md)

      [`getCallWithKey`](OraclePooledConnection.md)`, `[`getExplicitCachingEnabled`](OraclePooledConnection.md)`, `[`getImplicitCachingEnabled`](OraclePooledConnection.md)`, `[`getLastAccessedTime`](OraclePooledConnection.md)`, `[`getLogicalHandle`](OraclePooledConnection.md)`, `[`getStatementCacheSize`](OraclePooledConnection.md)`, `[`getStatementWithKey`](OraclePooledConnection.md)`, `[`getXAResource`](OraclePooledConnection.md)`, `[`purgeExplicitCache`](OraclePooledConnection.md)`, `[`purgeImplicitCache`](OraclePooledConnection.md)`, `[`registerCloseCallback`](OraclePooledConnection.md)`, `[`registerImplicitCacheConnectionEventListener`](OraclePooledConnection.md)`, `[`setExplicitCachingEnabled`](OraclePooledConnection.md)`, `[`setImplicitCachingEnabled`](OraclePooledConnection.md)`, `[`setLastAccessedTime`](OraclePooledConnection.md)`, `[`setShardingKey`](OraclePooledConnection.md)`, `[`setShardingKeyIfValid`](OraclePooledConnection.md)`, `[`setStatementCacheSize`](OraclePooledConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      [`addConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`addStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addStatementEventListener_javax_sql_StatementEventListener_)`, `[`close`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#close__)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#getConnection__)`, `[`removeConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`removeStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeStatementEventListener_javax_sql_StatementEventListener_)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnection.md)
- [Next Class](OracleXADataSource.md)

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
