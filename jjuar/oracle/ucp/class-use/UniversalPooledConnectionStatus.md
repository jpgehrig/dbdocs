Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalPooledConnectionStatus.md)
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

## Uses of Class oracle.ucp.UniversalPooledConnectionStatus

- **Packages that use [UniversalPooledConnectionStatus](../UniversalPooledConnectionStatus.md)**

  | Package    | Description                                                                                                  |
  |------------|--------------------------------------------------------------------------------------------------------------|
  | oracle.ucp | Includes both required and optional callback interfaces that are used to implement connection pool features. |

- - ### Uses of [UniversalPooledConnectionStatus](../UniversalPooledConnectionStatus.md) in [oracle.ucp](../package-summary.md)

    **Fields in [oracle.ucp](../package-summary.md) declared as [UniversalPooledConnectionStatus](../UniversalPooledConnectionStatus.md)**

    | Modifier and Type                                                                   | Field and Description                                                                                                                                                                                                                   |
    |-------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_BAD`](../UniversalPooledConnectionStatus.md)<br>The pooled connection's status is bad.                                                                                                         |
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_CLOSE_ON_RETURN`](../UniversalPooledConnectionStatus.md)<br>The pooled connection should be closed and not put back into the pool when it is returned by the borrower.                         |
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_CLOSED`](../UniversalPooledConnectionStatus.md)<br>The pooled connection's status is closed.                                                                                                   |
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_NORMAL`](../UniversalPooledConnectionStatus.md)<br>The pooled connection's status is normal.                                                                                                   |
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_RECONNECTING`](../UniversalPooledConnectionStatus.md)<br>The pooled connection's status is reconnecting.                                                                                       |
    | `static `[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnectionStatus.[`STATUS_REPLACE_ON_RETURN`](../UniversalPooledConnectionStatus.md)<br>The pooled connection should be closed and replaced with a brand new connection in the pool when it is returned by the borrower. |

    **Methods in [oracle.ucp](../package-summary.md) that return [UniversalPooledConnectionStatus](../UniversalPooledConnectionStatus.md)**

    | Modifier and Type                                                          | Method and Description                                                                                                    |
    |----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md) | UniversalPooledConnection.[`getStatus`](../UniversalPooledConnection.md)`()`<br>Gets the status of the pooled connection. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [UniversalPooledConnectionStatus](../UniversalPooledConnectionStatus.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalPooledConnection.[`setStatus`](../UniversalPooledConnection.md)`(`[`UniversalPooledConnectionStatus`](../UniversalPooledConnectionStatus.md)` status)`<br>Sets the status of the pooled connection. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalPooledConnectionStatus.md)
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
