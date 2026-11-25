Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.DRCPState.md)
- [Next Class](OracleConnectionWrapper.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.jdbc

## Interface OracleConnectionBuilder

- All Known Implementing Classes:
  [OracleConnectionBuilderImpl](pool/OracleConnectionBuilderImpl.md)

  ------------------------------------------------------------------------



      public interface OracleConnectionBuilder

  A builder created from a `OracleDataSource` object, used to establish a connection to the database that the `OracleDataSource` object represents. The connection properties that were specified for the `OracleDataSource` are used as the default values by the `OracleConnectionBuilder`.
  To use the builder, the corresponding builder method needs to be called for each parameter that needs to be part of the connection request followed by a build() method. The order in which the builder methods are called is not important. However if the same builder attribute is applied more than once, only the most recent value will be considered while building the connection. The builder object can be reused to build more than one connection and the builder attributes will be retained across multiple invocations of the build() method.

  The following example illustrates the use of `OracleConnectionBuilder` to create a [`OracleConnection`](OracleConnection.md):


          OracleDataSource ods = new oracle.jdbc.pool.OracleDataSource();
          OracleShardingKey superShardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("EASTERN_REGION", JDBCType.VARCHAR)
                 .build();
          OracleShardingKey shardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("PITTSBURGH_BRANCH", JDBCType.VARCHAR)
                 .build();
          OracleConnection connection = ods.createConnectionBuilder()
                                           .user("rafa")
                                           .password("tennis")
                                           .shardingKey(shardingKey)
                                           .superShardingKey(superShardingKey)
                                           .build();



  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleConnectionBuilder`                 | `accessToken``(`[`AccessToken`](AccessToken.md)` accessToken)`<br>Specifies the `accessToken` to be used when creating a connection.                                                                                                                                                                                                                                                                                                         |
    | [`OracleConnection`](OracleConnection.md) | `build``()`<br>Builds the connection object.                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `OracleConnectionBuilder`                 | `gssCredential``(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | `OracleConnectionBuilder`                 | `password``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | `OracleConnectionBuilder`                 | `shardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                   |
    | `OracleConnectionBuilder`                 | `sslContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | `OracleConnectionBuilder`                 | `superShardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                         |
    | `OracleConnectionBuilder`                 | `user``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |

<!-- -->

- - ### Method Detail

    - #### user

          OracleConnectionBuilder user(String user)

      Parameters:
      `user` -

      Returns:
      This `OracleConnectionBuilder` object

    <!-- -->

    - #### password

          OracleConnectionBuilder password(String password)

      Parameters:
      `password` -

      Returns:
      This `OracleConnectionBuilder` object

    <!-- -->

    - #### shardingKey

          OracleConnectionBuilder shardingKey(OracleShardingKey shardingKey)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This `OracleConnectionBuilder` object

    <!-- -->

    - #### superShardingKey

          OracleConnectionBuilder superShardingKey(OracleShardingKey superShardingKey)

      Parameters:
      `superShardingKey` - Super sharding key object that needs to be part of connection request

      Returns:
      This `OracleConnectionBuilder` object

    <!-- -->

    - #### gssCredential

          OracleConnectionBuilder gssCredential(GSSCredential credential)

      Provide the GSSCredential used to authenticate the connection.
      Parameters:
      `credential` - used to authenticate the connection. Not null.

    <!-- -->

    - #### sslContext

          OracleConnectionBuilder sslContext(SSLContext sslContext)

      Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.
      The SSLContext must be [initialized](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true#init_javax_net_ssl_KeyManager_A_javax_net_ssl_TrustManager_A_java_security_SecureRandom_) before building the connection. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Specifying a null value will clear any non-null value that may have been set previously, causing this builder to behave as if this method had never been called at all.

      Parameters:
      `sslContext` - An SSLContext to use as an SSLEngine factory.

      Returns:
      This `OracleConnectionBuilder` object

      Since:
      20

    <!-- -->

    - #### accessToken

          OracleConnectionBuilder accessToken(AccessToken accessToken)

      Specifies the `accessToken` to be used when creating a connection. The issuer of the token must be one that is supported by Oracle Database for client authentication.

      It is invalid to configure this builder with both a token and with a username or password. If both this method and `password(String)` or `user(String)` are invoked with non null values, then a [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) indicating an invalid configuration is thrown when creating a connection with this builder.

      Parameters:
      `accessToken` - the token to use for this connection. Not `null`.

      Returns:
      the same `ConnectionBuilder` instance

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - If the `accessToken` is `null`.

    <!-- -->

    - #### build

          OracleConnection build()
                          throws SQLException

      Builds the connection object.
      Returns:
      New `OracleConnection` that is created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.DRCPState.md)
- [Next Class](OracleConnectionWrapper.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
