Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleXAConnectionBuilder.md)
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

## Uses of Interface oracle.jdbc.OracleXAConnectionBuilder

- **Packages that use [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.xa         | Provides classes that implement the JDBC XA APIs.                                                                             |

- - ### Uses of [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`gssCredential`](../OracleXAConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`gssCredential`](../OracleXAConnectionBuilder.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection.                                                                                                                                                                                                                          |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`password`](../OracleXAConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`password`](../OracleXAConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                                                                                                                                                                                                                                                     |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`shardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`shardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                                                                                                |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`sslContext`](../OracleXAConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`sslContext`](../OracleXAConnectionBuilder.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Specifies a [`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true) to use as a factory for [SSLEngine](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLEngine.html?is-external=true) objects that carry out the TLS protocol. |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`superShardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`superShardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                                                                                      |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`user`](../OracleXAConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXAConnectionBuilder.[`user`](../OracleXAConnectionBuilder.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                                                                                                                                                                                                                                             |

  - ### Uses of [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Methods in [oracle.jdbc.datasource](../datasource/package-summary.md) that return [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)**

    | Modifier and Type                                              | Method and Description                                                                                                                          |
    |----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXADataSource.[`createXAConnectionBuilder`](../datasource/OracleXADataSource.md)`()`<br>Creates a new `OracleXAConnectionBuilder` instance |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXADataSource.[`createXAConnectionBuilder`](../datasource/OracleXADataSource.md)`()`<br>Creates a new `OracleXAConnectionBuilder` instance |

  - ### Uses of [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md) in [oracle.jdbc.xa](../xa/package-summary.md)

    **Classes in [oracle.jdbc.xa](../xa/package-summary.md) that implement [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)**

    | Modifier and Type | Class and Description                                                                                                           |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md)<br>Oracle Implementation class for Connection Builder |

    **Methods in [oracle.jdbc.xa](../xa/package-summary.md) that return [OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md)**

    | Modifier and Type                                              | Method and Description                                                                                                                  |
    |----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXADataSource.[`createXAConnectionBuilder`](../xa/OracleXADataSource.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md) | OracleXADataSource.[`createXAConnectionBuilder`](../xa/OracleXADataSource.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleXAConnectionBuilder.md)
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
