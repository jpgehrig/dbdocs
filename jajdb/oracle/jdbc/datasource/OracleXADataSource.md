Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
- Next Class

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

## Interface OracleXADataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [OracleCommonDataSource](OracleCommonDataSource.md), [XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleXADataSource](../replay/OracleXADataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [OracleXADataSource](../xa/OracleXADataSource.md), [OracleXADataSource](../xa/client/OracleXADataSource.md), [OracleXADataSourceImpl](../replay/OracleXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface OracleXADataSource
      extends XADataSource, OracleCommonDataSource

  This interface defines the Oracle extensions to the standard JDBC interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                              | Method and Description                                                                |
    |----------------------------------------------------------------|---------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | `createXAConnectionBuilder``()`<br>Creates a new `OracleXAConnectionBuilder` instance |

    - ### Methods inherited from interface javax.sql.[XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection__)`, `[`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection_java_lang_String_java_lang_String_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](OracleCommonDataSource.md)`, `[`getConnectionProperties`](OracleCommonDataSource.md)`, `[`getDatabaseName`](OracleCommonDataSource.md)`, `[`getDataSourceName`](OracleCommonDataSource.md)`, `[`getDescription`](OracleCommonDataSource.md)`, `[`getExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getMaxStatements`](OracleCommonDataSource.md)`, `[`getNetworkProtocol`](OracleCommonDataSource.md)`, `[`getPortNumber`](OracleCommonDataSource.md)`, `[`getRoleName`](OracleCommonDataSource.md)`, `[`getServerName`](OracleCommonDataSource.md)`, `[`getURL`](OracleCommonDataSource.md)`, `[`getUser`](OracleCommonDataSource.md)`, `[`setConnectionProperties`](OracleCommonDataSource.md)`, `[`setDatabaseName`](OracleCommonDataSource.md)`, `[`setDataSourceName`](OracleCommonDataSource.md)`, `[`setDescription`](OracleCommonDataSource.md)`, `[`setExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setMaxStatements`](OracleCommonDataSource.md)`, `[`setNetworkProtocol`](OracleCommonDataSource.md)`, `[`setPassword`](OracleCommonDataSource.md)`, `[`setPortNumber`](OracleCommonDataSource.md)`, `[`setRoleName`](OracleCommonDataSource.md)`, `[`setServerName`](OracleCommonDataSource.md)`, `[`setSSLContext`](OracleCommonDataSource.md)`, `[`setTokenSupplier`](OracleCommonDataSource.md)`, `[`setURL`](OracleCommonDataSource.md)`, `[`setUser`](OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Method Detail

    - #### createXAConnectionBuilder

          OracleXAConnectionBuilder createXAConnectionBuilder()
                                                       throws SQLException

      Creates a new `OracleXAConnectionBuilder` instance
      Returns:
      The `OracleXAConnectionBuilder` instance that was created

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs creating the builder

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
- Next Class

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
