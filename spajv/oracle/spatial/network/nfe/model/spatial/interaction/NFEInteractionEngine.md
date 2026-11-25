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

- [Prev Class](LineIntersectionMember.md)
- [Next Class](PointIntersectionMember.md)

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

## Class NFEInteractionEngine

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.interaction.NFEInteractionEngine

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEInteractionEngine
      extends java.lang.Object

  NFE component used to detect interaction between elements such as network or feature elements

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                    |
    |----------------------------------------------------------------------------------------------------------------|
    | `NFEInteractionEngine``(`[`NFEModel`](../../NFEModel.md)` model)`<br>Creates a new interaction engine instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                               |
    |--------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                             | `addConnectableHierarchies``(int[] connHierarchies)`<br>Sets which hierarchy levels allows inter-hierarchy interactions, that is, interactions between members of different hierarchies                                                                                                                                                                                                                              |
    | `void`                                                                                                             | `clearConnectableHierarchies``()`<br>Removes all the hierarchy levels for inter-hierarchy interactions.                                                                                                                                                                                                                                                                                                              |
    | `java.util.List<`[`Intersection`](Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>>` | `findIntersections``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` tgrFeatElem, java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> ignoredFeatElems, double tolerance)`<br>Retrieves all the intersections of the given Feature Element.                                                                                                                                |
    | `java.util.List<`[`Intersection`](Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>>` | `findIntersections``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` tgrFeatElem, `[`JGeometry`](../../../../../geometry/JGeometry.md)` tgrGeom, java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> ignoredFeatElems, double tolerance)`<br>Retrieves all the intersections of the given Feature Element, supposing the given geometry is the feature element's geometry. |
    | `void`                                                                                                             | `removeConnectableHierarchies``(int[] connHierarchies)`<br>Removes hierarchy levels for inter-hierarchy interactions                                                                                                                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEInteractionEngine

          public NFEInteractionEngine(NFEModel model)

      Creates a new interaction engine instance
      Parameters:
      `model` - the current NFE model

  <!-- -->

  - ### Method Detail

    - #### findIntersections

          public java.util.List<Intersection<NFEFeatureElement>> findIntersections(NFEFeatureElement tgrFeatElem,
                                                                                   java.util.Collection<NFEFeatureElement> ignoredFeatElems,
                                                                                   double tolerance)

      Retrieves all the intersections of the given Feature Element. If the passed Feature Element is a point, the resulting list will contain only one intersection of two or more feature elements. If the passed Feature Element is a line, the resulting list will contain all the intersection points sorted from first to end line point.
      Parameters:

      `tgrFeatElem` - The target Feature Element. All the intersections with this Feature Element will be retrieved

      `ignoredFeatElems` - Elements in this list will be ignored when interacting with the main Feature Element

      `tolerance` - tolerance used to determine if two points can be considered the same

      Returns:

    <!-- -->

    - #### findIntersections

          public java.util.List<Intersection<NFEFeatureElement>> findIntersections(NFEFeatureElement tgrFeatElem,
                                                                                   JGeometry tgrGeom,
                                                                                   java.util.Collection<NFEFeatureElement> ignoredFeatElems,
                                                                                   double tolerance)

      Retrieves all the intersections of the given Feature Element, supposing the given geometry is the feature element's geometry. If the passed Feature Element is a point, the resulting list will contain only one intersection of two or more feature elements. If the passed Feature Element is a line, the resulting list will contain all the intersection points sorted from first to end line point.
      Parameters:

      `tgrFeatElem` - The target Feature Element. All the intersections with this Feature Element will be retrieved

      `tgrGeom` - the feature element's geometry. It does not have to be the actual feature element's geometry but it has to be a suitable type for the feature element, that is, a line feature element requires a line geometry and so on.

      `ignoredFeatElems` - Elements in this list will be ignored when interacting with the main Feature Element

      `tolerance` - tolerance used to determine if two points can be considered the same

      Returns:

    <!-- -->

    - #### addConnectableHierarchies

          public void addConnectableHierarchies(int[] connHierarchies)

      Sets which hierarchy levels allows inter-hierarchy interactions, that is, interactions between members of different hierarchies
      Parameters:
      `connHierarchies` - an array of hierarchy levels

    <!-- -->

    - #### removeConnectableHierarchies

          public void removeConnectableHierarchies(int[] connHierarchies)

      Removes hierarchy levels for inter-hierarchy interactions
      Parameters:
      `connHierarchies` - an array of hierarchy levels

    <!-- -->

    - #### clearConnectableHierarchies

          public void clearConnectableHierarchies()

      Removes all the hierarchy levels for inter-hierarchy interactions.

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

- [Prev Class](LineIntersectionMember.md)
- [Next Class](PointIntersectionMember.md)

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
