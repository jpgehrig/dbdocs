Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnectionBuilder.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.OracleConnectionBuilder

- **Packages that use [OracleConnectionBuilder](../OracleConnectionBuilder.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |

- - ### Uses of [OracleConnectionBuilder](../OracleConnectionBuilder.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleConnectionBuilder](../OracleConnectionBuilder.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    |------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`accessToken`](../OracleConnectionBuilder.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Specifies the `accessToken` to be used when creating a connection.                                                                                                                                                                                                                                                                                                      |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`accessToken`](../OracleConnectionBuilder.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Specifies the `accessToken` to be used when creating a connection.                                                                                                                                                                                                                                                                                                      |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`gssCredential`](../OracleConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`gssCredential`](../OracleConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`password`](../OracleConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`password`](../OracleConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`shardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`shardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`sslContext`](../OracleConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`sslContext`](../OracleConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`superShardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`superShardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`user`](../OracleConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`user`](../OracleConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |

  - ### Uses of [OracleConnectionBuilder](../OracleConnectionBuilder.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Methods in [oracle.jdbc.datasource](../datasource/package-summary.md) that return [OracleConnectionBuilder](../OracleConnectionBuilder.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                 |
    |------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleDataSource.[`createConnectionBuilder`](../datasource/OracleDataSource.md)`()`<br>Create a new `OracleConnectionBuilder` instance |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleDataSource.[`createConnectionBuilder`](../datasource/OracleDataSource.md)`()`<br>Create a new `OracleConnectionBuilder` instance |

  - ### Uses of [OracleConnectionBuilder](../OracleConnectionBuilder.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../pool/package-summary.md) that implement [OracleConnectionBuilder](../OracleConnectionBuilder.md)**

    | Modifier and Type | Class and Description                                                                                                         |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)<br>Oracle Implementation class for Connection Builder |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnectionBuilder.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
