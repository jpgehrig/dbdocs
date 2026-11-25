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

- [Prev Class](NFENetworkElementGeoObject.md)
- [Next Class](NFESpatialModel.md)

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

## Class NFERTreeSpatialModel

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.NFERTreeSpatialModel

<!-- -->

- All Implemented Interfaces:
  [NFESpatialModel](NFESpatialModel.md)

  ------------------------------------------------------------------------



      public class NFERTreeSpatialModel
      extends java.lang.Object
      implements NFESpatialModel

  An implementation of NFESpatialModel that uses R-tree indices

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------------|
    | `NFERTreeSpatialModel``(`[`NFEModel`](../NFEModel.md)` model)`<br>Allocates a new spatial model associated to the given NFE model |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

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

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFERTreeSpatialModel

          public NFERTreeSpatialModel(NFEModel model)

      Allocates a new spatial model associated to the given NFE model
      Parameters:
      `model` - the current NFE model

  <!-- -->

  - ### Method Detail

    - #### addNetworkElementIndex

          public boolean addNetworkElementIndex(NFENetworkElement netElem)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Spatially-indexes a network element
      Specified by:
      [`addNetworkElementIndex`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the element could be indexed

    <!-- -->

    - #### refreshNetworkElementIndex

          public boolean refreshNetworkElementIndex(NFENetworkElement netElem)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Refreshes the spatial index of the network element to reflect its actual geometry. It should be called whenever the element's geometry changes.
      Specified by:
      [`refreshNetworkElementIndex`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the index could be refreshed.

    <!-- -->

    - #### removeNetworkElementIndex

          public boolean removeNetworkElementIndex(NFENetworkElement netElem)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Removes the index for the network element
      Specified by:
      [`removeNetworkElementIndex`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `netElem` - a network element instance

      Returns:
      true if the index was removed.

    <!-- -->

    - #### getNetworkElements

          public java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Point2D point,
                                                                            double tolerance)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the network elements interacting with the given point.
      Specified by:
      [`getNetworkElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      Returns:
      a collection containing all the network elements interacting with the point

    <!-- -->

    - #### getNetworkElements

          public java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Rectangle2D rect)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the network elements interacting with the given rectangle.
      Specified by:
      [`getNetworkElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `rect` - a rectangle in model's coordinate system

      Returns:
      a collection containing all the network elements interacting with the rectangle

    <!-- -->

    - #### getNetworkElements

          public java.util.Collection<NFENetworkElement> getNetworkElements(java.awt.geom.Area area)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the network elements interacting with the given area.
      Specified by:
      [`getNetworkElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `area` - an area in model's coordinate system

      Returns:
      a collection containing all the network elements interacting with the area

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Point2D point,
                                                                            double tolerance)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given point.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      Returns:
      a collection containing all the feature elements interacting with the point

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Rectangle2D rect)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given rectangle.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `rect` - a rectangle in model's coordinate system

      Returns:
      a collection containing all the feature elements interacting with the rectangle

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Area area)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given area.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `area` - an area in model's coordinate system

      Returns:
      a collection containing all the feature elements interacting with the area

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Point2D point,
                                                                            double tolerance,
                                                                            long featLayerId)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given point. Only the elements that belong to the given feature layer are retrieved.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `point` - a spatial point in moodel's coordinate system

      `tolerance` - the maximum distance an element can be from the target geometry to be considered in the result.

      `featLayerId` - only feature elements from this feature layer are returned.

      Returns:
      a collection containing all the feature elements interacting with the point

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Rectangle2D rect,
                                                                            long featLayerId)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given rectangle. Only the elements that belong to the given feature layer are retrieved.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

      Parameters:
      `rect` - a rectangle in model's coordinate system

      `featLayerId` - only feature elements from this feature layer are returned.

      Returns:
      a collection containing all the feature elements interacting with the rectangle

    <!-- -->

    - #### getFeatureElements

          public java.util.Collection<NFEFeatureElement> getFeatureElements(java.awt.geom.Area area,
                                                                            long featLayerId)

      Description copied from interface: [`NFESpatialModel`](NFESpatialModel.md)
      Gets all the feature elements interacting with the given area. Only the elements that belong to the given feature layer are retrieved.
      Specified by:
      [`getFeatureElements`](NFESpatialModel.md) in interface [`NFESpatialModel`](NFESpatialModel.md)

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

- [Prev Class](NFENetworkElementGeoObject.md)
- [Next Class](NFESpatialModel.md)

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
