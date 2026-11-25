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

oracle.jdbc.pool

## Class OracleDataSource

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OracleDataSource

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md)

  <!-- -->

  Direct Known Subclasses:
  [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md), [OracleOCIConnectionPool](OracleOCIConnectionPool.md)

  ------------------------------------------------------------------------



      public class OracleDataSource
      extends Object
      implements OracleDataSource, Serializable, Referenceable

  A DataSource object is a factory for Connection objects. An object that implements the DataSource interface will typically be registered with a JNDI service provider. A JDBC driver that is accessed via the DataSource API does not automatically register itself with the DriverManager.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                   | Field and Description         |
    |---------------------------------------------------------------------------------------------------------------------|-------------------------------|
    | `protected `[`OracleConnectionCacheManager`](OracleConnectionCacheManager.md)                                       | `cacheManager`                |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `connCacheName`               |
    | `protected `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true) | `connCacheProperties`         |
    | `protected boolean`                                                                                                 | `connCachingEnabled`          |
    | `protected `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true) | `connectionProperties`        |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `databaseName`                |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `dataSourceName`              |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `DEFAULT_SERVICE_NAME`        |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `description`                 |
    | `protected oracle.jdbc.driver.OracleDriver`                                                                         | `driver`                      |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `driverType`                  |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `ENABLE_AC_SUPPORT_PROPERTY`  |
    | `protected boolean`                                                                                                 | `explicitCachingEnabled`      |
    | `protected boolean`                                                                                                 | `explicitCachingEnabledSet`   |
    | `protected boolean`                                                                                                 | `fastConnFailover`            |
    | `protected boolean`                                                                                                 | `implicitCachingEnabled`      |
    | `protected boolean`                                                                                                 | `implicitCachingEnabledSet`   |
    | `boolean`                                                                                                           | `isOracleDataSource`          |
    | `protected int`                                                                                                     | `loginTimeout`                |
    | `protected `[`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true) | `logWriter`                   |
    | `protected int`                                                                                                     | `maxStatements`               |
    | `protected boolean`                                                                                                 | `maxStatementsSet`            |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `networkProtocol`             |
    | `protected oracle.jdbc.pool.OracleImplicitConnectionCache`                                                          | `odsCache`                    |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `onsConfigStr`                |
    | `protected oracle.jdbc.internal.OpaqueString`                                                                       | `password`                    |
    | `protected int`                                                                                                     | `portNumber`                  |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `serverName`                  |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `serviceName`                 |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `tnsEntry`                    |
    | `static boolean`                                                                                                    | `TRACE`                       |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `url`                         |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `user`                        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OracleDataSource``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                                                                                   | `addRefProperties``(`[`Reference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Reference.html?is-external=true)` ref)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                             | `close``()`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Close DataSource API. This removes the associated Connection Cache and frees resources. This must be the last method to invoke, after the user is finished using a cache enabled DataSource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `protected void`                                                                                                   | `copy``(OracleDataSource ds)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`OracleConnectionBuilderImpl`](OracleConnectionBuilderImpl.md)                                                    | `createConnectionBuilder``()`<br>Creates a new instance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `protected void`                                                                                                   | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``()`<br>Attempt to establish a database connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`OracleConnectionBuilderImpl`](OracleConnectionBuilderImpl.md)` builder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cachedConnectionAttributes)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Attempt to obtain a database connection from the Implicit Connection Cache using Connection Attributes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Attempt to establish a database connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cachedConnectionAttributes)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Attempt to obtain a database connection from the Implicit Connection Cache using user, passwd and Connection Attributes                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getConnectionCacheName``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)            | `getConnectionCacheProperties``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                          | `getConnectionCachingEnabled``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected oracle.jdbc.internal.OracleConnection`                                                                  | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)            | `getConnectionProperties``()`<br>getConnectionProperties Returns the current Properties set in the datasource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` propertyName)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDatabaseName``()`<br>Get the name of the database set on this DataSource instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDataSourceName``()`<br>Get the datasource name for this instance if set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDescription``()`<br>Get the Desciption of this data source.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getDriverType``()`<br>Get the Oracle JDBC driver type set for this datasource instance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                          | `getExplicitCachingEnabled``()`<br>getExplicitCachingEnabled Returns the current value of the **explicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                          | `getFastConnectionFailoverEnabled``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                          | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                              | `getLoginTimeout``()`<br>Gets the maximum time in seconds that this data source can wait while attempting to connect to a database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true)            | `getLogWriter``()`<br>Get the log writer for this data source.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                              | `getMaxStatements``()`<br>getMaxStatements Returns the current value of the **maxStatements** property.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getNetworkProtocol``()`<br>Get the network protocol set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getONSConfiguration``()`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Return the ONS configuration string that is used for remote ONS subscription, in the form specified in setONSConfiguration(String). This is used by Fast Connection Failover and Runtime Load Balancing.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)            | `getParentLogger``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getPassword``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getPhysicalConnection``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop, `[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` gssCredential, `[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext, `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`                                                                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                                                                                              | `getPortNumber``()`<br>Get the port number on which server is listening for requests.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`Reference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Reference.html?is-external=true)           | `getReference``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getRoleName``()`<br>Gets the datasource role name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getServerName``()`<br>Get the name of the server on which database is running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getServiceName``()`<br>Get the service_name To distinguish services from instances, a new URL using service_name is added, existing url with SID will be supported, but deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getTNSEntryName``()`<br>Get the TNS entry name for this instance if set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getURL``()`<br>Get the URL for this datasource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                    | `getUser``()`<br>Get the user name for this datasource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                          | `isWrapperFor``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<?> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                             | `setConnectionCacheName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                             | `setConnectionCacheProperties``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cp)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Setter method to set one or more Implicit Connection Cache properties. If a null value is set, default values will take effect. Below are the list of properties supported. These are the keys (case sensitive) to be used when setting their appropriate values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                             | `setConnectionCachingEnabled``(boolean flag)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Setter method to enable Implicit Connection Caching                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                             | `setConnectionProperties``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` value)`<br>Sets the Connection Properties for the datasource                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected void`                                                                                                   | `setConnectionProperty``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                             | `setDatabaseName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dbname)`<br>Set the name of a particular database on a server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                             | `setDataSourceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dsname)`<br>Set the DataSourceName.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                             | `setDescription``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` des)`<br>Set the Desciption for this data source instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                             | `setDriverType``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dt)`<br>Set the JDBC driver type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                             | `setExplicitCachingEnabled``(boolean cache)`<br>setExplicitCachingEnabled Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                             | `setFastConnectionFailoverEnabled``(boolean flag)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                             | `setImplicitCachingEnabled``(boolean cache)`<br>setImplicitCachingEnabled Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit cache.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                             | `setLoginTimeout``(int timeout)`<br>Sets the maximum time in seconds that this data source will wait while attempting to connect to a database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                             | `setLogWriter``(`[`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true)` pw)`<br>Set the log writer for this data source.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                             | `setMaxStatements``(int max)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                             | `setNetworkProtocol``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` np)`<br>Set the network protocol for the connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                             | `setONSConfiguration``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` onsConfigStr)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.<br>Set the configuration string used for remote ONS subscription. The parameter string closely resembles the content of the ONS configuration file "ons.config", and contains a list of "\<name\>=\<value\>" pairs separated by newline character '\n', where \<name\> can be one of "nodes", "walletfile", or "walletpassword". The parameter string should at least specify the ONS configuration attribute "nodes", as a list of host:port pairs separated by comma ','. SSL would be used when the "walletfile" attribute is specified as an Oracle wallet file.<br>An example ONS configuration string:<br>`      "nodes=host1:4200,host2:4200\nwalletfile=wfile\nwalletpassword=wpwd"`<br>`    `<br>This is used primarily by Fast Connection Failover and Runtime Load Balancing. |
    | `void`                                                                                                             | `setPassword``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pd)`<br>Set the password with which connections have to be obtained.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                             | `setPortNumber``(int pn)`<br>Set the port number where a server is listening for requests.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                             | `setRoleName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` roleName)`<br>Sets the datasource role name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                             | `setServerName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sn)`<br>Set the name of the Server on which database is running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                             | `setServiceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` svcname)`<br>Set the service_name of a database on a server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                             | `setSSLContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                             | `setTNSEntryName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dbname)`<br>Set the TNS entry name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                             | `setTokenSupplier``(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                             | `setURL``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url)`<br>Set the URL from which connections have to be obtained.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                             | `setUser``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` userName)`<br>Set the user name with which connections have to be obtained.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `protected void`                                                                                                   | `trace``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `<T> T`                                                                                                            | `unwrap``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<T> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)

      [`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)

