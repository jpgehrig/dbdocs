Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFERTreeSpatialModel.md)
- [Next Class](RTreeIndexedSpatialSet.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial

## Interface NFESpatialModel

- All Known Implementing Classes:
  [NFERTreeSpatialModel](NFERTreeSpatialModel.md)

  ------------------------------------------------------------------------



      public interface NFESpatialModel

  An NFE component that maintains spatial indexes for all the elements with geometry contained in an NFE model.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                | Method and Description                                                                                                                                                                 |
    |----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                        | `addNetworkElementIndex``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` netElem)`<br>Spatially-indexes a network element                                                    |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Area area)`<br>Gets all the feature elements interacting with the given area.                                                                      |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Area area, long featLayerId)`<br>Gets all the feature elements interacting with the given area.                                                    |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Point2D point, double tolerance)`<br>Gets all the feature elements interacting with the given point.                                               |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Point2D point, double tolerance, long featLayerId)`<br>Gets all the feature elements interacting with the given point.                             |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Rectangle2D rect)`<br>Gets all the feature elements interacting with the given rectangle.                                                          |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getFeatureElements``(java.awt.geom.Rectangle2D rect, long featLayerId)`<br>Gets all the feature elements interacting with the given rectangle.                                        |
    | `java.util.Collection<`[`NFENetworkElement`](../network/NFENetworkElement.md)`>` | `getNetworkElements``(java.awt.geom.Area area)`<br>Gets all the network elements interacting with the given area.                                                                      |
    | `java.util.Collection<`[`NFENetworkElement`](../network/NFENetworkElement.md)`>` | `getNetworkElements``(java.awt.geom.Point2D point, double tolerance)`<br>Gets all the network elements interacting with the given point.                                               |
    | `java.util.Collection<`[`NFENetworkElement`](../network/NFENetworkElement.md)`>` | `getNetworkElements``(java.awt.geom.Rectangle2D rect)`<br>Gets all the network elements interacting with the given rectangle.                                                          |
    | `boolean`                                                                        | `refreshNetworkElementIndex``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` netElem)`<br>Refreshes the spatial index of the network element to reflect its actual geometry. |
    | `boolean`                                                                        | `removeNetworkElementIndex``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` netElem)`<br>Removes the index for the network element                                           |

<!-- -->

- - ### Method Detail

    - #### addNetworkElementIndex

          boolean addNetworkElementIndex(NFENetworkElement netElem)

      Spatially-indexes a network element
      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the element could be indexed

    <!-- -->

    - #### refreshNetworkElementIndex

          boolean refreshNetworkElementIndex(NFENetworkElement netElem)

      Refreshes the spatial index of the network element to reflect its actual geometry. It should be called whenever the element's geometry changes.
      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the index could be refreshed.

    <!-- -->

    - #### removeNetworkElementIndex

          boolean removeNetworkElementIndex(NFENetworkElement netElem)

      Removes the index for the network element
      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the index was removed.

    <!-- -->

    - #### getNetworkElements

          java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Point2D point,
                                                                     double tolerance)

      Gets all the network elements interacting with the given point.
      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      Returns:
      a collection containing all the network elements interacting with the point

    <!-- -->

    - #### getNetworkElements

          java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Rectangle2D rect)

      Gets all the network elements interacting with the given rectangle.
      Parameters:
      `rect` - a rectangle in model's coordinate system

      Returns:
      a collection containing all the network elements interacting with the rectangle

    <!-- -->

    - #### getNetworkElements

          java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Area area)

      Gets all the network elements interacting with the given area.
      Parameters:
      `area` - an area in model's coordinate system

      Returns:
      a collection containing all the network elements interacting with the area

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Point2D point,
                                                                     double tolerance)

      Gets all the feature elements interacting with the given point.
      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      Returns:
      a collection containing all the feature elements interacting with the point

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Rectangle2D rect)

      Gets all the feature elements interacting with the given rectangle.
      Parameters:
      `rect` - a rectangle in model's coordinate system

      Returns:
      a collection containing all the feature elements interacting with the rectangle

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Area area)

      Gets all the feature elements interacting with the given area.
      Parameters:
      `area` - an area in model's coordinate system

      Returns:
      a collection containing all the feature elements interacting with the area

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Point2D point,
                                                                     double tolerance,
                                                                     long featLayerId)

      Gets all the feature elements interacting with the given point. Only the elements that belong to the given feature layer are retrieved.
      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      `featLayerId` - only feature elements from this feature layer are returned.

      Returns:
      a collection containing all the feature elements interacting with the point

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Rectangle2D rect,
                                                                     long featLayerId)

      Gets all the feature elements interacting with the given rectangle. Only the elements that belong to the given feature layer are retrieved.
      Parameters:
      `rect` - a rectangle in model's coordinate system

      `featLayerId` - only feature elements from this feature layer are returned.

      Returns:
      a collection containing all the feature elements interacting with the rectangle

    <!-- -->

    - #### getFeatureElements

          java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Area area,
                                                                     long featLayerId)

      Gets all the feature elements interacting with the given area. Only the elements that belong to the given feature layer are retrieved.
      Parameters:
      `area` - an area in model's coordinate system

      `featLayerId` - only feature elements from this feature layer are returned.

      Returns:
      a collection containing all the feature elements interacting with the area

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFERTreeSpatialModel.md)
- [Next Class](RTreeIndexedSpatialSet.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
