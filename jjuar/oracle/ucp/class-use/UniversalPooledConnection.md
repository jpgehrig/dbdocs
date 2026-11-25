Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalPooledConnection.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.UniversalPooledConnection

- **Packages that use [UniversalPooledConnection](../UniversalPooledConnection.md)**

  | Package    | Description                                                                                                  |
  |------------|--------------------------------------------------------------------------------------------------------------|
  | oracle.ucp | Includes both required and optional callback interfaces that are used to implement connection pool features. |

- - ### Uses of [UniversalPooledConnection](../UniversalPooledConnection.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [UniversalPooledConnection](../UniversalPooledConnection.md)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                                                                |
    |----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalPooledConnection`](../UniversalPooledConnection.md) | UniversalConnectionPool.[`borrowConnection`](../UniversalConnectionPool.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` connectionRetrievalInfo)`<br>Gets a connection from the connection pool.                                    |
    | [`UniversalPooledConnection`](../UniversalPooledConnection.md) | ConnectionFactoryAdapter.[`createPooledConnection`](../ConnectionFactoryAdapter.md)`(java.lang.Object connection, `[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` connectionRequestInfo)`<br>Creates a UniversalPooledConnection object. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [UniversalPooledConnection](../UniversalPooledConnection.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalConnectionPool.[`closeConnection`](../UniversalConnectionPool.md)`(`[`UniversalPooledConnection`](../UniversalPooledConnection.md)` pooledConnection)`<br>Closes the pooled connection.                        |
    | `void`            | UniversalConnectionPool.[`returnConnection`](../UniversalConnectionPool.md)`(`[`UniversalPooledConnection`](../UniversalPooledConnection.md)` pooledConnection)`<br>Returns a connection back into the connection pool. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalPooledConnection.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
