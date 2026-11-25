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

- [Prev Class](AbstractSpatialIndex.md)
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

oracle.spatial.network.nfe.vis.maps.index

## Class RTreeIndex

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.index.AbstractSpatialIndex](AbstractSpatialIndex.md)

  - - oracle.spatial.network.nfe.vis.maps.index.RTreeIndex

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class RTreeIndex
      extends AbstractSpatialIndex
      implements java.io.Serializable

  Defines an RTree spatial index for a 2 dimensional space.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                |
    |--------------------------------------------|
    | `RTreeIndex``()`<br>Creates a new instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                        |
    |---------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                               | `addEntry``(`[`GeoObject`](../core/GeoObject.md)` feature)`<br>Adds an entry to the index                                                                                     |
    | `boolean`                                               | `create``(java.util.Properties props)`<br>Creates the Rtree index with the given properties.                                                                                  |
    | `boolean`                                               | `create``(java.util.Properties props, java.util.List<`[`GeoObject`](../core/GeoObject.md)`> features)`<br>Creates the Rtree object with the input features using their MBR's. |
    | [`RTree`](../../../../../util/RTree.md)                 | `getTree``()`<br>Returns the internal Rtree structure                                                                                                                         |
    | `boolean`                                               | `removeEntry``(`[`GeoObject`](../core/GeoObject.md)` feature)`<br>Removes an entry from the index                                                                             |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `searchEntries``(java.awt.geom.Rectangle2D mbr)`<br>Returns all the entry that interact with the giveb MBR                                                                    |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.index.[AbstractSpatialIndex](AbstractSpatialIndex.md)

      [`getProperties`](AbstractSpatialIndex.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RTreeIndex

          public RTreeIndex()

      Creates a new instance

  <!-- -->

  - ### Method Detail

    - #### getTree

          public RTree getTree()

      Returns the internal Rtree structure
      Returns:

    <!-- -->

    - #### create

          public boolean create(java.util.Properties props)

      Creates the Rtree index with the given properties.
      Specified by:
      [`create`](AbstractSpatialIndex.md) in class [`AbstractSpatialIndex`](AbstractSpatialIndex.md)

      Parameters:
      `props` - the tree properties, which are: nodesize: the number of entries per node. Since this is a RAM- resident tree there is no need to match node size with disk pages and node sizes of 5-12 will give best results. Value 8 is used if this property is not defined. minimumFill: the number of entries in a node below which the node is considered underfull and the remaining entries orphaned and reinserted in the tree. If set to 1, there will be no orphaning. Value 1 is used if this property is not defined.

      Returns:
      true if the Rtree could be initialized

    <!-- -->

    - #### create

          public boolean create(java.util.Properties props,
                                java.util.List<GeoObject> features)

      Creates the Rtree object with the input features using their MBR's.
      Specified by:

      [`create`](AbstractSpatialIndex.md) in class [`AbstractSpatialIndex`](AbstractSpatialIndex.md)

      Parameters:

      `props` - the tree properties, which are: nodesize: the number of entries per node. Since this is a RAM- resident tree there is no need to match node size with disk pages and node sizes of 5-12 will give best results. Value 8 is used if this property is not defined. minimumFill: the number of entries in a node below which the node is considered underfull and the remaining entries orphaned and reinserted in the tree. If set to 1, there will be no orphaning. Value 1 is used if this property is not defined.

      `features` -

      Returns:

    <!-- -->

    - #### addEntry

          public boolean addEntry(GeoObject feature)
                           throws java.lang.Exception

      Adds an entry to the index
      Specified by:
      [`addEntry`](AbstractSpatialIndex.md) in class [`AbstractSpatialIndex`](AbstractSpatialIndex.md)

      Parameters:
      `feature` -

      Returns:
      true if the entry could be added

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### removeEntry

          public boolean removeEntry(GeoObject feature)
                              throws java.lang.Exception

      Removes an entry from the index
      Specified by:
      [`removeEntry`](AbstractSpatialIndex.md) in class [`AbstractSpatialIndex`](AbstractSpatialIndex.md)

      Parameters:
      `feature` -

      Returns:
      true if the entry could be removed

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### searchEntries

          public java.util.List<GeoObject> searchEntries(java.awt.geom.Rectangle2D mbr)

      Returns all the entry that interact with the giveb MBR
      Specified by:
      [`searchEntries`](AbstractSpatialIndex.md) in class [`AbstractSpatialIndex`](AbstractSpatialIndex.md)

      Parameters:
      `mbr` -

      Returns:
      a list of geo-objects that interact with the MBR

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

- [Prev Class](AbstractSpatialIndex.md)
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
