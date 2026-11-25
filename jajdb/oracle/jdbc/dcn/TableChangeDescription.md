Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TableChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](RowChangeDescription.RowOperation.md)
- [Next Class](TableChangeDescription.TableOperation.md)

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

## Interface TableChangeDescription

-

  ------------------------------------------------------------------------



      public interface TableChangeDescription

  This interface describes a database change at the table level.
  The information includes:

  - The name of the table;
  - The type of operation that affected this table. The operation can be: a DML operation (such as insert, delete, update) or a DDL operation (such as alter or drop);
  - The row level change description which is available only if the operation is a DML operation.

  Since:
  11.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                            |
    |-------------------|--------------------------------------------------------------------------------------|
    | `static class `   | [`TableChangeDescription.TableOperation`](TableChangeDescription.TableOperation.md)  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                                                                          | Method and Description                                                                         |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
    | `int`                                                                                                                                                                                      | `getObjectNumber``()`<br>Returns the object number (Oracle internal information).              |
    | [`RowChangeDescription`](RowChangeDescription.md)`[]`                                                                                                                                      | `getRowChangeDescription``()`<br>Returns the row level change description of the notification. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                            | `getTableName``()`<br>Returns the name of the table.                                           |
    | [`EnumSet`](http://download.oracle.com/javase/8/docs/api/java/util/EnumSet.html?is-external=true)`<`[`TableChangeDescription.TableOperation`](TableChangeDescription.TableOperation.md)`>` | `getTableOperations``()`<br>Returns the table operations that affected this table.             |

<!-- -->

- - ### Method Detail

    - #### getTableOperations

          EnumSet<TableChangeDescription.TableOperation> getTableOperations()

      Returns the table operations that affected this table.
      More than one operation can have affected this table. For example, one row can have been inserted and another can have been deleted. So this method returns an `EnumSet` of `TableOperation`.

      The row level description will contain the details but it isn't always available.

    <!-- -->

    - #### getTableName

          String getTableName()

      Returns the name of the table.

    <!-- -->

    - #### getObjectNumber

          int getObjectNumber()

      Returns the object number (Oracle internal information).

    <!-- -->

    - #### getRowChangeDescription

          RowChangeDescription[] getRowChangeDescription()

      Returns the row level change description of the notification.
      The row level change description is only available if the operation is a DML operation such as insert, update or delete.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TableChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](RowChangeDescription.RowOperation.md)
- [Next Class](TableChangeDescription.TableOperation.md)

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
