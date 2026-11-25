Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOCIConnectionPool.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSourceFactory.md)
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

oracle.jdbc.pool

## Class OracleOCIConnectionPool

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.pool.OracleDataSource](OracleDataSource.md)

  - - oracle.jdbc.pool.OracleOCIConnectionPool

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md)

  ------------------------------------------------------------------------



      public class OracleOCIConnectionPool
      extends OracleDataSource

  A type-2 driver connection pool.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                        | Field and Description           |
    |----------------------------------------------------------------------------------------------------------|---------------------------------|
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_ID`                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_POOL`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_ACTIVE_SIZE`          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_ALIASED_CONNECTION`   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_CONNECTION`           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_INCREMENT`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_IS_POOLCREATED`       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_LOGON_MODE`           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_MAX_LIMIT`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_MIN_LIMIT`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_NOWAIT`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_OBJECT`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_POOL_SIZE`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_PROXY_CONNECTION`     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNPOOL_TIMEOUT`              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `IS_CONNECTION_POOLING`         |
    | `oracle.jdbc.oci.OracleOCIConnection`                                                                    | `m_connection_pool`             |
    | `protected int`                                                                                          | `m_stmtCacheSize`               |
    | `protected boolean`                                                                                      | `m_stmtClearMetaData`           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_CERTIFICATE`             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_DISTINGUISHED_NAME`      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_NUM_ROLES`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_PASSWORD`                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_ROLES`                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_USER_NAME`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXYTYPE`                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXYTYPE_CERTIFICATE`         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXYTYPE_DISTINGUISHED_NAME`  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXYTYPE_USER_NAME`           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `TRANSACTIONS_DISTRIBUTED`      |

    - ### Fields inherited from class oracle.jdbc.pool.[OracleDataSource](OracleDataSource.md)

      [`cacheManager`](OracleDataSource.md)`, `[`connCacheName`](OracleDataSource.md)`, `[`connCacheProperties`](OracleDataSource.md)`, `[`connCachingEnabled`](OracleDataSource.md)`, `[`connectionProperties`](OracleDataSource.md)`, `[`databaseName`](OracleDataSource.md)`, `[`dataSourceName`](OracleDataSource.md)`, `[`DEFAULT_SERVICE_NAME`](OracleDataSource.md)`, `[`description`](OracleDataSource.md)`, `[`driver`](OracleDataSource.md)`, `[`driverType`](OracleDataSource.md)`, `[`ENABLE_AC_SUPPORT_PROPERTY`](OracleDataSource.md)`, `[`explicitCachingEnabled`](OracleDataSource.md)`, `[`explicitCachingEnabledSet`](OracleDataSource.md)`, `[`fastConnFailover`](OracleDataSource.md)`, `[`implicitCachingEnabled`](OracleDataSource.md)`, `[`implicitCachingEnabledSet`](OracleDataSource.md)`, `[`isOracleDataSource`](OracleDataSource.md)`, `[`loginTimeout`](OracleDataSource.md)`, `[`logWriter`](OracleDataSource.md)`, `[`maxStatements`](OracleDataSource.md)`, `[`maxStatementsSet`](OracleDataSource.md)`, `[`networkProtocol`](OracleDataSource.md)`, `[`odsCache`](OracleDataSource.md)`, `[`onsConfigStr`](OracleDataSource.md)`, `[`password`](OracleDataSource.md)`, `[`portNumber`](OracleDataSource.md)`, `[`serverName`](OracleDataSource.md)`, `[`serviceName`](OracleDataSource.md)`, `[`tnsEntry`](OracleDataSource.md)`, `[`TRACE`](OracleDataSource.md)`, `[`url`](OracleDataSource.md)`, `[`user`](OracleDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleOCIConnectionPool``()`<br>This will use the user-id, password and connection pool name values set using the methods setUser, setPassword, setConnectionPoolName.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `OracleOCIConnectionPool``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` us, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` p, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url)`<br>Deprecated.                                                                                                                                                                                                                 |
    | `OracleOCIConnectionPool``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` us, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` p, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` info)`<br>Notes: Choose a userid and password that can act as proxy for the users in the getProxyConnection() method. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                   | `close``()`<br>This will destroy the connection pool, and close all the connections opened from this data source.                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                   | `connectionClosed``(oracle.jdbc.oci.OracleOCIConnection conn)`                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `protected void`                                                                                         | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | `int`                                                                                                    | `getActiveSize``()`<br>Return the number of active or busy connections in the connection pool Note that the count cannot be guaranteed on any invoking subsequent OracleOCIConnectionCacheImpl method.                                                                                                                                                                                                                                                                       |
    | `oracle.jdbc.internal.OracleConnection`                                                                  | `getAliasedConnection``(byte[] conId)`<br>For creating aliased sessions.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)   | `getConnection``()`<br>Attempt to establish a database connection.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)   | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` us, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` p)`<br>For getting a connection to the database.                                                                                                                                                                                                    |
    | `protected oracle.jdbc.internal.OracleConnection`                                                        | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                                    | `getConnectionIncrement``()`<br>Return the Increment for increasing the connections for the Cache.                                                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                                                                                    | `getMaxLimit``()`<br>Return the Max limit on Connections.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                    | `getMinLimit``()`<br>Note: There are no individual setMin, setMax and setIncrement since that needs to be done in one call to setPoolConfig Return the minimum limit on the no of Connections.                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `getNoWait``()`<br>Return the connection No-wait parameter This attribute determines if retrial for a connection has to be done when all connections in the pool are found to be busy and the number of connections already reached max.                                                                                                                                                                                                                                     |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)  | `getPoolConfig``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `int`                                                                                                    | `getPoolSize``()`<br>Return the number of physical connections in the connection pool Note that the count cannot be guaranteed on any invoking subsequent OracleOCIConnectionCacheImpl method.                                                                                                                                                                                                                                                                               |
    | `oracle.jdbc.internal.OracleConnection`                                                                  | `getProxyConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` proxytype, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop)`<br>For creating a proxy connection.                                                                                                                                                                                      |
    | [`Reference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Reference.html?is-external=true) | `getReference``()`<br>Inherited from referenceable                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                                                                                    | `getStmtCacheSize``()`<br>Return the size of Statement Cache.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                    | `getTimeout``()`<br>Return the timeout The connections idle for more than this time (seconds) are terminated periodically, to maintain optimum number of open connections.This attribute can be set dynamically.                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                | `isDistributedTransEnabled``()`                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                | `isPoolCreated``()`<br>check if the pool has been created.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                | `isStmtCacheEnabled``()`<br>Check whether Statement Caching is enabled for this pool or Not.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static void`                                                                                            | `readPoolConfig``(int minLimit, int maxLimit, int increment, int timeout, boolean nowait, boolean transactionsDistributed, int[] p)`<br>read the properties into an integer array                                                                                                                                                                                                                                                                                            |
    | `static void`                                                                                            | `readPoolConfig``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` info, int[] p)`                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                   | `setPoolConfig``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop)`<br>(Re-)Set the pool configuration for the Cache.                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                   | `setStmtCacheSize``(int size)`<br>Set the statement cache size.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                   | `setStmtCacheSize``(int size, boolean clearMetaData)`<br>Set the statement cache size.                                                                                                                                                                                                                                                                                                                                                                                       |

    - ### Methods inherited from class oracle.jdbc.pool.[OracleDataSource](OracleDataSource.md)

      [`addRefProperties`](OracleDataSource.md)`, `[`copy`](OracleDataSource.md)`, `[`createConnectionBuilder`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnection`](OracleDataSource.md)`, `[`getConnectionCacheName`](OracleDataSource.md)`, `[`getConnectionCacheProperties`](OracleDataSource.md)`, `[`getConnectionCachingEnabled`](OracleDataSource.md)`, `[`getConnectionProperties`](OracleDataSource.md)`, `[`getConnectionProperty`](OracleDataSource.md)`, `[`getDatabaseName`](OracleDataSource.md)`, `[`getDataSourceName`](OracleDataSource.md)`, `[`getDescription`](OracleDataSource.md)`, `[`getDriverType`](OracleDataSource.md)`, `[`getExplicitCachingEnabled`](OracleDataSource.md)`, `[`getFastConnectionFailoverEnabled`](OracleDataSource.md)`, `[`getImplicitCachingEnabled`](OracleDataSource.md)`, `[`getLoginTimeout`](OracleDataSource.md)`, `[`getLogWriter`](OracleDataSource.md)`, `[`getMaxStatements`](OracleDataSource.md)`, `[`getNetworkProtocol`](OracleDataSource.md)`, `[`getONSConfiguration`](OracleDataSource.md)`, `[`getParentLogger`](OracleDataSource.md)`, `[`getPassword`](OracleDataSource.md)`, `[`getPhysicalConnection`](OracleDataSource.md)`, `[`getPortNumber`](OracleDataSource.md)`, `[`getRoleName`](OracleDataSource.md)`, `[`getServerName`](OracleDataSource.md)`, `[`getServiceName`](OracleDataSource.md)`, `[`getTNSEntryName`](OracleDataSource.md)`, `[`getURL`](OracleDataSource.md)`, `[`getUser`](OracleDataSource.md)`, `[`isWrapperFor`](OracleDataSource.md)`, `[`setConnectionCacheName`](OracleDataSource.md)`, `[`setConnectionCacheProperties`](OracleDataSource.md)`, `[`setConnectionCachingEnabled`](OracleDataSource.md)`, `[`setConnectionProperties`](OracleDataSource.md)`, `[`setConnectionProperty`](OracleDataSource.md)`, `[`setDatabaseName`](OracleDataSource.md)`, `[`setDataSourceName`](OracleDataSource.md)`, `[`setDescription`](OracleDataSource.md)`, `[`setDriverType`](OracleDataSource.md)`, `[`setExplicitCachingEnabled`](OracleDataSource.md)`, `[`setFastConnectionFailoverEnabled`](OracleDataSource.md)`, `[`setImplicitCachingEnabled`](OracleDataSource.md)`, `[`setLoginTimeout`](OracleDataSource.md)`, `[`setLogWriter`](OracleDataSource.md)`, `[`setMaxStatements`](OracleDataSource.md)`, `[`setNetworkProtocol`](OracleDataSource.md)`, `[`setONSConfiguration`](OracleDataSource.md)`, `[`setPassword`](OracleDataSource.md)`, `[`setPortNumber`](OracleDataSource.md)`, `[`setRoleName`](OracleDataSource.md)`, `[`setServerName`](OracleDataSource.md)`, `[`setServiceName`](OracleDataSource.md)`, `[`setSSLContext`](OracleDataSource.md)`, `[`setTNSEntryName`](OracleDataSource.md)`, `[`setTokenSupplier`](OracleDataSource.md)`, `[`setURL`](OracleDataSource.md)`, `[`setUser`](OracleDataSource.md)`, `[`trace`](OracleDataSource.md)`, `[`unwrap`](OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)

