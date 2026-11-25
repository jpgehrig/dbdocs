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

- [Prev Class](NFEProgressIndicatorLayer.md)
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

oracle.spatial.network.nfe.vis.mapcanvas.render

## Class NFERenderer\<V extends [NFEGeoObject](../../../model/spatial/NFEGeoObject.md)\>

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFERenderer\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of elements rendered. It must be a subclass of [`NFEGeoObject`](../../../model/spatial/NFEGeoObject.md)

  <!-- -->

  All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [GeoObjectLayer](../../maps/core/GeoObjectLayer.md), [HoverableLayer](../../maps/core/HoverableLayer.md), [Layer](../../maps/core/Layer.md), [SelectableLayer](../../maps/core/SelectableLayer.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEFeatureLayerRenderer](NFEFeatureLayerRenderer.md), [NFENetworkRenderer](NFENetworkRenderer.md), [NFEPathRenderer](NFEPathRenderer.md)

  ------------------------------------------------------------------------



      public abstract class NFERenderer<V extends NFEGeoObject>
      extends BasicLayer
      implements SelectableLayer, HoverableLayer, javax.swing.event.ChangeListener

  Basic renderer for displaying NFE layers using the MapCanvas. This class provides common functions used for rendering NFE API content.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------|
    | `NFERenderer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas)`<br>Constructor called from a subclass constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                       |
    |-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                          | `addContextualMenuHandler``(`[`ContextualMenuHandler`](ContextualMenuHandler.md)` contextualMenuHandler)`<br>Add a contextual menu handler                                                                                   |
    | `void`                                                          | `addSelectionListener``(`[`SelectionListener`](../../maps/core/SelectionListener.md)` l)`<br>Adds a SelectionListener                                                                                                        |
    | `void`                                                          | `clear``()`<br>Clears all contents of this layer.                                                                                                                                                                            |
    | `boolean`                                                       | `clearHover``()`<br>Removes the hovering state from all the geo-objects                                                                                                                                                      |
    | `boolean`                                                       | `clearSelection``()`<br>Clears all selected objects                                                                                                                                                                          |
    | `java.awt.geom.Rectangle2D`                                     | `getDataMBR``()`<br>Always return null here.                                                                                                                                                                                 |
    | `java.awt.geom.Rectangle2D`                                     | `getFullExtent``()`                                                                                                                                                                                                          |
    | `V`                                                             | `getGeoObject``(java.lang.String key)`<br>Gets the GeoObject identified by the given key                                                                                                                                     |
    | `java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `getHover``()`<br>Returns all the geo-object that are being hovered                                                                                                                                                          |
    | `float`                                                         | `getImageOpacityAlpha``()`<br>Gets the opacity                                                                                                                                                                               |
    | `V`                                                             | `getObject``(java.lang.Object key)`<br>Gets the GeoObject corresponding to the provided key                                                                                                                                  |
    | [`GeoObject`](../../maps/core/GeoObject.md)`[]`                 | `getObjects``()`<br>Gets all GeoObjects in this layer                                                                                                                                                                        |
    | `java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `getSelection``()`<br>Returns all selected objects                                                                                                                                                                           |
    | `java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `getSelection``(`[`GeoObject`](../../maps/core/GeoObject.md)` obj)`<br>Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object |
    | `JGeometrySegmentPoint`                                         | `getSnapPoint``(java.lang.Object key, java.awt.geom.Point2D point, double tolerance)`                                                                                                                                        |
    | `double`                                                        | `getTolerance``()`<br>Gets the screen tolerance converted to the model's coordinate system                                                                                                                                   |
    | `boolean`                                                       | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                                                    |
    | `java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `hitTest``(int x, int y, int granularity)`<br>Performs a hit test for the given mouse location (x,y).                                                                                                                        |
    | `java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `hitTest``(java.awt.geom.Rectangle2D mbr, int granularity)`<br>Performs a hit test for the given rectangle.                                                                                                                  |
    | `boolean`                                                       | `isHover``(`[`GeoObject`](../../maps/core/GeoObject.md)` obj)`<br>Returns true if the geo-object is being hovered                                                                                                            |
    | `boolean`                                                       | `isSelected``(`[`GeoObject`](../../maps/core/GeoObject.md)` obj)`<br>Checks if an object is selected                                                                                                                         |
    | `void`                                                          | `mapRegionChanged``(`[`MapRegionEvent`](../../maps/core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change.                              |
    | `int`                                                           | `numHovered``()`<br>Returns the number of geo-objects that are being hovered                                                                                                                                                 |
    | `int`                                                           | `numSelected``()`<br>Returns the number of selected objects                                                                                                                                                                  |
    | `void`                                                          | `refresh``()`<br>Refreshes the current data window                                                                                                                                                                           |
    | `void`                                                          | `refresh``(java.awt.geom.Rectangle2D dataWindow)`<br>Refreshes the data window at the given area                                                                                                                             |
    | `void`                                                          | `removeContextualMenuHandler``(`[`ContextualMenuHandler`](ContextualMenuHandler.md)` contextualMenuHandler)`<br>Remove a contextual menu handler                                                                             |
    | `void`                                                          | `removeSelectionListener``(`[`SelectionListener`](../../maps/core/SelectionListener.md)` l)`<br>Removes the given SelectionListener                                                                                          |
    | `long`                                                          | `render``(java.awt.Graphics2D graphics)`<br>Renders the layer contents to the given Graphics.                                                                                                                                |
    | `boolean`                                                       | `select``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> objs)`<br>Adds the provided objects to the selection list                                                                                            |
    | `boolean`                                                       | `setHover``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> objs)`<br>A list of geo-objects being hovered                                                                                                      |
    | `void`                                                          | `setImageOpacityAlpha``(float imageOpacityAlpha)`<br>Sets the opacity for the layer's rendered images                                                                                                                        |
    | `boolean`                                                       | `setSelection``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> selectedGeoObjects)`<br>Clears selection before setting the provided objects as selected                                                       |
    | `void`                                                          | `stateChanged``(javax.swing.event.ChangeEvent event)`                                                                                                                                                                        |
    | `boolean`                                                       | `unselect``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> objs)`<br>Removes the provided objects from the selection list                                                                                     |
    | `void`                                                          | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                                                                |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`added`](../../maps/core/Layer.md)`, `[`fromXMLElement`](../../maps/core/Layer.md)`, `[`getCanvas`](../../maps/core/Layer.md)`, `[`getIcon`](../../maps/core/Layer.md)`, `[`getName`](../../maps/core/Layer.md)`, `[`getProviderID`](../../maps/core/Layer.md)`, `[`getSRID`](../../maps/core/Layer.md)`, `[`isVisible`](../../maps/core/Layer.md)`, `[`removed`](../../maps/core/Layer.md)`, `[`repaint`](../../maps/core/Layer.md)`, `[`setCanvas`](../../maps/core/Layer.md)`, `[`setName`](../../maps/core/Layer.md)`, `[`setProviderID`](../../maps/core/Layer.md)`, `[`setSRID`](../../maps/core/Layer.md)`, `[`setVisible`](../../maps/core/Layer.md)`, `[`toXMLElement`](../../maps/core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### NFERenderer

          public NFERenderer(MapCanvas canvas)

      Constructor called from a subclass constructor. It initializes the basic renderer state.
      Parameters:
      `canvas` - the MapCanvas where the layer will be rendered

  <!-- -->

  - ### Method Detail

    - #### getTolerance

          public double getTolerance()

      Gets the screen tolerance converted to the model's coordinate system
      Returns:
      the tolerance value or zero if it is not specified or could not be converted

    <!-- -->

    - #### refresh

          public void refresh()

      Refreshes the current data window

    <!-- -->

    - #### refresh

          public void refresh(java.awt.geom.Rectangle2D dataWindow)

      Refreshes the data window at the given area
      Parameters:
      `dataWindow` - a region to be refreshed

    <!-- -->

    - #### getImageOpacityAlpha

          public float getImageOpacityAlpha()

      Gets the opacity
      Returns:
      the opacity value

    <!-- -->

    - #### setImageOpacityAlpha

          public void setImageOpacityAlpha(float imageOpacityAlpha)

      Sets the opacity for the layer's rendered images
      Parameters:
      `imageOpacityAlpha` - the opacity value

    <!-- -->

    - #### addContextualMenuHandler

          public void addContextualMenuHandler(ContextualMenuHandler contextualMenuHandler)

      Add a contextual menu handler
      Parameters:
      `contextualMenuHandler` - contextual menu handler

    <!-- -->

    - #### removeContextualMenuHandler

          public void removeContextualMenuHandler(ContextualMenuHandler contextualMenuHandler)

      Remove a contextual menu handler
      Parameters:
      `contextualMenuHandler` - contextual menu handler

    <!-- -->

    - #### getGeoObject

          public V getGeoObject(java.lang.String key)

      Gets the GeoObject identified by the given key
      Parameters:
      `key` - a GeoObject's key

      Returns:
      a GeoObject or null if it was not found

    <!-- -->

    - #### isSelected

          public boolean isSelected(GeoObject obj)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Checks if an object is selected
      Specified by:
      [`isSelected`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:
      true if the provided object is selected

    <!-- -->

    - #### clearSelection

          public boolean clearSelection()

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Clears all selected objects
      Specified by:
      [`clearSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:
      true if changes where made

    <!-- -->

    - #### numSelected

          public int numSelected()

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Returns the number of selected objects
      Specified by:
      [`numSelected`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:
      the number of selected objects

    <!-- -->

    - #### getSelection

          public java.util.List<GeoObject> getSelection()

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Returns all selected objects
      Specified by:

      [`getSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### getSelection

          public java.util.List<GeoObject> getSelection(GeoObject obj)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object
      Specified by:

      [`getSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### setSelection

          public boolean setSelection(java.util.List<GeoObject> selectedGeoObjects)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Clears selection before setting the provided objects as selected
      Specified by:

      [`setSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### select

          public boolean select(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Adds the provided objects to the selection list
      Specified by:

      [`select`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### unselect

          public boolean unselect(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Removes the provided objects from the selection list
      Specified by:

      [`unselect`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### addSelectionListener

          public void addSelectionListener(SelectionListener l)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Adds a SelectionListener
      Specified by:
      [`addSelectionListener`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

    <!-- -->

    - #### removeSelectionListener

          public void removeSelectionListener(SelectionListener l)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Removes the given SelectionListener
      Specified by:
      [`removeSelectionListener`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

    <!-- -->

    - #### stateChanged

          public void stateChanged(javax.swing.event.ChangeEvent event)

      Specified by:
      `stateChanged` in interface `javax.swing.event.ChangeListener`

    <!-- -->

    - #### setHover

          public boolean setHover(java.util.List<GeoObject> objs)

      Description copied from interface: [`HoverableLayer`](../../maps/core/HoverableLayer.md)
      A list of geo-objects being hovered
      Specified by:
      [`setHover`](../../maps/core/HoverableLayer.md) in interface [`HoverableLayer`](../../maps/core/HoverableLayer.md)

      Returns:
      true if the objects were hovered

    <!-- -->

    - #### clearHover

          public boolean clearHover()

      Description copied from interface: [`HoverableLayer`](../../maps/core/HoverableLayer.md)
      Removes the hovering state from all the geo-objects
      Specified by:

      [`clearHover`](../../maps/core/HoverableLayer.md) in interface [`HoverableLayer`](../../maps/core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### getHover

          public java.util.List<GeoObject> getHover()

      Description copied from interface: [`HoverableLayer`](../../maps/core/HoverableLayer.md)
      Returns all the geo-object that are being hovered
      Specified by:

      [`getHover`](../../maps/core/HoverableLayer.md) in interface [`HoverableLayer`](../../maps/core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### isHover

          public boolean isHover(GeoObject obj)

      Description copied from interface: [`HoverableLayer`](../../maps/core/HoverableLayer.md)
      Returns true if the geo-object is being hovered
      Specified by:

      [`isHover`](../../maps/core/HoverableLayer.md) in interface [`HoverableLayer`](../../maps/core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### numHovered

          public int numHovered()

      Description copied from interface: [`HoverableLayer`](../../maps/core/HoverableLayer.md)
      Returns the number of geo-objects that are being hovered
      Specified by:

      [`numHovered`](../../maps/core/HoverableLayer.md) in interface [`HoverableLayer`](../../maps/core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### getSnapPoint

          public JGeometrySegmentPoint getSnapPoint(java.lang.Object key,
                                                    java.awt.geom.Point2D point,
                                                    double tolerance)

    <!-- -->

    - #### getFullExtent

          public java.awt.geom.Rectangle2D getFullExtent()

      Specified by:
      [`getFullExtent`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`getFullExtent`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### clear

          public void clear()

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Clears all contents of this layer.
      Specified by:
      [`clear`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`clear`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`handleEvent`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`update`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### getDataMBR

          public java.awt.geom.Rectangle2D getDataMBR()

      Description copied from class: [`BasicLayer`](../../maps/layer/BasicLayer.md)
      Always return null here.
      Specified by:
      [`getDataMBR`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`getDataMBR`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### getObjects

          public GeoObject[] getObjects()

      Description copied from interface: [`GeoObjectLayer`](../../maps/core/GeoObjectLayer.md)
      Gets all GeoObjects in this layer
      Specified by:

      [`getObjects`](../../maps/core/GeoObjectLayer.md) in interface [`GeoObjectLayer`](../../maps/core/GeoObjectLayer.md)

      Returns:

    <!-- -->

    - #### getObject

          public V getObject(java.lang.Object key)

      Description copied from interface: [`GeoObjectLayer`](../../maps/core/GeoObjectLayer.md)
      Gets the GeoObject corresponding to the provided key
      Specified by:

      [`getObject`](../../maps/core/GeoObjectLayer.md) in interface [`GeoObjectLayer`](../../maps/core/GeoObjectLayer.md)

      Returns:

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(int x,
                                                   int y,
                                                   int granularity)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Performs a hit test for the given mouse location (x,y). All the geo-objects that pass the hit test will be returned.
      Specified by:
      [`hitTest`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`hitTest`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

      Parameters:
      `x` - mouse location x

      `y` - mouse location y

      Returns:
      a list of features that pass the hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(java.awt.geom.Rectangle2D mbr,
                                                   int granularity)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Performs a hit test for the given rectangle. All the geo-objects that are either inside or intersect the rectangle will be returned.
      Specified by:
      [`hitTest`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`hitTest`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

      Parameters:
      `mbr` - the test rectangle, in device coordinates

      Returns:
      a list of features that pass the box hit test; if no feature passes the hit test, the list is empty.

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`mapRegionChanged`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D graphics)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`render`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

      Parameters:
      `graphics` - the graphics object

      Returns:
      the rendering time in milliseconds.

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

- [Prev Class](NFEProgressIndicatorLayer.md)
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
