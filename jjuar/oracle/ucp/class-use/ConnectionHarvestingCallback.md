Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionHarvestingCallback.md)
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

## Uses of Interface oracle.ucp.ConnectionHarvestingCallback

- **Packages that use [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp      | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                            |
    |----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConnectionHarvestingCallback`](../ConnectionHarvestingCallback.md) | UniversalPooledConnection.[`getConnectionHarvestingCallback`](../UniversalPooledConnection.md)`()`<br>Obtains the `ConnectionHarvestingCallback` registered with this connection. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalPooledConnection.[`registerConnectionHarvestingCallback`](../UniversalPooledConnection.md)`(`[`ConnectionHarvestingCallback`](../ConnectionHarvestingCallback.md)` cbk)`<br>Registers a `ConnectionHarvestingCallback` with this connection. |

  - ### Uses of [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) with parameters of type [ConnectionHarvestingCallback](../ConnectionHarvestingCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | HarvestableConnection.[`registerConnectionHarvestingCallback`](../jdbc/HarvestableConnection.md)`(`[`ConnectionHarvestingCallback`](../ConnectionHarvestingCallback.md)` cbk)`<br>Registers a ConnectionHarvestingCallback with the this connection. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionHarvestingCallback.md)
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
