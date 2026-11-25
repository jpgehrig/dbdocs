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

- [Prev Class](AbstractDataSetLayer.md)
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

oracle.spatial.network.nfe.vis.maps.layer

## Class BasicLayer

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.layer.BasicLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../core/Layer.md)

  <!-- -->

  Direct Known Subclasses:
  [AbstractDataSetLayer](AbstractDataSetLayer.md), [BasicTool](../tools/BasicTool.md), [MapNavLayer](ui/MapNavLayer.md), [NFERenderer](../../mapcanvas/render/NFERenderer.md), [PointerLocationLayer](ui/PointerLocationLayer.md), [ProgressIndicatorLayer](ui/ProgressIndicatorLayer.md), [ScaleBarLayer](ui/ScaleBarLayer.md), [SimpleBGLayer](ui/SimpleBGLayer.md)

  ------------------------------------------------------------------------



      public class BasicLayer
      extends java.lang.Object
      implements Layer

  A basic layer that serves as a default implementation of the Layer interface. For simple types of concrete layers, it is easier to extend BasicLayer then override only interface methods that are different from default behavior.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`PROPERTY_NAME`](../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../core/Layer.md)`, `[`PROPERTY_SRID`](../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                   |
    |---------------------------------------------------------------|
    | `BasicLayer``(`[`MapCanvas`](../core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                  |
    |---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                  | `added``(java.lang.Object source)`<br>The function called when the layer is added to either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)          |
    | `void`                                                  | `addPropertyChangeListener``(java.beans.PropertyChangeListener listener)`                                                                                                               |
    | `void`                                                  | `addPropertyChangeListener``(java.lang.String propertyName, java.beans.PropertyChangeListener listener)`                                                                                |
    | `void`                                                  | `clear``()`<br>Clears all contents of this layer.                                                                                                                                       |
    | `void`                                                  | `fromXMLElement``(org.w3c.dom.Element element)`<br>Loads the content from an XML representation                                                                                         |
    | [`MapCanvas`](../core/MapCanvas.md)                     | `getCanvas``()`<br>Gets the map canvas that this layer is displayed on.                                                                                                                 |
    | `java.awt.geom.Rectangle2D`                             | `getDataMBR``()`<br>Always return null here.                                                                                                                                            |
    | `java.awt.geom.Rectangle2D`                             | `getFullExtent``()`                                                                                                                                                                     |
    | `javax.swing.Icon`                                      | `getIcon``()`                                                                                                                                                                           |
    | `java.lang.String`                                      | `getName``()`<br>Gets the name of the layer.                                                                                                                                            |
    | `java.util.Properties`                                  | `getProperties``()`                                                                                                                                                                     |
    | `java.lang.String`                                      | `getProperty``(java.lang.String key)`                                                                                                                                                   |
    | `java.lang.String`                                      | `getProperty``(java.lang.String key, java.lang.String defaultValue)`                                                                                                                    |
    | `java.beans.PropertyChangeListener[]`                   | `getPropertyChangeListeners``()`                                                                                                                                                        |
    | `java.beans.PropertyChangeListener[]`                   | `getPropertyChangeListeners``(java.lang.String propertyName)`                                                                                                                           |
    | `java.lang.String`                                      | `getProviderID``()`<br>Returns the provider ID                                                                                                                                          |
    | `int`                                                   | `getSRID``()`<br>Gets the SRID of the Layer, 0 if it doesn't have an associated SRID                                                                                                    |
    | `boolean`                                               | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                               |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `hitTest``(int x, int y, int granularity)`<br>Performs a hit test for the given mouse location (x,y).                                                                                   |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `hitTest``(java.awt.geom.Rectangle2D box, int granularity)`<br>Performs a hit test for the given rectangle.                                                                             |
    | `boolean`                                               | `isVisible``()`<br>Checks whether this layer is currently visible.                                                                                                                      |
    | `void`                                                  | `mapRegionChanged``(`[`MapRegionEvent`](../core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change. |
    | `void`                                                  | `removed``(java.lang.Object source)`<br>The function called when the layer is removed from either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)    |
    | `void`                                                  | `removePropertyChangeListener``(java.beans.PropertyChangeListener listener)`                                                                                                            |
    | `void`                                                  | `removePropertyChangeListener``(java.lang.String propertyName, java.beans.PropertyChangeListener listener)`                                                                             |
    | `long`                                                  | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                  |
    | `void`                                                  | `repaint``()`<br>Tells the layer to repaint itself immediately.                                                                                                                         |
    | `void`                                                  | `setCanvas``(`[`MapCanvas`](../core/MapCanvas.md)` canvas)`<br>Sets the map canvas on which this layer is displayed.                                                                    |
    | `void`                                                  | `setName``(java.lang.String name)`<br>Sets the name for this layer.                                                                                                                     |
    | `java.lang.String`                                      | `setProperty``(java.lang.String key, java.lang.String value)`                                                                                                                           |
    | `void`                                                  | `setProviderID``(java.lang.String providerID)`<br>Sets the provider ID                                                                                                                  |
    | `void`                                                  | `setSRID``(int srid)`<br>Sets the SRID of the Layer                                                                                                                                     |
    | `void`                                                  | `setVisible``(boolean v)`<br>Sets the visibility of this layer.                                                                                                                         |
    | `org.w3c.dom.Element`                                   | `toXMLElement``()`<br>Returns an XML representation of the layer                                                                                                                        |
    | `void`                                                  | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BasicLayer

          public BasicLayer(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### getIcon

          public javax.swing.Icon getIcon()

      Specified by:
      [`getIcon`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getProperties

          public java.util.Properties getProperties()

    <!-- -->

    - #### toXMLElement

          public org.w3c.dom.Element toXMLElement()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Returns an XML representation of the layer
      Specified by:

      [`toXMLElement`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Returns:

    <!-- -->

    - #### fromXMLElement

          public void fromXMLElement(org.w3c.dom.Element element)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Loads the content from an XML representation
      Specified by:
      [`fromXMLElement`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Gets the name of the layer.
      Specified by:
      [`getName`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Returns:
      the name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Sets the name for this layer.
      Specified by:
      [`setName`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Parameters:
      `name` - the name of the layer

    <!-- -->

    - #### isVisible

          public boolean isVisible()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Checks whether this layer is currently visible.
      Specified by:

      [`isVisible`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Returns:

    <!-- -->

    - #### setVisible

          public void setVisible(boolean v)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Sets the visibility of this layer.
      Specified by:
      [`setVisible`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getProperty

          public java.lang.String getProperty(java.lang.String key)

    <!-- -->

    - #### getProperty

          public java.lang.String getProperty(java.lang.String key,
                                              java.lang.String defaultValue)

    <!-- -->

    - #### setProperty

          public java.lang.String setProperty(java.lang.String key,
                                              java.lang.String value)

    <!-- -->

    - #### addPropertyChangeListener

          public void addPropertyChangeListener(java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### addPropertyChangeListener

          public void addPropertyChangeListener(java.lang.String propertyName,
                                                java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### getPropertyChangeListeners

          public java.beans.PropertyChangeListener[] getPropertyChangeListeners()

    <!-- -->

    - #### getPropertyChangeListeners

          public java.beans.PropertyChangeListener[] getPropertyChangeListeners(java.lang.String propertyName)

    <!-- -->

    - #### removePropertyChangeListener

          public void removePropertyChangeListener(java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### removePropertyChangeListener

          public void removePropertyChangeListener(java.lang.String propertyName,
                                                   java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### clear

          public void clear()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Clears all contents of this layer.
      Specified by:
      [`clear`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getCanvas

          public MapCanvas getCanvas()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Gets the map canvas that this layer is displayed on.
      Specified by:
      [`getCanvas`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### setCanvas

          public void setCanvas(MapCanvas canvas)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Sets the map canvas on which this layer is displayed.
      Specified by:
      [`setCanvas`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(int x,
                                                   int y,
                                                   int granularity)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Performs a hit test for the given mouse location (x,y). All the geo-objects that pass the hit test will be returned.
      Specified by:
      [`hitTest`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Parameters:
      `x` - mouse location x

      `y` - mouse location y

      Returns:
      a list of features that pass the hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(java.awt.geom.Rectangle2D box,
                                                   int granularity)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Performs a hit test for the given rectangle. All the geo-objects that are either inside or intersect the rectangle will be returned.
      Specified by:
      [`hitTest`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Parameters:
      `box` - the test rectangle, in device coordinates

      Returns:
      a list of features that pass the box hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### repaint

          public void repaint()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Tells the layer to repaint itself immediately. Typically called when a layer's rendering uses a buffered image, and that image might be in an inconsistent state or should be updated.
      Specified by:
      [`repaint`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getSRID

          public int getSRID()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Gets the SRID of the Layer, 0 if it doesn't have an associated SRID
      Specified by:

      [`getSRID`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Returns:

    <!-- -->

    - #### setSRID

          public void setSRID(int srid)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Sets the SRID of the Layer
      Specified by:
      [`setSRID`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getDataMBR

          public java.awt.geom.Rectangle2D getDataMBR()

      Always return null here.
      Specified by:
      [`getDataMBR`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getFullExtent

          public java.awt.geom.Rectangle2D getFullExtent()

      Specified by:
      [`getFullExtent`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### added

          public void added(java.lang.Object source)

      Description copied from interface: [`Layer`](../core/Layer.md)
      The function called when the layer is added to either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)
      Specified by:
      [`added`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### removed

          public void removed(java.lang.Object source)

      Description copied from interface: [`Layer`](../core/Layer.md)
      The function called when the layer is removed from either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)
      Specified by:
      [`removed`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

    <!-- -->

    - #### getProviderID

          public java.lang.String getProviderID()

      Description copied from interface: [`Layer`](../core/Layer.md)
      Returns the provider ID
      Specified by:

      [`getProviderID`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Returns:

    <!-- -->

    - #### setProviderID

          public void setProviderID(java.lang.String providerID)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Sets the provider ID
      Specified by:
      [`setProviderID`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

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

- [Prev Class](AbstractDataSetLayer.md)
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
