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

- [Prev Class](OracleConnectionPoolDataSourceImpl.md)
- [Next Class](OracleDataSourceFactory.md)

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

## Interface OracleDataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md), [OracleXADataSource](OracleXADataSource.md)

  ------------------------------------------------------------------------



      public interface OracleDataSource
      extends OracleDataSource

  A data source that supports transparent failover replay of JDBC operations.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                        | Field and Description       |
    |----------------------------------------------------------------------------------------------------------|-----------------------------|
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTIES`     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DATA_SOURCE_NAME`          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DATABASE_NAME`             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DESCRIPTION`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `EXPLICIT_CACHING_ENABLED`  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `IMPLICIT_CACHING_ENABLED`  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `MAX_STATEMENTS`            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_PROTOCOL`          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PASSWORD`                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PORT_NUMBER`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `ROLE_NAME`                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `SERVER_NAME`               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `URL`                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `USER`                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                                                                              |
    |-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                          | `clearReplayStatistics``()`<br>Clears replay statistics accumulated so far on all connection created by this data source.                                                                                                                                                                           |
    | `oracle.jdbc.replay.internal.ConnectionInitializationCallback`                                  | `getConnectionInitializationCallback``()`<br>Obtains the registered connection initialization callback, if any.                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` propertyName)`<br>Gets the specified connection property that are set on this data source.                                                                               |
    | `boolean`                                                                                       | `getExplicitCachingEnabled``()`<br>Returns the current value of the **explicitCachingEnabled** property.                                                                                                                                                                                            |
    | `boolean`                                                                                       | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.                                                                                                                                                                  |
    | `int`                                                                                           | `getMaxStatements``()`<br>Returns the current value of the **maxStatements** property.                                                                                                                                                                                                              |
    | [`ReplayStatistics`](ReplayStatistics.md)                                                       | `getReplayStatistics``()`<br>Obtains replay statistics accumulated so far.                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getRoleName``()`<br>Gets the data source role name.                                                                                                                                                                                                                                                |
    | `void`                                                                                          | `registerConnectionInitializationCallback``(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)`<br>Registers a connection initialization callback.                                                                                                                                   |
    | `void`                                                                                          | `setConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets a connection property on the connection factory. |
    | `void`                                                                                          | `setExplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache.                                                                                                                                            |
    | `void`                                                                                          | `setImplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit statement cache.                                                                                                                                  |
    | `void`                                                                                          | `setMaxStatements``(int max)`<br>Specifies the value of the **maxStatements** property.                                                                                                                                                                                                             |
    | `void`                                                                                          | `setRoleName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` roleName)`<br>Sets the data source role name.                                                                                                                                      |
    | `void`                                                                                          | `unregisterConnectionInitializationCallback``(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)`<br>Unregisters a specified connection initialization callback.                                                                                                                     |

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

