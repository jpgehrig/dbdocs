Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JRaster.md)
- [Next Class](ObjectInfo.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.georaster

## Class LayerInfo

- java.lang.Object

- - oracle.spatial.georaster.LayerInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class LayerInfo
      extends java.lang.Object

  LayerInfo is a Java class mapped to the XML element LayerInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                          |
    |-----------------------------------|---------------------------------------------------------------------------------|
    | `java.lang.String`                | `getLayerDimension``()`<br>Returns the layer dimension.                         |
    | [`SubLayerInfo`](SubLayerInfo.md) | `getObjectLayer``()`<br>Returns the object layer.                               |
    | [`SubLayerInfo`](SubLayerInfo.md) | `getSubLayer``(long layer)`<br>Returns a subLayer specified by parameter layer. |
    | `java.util.Vector`                | `getSubLayers``()`<br>Returns subLayers as a vector.                            |
    | [`SubLayerInfo`](SubLayerInfo.md) | `initSubLayer``()`<br>Adds a new subLayer in the current layerInfo.             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getLayerDimension

          public java.lang.String getLayerDimension()

      Returns the layer dimension.
      Returns:
      layer dimension.

    <!-- -->

    - #### getObjectLayer

          public SubLayerInfo getObjectLayer()

      Returns the object layer.
      Returns:
      object layer.

    <!-- -->

    - #### getSubLayers

          public java.util.Vector getSubLayers()

      Returns subLayers as a vector.
      Returns:
      subLayers as a vector.

    <!-- -->

    - #### getSubLayer

          public SubLayerInfo getSubLayer(long layer)

      Returns a subLayer specified by parameter layer.
      Returns:
      subLayer.

    <!-- -->

    - #### initSubLayer

          public SubLayerInfo initSubLayer()

      Adds a new subLayer in the current layerInfo.
      Returns:
      the new subLayer.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JRaster.md)
- [Next Class](ObjectInfo.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
