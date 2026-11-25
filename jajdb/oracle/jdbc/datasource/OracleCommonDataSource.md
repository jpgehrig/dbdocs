Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleCommonDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
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

oracle.jdbc.datasource

## Interface OracleCommonDataSource

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md), [OracleConnectionPoolDataSource](../replay/OracleConnectionPoolDataSource.md), [OracleDataSource](OracleDataSource.md), [OracleDataSource](../replay/OracleDataSource.md), [OracleXADataSource](OracleXADataSource.md), [OracleXADataSource](../replay/OracleXADataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [OracleConnectionPoolDataSource](../pool/OracleConnectionPoolDataSource.md), [OracleConnectionPoolDataSourceImpl](../replay/OracleConnectionPoolDataSourceImpl.md), [OracleDataSource](../pool/OracleDataSource.md), [OracleDataSourceImpl](../replay/OracleDataSourceImpl.md), [OracleOCIConnectionPool](../pool/OracleOCIConnectionPool.md), [OracleXADataSource](../xa/OracleXADataSource.md), [OracleXADataSource](../xa/client/OracleXADataSource.md), [OracleXADataSourceImpl](../replay/OracleXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface OracleCommonDataSource
      extends CommonDataSource

  Interface that defines the methods which are common between `OracleDataSource`, `OracleXADataSource` and `OracleConnectionPoolDataSource` and defines the Oracle extensions to the standard JDBC interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true).
  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Default Methods](javascript:show(16);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
    |---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `default `[`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md)                                  | `createShardingKeyBuilder``()`<br>Creates a new `OracleShardingKeyBuilder` instance.                                                                                                                                                                                                                                                                                                                                                            |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true) | `getConnectionProperties``()`<br>Gets the Connection Properties that are set in the datasource Returns the current Properties set in the datasource.                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDatabaseName``()`<br>Gets the name of the database set on this DataSource instance.                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDataSourceName``()`<br>Gets the datasource name for this instance if set.                                                                                                                                                                                                                                                                                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDescription``()`<br>Get the Desciption of this data source.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                               | `getExplicitCachingEnabled``()`<br>Returns the current value of the **explicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                               | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                   | `getMaxStatements``()`<br>Returns the current value of the **maxStatements** property.                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getNetworkProtocol``()`<br>Gets the network protocol set on the datasource.                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                   | `getPortNumber``()`<br>Gets the port number on which server is listening for requests.                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getRoleName``()`<br>Gets the data source role name.                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getServerName``()`<br>Gets the name of the server on which database is running.                                                                                                                                                                                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getURL``()`<br>Gets the URL for this datasource.                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getUser``()`<br>Gets the user name for this datasource.                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                  | `setConnectionProperties``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` value)`<br>Sets the Connection Properties for the datasource                                                                                                                                                                                                                                               |
    | `void`                                                                                                  | `setDatabaseName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dbname)`<br>Sets the name of a particular database on a server.                                                                                                                                                                                                                                                            |
    | `void`                                                                                                  | `setDataSourceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dsname)`<br>Sets the datasource name.                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                  | `setDescription``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` des)`<br>Sets the Description for this data source instance.                                                                                                                                                                                                                                                                |
    | `void`                                                                                                  | `setExplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache.                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                  | `setImplicitCachingEnabled``(boolean cache)`<br>Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit statement cache.                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setMaxStatements``(int max)`<br>Specifies the value of the **maxStatements** property.                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                  | `setNetworkProtocol``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` np)`<br>Sets the network protocol for the connections.                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setPassword``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pd)`<br>Sets the password with which connections have to be obtained.                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setPortNumber``(int pn)`<br>Sets the port number where a server is listening for requests.                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                  | `setRoleName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` roleName)`<br>Sets the data source role name.                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setServerName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sn)`<br>Sets the name of the Server on which database is running.                                                                                                                                                                                                                                                            |
    | `void`                                                                                                  | `setSSLContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | `void`                                                                                                  | `setTokenSupplier``(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`.                                                                                                             |
    | `void`                                                                                                  | `setURL``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` url)`<br>Sets the URL from which connections have to be obtained.                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                  | `setUser``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` userName)`<br>Set the user name with which connections have to be obtained.                                                                                                                                                                                                                                                        |

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

<!-- -->

- - ### Method Detail

    - #### createShardingKeyBuilder

          default OracleShardingKeyBuilder createShardingKeyBuilder()
                                                             throws SQLException

      Creates a new `OracleShardingKeyBuilder` instance.
      Returns:
      The ShardingKeyBuilder instance that was created

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs creating the builder

      See Also:
      [`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md)

    <!-- -->

    - #### setDataSourceName

          void setDataSourceName(String dsname)
                          throws SQLException

      Sets the datasource name.
      Parameters:
      `dsname` - DataSource Name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDataSourceName

          String getDataSourceName()

      Gets the datasource name for this instance if set. Returns null if not set.
      Returns:
      DaraSource name

    <!-- -->

    - #### getDatabaseName

          String getDatabaseName()

      Gets the name of the database set on this DataSource instance.
      Returns:
      database name set on this instance or null if not set.

    <!-- -->

    - #### setDatabaseName

          void setDatabaseName(String dbname)
                        throws SQLException

      Sets the name of a particular database on a server. In Oracle's jargon this is called SID (System Identifier).
      If URL is set, this property will be ignored.

      Parameters:
      `dsname` - database name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setServerName

          void setServerName(String sn)
                      throws SQLException

      Sets the name of the Server on which database is running. If URL is set, this property will be ignored.
      Parameters:
      `sn` - server/host name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getServerName

          String getServerName()

      Gets the name of the server on which database is running.
      Returns:
      server name set on this instance or null if not set.

    <!-- -->

    - #### setURL

          void setURL(String url)
               throws SQLException

      Sets the URL from which connections have to be obtained. If URL is set all other properties like databasename, servername, portNumber, network protocol, tnsentry, and driver Type will be ignored.
      Parameters:
      `url` - URL to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getURL

          String getURL()
                 throws SQLException

      Gets the URL for this datasource. Will return the default value "jdbc:oracle:oci8:@" if not set before.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setUser

          void setUser(String userName)
                throws SQLException

      Set the user name with which connections have to be obtained.
      Parameters:
      `user` - Username to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getUser

          String getUser()

      Gets the user name for this datasource. Will return the default value ("scott") if not set before.

    <!-- -->

    - #### setPassword

          void setPassword(String pd)
                    throws SQLException

      Sets the password with which connections have to be obtained. The default value is "tiger".
      Parameters:
      `pd` - Passowrd to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDescription

          String getDescription()

      Get the Desciption of this data source.
      Returns:
      Description that was set or will return null if not set.

    <!-- -->

    - #### setDescription

          void setDescription(String des)
                       throws SQLException

      Sets the Description for this data source instance.
      Parameters:
      `des` - Desciption to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNetworkProtocol

          String getNetworkProtocol()

      Gets the network protocol set on the datasource.
      Returns:
      network protocol that was set or null if not.

    <!-- -->

    - #### setNetworkProtocol

          void setNetworkProtocol(String np)
                           throws SQLException

      Sets the network protocol for the connections. Default is "tcp". Can be set to all possible protocols Net8 supports. Only needed for JDBC OCI driver.
      Parameters:
      `np` - set the network protocol to be used.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPortNumber

          void setPortNumber(int pn)
                      throws SQLException

      Sets the port number where a server is listening for requests. Not required when URL is set.
      Parameters:
      `pn` - port number on which server is listening

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPortNumber

          int getPortNumber()

      Gets the port number on which server is listening for requests.
      Returns:
      port number if set or null if not set.

    <!-- -->

    - #### setConnectionProperties

          void setConnectionProperties(Properties value)
                                throws SQLException

      Sets the Connection Properties for the datasource
      The argument to this method is a Properties object. This properties object is used to create the connections returned by the receiver. The keys and values are Strings. The keys, values, and their meanings are defined in oracle.jdbc.OracleConnection.

      Parameters:
      `value` - a Properties object with the desired connection property names and values.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`OracleConnection`](../OracleConnection.md)

    <!-- -->

    - #### getConnectionProperties

          Properties getConnectionProperties()
                                      throws SQLException

      Gets the Connection Properties that are set in the datasource Returns the current Properties set in the datasource.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setMaxStatements

          void setMaxStatements(int max)
                         throws SQLException

      Specifies the value of the **maxStatements** property. This is the size of the statement cache used by both implicit and explicit caching. This value does not apply to the statement cache size of connections created by ImplicitStatementCache for which the cache size is set through a java.util.Properties object.
      Parameters:
      `max` - Requested size of the cache. If the existing cache size is less than max, statements will be purged to reduce the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if max \< 0

    <!-- -->

    - #### getMaxStatements

          int getMaxStatements()
                        throws SQLException

      Returns the current value of the **maxStatements** property.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          void setImplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Sets the value of the **implicitCachingEnabled** property, which enables or disables the implicit statement cache. Note that this is independent of the cache size that is set with setMaxStatements().
      Parameters:
      `cache` - If true, then implicit caching is enabled. If false, then any existing statement is purged and the implicit caching is disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getImplicitCachingEnabled

          boolean getImplicitCachingEnabled()
                                     throws SQLException

      getImplicitCachingEnabled Returns the current value of the **implicitCachingEnabled** property.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          void setExplicitCachingEnabled(boolean cache)
                                  throws SQLException

      Sets the value of the **explicitCachingEnabled** property, which enables or disables the explicit cache. Note that this is independent of the cache size, which is set with setMaxStatements().
      Parameters:
      `cache` - If true, then explicit caching is enabled. If false, then any existing statement is purged and the explicit caching is disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          boolean getExplicitCachingEnabled()
                                     throws SQLException

      Returns the current value of the **explicitCachingEnabled** property.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setRoleName

          void setRoleName(String roleName)
                    throws SQLException

      Sets the data source role name.
      Parameters:
      `roleName` - data source role name to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRoleName

          String getRoleName()

      Gets the data source role name.
      Returns:
      data source role name.

    <!-- -->

    - #### setSSLContext

          void setSSLContext(SSLContext sslContext)
                      throws SQLException

      Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.
      The SSLContext must be [initialized](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true#init_javax_net_ssl_KeyManager_A_javax_net_ssl_TrustManager_A_java_security_SecureRandom_) before establishing a connection to the data source. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Specifying a null value will clear any non-null value that may have been set previously, causing this data source to behave as if this method had never been called at all.

      Parameters:
      `sslContext` - An SSLContext to use as an SSLEngine factory.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if this data source is incompatible with the specified SSLContext.

      Since:
      20

    <!-- -->

    - #### setTokenSupplier

          void setTokenSupplier(java.util.function.Supplier<? extends AccessToken> tokenSupplier)

      Sets a supplier function that generates an access token when creating a connection with this `DataSource`. The supplier function is invoked each time this `DataSource` creates a connection. Instances of [`AccessToken`](../AccessToken.md) that are output by the supplier must represent a token type that is supported by Oracle Database for client authentication. The supplier must be thread safe.

      It is invalid to configure this `DataSource` with both a token supplier and with a user name or password. If invocations of `setUser(String)`, `setPassword(String)`, `setConnectionProperties(java.util.Properties)`, or `#setConnectionProperty(String, String)` have configured this `DataSource` with a user name or password, and an invocation of this method has also configured a token supplier, then a [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) indicating an invalid configuration is thrown when creating a connection with this datasource.

      Note that [`AccessToken.createJsonWebTokenCache(Supplier)`](../AccessToken.md) can be called to create a thread safe `Supplier` that caches tokens from a user defined `Supplier`.

      Parameters:
      `tokenSupplier` - Token supplying function. Not `null`.

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - If the `tokenSupplier` is null.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleCommonDataSource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
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