- - ### Field Detail

    - #### USER

          static final String USER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### URL

          static final String URL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PASSWORD

          static final String PASSWORD

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERVER_NAME

          static final String SERVER_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PORT_NUMBER

          static final String PORT_NUMBER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATABASE_NAME

          static final String DATABASE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATA_SOURCE_NAME

          static final String DATA_SOURCE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DESCRIPTION

          static final String DESCRIPTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NETWORK_PROTOCOL

          static final String NETWORK_PROTOCOL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ROLE_NAME

          static final String ROLE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTIES

          static final String CONNECTION_PROPERTIES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MAX_STATEMENTS

          static final String MAX_STATEMENTS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IMPLICIT_CACHING_ENABLED

          static final String IMPLICIT_CACHING_ENABLED

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EXPLICIT_CACHING_ENABLED

          static final String EXPLICIT_CACHING_ENABLED

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setRoleName

          void setRoleName(String roleName)
                    throws SQLException

      Sets the data source role name.
      Specified by:
      [`setRoleName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `roleName` - data source role name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRoleName

          String getRoleName()

      Gets the data source role name.
      Specified by:
      [`getRoleName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      data source role name.

    <!-- -->

    - #### registerConnectionInitializationCallback

          void registerConnectionInitializationCallback(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)
                                                 throws SQLException

      Registers a connection initialization callback.
      Parameters:
      `cbk` - The `ConnectionInitializationCallback` object to be registered.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there is a callback already registered with the pool.

    <!-- -->

    - #### unregisterConnectionInitializationCallback

          void unregisterConnectionInitializationCallback(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)
                                                   throws SQLException

      Unregisters a specified connection initialization callback.
      Parameters:
      `cbk` - The `ConnectionInitializationCallback` object to be unregistered.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If callback removal fails.

    <!-- -->

    - #### getConnectionInitializationCallback

          oracle.jdbc.replay.internal.ConnectionInitializationCallback getConnectionInitializationCallback()

      Obtains the registered connection initialization callback, if any.
      Returns:
      The registered `ConnectionInitializationCallback`, or null if there is no callback registered.

    <!-- -->

    - #### getConnectionProperty

          String getConnectionProperty(String propertyName)

      Gets the specified connection property that are set on this data source.
      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection property. Null if the property is not set.

    <!-- -->

    - #### setConnectionProperty

          void setConnectionProperty(String name,
                                     String value)
                              throws SQLException

      Sets a connection property on the connection factory. This is used only for DataSource connection factories that also support connection properties; for example, the `oracle.jdbc.pool.OracleDataSource` in the Oracle JDBC driver.
      Parameters:
      `name` - The name of the connection property to be set on the connection factory class.

      `value` - The value of the connection property to be set on the connection factory class.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If any exception occurred while setting the connection property.

      See Also:
      `setConnectionFactoryProperties`

    <!-- -->

    - #### setMaxStatements

          void setMaxStatements(int max)
                         throws SQLException

      Specifies the value of the **maxStatements** property. This is the size of the statement cache used by both implicit and explicit caching. This value does not apply to the statement cache size of connections created by ImplicitStatementCache for which the cache size is set through a java.util.Properties object.
      Specified by:
      [`setMaxStatements`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `max` - Requested size of the cache. If the existing cache size is less than max, statements will be purged to reduce the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if max \< 0

    <!-- -->

    - #### getMaxStatements

          int getMaxStatements()
                        throws SQLException

      Returns the current value of the **maxStatements** property.
      Specified by:
      [`getMaxStatements`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          void setImplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit statement cache. Note that this is independent of the cache size that is set with setMaxStatements().
      Specified by:
      [`setImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `cache` - If true, then implicit caching is enabled. If false, then any existing statement is purged and the implicit caching is disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getImplicitCachingEnabled

          boolean getImplicitCachingEnabled()
                                     throws SQLException

      getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.
      Specified by:
      [`getImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          void setExplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache. Note that this is independent of the cache size, which is set with setMaxStatements().
      Specified by:
      [`setExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `cache` - If true, then explicit caching is enabled. If false, then any existing statement is purged and the explicit caching is disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          boolean getExplicitCachingEnabled()
                                     throws SQLException

      Returns the current value of the **explicitCachingEnabled** property.
      Specified by:
      [`getExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getReplayStatistics

          ReplayStatistics getReplayStatistics()

      Obtains replay statistics accumulated so far. These reflect replay actions across all the connections created by this data source. It is recommended that this call be made when the connections are quiescent and there are few new connections being opened.
      Returns:
      A replay statistics object containing all the metrics.

    <!-- -->

    - #### clearReplayStatistics

          void clearReplayStatistics()

      Clears replay statistics accumulated so far on all connection created by this data source. It is recommended that this call be made when the connections are quiescent and there are few new connections being opened.

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

- [Prev Class](OracleConnectionPoolDataSourceImpl.md)
- [Next Class](OracleDataSourceFactory.md)

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
