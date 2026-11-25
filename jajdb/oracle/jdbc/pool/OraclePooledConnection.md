Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOCIConnectionPool.md)
- [Next Class](OraclePooledConnectionBuilderImpl.md)

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

## Class OraclePooledConnection

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OraclePooledConnection

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true), [OraclePooledConnection](../datasource/OraclePooledConnection.md)

  <!-- -->

  Direct Known Subclasses:
  [OracleXAConnection](../xa/OracleXAConnection.md)

  ------------------------------------------------------------------------



      public class OraclePooledConnection
      extends Object
      implements OraclePooledConnection, Serializable

  An OraclePooledConnection object is a connection object that provides hooks for connection pool management. A PooledConnection object represents a physical connection to a data source. It implements javax.sql.PooledConnection

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                           | Field and Description                 |
    |-------------------------------------------------------------------------------------------------------------|---------------------------------------|
    | `protected boolean`                                                                                         | `autoCommit`                          |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)     | `cachedConnectionAttributes`          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `close_callback_string`               |
    | `int`                                                                                                       | `closeOption`                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `connect_auto_commit_string`          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `connection_properties_string`        |
    | `protected boolean`                                                                                         | `connectionMarkedDown`                |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `dataSourceDbUniqNameKey`             |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `dataSourceHostNameKey`               |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `dataSourceInstanceNameKey`           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `event_listener_string`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `explicit_caching_enabled`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `ExplicitStatementCachingEnabled`     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `implicit_caching_enabled`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `ImplicitStatementCachingEnabled`     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `isClearMetaData`                     |
    | `protected oracle.jdbc.internal.OracleConnection`                                                           | `logicalHandle`                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `LoginTimeout`                        |
    | `protected boolean`                                                                                         | `needToAbort`                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `NO_IMPLICIT_BEGIN_REQUEST_PROPERTY`  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `object_type_map`                     |
    | `protected oracle.jdbc.driver.OracleDriver`                                                                 | `oracleDriver`                        |
    | `protected oracle.jdbc.internal.OracleConnection`                                                           | `physicalConn`                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `pool_auto_commit_string`             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `private_data`                        |
    | `protected oracle.jdbc.internal.OracleConnection`                                                           | `replayConn`                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `sql_exception_string`                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `statement_cache_size`                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `transaction_isolation`               |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)     | `unMatchedCachedConnAttr`             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)    | `url_string`                          |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OraclePooledConnection``()`                                                                                                                                                                                                                                                                                                                                                       |
    | `OraclePooledConnection``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` pc)`<br>Create a Pooled Connection.                                                                                                                                                                                                             |
    | `OraclePooledConnection``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` pc, boolean ac)`<br>Create a Pooled Connection.                                                                                                                                                                                                 |
    | `OraclePooledConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url)`<br>Creates a PooledConnection.                                                                                                                                                                                                                   |
    | `OraclePooledConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Creates a PooledConnection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                               | `addConnectionEventListener``(`[`ConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionEventListener.html?is-external=true)` cel)`<br>Add an event listener.                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                               | `addStatementEventListener``(`[`StatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/StatementEventListener.html?is-external=true)` listener)`                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                               | `close``()`<br>Close the physical connection.                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `protected void`                                                                                                     | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true) | `getCallWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>getCallWithKey Searches the explicit cache for a match on key.                                                                                                                                                                                                                                                                                  |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)               | `getConnection``()`<br>Create an object handle for this physical connection.                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected oracle.jdbc.internal.OracleConnection`                                                                    | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                            | `getExplicitCachingEnabled``()`<br>getExplicitCachingEnabled Returns true if the explicit cache is currently enabled, false otherwise.                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                            | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns true if the implicit cache is currently enabled, false otherwise.                                                                                                                                                                                                                                                                                                                                       |
    | `long`                                                                                                               | `getLastAccessedTime``()`<br>Get the last accessed time on the PooledConnection.                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)               | `getLogicalHandle``()`<br>Return the logical handle to the caller.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)               | `getPhysicalHandle``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                                | `getStatementCacheSize``()`<br>getStatementCacheSize Returns the current size of the application cache.                                                                                                                                                                                                                                                                                                                                                                      |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true) | `getStatementWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>getStatementWithKey Searches the explicit cache for a match on key.                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                                | `getStmtCacheSize``()`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)   | `getXAResource``()`<br>Return an XA resource to the caller.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                            | `isStatementCacheInitialized``()`                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                               | `purgeExplicitCache``()`<br>purgeExplicitCache Removes all existing statements from the explicit cache, after which it will be empty.                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `purgeImplicitCache``()`<br>purgeImplicitCache Removes all existing statements from the implicit cache, after which it will be empty.                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `registerImplicitCacheConnectionEventListener``(`[`ConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionEventListener.html?is-external=true)` cel)`<br>Register an event listener for the implicit connection cache.                                                                                                                                                                                                                   |
    | `void`                                                                                                               | `removeConnectionEventListener``(`[`ConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionEventListener.html?is-external=true)` cel)`<br>Remove an event listener.                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                               | `removeStatementEventListener``(`[`StatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/StatementEventListener.html?is-external=true)` listener)`                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `setConnection``(oracle.jdbc.internal.OracleConnection rconn)`                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `setExplicitCachingEnabled``(boolean cache)`<br>setExplicitCachingEnabled Enables or disables the explicit cache.                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                               | `setImplicitCachingEnabled``(boolean cache)`<br>setImplicitCachingEnabled Enables or disables the implicit cache.                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                               | `setLastAccessedTime``(long lastAccessedTime)`<br>Set the last accessed time on the PooledConnection.                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `setProperties``(`[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)` prop)`                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `setShardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                            | `setShardingKeyIfValid``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection's session.                                                                                         |
    | `void`                                                                                                               | `setStatementCacheSize``(int size)`<br>setStatementCacheSize Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                               | `setStmtCacheSize``(int size)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                               | `setStmtCacheSize``(int size, boolean clearMetaData)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### url_string

          public static final String url_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### pool_auto_commit_string

          public static final String pool_auto_commit_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### object_type_map

          public static final String object_type_map

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### transaction_isolation

          public static final String transaction_isolation

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### statement_cache_size

          public static final String statement_cache_size

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### isClearMetaData

          public static final String isClearMetaData

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ImplicitStatementCachingEnabled

          public static final String ImplicitStatementCachingEnabled

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ExplicitStatementCachingEnabled

          public static final String ExplicitStatementCachingEnabled

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LoginTimeout

          public static final String LoginTimeout

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### connect_auto_commit_string

          public static final String connect_auto_commit_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### implicit_caching_enabled

          public static final String implicit_caching_enabled

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### explicit_caching_enabled

          public static final String explicit_caching_enabled

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### connection_properties_string

          public static final String connection_properties_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### event_listener_string

          public static final String event_listener_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### sql_exception_string

          public static final String sql_exception_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### close_callback_string

          public static final String close_callback_string

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### private_data

          public static final String private_data

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### autoCommit

          protected boolean autoCommit

    <!-- -->

    - #### logicalHandle

          protected transient oracle.jdbc.internal.OracleConnection logicalHandle

    <!-- -->

    - #### physicalConn

          protected transient oracle.jdbc.internal.OracleConnection physicalConn

    <!-- -->

    - #### replayConn

          protected transient oracle.jdbc.internal.OracleConnection replayConn

    <!-- -->

    - #### cachedConnectionAttributes

          public Properties cachedConnectionAttributes

    <!-- -->

    - #### unMatchedCachedConnAttr

          public Properties unMatchedCachedConnAttr

    <!-- -->

    - #### closeOption

          public int closeOption

    <!-- -->

    - #### dataSourceInstanceNameKey

          protected String dataSourceInstanceNameKey

    <!-- -->

    - #### dataSourceHostNameKey

          protected String dataSourceHostNameKey

    <!-- -->

    - #### dataSourceDbUniqNameKey

          protected String dataSourceDbUniqNameKey

    <!-- -->

    - #### connectionMarkedDown

          protected boolean connectionMarkedDown

    <!-- -->

    - #### needToAbort

          protected boolean needToAbort

    <!-- -->

    - #### oracleDriver

          protected transient oracle.jdbc.driver.OracleDriver oracleDriver

    <!-- -->

    - #### NO_IMPLICIT_BEGIN_REQUEST_PROPERTY

          public static final String NO_IMPLICIT_BEGIN_REQUEST_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OraclePooledConnection

          public OraclePooledConnection()

    <!-- -->

    - #### OraclePooledConnection

          public OraclePooledConnection(String url)
                                 throws SQLException

      Creates a PooledConnection.

      Parameters:
      `url` - URL of the physical connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### OraclePooledConnection

          public OraclePooledConnection(String url,
                                        String user,
                                        String passwd)
                                 throws SQLException

      Creates a PooledConnection.

      Parameters:
      `url` - URL of the physical connection.

      `user` - User Name

      `passwd` - Password

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### OraclePooledConnection

          public OraclePooledConnection(Connection pc)

      Create a Pooled Connection.

      Parameters:
      `pc` - The corresponding physical connection.

    <!-- -->

    - #### OraclePooledConnection

          public OraclePooledConnection(Connection pc,
                                        boolean ac)

      Create a Pooled Connection.

      Parameters:
      `pc` - The corresponding physical connection

      `ac` - autoCommit value

  <!-- -->

  - ### Method Detail

    - #### addConnectionEventListener

          public void addConnectionEventListener(ConnectionEventListener cel)

      Add an event listener.

      Specified by:
      [`addConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addConnectionEventListener_javax_sql_ConnectionEventListener_) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      Parameters:
      `cel` - The listener to be added

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Close the physical connection.

      Specified by:
      [`close`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#close__) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Create an object handle for this physical connection. The object returned is a temporary handle used by application code to refer to a physical connection that is being pooled.

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#getConnection__) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      Returns:
      a Connection object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getLogicalHandle

          public Connection getLogicalHandle()
                                      throws SQLException

      Return the logical handle to the caller. This logical handle refers to the physical connection that is pooled.

      Specified by:
      [`getLogicalHandle`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Returns:
      a Connection object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPhysicalHandle

          public Connection getPhysicalHandle()
                                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setLastAccessedTime

          public void setLastAccessedTime(long lastAccessedTime)
                                   throws SQLException

      Set the last accessed time on the PooledConnection. This is used by the inactivity timeout thread

      Specified by:
      [`setLastAccessedTime`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `lastAccessedTime,` - last accessed time in milliseconds

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLastAccessedTime

          public long getLastAccessedTime()
                                   throws SQLException

      Get the last accessed time on the PooledConnection. This is used by the inactivity timeout thread

      Specified by:
      [`getLastAccessedTime`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Returns:
      long (milliseconds)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### removeConnectionEventListener

          public void removeConnectionEventListener(ConnectionEventListener cel)

      Remove an event listener.

      Specified by:
      [`removeConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeConnectionEventListener_javax_sql_ConnectionEventListener_) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      Parameters:
      `cel` - The listener to be removed.

    <!-- -->

    - #### registerImplicitCacheConnectionEventListener

          public void registerImplicitCacheConnectionEventListener(ConnectionEventListener cel)

      Register an event listener for the implicit connection cache.

      Specified by:
      [`registerImplicitCacheConnectionEventListener`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `cel` - The listener to be registered

    <!-- -->

    - #### setStmtCacheSize

          public void setStmtCacheSize(int size)
                                throws SQLException

      Deprecated. 
      Set the statement cache size. Default is 0. You cannot call this for logicalhandles obtained from PooledConnections.
      If more than \<it\> size \</it\> cursors are already cached than they will be closed. By default the meta data of the cursor will be saved. Only data and the state will be cleared. You need to call this first to enable either type of Statement caching. When both types of Statement caching are enabled, the \<it\> size \</size\> is the total number of cursors cached for both the schemes together.

      Parameters:
      `size` - Size of the Cache

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setStmtCacheSize

          public void setStmtCacheSize(int size,
                                       boolean clearMetaData)
                                throws SQLException

      Deprecated. 
      Set the statement cache size. Default is 0. You cannot call this for logicalhandles obtained from PooledConnections.
      If more than \<it\> size \</it\> cursors are already cached than they will be closed. By default, the meta data of the cursor will be saved. But if clearMetaData is set to true, even that will be cleared. You need to call this first to enable either type of Statement caching. When both types of Statement caching are enabled, the \<it\> size \</size\> is the total number of cursors cached for both the schemes together.

      Parameters:
      `size` - Size of the Cache

      `clearMetaData` - Whether the state has to be cleared or not

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStmtCacheSize

          public int getStmtCacheSize()

      Deprecated. 
      Return the size of Statement Cache.
      Returns:
      int Size of Statement Cache. If not set, the default 0 is returned.

    <!-- -->

    - #### setStatementCacheSize

          public void setStatementCacheSize(int size)
                                     throws SQLException

      setStatementCacheSize Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).
      Specified by:
      [`setStatementCacheSize`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `size` - Requested size of the cache. If the existing cache size is less than size, statements will be purged to reduce the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if size \< 0, or if called on a logical connection.

    <!-- -->

    - #### getStatementCacheSize

          public int getStatementCacheSize()
                                    throws SQLException

      getStatementCacheSize Returns the current size of the application cache. This is valid on both physical and logical connections.
      Specified by:
      [`getStatementCacheSize`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          public void setImplicitCachingEnabled(boolean cache)
                                         throws SQLException

      setImplicitCachingEnabled Enables or disables the implicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Specified by:
      [`setImplicitCachingEnabled`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `cache` - If true, then implicit caching will be enabled. If false, then any existing statements will be purged and the implicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getImplicitCachingEnabled

          public boolean getImplicitCachingEnabled()
                                            throws SQLException

      getImplicitCachingEnabled Returns true if the implicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Specified by:
      [`getImplicitCachingEnabled`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          public void setExplicitCachingEnabled(boolean cache)
                                         throws SQLException

      setExplicitCachingEnabled Enables or disables the explicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Specified by:
      [`setExplicitCachingEnabled`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `cache` - If true, then explicit caching will be enabled. If false, then any existing statements will be purged and the explicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          public boolean getExplicitCachingEnabled()
                                            throws SQLException

      getExplicitCachingEnabled Returns true if the explicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Specified by:
      [`getExplicitCachingEnabled`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeImplicitCache

          public void purgeImplicitCache()
                                  throws SQLException

      purgeImplicitCache Removes all existing statements from the implicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Specified by:
      [`purgeImplicitCache`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeExplicitCache

          public void purgeExplicitCache()
                                  throws SQLException

      purgeExplicitCache Removes all existing statements from the explicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Specified by:
      [`purgeExplicitCache`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStatementWithKey

          public PreparedStatement getStatementWithKey(String key)
                                                throws SQLException

      getStatementWithKey Searches the explicit cache for a match on key. If found, the statement is returned, with the paramater and define metadata identical to the last usage. If a CallableStatement is found (instead of a PreparedStatement, ORA-17125 is raised. If no match is found, or if explicit caching is not enabled, null is returned.
      Specified by:
      [`getStatementWithKey`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `key` - Specified key to search for

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCallWithKey

          public CallableStatement getCallWithKey(String key)
                                           throws SQLException

      getCallWithKey Searches the explicit cache for a match on key. If found, the statement is returned, with the paramater and define metadata identical to the last usage. If a PreparedStatement is found (instead of a CallableStatement, ORA-17125 is raised. If no match is found, or if explicit caching is not enabled, null is returned.
      Specified by:
      [`getCallWithKey`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `key` - Specified key to search for

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isStatementCacheInitialized

          public boolean isStatementCacheInitialized()

    <!-- -->

    - #### setProperties

          public final void setProperties(Hashtable prop)

    <!-- -->

    - #### getXAResource

          public XAResource getXAResource()
                                   throws SQLException

      Return an XA resource to the caller. This is just a placeholder. Only the one on XAConnection is meaningful.
      Specified by:
      [`getXAResource`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Returns:
      the XAResource (null if error occurs)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

    <!-- -->

    - #### addStatementEventListener

          public void addStatementEventListener(StatementEventListener listener)

      Specified by:
      [`addStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addStatementEventListener_javax_sql_StatementEventListener_) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

    <!-- -->

    - #### removeStatementEventListener

          public void removeStatementEventListener(StatementEventListener listener)

      Specified by:
      [`removeStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeStatementEventListener_javax_sql_StatementEventListener_) in interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

    <!-- -->

    - #### setConnection

          public void setConnection(oracle.jdbc.internal.OracleConnection rconn)
                             throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setShardingKeyIfValid

          public boolean setShardingKeyIfValid(OracleShardingKey shardingKey,
                                               OracleShardingKey superShardingKey,
                                               int timeout)
                                        throws SQLException

      Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection's session.
      Specified by:
      [`setShardingKeyIfValid`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `shardingKey` - Sharding key to be validated against this connection

      `superShardingKey` - Super Sharding key to be validated against this connection

      `timeout` - Time in seconds before which the validation process is expected to be complete, else the validation process is aborted. The value of the timeout must be set to zero to disable the timeout during the validation.

      Returns:
      true if the connection is valid and the shard keys are valid to be set on this connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is any exception while performing this validation or if timeout value is less than 0.

    <!-- -->

    - #### setShardingKey

          public void setShardingKey(OracleShardingKey shardingKey,
                                     OracleShardingKey superShardingKey)
                              throws SQLException

      Sets the sharding key and the super sharding key on this connection.
      Specified by:
      [`setShardingKey`](../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../datasource/OraclePooledConnection.md)

      Parameters:
      `shardingKey` - sharding key to be set on this connection

      `superShardingKey` - Super Sharding key to be set on this connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while setting the sharding keys on this connection.

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOCIConnectionPool.md)
- [Next Class](OraclePooledConnectionBuilderImpl.md)

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
