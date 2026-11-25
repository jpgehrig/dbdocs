Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleParameterMetaData.md)
- [Next Class](OraclePreparedStatement.md)

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

## Interface OraclePooledConnectionBuilder

- All Known Implementing Classes:
  [OraclePooledConnectionBuilderImpl](pool/OraclePooledConnectionBuilderImpl.md)

  ------------------------------------------------------------------------



      public interface OraclePooledConnectionBuilder

  A builder created from a `OracleConnectionPoolDataSource` object, used to establish a connection to the database that the `OracleConnectionPoolDataSource` object represents. The connection properties that were specified for the `OracleConnectionPoolDataSource` are used as the default values by the `OraclePooledConnectionBuilder`.
  To use the builder, the corresponding builder method needs to be called for each parameter that needs to be part of the connection request followed by a build() method. The order in which the builder methods are called is not important. However if the same builder attribute is applied more than once, only the most recent value will be considered while building the connection. The builder object can be reused to build more than one connection and the builder attributes will be retained across multiple invocations of the build() method.

  The following example illustrates the use of `OraclePooledConnectionBuilder` to create a [`OraclePooledConnection`](datasource/OraclePooledConnection.md):


          OracleConnectionPoolDataSource ods =
              new oracle.jdbc.pool.OracleConnectionPoolDataSource();
          OracleShardingKey superShardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("EASTERN_REGION", JDBCType.VARCHAR)
                 .build();
          OracleShardingKey shardingKey =
              ods.createShardingKeyBuilder()
                 .subkey("PITTSBURGH_BRANCH", JDBCType.VARCHAR)
                 .build();
          OraclePooledConnection connection = ods.createConnectionBuilder()
                                                 .user("rafa")
                                                 .password("tennis")
                                                 .setShardingKey(shardingKey)
                                                 .setSuperShardingKey(superShardingKey)
                                                 .build();



  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnection`](datasource/OraclePooledConnection.md) | `build``()`<br>Builds the OraclePooledConnections object.                                                                                                                                                                                                                                                                                                                                                                                    |
    | `OraclePooledConnectionBuilder`                                  | `gssCredential``(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | `OraclePooledConnectionBuilder`                                  | `password``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | `OraclePooledConnectionBuilder`                                  | `shardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                   |
    | `OraclePooledConnectionBuilder`                                  | `sslContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | `OraclePooledConnectionBuilder`                                  | `superShardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                         |
    | `OraclePooledConnectionBuilder`                                  | `user``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |

<!-- -->

- - ### Method Detail

    - #### user

          OraclePooledConnectionBuilder user(String user)

      Parameters:
      `user` -

      Returns:
      This `OraclePooledConnectionBuilder` object.

    <!-- -->

    - #### password

          OraclePooledConnectionBuilder password(String password)

      Parameters:
      `password` -

      Returns:
      This `OraclePooledConnectionBuilder` object.

    <!-- -->

    - #### shardingKey

          OraclePooledConnectionBuilder shardingKey(OracleShardingKey shardingKey)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This `OraclePooledConnectionBuilder` object.

    <!-- -->

    - #### superShardingKey

          OraclePooledConnectionBuilder superShardingKey(OracleShardingKey superShardingKey)

      Parameters:
      `superShardingKey` - Super sharding key object that needs to be part of connection request

      Returns:
      This `OraclePooledConnectionBuilder` object.

    <!-- -->

    - #### gssCredential

          OraclePooledConnectionBuilder gssCredential(GSSCredential credential)

      Provide the GSSCredential used to authenticate the connection.
      Parameters:
      `credential` - used to authenticate the connection. Not null.

    <!-- -->

    - #### sslContext

          OraclePooledConnectionBuilder sslContext(SSLContext sslContext)

      Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol.
      The SSLContext must be [initialized](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true#init_javax_net_ssl_KeyManager_A_javax_net_ssl_TrustManager_A_java_security_SecureRandom_) before building the connection. The certificates specified by that initialization will be used in place of any connection properties that would otherwise have specified certificates, such as key store and trust store property values.

      Specifying a null value will clear any non-null value that may have been set previously, causing this builder to behave as if this method had never been called at all.

      Parameters:
      `sslContext` - An SSLContext to use as an SSLEngine factory.

      Returns:
      This `OraclePooledConnectionBuilder` object

    <!-- -->

    - #### build

          OraclePooledConnection build()
                                throws SQLException

      Builds the OraclePooledConnections object.
      Returns:
      New `OraclePooledConnection` that is built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleParameterMetaData.md)
- [Next Class](OraclePreparedStatement.md)

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
