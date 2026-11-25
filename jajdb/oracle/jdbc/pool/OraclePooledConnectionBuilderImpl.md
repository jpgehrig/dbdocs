Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnection.md)
- [Next Class](OracleShardingKeyBuilderImpl.md)

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

## Class OraclePooledConnectionBuilderImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.OraclePooledConnectionBuilderImpl

<!-- -->

- All Implemented Interfaces:
  [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)

  ------------------------------------------------------------------------



      public abstract class OraclePooledConnectionBuilderImpl
      extends Object
      implements OraclePooledConnectionBuilder

  Oracle Implementation class for Connection Builder

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                             | Field and Description |
    |-------------------------------------------------------------------------------------------------------------------------------|-----------------------|
    | `protected `[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true) | `gssCredential`       |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `instanceName`        |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `password`            |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `serviceName`         |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md)                                                                    | `shardingKey`         |
    | `protected `[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)       | `sslContext`          |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md)                                                                    | `superShardingKey`    |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `user`                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description              |
    |------------------------------------------|
    | `OraclePooledConnectionBuilderImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                 | Method and Description                                                                                                                                                                                              |
    |-------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`OraclePooledConnection`](../datasource/OraclePooledConnection.md)                                    | `build``()`<br>Builds the connection of type OraclePooledConnection.                                                                                                                                                |
    | [`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true) | `getGSSCredential``()`                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getInstanceName``()`                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getPassword``()`                                                                                                                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getServiceName``()`                                                                                                                                                                                                |
    | [`OracleShardingKeyImpl`](OracleShardingKeyImpl.md)                                                               | `getShardingKey``()`                                                                                                                                                                                                |
    | [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)       | `getSSLContext``()`                                                                                                                                                                                                 |
    | [`OracleShardingKeyImpl`](OracleShardingKeyImpl.md)                                                               | `getSuperShardingKey``()`                                                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getUser``()`                                                                                                                                                                                                       |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `gssCredential``(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection. |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `instanceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                    |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `password``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                            |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `serviceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                      |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `shardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                       |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `sslContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                     |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `superShardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                             |
    | `OraclePooledConnectionBuilderImpl`                                                                               | `user``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                    |

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

    - #### gssCredential

          protected GSSCredential gssCredential

    <!-- -->

    - #### sslContext

          protected SSLContext sslContext

  <!-- -->

  - ### Constructor Detail

    - #### OraclePooledConnectionBuilderImpl

          public OraclePooledConnectionBuilderImpl()

  <!-- -->

  - ### Method Detail

    - #### build

          public abstract OraclePooledConnection build()
                                                throws SQLException

      Builds the connection of type OraclePooledConnection.
      Specified by:
      [`build`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Returns:
      the new object that is built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`OracleConnectionBuilder.build()`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### password

          public OraclePooledConnectionBuilderImpl password(String password)

      Specified by:
      [`password`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Parameters:
      `password` - Password to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.password(java.lang.String)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### user

          public OraclePooledConnectionBuilderImpl user(String user)

      Specified by:
      [`user`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Parameters:
      `user` - User Name to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.user(java.lang.String)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### serviceName

          public OraclePooledConnectionBuilderImpl serviceName(String serviceName)

      Parameters:
      `serviceName` - Service name to be part of the connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### instanceName

          public OraclePooledConnectionBuilderImpl instanceName(String instanceName)

      Parameters:
      `instanceName` - Instance name to be part of the connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### shardingKey

          public OraclePooledConnectionBuilderImpl shardingKey(OracleShardingKey shardingKey)

      Specified by:
      [`shardingKey`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.shardingKey(oracle.jdbc.OracleShardingKey)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### superShardingKey

          public OraclePooledConnectionBuilderImpl superShardingKey(OracleShardingKey superShardingKey)

      Specified by:
      [`superShardingKey`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Parameters:
      `superShardingKey` - Super Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleConnectionBuilder.superShardingKey(oracle.jdbc.OracleShardingKey)`](../OracleConnectionBuilder.md)

    <!-- -->

    - #### gssCredential

          public OraclePooledConnectionBuilderImpl gssCredential(GSSCredential credential)

      Provide the GSSCredential used to authenticate the connection.
      Specified by:
      [`gssCredential`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

      Parameters:
      `credential` - used to authenticate the connection. Not null.

    <!-- -->

    - #### sslContext

          public OraclePooledConnectionBuilderImpl sslContext(SSLContext sslContext)

      Set the SSLContext on this builder.
      Specified by:
      [`sslContext`](../OraclePooledConnectionBuilder.md) in interface [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md)

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

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePooledConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnection.md)
- [Next Class](OracleShardingKeyBuilderImpl.md)

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
