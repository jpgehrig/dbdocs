Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](SpecifiedCursorManager.md)
- [Next Class](StringParameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Interface SQLCursorManager

-

  ------------------------------------------------------------------------



      public interface SQLCursorManager

  An interface for an object that gets the SQL statement that the Oracle OLAP SQL Generator generates for a `Source` that specifies a query. Before you create an instance of an implementation of `SQLCursorManager`, you must commit the current `Transaction`. You create an instance of a `SQLCursorManager` with the `createSQLCursorManager` or `createSQLCursorManagers` methods of a `DataProvider`.
  See Also:
  [`TransactionProvider`](../../transaction/TransactionProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                           |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `close``()`<br>Closes the `SQLCursorManager` and releases the resources associated with it.                                                                                                      |
    | `java.lang.String` | `generateSQL``()`<br>Gets a `String` that contains the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager`.                                                    |
    | `void`             | `generateSQL``(java.lang.StringBuffer buffer)`<br>Gets the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager` and appends it to the specified `StringBuffer`. |
    | `boolean`          | `isOpen``()`<br>Indicates whether this `SQLCursorManager` is open.                                                                                                                               |

<!-- -->

- - ### Method Detail

    - #### isOpen

          boolean isOpen()

      Indicates whether this `SQLCursorManager` is open.
      Returns:
      `true` if the `SQLCursorManager` is open and `false` if it is closed.

    <!-- -->

    - #### close

          void close()

      Closes the `SQLCursorManager` and releases the resources associated with it.

    <!-- -->

    - #### generateSQL

          java.lang.String generateSQL()

      Gets a `String` that contains the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager`.
      Returns:
      A `String` that contains the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager`.

    <!-- -->

    - #### generateSQL

          void generateSQL(java.lang.StringBuffer buffer)

      Gets the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager` and appends it to the specified `StringBuffer`.
      Parameters:
      `buffer` - A `StringBuffer` that contains the SQL statement that Oracle OLAP generates for the `Source` for this `SQLCursorManager`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SpecifiedCursorManager.md)
- [Next Class](StringParameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
