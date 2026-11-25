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

- [Prev Class](Filter.md)
- [Next Class](GeoObject.md)

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

oracle.spatial.network.nfe.vis.maps.core

## Interface GeoDataProducer

- All Superinterfaces:
  [DataProducer](DataProducer.md)

  ------------------------------------------------------------------------



      public interface GeoDataProducer
      extends DataProducer

  A generic spatial data producer that gets data from MDS on demand. You can think of a GeoDataProducer as a data cache for a particular theme or table. It is typically associated with a Layer object. When the viewport changes, the Layer object may ask its GeoDataProducer to load necessary data that fills the new viewport. A GeoDataProducer should always load its data in a separate thread, and update the layer when data loading is done. The producer will produce events on these occasions: - successful completion of data loading for the current request - exception during data loading

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                           |
    |---------------------------------|--------------------------------------------------------------------------------------------------|
    | `void`                          | `abortLoad``()`                                                                                  |
    | `void`                          | `clear``()`<br>Clears all existing data.                                                         |
    | [`GeoObject`](GeoObject.md)`[]` | `getData``()`<br>Gets currently available (already loaded) data.                                 |
    | `java.awt.geom.Rectangle2D`     | `getDataMBR``()`<br>returns the MBR of all the data currently loaded.                            |
    | `int`                           | `getTargetSRID``()`<br>Gets the data SRID.                                                       |
    | `void`                          | `loadData``(java.awt.geom.Area queryArea, int qwSrid)`<br>Loads data for the given query window. |
    | `void`                          | `loadData``(java.awt.geom.Rectangle2D queryWindow, int qwSrid)`                                  |
    | `void`                          | `setTargetSRID``(int srid)`<br>Sets the data SRID.                                               |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[DataProducer](DataProducer.md)

      [`getLayer`](DataProducer.md)`, `[`setLayer`](DataProducer.md)

<!-- -->

- - ### Method Detail

    - #### getData

          GeoObject[] getData()

      Gets currently available (already loaded) data.
      Returns:

    <!-- -->

    - #### clear

          void clear()

      Clears all existing data.

    <!-- -->

    - #### setTargetSRID

          void setTargetSRID(int srid)

      Sets the data SRID. If the source data is not in this SRID, it will be transformed into this SRID.
      Parameters:
      `srid` -

    <!-- -->

    - #### getTargetSRID

          int getTargetSRID()

      Gets the data SRID.

    <!-- -->

    - #### getDataMBR

          java.awt.geom.Rectangle2D getDataMBR()

      returns the MBR of all the data currently loaded.
      Returns:

    <!-- -->

    - #### loadData

          void loadData(java.awt.geom.Area queryArea,
                        int qwSrid)

      Loads data for the given query window. If the query window is null or has an infinite size, then all available data will be loaded from the source.
      Parameters:
      `queryArea` -

      `qwSrid` - the SRID of the query area

    <!-- -->

    - #### loadData

          void loadData(java.awt.geom.Rectangle2D queryWindow,
                        int qwSrid)

    <!-- -->

    - #### abortLoad

          void abortLoad()

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

- [Prev Class](Filter.md)
- [Next Class](GeoObject.md)

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
