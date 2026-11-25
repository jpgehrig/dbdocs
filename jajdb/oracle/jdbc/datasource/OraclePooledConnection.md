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

- [Prev Class](OracleDataSource.md)
- [Next Class](OracleXAConnection.md)

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

## Interface OraclePooledConnection

- All Superinterfaces:
  [PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleXAConnection](OracleXAConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [OraclePooledConnection](../pool/OraclePooledConnection.md), [OracleXAConnection](../xa/OracleXAConnection.md), [OracleXAConnection](../xa/client/OracleXAConnection.md), [OracleXAHeteroConnection](../xa/client/OracleXAHeteroConnection.md)

  ------------------------------------------------------------------------



      public interface OraclePooledConnection
      extends PooledConnection

  This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                     |
    |----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true) | `getCallWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Searches the explicit cache for a match on key.                                                                                                                                                                                               |
    | `boolean`                                                                                                            | `getExplicitCachingEnabled``()`<br>Checks if explicit cache is currently enabled.                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                            | `getImplicitCachingEnabled``()`<br>Checks if implicit cache is currently enabled.                                                                                                                                                                                                                                                                                          |
    | `long`                                                                                                               | `getLastAccessedTime``()`<br>Get the last accessed time on the PooledConnection.                                                                                                                                                                                                                                                                                           |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)               | `getLogicalHandle``()`<br>Return the logical handle to the caller.                                                                                                                                                                                                                                                                                                         |
    | `int`                                                                                                                | `getStatementCacheSize``()`<br>Returns the current size of the application cache.                                                                                                                                                                                                                                                                                          |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true) | `getStatementWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Searches the explicit cache for a match on key.                                                                                                                                                                                          |
    | [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)   | `getXAResource``()`<br>Return an XA resource to the caller.                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                               | `purgeExplicitCache``()`<br>Removes all existing statements from the explicit cache, after which it will be empty.                                                                                                                                                                                                                                                         |
    | `void`                                                                                                               | `purgeImplicitCache``()`<br>Removes all existing statements from the implicit cache, after which it will be empty.                                                                                                                                                                                                                                                         |
    | `void`                                                                                                               | `registerCloseCallback``(oracle.jdbc.driver.OracleCloseCallback occ, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` privData)`<br>Registers a close callback.                                                                                                                                                           |
    | `void`                                                                                                               | `registerImplicitCacheConnectionEventListener``(`[`ConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionEventListener.html?is-external=true)` cel)`<br>Register an event listener for the implicit connection cache.                                                                                                                 |
    | `void`                                                                                                               | `setExplicitCachingEnabled``(boolean cache)`<br>Enables or disables the explicit cache.                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                               | `setImplicitCachingEnabled``(boolean cache)`<br>Enables or disables the implicit cache.                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                               | `setLastAccessedTime``(long lastAccessedTime)`<br>Set the last accessed time on the PooledConnection.                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                               | `setShardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                |
    | `boolean`                                                                                                            | `setShardingKeyIfValid``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection. |
    | `void`                                                                                                               | `setStatementCacheSize``(int size)`<br>Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).                                                                                                                                                                                                                 |

    - ### Methods inherited from interface javax.sql.[PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      [`addConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`addStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addStatementEventListener_javax_sql_StatementEventListener_)`, `[`close`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#close__)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#getConnection__)`, `[`removeConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`removeStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeStatementEventListener_javax_sql_StatementEventListener_)

<!-- -->

- - ### Method Detail

    - #### getLogicalHandle

          Connection getLogicalHandle()
                               throws SQLException

      Return the logical handle to the caller. This logical handle refers to the physical connection that is pooled.

      Returns:
      a Connection object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setLastAccessedTime

          void setLastAccessedTime(long lastAccessedTime)
                            throws SQLException

      Set the last accessed time on the PooledConnection. This is used by the inactivity timeout thread

      Parameters:
      `lastAccessedTime` - last accessed time in milliseconds

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLastAccessedTime

          long getLastAccessedTime()
                            throws SQLException

      Get the last accessed time on the PooledConnection. This is used by the inactivity timeout thread

      Returns:
      long (milliseconds)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### registerCloseCallback

          void registerCloseCallback(oracle.jdbc.driver.OracleCloseCallback occ,
                                     Object privData)

      Registers a close callback.

      Parameters:
      `occ` - The callback to be registered.

      `privData` - Private data object to be passed to the callback.

    <!-- -->

    - #### registerImplicitCacheConnectionEventListener

          void registerImplicitCacheConnectionEventListener(ConnectionEventListener cel)

      Register an event listener for the implicit connection cache.

      Parameters:
      `cel` - The listener to be registered

    <!-- -->

    - #### setStatementCacheSize

          void setStatementCacheSize(int size)
                              throws SQLException

      Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).
      Parameters:
      `size` - Requested size of the cache. If the existing cache size is less than size, statements will be purged to reduce the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if size \< 0, or if called on a logical connection.

    <!-- -->

    - #### getStatementCacheSize

          int getStatementCacheSize()
                             throws SQLException

      Returns the current size of the application cache. This is valid on both physical and logical connections.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          void setImplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Enables or disables the implicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Parameters:
      `cache` - If true, then implicit caching will be enabled. If false, then any existing statements will be purged and the implicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getImplicitCachingEnabled

          boolean getImplicitCachingEnabled()
                                     throws SQLException

      Checks if implicit cache is currently enabled. Returns true if the implicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          void setExplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Enables or disables the explicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Parameters:
      `cache` - If true, then explicit caching will be enabled. If false, then any existing statements will be purged and the explicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          boolean getExplicitCachingEnabled()
                                     throws SQLException

      Checks if explicit cache is currently enabled. Returns true if the explicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeImplicitCache

          void purgeImplicitCache()
                           throws SQLException

      Removes all existing statements from the implicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeExplicitCache

          void purgeExplicitCache()
                           throws SQLException

      Removes all existing statements from the explicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStatementWithKey

          PreparedStatement getStatementWithKey(String key)
                                         throws SQLException

      Searches the explicit cache for a match on key. If found, the statement is returned, with the parameter and define metadata identical to the last usage. If a CallableStatement is found (instead of a PreparedStatement, ORA-17125 is raised. If no match is found, or if explicit caching is not enabled, null is returned.
      Parameters:
      `key` - Specified key to search for

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCallWithKey

          CallableStatement getCallWithKey(String key)
                                    throws SQLException

      Searches the explicit cache for a match on key. If found, the statement is returned, with the parameter and define metadata identical to the last usage. If a PreparedStatement is found (instead of a CallableStatement, ORA-17125 is raised. If no match is found, or if explicit caching is not enabled, null is returned.
      Parameters:
      `key` - Specified key to search for

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getXAResource

          XAResource getXAResource()
                            throws SQLException

      Return an XA resource to the caller. This is just a placeholder. Only the one on XAConnection is meaningful.
      Returns:
      the XAResource (null if error occurs)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

    <!-- -->

    - #### setShardingKeyIfValid

          boolean setShardingKeyIfValid(OracleShardingKey shardingKey,
                                        OracleShardingKey superShardingKey,
                                        int timeout)
                                 throws SQLException

      Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection.
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

          void setShardingKey(OracleShardingKey shardingKey,
                              OracleShardingKey superShardingKey)
                       throws SQLException

      Sets the sharding key and the super sharding key on this connection.
      Parameters:
      `shardingKey` - sharding key to be set on this connection

      `superShardingKey` - Super Sharding key to be set on this connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while setting the sharding keys on this connection.

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

- [Prev Class](OracleDataSource.md)
- [Next Class](OracleXAConnection.md)

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
