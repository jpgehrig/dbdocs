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

- [Prev Class](MdmPrimaryDimension.md)
- [Next Class](MdmQueryColumn.md)

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

## Interface MdmQuery

- All Known Implementing Classes:
  [MdmCube](MdmCube.md), [MdmHierarchy](MdmHierarchy.md), [MdmLevelHierarchy](MdmLevelHierarchy.md), [MdmMeasureDimension](MdmMeasureDimension.md), [MdmPrimaryDimension](MdmPrimaryDimension.md), [MdmStandardDimension](MdmStandardDimension.md), [MdmTable](MdmTable.md), [MdmTimeDimension](MdmTimeDimension.md), [MdmValueHierarchy](MdmValueHierarchy.md)

  ------------------------------------------------------------------------



      public interface MdmQuery

  An interface for MDM objects that can have an associated `Query` object.
  See Also:
  [`Query`](../../syntax/Query.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                         | Method and Description                                                                              |
    |-----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
    | [`Query`](../../syntax/Query.md)                          | `getQuery``()`<br>Gets the `Query` associated with the `MdmQuery`.                                  |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                     | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                   |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>` | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with the `MdmQuery`. |
    | `java.lang.String`                                        | `getQueryName``()`<br>Gets the identifier of the `MdmQuery` object.                                 |

<!-- -->

- - ### Method Detail

    - #### getQueryName

          java.lang.String getQueryName()

      Gets the identifier of the `MdmQuery` object.
      Returns:
      A `String` that contains the identifier of the `MdmQuery` object.

    <!-- -->

    - #### getQuery

          Query getQuery()

      Gets the `Query` associated with the `MdmQuery`.
      Returns:
      The `Query` associated with the `MdmQuery`.

    <!-- -->

    - #### getQueryColumns

          java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with the `MdmQuery`.
      Returns:
      A `List` of the `MdmQueryColumn` objects associated with the `MdmQuery`.

    <!-- -->

    - #### getQueryColumn

          MdmQueryColumn getQueryColumn(java.lang.String name)

      Gets the specified `MdmQueryColumn`.
      Parameters:
      `name` - A `String` that contains the name of an `MdmQueryColumn`.

      Returns:
      The `MdmQueryColumn` that has the specified name.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmPrimaryDimension.md)
- [Next Class](MdmQueryColumn.md)

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
