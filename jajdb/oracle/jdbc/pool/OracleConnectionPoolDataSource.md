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

- [Prev Class](OracleConnectionCacheManager.md)
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

oracle.jdbc.pool

## Class OracleConnectionPoolDataSource

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.pool.OracleDataSource](OracleDataSource.md)

  - - oracle.jdbc.pool.OracleConnectionPoolDataSource

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md)

  <!-- -->

  Direct Known Subclasses:
  [OracleXADataSource](../xa/OracleXADataSource.md)

  ------------------------------------------------------------------------



      public class OracleConnectionPoolDataSource
      extends OracleDataSource
      implements OracleConnectionPoolDataSource

  A DataSource object is a factory for Connection objects. An object that implements the DataSource interface will typically be registered with a JNDI service provider. A JDBC driver that is accessed via the DataSource API does not automatically register itself with the DriverManager.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.jdbc.pool.[OracleDataSource](OracleDataSource.md)

      [`cacheManager`](OracleDataSource.md)`, `[`connCacheName`](OracleDataSource.md)`, `[`connCacheProperties`](OracleDataSource.md)`, `[`connCachingEnabled`](OracleDataSource.md)`, `[`connectionProperties`](OracleDataSource.md)`, `[`databaseName`](OracleDataSource.md)`, `[`dataSourceName`](OracleDataSource.md)`, `[`DEFAULT_SERVICE_NAME`](OracleDataSource.md)`, `[`description`](OracleDataSource.md)`, `[`driver`](OracleDataSource.md)`, `[`driverType`](OracleDataSource.md)`, `[`ENABLE_AC_SUPPORT_PROPERTY`](OracleDataSource.md)`, `[`explicitCachingEnabled`](OracleDataSource.md)`, `[`explicitCachingEnabledSet`](OracleDataSource.md)`, `[`fastConnFailover`](OracleDataSource.md)`, `[`implicitCachingEnabled`](OracleDataSource.md)`, `[`implicitCachingEnabledSet`](OracleDataSource.md)`, `[`isOracleDataSource`](OracleDataSource.md)`, `[`loginTimeout`](OracleDataSource.md)`, `[`logWriter`](OracleDataSource.md)`, `[`maxStatements`](OracleDataSource.md)`, `[`maxStatementsSet`](OracleDataSource.md)`, `[`networkProtocol`](OracleDataSource.md)`, `[`odsCache`](OracleDataSource.md)`, `[`onsConfigStr`](OracleDataSource.md)`, `[`password`](OracleDataSource.md)`, `[`portNumber`](OracleDataSource.md)`, `[`serverName`](OracleDataSource.md)`, `[`serviceName`](OracleDataSource.md)`, `[`tnsEntry`](OracleDataSource.md)`, `[`TRACE`](OracleDataSource.md)`, `[`url`](OracleDataSource.md)`, `[`user`](OracleDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description           |
    |---------------------------------------|
    | `OracleConnectionPoolDataSource``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                   | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)                                              | `createPooledConnectionBuilder``()`<br>Creates a new `OraclePooledConnectionBuilder` instance                                                                                                                                                                                                                                                                                                                                  |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)  | `getPhysicalConnection``()`<br>Get a Physical Connection with default url, user name, and password                                                                                                                                                                                                                                                                                                                             |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)  | `getPhysicalConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Get a Physical Connection with the user name and password & default URL                                                                                                       |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)  | `getPhysicalConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _url, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Get a Physical Connection with the given url, user name, and password |
    | [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true) | `getPooledConnection``()`<br>Attempt to establish a database connection.                                                                                                                                                                                                                                                                                                                                                       |
    | `protected `[`OraclePooledConnection`](OraclePooledConnection.md)                                                   | `getPooledConnection``(`[`OracleConnectionBuilderImpl`](OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                                                                                                                                                                                                                                                         |
    | [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true) | `getPooledConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Attempt to establish a database connection.                                                                                                                                     |

    - ### Methods inherited from class oracle.jdbc.pool.[OracleDataSource](OracleDataSource.md)

      [`addRefProperties`](OracleDataSource.md)`, `[`close`](OracleDataSource.md)`, `[`copy`](OracleDataSource.md)`, `[`createConnectionBuilder`](OracleDataSource.md)`, `[`debug`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnectionCacheName`](OracleDataSource.md)`, `[`getConnectionCacheProperties`](OracleDataSource.md)`, `[`getConnectionCachingEnabled`](OracleDataSource.md)`, `[`getConnectionDuringExceptionHandling`](OracleDataSource.md)`, `[`getConnectionProperties`](OracleDataSource.md)`, `[`getConnectionProperty`](OracleDataSource.md)`, `[`getDatabaseName`](OracleDataSource.md)`, `[`getDataSourceName`](OracleDataSource.md)`, `[`getDescription`](OracleDataSource.md)`, `[`getDriverType`](OracleDataSource.md)`, `[`getExplicitCachingEnabled`](OracleDataSource.md)`, `[`getFastConnectionFailoverEnabled`](OracleDataSource.md)`, `[`getImplicitCachingEnabled`](OracleDataSource.md)`, `[`getLoginTimeout`](OracleDataSource.md)`, `[`getLogWriter`](OracleDataSource.md)`, `[`getMaxStatements`](OracleDataSource.md)`, `[`getNetworkProtocol`](OracleDataSource.md)`, `[`getONSConfiguration`](OracleDataSource.md)`, `[`getParentLogger`](OracleDataSource.md)`, `[`getPassword`](OracleDataSource.md)`, `[`getPhysicalConnection`](OracleDataSource.md)`, `[`getPortNumber`](OracleDataSource.md)`, `[`getReference`](OracleDataSource.md)`, `[`getRoleName`](OracleDataSource.md)`, `[`getServerName`](OracleDataSource.md)`, `[`getServiceName`](OracleDataSource.md)`, `[`getTNSEntryName`](OracleDataSource.md)`, `[`getURL`](OracleDataSource.md)`, `[`getUser`](OracleDataSource.md)`, `[`isWrapperFor`](OracleDataSource.md)`, `[`setConnectionCacheName`](OracleDataSource.md)`, `[`setConnectionCacheProperties`](OracleDataSource.md)`, `[`setConnectionCachingEnabled`](OracleDataSource.md)`, `[`setConnectionProperties`](OracleDataSource.md)`, `[`setConnectionProperty`](OracleDataSource.md)`, `[`setDatabaseName`](OracleDataSource.md)`, `[`setDataSourceName`](OracleDataSource.md)`, `[`setDescription`](OracleDataSource.md)`, `[`setDriverType`](OracleDataSource.md)`, `[`setExplicitCachingEnabled`](OracleDataSource.md)`, `[`setFastConnectionFailoverEnabled`](OracleDataSource.md)`, `[`setImplicitCachingEnabled`](OracleDataSource.md)`, `[`setLoginTimeout`](OracleDataSource.md)`, `[`setLogWriter`](OracleDataSource.md)`, `[`setMaxStatements`](OracleDataSource.md)`, `[`setNetworkProtocol`](OracleDataSource.md)`, `[`setONSConfiguration`](OracleDataSource.md)`, `[`setPassword`](OracleDataSource.md)`, `[`setPortNumber`](OracleDataSource.md)`, `[`setRoleName`](OracleDataSource.md)`, `[`setServerName`](OracleDataSource.md)`, `[`setServiceName`](OracleDataSource.md)`, `[`setSSLContext`](OracleDataSource.md)`, `[`setTNSEntryName`](OracleDataSource.md)`, `[`setTokenSupplier`](OracleDataSource.md)`, `[`setURL`](OracleDataSource.md)`, `[`setUser`](OracleDataSource.md)`, `[`trace`](OracleDataSource.md)`, `[`unwrap`](OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)`, `[`getConnectionProperties`](../datasource/OracleCommonDataSource.md)`, `[`getDatabaseName`](../datasource/OracleCommonDataSource.md)`, `[`getDataSourceName`](../datasource/OracleCommonDataSource.md)`, `[`getDescription`](../datasource/OracleCommonDataSource.md)`, `[`getExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md)`, `[`getImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md)`, `[`getMaxStatements`](../datasource/OracleCommonDataSource.md)`, `[`getNetworkProtocol`](../datasource/OracleCommonDataSource.md)`, `[`getPortNumber`](../datasource/OracleCommonDataSource.md)`, `[`getRoleName`](../datasource/OracleCommonDataSource.md)`, `[`getServerName`](../datasource/OracleCommonDataSource.md)`, `[`getURL`](../datasource/OracleCommonDataSource.md)`, `[`getUser`](../datasource/OracleCommonDataSource.md)`, `[`setConnectionProperties`](../datasource/OracleCommonDataSource.md)`, `[`setDatabaseName`](../datasource/OracleCommonDataSource.md)`, `[`setDataSourceName`](../datasource/OracleCommonDataSource.md)`, `[`setDescription`](../datasource/OracleCommonDataSource.md)`, `[`setExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md)`, `[`setImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md)`, `[`setMaxStatements`](../datasource/OracleCommonDataSource.md)`, `[`setNetworkProtocol`](../datasource/OracleCommonDataSource.md)`, `[`setPassword`](../datasource/OracleCommonDataSource.md)`, `[`setPortNumber`](../datasource/OracleCommonDataSource.md)`, `[`setRoleName`](../datasource/OracleCommonDataSource.md)`, `[`setServerName`](../datasource/OracleCommonDataSource.md)`, `[`setSSLContext`](../datasource/OracleCommonDataSource.md)`, `[`setTokenSupplier`](../datasource/OracleCommonDataSource.md)`, `[`setURL`](../datasource/OracleCommonDataSource.md)`, `[`setUser`](../datasource/OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Constructor Detail

    - #### OracleConnectionPoolDataSource

          public OracleConnectionPoolDataSource()
                                         throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getPooledConnection

          public PooledConnection getPooledConnection()
                                               throws SQLException

      Attempt to establish a database connection.

      Specified by:
      [`getPooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true#getPooledConnection__) in interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true)

      Returns:
      a PooledConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getPooledConnection

          public PooledConnection getPooledConnection(String _user,
                                                      String _passwd)
                                               throws SQLException

      Attempt to establish a database connection.

      Specified by:
      [`getPooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true#getPooledConnection_java_lang_String_java_lang_String_) in interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true)

      Parameters:
      `user` - the database user on whose behalf the Connection is being made

      `password` - the user's password

      Returns:
      a PooledConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection()
                                              throws SQLException

      Get a Physical Connection with default url, user name, and password
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection(String _url,
                                                     String _user,
                                                     String _passwd)
                                              throws SQLException

      Get a Physical Connection with the given url, user name, and password
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection(String _user,
                                                     String _passwd)
                                              throws SQLException

      Get a Physical Connection with the user name and password & default URL
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPooledConnection

          protected OraclePooledConnection getPooledConnection(OracleConnectionBuilderImpl connBuilder)
                                                        throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createPooledConnectionBuilder

          public OraclePooledConnectionBuilder createPooledConnectionBuilder()
                                                                      throws SQLException

      Description copied from interface: [`OracleConnectionPoolDataSource`](../datasource/OracleConnectionPoolDataSource.md)
      Creates a new `OraclePooledConnectionBuilder` instance
      Specified by:
      [`createPooledConnectionBuilder`](../datasource/OracleConnectionPoolDataSource.md) in interface [`OracleConnectionPoolDataSource`](../datasource/OracleConnectionPoolDataSource.md)

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

- [Prev Class](OracleConnectionCacheManager.md)
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
