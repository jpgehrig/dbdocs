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

- [Prev Class](HierarchyLevelMap.md)
- [Next Class](MemberListMap.md)

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

## Class MeasureMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.ValueMap](ValueMap.md)

        - - oracle.olapi.metadata.mapping.MeasureMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MeasureMap
      extends ValueMap

  A `ValueMap` that maps an `MdmMeasure` to an `Expression`. You get an `MeasureMap` by calling the `findOrCreateMeasureMap` method of a `CubeMap`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                 |
    |----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | [`CubeMap`](CubeMap.md)                      | `getCubeMap``()`<br>Gets the `CubeMap` that is the owner of this `MeasureMap`.                                                         |
    | [`MdmBaseMeasure`](../mdm/MdmBaseMeasure.md) | `getMeasure``()`<br>Gets the `MdmBaseMeasure` associated with the `MeasureMap`.                                                        |
    | `void`                                       | `setMeasure``(`[`MdmBaseMeasure`](../mdm/MdmBaseMeasure.md)` input)`<br>Specifies the `MdmMeasure` to associate with the `MeasureMap`. |

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

    - #### setMeasure

          public void setMeasure(MdmBaseMeasure input)

      Specifies the `MdmMeasure` to associate with the `MeasureMap`.
      Parameters:
      `input` - The `MdmMeasure` to associate with the `MeasureMap`.

    <!-- -->

    - #### getMeasure

          public MdmBaseMeasure getMeasure()

      Gets the `MdmBaseMeasure` associated with the `MeasureMap`.
      Returns:
      The `MdmBaseMeasure` associated with the `MeasureMap`.

    <!-- -->

    - #### getCubeMap

          public CubeMap getCubeMap()

      Gets the `CubeMap` that is the owner of this `MeasureMap`.
      Returns:
      The `CubeMap` that owns this `MeasureMap`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](HierarchyLevelMap.md)
- [Next Class](MemberListMap.md)

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
