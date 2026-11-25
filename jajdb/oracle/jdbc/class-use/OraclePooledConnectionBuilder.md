Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OraclePooledConnectionBuilder.md)
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

## Uses of Interface oracle.jdbc.OraclePooledConnectionBuilder

- **Packages that use [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.replay     | Provides interfaces and factory methods for Application Continuity.                                                           |

- - ### Uses of [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`gssCredential`](../OraclePooledConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`gssCredential`](../OraclePooledConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`password`](../OraclePooledConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`password`](../OraclePooledConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`shardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`shardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`sslContext`](../OraclePooledConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`sslContext`](../OraclePooledConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`superShardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`superShardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`user`](../OraclePooledConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`user`](../OraclePooledConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |

  - ### Uses of [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Methods in [oracle.jdbc.datasource](../datasource/package-summary.md) that return [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                          |
    |------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSource.[`createPooledConnectionBuilder`](../datasource/OracleConnectionPoolDataSource.md)`()`<br>Creates a new `OraclePooledConnectionBuilder` instance |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSource.[`createPooledConnectionBuilder`](../datasource/OracleConnectionPoolDataSource.md)`()`<br>Creates a new `OraclePooledConnectionBuilder` instance |

  - ### Uses of [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../pool/package-summary.md) that implement [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

    | Modifier and Type | Class and Description                                                                                                                     |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OraclePooledConnectionBuilderImpl`](../pool/OraclePooledConnectionBuilderImpl.md)<br>Oracle Implementation class for Connection Builder |

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) that return [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

    | Modifier and Type                                                      | Method and Description                                                                                           |
    |------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSource.[`createPooledConnectionBuilder`](../pool/OracleConnectionPoolDataSource.md)`()`  |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSource.[`createPooledConnectionBuilder`](../pool/OracleConnectionPoolDataSource.md)`()`  |

  - ### Uses of [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md) in [oracle.jdbc.replay](../replay/package-summary.md)

    **Methods in [oracle.jdbc.replay](../replay/package-summary.md) that return [OraclePooledConnectionBuilder](../OraclePooledConnectionBuilder.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                     |
    |------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSourceImpl.[`createPooledConnectionBuilder`](../replay/OracleConnectionPoolDataSourceImpl.md)`()`  |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OracleConnectionPoolDataSourceImpl.[`createPooledConnectionBuilder`](../replay/OracleConnectionPoolDataSourceImpl.md)`()`  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OraclePooledConnectionBuilder.md)
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
