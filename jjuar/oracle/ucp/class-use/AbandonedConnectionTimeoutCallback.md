Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AbandonedConnectionTimeoutCallback.md)
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

## Uses of Interface oracle.ucp.AbandonedConnectionTimeoutCallback

- **Packages that use [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp      | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md)**

    | Modifier and Type                                                                | Method and Description                                                                                                                                                                        |
    |----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AbandonedConnectionTimeoutCallback`](../AbandonedConnectionTimeoutCallback.md) | UniversalPooledConnection.[`getAbandonedConnectionTimeoutCallback`](../UniversalPooledConnection.md)`()`<br>Obtains the `AbandonedConnectionTimeoutCallback` registered with this connection. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                         |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalPooledConnection.[`registerAbandonedConnectionTimeoutCallback`](../UniversalPooledConnection.md)`(`[`AbandonedConnectionTimeoutCallback`](../AbandonedConnectionTimeoutCallback.md)` cbk)`<br>Registers an `AbandonedConnectionTimeoutCallback` with this connection. |

  - ### Uses of [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) with parameters of type [AbandonedConnectionTimeoutCallback](../AbandonedConnectionTimeoutCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | ConnectionWithAbandonedTimeout.[`registerAbandonedConnectionTimeoutCallback`](../jdbc/ConnectionWithAbandonedTimeout.md)`(`[`AbandonedConnectionTimeoutCallback`](../AbandonedConnectionTimeoutCallback.md)` cbk)`<br>Registers `AbandonedConnectionTimeoutCallback` with this connection. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AbandonedConnectionTimeoutCallback.md)
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
