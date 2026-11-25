Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TimeToLiveConnectionTimeoutCallback.md)
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

## Uses of Interface oracle.ucp.TimeToLiveConnectionTimeoutCallback

- **Packages that use [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp      | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md)**

    | Modifier and Type                                                                  | Method and Description                                                                                                                                                                          |
    |------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TimeToLiveConnectionTimeoutCallback`](../TimeToLiveConnectionTimeoutCallback.md) | UniversalPooledConnection.[`getTimeToLiveConnectionTimeoutCallback`](../UniversalPooledConnection.md)`()`<br>Obtains the `TimeToLiveConnectionTimeoutCallback` registered with this connection. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                            |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalPooledConnection.[`registerTimeToLiveConnectionTimeoutCallback`](../UniversalPooledConnection.md)`(`[`TimeToLiveConnectionTimeoutCallback`](../TimeToLiveConnectionTimeoutCallback.md)` cbk)`<br>Registers a `TimeToLiveConnectionTimeoutCallback` with this connection. |

  - ### Uses of [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) with parameters of type [TimeToLiveConnectionTimeoutCallback](../TimeToLiveConnectionTimeoutCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | ConnectionWithTimeToLiveTimeout.[`registerTimeToLiveConnectionTimeoutCallback`](../jdbc/ConnectionWithTimeToLiveTimeout.md)`(`[`TimeToLiveConnectionTimeoutCallback`](../TimeToLiveConnectionTimeoutCallback.md)` cbk)`<br>Registers a time-to-live connection timeout callback with this connection. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TimeToLiveConnectionTimeoutCallback.md)
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
