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

- [Prev Class](HoverManager.md)
- [Next Class](LayerManager.md)

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

## Interface Layer

- All Known Subinterfaces:
  [EditableLayer](EditableLayer.md), [GeoObjectLayer](GeoObjectLayer.md), [HoverableLayer](HoverableLayer.md), [MVThemeLayer](MVThemeLayer.md), [SelectableLayer](SelectableLayer.md), [Tool](../tools/Tool.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md), [BasicLayer](../layer/BasicLayer.md), [BasicTool](../tools/BasicTool.md), [MapNavLayer](../layer/ui/MapNavLayer.md), [NFEAddFeatureElementTool](../../mapcanvas/tool/NFEAddFeatureElementTool.md), [NFEAddFeatureTool](../../mapcanvas/tool/NFEAddFeatureTool.md), [NFEBoxSelectionTool](../../mapcanvas/tool/NFEBoxSelectionTool.md), [NFEEditVertexTool](../../mapcanvas/tool/NFEEditVertexTool.md), [NFEFeatureElementSelectionTool](../../mapcanvas/tool/NFEFeatureElementSelectionTool.md), [NFEFeatureLayerRenderer](../../mapcanvas/render/NFEFeatureLayerRenderer.md), [NFEFeatureSelectionTool](../../mapcanvas/tool/NFEFeatureSelectionTool.md), [NFEManipulableFeatureLayerRenderer](../../mapcanvas/render/NFEManipulableFeatureLayerRenderer.md), [NFEManipulateTool](../../mapcanvas/tool/NFEManipulateTool.md), [NFENetElementSelectionTool](../../mapcanvas/tool/NFENetElementSelectionTool.md), [NFENetworkRenderer](../../mapcanvas/render/NFENetworkRenderer.md), [NFEPathRenderer](../../mapcanvas/render/NFEPathRenderer.md), [NFEProgressIndicatorLayer](../../mapcanvas/render/NFEProgressIndicatorLayer.md), [NFERenderer](../../mapcanvas/render/NFERenderer.md), [NFESelectionTool](../../mapcanvas/tool/NFESelectionTool.md), [NFETool](../../mapcanvas/tool/NFETool.md), [PointerLocationLayer](../layer/ui/PointerLocationLayer.md), [ProgressIndicatorLayer](../layer/ui/ProgressIndicatorLayer.md), [ScaleBarLayer](../layer/ui/ScaleBarLayer.md), [SimpleBGLayer](../layer/ui/SimpleBGLayer.md)

  ------------------------------------------------------------------------



      public interface Layer

  A Layer represents a graphics layer that handles the display of and interaction with a particular type of contents. Each layer is responsible for repainting itself and updating its content model as needed. It also listens for and handles various events. Layers are organized and draw in the painter's order. All layers are managed by a LayerManager.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description  |
    |---------------------------|------------------------|
    | `static java.lang.String` | `PROPERTY_NAME`        |
    | `static java.lang.String` | `PROPERTY_PROVIDERID`  |
    | `static java.lang.String` | `PROPERTY_SRID`        |
    | `static java.lang.String` | `PROPERTY_VISIBLE`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                               |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `added``(java.lang.Object source)`<br>The function called when the layer is added to either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)       |
    | `void`                                          | `clear``()`<br>Clears all contents of this layer.                                                                                                                                    |
    | `void`                                          | `fromXMLElement``(org.w3c.dom.Element element)`<br>Loads the content from an XML representation                                                                                      |
    | [`MapCanvas`](MapCanvas.md)                     | `getCanvas``()`<br>Gets the map canvas that this layer is displayed on.                                                                                                              |
    | `java.awt.geom.Rectangle2D`                     | `getDataMBR``()`<br>Gets the minimum bounding rectangle of all the data in this layer.                                                                                               |
    | `java.awt.geom.Rectangle2D`                     | `getFullExtent``()`                                                                                                                                                                  |
    | `javax.swing.Icon`                              | `getIcon``()`                                                                                                                                                                        |
    | `java.lang.String`                              | `getName``()`<br>Gets the name of the layer.                                                                                                                                         |
    | `java.lang.String`                              | `getProviderID``()`<br>Returns the provider ID                                                                                                                                       |
    | `int`                                           | `getSRID``()`<br>Gets the SRID of the Layer, 0 if it doesn't have an associated SRID                                                                                                 |
    | `boolean`                                       | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                            |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>` | `hitTest``(int x, int y, int granularity)`<br>Performs a hit test for the given mouse location (x,y).                                                                                |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>` | `hitTest``(java.awt.geom.Rectangle2D box, int granularity)`<br>Performs a hit test for the given rectangle.                                                                          |
    | `boolean`                                       | `isVisible``()`<br>Checks whether this layer is currently visible.                                                                                                                   |
    | `void`                                          | `mapRegionChanged``(`[`MapRegionEvent`](MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change.      |
    | `void`                                          | `removed``(java.lang.Object source)`<br>The function called when the layer is removed from either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later) |
    | `long`                                          | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                               |
    | `void`                                          | `repaint``()`<br>Tells the layer to repaint itself immediately.                                                                                                                      |
    | `void`                                          | `setCanvas``(`[`MapCanvas`](MapCanvas.md)` parent)`<br>Sets the map canvas on which this layer is displayed.                                                                         |
    | `void`                                          | `setName``(java.lang.String name)`<br>Sets the name for this layer.                                                                                                                  |
    | `void`                                          | `setProviderID``(java.lang.String providerID)`<br>Sets the provider ID                                                                                                               |
    | `void`                                          | `setSRID``(int srid)`<br>Sets the SRID of the Layer                                                                                                                                  |
    | `void`                                          | `setVisible``(boolean v)`<br>Sets the visibility of this layer.                                                                                                                      |
    | `org.w3c.dom.Element`                           | `toXMLElement``()`<br>Returns an XML representation of the layer                                                                                                                     |
    | `void`                                          | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                        |

