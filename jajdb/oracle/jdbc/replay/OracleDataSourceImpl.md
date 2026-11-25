Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSourceFactory.md)
- [Next Class](OracleXADataSource.md)

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

## Class OracleDataSourceImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.replay.OracleDataSourceImpl

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md)

  <!-- -->

  Direct Known Subclasses:
  [OracleConnectionPoolDataSourceImpl](OracleConnectionPoolDataSourceImpl.md)

  ------------------------------------------------------------------------



      public class OracleDataSourceImpl
      extends Object
      implements oracle.jdbc.replay.internal.OracleDataSource, Serializable, Referenceable, ObjectFactory

  JDBC Data Source that supports transparent JDBC operation replay upon a failover.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                                           | Field and Description               |
    |---------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `CHECKSUM_PROPERTY`                 |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                 | `clientChecksum11203x`              |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                 | `clientChecksum12x`                 |
    | `protected `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)                         | `connectionProperties`              |
    | `protected `[`AtomicBoolean`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicBoolean.html?is-external=true) | `doneDumpOnMemoryPressure`          |
    | `protected static int`                                                                                                                      | `FAILOVER_RESTORE_AUTO`             |
    | `protected static int`                                                                                                                      | `FAILOVER_RESTORE_LEVEL1`           |
    | `protected static int`                                                                                                                      | `FAILOVER_RESTORE_NONE`             |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `FAILOVER_RESTORE_PROPERTY`         |
    | `protected static int`                                                                                                                      | `FAILOVER_TYPE_AUTO`                |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `FAILOVER_TYPE_PROPERTY`            |
    | `protected static int`                                                                                                                      | `FAILOVER_TYPE_TRANSACTION`         |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `IGNORE_AC_CONTEXT_PROPERTY`        |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `INITIATION_TIMEOUT_PROPERTY`       |
    | `protected boolean`                                                                                                                         | `isAutoACEnabled`                   |
    | `protected `[`AtomicBoolean`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicBoolean.html?is-external=true) | `isFirstConnection`                 |
    | `protected boolean`                                                                                                                         | `isReplayInDynamicMode`             |
    | `protected boolean`                                                                                                                         | `isStateRestorationAuto`            |
    | `protected boolean`                                                                                                                         | `isTransactionReplayEnabled`        |
    | `protected `[`OracleDataSource`](../pool/OracleDataSource.md)                                                                               | `ods`                               |
    | `protected `[`OracleDataSource`](../pool/OracleDataSource.md)                                                                               | `odsReconnectOnly`                  |
    | `protected oracle.jdbc.internal.OpaqueString`                                                                                               | `password`                          |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `RECONNECT_DELAY_PROPERTY`          |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `RECONNECT_RETRIES_PROPERTY`        |
    | `protected int`                                                                                                                             | `reconnectDelay`                    |
    | `protected `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)                         | `reconnectionProperties`            |
    | `protected int`                                                                                                                             | `reconnectRetries`                  |
    | `protected int`                                                                                                                             | `replayInitiationTimeout`           |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `REQUEST_SIZE_LIMIT_PROPERTY`       |
    | `protected static int`                                                                                                                      | `SESSION_STATE_CONSISTENCY_STATIC`  |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                          | `SESSION_STATE_PROPERTY`            |
    | `protected oracle.jdbc.replay.internal.ReplayableConnection.StateRestorationType`                                                           | `stateRestorationType`              |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                 | `user`                              |

    - ### Fields inherited from interface oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)

      [`CONNECTION_PROPERTIES`](OracleDataSource.md)`, `[`DATA_SOURCE_NAME`](OracleDataSource.md)`, `[`DATABASE_NAME`](OracleDataSource.md)`, `[`DESCRIPTION`](OracleDataSource.md)`, `[`EXPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`IMPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`MAX_STATEMENTS`](OracleDataSource.md)`, `[`NETWORK_PROTOCOL`](OracleDataSource.md)`, `[`PASSWORD`](OracleDataSource.md)`, `[`PORT_NUMBER`](OracleDataSource.md)`, `[`ROLE_NAME`](OracleDataSource.md)`, `[`SERVER_NAME`](OracleDataSource.md)`, `[`URL`](OracleDataSource.md)`, `[`USER`](OracleDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OracleDataSourceImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                             | `clearDoneDumpOnMemoryPressure``()`                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                             | `clearReplayStatistics``()`<br>Clears replay statistics accumulated so far on all connection created by this data source.                                                                                                                                                                                                                                                                                                                                                 |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)                                            | `createConnectionBuilder``()`<br>Creates a new OracleConnectionBuilder instance                                                                                                                                                                                                                                                                                                                                                                                           |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `enableACAndProxifyIfNecessary``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                                                                                                                                                                   |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getConnection``(`[`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)` connBldr)`                                                                                                                                                                                                                                                                                                                                                                     |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` username, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Attempts to obtain a database connection with the specified user and password.                                                                                                                                                 |
    | `oracle.jdbc.replay.internal.ConnectionInitializationCallback`                                                     | `getConnectionInitializationCallback``()`<br>Obtains the registered connection initialization callback, if any.                                                                                                                                                                                                                                                                                                                                                           |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnectionNoProxy``(`[`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                                                                                                                                                                                                                                                                                           |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)            | `getConnectionProperties``()`<br>Gets the connection properties that are set on this data source.                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` propertyName)`<br>Gets the specified connection property that are set on this data source.                                                                                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDatabaseName``()`<br>Gets the database name.                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDataSourceName``()`<br>Gets the data source name.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDescription``()`<br>Gets the data source description.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                          | `getExplicitCachingEnabled``()`<br>Returns the current value of the **explicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                          | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                              | `getLoginTimeout``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true)            | `getLogWriter``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                              | `getMaxStatements``()`<br>Returns the current value of the **maxStatements** property.                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getNetworkProtocol``()`<br>Gets the datasource networkProtocol.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                    | `getObjectInstance``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` refObj, `[`Name`](http://download.oracle.com/javase/8/docs/api/javax/naming/Name.html?is-external=true)` name, `[`Context`](http://download.oracle.com/javase/8/docs/api/javax/naming/Context.html?is-external=true)` nameCtx, `[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)`<?,?> env)`  |
    | [`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)            | `getParentLogger``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `int`                                                                                                              | `getPortNumber``()`<br>Gets the database port number.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `oracle.jdbc.proxy.ProxyFactory`                                                                                   | `getProxyFactory``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`Reference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Reference.html?is-external=true)           | `getReference``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`ReplayStatistics`](ReplayStatistics.md)                                                                          | `getReplayStatistics``()`<br>Obtains replay statistics accumulated so far.                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getReplayStatisticsString``()`                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                                                                                              | `getRequestSizeLimit``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getRoleName``()`<br>Gets the datasource role name.                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getServerName``()`<br>Gets the database server name.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getURL``()`<br>Gets the URL for this datasource.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getUser``()`<br>Gets the user name for this datasource.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                          | `isWrapperFor``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<?> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                            |
    | `void`                                                                                                             | `registerConnectionInitializationCallback``(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)`<br>Registers a ConnectionInitializationCallback with the data source.                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                             | `setConnectionProperties``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` connProperties)`<br>Sets the connection properties on the data source.                                                                                                                                                                                                                                                               |
    | `void`                                                                                                             | `setConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets a connection property on the data source.                                                                                                                                                                              |
    | `void`                                                                                                             | `setDatabaseName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` databaseName)`<br>Sets the database name.                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                             | `setDataSourceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dataSourceName)`<br>Sets the data source name.                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                             | `setDescription``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` description)`<br>Sets the data source description.                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                             | `setExplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache.                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                             | `setImplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit statement cache.                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                             | `setLoginTimeout``(int seconds)`                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                             | `setLogWriter``(`[`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true)` out)`                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                             | `setMaxStatements``(int max)`<br>Specifies the value of the **maxStatements** property.                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                             | `setNetworkProtocol``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` networkProtocol)`<br>Sets the datasource networkProtocol.                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                             | `setPassword``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Sets the password with which connections have to be obtained.                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                             | `setPortNumber``(int portNumber)`<br>Sets the database port number.                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                             | `setRoleName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` roleName)`<br>Sets the datasource role name.                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                             | `setServerName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serverName)`<br>Sets the database server name.                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                             | `setSSLContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.                           |
    | `void`                                                                                                             | `setTokenSupplier``(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`.                                                                                                                                       |
    | `protected void`                                                                                                   | `setupACSpecificProperties``()`                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                             | `setURL``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url)`<br>Sets the URL from which connections have to be obtained.                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                             | `setUser``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` username)`<br>Set the user name with which connections have to be obtained.                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                             | `unregisterConnectionInitializationCallback``(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)`<br>Removes the ConnectionInitializationCallback registered with the data source, if any.                                                                                                                                                                                                                                                                 |
    | `<T> T`                                                                                                            | `unwrap``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<T> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                                  |
    | `void`                                                                                                             | `updateReplayStatistics``(oracle.jdbc.replay.internal.ReplayStatistics newStats)`                                                                                                                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)

