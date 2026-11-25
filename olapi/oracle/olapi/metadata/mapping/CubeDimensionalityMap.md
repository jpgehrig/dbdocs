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

- [Prev Class](AttributeMap.md)
- [Next Class](CubeMap.md)

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

## Class CubeDimensionalityMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.ValueMap](ValueMap.md)

        - - oracle.olapi.metadata.mapping.CubeDimensionalityMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class CubeDimensionalityMap
      extends ValueMap

  Associates a `CubeMap` with `MdmDimension` and `MdmDimensionality` objects. An application creates a `CubeDimensionalityMap` with the [`findOrCreateCubeDimensionalityMap`](CubeMap.md) method of a `CubeMap`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                               |
    |----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CubeMap`](CubeMap.md)                            | `getCubeMap``()`<br>Gets the `CubeMap` that is the owner of this `CubeDimensionalityMap`.                                                                            |
    | [`MdmDimensionality`](../mdm/MdmDimensionality.md) | `getDimensionality``()`<br>Gets the `MdmDimensionality` associated with the `CubeDimensionalityMap`.                                                                 |
    | [`Condition`](../../syntax/Condition.md)           | `getJoinCondition``()`<br>Gets the `Condition` that represents the join condition for the dimension in the cube.                                                     |
    | [`MdmDimension`](../mdm/MdmDimension.md)           | `getMappedDimension``()`<br>Gets the `MdmDimension` associated with the `CubeDimensionalityMap`.                                                                     |
    | [`Expression`](../../syntax/Expression.md)         | `getPartitionJoinExpression``()`                                                                                                                                     |
    | `void`                                             | `setDimensionality``(`[`MdmDimensionality`](../mdm/MdmDimensionality.md)` input)`<br>Specifies an `MdmDimensionality` to associate with the `CubeDimensionalityMap`. |
    | `void`                                             | `setJoinCondition``(`[`Condition`](../../syntax/Condition.md)` joinCondition)`<br>Specifies a `Condition` as the join condition for the dimension in the cube.       |
    | `void`                                             | `setMappedDimension``(`[`MdmDimension`](../mdm/MdmDimension.md)` mappedDim)`<br>Specifies the `MdmDimension` to associate with the cube.                             |
    | `void`                                             | `setPartitionJoinExpression``(`[`Expression`](../../syntax/Expression.md)` exp)`                                                                                     |

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[ValueMap](ValueMap.md)

      [`getExpression`](ValueMap.md)`, `[`getName`](ValueMap.md)`, `[`setExpression`](ValueMap.md)`, `[`setName`](ValueMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setDimensionality

          public void setDimensionality(MdmDimensionality input)

      Specifies an `MdmDimensionality` to associate with the `CubeDimensionalityMap`.
      Parameters:
      `input` - The `MdmDimensionality` to associate with the `CubeDimensionalityMap`.

    <!-- -->

    - #### getDimensionality

          public MdmDimensionality getDimensionality()

      Gets the `MdmDimensionality` associated with the `CubeDimensionalityMap`.
      Returns:
      The `MdmDimensionality` associated with the `CubeDimensionalityMap`.

    <!-- -->

    - #### getJoinCondition

          public Condition getJoinCondition()

      Gets the `Condition` that represents the join condition for the dimension in the cube.
      Returns:
      The `Condition` that is the join condition for the `CubeDimensionalityMap`.

    <!-- -->

    - #### setJoinCondition

          public void setJoinCondition(Condition joinCondition)

      Specifies a `Condition` as the join condition for the dimension in the cube.
      Parameters:
      `joinCondition` - A `Condition` to be the join condition for the `CubeDimensionalityMap`.

    <!-- -->

    - #### getMappedDimension

          public MdmDimension getMappedDimension()

      Gets the `MdmDimension` associated with the `CubeDimensionalityMap`.
      Returns:
      The `MdmDimension` associated with the `CubeDimensionalityMap`.

    <!-- -->

    - #### setMappedDimension

          public void setMappedDimension(MdmDimension mappedDim)

      Specifies the `MdmDimension` to associate with the cube.
      Parameters:
      `mappedDim` - The `MdmDimension` to associate with the cube.

    <!-- -->

    - #### getCubeMap

          public final CubeMap getCubeMap()

      Gets the `CubeMap` that is the owner of this `CubeDimensionalityMap`.
      Returns:
      The `CubeMap` that owns this `CubeDimensionalityMap`.

    <!-- -->

    - #### getPartitionJoinExpression

          public Expression getPartitionJoinExpression()

    <!-- -->

    - #### setPartitionJoinExpression

          public void setPartitionJoinExpression(Expression exp)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AttributeMap.md)
- [Next Class](CubeMap.md)

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
