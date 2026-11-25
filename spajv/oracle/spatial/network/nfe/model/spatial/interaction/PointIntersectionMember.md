Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEInteractionEngine.md)
- Next Class

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial.interaction

## Class PointIntersectionMember\<V\>

- java.lang.Object

- - [oracle.spatial.network.nfe.model.spatial.interaction.IntersectionMember](IntersectionMember.md)\<V\>

  - - oracle.spatial.network.nfe.model.spatial.interaction.PointIntersectionMember\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of the intersection member

  <!-- -->

  All Implemented Interfaces:
  java.lang.Cloneable

  ------------------------------------------------------------------------



      public class PointIntersectionMember<V>
      extends IntersectionMember<V>

  An intersection member which geometry is a point

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `PointIntersectionMember``(V element, `[`JGeometry`](../../../../../geometry/JGeometry.md)` point)`<br>Allocates a new point intersection member |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                 |
    |-------------------------|----------------------------------------------------------------------------------------|
    | `java.lang.Object`      | `clone``()`                                                                            |
    | `java.awt.geom.Point2D` | `getIntersectionPoint``()`<br>Gets the spatial point where the element is intersected. |
    | `boolean`               | `isLine``()`<br>Tells whether the element held is a line                               |
    | `boolean`               | `isPoint``()`<br>Tells whether the element held is a point                             |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.spatial.interaction.[IntersectionMember](IntersectionMember.md)

      [`getDistToInterCommonPoint`](IntersectionMember.md)`, `[`getElement`](IntersectionMember.md)`, `[`getGeometry`](IntersectionMember.md)`, `[`getId`](IntersectionMember.md)`, `[`getIntersectionLocation`](IntersectionMember.md)`, `[`setDistToInterCommonPoint`](IntersectionMember.md)`, `[`setElement`](IntersectionMember.md)`, `[`setGeometry`](IntersectionMember.md)`, `[`setIntersectionLocation`](IntersectionMember.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PointIntersectionMember

          public PointIntersectionMember(V element,
                                         JGeometry point)

      Allocates a new point intersection member
      Parameters:
      `element` - the intersection's element

      `point` - the element's point geometry

  <!-- -->

  - ### Method Detail

    - #### isLine

          public boolean isLine()

      Description copied from class: [`IntersectionMember`](IntersectionMember.md)
      Tells whether the element held is a line
      Specified by:
      [`isLine`](IntersectionMember.md) in class [`IntersectionMember`](IntersectionMember.md)`<V>`

      Returns:
      true if the element is a line

    <!-- -->

    - #### isPoint

          public boolean isPoint()

      Description copied from class: [`IntersectionMember`](IntersectionMember.md)
      Tells whether the element held is a point
      Specified by:
      [`isPoint`](IntersectionMember.md) in class [`IntersectionMember`](IntersectionMember.md)`<V>`

      Returns:
      true if the element is a point

    <!-- -->

    - #### getIntersectionPoint

          public java.awt.geom.Point2D getIntersectionPoint()

      Description copied from class: [`IntersectionMember`](IntersectionMember.md)
      Gets the spatial point where the element is intersected.
      Specified by:
      [`getIntersectionPoint`](IntersectionMember.md) in class [`IntersectionMember`](IntersectionMember.md)`<V>`

      Returns:
      a java point

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Overrides:
      [`clone`](IntersectionMember.md) in class [`IntersectionMember`](IntersectionMember.md)`<V>`

      Throws:
      `java.lang.CloneNotSupportedException`

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEInteractionEngine.md)
- Next Class

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
