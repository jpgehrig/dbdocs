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

- [Prev Class](IntersectionLocation.md)
- [Next Class](LineIntersectionList.md)

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

## Class IntersectionMember\<V\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.interaction.IntersectionMember\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of the intersection member

  <!-- -->

  All Implemented Interfaces:
  java.lang.Cloneable

  <!-- -->

  Direct Known Subclasses:
  [LineIntersectionMember](LineIntersectionMember.md), [PointIntersectionMember](PointIntersectionMember.md)

  ------------------------------------------------------------------------



      public abstract class IntersectionMember<V>
      extends java.lang.Object
      implements java.lang.Cloneable

  Holds the information of an element participating in an intersection interaction along with the information of how the element is intersected.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------|
    | `IntersectionMember``(V element, `[`JGeometry`](../../../../../geometry/JGeometry.md)` geometry)`<br>Allocates a new intersection member |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                        |
    |-----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                  | `clone``()`                                                                                                                                                                   |
    | `double`                                            | `getDistToInterCommonPoint``()`<br>Gets the distance from the element's intersected point to the point considered as the origin of the intersection                           |
    | `V`                                                 | `getElement``()`<br>Gets the intersection's element                                                                                                                           |
    | [`JGeometry`](../../../../../geometry/JGeometry.md) | `getGeometry``()`<br>Gets the geometry of the intersection's element                                                                                                          |
    | `long`                                              | `getId``()`<br>Gets the member's id                                                                                                                                           |
    | [`IntersectionLocation`](IntersectionLocation.md)   | `getIntersectionLocation``()`<br>Gets the element's location where the intersection takes place                                                                               |
    | `abstract java.awt.geom.Point2D`                    | `getIntersectionPoint``()`<br>Gets the spatial point where the element is intersected.                                                                                        |
    | `abstract boolean`                                  | `isLine``()`<br>Tells whether the element held is a line                                                                                                                      |
    | `abstract boolean`                                  | `isPoint``()`<br>Tells whether the element held is a point                                                                                                                    |
    | `void`                                              | `setDistToInterCommonPoint``(double distToComInterPoint)`<br>Sets the distance from the element's intersected point to the point considered as the origin of the intersection |
    | `void`                                              | `setElement``(V element)`<br>Sets the intersection's element                                                                                                                  |
    | `void`                                              | `setGeometry``(`[`JGeometry`](../../../../../geometry/JGeometry.md)` geometry)`<br>Sets the geometry of the intersection's element                                            |
    | `void`                                              | `setIntersectionLocation``(`[`IntersectionLocation`](IntersectionLocation.md)` intersectionLocation)`<br>Sets the element's location where the intersection takes place       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### IntersectionMember

          public IntersectionMember(V element,
                                    JGeometry geometry)

      Allocates a new intersection member
      Parameters:
      `element` - the element participating in the intersection

      `geometry` - the element's geometry

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Gets the member's id
      Returns:
      the member's id

    <!-- -->

    - #### getElement

          public V getElement()

      Gets the intersection's element
      Returns:
      the intersection's element

    <!-- -->

    - #### setElement

          public void setElement(V element)

      Sets the intersection's element
      Parameters:
      `element` - the intersection's element

    <!-- -->

    - #### getGeometry

          public JGeometry getGeometry()

      Gets the geometry of the intersection's element
      Returns:
      the geometry of the intersection's element

    <!-- -->

    - #### setGeometry

          public void setGeometry(JGeometry geometry)

      Sets the geometry of the intersection's element
      Parameters:
      `geometry` - the geometry of the intersection's element

    <!-- -->

    - #### getIntersectionLocation

          public IntersectionLocation getIntersectionLocation()

      Gets the element's location where the intersection takes place
      Returns:
      an intersection location type

    <!-- -->

    - #### setIntersectionLocation

          public void setIntersectionLocation(IntersectionLocation intersectionLocation)

      Sets the element's location where the intersection takes place
      Parameters:
      `intersectionLocation` - an intersection location type

    <!-- -->

    - #### getDistToInterCommonPoint

          public double getDistToInterCommonPoint()

      Gets the distance from the element's intersected point to the point considered as the origin of the intersection
      Returns:
      the distance to the intersection common point

    <!-- -->

    - #### setDistToInterCommonPoint

          public void setDistToInterCommonPoint(double distToComInterPoint)

      Sets the distance from the element's intersected point to the point considered as the origin of the intersection
      Parameters:
      `distToComInterPoint` - the distance to the intersection's common point

    <!-- -->

    - #### isLine

          public abstract boolean isLine()

      Tells whether the element held is a line
      Returns:
      true if the element is a line

    <!-- -->

    - #### isPoint

          public abstract boolean isPoint()

      Tells whether the element held is a point
      Returns:
      true if the element is a point

    <!-- -->

    - #### getIntersectionPoint

          public abstract java.awt.geom.Point2D getIntersectionPoint()

      Gets the spatial point where the element is intersected.
      Returns:
      a java point

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](IntersectionLocation.md)
- [Next Class](LineIntersectionList.md)

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
