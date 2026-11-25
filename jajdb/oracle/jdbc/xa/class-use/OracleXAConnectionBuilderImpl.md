Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleXAConnectionBuilderImpl.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Class oracle.jdbc.xa.OracleXAConnectionBuilderImpl

- **Packages that use [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md)**

  | Package               | Description                                                         |
  |-----------------------|---------------------------------------------------------------------|
  | oracle.jdbc.replay    | Provides interfaces and factory methods for Application Continuity. |
  | oracle.jdbc.xa        | Provides classes that implement the JDBC XA APIs.                   |
  | oracle.jdbc.xa.client | Provides classes that implement the JDBC XA APIs.                   |

- - ### Uses of [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md) in [oracle.jdbc.replay](../../replay/package-summary.md)

    **Methods in [oracle.jdbc.replay](../../replay/package-summary.md) that return [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                 |
    |------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXADataSourceImpl.[`createXAConnectionBuilder`](../../replay/OracleXADataSourceImpl.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXADataSourceImpl.[`createXAConnectionBuilder`](../../replay/OracleXADataSourceImpl.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |

  - ### Uses of [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md) in [oracle.jdbc.xa](../package-summary.md)

    **Methods in [oracle.jdbc.xa](../package-summary.md) that return [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                                   |
    |------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`gssCredential`](../OracleXAConnectionBuilderImpl.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection. |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`gssCredential`](../OracleXAConnectionBuilderImpl.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection. |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`instanceName`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                    |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`instanceName`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                    |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`password`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                            |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`password`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                            |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`serviceName`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                      |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`serviceName`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                      |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` shardingKey)`                                                                                                                                    |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` shardingKey)`                                                                                                                                    |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`sslContext`](../OracleXAConnectionBuilderImpl.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                     |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`sslContext`](../OracleXAConnectionBuilderImpl.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                     |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` superShardingKey)`                                                                                                                          |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` superShardingKey)`                                                                                                                          |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`user`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                    |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`user`](../OracleXAConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                    |

  - ### Uses of [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md) in [oracle.jdbc.xa.client](../client/package-summary.md)

    **Methods in [oracle.jdbc.xa.client](../client/package-summary.md) that return [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                      |
    |------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXADataSource.[`createXAConnectionBuilder`](../client/OracleXADataSource.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |
    | [`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md) | OracleXADataSource.[`createXAConnectionBuilder`](../client/OracleXADataSource.md)`()`<br>Creates a new Oracle XA ConnectionBuilder instance |

    **Methods in [oracle.jdbc.xa.client](../client/package-summary.md) with parameters of type [OracleXAConnectionBuilderImpl](../OracleXAConnectionBuilderImpl.md)**

    | Modifier and Type                                                                                           | Method and Description                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | OracleXADataSource.[`getXAConnection`](../client/OracleXADataSource.md)`(`[`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md)` builder)`  |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true) | OracleXADataSource.[`getXAConnection`](../client/OracleXADataSource.md)`(`[`OracleXAConnectionBuilderImpl`](../OracleXAConnectionBuilderImpl.md)` builder)`  |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleXAConnectionBuilderImpl.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
