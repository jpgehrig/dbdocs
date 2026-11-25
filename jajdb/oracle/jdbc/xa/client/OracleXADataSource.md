Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
- [Next Class](OracleXAHeteroCloseCallback.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.jdbc.xa.client

## Class OracleXADataSource

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.pool.OracleDataSource](../../pool/OracleDataSource.md)

  - - [oracle.jdbc.pool.OracleConnectionPoolDataSource](../../pool/OracleConnectionPoolDataSource.md)

    - - [oracle.jdbc.xa.OracleXADataSource](../OracleXADataSource.md)

      - - oracle.jdbc.xa.client.OracleXADataSource

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true), [OracleCommonDataSource](../../datasource/OracleCommonDataSource.md), [OracleConnectionPoolDataSource](../../datasource/OracleConnectionPoolDataSource.md), [OracleDataSource](../../datasource/OracleDataSource.md), [OracleXADataSource](../../datasource/OracleXADataSource.md)

  ------------------------------------------------------------------------



      public class OracleXADataSource
      extends OracleXADataSource

  A factory for XAConnection objects. An object that implements the XADataSource interface is typically registered with a JNDI service provider.
  For optimization purposes, we implemented 2 versions of OracleXADataSource: one for client, and one for server when used in Java Stored Procedures and in EJB. The server-version is only available in 8.1.6 and post-8.1.6 backends. This one is the implementation of OracleXADataSource for client-side usage and works for both pre- and post-8.1.6 RMs.

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static boolean`  | `TRACE`               |

    - ### Fields inherited from class oracle.jdbc.xa.[OracleXADataSource](../OracleXADataSource.md)

      [`useNativeXA`](../OracleXADataSource.md)

    <!-- -->

    - ### Fields inherited from class oracle.jdbc.pool.[OracleDataSource](../../pool/OracleDataSource.md)

      [`cacheManager`](../../pool/OracleDataSource.md)`, `[`connCacheName`](../../pool/OracleDataSource.md)`, `[`connCacheProperties`](../../pool/OracleDataSource.md)`, `[`connCachingEnabled`](../../pool/OracleDataSource.md)`, `[`connectionProperties`](../../pool/OracleDataSource.md)`, `[`databaseName`](../../pool/OracleDataSource.md)`, `[`dataSourceName`](../../pool/OracleDataSource.md)`, `[`DEFAULT_SERVICE_NAME`](../../pool/OracleDataSource.md)`, `[`description`](../../pool/OracleDataSource.md)`, `[`driver`](../../pool/OracleDataSource.md)`, `[`driverType`](../../pool/OracleDataSource.md)`, `[`ENABLE_AC_SUPPORT_PROPERTY`](../../pool/OracleDataSource.md)`, `[`explicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`explicitCachingEnabledSet`](../../pool/OracleDataSource.md)`, `[`fastConnFailover`](../../pool/OracleDataSource.md)`, `[`implicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`implicitCachingEnabledSet`](../../pool/OracleDataSource.md)`, `[`isOracleDataSource`](../../pool/OracleDataSource.md)`, `[`loginTimeout`](../../pool/OracleDataSource.md)`, `[`logWriter`](../../pool/OracleDataSource.md)`, `[`maxStatements`](../../pool/OracleDataSource.md)`, `[`maxStatementsSet`](../../pool/OracleDataSource.md)`, `[`networkProtocol`](../../pool/OracleDataSource.md)`, `[`odsCache`](../../pool/OracleDataSource.md)`, `[`onsConfigStr`](../../pool/OracleDataSource.md)`, `[`password`](../../pool/OracleDataSource.md)`, `[`portNumber`](../../pool/OracleDataSource.md)`, `[`serverName`](../../pool/OracleDataSource.md)`, `[`serviceName`](../../pool/OracleDataSource.md)`, `[`tnsEntry`](../../pool/OracleDataSource.md)`, `[`url`](../../pool/OracleDataSource.md)`, `[`user`](../../pool/OracleDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                        |
    |--------------------------------------------------------------------|
    | `OracleXADataSource``()`<br>Create an OracleXADataSource instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md)                                      | `createXAConnectionBuilder``()`<br>Creates a new Oracle XA ConnectionBuilder instance                                                                                                                                                                                                                                                                                                                                                                                        |
    | `protected void`                                                                                            | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | `getXAConnection``()`<br>Attempt to establish a database connection.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | `getXAConnection``(`[`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md)` builder)`                                                                                                                                                                                                                                                                                                                                                                        |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | `getXAConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` userName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Attempt to establish a database connection.                                                                                                                                                                                     |

    - ### Methods inherited from class oracle.jdbc.xa.[OracleXADataSource](../OracleXADataSource.md)

      [`copy`](../OracleXADataSource.md)`, `[`getConnectionDuringExceptionHandling`](../OracleXADataSource.md)`, `[`setURL`](../OracleXADataSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.jdbc.pool.[OracleConnectionPoolDataSource](../../pool/OracleConnectionPoolDataSource.md)

      [`createPooledConnectionBuilder`](../../pool/OracleConnectionPoolDataSource.md)`, `[`getPhysicalConnection`](../../pool/OracleConnectionPoolDataSource.md)`, `[`getPhysicalConnection`](../../pool/OracleConnectionPoolDataSource.md)`, `[`getPhysicalConnection`](../../pool/OracleConnectionPoolDataSource.md)`, `[`getPooledConnection`](../../pool/OracleConnectionPoolDataSource.md)`, `[`getPooledConnection`](../../pool/OracleConnectionPoolDataSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.jdbc.pool.[OracleDataSource](../../pool/OracleDataSource.md)

      [`addRefProperties`](../../pool/OracleDataSource.md)`, `[`close`](../../pool/OracleDataSource.md)`, `[`createConnectionBuilder`](../../pool/OracleDataSource.md)`, `[`getConnection`](../../pool/OracleDataSource.md)`, `[`getConnection`](../../pool/OracleDataSource.md)`, `[`getConnection`](../../pool/OracleDataSource.md)`, `[`getConnection`](../../pool/OracleDataSource.md)`, `[`getConnection`](../../pool/OracleDataSource.md)`, `[`getConnectionCacheName`](../../pool/OracleDataSource.md)`, `[`getConnectionCacheProperties`](../../pool/OracleDataSource.md)`, `[`getConnectionCachingEnabled`](../../pool/OracleDataSource.md)`, `[`getConnectionProperties`](../../pool/OracleDataSource.md)`, `[`getConnectionProperty`](../../pool/OracleDataSource.md)`, `[`getDatabaseName`](../../pool/OracleDataSource.md)`, `[`getDataSourceName`](../../pool/OracleDataSource.md)`, `[`getDescription`](../../pool/OracleDataSource.md)`, `[`getDriverType`](../../pool/OracleDataSource.md)`, `[`getExplicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`getFastConnectionFailoverEnabled`](../../pool/OracleDataSource.md)`, `[`getImplicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`getLoginTimeout`](../../pool/OracleDataSource.md)`, `[`getLogWriter`](../../pool/OracleDataSource.md)`, `[`getMaxStatements`](../../pool/OracleDataSource.md)`, `[`getNetworkProtocol`](../../pool/OracleDataSource.md)`, `[`getONSConfiguration`](../../pool/OracleDataSource.md)`, `[`getParentLogger`](../../pool/OracleDataSource.md)`, `[`getPassword`](../../pool/OracleDataSource.md)`, `[`getPhysicalConnection`](../../pool/OracleDataSource.md)`, `[`getPortNumber`](../../pool/OracleDataSource.md)`, `[`getReference`](../../pool/OracleDataSource.md)`, `[`getRoleName`](../../pool/OracleDataSource.md)`, `[`getServerName`](../../pool/OracleDataSource.md)`, `[`getServiceName`](../../pool/OracleDataSource.md)`, `[`getTNSEntryName`](../../pool/OracleDataSource.md)`, `[`getURL`](../../pool/OracleDataSource.md)`, `[`getUser`](../../pool/OracleDataSource.md)`, `[`isWrapperFor`](../../pool/OracleDataSource.md)`, `[`setConnectionCacheName`](../../pool/OracleDataSource.md)`, `[`setConnectionCacheProperties`](../../pool/OracleDataSource.md)`, `[`setConnectionCachingEnabled`](../../pool/OracleDataSource.md)`, `[`setConnectionProperties`](../../pool/OracleDataSource.md)`, `[`setConnectionProperty`](../../pool/OracleDataSource.md)`, `[`setDatabaseName`](../../pool/OracleDataSource.md)`, `[`setDataSourceName`](../../pool/OracleDataSource.md)`, `[`setDescription`](../../pool/OracleDataSource.md)`, `[`setDriverType`](../../pool/OracleDataSource.md)`, `[`setExplicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`setFastConnectionFailoverEnabled`](../../pool/OracleDataSource.md)`, `[`setImplicitCachingEnabled`](../../pool/OracleDataSource.md)`, `[`setLoginTimeout`](../../pool/OracleDataSource.md)`, `[`setLogWriter`](../../pool/OracleDataSource.md)`, `[`setMaxStatements`](../../pool/OracleDataSource.md)`, `[`setNetworkProtocol`](../../pool/OracleDataSource.md)`, `[`setONSConfiguration`](../../pool/OracleDataSource.md)`, `[`setPassword`](../../pool/OracleDataSource.md)`, `[`setPortNumber`](../../pool/OracleDataSource.md)`, `[`setRoleName`](../../pool/OracleDataSource.md)`, `[`setServerName`](../../pool/OracleDataSource.md)`, `[`setServiceName`](../../pool/OracleDataSource.md)`, `[`setSSLContext`](../../pool/OracleDataSource.md)`, `[`setTNSEntryName`](../../pool/OracleDataSource.md)`, `[`setTokenSupplier`](../../pool/OracleDataSource.md)`, `[`setUser`](../../pool/OracleDataSource.md)`, `[`trace`](../../pool/OracleDataSource.md)`, `[`unwrap`](../../pool/OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../../datasource/OracleCommonDataSource.md)`, `[`getConnectionProperties`](../../datasource/OracleCommonDataSource.md)`, `[`getDatabaseName`](../../datasource/OracleCommonDataSource.md)`, `[`getDataSourceName`](../../datasource/OracleCommonDataSource.md)`, `[`getDescription`](../../datasource/OracleCommonDataSource.md)`, `[`getExplicitCachingEnabled`](../../datasource/OracleCommonDataSource.md)`, `[`getImplicitCachingEnabled`](../../datasource/OracleCommonDataSource.md)`, `[`getMaxStatements`](../../datasource/OracleCommonDataSource.md)`, `[`getNetworkProtocol`](../../datasource/OracleCommonDataSource.md)`, `[`getPortNumber`](../../datasource/OracleCommonDataSource.md)`, `[`getRoleName`](../../datasource/OracleCommonDataSource.md)`, `[`getServerName`](../../datasource/OracleCommonDataSource.md)`, `[`getURL`](../../datasource/OracleCommonDataSource.md)`, `[`getUser`](../../datasource/OracleCommonDataSource.md)`, `[`setConnectionProperties`](../../datasource/OracleCommonDataSource.md)`, `[`setDatabaseName`](../../datasource/OracleCommonDataSource.md)`, `[`setDataSourceName`](../../datasource/OracleCommonDataSource.md)`, `[`setDescription`](../../datasource/OracleCommonDataSource.md)`, `[`setExplicitCachingEnabled`](../../datasource/OracleCommonDataSource.md)`, `[`setImplicitCachingEnabled`](../../datasource/OracleCommonDataSource.md)`, `[`setMaxStatements`](../../datasource/OracleCommonDataSource.md)`, `[`setNetworkProtocol`](../../datasource/OracleCommonDataSource.md)`, `[`setPassword`](../../datasource/OracleCommonDataSource.md)`, `[`setPortNumber`](../../datasource/OracleCommonDataSource.md)`, `[`setRoleName`](../../datasource/OracleCommonDataSource.md)`, `[`setServerName`](../../datasource/OracleCommonDataSource.md)`, `[`setSSLContext`](../../datasource/OracleCommonDataSource.md)`, `[`setTokenSupplier`](../../datasource/OracleCommonDataSource.md)`, `[`setUser`](../../datasource/OracleCommonDataSource.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Field Detail

    - #### TRACE

          public static final boolean TRACE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleXADataSource

          public OracleXADataSource()
                             throws SQLException

      Create an OracleXADataSource instance.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if error occurs while creating an object

  <!-- -->

  - ### Method Detail

    - #### getXAConnection

          public XAConnection getXAConnection()
                                       throws SQLException

      Attempt to establish a database connection.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection__) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Specified by:
      [`getXAConnection`](../OracleXADataSource.md) in class [`OracleXADataSource`](../OracleXADataSource.md)

      Returns:
      an Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getXAConnection

          public XAConnection getXAConnection(String userName,
                                              String passwd)
                                       throws SQLException

      Attempt to establish a database connection.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection_java_lang_String_java_lang_String_) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Specified by:
      [`getXAConnection`](../OracleXADataSource.md) in class [`OracleXADataSource`](../OracleXADataSource.md)

      Parameters:
      `userName` - the database user on whose behalf the Connection is made

      `passwd` - the user's password

      Returns:
      an XAConnection encapsulating a connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getXAConnection

          public XAConnection getXAConnection(OracleXAConnectionBuilderImpl builder)
                                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createXAConnectionBuilder

          public OracleXAConnectionBuilderImpl createXAConnectionBuilder()

      Creates a new Oracle XA ConnectionBuilder instance
      Specified by:
      [`createXAConnectionBuilder`](../../datasource/OracleXADataSource.md) in interface [`OracleXADataSource`](../../datasource/OracleXADataSource.md)

      Overrides:
      [`createXAConnectionBuilder`](../OracleXADataSource.md) in class [`OracleXADataSource`](../OracleXADataSource.md)

      Returns:
      The XA ConnectionBuilder instance that was created

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

      Overrides:
      [`debug`](../../pool/OracleDataSource.md) in class [`OracleDataSource`](../../pool/OracleDataSource.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
- [Next Class](OracleXAHeteroCloseCallback.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
