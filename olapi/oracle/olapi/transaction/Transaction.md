Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](NotPreparedException.md)
- [Next Class](TransactionalObjectInvalidException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.transaction

## Interface Transaction

-

  ------------------------------------------------------------------------



      public interface Transaction

  An interface that represents an OLAP transaction with an Oracle Database instance. An application interacts with the Oracle OLAP Java API implementation of the `Transaction` interface through a `TransactionProvider`.
  An application creates metadata and `Source` objects in the context of the current `Transaction`. Using a `TransactionProvider`, an application can create a child `Transaction`. An application can get and save a `Transaction` and make it the current `Transaction` as desired.

  The changes an application makes in a `Transaction` do not take effect until the application commits the `Transaction`. An application can roll back a `Transaction` to discard the changes instead of committing them.

  See Also:
  [`TransactionProvider`](TransactionProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                          | Method and Description                                                                  |
    |--------------------------------------------|-----------------------------------------------------------------------------------------|
    | [`UserSession`](../session/UserSession.md) | `getUserSession``()`<br>Gets the `UserSession` that is the owner of this `Transaction`. |

<!-- -->

- - ### Method Detail

    - #### getUserSession

          UserSession getUserSession()

      Gets the `UserSession` that is the owner of this `Transaction`. The `UserSession` represents the Oracle OLAP session and the connection to the Oracle Database instance.
      Returns:
      The `UserSession` that owns this `Transaction`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NotPreparedException.md)
- [Next Class](TransactionalObjectInvalidException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
