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

- [Prev Class](MdmValueHierarchy.md)
- [Next Class](MdmViewColumnOwner.md)

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

oracle.olapi.metadata.mdm

## Class MdmViewColumn

- java.lang.Object

- - oracle.olapi.metadata.mdm.MdmViewColumn

<!-- -->

- All Implemented Interfaces:
  [MdmQueryColumn](MdmQueryColumn.md)

  ------------------------------------------------------------------------



      public final class MdmViewColumn
      extends java.lang.Object
      implements MdmQueryColumn

  An object that represents a column in a view in an Oracle Database.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                     |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BaseMetadataObject`](../BaseMetadataObject.md) | `getColumnObject``()`<br>Gets the owner of this `MdmViewColumn` as a `BaseMetadataObject`.                                                 |
    | `java.lang.String`                               | `getName``()`<br>Gets the name of the column for use in an `Expression`.                                                                   |
    | [`MdmViewColumnOwner`](MdmViewColumnOwner.md)    | `getOwner``()`<br>Gets the `MdmViewColumnOwner` that owns this `MdmViewColumn`, such as an `MdmPrimaryDimension` or an `MdmBaseAttribute`. |
    | [`SQLDataType`](../../syntax/SQLDataType.md)     | `getSQLDataType``()`<br>Gets the `SQLDataType` associated with the column.                                                                 |
    | `java.lang.String`                               | `getViewColumnName``()`<br>Gets the name of the column in the view.                                                                        |
    | `void`                                           | `setViewColumnName``(java.lang.String name)`<br>Specifies the name of the column in the view.                                              |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Gets the name of the column for use in an `Expression`.
      Specified by:
      [`getName`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      A `String` that contains the name of the column.

      See Also:
      [`Expression`](../../syntax/Expression.md)

    <!-- -->

    - #### getViewColumnName

          public java.lang.String getViewColumnName()

      Gets the name of the column in the view.
      Returns:
      A `String` that contains the name of the column.

    <!-- -->

    - #### setViewColumnName

          public void setViewColumnName(java.lang.String name)

      Specifies the name of the column in the view.
      Parameters:
      `name` - A `String` that contains the name of the column.

    <!-- -->

    - #### getSQLDataType

          public SQLDataType getSQLDataType()

      Gets the `SQLDataType` associated with the column.
      Specified by:
      [`getSQLDataType`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      The `SQLDataType` associated with the column.

    <!-- -->

    - #### getColumnObject

          public final BaseMetadataObject getColumnObject()

      Gets the owner of this `MdmViewColumn` as a `BaseMetadataObject`.
      Specified by:
      [`getColumnObject`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      The `BaseMetadataObject` that owns this `MdmViewColumn`.

    <!-- -->

    - #### getOwner

          public MdmViewColumnOwner getOwner()

      Gets the `MdmViewColumnOwner` that owns this `MdmViewColumn`, such as an `MdmPrimaryDimension` or an `MdmBaseAttribute`.
      Returns:
      The `MdmViewColumnOwner` that owns this `MdmViewColumn`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmValueHierarchy.md)
- [Next Class](MdmViewColumnOwner.md)

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
