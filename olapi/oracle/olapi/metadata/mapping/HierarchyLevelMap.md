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

- [Prev Class](DimensionMap.md)
- [Next Class](MeasureMap.md)

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

oracle.olapi.metadata.mapping

## Class HierarchyLevelMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.DimensionMap](DimensionMap.md)

        - - oracle.olapi.metadata.mapping.HierarchyLevelMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class HierarchyLevelMap
      extends DimensionMap

  A `DimensionMap` that maps an `MdmHierarchyLevel` to a data source. You get a `HierarchyLevelMap` by calling the [`findOrCreateHierarchyLevelMap`](../mdm/MdmHierarchyLevel.md) method of the `MdmHierarchyLevel`. If you use a `HierarchyLevelMap` to map an `MdmHierarchyLevel`, then you should not also use a `MemberListMap` to map an `MdmPrimaryDimension` or an `MdmDimensionLevel` to the same data source.
  You must specify a `Query` or a `FromClause` for the `HierarchyLevelMap` unless the members of the `MdmHierarchyLevel` are the same as those of the associated `MdmDimensionLevel`. The `Query` must represent a table or a view. You must also specify a join `Condition` for the `HierarchyLevelMap` unless the level is the highest level of the hierarchy or the `MdmHierarchyLevel` has the same `Query` as the `MdmHierarchyLevel` for the next highest level.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                                            |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Condition`](../../syntax/Condition.md) | `getJoinCondition``()`<br>Gets the `Condition` that represents a join condition for the level.                                                    |
    | `void`                                   | `setJoinCondition``(`[`Condition`](../../syntax/Condition.md)` input)`<br>Specifies a `Condition` that represents a join condition for the level. |

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[DimensionMap](DimensionMap.md)

      [`addAttributeMap`](DimensionMap.md)`, `[`findOrCreateAttributeMap`](DimensionMap.md)`, `[`findOrCreateAttributeMap`](DimensionMap.md)`, `[`getAttributeMaps`](DimensionMap.md)`, `[`getDimension`](DimensionMap.md)`, `[`getFromClause`](DimensionMap.md)`, `[`getKeyExpression`](DimensionMap.md)`, `[`getQuery`](DimensionMap.md)`, `[`getWhereClause`](DimensionMap.md)`, `[`removeAttributeMap`](DimensionMap.md)`, `[`setDimension`](DimensionMap.md)`, `[`setFromClause`](DimensionMap.md)`, `[`setKeyExpression`](DimensionMap.md)`, `[`setQuery`](DimensionMap.md)`, `[`setWhereClause`](DimensionMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[ObjectMap](ObjectMap.md)

      [`getName`](ObjectMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setJoinCondition

          public void setJoinCondition(Condition input)

      Specifies a `Condition` that represents a join condition for the level.
      Parameters:
      `input` - The `Condition` to associate with the `HierarchyLevelMap`.

    <!-- -->

    - #### getJoinCondition

          public Condition getJoinCondition()

      Gets the `Condition` that represents a join condition for the level.
      Returns:
      The `Condition` associated with the `HierarchyLevelMap`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DimensionMap.md)
- [Next Class](MeasureMap.md)

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
