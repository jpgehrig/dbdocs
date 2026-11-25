Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
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

oracle.jdbc.xa

## Class OracleXAConnectionBuilderImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.xa.OracleXAConnectionBuilderImpl

<!-- -->

- All Implemented Interfaces:
  [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)

  ------------------------------------------------------------------------



      public abstract class OracleXAConnectionBuilderImpl
      extends Object
      implements OracleXAConnectionBuilder

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

    | Constructor and Description          |
    |--------------------------------------|
    | `OracleXAConnectionBuilderImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                 | Method and Description                                                                                                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`OracleXAConnection`](../datasource/OracleXAConnection.md)                                            | `build``()`<br>Builds the connection of type OracleXAConnection.                                                                                                                                                                          |
    | [`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true) | `getGSSCredential``()`                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getInstanceName``()`                                                                                                                                                                                                                     |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)                                           | `getOracleConnectionBuilder``(`[`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)` connBldr)`<br>Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance . |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getPassword``()`                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getServiceName``()`                                                                                                                                                                                                                      |
    | [`OracleShardingKeyImpl`](../pool/OracleShardingKeyImpl.md)                                                       | `getShardingKey``()`                                                                                                                                                                                                                      |
    | [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)       | `getSSLContext``()`                                                                                                                                                                                                                       |
    | [`OracleShardingKeyImpl`](../pool/OracleShardingKeyImpl.md)                                                       | `getSuperShardingKey``()`                                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                   | `getUser``()`                                                                                                                                                                                                                             |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `gssCredential``(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                       |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `instanceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                                          |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `password``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                  |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `serviceName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                                            |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `shardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                             |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `sslContext``(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                                           |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `superShardingKey``(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                   |
    | `OracleXAConnectionBuilderImpl`                                                                                   | `user``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                          |

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

    - #### OracleXAConnectionBuilderImpl

          public OracleXAConnectionBuilderImpl()

  <!-- -->

  - ### Method Detail

    - #### build

          public abstract OracleXAConnection build()
                                            throws SQLException

      Builds the connection of type OracleXAConnection. The build() method can be called only once on a builder object.
      Specified by:
      [`build`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Returns:
      the new object that is built.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`OracleXAConnectionBuilder.build()`](../OracleXAConnectionBuilder.md)

    <!-- -->

    - #### password

          public OracleXAConnectionBuilderImpl password(String password)

      Specified by:
      [`password`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Parameters:
      `password` - Password to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleXAConnectionBuilder.password(java.lang.String)`](../OracleXAConnectionBuilder.md)

    <!-- -->

    - #### user

          public OracleXAConnectionBuilderImpl user(String user)

      Specified by:
      [`user`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Parameters:
      `user` - User Name to be a part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleXAConnectionBuilder.user(java.lang.String)`](../OracleXAConnectionBuilder.md)

    <!-- -->

    - #### serviceName

          public OracleXAConnectionBuilderImpl serviceName(String serviceName)

      Parameters:
      `serviceName` - Service name to be part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      `oracle.jdbc.OracleXAConnectionBuilder#serviceName(java.lang.String)`

    <!-- -->

    - #### instanceName

          public OracleXAConnectionBuilderImpl instanceName(String instanceName)

      Parameters:
      `instanceName` - Instance name to be part of the connection request

      Returns:
      This instance of the connection builder.

      See Also:
      `oracle.jdbc.OracleXAConnectionBuilder#instanceName(java.lang.String)`

    <!-- -->

    - #### shardingKey

          public OracleXAConnectionBuilderImpl shardingKey(OracleShardingKey shardingKey)

      Specified by:
      [`shardingKey`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleXAConnectionBuilder.shardingKey(oracle.jdbc.OracleShardingKey)`](../OracleXAConnectionBuilder.md)

    <!-- -->

    - #### superShardingKey

          public OracleXAConnectionBuilderImpl superShardingKey(OracleShardingKey superShardingKey)

      Specified by:
      [`superShardingKey`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Parameters:
      `superShardingKey` - Super Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

      See Also:
      [`OracleXAConnectionBuilder.superShardingKey(oracle.jdbc.OracleShardingKey)`](../OracleXAConnectionBuilder.md)

    <!-- -->

    - #### gssCredential

          public OracleXAConnectionBuilderImpl gssCredential(GSSCredential credential)

      Provide the GSSCredential used to authenticate the connection.
      Specified by:
      [`gssCredential`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

      Parameters:
      `credential` - used to authenticate the connection. Not null.

    <!-- -->

    - #### sslContext

          public OracleXAConnectionBuilderImpl sslContext(SSLContext sslContext)

      Set the SSLContext on this builder.
      Specified by:
      [`sslContext`](../OracleXAConnectionBuilder.md) in interface [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)

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

    - #### getOracleConnectionBuilder

          public OracleConnectionBuilderImpl getOracleConnectionBuilder(OracleConnectionBuilderImpl connBldr)

      Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance .
      Parameters:
      `connBldr` - The connection builder instance that needs to be initialized with this builder attributes.

      Returns:
      Connection builder object

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAConnectionBuilderImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnection.md)
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
