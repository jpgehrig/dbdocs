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

- [Prev Class](AbstractIndexedDataSet.md)
- [Next Class](RTreeIndex.md)

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

## Class AbstractSpatialIndex

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.index.AbstractSpatialIndex

<!-- -->

- Direct Known Subclasses:
  [RTreeIndex](RTreeIndex.md)

  ------------------------------------------------------------------------



      public abstract class AbstractSpatialIndex
      extends java.lang.Object

  Abstract spatial index class. Can be used to build indexing structures on spatial data sets (composed of abstract features). These index structures can be used in edit applications to handle identify operations and others.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AbstractSpatialIndex``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                 |
    |------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract boolean`                                               | `addEntry``(`[`GeoObject`](../core/GeoObject.md)` feature)`<br>Adds an entry to the index                                                                              |
    | `abstract boolean`                                               | `create``(java.util.Properties props)`<br>Creates the index with the specified properties                                                                              |
    | `abstract boolean`                                               | `create``(java.util.Properties props, java.util.List<`[`GeoObject`](../core/GeoObject.md)`> features)`<br>Creates the index with the input features using their MBR's. |
    | `java.util.Properties`                                           | `getProperties``()`<br>Returns the index properties                                                                                                                    |
    | `abstract boolean`                                               | `removeEntry``(`[`GeoObject`](../core/GeoObject.md)` feature)`<br>Removes an entry from the index                                                                      |
    | `abstract java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `searchEntries``(java.awt.geom.Rectangle2D mbr)`<br>Returns all the entry that interact with the giveb MBR                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AbstractSpatialIndex

          public AbstractSpatialIndex()

  <!-- -->

  - ### Method Detail

    - #### getProperties

          public java.util.Properties getProperties()

      Returns the index properties
      Returns:

    <!-- -->

    - #### create

          public abstract boolean create(java.util.Properties props)

      Creates the index with the specified properties
      Parameters:
      `props` -

      Returns:
      true if the index was successfully created

    <!-- -->

    - #### create

          public abstract boolean create(java.util.Properties props,
                                         java.util.List<GeoObject> features)

      Creates the index with the input features using their MBR's.
      Parameters:
      `props` -

      `features` -

      Returns:
      true if the index was successfully created

    <!-- -->

    - #### addEntry

          public abstract boolean addEntry(GeoObject feature)
                                    throws java.lang.Exception

      Adds an entry to the index
      Parameters:
      `feature` -

      Returns:
      true if the entry was added

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### removeEntry

          public abstract boolean removeEntry(GeoObject feature)
                                       throws java.lang.Exception

      Removes an entry from the index
      Parameters:
      `feature` -

      Returns:
      true if the entry could be removed

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### searchEntries

          public abstract java.util.List<GeoObject> searchEntries(java.awt.geom.Rectangle2D mbr)

      Returns all the entry that interact with the giveb MBR
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

- [Prev Class](AbstractIndexedDataSet.md)
- [Next Class](RTreeIndex.md)

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