<!-- -->

- - ### Field Detail

    - #### DEFAULT_SERVICE_NAME

          protected static final String DEFAULT_SERVICE_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### logWriter

          protected PrintWriter logWriter

    <!-- -->

    - #### loginTimeout

          protected int loginTimeout

    <!-- -->

    - #### databaseName

          protected String databaseName

    <!-- -->

    - #### serviceName

          protected String serviceName

    <!-- -->

    - #### dataSourceName

          protected String dataSourceName

    <!-- -->

    - #### description

          protected String description

    <!-- -->

    - #### networkProtocol

          protected String networkProtocol

    <!-- -->

    - #### portNumber

          protected int portNumber

    <!-- -->

    - #### user

          protected String user

    <!-- -->

    - #### password

          protected oracle.jdbc.internal.OpaqueString password

    <!-- -->

    - #### serverName

          protected String serverName

    <!-- -->

    - #### url

          protected String url

    <!-- -->

    - #### driverType

          protected String driverType

    <!-- -->

    - #### tnsEntry

          protected String tnsEntry

    <!-- -->

    - #### maxStatements

          protected int maxStatements

    <!-- -->

    - #### implicitCachingEnabled

          protected boolean implicitCachingEnabled

    <!-- -->

    - #### explicitCachingEnabled

          protected boolean explicitCachingEnabled

    <!-- -->

    - #### maxStatementsSet

          protected boolean maxStatementsSet

    <!-- -->

    - #### implicitCachingEnabledSet

          protected boolean implicitCachingEnabledSet

    <!-- -->

    - #### explicitCachingEnabledSet

          protected boolean explicitCachingEnabledSet

    <!-- -->

    - #### odsCache

          protected transient oracle.jdbc.pool.OracleImplicitConnectionCache odsCache

    <!-- -->

    - #### cacheManager

          protected transient OracleConnectionCacheManager cacheManager

    <!-- -->

    - #### connCacheName

          protected String connCacheName

    <!-- -->

    - #### connCacheProperties

          protected Properties connCacheProperties

    <!-- -->

    - #### connectionProperties

          protected Properties connectionProperties

    <!-- -->

    - #### connCachingEnabled

          protected boolean connCachingEnabled

    <!-- -->

    - #### fastConnFailover

          protected boolean fastConnFailover

    <!-- -->

    - #### onsConfigStr

          protected String onsConfigStr

    <!-- -->

    - #### isOracleDataSource

          public boolean isOracleDataSource

    <!-- -->

    - #### driver

          protected transient oracle.jdbc.driver.OracleDriver driver

    <!-- -->

    - #### ENABLE_AC_SUPPORT_PROPERTY

          protected static final String ENABLE_AC_SUPPORT_PROPERTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TRACE

          public static final boolean TRACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleDataSource

          public OracleDataSource()
                           throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Attempt to establish a database connection.

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection(String _user,
                                          String _passwd)
                                   throws SQLException

      Attempt to establish a database connection.

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Parameters:
      `user` - the database user on whose behalf the Connection is being made

      `password` - the user's password

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection(OracleConnectionBuilderImpl builder)
                                   throws SQLException

      Parameters:
      `builder` - , builder which has the required properties set for building the connection

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection(Properties prop,
                                                     GSSCredential gssCredential,
                                                     SSLContext sslContext,
                                                     java.util.function.Supplier<? extends AccessToken> tokenSupplier)
                                              throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnection

          public Connection getConnection(Properties cachedConnectionAttributes)
                                   throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Attempt to obtain a database connection from the Implicit Connection Cache using Connection Attributes

      Returns:
      logical Connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection(String _user,
                                          String _passwd,
                                          Properties cachedConnectionAttributes)
                                   throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Attempt to obtain a database connection from the Implicit Connection Cache using user, passwd and Connection Attributes

      Returns:
      logical Connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Close DataSource API. This removes the associated Connection Cache and frees resources. This must be the last method to invoke, after the user is finished using a cache enabled DataSource.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setConnectionCachingEnabled

          public void setConnectionCachingEnabled(boolean flag)
                                           throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Setter method to enable Implicit Connection Caching

      Parameters:
      `flag` - boolean value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionCachingEnabled

          public boolean getConnectionCachingEnabled()
                                              throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setConnectionCacheName

          public void setConnectionCacheName(String cacheName)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionCacheName

          public String getConnectionCacheName()
                                        throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setConnectionCacheProperties

          public void setConnectionCacheProperties(Properties cp)
                                            throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Setter method to set one or more Implicit Connection Cache properties. If a null value is set, default values will take effect. Below are the list of properties supported. These are the keys (case sensitive) to be used when setting their appropriate values.

      Parameters:
      `cp` - key/value pairs. Description of the supported keys follow.

      - MinLimit

        Sets limit on Minimum number of connections. Defaults to 0.

      - MaxLimit

        Sets limit on Maximum number of connections. No default.

      - InitialLimit

        Sets limit on the number of initial connections populated, when the cache is first created. Defaults to 0.

      - MaxStatementsLimit

        Sets the Maximum number of statements that each connection keeps open, for statement caching. Defaults to 0.

      - InactivityTimeout

        Sets the Maximum time, in seconds, a connection in the cache can remain idle (that is not checked out of the cache). Defaults to 0.

      - TimeToLiveTimeout

        Sets that maximum time, in seconds, a checked out connection can remain idle. Defaults to 0.

      - AbandonedConnectionTimeout

        Sets the maximum time a checked out connection can remain unused (no SQL activity) before the connection is closed and returned to the cache. Defaults to 0.

      - ConnectionWaitTimeout

        Specifies the time limit to wait, when a new connection request arrives, and there are no connections to check out. Defaults to 0.

      - PropertyCheckInterval

        Sets the time interval for the cache daemon thread to enforce the time out limits. Defaults to 900 seconds (15 minutes).

      - ValidateConnection

        Verifies each connection for validity, before a checked out connection is returned to the caller. Defaults to false.

      - ClosestConnectionMatch

        Causes the connection cache to retrieve the connection with the closest approximation to the specified connection attributes. Defaults to false.

      - AttributeWeights

        Sets the weight (integer) for each connection attribute. This is used when ClosestConnectionMatch is set to true, and enables retrieval of a connection with the highest combined weight of all its connection attributes. Defaults to a weight of 1.

      - LowerThresholdLimit

        Sets the lower threshold limit on the cache. This is used for the releaseConnection() cache callback method is registered. Defaults to 20%.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionCacheProperties

          public Properties getConnectionCacheProperties()
                                                  throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setFastConnectionFailoverEnabled

          public void setFastConnectionFailoverEnabled(boolean flag)
                                                throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFastConnectionFailoverEnabled

          public boolean getFastConnectionFailoverEnabled()
                                                   throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getONSConfiguration

          public String getONSConfiguration()
                                     throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Return the ONS configuration string that is used for remote ONS subscription, in the form specified in setONSConfiguration(String). This is used by Fast Connection Failover and Runtime Load Balancing.

      Returns:
      The ONS configuration string used for remote ONS subscription.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setONSConfiguration

          public void setONSConfiguration(String onsConfigStr)
                                   throws SQLException

      Deprecated. Use Oracle Universal Connection Pool instead.
      Set the configuration string used for remote ONS subscription. The parameter string closely resembles the content of the ONS configuration file "ons.config", and contains a list of "\<name\>=\<value\>" pairs separated by newline character '\n', where \<name\> can be one of "nodes", "walletfile", or "walletpassword". The parameter string should at least specify the ONS configuration attribute "nodes", as a list of host:port pairs separated by comma ','. SSL would be used when the "walletfile" attribute is specified as an Oracle wallet file.

      An example ONS configuration string:

                "nodes=host1:4200,host2:4200\nwalletfile=wfile\nwalletpassword=wpwd"


      This is used primarily by Fast Connection Failover and Runtime Load Balancing.

      Parameters:
      `onsConfigStr` - The configuration string for remote ONS subscription

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLoginTimeout

          public int getLoginTimeout()

      Gets the maximum time in seconds that this data source can wait while attempting to connect to a database. A value of zero means that the timeout is the default system timeout if there is one; otherwise it means that there is no timeout. When a DataSource object is created the login timeout is initially zero.
      Specified by:
      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Returns:
      the data source login time limit

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs.

    <!-- -->

    - #### setLoginTimeout

          public void setLoginTimeout(int timeout)

      Sets the maximum time in seconds that this data source will wait while attempting to connect to a database. A value of zero specifies that the timeout is the default system timeout if there is one; otherwise it specifies that there is no timeout. When a DataSource object is created the login timeout is initially zero.

      Specified by:
      [`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Parameters:
      `seconds` - the data source login time limit

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs.

    <!-- -->

    - #### setLogWriter

          public void setLogWriter(PrintWriter pw)

      Set the log writer for this data source.

      The log writer is a character output stream to which all logging and tracing messages for this data source object instance will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. Messages printed to a data source specific log writer are not printed to the log writer associated with the java.sql.Drivermanager class. When a DataSource object is created the log writer is initially null, in other words, logging is disabled.

      Specified by:
      [`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Parameters:
      `out` - the new log writer; to disable, set to null

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getLogWriter

          public PrintWriter getLogWriter()

      Get the log writer for this data source.

      The log writer is a character output stream to which all logging and tracing messages for this data source object instance will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. Messages printed to a data source specific log writer are not printed to the log writer associated with the java.sql.Drivermanager class. When a DataSource object is created the log writer is initially null, in other words, logging is disabled.

      Specified by:
      [`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__) in interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      Returns:
      the log writer for this data source, null if disabled

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### setTNSEntryName

          public void setTNSEntryName(String dbname)

      Set the TNS entry name. Works only for JDBC OCI driver. Assumed that client side Oracle in installed and TNS_ADMIN env variable is set. If URL is set, this property will be ignored.
      Parameters:
      `dbname` - tns entry name

    <!-- -->

    - #### getTNSEntryName

          public String getTNSEntryName()

      Get the TNS entry name for this instance if set. Returns null if not set.
      Returns:
      TNS entry name

    <!-- -->

    - #### setDataSourceName

          public void setDataSourceName(String dsname)

      Set the DataSourceName. Users need not set this as it will be set set automatically depending upon the instance created. Returns OracleDataSource for an OracleDataSource instance. Returns OracleXADataSource for an OracleXADataSource instance.
      Specified by:
      [`setDataSourceName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `dsname` - DataSource Name to be set.

    <!-- -->

    - #### getDataSourceName

          public String getDataSourceName()

      Get the datasource name for this instance if set. Returns null if not set.
      Specified by:
      [`getDataSourceName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      DaraSource name

    <!-- -->

    - #### getDatabaseName

          public String getDatabaseName()

      Get the name of the database set on this DataSource instance.
      Specified by:
      [`getDatabaseName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      database name set on this instance or null if not set.

    <!-- -->

    - #### setDatabaseName

          public void setDatabaseName(String dbname)

      Set the name of a particular database on a server. In Oracle's jargon this is called SID (System Identifier).
      If URL is set, this property will be ignored.

      Specified by:
      [`setDatabaseName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `dsname` - database name to be set.

    <!-- -->

    - #### setServiceName

          public void setServiceName(String svcname)

      Set the service_name of a database on a server. If URL is set, this property will be ignored. To distinguish services from instances, a new URL using service_name is added, existing url with SID will be supported, but deprecated.
      Parameters:
      `svcname` - service_name to be set.

    <!-- -->

    - #### getServiceName

          public String getServiceName()

      Get the service_name To distinguish services from instances, a new URL using service_name is added, existing url with SID will be supported, but deprecated.
      Returns:
      service_name assiciated with the instance or null if not set.

    <!-- -->

    - #### setServerName

          public void setServerName(String sn)

      Set the name of the Server on which database is running. If URL is set, this property will be ignored.
      Specified by:
      [`setServerName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `sn` - server/host name to be set.

    <!-- -->

    - #### getServerName

          public String getServerName()

      Get the name of the server on which database is running.
      Specified by:
      [`getServerName`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      server name set on this instance or null if not set.

    <!-- -->

    - #### setURL

          public void setURL(String url)

      Set the URL from which connections have to be obtained. If URL is set all other properties like databasename, servername, portNumber, network protocol, tnsentry, and driver Type will be ignored.
      Specified by:
      [`setURL`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `url` - URL to be set.

    <!-- -->

    - #### getURL

          public String getURL()
                        throws SQLException

      Get the URL for this datasource. Will return the default value "jdbc:oracle:oci8:@" if not set before.
      Specified by:
      [`getURL`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setUser

          public void setUser(String userName)

      Set the user name with which connections have to be obtained.
      Specified by:
      [`setUser`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `user` - Username to be set.

    <!-- -->

    - #### getUser

          public String getUser()

      Get the user name for this datasource. Will return the default value ("scott") if not set before.
      Specified by:
      [`getUser`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

    <!-- -->

    - #### setPassword

          public void setPassword(String pd)

      Set the password with which connections have to be obtained. The default value is "tiger".
      Specified by:
      [`setPassword`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `pd` - Passowrd to be set.

    <!-- -->

    - #### getPassword

          protected String getPassword()

    <!-- -->

    - #### getDescription

          public String getDescription()

      Get the Desciption of this data source.
      Specified by:
      [`getDescription`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      Description that was set or will return null if not set.

    <!-- -->

    - #### setDescription

          public void setDescription(String des)

      Set the Desciption for this data source instance.
      Specified by:
      [`setDescription`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `des` - Desciption to be set.

    <!-- -->

    - #### getDriverType

          public String getDriverType()

      Get the Oracle JDBC driver type set for this datasource instance
      Returns:
      Driver Type that was set or null if not set.

    <!-- -->

    - #### setDriverType

          public void setDriverType(String dt)

      Set the JDBC driver type. Possible values are thin, oci8, and kprb. If URL is set, this property will be ignored.
      If set to kprb, nothing else is needed to open a connection. This is meant for Server side JDBC driver when running inside server.

      If set to thin, serverName, portNumber and databaseName are need to open a connection.

      If set to oci, and network protocol is set to IPC or TNSEntryName is set then nothing else is needed. If not, serverName, portNumber and databaseName have to be provided.

      Parameters:
      `dt` - Driver Type tp be set.

    <!-- -->

    - #### getNetworkProtocol

          public String getNetworkProtocol()

      Get the network protocol set.
      Specified by:
      [`getNetworkProtocol`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      network protocol that was set or null if not.

    <!-- -->

    - #### setNetworkProtocol

          public void setNetworkProtocol(String np)
                                  throws SQLException

      Set the network protocol for the connections. Default is "tcp". Can be set to all possible protocols Net8 supports. Only needed for JDBC OCI driver.
      Specified by:
      [`setNetworkProtocol`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `np` - set the network protocol to be used.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPortNumber

          public void setPortNumber(int pn)

      Set the port number where a server is listening for requests. Not required when URL is set.
      Specified by:
      [`setPortNumber`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `pn` - port number on which server is listening

    <!-- -->

    - #### getPortNumber

          public int getPortNumber()

      Get the port number on which server is listening for requests.
      Specified by:
      [`getPortNumber`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Returns:
      port number if set or null if not set.

    <!-- -->

    - #### getReference

          public Reference getReference()
                                 throws NamingException

      Specified by:
      [`getReference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true#getReference__) in interface [`Referenceable`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true)

      Throws:
      [`NamingException`](http://download.oracle.com/javase/8/docs/api/javax/naming/NamingException.html?is-external=true)

    <!-- -->

    - #### addRefProperties

          protected void addRefProperties(Reference ref)

    <!-- -->

    - #### trace

          protected void trace(String s)

    <!-- -->

    - #### copy

          protected void copy(OracleDataSource ds)
                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setMaxStatements

          public void setMaxStatements(int max)
                                throws SQLException

      Deprecated. 
      setMaxStatements Specifies the value of the **maxStatements** property. This will be the size of the application cache (which will be used by both implicit and explicit caching). This value does not apply to the statement cache size of connections created by ImplicitStatementCache for which the cache size is set through java.util.Properties object.
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

      getMaxStatements Returns the current value of the **maxStatements** property.
      Specified by:
      [`getMaxStatements`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          public void setImplicitCachingEnabled(boolean cache)
                                         throws SQLException

      setImplicitCachingEnabled Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit cache. Note that this is independent of the cache size, set with setMaxStatements().
      Specified by:
      [`setImplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `cache` - If true, then implicit caching will be enabled. If false, then any existing statements will be purged and the implicit cache will be disabled.

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

      setExplicitCachingEnabled Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache. Note that this is independent of the cache size, set with setMaxStatements().
      Specified by:
      [`setExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `cache` - If true, then explicit caching will be enabled. If false, then any existing statements will be purged and the explicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          public boolean getExplicitCachingEnabled()
                                            throws SQLException

      getExplicitCachingEnabled Returns the current value of the **explicitCachingEnabled** property.
      Specified by:
      [`getExplicitCachingEnabled`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setConnectionProperties

          public void setConnectionProperties(Properties value)
                                       throws SQLException

      Sets the Connection Properties for the datasource
      The argument to this method is a Properties object. This properties object is used to create the connections returned by the receiver. The keys and values are Strings. The keys, values, and their meanings are defined in oracle.jdbc.OracleConnection.

      Specified by:
      [`setConnectionProperties`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Parameters:
      `value` - a Properties object with the desired connection property names and values.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`OracleConnection`](../OracleConnection.md)

    <!-- -->

    - #### getConnectionProperty

          protected String getConnectionProperty(String propertyName)
                                          throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setConnectionProperty

          protected void setConnectionProperty(String name,
                                               String value)
                                        throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

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

    - #### getConnectionProperties

          public Properties getConnectionProperties()
                                             throws SQLException

      getConnectionProperties Returns the current Properties set in the datasource.
      Specified by:
      [`getConnectionProperties`](../datasource/OracleCommonDataSource.md) in interface [`OracleCommonDataSource`](../datasource/OracleCommonDataSource.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isWrapperFor

          public boolean isWrapperFor(Class<?> iface)
                               throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - requested interface

      Returns:
      true iff this implements the requested interface

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the arg is not an interface

      Since:
      JDBC 4.0

    <!-- -->

    - #### unwrap

          public <T> T unwrap(Class<T> iface)
                       throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface. If it does return this.
      Specified by:
      [`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - requested interface

      Returns:
      this iff this implements the requested interface

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if this does not implement the arg or the arg is not an interface

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

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### createConnectionBuilder

          public OracleConnectionBuilderImpl createConnectionBuilder()

      Creates a new instance
      Specified by:
      [`createConnectionBuilder`](../datasource/OracleDataSource.md) in interface [`OracleDataSource`](../datasource/OracleDataSource.md)

      Returns:
      The OracleConnectionBuilder instance that was created

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

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
- [Use](class-use/OracleDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionPoolDataSource.md)
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
