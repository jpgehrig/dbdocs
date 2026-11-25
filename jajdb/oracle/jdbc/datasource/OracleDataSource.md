Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionPoolDataSource.md)
- [Next Class](OraclePooledConnection.md)

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

## Interface OracleDataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](OracleCommonDataSource.md), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleConnectionPoolDataSource](../replay/OracleConnectionPoolDataSource.md), [OracleDataSource](../replay/OracleDataSource.md), [OracleXADataSource](../replay/OracleXADataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [OracleConnectionPoolDataSource](../pool/OracleConnectionPoolDataSource.md), [OracleConnectionPoolDataSourceImpl](../replay/OracleConnectionPoolDataSourceImpl.md), [OracleDataSource](../pool/OracleDataSource.md), [OracleDataSourceImpl](../replay/OracleDataSourceImpl.md), [OracleOCIConnectionPool](../pool/OracleOCIConnectionPool.md), [OracleXADataSource](../xa/OracleXADataSource.md), [OracleXADataSource](../xa/client/OracleXADataSource.md), [OracleXADataSourceImpl](../replay/OracleXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface OracleDataSource
      extends DataSource, OracleCommonDataSource

  This interface defines the Oracle extensions to the standard JDBC interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                          | Method and Description                                                           |
    |------------------------------------------------------------|----------------------------------------------------------------------------------|
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | `createConnectionBuilder``()`<br>Create a new `OracleConnectionBuilder` instance |

    - ### Methods inherited from interface javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](OracleCommonDataSource.md)`, `[`getConnectionProperties`](OracleCommonDataSource.md)`, `[`getDatabaseName`](OracleCommonDataSource.md)`, `[`getDataSourceName`](OracleCommonDataSource.md)`, `[`getDescription`](OracleCommonDataSource.md)`, `[`getExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`getMaxStatements`](OracleCommonDataSource.md)`, `[`getNetworkProtocol`](OracleCommonDataSource.md)`, `[`getPortNumber`](OracleCommonDataSource.md)`, `[`getRoleName`](OracleCommonDataSource.md)`, `[`getServerName`](OracleCommonDataSource.md)`, `[`getURL`](OracleCommonDataSource.md)`, `[`getUser`](OracleCommonDataSource.md)`, `[`setConnectionProperties`](OracleCommonDataSource.md)`, `[`setDatabaseName`](OracleCommonDataSource.md)`, `[`setDataSourceName`](OracleCommonDataSource.md)`, `[`setDescription`](OracleCommonDataSource.md)`, `[`setExplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setImplicitCachingEnabled`](OracleCommonDataSource.md)`, `[`setMaxStatements`](OracleCommonDataSource.md)`, `[`setNetworkProtocol`](OracleCommonDataSource.md)`, `[`setPassword`](OracleCommonDataSource.md)`, `[`setPortNumber`](OracleCommonDataSource.md)`, `[`setRoleName`](OracleCommonDataSource.md)`, `[`setServerName`](OracleCommonDataSource.md)`, `[`setSSLContext`](OracleCommonDataSource.md)`, `[`setTokenSupplier`](OracleCommonDataSource.md)`, `[`setURL`](OracleCommonDataSource.md)`, `[`setUser`](OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Method Detail

    - #### createConnectionBuilder

          OracleConnectionBuilder createConnectionBuilder()
                                                   throws SQLException

      Create a new `OracleConnectionBuilder` instance
      Returns:
      The `OracleConnectionBuilder` instance that was created

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while creating the builder

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionPoolDataSource.md)
- [Next Class](OraclePooledConnection.md)

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
