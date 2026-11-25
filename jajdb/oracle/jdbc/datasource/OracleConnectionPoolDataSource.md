Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionPoolDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleCommonDataSource.md)
- [Next Class](OracleDataSource.md)

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

## Interface OracleConnectionPoolDataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true), [OracleCommonDataSource](OracleCommonDataSource.md)

  <!-- -->

  All Known Subinterfaces:
  [OracleConnectionPoolDataSource](../replay/OracleConnectionPoolDataSource.md), [OracleXADataSource](../replay/OracleXADataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [OracleConnectionPoolDataSource](../pool/OracleConnectionPoolDataSource.md), [OracleConnectionPoolDataSourceImpl](../replay/OracleConnectionPoolDataSourceImpl.md), [OracleXADataSource](../xa/OracleXADataSource.md), [OracleXADataSource](../xa/client/OracleXADataSource.md), [OracleXADataSourceImpl](../replay/OracleXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface OracleConnectionPoolDataSource
      extends ConnectionPoolDataSource, OracleCommonDataSource

  This interface defines the Oracle extensions to the standard JDBC interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                      | Method and Description                                                                        |
    |------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | `createPooledConnectionBuilder``()`<br>Creates a new `OraclePooledConnectionBuilder` instance |

    - ### Methods inherited from interface javax.sql.[ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true)

      [`getPooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true#getPooledConnection__)`, `[`getPooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true#getPooledConnection_java_lang_String_java_lang_String_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](OracleCommonDataSource.md)`, `[`getConnectionProperties`](OracleCommonDataSource.md)`, `[`getDatabaseName`](OracleCommonDataSource.md)`, `[`getDataSourceName`](OracleCommonDataSource.md)`, `[`getDescription`](OracleCommonDataSource.md)`, `[`getExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getMaxStatements`](OracleCommonDataSource.md)`, `[`getNetworkProtocol`](OracleCommonDataSource.md)`, `[`getPortNumber`](OracleCommonDataSource.md)`, `[`getRoleName`](OracleCommonDataSource.md)`, `[`getServerName`](OracleCommonDataSource.md)`, `[`getURL`](OracleCommonDataSource.md)`, `[`getUser`](OracleCommonDataSource.md)`, `[`setConnectionProperties`](OracleCommonDataSource.md)`, `[`setDatabaseName`](OracleCommonDataSource.md)`, `[`setDataSourceName`](OracleCommonDataSource.md)`, `[`setDescription`](OracleCommonDataSource.md)`, `[`setExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setMaxStatements`](OracleCommonDataSource.md)`, `[`setNetworkProtocol`](OracleCommonDataSource.md)`, `[`setPassword`](OracleCommonDataSource.md)`, `[`setPortNumber`](OracleCommonDataSource.md)`, `[`setRoleName`](OracleCommonDataSource.md)`, `[`setServerName`](OracleCommonDataSource.md)`, `[`setSSLContext`](OracleCommonDataSource.md)`, `[`setTokenSupplier`](OracleCommonDataSource.md)`, `[`setURL`](OracleCommonDataSource.md)`, `[`setUser`](OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Method Detail

    - #### createPooledConnectionBuilder

          OraclePooledConnectionBuilder createPooledConnectionBuilder()
                                                               throws SQLException

      Creates a new `OraclePooledConnectionBuilder` instance
      Returns:
      The `OraclePooledConnectionBuilder` instance that was created

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while creating the builder

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionPoolDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleCommonDataSource.md)
- [Next Class](OracleDataSource.md)

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
