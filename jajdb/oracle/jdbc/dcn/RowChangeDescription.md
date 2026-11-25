Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/RowChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](QueryChangeDescription.QueryChangeEventType.md)
- [Next Class](RowChangeDescription.RowOperation.md)

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

oracle.jdbc.dcn

## Interface RowChangeDescription

-

  ------------------------------------------------------------------------



      public interface RowChangeDescription

  This interface describes the row level information that can be retrieved from a database change event.
  The information includes:

  - The row id;
  - The kind of DML operation that affected this row (the rows was either inserted, updated or deleted).

  Since:
  11.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                    |
    |-------------------|------------------------------------------------------------------------------|
    | `static class `   | [`RowChangeDescription.RowOperation`](RowChangeDescription.RowOperation.md)  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                                 |
    |-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
    | [`ROWID`](../../sql/ROWID.md)                                               | `getRowid``()`<br>Returns the row id of the row.                                                       |
    | [`RowChangeDescription.RowOperation`](RowChangeDescription.RowOperation.md) | `getRowOperation``()`<br>Returns the operation kind: this row was either inserted, updated or deleted. |

<!-- -->

- - ### Method Detail

    - #### getRowOperation

          RowChangeDescription.RowOperation getRowOperation()

      Returns the operation kind: this row was either inserted, updated or deleted.

    <!-- -->

    - #### getRowid

          ROWID getRowid()

      Returns the row id of the row.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/RowChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](QueryChangeDescription.QueryChangeEventType.md)
- [Next Class](RowChangeDescription.RowOperation.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
