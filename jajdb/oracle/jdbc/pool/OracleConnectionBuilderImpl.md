Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleConnectionCache.md)

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

## Class OracleConnectionBuilderImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OracleConnectionBuilderImpl

<!-- -->

- All Implemented Interfaces:
  [OracleConnectionBuilder](../OracleConnectionBuilder.md)

  ------------------------------------------------------------------------



      public abstract class OracleConnectionBuilderImpl
      extends Object
      implements OracleConnectionBuilder

  Oracle Implementation class for Connection Builder

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                                                                                             | Field and Description                                                                                                |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `protected `[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)                                                                 | `gssCredential`                                                                                                      |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `instanceName`                                                                                                       |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `password`                                                                                                           |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `serviceName`                                                                                                        |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md)                                                                                                                                    | `shardingKey`                                                                                                        |
    | `protected `[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)                                                                       | `sslContext`                                                                                                         |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md)                                                                                                                                    | `superShardingKey`                                                                                                   |
    | `protected `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | `tokenSupplier`<br>Supplier of access tokens that this builder is configured to use for authenticating a connection. |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `user`                                                                                                               |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description        |
    |------------------------------------|
    | `OracleConnectionBuilderImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                                 | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                      |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `accessToken``(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Sets the `accessToken(oracle.jdbc.AccessToken)` field of this builder.                                                                                                                                                                                                                                                                                 |
    | `abstract `[`OracleConnection`](../OracleConnection.md)                                                                                                                           | `build``()`<br>Builds the connection of type OracleConnection.                                                                                                                                                                                                                                                                                                                                                              |
    | [`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)                                                                 | `getGSSCredential``()`                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `getInstanceName``()`                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `getPassword``()`                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `getServiceName``()`                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`OracleShardingKeyImpl`](OracleShardingKeyImpl.md)                                                                                                                               | `getShardingKey``()`                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)                                                                       | `getSSLContext``()`                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`OracleShardingKeyImpl`](OracleShardingKeyImpl.md)                                                                                                                               | `getSuperShardingKey``()`                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | `getTokenSupplier``()`<br>Returns a supplier of `AccessToken`s if one has been specified by user code calling `accessToken(AccessToken)`, or by internal code calling `setTokenSupplier(Supplier)`.                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                   | `getUser``()`                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `gssCredential``(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                         |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `instanceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                                                                                                                                                                                                                            |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `password``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                    |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `serviceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                                                                                            | `setTokenSupplier``(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Internal API to configure this builder with a [`Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true) of [`AccessToken`](../AccessToken.md)s. |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `shardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                               |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `sslContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                                                                                                                                                                                                                             |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `superShardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                     |
    | `OracleConnectionBuilderImpl`                                                                                                                                                     | `user``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                                                                                            | `verifyBuildConfiguration``()`<br>Verifies if this builder has been configured such that a call to `build()` will produce a valid connection.                                                                                                                                                                                                                                                                               |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### user

          protected String user

    <!-- -->

    - #### password

          protected String password

    <!-- -->

    - #### serviceName

          protected String serviceName

    <!-- -->

    - #### instanceName

          protected String instanceName

    <!-- -->

    - #### shardingKey

          protected OracleShardingKey shardingKey

    <!-- -->

    - #### superShardingKey

          protected OracleShardingKey superShardingKey

    <!-- -->

    - #### sslContext

          protected SSLContext sslContext

    <!-- -->

    - #### tokenSupplier

          protected java.util.function.Supplier<? extends AccessToken> tokenSupplier

      Supplier of access tokens that this builder is configured to use for authenticating a connection. The value of this field may either be specified by user code calling `accessToken(AccessToken)`, or internal code calling `setTokenSupplier(Supplier)`. In the case of user code calling the external API, this supplier returns a fixed value tht was passed into `accessToken(AccessToken)` **This field stores security sensitive valus. It should not be included in log messages. It should be annotated with @Blind by getter and setter methods.**

    <!-- -->

    - #### gssCredential

          protected GSSCredential gssCredential

  <!-- -->

  - ### Constructor Detail

    - #### OracleConnectionBuilderImpl

          public OracleConnectionBuilderImpl()

  <!-- -->

  - ### Method Detail

    - #### build

          public abstract OracleConnection build()
                                          throws SQLException

      Builds the connection of type OracleConnection. The build() method can be called only once on a builder object.
      Specified by:
      [`build`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Returns:
      the new object that is built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`OracleConnectionBuilder.build()`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### password

          public OracleConnectionBuilderImpl password(String password)

      Specified by:
      [`password`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `password` - Password to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.password(java.lang.String)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### user

          public OracleConnectionBuilderImpl user(String user)

      Specified by:
      [`user`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `user` - User Name to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.user(java.lang.String)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### serviceName

          public OracleConnectionBuilderImpl serviceName(String serviceName)

      Parameters:
      `serviceName` - Service name to be part of the connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### instanceName

          public OracleConnectionBuilderImpl instanceName(String instanceName)

      Parameters:
      `instanceName` - Instance name to be part of the connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### shardingKey

          public OracleConnectionBuilderImpl shardingKey(OracleShardingKey shardingKey)

      Specified by:
      [`shardingKey`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.shardingKey(oracle.jdbc.OracleShardingKey)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### superShardingKey

          public OracleConnectionBuilderImpl superShardingKey(OracleShardingKey superShardingKey)

      Specified by:
      [`superShardingKey`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `superShardingKey` - Super Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.superShardingKey(oracle.jdbc.OracleShardingKey)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### gssCredential

          public OracleConnectionBuilderImpl gssCredential(GSSCredential credential)

      Provide the GSSCredential used to authenticate the connection.
      Specified by:
      [`gssCredential`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `credential` - used to authenticate the connection. Not null.

    <!-- -->

    - #### sslContext

          public OracleConnectionBuilderImpl sslContext(SSLContext sslContext)

      Set the SSLContext on this builder.
      Specified by:
      [`sslContext`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `sslContext` - An SSLContext to set. May be null.

      Returns:
      This builder.

    <!-- -->

    - #### getSSLContext

          public final SSLContext getSSLContext()

      Returns:
      SSLContext set on this builder. May be null.

    <!-- -->

    - #### getUser

          public String getUser()

      Returns:
      user name set on the builder object

    <!-- -->

    - #### getPassword

          public String getPassword()

      Returns:
      password set on the builder object

    <!-- -->

    - #### getServiceName

          public String getServiceName()

      Returns:
      service name set on the builder object

    <!-- -->

    - #### getInstanceName

          public String getInstanceName()

      Returns:
      instance name set on the builder object

    <!-- -->

    - #### getShardingKey

          public OracleShardingKeyImpl getShardingKey()

      Returns:
      Sharding key if set on the builder object

    <!-- -->

    - #### getSuperShardingKey

          public OracleShardingKeyImpl getSuperShardingKey()

      Returns:
      Super sharding key if set on the builder object

    <!-- -->

    - #### getGSSCredential

          public GSSCredential getGSSCredential()

      Returns:
      GSSCredential set on the builder object

    <!-- -->

    - #### accessToken

          public final OracleConnectionBuilderImpl accessToken(AccessToken accessToken)

      Sets the `accessToken(oracle.jdbc.AccessToken)` field of this builder.

      The behavior and signature of this method are identical to what is specified by `oracle.jdbc.OracleConnectionBuilder#accessToken(char[], PrivateKey)`. Subclasses that implement `OracleConnectionBuilder` may inherit this implementation.

      Specified by:
      [`accessToken`](../OracleConnectionBuilder.md) in interface [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)

      Parameters:
      `accessToken` - the token to use for this connection. Not `null`.

      Returns:
      the same `ConnectionBuilder` instance

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - If `accessToken` is null.

    <!-- -->

    - #### setTokenSupplier

          public final void setTokenSupplier(java.util.function.Supplier<? extends AccessToken> tokenSupplier)

      Internal API to configure this builder with a [`Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true) of [`AccessToken`](../AccessToken.md)s. The `Supplier` may assume that the driver will only request a token from it immediately prior to sending that token to the database. This affords highest possible precision for a `Supplier` when estimating whether or not a cached token would reach the database before expiring.
      Parameters:
      `tokenSupplier` - Supplier of tokens

    <!-- -->

    - #### getTokenSupplier

          public final java.util.function.Supplier<? extends AccessToken> getTokenSupplier()

      Returns a supplier of `AccessToken`s if one has been specified by user code calling `accessToken(AccessToken)`, or by internal code calling `setTokenSupplier(Supplier)`. *The `Supplier` returned by this method should only be invoked to output a token immediately prior to sending the token to the database. This affords the supplier with the best possible preceision for estimating whether or not a cached token would reach the database before expiring.*
      Returns:
      Supplier of `AccessToken`s specified to this builder, or `null` if none has been specified.

    <!-- -->

    - #### verifyBuildConfiguration

          public final void verifyBuildConfiguration()
                                              throws SQLException

      Verifies if this builder has been configured such that a call to `build()` will produce a valid connection. This method verifies any conditions described in the JavaDocs of `AbstractConnectionBuilder`. Subclasses implement `build()` to call this method prior to returning a connection.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If this builder has an invalid configuration.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleConnectionCache.md)

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
