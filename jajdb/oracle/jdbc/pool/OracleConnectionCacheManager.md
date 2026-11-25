Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCacheManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionCacheCallback.md)
- [Next Class](OracleConnectionPoolDataSource.md)

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

## Class OracleConnectionCacheManager

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OracleConnectionCacheManager

<!-- -->

-

  ------------------------------------------------------------------------

  Deprecated. 
  Use Oracle Universal Connection Pool instead. Connection Cache Manager class for the Implicit Connection Caching Mechanism.


      public class OracleConnectionCacheManager
      extends Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                                                  | Field and Description                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                 | `EVENT_DELIMITER`<br>Deprecated. <br>                    |
    | `protected static int`                                                                                                                             | `FAILOVER_EVENT_TYPE_HOST`<br>Deprecated. <br>           |
    | `protected static int`                                                                                                                             | `FAILOVER_EVENT_TYPE_SERVICE`<br>Deprecated. <br>        |
    | `protected int`                                                                                                                                    | `failoverEnabledCacheCount`<br>Deprecated. <br>          |
    | `protected oracle.jdbc.pool.OracleFailoverEventHandlerThread`                                                                                      | `failoverEventHandlerThread`<br>Deprecated. <br>         |
    | `protected int[]`                                                                                                                                  | `fatalErrorCodes`<br>Deprecated. <br>                    |
    | `protected `[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)                                  | `m_connCache`<br>Deprecated. <br>                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                           | `PHYSICAL_CONNECTION_CLOSED_COUNT`<br>Deprecated. <br>   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                           | `PHYSICAL_CONNECTION_CREATED_COUNT`<br>Deprecated. <br>  |
    | `static int`                                                                                                                                       | `REFRESH_ALL_CONNECTIONS`<br>Deprecated. <br>            |
    | `static int`                                                                                                                                       | `REFRESH_INVALID_CONNECTIONS`<br>Deprecated. <br>        |
    | `static boolean`                                                                                                                                   | `TRACE`<br>Deprecated. <br>                              |
    | `protected static `[`AtomicInteger`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicInteger.html?is-external=true) | `UNNAMED_CACHE_COUNT`<br>Deprecated. <br>                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |---------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                                                                        | `checkAndStartThread``(`[`Thread`](http://download.oracle.com/javase/8/docs/api/java/lang/Thread.html?is-external=true)` thr)`<br>Deprecated. <br>Check and start the Failover thread.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `protected void`                                                                                        | `cleanupFCFEventHandlerThread``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `protected void`                                                                                        | `cleanupFCFThreads``(oracle.jdbc.pool.OracleImplicitConnectionCache oicc)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `protected void`                                                                                        | `cleanupFCFWorkerThread``(oracle.jdbc.pool.OracleImplicitConnectionCache oicc)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `createCache``(`[`OracleDataSource`](OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using an auto-generated Connection Cache name, and the supplied Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.                                                                                                                                                                                                     |
    | `void`                                                                                                  | `createCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, `[`OracleDataSource`](OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using the supplied Connection Cache name, and the Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.                                                                                                      |
    | `protected void`                                                                                        | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`<br>Deprecated. <br>                                                                                                                                                                          |
    | `void`                                                                                                  | `disableCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Disable a given connection cache                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `enableCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Enable a given connection cache                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                               | `existsCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Check if connection cache exists.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `protected boolean`                                                                                     | `failoverEnabledCacheExists``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getCacheNameList``()`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Get all the cache names managed by this connection cache manager                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true) | `getCacheProperties``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Get the connection cache properties corresponding to the cache name.                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static OracleConnectionCacheManager`                                                                   | `getConnectionCacheManagerInstance``()`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Returns the static ConnectionCacheManager Instance. If necessary a new instance is created and returned to the caller.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `protected oracle.jdbc.internal.OracleConnection`                                                       | `getConnectionDuringExceptionHandling``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `int[]`                                                                                                 | `getConnectionErrorCodes``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                   | `getNumberOfActiveConnections``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Get the number of connections already in use (checked out connections)                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                   | `getNumberOfAvailableConnections``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Get the number connections in the cache, that are available for use                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)               | `getStatistics``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Get the statistics about the implicit connection cache. The stats contains the number of connections opened and the number of connections closed.                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                               | `isFatalConnectionError``(`[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` se)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `protected void`                                                                                        | `parseRuntimeLoadBalancingEvent``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` service, byte[] eventBody)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `purgeCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, boolean cleanupCheckedOutConnections)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Purges Connections in the Connection Cache. A boolean flag indicates whether all connections in the cache are cleaned up(including checkedout connections) or just the connections in the cache                                                                                                                                                                                                                                       |
    | `void`                                                                                                  | `refreshCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, int mode)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Refreshes Connections in the Connection Cache.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `reinitializeCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Reinitialize a connection cache using the new set of properties supplied                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `removeCache``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, long waitTimeout)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Removes the Connection Cache, associated with the given Connection Cache Name. When a timeout value is specified, the remove processing pauses for the specified period of time, before proceeding to remove the connection cache.                                                                                                                                                                                                                       |
    | `void`                                                                                                  | `setConnectionErrorCodes``(int[] fatalErrorCodes)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                  | `setConnectionPoolDataSource``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, `[`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true)` ds)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Sets the ConnectionPoolDataSource that may be used to create the implicit connection cache. If the connections are already created on the connection cache, then an exception is thrown. If no connections are opened, then the new ConnectionPoolDataSource is used and may overwrite the previous one, if any. |
    | `protected void`                                                                                        | `verifyAndHandleEvent``(int eventType, byte[] eventBody)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### m_connCache

          protected Hashtable m_connCache

      Deprecated. 

    <!-- -->

    - #### REFRESH_INVALID_CONNECTIONS

          public static final int REFRESH_INVALID_CONNECTIONS

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### REFRESH_ALL_CONNECTIONS

          public static final int REFRESH_ALL_CONNECTIONS

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PHYSICAL_CONNECTION_CREATED_COUNT

          public static final String PHYSICAL_CONNECTION_CREATED_COUNT

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PHYSICAL_CONNECTION_CLOSED_COUNT

          public static final String PHYSICAL_CONNECTION_CLOSED_COUNT

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_EVENT_TYPE_SERVICE

          protected static final int FAILOVER_EVENT_TYPE_SERVICE

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_EVENT_TYPE_HOST

          protected static final int FAILOVER_EVENT_TYPE_HOST

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EVENT_DELIMITER

          protected static final String EVENT_DELIMITER

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### failoverEventHandlerThread

          protected oracle.jdbc.pool.OracleFailoverEventHandlerThread failoverEventHandlerThread

      Deprecated. 

    <!-- -->

    - #### fatalErrorCodes

          protected int[] fatalErrorCodes

      Deprecated. 

    <!-- -->

    - #### failoverEnabledCacheCount

          protected int failoverEnabledCacheCount

      Deprecated. 

    <!-- -->

    - #### UNNAMED_CACHE_COUNT

          protected static AtomicInteger UNNAMED_CACHE_COUNT

      Deprecated. 

    <!-- -->

    - #### TRACE

          public static final boolean TRACE

      Deprecated. 
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getConnectionCacheManagerInstance

          public static OracleConnectionCacheManager getConnectionCacheManagerInstance()
                                                                                throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Returns the static ConnectionCacheManager Instance. If necessary a new instance is created and returned to the caller.
      Parameters:
      `None` -

      Returns:
      OracleConnectionCacheManager object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### createCache

          public String createCache(OracleDataSource ods,
                                    Properties cacheProperties)
                             throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Creates a connection cache using an auto-generated Connection Cache name, and the supplied Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.
      Parameters:
      `ods` - OracleDataSource object

      `cacheProperties` - Connection Cache Properties for this cache

      Returns:
      The auto-generated Connection Cache Name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### createCache

          public void createCache(String cacheName,
                                  OracleDataSource ods,
                                  Properties cacheProperties)
                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Creates a connection cache using the supplied Connection Cache name, and the Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.
      Parameters:
      `cacheName` - Connection Cache Name

      `ods` - OracleDataSource object

      `cacheProperties` - Connection Cache Properties for this cache

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### removeCache

          public void removeCache(String cacheName,
                                  long waitTimeout)
                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Removes the Connection Cache, associated with the given Connection Cache Name. When a timeout value is specified, the remove processing pauses for the specified period of time, before proceeding to remove the connection cache.
      Parameters:
      `cacheName` - Connection Cache Name

      `waitTimeout` - Timeout value, specified in seconds. A zero or a positive value will be the time allowed before closure of the cache. A negative timeout prompts aborting all the connections before close.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### reinitializeCache

          public void reinitializeCache(String cacheName,
                                        Properties cacheProperties)
                                 throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Reinitialize a connection cache using the new set of properties supplied
      Parameters:
      `cacheName` - Connection Cache Name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### existsCache

          public boolean existsCache(String cacheName)
                              throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Check if connection cache exists.
      Parameters:
      `cacheName` - Connection Cache Name

      Returns:
      true or false, depending on whether the Connection Cache exists

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### enableCache

          public void enableCache(String cacheName)
                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Enable a given connection cache
      Parameters:
      `cacheName` - Connection Cache Name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### disableCache

          public void disableCache(String cacheName)
                            throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Disable a given connection cache
      Parameters:
      `cacheName` - Connection Cache Name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### refreshCache

          public void refreshCache(String cacheName,
                                   int mode)
                            throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Refreshes Connections in the Connection Cache.
      Parameters:
      `cacheName` - Connection Cache Name

      `mode` - The operation to be done on the cache. Operation modes are, REFRESH_INVALID_CONNECTIONS - Refresh invalid connection on the node which is down. REFRESH_ALL_CONNECTIONS - Refresh all connection on the node which is down.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### purgeCache

          public void purgeCache(String cacheName,
                                 boolean cleanupCheckedOutConnections)
                          throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Purges Connections in the Connection Cache. A boolean flag indicates whether all connections in the cache are cleaned up(including checkedout connections) or just the connections in the cache
      Parameters:
      `cacheName` - Connection Cache Name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getCacheProperties

          public Properties getCacheProperties(String cacheName)
                                        throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Get the connection cache properties corresponding to the cache name.
      Parameters:
      `cacheName` - Connection Cache Name

      Returns:
      Connection Cache Properties

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getCacheNameList

          public String[] getCacheNameList()
                                    throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Get all the cache names managed by this connection cache manager
      Parameters:
      `None` -

      Returns:
      List of Connection Cache Names, returned as a String Array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getNumberOfAvailableConnections

          public int getNumberOfAvailableConnections(String cacheName)
                                              throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Get the number connections in the cache, that are available for use
      Parameters:
      `cacheName` - Connection Cache Name

      Returns:
      Number of Connections in the Cache

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getNumberOfActiveConnections

          public int getNumberOfActiveConnections(String cacheName)
                                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Get the number of connections already in use (checked out connections)
      Parameters:
      `cacheName` - Connection Cache Name

      Returns:
      Number of Connections checked out

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setConnectionPoolDataSource

          public void setConnectionPoolDataSource(String cacheName,
                                                  ConnectionPoolDataSource ds)
                                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Sets the ConnectionPoolDataSource that may be used to create the implicit connection cache. If the connections are already created on the connection cache, then an exception is thrown. If no connections are opened, then the new ConnectionPoolDataSource is used and may overwrite the previous one, if any.
      Parameters:
      `cacheName` - Connection Cache Name

      `ds` - a datasource from which the Implicit Cache can create PooledConnections.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - A ConnectionPoolDataSource object already exists and connections are already open.

    <!-- -->

    - #### verifyAndHandleEvent

          protected void verifyAndHandleEvent(int eventType,
                                              byte[] eventBody)
                                       throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### checkAndStartThread

          protected void checkAndStartThread(Thread thr)
                                      throws SQLException

      Deprecated. 
      Check and start the Failover thread. isAlive() returns false, only if the thread state is (1) New thread (2) Terminated

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### failoverEnabledCacheExists

          protected boolean failoverEnabledCacheExists()

      Deprecated. 

    <!-- -->

    - #### parseRuntimeLoadBalancingEvent

          protected void parseRuntimeLoadBalancingEvent(String service,
                                                        byte[] eventBody)
                                                 throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### cleanupFCFThreads

          protected void cleanupFCFThreads(oracle.jdbc.pool.OracleImplicitConnectionCache oicc)
                                    throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### cleanupFCFWorkerThread

          protected void cleanupFCFWorkerThread(oracle.jdbc.pool.OracleImplicitConnectionCache oicc)
                                         throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### cleanupFCFEventHandlerThread

          protected void cleanupFCFEventHandlerThread()
                                               throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isFatalConnectionError

          public boolean isFatalConnectionError(SQLException se)

      Deprecated. 

    <!-- -->

    - #### setConnectionErrorCodes

          public void setConnectionErrorCodes(int[] fatalErrorCodes)
                                       throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionErrorCodes

          public int[] getConnectionErrorCodes()
                                        throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStatistics

          public Map getStatistics(String cacheName)
                            throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead. Get the statistics about the implicit connection cache. The stats contains the number of connections opened and the number of connections closed.
      Parameters:
      `cacheName` - Name of the cache

      Returns:
      A map file containing the value of key: CONNECTION_CREATED_COUNT Number of connections opened. key: CONNECTION_CLOSED_COUNT Number of connections closed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Deprecated. 

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

      Deprecated. 

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCacheManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionCacheCallback.md)
- [Next Class](OracleConnectionPoolDataSource.md)

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
