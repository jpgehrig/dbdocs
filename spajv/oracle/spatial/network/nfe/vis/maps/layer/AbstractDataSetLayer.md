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
- [Next Class](BasicLayer.md)

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

## Class AbstractDataSetLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.AbstractDataSetLayer

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [EditableLayer](../core/EditableLayer.md), [GeoObjectLayer](../core/GeoObjectLayer.md), [HoverableLayer](../core/HoverableLayer.md), [Layer](../core/Layer.md), [MVThemeLayer](../core/MVThemeLayer.md), [SelectableLayer](../core/SelectableLayer.md)

  ------------------------------------------------------------------------



      public abstract class AbstractDataSetLayer
      extends BasicLayer
      implements EditableLayer, SelectableLayer, HoverableLayer, MVThemeLayer, javax.swing.event.ChangeListener

  (non-Javadoc)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description           |
    |---------------------------|---------------------------------|
    | `static java.lang.String` | `PROPERTY_BASETABLE`            |
    | `static java.lang.String` | `PROPERTY_DATASOURCE`           |
    | `static java.lang.String` | `PROPERTY_EDITOR`               |
    | `static java.lang.String` | `PROPERTY_JSESSIONID`           |
    | `static java.lang.String` | `PROPERTY_KEYCOLUMN`            |
    | `static java.lang.String` | `PROPERTY_KEYSEQUENCE`          |
    | `static java.lang.String` | `PROPERTY_LABELCOLUMN`          |
    | `static java.lang.String` | `PROPERTY_LABELSTYLE`           |
    | `static java.lang.String` | `PROPERTY_LIVESCALE`            |
    | `static java.lang.String` | `PROPERTY_OPTIMIZE_GEOMOP`      |
    | `static java.lang.String` | `PROPERTY_OWNER`                |
    | `static java.lang.String` | `PROPERTY_QUERYCONDITION`       |
    | `static java.lang.String` | `PROPERTY_RENDER_MVNOTEDITING`  |
    | `static java.lang.String` | `PROPERTY_RENDER_ONZOOMIN`      |
    | `static java.lang.String` | `PROPERTY_RENDER_ONZOOMOUT`     |
    | `static java.lang.String` | `PROPERTY_RENDERSTYLE`          |
    | `static java.lang.String` | `PROPERTY_RENDERSTYLE_NONLIVE`  |
    | `static java.lang.String` | `PROPERTY_SERVERURL`            |
    | `static java.lang.String` | `PROPERTY_SPATIALCOLUMN`        |

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[EditableLayer](../core/EditableLayer.md)

      [`PROPERTY_EDITABLE`](../core/EditableLayer.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`PROPERTY_NAME`](../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../core/Layer.md)`, `[`PROPERTY_SRID`](../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../core/Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                               |
    |----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                         | `addEditChangeListener``(`[`EditChangeListener`](../core/EditChangeListener.md)` l)`<br>Adds a change listener to listen for editing changes.                                                                        |
    | `void`                                                         | `addSelectionListener``(`[`SelectionListener`](../core/SelectionListener.md)` l)`<br>Adds a SelectionListener                                                                                                        |
    | `boolean`                                                      | `appendToObject``(java.lang.Object key, java.lang.Object spatialObject)`<br>Appends the provided spatialObject to an existing feature                                                                                |
    | `void`                                                         | `clearChanges``()`                                                                                                                                                                                                   |
    | `boolean`                                                      | `clearHover``()`<br>Removes the hovering state from all the geo-objects                                                                                                                                              |
    | `boolean`                                                      | `clearSelection``()`<br>Clears all selected objects                                                                                                                                                                  |
    | [`GeoObject`](../core/GeoObject.md)                            | `deleteObject``(java.lang.Object key)`<br>Deletes an existing GeoObject instance.                                                                                                                                    |
    | `void`                                                         | `fromXMLElement``(org.w3c.dom.Element element)`<br>Loads the content from an XML representation                                                                                                                      |
    | [`AbstractFeature`](../geoobject/AbstractFeature.md)`[]`       | `getCurrentDeletedFeatures``()`                                                                                                                                                                                      |
    | `AbstractDataSet`                                              | `getDataSet``()`                                                                                                                                                                                                     |
    | `AbstractDataSource`                                           | `getDataSource``()`                                                                                                                                                                                                  |
    | `java.awt.geom.Rectangle2D`                                    | `getFullExtent``()`                                                                                                                                                                                                  |
    | [`GeoDataProducer`](../core/GeoDataProducer.md)                | `getGeoDataProducer``()`<br>Gets the currently set GeoDataProducer.                                                                                                                                                  |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`        | `getHover``()`<br>Returns all the geo-object that are being hovered                                                                                                                                                  |
    | [`AbstractIndexedDataSet`](../index/AbstractIndexedDataSet.md) | `getIndexedDataSet``()`                                                                                                                                                                                              |
    | `java.lang.String[]`                                           | `getNonComplexAttributes``()`                                                                                                                                                                                        |
    | [`GeoObject`](../core/GeoObject.md)                            | `getObject``(java.lang.Object key)`<br>Gets the GeoObject corresponding to the provided key                                                                                                                          |
    | [`GeoObject`](../core/GeoObject.md)`[]`                        | `getObjects``()`<br>Gets all GeoObjects in this layer                                                                                                                                                                |
    | `boolean`                                                      | `getRenderOnZoomIn``()`                                                                                                                                                                                              |
    | `boolean`                                                      | `getRenderOnZoomOut``()`                                                                                                                                                                                             |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`        | `getSelection``()`<br>Returns all selected objects                                                                                                                                                                   |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`        | `getSelection``(`[`GeoObject`](../core/GeoObject.md)` obj)`<br>Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object |
    | `void`                                                         | `getTableKeyColumn``()`                                                                                                                                                                                              |
    | [`WorkSpace`](../geoobject/WorkSpace.md)                       | `getWorkspace``()`                                                                                                                                                                                                   |
    | `boolean`                                                      | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                                            |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`        | `hitTest``(int x, int y, int granularity)`<br>Performs a hit test for the given mouse location (x,y).                                                                                                                |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>`        | `hitTest``(java.awt.geom.Rectangle2D box, int granularity)`<br>Performs a hit test for the given rectangle.                                                                                                          |
    | `boolean`                                                      | `insertObject``(java.lang.Object key, `[`GeoObject`](../core/GeoObject.md)` obj)`<br>Inserts a new GeoObject instance                                                                                                |
    | `boolean`                                                      | `isEditable``()`                                                                                                                                                                                                     |
    | `boolean`                                                      | `isHover``(`[`GeoObject`](../core/GeoObject.md)` obj)`<br>Returns true if the geo-object is being hovered                                                                                                            |
    | `boolean`                                                      | `isModified``()`                                                                                                                                                                                                     |
    | `boolean`                                                      | `isSelected``(`[`GeoObject`](../core/GeoObject.md)` obj)`<br>Checks if an object is selected                                                                                                                         |
    | `void`                                                         | `mapRegionChanged``(`[`MapRegionEvent`](../core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change.                              |
    | [`GeoObject`](../core/GeoObject.md)                            | `newObject``(java.lang.Object spatialObject, java.lang.Object[] params)`<br>Creates a new GeoObject with the provided parameters                                                                                     |
    | `int`                                                          | `numHovered``()`<br>Returns the number of geo-objects that are being hovered                                                                                                                                         |
    | `int`                                                          | `numSelected``()`<br>Returns the number of selected objects                                                                                                                                                          |
    | `void`                                                         | `onDataException``(`[`DataProducer`](../core/DataProducer.md)` producer, java.lang.Throwable exception)`<br>A call-back function to handle exceptions during data loading.                                           |
    | `void`                                                         | `onDataReady``(`[`DataProducer`](../core/DataProducer.md)` producer, java.util.List<`[`AbstractFeature`](../geoobject/AbstractFeature.md)`> data)`<br>A call-back function to handle data ready state.               |
    | `void`                                                         | `redo``(EditChangeEvent change)`                                                                                                                                                                                     |
    | `void`                                                         | `removeEditChangeListener``(`[`EditChangeListener`](../core/EditChangeListener.md)` l)`                                                                                                                              |
    | `void`                                                         | `removeSelectionListener``(`[`SelectionListener`](../core/SelectionListener.md)` l)`<br>Removes the given SelectionListener                                                                                          |
    | `long`                                                         | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                                               |
    | `boolean`                                                      | `save``()`                                                                                                                                                                                                           |
    | `boolean`                                                      | `select``(java.util.List<`[`GeoObject`](../core/GeoObject.md)`> objs)`<br>Adds the provided objects to the selection list                                                                                            |
    | `void`                                                         | `setCanvas``(`[`MapCanvas`](../core/MapCanvas.md)` canvas)`<br>Sets the map canvas on which this layer is displayed.                                                                                                 |
    | `void`                                                         | `setDataSource``(AbstractDataSource dataSource)`                                                                                                                                                                     |
    | `void`                                                         | `setEditable``(boolean editable)`                                                                                                                                                                                    |
    | `void`                                                         | `setGeoDataProducer``(AbstractDataSetProducer geoProducer)`<br>Sets a AbstractDataSetProducer on this layer.                                                                                                         |
    | `void`                                                         | `setHighliteGeometries``(`[`JGeometry`](../../../../../geometry/JGeometry.md)`[] geoms)`                                                                                                                             |
    | `boolean`                                                      | `setHover``(java.util.List<`[`GeoObject`](../core/GeoObject.md)`> objs)`<br>A list of geo-objects being hovered                                                                                                      |
    | `void`                                                         | `setIndexedDataSet``(`[`AbstractIndexedDataSet`](../index/AbstractIndexedDataSet.md)` indexedSet)`                                                                                                                   |
    | `void`                                                         | `setRenderOnZoomIn``(boolean render)`                                                                                                                                                                                |
    | `void`                                                         | `setRenderOnZoomOut``(boolean render)`                                                                                                                                                                               |
    | `boolean`                                                      | `setSelection``(java.util.List<`[`GeoObject`](../core/GeoObject.md)`> objs)`<br>Clears selection before setting the provided objects as selected                                                                     |
    | `void`                                                         | `setToUpdate``()`                                                                                                                                                                                                    |
    | `void`                                                         | `stateChanged``(javax.swing.event.ChangeEvent e)`                                                                                                                                                                    |
    | `abstract int`                                                 | `transformFeatures``(`[`GeoObject`](../core/GeoObject.md)`[] features, java.awt.geom.AffineTransform at)`                                                                                                            |
    | `void`                                                         | `undo``(EditChangeEvent change)`<br>Performs and undo operation.                                                                                                                                                     |
    | `boolean`                                                      | `unselect``(java.util.List<`[`GeoObject`](../core/GeoObject.md)`> objs)`<br>Removes the provided objects from the selection list                                                                                     |
    | `void`                                                         | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                                                        |
    | [`GeoObject`](../core/GeoObject.md)                            | `updateObject``(java.lang.Object key, `[`GeoObject`](../core/GeoObject.md)` changedObject)`<br>Updates an existing GeoObject with the specified change.                                                              |
    | `boolean`                                                      | `updateObjectAttributes``(java.lang.String key, Field[] updAttrs)`<br>Updates one or more object attributes.                                                                                                         |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](BasicLayer.md)

      [`added`](BasicLayer.md)`, `[`addPropertyChangeListener`](BasicLayer.md)`, `[`addPropertyChangeListener`](BasicLayer.md)`, `[`clear`](BasicLayer.md)`, `[`getCanvas`](BasicLayer.md)`, `[`getDataMBR`](BasicLayer.md)`, `[`getIcon`](BasicLayer.md)`, `[`getName`](BasicLayer.md)`, `[`getProperties`](BasicLayer.md)`, `[`getProperty`](BasicLayer.md)`, `[`getProperty`](BasicLayer.md)`, `[`getPropertyChangeListeners`](BasicLayer.md)`, `[`getPropertyChangeListeners`](BasicLayer.md)`, `[`getProviderID`](BasicLayer.md)`, `[`getSRID`](BasicLayer.md)`, `[`isVisible`](BasicLayer.md)`, `[`removed`](BasicLayer.md)`, `[`removePropertyChangeListener`](BasicLayer.md)`, `[`removePropertyChangeListener`](BasicLayer.md)`, `[`repaint`](BasicLayer.md)`, `[`setName`](BasicLayer.md)`, `[`setProperty`](BasicLayer.md)`, `[`setProviderID`](BasicLayer.md)`, `[`setSRID`](BasicLayer.md)`, `[`setVisible`](BasicLayer.md)`, `[`toXMLElement`](BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`added`](../core/Layer.md)`, `[`clear`](../core/Layer.md)`, `[`getCanvas`](../core/Layer.md)`, `[`getDataMBR`](../core/Layer.md)`, `[`getIcon`](../core/Layer.md)`, `[`getName`](../core/Layer.md)`, `[`getProviderID`](../core/Layer.md)`, `[`getSRID`](../core/Layer.md)`, `[`isVisible`](../core/Layer.md)`, `[`removed`](../core/Layer.md)`, `[`repaint`](../core/Layer.md)`, `[`setName`](../core/Layer.md)`, `[`setProviderID`](../core/Layer.md)`, `[`setSRID`](../core/Layer.md)`, `[`setVisible`](../core/Layer.md)`, `[`toXMLElement`](../core/Layer.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[MVThemeLayer](../core/MVThemeLayer.md)

      [`getThemeDescriptor`](../core/MVThemeLayer.md)

<!-- -->

- - ### Field Detail

    - #### PROPERTY_SERVERURL

          public static final java.lang.String PROPERTY_SERVERURL

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_DATASOURCE

          public static final java.lang.String PROPERTY_DATASOURCE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_EDITOR

          public static final java.lang.String PROPERTY_EDITOR

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_JSESSIONID

          public static final java.lang.String PROPERTY_JSESSIONID

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_OWNER

          public static final java.lang.String PROPERTY_OWNER

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_BASETABLE

          public static final java.lang.String PROPERTY_BASETABLE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_KEYCOLUMN

          public static final java.lang.String PROPERTY_KEYCOLUMN

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_SPATIALCOLUMN

          public static final java.lang.String PROPERTY_SPATIALCOLUMN

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_QUERYCONDITION

          public static final java.lang.String PROPERTY_QUERYCONDITION

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_KEYSEQUENCE

          public static final java.lang.String PROPERTY_KEYSEQUENCE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_RENDERSTYLE

          public static final java.lang.String PROPERTY_RENDERSTYLE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_RENDERSTYLE_NONLIVE

          public static final java.lang.String PROPERTY_RENDERSTYLE_NONLIVE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_LABELCOLUMN

          public static final java.lang.String PROPERTY_LABELCOLUMN

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_LABELSTYLE

          public static final java.lang.String PROPERTY_LABELSTYLE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_RENDER_MVNOTEDITING

          public static final java.lang.String PROPERTY_RENDER_MVNOTEDITING

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_LIVESCALE

          public static final java.lang.String PROPERTY_LIVESCALE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_RENDER_ONZOOMOUT

          public static final java.lang.String PROPERTY_RENDER_ONZOOMOUT

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_RENDER_ONZOOMIN

          public static final java.lang.String PROPERTY_RENDER_ONZOOMIN

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_OPTIMIZE_GEOMOP

          public static final java.lang.String PROPERTY_OPTIMIZE_GEOMOP

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### fromXMLElement

          public void fromXMLElement(org.w3c.dom.Element element)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Loads the content from an XML representation
      Specified by:
      [`fromXMLElement`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`fromXMLElement`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

    <!-- -->

    - #### setCanvas

          public void setCanvas(MapCanvas canvas)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Sets the map canvas on which this layer is displayed.
      Specified by:
      [`setCanvas`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`setCanvas`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

    <!-- -->

    - #### getTableKeyColumn

          public void getTableKeyColumn()

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`update`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### getWorkspace

          public WorkSpace getWorkspace()
                                 throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRenderOnZoomOut

          public boolean getRenderOnZoomOut()

    <!-- -->

    - #### setRenderOnZoomOut

          public void setRenderOnZoomOut(boolean render)

    <!-- -->

    - #### getRenderOnZoomIn

          public boolean getRenderOnZoomIn()

    <!-- -->

    - #### setRenderOnZoomIn

          public void setRenderOnZoomIn(boolean render)

    <!-- -->

    - #### getIndexedDataSet

          public AbstractIndexedDataSet getIndexedDataSet()

      Returns:

    <!-- -->

    - #### setIndexedDataSet

          public void setIndexedDataSet(AbstractIndexedDataSet indexedSet)

    <!-- -->

    - #### getNonComplexAttributes

          public java.lang.String[] getNonComplexAttributes()

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`handleEvent`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

    <!-- -->

    - #### getDataSet

          public AbstractDataSet getDataSet()

    <!-- -->

    - #### getFullExtent

          public java.awt.geom.Rectangle2D getFullExtent()

      Specified by:
      [`getFullExtent`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`getFullExtent`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

    <!-- -->

    - #### setEditable

          public void setEditable(boolean editable)

      Specified by:
      [`setEditable`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### isEditable

          public boolean isEditable()

      Specified by:
      [`isEditable`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### isModified

          public boolean isModified()

      Specified by:
      [`isModified`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### save

          public boolean save()

      Specified by:
      [`save`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### clearChanges

          public void clearChanges()

      Specified by:
      [`clearChanges`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### getObjects

          public GeoObject[] getObjects()

      Description copied from interface: [`GeoObjectLayer`](../core/GeoObjectLayer.md)
      Gets all GeoObjects in this layer
      Specified by:

      [`getObjects`](../core/GeoObjectLayer.md) in interface [`GeoObjectLayer`](../core/GeoObjectLayer.md)

      Returns:

    <!-- -->

    - #### getObject

          public GeoObject getObject(java.lang.Object key)

      Description copied from interface: [`GeoObjectLayer`](../core/GeoObjectLayer.md)
      Gets the GeoObject corresponding to the provided key
      Specified by:

      [`getObject`](../core/GeoObjectLayer.md) in interface [`GeoObjectLayer`](../core/GeoObjectLayer.md)

      Returns:

    <!-- -->

    - #### newObject

          public GeoObject newObject(java.lang.Object spatialObject,
                                     java.lang.Object[] params)
                              throws java.lang.Exception

      Description copied from interface: [`EditableLayer`](../core/EditableLayer.md)
      Creates a new GeoObject with the provided parameters
      Specified by:
      [`newObject`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### appendToObject

          public boolean appendToObject(java.lang.Object key,
                                        java.lang.Object spatialObject)
                                 throws java.lang.Exception

      Description copied from interface: [`EditableLayer`](../core/EditableLayer.md)
      Appends the provided spatialObject to an existing feature
      Specified by:
      [`appendToObject`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(int x,
                                                   int y,
                                                   int granularity)

      Performs a hit test for the given mouse location (x,y). All the geo-objects that pass the hit test will be returned.
      Specified by:
      [`hitTest`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`hitTest`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

      Parameters:
      `x` - mouse location x

      `y` - mouse location y

      Returns:
      an array of features that pass the hit test; if no feature passes the hit test, null is returned.

    <!-- -->

    - #### hitTest

          public java.util.List<GeoObject> hitTest(java.awt.geom.Rectangle2D box,
                                                   int granularity)

      Performs a hit test for the given rectangle. All the geo-objects that are either inside or intersect the rectangle will be returned.
      Specified by:
      [`hitTest`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`hitTest`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

      Parameters:
      `box` - the test rectangle, in device coordinates

      Returns:
      an array of features that pass the box hit test; if no feature passes the hit test, null is returned.

    <!-- -->

    - #### setGeoDataProducer

          public void setGeoDataProducer(AbstractDataSetProducer geoProducer)

      Sets a AbstractDataSetProducer on this layer.
      Parameters:
      `geoProducer` - a AbstractDataSetProducer instance

    <!-- -->

    - #### getGeoDataProducer

          public GeoDataProducer getGeoDataProducer()

      Gets the currently set GeoDataProducer.
      Returns:
      geoDataProducer

    <!-- -->

    - #### onDataException

          public void onDataException(DataProducer producer,
                                      java.lang.Throwable exception)

      A call-back function to handle exceptions during data loading. The exception is typically caught by an associated data producer.
      Parameters:
      `producer` - the producer that throws the exception during data loading

      `exception` - the exception or error that was encountered.

    <!-- -->

    - #### updateObject

          public GeoObject updateObject(java.lang.Object key,
                                        GeoObject changedObject)

      Updates an existing GeoObject with the specified change.
      Specified by:
      [`updateObject`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Parameters:
      `changedObject` - the object containing changes

      Returns:
      the old object

    <!-- -->

    - #### updateObjectAttributes

          public boolean updateObjectAttributes(java.lang.String key,
                                                Field[] updAttrs)
                                         throws java.lang.Exception

      Updates one or more object attributes.
      Parameters:
      `updAttrs` - the object attributes to be updated

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### deleteObject

          public GeoObject deleteObject(java.lang.Object key)

      Deletes an existing GeoObject instance.
      Specified by:
      [`deleteObject`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Parameters:
      `key` - the object to be deleted

      Returns:
      the deleted object

    <!-- -->

    - #### insertObject

          public boolean insertObject(java.lang.Object key,
                                      GeoObject obj)
                               throws java.lang.Exception

      Inserts a new GeoObject instance
      Specified by:
      [`insertObject`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Parameters:
      `obj` - the new object to be added to this layer.

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### undo

          public void undo(EditChangeEvent change)
                    throws java.lang.Exception

      Performs and undo operation.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### redo

          public void redo(EditChangeEvent change)
                    throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values.
      Specified by:
      [`mapRegionChanged`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`mapRegionChanged`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

    <!-- -->

    - #### onDataReady

          public void onDataReady(DataProducer producer,
                                  java.util.List<AbstractFeature> data)

      A call-back function to handle data ready state.
      Parameters:
      `producer` - the producer whose data is ready to be consumed by this layer.

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../core/Layer.md) in interface [`Layer`](../core/Layer.md)

      Overrides:
      [`render`](BasicLayer.md) in class [`BasicLayer`](BasicLayer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### addEditChangeListener

          public void addEditChangeListener(EditChangeListener l)

      Adds a change listener to listen for editing changes.
      Specified by:
      [`addEditChangeListener`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

      Parameters:
      `l` -

    <!-- -->

    - #### removeEditChangeListener

          public void removeEditChangeListener(EditChangeListener l)

      Specified by:
      [`removeEditChangeListener`](../core/EditableLayer.md) in interface [`EditableLayer`](../core/EditableLayer.md)

    <!-- -->

    - #### getCurrentDeletedFeatures

          public AbstractFeature[] getCurrentDeletedFeatures()

    <!-- -->

    - #### setToUpdate

          public void setToUpdate()

    <!-- -->

    - #### transformFeatures

          public abstract int transformFeatures(GeoObject[] features,
                                                java.awt.geom.AffineTransform at)
                                         throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isSelected

          public boolean isSelected(GeoObject obj)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Checks if an object is selected
      Specified by:
      [`isSelected`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:
      true if the provided object is selected

    <!-- -->

    - #### clearSelection

          public boolean clearSelection()

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Clears all selected objects
      Specified by:
      [`clearSelection`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:
      true if changes where made

    <!-- -->

    - #### numSelected

          public int numSelected()

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Returns the number of selected objects
      Specified by:
      [`numSelected`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:
      the number of selected objects

    <!-- -->

    - #### getSelection

          public java.util.List<GeoObject> getSelection()

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Returns all selected objects
      Specified by:

      [`getSelection`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### getSelection

          public java.util.List<GeoObject> getSelection(GeoObject obj)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object
      Specified by:

      [`getSelection`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### setSelection

          public boolean setSelection(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Clears selection before setting the provided objects as selected
      Specified by:

      [`setSelection`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### select

          public boolean select(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Adds the provided objects to the selection list
      Specified by:

      [`select`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### unselect

          public boolean unselect(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Removes the provided objects from the selection list
      Specified by:

      [`unselect`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

      Returns:

    <!-- -->

    - #### addSelectionListener

          public void addSelectionListener(SelectionListener l)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Adds a SelectionListener
      Specified by:
      [`addSelectionListener`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

    <!-- -->

    - #### removeSelectionListener

          public void removeSelectionListener(SelectionListener l)

      Description copied from interface: [`SelectableLayer`](../core/SelectableLayer.md)
      Removes the given SelectionListener
      Specified by:
      [`removeSelectionListener`](../core/SelectableLayer.md) in interface [`SelectableLayer`](../core/SelectableLayer.md)

    <!-- -->

    - #### setHover

          public boolean setHover(java.util.List<GeoObject> objs)

      Description copied from interface: [`HoverableLayer`](../core/HoverableLayer.md)
      A list of geo-objects being hovered
      Specified by:
      [`setHover`](../core/HoverableLayer.md) in interface [`HoverableLayer`](../core/HoverableLayer.md)

      Returns:
      true if the objects were hovered

    <!-- -->

    - #### clearHover

          public boolean clearHover()

      Description copied from interface: [`HoverableLayer`](../core/HoverableLayer.md)
      Removes the hovering state from all the geo-objects
      Specified by:

      [`clearHover`](../core/HoverableLayer.md) in interface [`HoverableLayer`](../core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### getHover

          public java.util.List<GeoObject> getHover()

      Description copied from interface: [`HoverableLayer`](../core/HoverableLayer.md)
      Returns all the geo-object that are being hovered
      Specified by:

      [`getHover`](../core/HoverableLayer.md) in interface [`HoverableLayer`](../core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### isHover

          public boolean isHover(GeoObject obj)

      Description copied from interface: [`HoverableLayer`](../core/HoverableLayer.md)
      Returns true if the geo-object is being hovered
      Specified by:

      [`isHover`](../core/HoverableLayer.md) in interface [`HoverableLayer`](../core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### numHovered

          public int numHovered()

      Description copied from interface: [`HoverableLayer`](../core/HoverableLayer.md)
      Returns the number of geo-objects that are being hovered
      Specified by:

      [`numHovered`](../core/HoverableLayer.md) in interface [`HoverableLayer`](../core/HoverableLayer.md)

      Returns:

    <!-- -->

    - #### stateChanged

          public void stateChanged(javax.swing.event.ChangeEvent e)

      Specified by:
      `stateChanged` in interface `javax.swing.event.ChangeListener`

    <!-- -->

    - #### getDataSource

          public AbstractDataSource getDataSource()

    <!-- -->

    - #### setDataSource

          public void setDataSource(AbstractDataSource dataSource)

    <!-- -->

    - #### setHighliteGeometries

          public void setHighliteGeometries(JGeometry[] geoms)

      Parameters:
      `geoms` -

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
- [Next Class](BasicLayer.md)

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
