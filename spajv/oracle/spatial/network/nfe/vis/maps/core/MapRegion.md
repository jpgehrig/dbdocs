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

- [Prev Class](MapCanvas.md)
- [Next Class](MapRegionEvent.md)

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

## Class MapRegion

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.MapRegion

<!-- -->

-

  ------------------------------------------------------------------------



      public class MapRegion
      extends java.lang.Object

  MapRegion defines the current map display region, including the image (device) area and the data window. The device window is expressed in pixel, while the data window is expressed in the native (geographic) coordinate system of the data. It provides various convenience methods for zoom/pan operations. An affine viewport transformation is also maintained by this class to reflect the current map display characteristics.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                          |
    |------------------------------------------------------|
    | `MapRegion``(`[`MapCanvas`](MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                                                                      |
    |---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                          | `addChangeListener``(javax.swing.event.ChangeListener l)`<br>Adds a change listener to listen for queryWindow changes.                                                                                                                                                      |
    | `double`                        | `getCurrentRatioScale``()`<br>Returns the current ratio scale.                                                                                                                                                                                                              |
    | `java.awt.geom.Rectangle2D`     | `getDataWindow``()`<br>Gets the data window rectangle                                                                                                                                                                                                                       |
    | `int`                           | `getDataWindowSrid``()`<br>Gets the data window SRID                                                                                                                                                                                                                        |
    | `double`                        | `getMapScale``()`<br>Gets the current map scale denominator in the ratio scale.                                                                                                                                                                                             |
    | `int`                           | `getMapSrid``()`<br>Gets the current map SRID                                                                                                                                                                                                                               |
    | `SRS`                           | `getSRS``()`<br>Returns the map region SRS object.                                                                                                                                                                                                                          |
    | `java.awt.geom.AffineTransform` | `getTransformDifference``(java.awt.geom.AffineTransform oldXFM)`                                                                                                                                                                                                            |
    | `int`                           | `getUserSrid``()`                                                                                                                                                                                                                                                           |
    | `java.awt.geom.AffineTransform` | `getViewportTransform``()`                                                                                                                                                                                                                                                  |
    | `void`                          | `pan``(int tx, int ty)`<br>Moves the map display by 'tx' pixels on the X axis, and 'ty' pixels on the Y axis in the device coordinate system.                                                                                                                               |
    | `void`                          | `removeChangeListener``(javax.swing.event.ChangeListener l)`<br>Removes the give change listener                                                                                                                                                                            |
    | `void`                          | `setDataWindow``(java.awt.geom.Rectangle2D dataWindow)`<br>Sets the data window rectangle                                                                                                                                                                                   |
    | `void`                          | `setDataWindow``(java.awt.geom.Rectangle2D dataWindow, int zoomLevelDif)`<br>Sets the data window rectangle and zoom level                                                                                                                                                  |
    | `void`                          | `setDataWindowByScale``(double centerX, double centerY, double scale)`<br>Sets the data window size using the given scale                                                                                                                                                   |
    | `void`                          | `setDataWindowSrid``(int dataWindowSrid)`<br>Sets the data window srid                                                                                                                                                                                                      |
    | `void`                          | `setMapSrid``(int mapSrid)`<br>Sets the current map SRID                                                                                                                                                                                                                    |
    | `void`                          | `setSRS``(SRS srs)`<br>Sets the map region SRS information.                                                                                                                                                                                                                 |
    | `void`                          | `setUserSrid``(int userSrid)`<br>Sometimes when a map is displayed in a projected coordinate system, the coordinates do not make much sense to a user, who expects to see coordinates such as those displayed when moving mouse around the map to be in longitude/latitude. |
    | `void`                          | `zoom``(java.awt.geom.Point2D deviceAnchor, double factor, int level)`                                                                                                                                                                                                      |
    | `void`                          | `zoomBox``(java.awt.geom.Rectangle2D window)`<br>Zooms to the provided box                                                                                                                                                                                                  |
    | `void`                          | `zoomIn``()`<br>Performs a zoom in                                                                                                                                                                                                                                          |
    | `void`                          | `zoomIn``(java.awt.geom.Point2D deviceAnchor)`<br>Performs a zoom in at the given point                                                                                                                                                                                     |
    | `void`                          | `zoomOut``()`<br>Performs a zoom out                                                                                                                                                                                                                                        |
    | `void`                          | `zoomOut``(java.awt.geom.Point2D deviceAnchor)`<br>Performs a zoom out at the given pont                                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MapRegion

          public MapRegion(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### setDataWindowByScale

          public void setDataWindowByScale(double centerX,
                                           double centerY,
                                           double scale)
                                    throws java.lang.Exception

      Sets the data window size using the given scale
      Parameters:
      `centerX` -

      `centerY` -

      `scale` -

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMapSrid

          public int getMapSrid()

      Gets the current map SRID
      Returns:

    <!-- -->

    - #### setMapSrid

          public void setMapSrid(int mapSrid)

      Sets the current map SRID
      Parameters:
      `mapSrid` -

    <!-- -->

    - #### getDataWindow

          public java.awt.geom.Rectangle2D getDataWindow()

      Gets the data window rectangle
      Returns:

    <!-- -->

    - #### setDataWindow

          public void setDataWindow(java.awt.geom.Rectangle2D dataWindow)

      Sets the data window rectangle
      Parameters:
      `dataWindow` -

    <!-- -->

    - #### setDataWindow

          public void setDataWindow(java.awt.geom.Rectangle2D dataWindow,
                                    int zoomLevelDif)

      Sets the data window rectangle and zoom level
      Parameters:
      `dataWindow` -

      `zoomLevelDif` -

    <!-- -->

    - #### getDataWindowSrid

          public int getDataWindowSrid()

      Gets the data window SRID
      Returns:

    <!-- -->

    - #### setDataWindowSrid

          public void setDataWindowSrid(int dataWindowSrid)

      Sets the data window srid
      Parameters:
      `dataWindowSrid` -

    <!-- -->

    - #### getMapScale

          public double getMapScale()

      Gets the current map scale denominator in the ratio scale.
      Returns:

    <!-- -->

    - #### getViewportTransform

          public java.awt.geom.AffineTransform getViewportTransform()

    <!-- -->

    - #### getTransformDifference

          public java.awt.geom.AffineTransform getTransformDifference(java.awt.geom.AffineTransform oldXFM)

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener l)

      Adds a change listener to listen for queryWindow changes.
      Parameters:
      `l` -

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener l)

      Removes the give change listener
      Parameters:
      `l` -

    <!-- -->

    - #### zoomBox

          public void zoomBox(java.awt.geom.Rectangle2D window)

      Zooms to the provided box
      Parameters:
      `window` -

    <!-- -->

    - #### zoomIn

          public void zoomIn()

      Performs a zoom in

    <!-- -->

    - #### zoomIn

          public void zoomIn(java.awt.geom.Point2D deviceAnchor)

      Performs a zoom in at the given point
      Parameters:
      `deviceAnchor` -

    <!-- -->

    - #### zoomOut

          public void zoomOut()

      Performs a zoom out

    <!-- -->

    - #### zoomOut

          public void zoomOut(java.awt.geom.Point2D deviceAnchor)

      Performs a zoom out at the given pont
      Parameters:
      `deviceAnchor` -

    <!-- -->

    - #### zoom

          public void zoom(java.awt.geom.Point2D deviceAnchor,
                           double factor,
                           int level)

    <!-- -->

    - #### pan

          public void pan(int tx,
                          int ty)

      Moves the map display by 'tx' pixels on the X axis, and 'ty' pixels on the Y axis in the device coordinate system.
      Parameters:
      `tx` - the distance by which coordinates are translated in the X axis direction

      `ty` - the distance by which coordinates are translated in the Y axis direction

    <!-- -->

    - #### setSRS

          public void setSRS(SRS srs)

      Sets the map region SRS information.
      Parameters:
      `srs` -

    <!-- -->

    - #### getSRS

          public SRS getSRS()

      Returns the map region SRS object.
      Returns:

    <!-- -->

    - #### getCurrentRatioScale

          public double getCurrentRatioScale()

      Returns the current ratio scale. Map region SRS must be defined.
      Returns:
      ratio scale value of Double.NaN if can not be computed

    <!-- -->

    - #### getUserSrid

          public int getUserSrid()

    <!-- -->

    - #### setUserSrid

          public void setUserSrid(int userSrid)

      Sometimes when a map is displayed in a projected coordinate system, the coordinates do not make much sense to a user, who expects to see coordinates such as those displayed when moving mouse around the map to be in longitude/latitude. In such cases, the user SRID can be set to 8307, which is purely for end user convenience.

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

- [Prev Class](MapCanvas.md)
- [Next Class](MapRegionEvent.md)

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
