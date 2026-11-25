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

- [Prev Class](OracleDataSourceImpl.md)
- [Next Class](OracleXADataSourceImpl.md)

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

oracle.jdbc.replay

## Interface OracleXADataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md), [OracleXADataSource](../datasource/OracleXADataSource.md), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

  ------------------------------------------------------------------------



      public interface OracleXADataSource
      extends OracleConnectionPoolDataSource, OracleXADataSource

  A data source that supports transparent failover replay of JDBC operations.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)

      [`CONNECTION_PROPERTIES`](OracleDataSource.md)`, `[`DATA_SOURCE_NAME`](OracleDataSource.md)`, `[`DATABASE_NAME`](OracleDataSource.md)`, `[`DESCRIPTION`](OracleDataSource.md)`, `[`EXPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`IMPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`MAX_STATEMENTS`](OracleDataSource.md)`, `[`NETWORK_PROTOCOL`](OracleDataSource.md)`, `[`PASSWORD`](OracleDataSource.md)`, `[`PORT_NUMBER`](OracleDataSource.md)`, `[`ROLE_NAME`](OracleDataSource.md)`, `[`SERVER_NAME`](OracleDataSource.md)`, `[`URL`](OracleDataSource.md)`, `[`USER`](OracleDataSource.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                           | Method and Description                                                                                                                                                                                                                                                                                                              |
    |-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | `getXAConnection``()`<br>Attempts to establish a database connection that can be used in a distributed transaction.                                                                                                                                                                                                                 |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | `getXAConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Attempts to establish a database connection that can be used in a distributed transaction. |

    - ### Methods inherited from interface oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md)

      [`getPooledConnection`](OracleConnectionPoolDataSource.md)`, `[`getPooledConnection`](OracleConnectionPoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)

      [`clearReplayStatistics`](OracleDataSource.md)`, `[`getConnectionInitializationCallback`](OracleDataSource.md)`, `[`getConnectionProperty`](OracleDataSource.md)`, `[`getExplicitCachingEnabled`](OracleDataSource.md)`, `[`getImplicitCachingEnabled`](OracleDataSource.md)`, `[`getMaxStatements`](OracleDataSource.md)`, `[`getReplayStatistics`](OracleDataSource.md)`, `[`getRoleName`](OracleDataSource.md)`, `[`registerConnectionInitializationCallback`](OracleDataSource.md)`, `[`setConnectionProperty`](OracleDataSource.md)`, `[`setExplicitCachingEnabled`](OracleDataSource.md)`, `[`setImplicitCachingEnabled`](OracleDataSource.md)`, `[`setMaxStatements`](OracleDataSource.md)`, `[`setRoleName`](OracleDataSource.md)`, `[`unregisterConnectionInitializationCallback`](OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md)

      [`createConnectionBuilder`](../datasource/OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)`, `[`getConnectionProperties`](../datasource/OracleCommonDataSource.md)`, `[`getDatabaseName`](../datasource/OracleCommonDataSource.md)`, `[`getDataSourceName`](../datasource/OracleCommonDataSource.md)`, `[`getDescription`](../datasource/OracleCommonDataSource.md)`, `[`getNetworkProtocol`](../datasource/OracleCommonDataSource.md)`, `[`getPortNumber`](../datasource/OracleCommonDataSource.md)`, `[`getServerName`](../datasource/OracleCommonDataSource.md)`, `[`getURL`](../datasource/OracleCommonDataSource.md)`, `[`getUser`](../datasource/OracleCommonDataSource.md)`, `[`setConnectionProperties`](../datasource/OracleCommonDataSource.md)`, `[`setDatabaseName`](../datasource/OracleCommonDataSource.md)`, `[`setDataSourceName`](../datasource/OracleCommonDataSource.md)`, `[`setDescription`](../datasource/OracleCommonDataSource.md)`, `[`setNetworkProtocol`](../datasource/OracleCommonDataSource.md)`, `[`setPassword`](../datasource/OracleCommonDataSource.md)`, `[`setPortNumber`](../datasource/OracleCommonDataSource.md)`, `[`setServerName`](../datasource/OracleCommonDataSource.md)`, `[`setSSLContext`](../datasource/OracleCommonDataSource.md)`, `[`setTokenSupplier`](../datasource/OracleCommonDataSource.md)`, `[`setURL`](../datasource/OracleCommonDataSource.md)`, `[`setUser`](../datasource/OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md)

      [`createPooledConnectionBuilder`](../datasource/OracleConnectionPoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md)

      [`createXAConnectionBuilder`](../datasource/OracleXADataSource.md)

<!-- -->

- - ### Method Detail

    - #### getXAConnection

          XAConnection getXAConnection()
                                throws SQLException

      Attempts to establish a database connection that can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection__) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Returns:
      An XAConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getXAConnection

          XAConnection getXAConnection(String user,
                                       String passwd)
                                throws SQLException

      Attempts to establish a database connection that can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection_java_lang_String_java_lang_String_) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Parameters:
      `user` - The database user on whose behalf the Connection is being made.

      `passwd` - The user's password

      Returns:
      An XAConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

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

- [Prev Class](OracleDataSourceImpl.md)
- [Next Class](OracleXADataSourceImpl.md)

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