<!-- -->

- - ### Field Detail

    - #### PROPERTY_NAME

          static final java.lang.String PROPERTY_NAME

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_VISIBLE

          static final java.lang.String PROPERTY_VISIBLE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_SRID

          static final java.lang.String PROPERTY_SRID

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_PROVIDERID

          static final java.lang.String PROPERTY_PROVIDERID

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getName

          java.lang.String getName()

      Gets the name of the layer.
      Returns:
      the name

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the name for this layer.
      Parameters:
      `name` - the name of the layer

    <!-- -->

    - #### isVisible

          boolean isVisible()

      Checks whether this layer is currently visible.
      Returns:

    <!-- -->

    - #### setVisible

          void setVisible(boolean v)

      Sets the visibility of this layer.
      Parameters:
      `v` -

    <!-- -->

    - #### clear

          void clear()

      Clears all contents of this layer.

    <!-- -->

    - #### handleEvent

          boolean handleEvent(java.util.EventObject evt)

      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Parameters:
      `evt` -

    <!-- -->

    - #### update

          void update(long elapsedTime)

      updates the contents data model or structure.
      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### render

          long render(java.awt.Graphics2D g)

      Renders the layer contents to the given Graphics.
      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### hitTest

          java.util.List<GeoObject> hitTest(int x,
                                            int y,
                                            int granularity)

      Performs a hit test for the given mouse location (x,y). All the geo-objects that pass the hit test will be returned.
      Parameters:
      `x` - mouse location x

      `y` - mouse location y

      Returns:
      a list of features that pass the hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### hitTest

          java.util.List<GeoObject> hitTest(java.awt.geom.Rectangle2D box,
                                            int granularity)

      Performs a hit test for the given rectangle. All the geo-objects that are either inside or intersect the rectangle will be returned.
      Parameters:
      `box` - the test rectangle, in device coordinates

      Returns:
      a list of features that pass the box hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### setCanvas

          void setCanvas(MapCanvas parent)

      Sets the map canvas on which this layer is displayed.

    <!-- -->

    - #### getCanvas

          MapCanvas getCanvas()

      Gets the map canvas that this layer is displayed on.

    <!-- -->

    - #### mapRegionChanged

          void mapRegionChanged(MapRegionEvent e)

      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.

    <!-- -->

    - #### repaint

          void repaint()

      Tells the layer to repaint itself immediately. Typically called when a layer's rendering uses a buffered image, and that image might be in an inconsistent state or should be updated.

    <!-- -->

    - #### getIcon

          javax.swing.Icon getIcon()

    <!-- -->

    - #### getSRID

          int getSRID()

      Gets the SRID of the Layer, 0 if it doesn't have an associated SRID
      Returns:

    <!-- -->

    - #### setSRID

          void setSRID(int srid)

      Sets the SRID of the Layer

    <!-- -->

    - #### getDataMBR

          java.awt.geom.Rectangle2D getDataMBR()

      Gets the minimum bounding rectangle of all the data in this layer.

    <!-- -->

    - #### getFullExtent

          java.awt.geom.Rectangle2D getFullExtent()

    <!-- -->

    - #### added

          void added(java.lang.Object source)

      The function called when the layer is added to either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)

    <!-- -->

    - #### removed

          void removed(java.lang.Object source)

      The function called when the layer is removed from either a MapCanvas or an EditSession (typically both, MapCanvas first, EditSession later)

    <!-- -->

    - #### toXMLElement

          org.w3c.dom.Element toXMLElement()

      Returns an XML representation of the layer
      Returns:

    <!-- -->

    - #### fromXMLElement

          void fromXMLElement(org.w3c.dom.Element element)

      Loads the content from an XML representation
      Parameters:
      `element` -

    <!-- -->

    - #### getProviderID

          java.lang.String getProviderID()

      Returns the provider ID
      Returns:

    <!-- -->

    - #### setProviderID

          void setProviderID(java.lang.String providerID)

      Sets the provider ID
      Parameters:
      `providerID` -

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

- [Prev Class](HoverManager.md)
- [Next Class](LayerManager.md)

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
