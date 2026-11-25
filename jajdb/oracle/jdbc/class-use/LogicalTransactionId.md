Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../LogicalTransactionId.md)
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

## Uses of Interface oracle.jdbc.LogicalTransactionId

- **Packages that use [LogicalTransactionId](../LogicalTransactionId.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [LogicalTransactionId](../LogicalTransactionId.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [LogicalTransactionId](../LogicalTransactionId.md)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                        |
    |-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`LogicalTransactionId`](../LogicalTransactionId.md) | LogicalTransactionIdEvent.[`getLogicalTransactionId`](../LogicalTransactionIdEvent.md)`()`                                                                                                                                    |
    | [`LogicalTransactionId`](../LogicalTransactionId.md)            | OracleConnection.[`getLogicalTransactionId`](../OracleConnection.md)`()`<br>Gets the current Logical Transaction Id which are sent by the server in a piggy back message and hence this method call doesn't make a roundtrip. |
    | [`LogicalTransactionId`](../LogicalTransactionId.md)            | OracleConnectionWrapper.[`getLogicalTransactionId`](../OracleConnectionWrapper.md)`()`                                                                                                                                        |
    | [`LogicalTransactionId`](../LogicalTransactionId.md)            | OracleConnectionWrapper.[`getLogicalTransactionId`](../OracleConnectionWrapper.md)`()`                                                                                                                                        |
    | [`LogicalTransactionId`](../LogicalTransactionId.md)            | OracleConnection.[`getLogicalTransactionId`](../OracleConnection.md)`()`<br>Gets the current Logical Transaction Id which are sent by the server in a piggy back message and hence this method call doesn't make a roundtrip. |
    | `abstract `[`LogicalTransactionId`](../LogicalTransactionId.md) | LogicalTransactionIdEvent.[`getLogicalTransactionId`](../LogicalTransactionIdEvent.md)`()`                                                                                                                                    |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../LogicalTransactionId.md)
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