<!-- -->

- - ### Field Detail

    - #### m_connection_pool

          public oracle.jdbc.oci.OracleOCIConnection m_connection_pool

    <!-- -->

    - #### IS_CONNECTION_POOLING

          public static final String IS_CONNECTION_POOLING

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_OBJECT

          public static final String CONNPOOL_OBJECT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_LOGON_MODE

          public static final String CONNPOOL_LOGON_MODE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNECTION_POOL

          public static final String CONNECTION_POOL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_CONNECTION

          public static final String CONNPOOL_CONNECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_PROXY_CONNECTION

          public static final String CONNPOOL_PROXY_CONNECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_ALIASED_CONNECTION

          public static final String CONNPOOL_ALIASED_CONNECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_USER_NAME

          public static final String PROXY_USER_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_DISTINGUISHED_NAME

          public static final String PROXY_DISTINGUISHED_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_CERTIFICATE

          public static final String PROXY_CERTIFICATE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_ROLES

          public static final String PROXY_ROLES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_NUM_ROLES

          public static final String PROXY_NUM_ROLES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXY_PASSWORD

          public static final String PROXY_PASSWORD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE

          public static final String PROXYTYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_USER_NAME

          public static final String PROXYTYPE_USER_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_DISTINGUISHED_NAME

          public static final String PROXYTYPE_DISTINGUISHED_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_CERTIFICATE

          public static final String PROXYTYPE_CERTIFICATE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNECTION_ID

          public static final String CONNECTION_ID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_MIN_LIMIT

          public static final String CONNPOOL_MIN_LIMIT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_MAX_LIMIT

          public static final String CONNPOOL_MAX_LIMIT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_INCREMENT

          public static final String CONNPOOL_INCREMENT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_ACTIVE_SIZE

          public static final String CONNPOOL_ACTIVE_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_POOL_SIZE

          public static final String CONNPOOL_POOL_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_TIMEOUT

          public static final String CONNPOOL_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_NOWAIT

          public static final String CONNPOOL_NOWAIT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNPOOL_IS_POOLCREATED

          public static final String CONNPOOL_IS_POOLCREATED

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TRANSACTIONS_DISTRIBUTED

          public static final String TRANSACTIONS_DISTRIBUTED

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### m_stmtCacheSize

          protected int m_stmtCacheSize

    <!-- -->

    - #### m_stmtClearMetaData

          protected boolean m_stmtClearMetaData

  <!-- -->

  - ### Constructor Detail

    - #### OracleOCIConnectionPool

          public OracleOCIConnectionPool(String us,
                                         String p,
                                         String url,
                                         Properties info)
                                  throws SQLException

      Notes: Choose a userid and password that can act as proxy for the users in the getProxyConnection() method.
      Parameters:
      `us` - ConnectionPool user-id.

      `p` - ConnectionPool password

      `url` - This would be the full url including the database name. The database name would be the logical name of the pool.

      `info` - Set of properties (optional) for specifying the pool configuration.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### OracleOCIConnectionPool

          public OracleOCIConnectionPool(String us,
                                         String p,
                                         String url)
                                  throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### OracleOCIConnectionPool

          public OracleOCIConnectionPool()
                                  throws SQLException

      This will use the user-id, password and connection pool name values set using the methods setUser, setPassword, setConnectionPoolName.
      Notes: No useful operations (like getConnection) can be performed on this class unless the methods setUser, setPassword, setConnectionPoolName are invoked. Choose a userid and password that can act as proxy for the users in the getProxyConnection() method.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Description copied from class: [`OracleDataSource`](OracleDataSource.md)
      Attempt to establish a database connection.

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Overrides:
      [`getConnection`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection(String us,
                                          String p)
                                   throws SQLException

      For getting a connection to the database.
      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Overrides:
      [`getConnection`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

      Parameters:
      `us` - Connection user-id

      `p` - Connection password

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getReference

          public Reference getReference()
                                 throws NamingException

      Inherited from referenceable
      Specified by:
      [`getReference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true#getReference__) in interface [`Referenceable`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true)

      Overrides:
      [`getReference`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

      Returns:
      Returns a reference to this OracleOCIConnectionPool instance

      Throws:
      [`NamingException`](http://download.oracle.com/javase/8/docs/api/javax/naming/NamingException.html?is-external=true)

    <!-- -->

    - #### getProxyConnection

          public oracle.jdbc.internal.OracleConnection getProxyConnection(String proxytype,
                                                                          Properties prop)
                                                                   throws SQLException

      For creating a proxy connection.
      Notes: The user and password used to create OracleOCIConnectionPool() must be allowed to act as proxy for user 'us'.

      Parameters:
      `proxytype` - Can be one of following types OracleOCIConnectionPool.PROXYCONNECTION_USER_NAME - This will be the normal mode of specifying the user name in proxyUser OracleOCIConnectionPool.PROXYCONNECTION_DISTINGUISHED_NAME - This will specify the distinguished name of the user in proxyUser OracleOCIConnectionPool.PROXYCONNECTION_CERTIFICATE - This will specify the proxy certificate in proxyUser

      `proxyUser` - The user, or certificate, to be proxied against.

      `roles` - Set of roles which this proxy connection can use

      Returns:
      connection object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAliasedConnection

          public oracle.jdbc.internal.OracleConnection getAliasedConnection(byte[] conId)
                                                                     throws SQLException

      For creating aliased sessions.
      Notes: Once this call is issued, this connection object can't be used for any operation, as the intent for connection cloning is failover.

      Parameters:
      `conId` - - byte\[\] of the connection id

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      This will destroy the connection pool, and close all the connections opened from this data source. Hence all the statement objects created from these connection objects will also be closed.
      Overrides:
      [`close`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPoolConfig

          public void setPoolConfig(Properties prop)
                             throws SQLException

      (Re-)Set the pool configuration for the Cache. Note: We will not be exposing set for individual settings of the pool's configuration. Users will have to call setPoolConfig with min, max & increment in order for the pool's configuration to be changed.
      Parameters:
      `prop` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### readPoolConfig

          public static void readPoolConfig(int minLimit,
                                            int maxLimit,
                                            int increment,
                                            int timeout,
                                            boolean nowait,
                                            boolean transactionsDistributed,
                                            int[] p)

      read the properties into an integer array

    <!-- -->

    - #### readPoolConfig

          public static void readPoolConfig(Properties info,
                                            int[] p)

    <!-- -->

    - #### getPoolConfig

          public Properties getPoolConfig()
                                   throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getActiveSize

          public int getActiveSize()
                            throws SQLException

      Return the number of active or busy connections in the connection pool Note that the count cannot be guaranteed on any invoking subsequent OracleOCIConnectionCacheImpl method. This should be used only as estimate and perhaps for statistical analysis.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPoolSize

          public int getPoolSize()
                          throws SQLException

      Return the number of physical connections in the connection pool Note that the count cannot be guaranteed on any invoking subsequent OracleOCIConnectionCacheImpl method. This should be used only as estimate and perhaps for statistical analysis.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTimeout

          public int getTimeout()
                         throws SQLException

      Return the timeout The connections idle for more than this time (seconds) are terminated periodically, to maintain optimum number of open connections.This attribute can be set dynamically. If this attribute is not set, the connections are never timed out.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNoWait

          public String getNoWait()
                           throws SQLException

      Return the connection No-wait parameter This attribute determines if retrial for a connection has to be done when all connections in the pool are found to be busy and the number of connections already reached max. If this attribute is set, an error is thrown when all the connections are busy and no more connections can be opened. Otherwise the call waits till it gets a connection.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMinLimit

          public int getMinLimit()
                          throws SQLException

      Note: There are no individual setMin, setMax and setIncrement since that needs to be done in one call to setPoolConfig Return the minimum limit on the no of Connections.
      Returns:
      minimum limit on the no of Connections.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxLimit

          public int getMaxLimit()
                          throws SQLException

      Return the Max limit on Connections.
      Returns:
      int Max no of Connections that can be opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionIncrement

          public int getConnectionIncrement()
                                     throws SQLException

      Return the Increment for increasing the connections for the Cache.
      Returns:
      int Increment

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isDistributedTransEnabled

          public boolean isDistributedTransEnabled()

    <!-- -->

    - #### isPoolCreated

          public boolean isPoolCreated()

      check if the pool has been created. This occurs when \<init\> is called with user/password or getConnection() has been called

    <!-- -->

    - #### connectionClosed

          public void connectionClosed(oracle.jdbc.oci.OracleOCIConnection conn)
                                throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setStmtCacheSize

          public void setStmtCacheSize(int size)
                                throws SQLException

      Set the statement cache size. Default is 0. You cannot set this for logicalhandles obtained from this pool. If more than \<it\> size \</it\> cursors are already cached than they will be closed. By default the meta data of the cursor will be saved. Only data and the state will be cleared. You need to call this first to enable either type of Statement caching. When both types of Statement caching are enabled, the \<it\> size \</size\> is the total number of cursors cached for both the schemes together.
      Parameters:
      `size` - Size of the Cache

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setStmtCacheSize

          public void setStmtCacheSize(int size,
                                       boolean clearMetaData)
                                throws SQLException

      Set the statement cache size. Default is 0. You cannot set this for logicalhandles obtained from this pool. If more than \<it\> size \</it\> cursors are already cached than they will be closed. By default, the meta data of the cursor will be saved. But if clearMetaData is set to true, even that will be cleared. You need to call this first to enable either type of Statement caching. When both types of Statement caching are enabled, the \<it\> size \</size\> is the total number of cursors cached for both the schemes together.
      Parameters:
      `size` - Size of the Cache

      `clearMetaData` - Whether the state has to be cleared or not

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStmtCacheSize

          public int getStmtCacheSize()

      Return the size of Statement Cache.
      Returns:
      int Size of Statement Cache. If not set, the default 0 is returned.

    <!-- -->

    - #### isStmtCacheEnabled

          public boolean isStmtCacheEnabled()

      Check whether Statement Caching is enabled for this pool or Not.

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Overrides:
      [`getConnectionDuringExceptionHandling`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

      Overrides:
      [`debug`](OracleDataSource.md) in class [`OracleDataSource`](OracleDataSource.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOCIConnectionPool.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSourceFactory.md)
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
