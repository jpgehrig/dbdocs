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

- [Prev Class](LineIntersectionList.md)
- [Next Class](NFEInteractionEngine.md)

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

## Class LineIntersectionMember\<V\>

- java.lang.Object

- - [oracle.spatial.network.nfe.model.spatial.interaction.IntersectionMember](IntersectionMember.md)\<V\>

  - - oracle.spatial.network.nfe.model.spatial.interaction.LineIntersectionMember\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of intersection member

  <!-- -->

  All Implemented Interfaces:
  java.lang.Cloneable

  ------------------------------------------------------------------------



      public class LineIntersectionMember<V>
      extends IntersectionMember<V>

  An intersection member which geometry is a line

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LineIntersectionMember``(V element, `[`JGeometry`](../../../../../geometry/JGeometry.md)` line)`                                                                                             |
    | `LineIntersectionMember``(V element, `[`JGeometry`](../../../../../geometry/JGeometry.md)` line, JGeometrySegmentPoint intersectionSegmentPoint)`<br>Allocates a new line intersection member |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                |
    |------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                         | `clone``()`                                                                                                                                                                                           |
    | `static `[`IntersectionLocation`](IntersectionLocation.md) | `getIntersectionLocaction``(`[`JGeometry`](../../../../../geometry/JGeometry.md)` line, JGeometrySegmentPoint segmentPoint)`<br>Gets a line's intersection location based on the line's segment point |
    | `java.awt.geom.Point2D`                                    | `getIntersectionPoint``()`<br>Gets the spatial point where the element is intersected.                                                                                                                |
    | `JGeometrySegmentPoint`                                    | `getIntersectionSegmentPoint``()`<br>Gets the line's segment point where the intersection is taking place                                                                                             |
    | `boolean`                                                  | `isLine``()`<br>Tells whether the element held is a line                                                                                                                                              |
    | `boolean`                                                  | `isPoint``()`<br>Tells whether the element held is a point                                                                                                                                            |
    | `void`                                                     | `setIntersectionSegmentPoint``(JGeometrySegmentPoint segmentPoint)`<br>Sets the line's segment point where the intersection is taking place                                                           |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.spatial.interaction.[IntersectionMember](IntersectionMember.md)

      [`getDistToInterCommonPoint`](IntersectionMember.md)`, `[`getElement`](IntersectionMember.md)`, `[`getGeometry`](IntersectionMember.md)`, `[`getId`](IntersectionMember.md)`, `[`getIntersectionLocation`](IntersectionMember.md)`, `[`setDistToInterCommonPoint`](IntersectionMember.md)`, `[`setElement`](IntersectionMember.md)`, `[`setGeometry`](IntersectionMember.md)`, `[`setIntersectionLocation`](IntersectionMember.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LineIntersectionMember

          public LineIntersectionMember(V element,
                                        JGeometry line,
                                        JGeometrySegmentPoint intersectionSegmentPoint)

      Allocates a new line intersection member
      Parameters:
      `element` - the intersection's element

      `line` - the element's line

      `intersectionSegmentPoint` - the line's segment point where the intersection is taking place

    <!-- -->

    - #### LineIntersectionMember

          public LineIntersectionMember(V element,
                                        JGeometry line)

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

    - #### getIntersectionSegmentPoint

          public JGeometrySegmentPoint getIntersectionSegmentPoint()

      Gets the line's segment point where the intersection is taking place
      Returns:
      a line's segment point

    <!-- -->

    - #### setIntersectionSegmentPoint

          public void setIntersectionSegmentPoint(JGeometrySegmentPoint segmentPoint)

      Sets the line's segment point where the intersection is taking place
      Parameters:
      `segmentPoint` - a line's segment point

    <!-- -->

    - #### getIntersectionLocaction

          public static IntersectionLocation getIntersectionLocaction(JGeometry line,
                                                                      JGeometrySegmentPoint segmentPoint)

      Gets a line's intersection location based on the line's segment point
      Parameters:
      `line` - a line geometry

      `segmentPoint` - the line's segment point

      Returns:
      an intersection location for the line

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

- [Prev Class](LineIntersectionList.md)
- [Next Class](NFEInteractionEngine.md)

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