<!-- -->

- - ### Field Detail

    - #### ods

          protected OracleDataSource ods

    <!-- -->

    - #### odsReconnectOnly

          protected OracleDataSource odsReconnectOnly

    <!-- -->

    - #### user

          protected String user

    <!-- -->

    - #### password

          protected oracle.jdbc.internal.OpaqueString password

    <!-- -->

    - #### connectionProperties

          protected Properties connectionProperties

    <!-- -->

    - #### reconnectionProperties

          protected Properties reconnectionProperties

    <!-- -->

    - #### isFirstConnection

          protected AtomicBoolean isFirstConnection

    <!-- -->

    - #### RECONNECT_DELAY_PROPERTY

          protected static final String RECONNECT_DELAY_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RECONNECT_RETRIES_PROPERTY

          protected static final String RECONNECT_RETRIES_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### reconnectDelay

          protected int reconnectDelay

    <!-- -->

    - #### reconnectRetries

          protected int reconnectRetries

    <!-- -->

    - #### FAILOVER_TYPE_PROPERTY

          protected static final String FAILOVER_TYPE_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_TYPE_TRANSACTION

          protected static final int FAILOVER_TYPE_TRANSACTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SESSION_STATE_CONSISTENCY_STATIC

          protected static final int SESSION_STATE_CONSISTENCY_STATIC

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_TYPE_AUTO

          protected static final int FAILOVER_TYPE_AUTO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### isTransactionReplayEnabled

          protected boolean isTransactionReplayEnabled

    <!-- -->

    - #### isAutoACEnabled

          protected boolean isAutoACEnabled

    <!-- -->

    - #### SESSION_STATE_PROPERTY

          protected static final String SESSION_STATE_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### isReplayInDynamicMode

          protected boolean isReplayInDynamicMode

    <!-- -->

    - #### FAILOVER_RESTORE_PROPERTY

          protected static final String FAILOVER_RESTORE_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_RESTORE_NONE

          protected static final int FAILOVER_RESTORE_NONE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_RESTORE_LEVEL1

          protected static final int FAILOVER_RESTORE_LEVEL1

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FAILOVER_RESTORE_AUTO

          protected static final int FAILOVER_RESTORE_AUTO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### stateRestorationType

          protected oracle.jdbc.replay.internal.ReplayableConnection.StateRestorationType stateRestorationType

    <!-- -->

    - #### isStateRestorationAuto

          protected boolean isStateRestorationAuto

    <!-- -->

    - #### INITIATION_TIMEOUT_PROPERTY

          protected static final String INITIATION_TIMEOUT_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### replayInitiationTimeout

          protected int replayInitiationTimeout

    <!-- -->

    - #### CHECKSUM_PROPERTY

          protected static final String CHECKSUM_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### clientChecksum12x

          protected final String clientChecksum12x

    <!-- -->

    - #### clientChecksum11203x

          protected final String clientChecksum11203x

    <!-- -->

    - #### IGNORE_AC_CONTEXT_PROPERTY

          protected static final String IGNORE_AC_CONTEXT_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### REQUEST_SIZE_LIMIT_PROPERTY

          protected static final String REQUEST_SIZE_LIMIT_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### doneDumpOnMemoryPressure

          protected AtomicBoolean doneDumpOnMemoryPressure

  <!-- -->

  - ### Constructor Detail

    - #### OracleDataSourceImpl

          public OracleDataSourceImpl()

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnection

          public Connection getConnection(String username,
                                          String passwd)
                                   throws SQLException

      Attempts to obtain a database connection with the specified user and password.
      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Parameters:
      `username` - The database user on whose behalf the connection is being made.

      `passwd` - The user's password.

      Returns:
      A Connection to the database.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          protected Connection getConnection(OracleConnectionBuilderImpl connBldr)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionNoProxy

          public Connection getConnectionNoProxy(OracleConnectionBuilderImpl connBuilder)
                                          throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setupACSpecificProperties

          protected void setupACSpecificProperties()
                                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### enableACAndProxifyIfNecessary

          protected Connection enableACAndProxifyIfNecessary(Connection conn,
                                                             OracleConnectionBuilderImpl connBuilder)
                                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLogWriter

          public PrintWriter getLogWriter()
                                   throws SQLException

      Specified by:
      [`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setLogWriter

          public void setLogWriter(PrintWriter out)
                            throws SQLException

      Specified by:
      [`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setLoginTimeout

          public void setLoginTimeout(int seconds)
                               throws SQLException

      Specified by:
      [`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLoginTimeout

          public int getLoginTimeout()
                              throws SQLException

      Specified by:
      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getUser

          public String getUser()

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Gets the user name for this datasource. Will return the default value ("scott") if not set before.
      Specified by:
      [`getUser`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

    <!-- -->

    - #### setUser

          public void setUser(String username)
                       throws SQLException

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Set the user name with which connections have to be obtained.
      Specified by:
      [`setUser`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPassword

          public void setPassword(String passwd)
                           throws SQLException

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Sets the password with which connections have to be obtained. The default value is "tiger".
      Specified by:
      [`setPassword`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `passwd` - Passowrd to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getURL

          public String getURL()

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Gets the URL for this datasource. Will return the default value "jdbc:oracle:oci8:@" if not set before.
      Specified by:
      [`getURL`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

    <!-- -->

    - #### setURL

          public void setURL(String url)
                      throws SQLException

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Sets the URL from which connections have to be obtained. If URL is set all other properties like databasename, servername, portNumber, network protocol, tnsentry, and driver Type will be ignored.
      Specified by:
      [`setURL`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `url` - URL to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setServerName

          public void setServerName(String serverName)
                             throws SQLException

      Sets the database server name.
      Specified by:
      [`setServerName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `serverName` - Database server name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getServerName

          public String getServerName()

      Gets the database server name.
      Specified by:
      [`getServerName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      Database server name.

    <!-- -->

    - #### setPortNumber

          public void setPortNumber(int portNumber)
                             throws SQLException

      Sets the database port number.
      Specified by:
      [`setPortNumber`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `portNumber` - Database port number to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPortNumber

          public int getPortNumber()

      Gets the database port number.
      Specified by:
      [`getPortNumber`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      Database port number.

    <!-- -->

    - #### setDatabaseName

          public void setDatabaseName(String databaseName)
                               throws SQLException

      Sets the database name.
      Specified by:
      [`setDatabaseName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `databaseName` - Database name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDatabaseName

          public String getDatabaseName()

      Gets the database name.
      Specified by:
      [`getDatabaseName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      Database name.

    <!-- -->

    - #### setDataSourceName

          public void setDataSourceName(String dataSourceName)
                                 throws SQLException

      Sets the data source name.
      Specified by:
      [`setDataSourceName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `dataSourceName` - data source name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDataSourceName

          public String getDataSourceName()

      Gets the data source name.
      Specified by:
      [`getDataSourceName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      data source name.

    <!-- -->

    - #### setDescription

          public void setDescription(String description)
                              throws SQLException

      Sets the data source description.
      Specified by:
      [`setDescription`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `description` - data source description to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDescription

          public String getDescription()

      Gets the data source description.
      Specified by:
      [`getDescription`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      data source description.

    <!-- -->

    - #### setNetworkProtocol

          public void setNetworkProtocol(String networkProtocol)
                                  throws SQLException

      Sets the datasource networkProtocol.
      Specified by:
      [`setNetworkProtocol`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `networkProtocol` - datasource networkProtocol to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNetworkProtocol

          public String getNetworkProtocol()

      Gets the datasource networkProtocol.
      Specified by:
      [`getNetworkProtocol`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      datasource networkProtocol.

    <!-- -->

    - #### setRoleName

          public void setRoleName(String roleName)
                           throws SQLException

      Sets the datasource role name.
      Specified by:
      [`setRoleName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `roleName` - datasource role name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRoleName

          public String getRoleName()

      Gets the datasource role name.
      Specified by:
      [`getRoleName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      datasource role name.

    <!-- -->

    - #### registerConnectionInitializationCallback

          public void registerConnectionInitializationCallback(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)
                                                        throws SQLException

      Registers a ConnectionInitializationCallback with the data source.
      Parameters:
      `cbk` - The ConnectionInitializationCallback to be registered.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If the argument is null or callback registration fails.

    <!-- -->

    - #### unregisterConnectionInitializationCallback

          public void unregisterConnectionInitializationCallback(oracle.jdbc.replay.internal.ConnectionInitializationCallback cbk)
                                                          throws SQLException

      Removes the ConnectionInitializationCallback registered with the data source, if any.
      Parameters:
      `cbk` - The `ConnectionInitializationCallback` object to be unregistered.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If callback removal fails.

    <!-- -->

    - #### getConnectionInitializationCallback

          public oracle.jdbc.replay.internal.ConnectionInitializationCallback getConnectionInitializationCallback()

      Description copied from interface: [`OracleDataSource`](OracleDataSource.md)
      Obtains the registered connection initialization callback, if any.
      Returns:
      The registered `ConnectionInitializationCallback`, or null if there is no callback registered.

    <!-- -->

    - #### getConnectionProperties

          public Properties getConnectionProperties()

      Gets the connection properties that are set on this data source.
      Specified by:
      [`getConnectionProperties`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      Connection properties.

    <!-- -->

    - #### getConnectionProperty

          public String getConnectionProperty(String propertyName)

      Gets the specified connection property that are set on this data source.
      Parameters:
      `propertyName` - The name of the specified property.

      Returns:
      The value of the inquired connection property. Null if the property is not set.

    <!-- -->

    - #### setConnectionProperty

          public void setConnectionProperty(String name,
                                            String value)
                                     throws SQLException

      Sets a connection property on the data source.
      Parameters:
      `name` - The name of the connection property to be set.

      `value` - The value of the connection property to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If any exception occurred while setting the connection property.

      See Also:
      `setConnectionProperties`

    <!-- -->

    - #### setConnectionProperties

          public void setConnectionProperties(Properties connProperties)
                                       throws SQLException

      Sets the connection properties on the data source. The setting is not cumulative, so caller must provide all the properties to be set at once.
      Specified by:
      [`setConnectionProperties`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `connectionProperties` - Connection properties to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If any exception occurred while setting the connection properties.

      See Also:
      [`OracleConnection`](../OracleConnection.md)

    <!-- -->

    - #### setMaxStatements

          public void setMaxStatements(int max)
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

          public int getMaxStatements()
                               throws SQLException

      Returns the current value of the **maxStatements** property.
      Specified by:
      [`getMaxStatements`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          public void setImplicitCachingEnabled(boolean cache)
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

          public boolean getImplicitCachingEnabled()
                                            throws SQLException

      getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.
      Specified by:
      [`getImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          public void setExplicitCachingEnabled(boolean cache)
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

          public boolean getExplicitCachingEnabled()
                                            throws SQLException

      Returns the current value of the **explicitCachingEnabled** property.
      Specified by:
      [`getExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getReplayStatistics

          public ReplayStatistics getReplayStatistics()

      Description copied from interface: [`OracleDataSource`](OracleDataSource.md)
      Obtains replay statistics accumulated so far. These reflect replay actions across all the connections created by this data source. It is recommended that this call be made when the connections are quiescent and there are few new connections being opened.
      Returns:
      A replay statistics object containing all the metrics.

    <!-- -->

    - #### clearDoneDumpOnMemoryPressure

          public void clearDoneDumpOnMemoryPressure()

    <!-- -->

    - #### getReplayStatisticsString

          public String getReplayStatisticsString()

    <!-- -->

    - #### clearReplayStatistics

          public void clearReplayStatistics()

      Description copied from interface: [`OracleDataSource`](OracleDataSource.md)
      Clears replay statistics accumulated so far on all connection created by this data source. It is recommended that this call be made when the connections are quiescent and there are few new connections being opened.

    <!-- -->

    - #### getReference

          public Reference getReference()
                                 throws NamingException

      Specified by:
      [`getReference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true#getReference__) in interface [`Referenceable`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true)

      Throws:
      [`NamingException`](http://download.oracle.com/javase/8/docs/api/javax/naming/NamingException.html?is-external=true)

    <!-- -->

    - #### getObjectInstance

          public Object getObjectInstance(Object refObj,
                                          Name name,
                                          Context nameCtx,
                                          Hashtable<?,?> env)
                                   throws Exception

      Specified by:
      [`getObjectInstance`](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true#getObjectInstance_java_lang_Object_javax_naming_Name_javax_naming_Context_java_util_Hashtable_) in interface [`ObjectFactory`](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true)

      Throws:
      [`Exception`](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)

    <!-- -->

    - #### isWrapperFor

          public boolean isWrapperFor(Class<?> iface)
                               throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - Requested interface.

      Returns:
      true If this implements the requested interface.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If the argument is not an interface.

      Since:
      JDBC 4.0

    <!-- -->

    - #### unwrap

          public <T> T unwrap(Class<T> iface)
                       throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      [`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - Requested interface.

      Returns:
      this If this implements the requested interface.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If this does not implement the arg or the arg is not an interface.

      Since:
      JDBC 4.0

    <!-- -->

    - #### getParentLogger

          public Logger getParentLogger()
                                 throws SQLFeatureNotSupportedException

      Specified by:
      [`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Throws:
      [`SQLFeatureNotSupportedException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLFeatureNotSupportedException.html?is-external=true)

    <!-- -->

    - #### updateReplayStatistics

          public void updateReplayStatistics(oracle.jdbc.replay.internal.ReplayStatistics newStats)

    <!-- -->

    - #### getRequestSizeLimit

          public int getRequestSizeLimit()
                                  throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getProxyFactory

          public oracle.jdbc.proxy.ProxyFactory getProxyFactory()
                                                         throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createConnectionBuilder

          public OracleConnectionBuilderImpl createConnectionBuilder()

      Creates a new OracleConnectionBuilder instance
      Specified by:
      [`createConnectionBuilder`](../datasource/OracleDataSource.md) in interface [`OracleDataSource`](../datasource/OracleDataSource.md)

      Returns:
      The OracleConnectionBuilder instance that was created

    <!-- -->

    - #### setSSLContext

          public final void setSSLContext(SSLContext sslContext)

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.
      The SSLContext must be [initialized](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true#init_javax_net_ssl_KeyManager_A_javax_net_ssl_TrustManager_A_java_security_SecureRandom_) before establishing a connection to the data source. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Specifying a null value will clear any non-null value that may have been set previously, causing this data source to behave as if this method had never been called at all.

      Specified by:
      [`setSSLContext`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `sslContext` - An SSLContext to use as an SSLEngine factory.

    <!-- -->

    - #### setTokenSupplier

          public final void setTokenSupplier(java.util.function.Supplier<? extends AccessToken> tokenSupplier)

      Description copied from interface: [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)
      Sets a supplier function that generates an access token when creating a connection with this `DataSource`. The supplier function is invoked each time this `DataSource` creates a connection. Instances of [`AccessToken`](../AccessToken.md) that are output by the supplier must represent a token type that is supported by Oracle Database for client authentication. The supplier must be thread safe.

      It is invalid to configure this `DataSource` with both a token supplier and with a user name or password. If invocations of [`OracleCommonDataSource.setUser(String)`](../datasource/OracleCommonDataSource.md), [`OracleCommonDataSource.setPassword(String)`](../datasource/OracleCommonDataSource.md), [`OracleCommonDataSource.setConnectionProperties(java.util.Properties)`](../datasource/OracleCommonDataSource.md), or `#setConnectionProperty(String, String)` have configured this `DataSource` with a user name or password, and an invocation of this method has also configured a token supplier, then a [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) indicating an invalid configuration is thrown when creating a connection with this datasource.

      Note that [`AccessToken.createJsonWebTokenCache(Supplier)`](../AccessToken.md) can be called to create a thread safe `Supplier` that caches tokens from a user defined `Supplier`.

      Specified by:
      [`setTokenSupplier`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `tokenSupplier` - Token supplying function. Not `null`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSourceFactory.md)
- [Next Class](OracleXADataSource.md)

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
