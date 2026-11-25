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

- Prev Class
- [Next Class](AbstractSpatialIndex.md)

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

oracle.spatial.network.nfe.vis.maps.index

## Class AbstractIndexedDataSet

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.index.AbstractIndexedDataSet

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class AbstractIndexedDataSet
      extends java.lang.Object

  An indexed dataset that is associated to a data layer

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `AbstractIndexedDataSet``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                               |
    |-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                       | `addFeature``(`[`AbstractFeature`](../geoobject/AbstractFeature.md)` feature)`<br>Adds a new feature to index data set.                                                              |
    | `boolean`                                                       | `appendFeature``(`[`AbstractFeature`](../geoobject/AbstractFeature.md)` feature)`<br>Appends a feature to index data set.                                                            |
    | [`AbstractFeature`](../geoobject/AbstractFeature.md)            | `getAbstractFeature``(java.lang.String featKey)`<br>Returns the feature associated to the given key Returns the abstract feature                                                     |
    | `AbstractDataSet`                                               | `getDataSet``()`                                                                                                                                                                     |
    | [`AbstractDataSetLayer`](../layer/AbstractDataSetLayer.md)      | `getDataSetLayer``()`<br>Returns the layer owning this object                                                                                                                        |
    | `java.util.Set<`[`GeoObject`](../core/GeoObject.md)`>`          | `getFeatures``(java.awt.geom.Area area)`<br>Returns all the features that interact with the given area                                                                               |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`         | `getFeatures``(java.awt.geom.Point2D point, double tolerance)`<br>Returns all the features interacting with the given point used the specified tolerance as buffer around the point  |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`         | `getFeatures``(java.awt.geom.Rectangle2D mbr)`<br>Returns all the features that interact with the given MBR                                                                          |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`         | `getFeaturesByAttribute``(java.awt.geom.Rectangle2D mbr, Field attribute)`<br>Returns the feature that interact with input mbr and have an attribute value equal to input attribute. |
    | [`AbstractSpatialIndex`](AbstractSpatialIndex.md)               | `getSpatialindex``()`                                                                                                                                                                |
    | `abstract `[`AbstractFeature`](../geoobject/AbstractFeature.md) | `identify``(java.awt.geom.Point2D point, double tolerance, int granularity)`<br>Returns a feature that is located at the given point using the specified tolerance                   |
    | `void`                                                          | `redo``(EditChangeEvent change)`<br>Restores the last edit operation.                                                                                                                |
    | `boolean`                                                       | `removeFeature``(`[`AbstractFeature`](../geoobject/AbstractFeature.md)` feature)`<br>Removes feature from index data set.                                                            |
    | `void`                                                          | `setDataSetLayer``(`[`AbstractDataSetLayer`](../layer/AbstractDataSetLayer.md)` dataSetLayer)`                                                                                       |
    | `void`                                                          | `setSpatialIndex``(`[`AbstractSpatialIndex`](AbstractSpatialIndex.md)` index)`                                                                                                       |
    | `void`                                                          | `undo``(EditChangeEvent change)`<br>Removes the last edit operation.                                                                                                                 |
    | `boolean`                                                       | `updateSpatialAttribute``(java.lang.Object key, java.lang.Object spatialChange)`<br>Updates feature of index data set.                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AbstractIndexedDataSet

          public AbstractIndexedDataSet()

  <!-- -->

  - ### Method Detail

    - #### getDataSet

          public AbstractDataSet getDataSet()

      Returns:

    <!-- -->

    - #### getSpatialindex

          public AbstractSpatialIndex getSpatialindex()

      Returns:

    <!-- -->

    - #### setSpatialIndex

          public void setSpatialIndex(AbstractSpatialIndex index)

      Parameters:
      `index` -

    <!-- -->

    - #### addFeature

          public boolean addFeature(AbstractFeature feature)
                             throws java.lang.Exception

      Adds a new feature to index data set. Data set must be read-write mode. Data set change manager records change.
      Parameters:
      `feature` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### appendFeature

          public boolean appendFeature(AbstractFeature feature)
                                throws java.lang.Exception

      Appends a feature to index data set. Data set change manager does not record change. Use this method if you want to extend the feature list, but do not want to record it as a data set change.
      Parameters:
      `feature` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### removeFeature

          public boolean removeFeature(AbstractFeature feature)
                                throws java.lang.Exception

      Removes feature from index data set. Data set must be read-write mode. Data set change manager records change.
      Parameters:
      `feature` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### updateSpatialAttribute

          public boolean updateSpatialAttribute(java.lang.Object key,
                                                java.lang.Object spatialChange)
                                         throws java.lang.Exception

      Updates feature of index data set. Data set must be read-write mode. Data set change manager records change.
      Parameters:
      `key` -

      `spatialChange` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getFeatures

          public java.util.List<GeoObject> getFeatures(java.awt.geom.Point2D point,
                                                       double tolerance)

      Returns all the features interacting with the given point used the specified tolerance as buffer around the point
      Parameters:
      `point` -

      `tolerance` -

      Returns:
      a list of interacting features

    <!-- -->

    - #### getFeatures

          public java.util.List<GeoObject> getFeatures(java.awt.geom.Rectangle2D mbr)

      Returns all the features that interact with the given MBR
      Parameters:
      `mbr` -

      Returns:
      a list of interacting features

    <!-- -->

    - #### getFeatures

          public java.util.Set<GeoObject> getFeatures(java.awt.geom.Area area)

      Returns all the features that interact with the given area
      Parameters:
      `area` -

      Returns:
      a set of interacting features

    <!-- -->

    - #### getAbstractFeature

          public AbstractFeature getAbstractFeature(java.lang.String featKey)

      Returns the feature associated to the given key Returns the abstract feature
      Parameters:

      `featKey` - a feature or null if the feature was not found for the key

      Returns:

    <!-- -->

    - #### undo

          public void undo(EditChangeEvent change)
                    throws java.lang.Exception

      Removes the last edit operation.
      Parameters:
      `change` -

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### redo

          public void redo(EditChangeEvent change)
                    throws java.lang.Exception

      Restores the last edit operation.
      Parameters:
      `change` -

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### identify

          public abstract AbstractFeature identify(java.awt.geom.Point2D point,
                                                   double tolerance,
                                                   int granularity)

      Returns a feature that is located at the given point using the specified tolerance
      Parameters:
      `point` -

      `tolerance` -

      `granularity` -

      Returns:
      a feature or null if no point is located at the given point

    <!-- -->

    - #### setDataSetLayer

          public void setDataSetLayer(AbstractDataSetLayer dataSetLayer)

    <!-- -->

    - #### getDataSetLayer

          public AbstractDataSetLayer getDataSetLayer()

      Returns the layer owning this object
      Returns:

    <!-- -->

    - #### getFeaturesByAttribute

          public java.util.List<GeoObject> getFeaturesByAttribute(java.awt.geom.Rectangle2D mbr,
                                                                  Field attribute)

      Returns the feature that interact with input mbr and have an attribute value equal to input attribute.
      Parameters:

      `mbr` -

      `attribute` - should of same type as feature attribute.

      Returns:

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

- Prev Class
- [Next Class](AbstractSpatialIndex.md)

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
