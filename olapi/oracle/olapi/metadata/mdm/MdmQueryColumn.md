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

- [Prev Class](MdmQuery.md)
- [Next Class](MdmRootSchema.md)

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

## Interface MdmQueryColumn

- All Known Implementing Classes:
  [MdmAttribute](MdmAttribute.md), [MdmBaseAttribute](MdmBaseAttribute.md), [MdmBaseMeasure](MdmBaseMeasure.md), [MdmColumn](MdmColumn.md), [MdmDerivedAttribute](MdmDerivedAttribute.md), [MdmDerivedMeasure](MdmDerivedMeasure.md), [MdmMeasure](MdmMeasure.md), [MdmMultiValuedAttribute](MdmMultiValuedAttribute.md), [MdmMultiValuedDerivedAttribute](MdmMultiValuedDerivedAttribute.md), [MdmSingleValuedAttribute](MdmSingleValuedAttribute.md), [MdmViewColumn](MdmViewColumn.md)

  ------------------------------------------------------------------------



      public interface MdmQueryColumn

  An interface for an object that represents a column of a table or view that is associated with an `MdmQuery`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                | Method and Description                                                  |
    |--------------------------------------------------|-------------------------------------------------------------------------|
    | [`BaseMetadataObject`](../BaseMetadataObject.md) | `getColumnObject``()`<br>Gets the column object.                        |
    | `java.lang.String`                               | `getName``()`<br>Gets the name of the column.                           |
    | [`SQLDataType`](../../syntax/SQLDataType.md)     | `getSQLDataType``()`<br>Gets the `SQLDataType` of the `MdmQueryColumn`. |

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName()

      Gets the name of the column.
      Returns:
      A `String` that contains the name of the column.

    <!-- -->

    - #### getSQLDataType

          SQLDataType getSQLDataType()

      Gets the `SQLDataType` of the `MdmQueryColumn`.
      Returns:
      The `SQLDataType` of the `MdmQueryColumn`.

    <!-- -->

    - #### getColumnObject

          BaseMetadataObject getColumnObject()

      Gets the column object.
      Returns:
      A `BaseMetadataObject` that represents the column.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmQuery.md)
- [Next Class](MdmRootSchema.md)

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
