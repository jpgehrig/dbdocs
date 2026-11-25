------------------------------------------------------------------------

#### new Map(container, options)

OM.Map is the main class of the Oracle Maps V2 API. It is associated with
a specific map DIV and contains various map layers, controls and tools.


Each Map instance must have a map universe which defines the overall
map bounds and zoom level details (such as number of zoom levels and map
scale at each zoom level). The universe can be modified or switched on the fly,
such as when switching from a cached map (or map tile layer) to a purely
thematic map (with no background map tiles).


The Map instance may fire various events througout its life cycle. These events
are typically instances of the class [`OM.event.MapEvent`](OM.event.MapEvent.md) or [`OM.event.MouseEvent`](OM.event.MouseEvent.md).
Applications can register listeners, or handlers, on these events to hook in specific application logic, such as
performing custom actions just before the map is to be zoomed in. For the type of
map events that can be listend on, check the event type constants defined in the
class [`OM.event.MapEvent`](OM.event.MapEvent.md) and [`OM.event.MouseEvent`](OM.event.MouseEvent.md).



Typically an application will create a Map instance, add a tile layer
that serves as the background map, and one or more interactive vector layers.
Vector layers can get their data from a variety of sources such as the database or service feeds.
These are defined in the VectorLayer's API documentation.


A vector layer has an associated rendering style. These can be predefined or
created dynamically in the client code. You can then assign
them to the vector layers to change how geographic features are rendered.
You can also specify the special styles to be used on mouse-over/hover,
or when a feature is selected/highlighted.

##### Parameters:

| Name        | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `container` | div    | The map container div.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `options`   | Object | This is an object literal that specifies the initial map options. It can have the following properties.<br>Note: Only one of the zoomLevel, scale or resolution properties is needed to defined the initial map display scale.<br><br>• mapviewerURL {String} Optional. The default value is derived from the host name of the application URL.<br>• universe {OM.universe.Universe} Required for thematic map (i.e. no tile layer used). Optional otherwise.<br>The default map universe is derived from the tile layer configuration if the map has at least one tile layer.<br>• disableOverviewMap {boolean}. Whether the map is initialized with or without an overview map panel.<br>If it's true, the overview map will not display even on invoking showOverviewMap().<br>The default value is true.<br>• wraparound {Boolean} Optional. If true then wraparound is enabled on the background map tile layer.<br>Default is false and wraparound is not enabled.<br>• <br><br>• useRTree {Boolean} Optional. Specify whether an in-memory R-Tree should be used to index features in vector layers.<br>This can also be set/reset using OM.gv.setUseRTree(flag)<br>• autoLoadCss {Boolean} indicates whether the oraclemapsv2.css file should be loaded automatically by this<br>Map instance. Default is true. Set this to false if oraclemapsv2.css is loaded explicity using a stylesheet<br>link in the page. If this attribute is not specified then the css file will be auto loaded. (Added since 12.2.1.3)<br> |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

##### Returns:

The newly created Map object.

Type
OM.Map

### Methods

------------------------------------------------------------------------

#### addLayer(layer \[, type\], layer_idx)

Add a layer to the map. This layer name must be unique. If a layer with the same name already exists, then this layer won't be added into the map.

##### Parameters:

| Name        | Type                                | Argument         | Description                                                                                                                                     |
|-------------|-------------------------------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `layer`     | [OM.layer.Layer](OM.layer.Layer.md) |                  | A map layer object.                                                                                                                             |
| `type`      | String                              | \<optional\><br> | An optional String parameter that specifies the category of the vectorlayer, this category name will be displayed in<br>the layer control list. |
| `layer_idx` | number                              |                  | The index layer to be inserted at.                                                                                                              |

##### Returns:

The index the layer at which the layer was inserted.

Type
number

------------------------------------------------------------------------

#### addMagnifier(magnifier)

Add a magnifier tool to map.

##### Parameters:

| Name        | Type                                            | Description                         |
|-------------|-------------------------------------------------|-------------------------------------|
| `magnifier` | [OM.control.Magnifier](OM.control.Magnifier.md) | The magnifier tool instance to add. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### addMapDecoration(mapDeco)

Add a MapDecoration object to the map. A map decoration is
a piece of user supplied HTML content (such as a map title string or a custom built
map control) that can be displayed on top of the map.
Once added, a map decoration will not move with the map when the map is recentered.

The map decoration can be set to be collapsible so that it can be minimized when
the user clicks on the minimize button. By default, a map decoration is
not collapsible.



The map decoration can be set to be draggable so that the user can move
the map decoration inside the map window by dragging it using the mouse.

##### Parameters:

| Name      | Type                                                    | Description                                   |
|-----------|---------------------------------------------------------|-----------------------------------------------|
| `mapDeco` | [OM.control.MapDecoration](OM.control.MapDecoration.md) | A MapDecoration object to be added to the map |

##### Returns:

Type
null

------------------------------------------------------------------------

#### addNavigationPanelBar()

Add a navigation panel to the map.

##### Returns:

Type
null

------------------------------------------------------------------------

#### addScaleBar()

Add a scalebar to map.

##### Returns:

Type
null

------------------------------------------------------------------------

#### addScaleBarDiv(scaleDiv, scale)

Add scalebar bar to a specified div.

##### Parameters:

| Name       | Type                                          | Description                            |
|------------|-----------------------------------------------|----------------------------------------|
| `scaleDiv` | div                                           | A div used to contain scale bar value. |
| `scale`    | [OM.control.ScaleBar](OM.control.ScaleBar.md) | The scale instance from the map.       |

##### Returns:

Type
void

------------------------------------------------------------------------

#### addScaleBarUnit(unitDiv, scale)

Add scalebar unit to a specified div.

##### Parameters:

| Name      | Type                                          | Description                            |
|-----------|-----------------------------------------------|----------------------------------------|
| `unitDiv` | div                                           | A div used to contain scale bar value. |
| `scale`   | [OM.control.ScaleBar](OM.control.ScaleBar.md) | The scale instance from the map.       |

##### Returns:

Type
null

------------------------------------------------------------------------

#### addScaleBarValue(valueDiv, scale)

Add scalebar value to a specified div.

##### Parameters:

| Name       | Type                                          | Description                            |
|------------|-----------------------------------------------|----------------------------------------|
| `valueDiv` | div                                           | A div used to contain scale bar value. |
| `scale`    | [OM.control.ScaleBar](OM.control.ScaleBar.md) | The scale instance from the map.       |

##### Returns:

Type
null

------------------------------------------------------------------------

#### addToolBar(toolbar)

Add a toolbar to map.

##### Parameters:

| Name      | Type               | Description                             |
|-----------|--------------------|-----------------------------------------|
| `toolbar` | OM.control.Toolbar | The toolbar instance to add to the map. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### closeInfoWindows()

Close all info-windows on the map.

##### Returns:

Type
null

------------------------------------------------------------------------

#### destroyMap()

Destroy the map and all layers.

##### Returns:

Type
void

------------------------------------------------------------------------

#### displayInfoWindow(point, htmlString, options)

Display an information window on the map at a specified location.
The content of the information window is defined by an HTML string. The user can
close the information window by clicking the close ("X") button inside the window.

##### Parameters:

| Name         | Type                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|--------------|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `point`      | [OM.geometry.Point](OM.geometry.Point.md) | A point geometry object that specifies the location of<br>the info window on the map. The point is in the map coordinate system. e.g. if<br>the map (or tile layer) is in WGS84 (SRID 8307) then the point's SRID should also be 8307.<br>If the width and height are omitted, the info window will automatically sized<br>to best fit the content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `htmlString` | string                                    | An HTML content string to be displayed inside the information window.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `options`    | Object                                    | An object, or object literal, specifying various info-window properties.<br>• ellipsis {boolean} Whether to truncate a title which will not fit and display ... at the end. Default is true.<br>• width {number} The width of the information window in pixels.<br>• height {number} The height of the information window in pixels.<br>• title {string} An optional string parameter that specifies the info window title string.<br>• infoWindowStyle {Object} The css object that specifies the custom infoWindow style parameters<br>• titleStyle {Object} The css object that specifies the infoWindow title style parameters<br>• contentStyle {Object} The css object that specifies the infoWindow content style parameters<br>• tailStyle {Object} The object that specifies the infoWindow tail style parameters<br>The parameters object contains 2 attributes.<br><br>• offset {number} An integer-valued parameter defining the offset of tail.<br>• background {string} A string parameter defining the background of tail<br>• <br><br>• closeButtonStyle {Object} The object that specifies the infoWindow close button style parameters<br>The parameters object contains 6 attributes.<br><br>• mouseOutButton {object} This parameter defining the mouse out image src of the close button.<br>The parameters object contains 1 attribute.<br><br>• src {string} A parameter defining the mouse out image src of the close button.<br>• <br><br>• mouseOverButton {object} This parameter defining the mouse over image src of the close button.<br>The parameters object contains 1 attribute.<br><br>• src {string} A parameter defining the mouse over image src of the close button.<br>• <br><br>• width {number} An integer-valued parameter defining the width of close button.<br>• height {number} An integer-valued defining the height of close button.<br>• xOffset {number} An integer-valued defining the xOffset of close button.<br>• yOffset {number} An integer-valued defining the yOffset of close button.<br>• <br> |

##### Returns:

Type
void

------------------------------------------------------------------------

#### displayTabbedInfoWindow(point, tabs, options)

Display a tabbed information window on the map at a specified location.
The content of the information window is defined by an HTML string. The application user can
close the information window by clicking the close ("X") button inside the window.

##### Parameters:

| Name      | Type                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-----------|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `point`   | [OM.geometry.Point](OM.geometry.Point.md) | A point geometry object that specifies the location of<br>the info window on the map. The point is in the map coordinate system. e.g. if<br>the map (or tile layer) is in WGS84 (SRID 8307) then the point's SRID should also be 8307.<br>If the width and height are omitted, the info window will automatically sized<br>to best fit the content.                                                                                                                                                                                                                                                                                |
| `tabs`    | Array                                     | An array that specifies each tab's title and content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `options` | Object                                    | An object, or object literal, specifying various info-window properties.<br>• activeIndex {number} It indicates which tab is active. The default value is 0, the first tab.<br>• width {number} The width of the information window in pixels.<br>• height {number} The height of the information window in pixels.<br>• tailStyle {Object} The object that specifies the infoWindow tail style parameters<br>The parameters object contains 2 attributes.<br><br>• offset {number} An integre-valued parameter defining the offset of tail.<br>• background {string} A string parameter defining the background of tail<br>• <br> |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableDoubleClick(enabled)

Enable or disable mouse double-click. When mouse double-click is enabled,
the user can zoom in by double click on map.

##### Parameters:

| Name      | Type    | Description                                                                  |
|-----------|---------|------------------------------------------------------------------------------|
| `enabled` | Boolean | If true then mouse double clicking is enabled, if false then it is disabled. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableInfoWindowEventPropagation(enabled)

Enable event propagation from the info window. When enabled, events such as mouse clicks
and keyboard strokes are propagated, to other event listeners in the map client instance, after they are handled
inside the info window. When event propagation is diabled, events are trapped
inside the info window and not propapated outside. The latter is usally
preferred when the info window needs to handle some events that should only
occur within the map decoration itself. By default, event propagation for info
window is disabled.

##### Parameters:

| Name      | Type    | Description                                                                    |
|-----------|---------|--------------------------------------------------------------------------------|
| `enabled` | boolean | true (enable event propagation) or false (disable event propagation. default). |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableMapDrag(enabled)

Enable or disable map dragging (panning).

##### Parameters:

| Name      | Type    | Description                                                     |
|-----------|---------|-----------------------------------------------------------------|
| `enabled` | Boolean | If true then map drag is enabled, if false then it is disabled. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableMapWraparound(enabled)

Enable or disable map wraparound.

##### Parameters:

| Name      | Type    | Description                                                       |
|-----------|---------|-------------------------------------------------------------------|
| `enabled` | Boolean | If true then wraparound is enabled, if false then it is disabled. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableMapZoom(enabled)

Enable or disable map zoom.

##### Parameters:

| Name      | Type    | Description                         |
|-----------|---------|-------------------------------------|
| `enabled` | Boolean | If false, the map cannot be zoomed. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableMouseWheelZooming(enabled)

Enable or disable mouse wheel zooming. When mouse wheel zooming is enabled,
the user can zoom in by scrolling the mouse wheel forward and zoom out
by scrolling the mouse wheel backward.

##### Parameters:

| Name      | Type    | Description                                                                |
|-----------|---------|----------------------------------------------------------------------------|
| `enabled` | Boolean | If true then mouse wheel zooming is enabled, if false then it is disabled. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableMultiLayerInfoWindow(enabled)

Enable or disable multiple vector layer infowindow. When it is set to false, the default setting,
only one feature's info is shown for a mouse event if ther eare overlapping features; when it is set to true, all
overlapping features' info in one vector layer or multiple vector layers is shown.

##### Parameters:

| Name      | Type    | Description                                                                                                        |
|-----------|---------|--------------------------------------------------------------------------------------------------------------------|
| `enabled` | Boolean | A boolean value to enable (true) or disable (false) of showing<br>multiple vector layer features in an infowindow. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableURLDragDrop(enable, options)

Enable drag-n-drop of a datapack URL onto a map. If the URL is valid, a datapack layer
will be created and added to map.

##### Parameters:

| Name      | Type    | Description                                                                                                                                                                                                                                                                                                                                                                            |
|-----------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enable`  | Boolean | Enable/Disable URL drag-n-drop.                                                                                                                                                                                                                                                                                                                                                        |
| `options` | Object  | An object which may have following properties.<br>• style {OM.style.Style} a style which is used to render the layer. Use a color style (OM.style.Color)<br>if the layer can contain a mix of points, lines, and polygons.<br>• zoomToTheme {Boolean} If true the map center and zoom level are automatically adjusted so that all<br>features can be displayed inside the map window. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### enableZoomAnimation(enabled)

Enable or disable zoom animation.
If enabled is true an animation effect is used on zoom in or out.

##### Parameters:

| Name      | Type    | Description                                                             |
|-----------|---------|-------------------------------------------------------------------------|
| `enabled` | boolean | A boolean value which indicates whether or not to enable zoom animation |

##### Returns:

Type
null

------------------------------------------------------------------------

#### forceBuiltinCopyright(layer, evtPkg)

Adds the built-in copyright for Oracle hosted tile layers.

##### Parameters:

| Name     | Type   | Description                                   |
|----------|--------|-----------------------------------------------|
| `layer`  | Object | The tile layer that just got added to the map |
| `evtPkg` | Object | The OM event package                          |

------------------------------------------------------------------------

#### getAbsoluteCursorLocation()

Get the absolute ground coordinate for the current cursor position

##### Returns:

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getCursorLocation()

Get the ground coordinate for the current cursor position

##### Returns:

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getFeatureLayers()

Return an array containing all feature layers added to the map.
These are typically OM.layer.VectorLayer instances.

##### Returns:

An array of layers. Usually all added OM.layer.VectorLayer instances.

Type
Array

------------------------------------------------------------------------

#### getFlattenedCanvas(callBack, width, height, options)

Get the map content as an image

##### Parameters:

| Name       | Type     | Description                                                                                                                                                                                                                                     |
|------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `callBack` | function | The callback function to which the image will be passed.                                                                                                                                                                                        |
| `width`    | number   | The width of the map image in pixels. If omitted, the map image width<br>will be set to the width of the current map div container.                                                                                                             |
| `height`   | number   | The height of the map image in pixels. If omitted, the map image<br>height will be set to the height of the current map div container.                                                                                                          |
| `options`  | Object   | An object literal for specifying which map decorations (in this version, only scaleBar is supported)<br>should or should not be displayed; it may all specify a datasource name when applicable, e.g.:<br>{scaleBar:true, dataSource:"MVDEMO"}. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### getLayerByName(name)

Find a specific layer by name

##### Parameters:

| Name   | Type   | Description                 |
|--------|--------|-----------------------------|
| `name` | string | The name of a desired layer |

##### Returns:

The specified layer or null if no such layer exists

Type
[OM.layer.Layer](OM.layer.Layer.md)

------------------------------------------------------------------------

#### getMapAsServerImage(callBack, width, height, options)

Get the map content as an image URL

##### Parameters:

| Name       | Type     | Description                                                                                                                                                                                                                                    |
|------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `callBack` | function | The callback function to which the image URL will be passed.                                                                                                                                                                                   |
| `width`    | number   | The width of the map image. If omitted, the map image width<br>will be set to the width of the current map div container.                                                                                                                      |
| `height`   | number   | The height of the map image. If omitted, the map image<br>height will be set to the height of the current map div container.                                                                                                                   |
| `options`  | Object   | An object literal for specifying which map decorations (in this version, only scaleBar is supported)<br>should or should not be displayed; it may all specify a datasource name when applicable, eg.:<br>{scaleBar:true, dataSource:"MVDEMO"}. |

##### Returns:

void

------------------------------------------------------------------------

#### getMapAsSVG(callBack)

Get the map content as an SVG document.

##### Parameters:

| Name       | Type     | Description                                                              |
|------------|----------|--------------------------------------------------------------------------|
| `callBack` | function | The callback function to which the SVG document (string) will be passed. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### getMapAsXML(format, callBack, width, height, options)

Get the XML map request for the current map. The xml map request
can be used to render the current map as a single map image.

##### Parameters:

| Name       | Type     | Description                                                                                                                                                                                                                                    |
|------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `format`   | String   | The desired map image format (e.g. PNG or PNG_URL).                                                                                                                                                                                            |
| `callBack` | function | The callback function to which the will be passed.                                                                                                                                                                                             |
| `width`    | number   | The width of the map image in pixels. If omitted, the map image width<br>will be set to the width of the current map div container.                                                                                                            |
| `height`   | number   | The height of the map image in pixels. If omitted, the map image<br>height will be set to the height of the current map div container.                                                                                                         |
| `options`  | Object   | An object literal for specifying which map decorations (in this version, only scaleBar is supported)<br>should or should not be displayed; it may all specify a datasource name when applicable, eg.:<br>{scaleBar:true, dataSource:"MVDEMO"}. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### getMapCenter()

Get map center

##### Parameters:

| Name   | Type                                              | Description                                                                                                                                                                                                                      |
|--------|---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `geo.` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | A Rectangle defining the expected bounds of the displayed map.<br>If the param is not null, zoom to the specified rectangular area first and then return the map center.<br>If the param is null, return the current map center. |

##### Returns:

the map center point

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getMapContext()

Return the map context.

##### Returns:

The map context

Type
[OM.MapContext](OM.MapContext.md)

------------------------------------------------------------------------

#### getMapScale()

Get the current map scale. Assumes a ration scale, i.e. grounds units per screen unit.

##### Returns:

scale. The current map scale.

Type
number

------------------------------------------------------------------------

#### getMapWindowBoundingBox()

Get the bounds (bounding box) for the current map window.

##### Returns:

the current map bounds

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getMapZoomLevel()

Get map zoom level

##### Parameters:

| Name   | Type                                              | Description                                                                                                                                                                                                                              |
|--------|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `geo.` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | A Rectangle defining the expected bounds of the displayed map.<br>If the param is not null, zoom to the specified rectangular area first and then return the map zoom level.<br>If the param is null, return the current map zoom level. |

##### Returns:

zoom The current zoom level of the map

Type
number

------------------------------------------------------------------------

#### getMaskOutInfoWindow()

Get the maskOutInfoWindow flag. When it is true (it may have been set to true for cases
such as a redline tool is selected), mouse events will not trigger the info window.

##### Returns:

true or false

Type
Boolean

------------------------------------------------------------------------

#### getScreenLocation(point)

Get the screen location for the specified ground coordinate

##### Parameters:

| Name    | Type                                      | Description                                   |
|---------|-------------------------------------------|-----------------------------------------------|
| `point` | [OM.geometry.Point](OM.geometry.Point.md) | The geometry point for the ground coordinates |

##### Returns:

with x and y members

Type
Object

------------------------------------------------------------------------

#### getScreenPointLocation(x, y, isAbsolute)

Get the ground coordinate for the specified screen location

##### Parameters:

| Name         | Type    | Description                     |
|--------------|---------|---------------------------------|
| `x`          | number  | The X ordinate in screen pixels |
| `y`          | number  | The Y ordinate in screen pixels |
| `isAbsolute` | boolean | Default is false                |

##### Returns:

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getTileLayers()

Get the tile layers in a map. Returns an array containing all tile layers added to the map.
These are typically tile layer instances within a map div.

##### Returns:

An array of OM.layer. Usually all added OM.layer.TileLayer instances.

Type
Array

------------------------------------------------------------------------

#### getUniverse()

Returns the map universe. If the map universe is not set by setUniverse,
this method returns a copy of the universe of the first visible tile layer if there is any.

##### Returns:

Type
[OM.universe.Universe](OM.universe.Universe.md)

------------------------------------------------------------------------

#### hideOverviewMap()

Hide the existing Overview map

##### Returns:

Type
null

------------------------------------------------------------------------

#### init()

Initialize the map and display it.It needs to be called only once.
This is the same as MVMapView.display().

##### Returns:

Type
void

------------------------------------------------------------------------

#### isMVMapDecorationElem(e)

check if the input element is a MapViewer map decoration (such as copyright)

##### Parameters:

| Name | Type | Description           |
|------|------|-----------------------|
| `e`  |      | DOM element to check. |

##### Returns:

true if the element is a map decoration; false otherwise

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### pan()

Pan (move) the map by the specified X and Y offset.
Note: both zoom and pan operations will always consult the Universe to determine the exact behavior.
For instance, if the Universe contains pre-defined zoom levels, then zoom in/out will be based on the zoom levels.
If there is no zoom level (tile-layer) defined in the Universe, then zoom in/out will be simply
based on a default scaling behaviour, such as increasing/reducing map size by a factor of 2.

##### Parameters:

| Name         | Type    | Description                                                              |
|--------------|---------|--------------------------------------------------------------------------|
| `xOffset.`   | number  | The X offset in screen pixels.                                           |
| `yOffset.`   | number  | The Y offset in screen pixels.                                           |
| `smoothPan.` | Boolean | Indicates whether the map smooth/animated panning effect should be used. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### print()

Print the current map content

##### Returns:

.

Type
void

------------------------------------------------------------------------

#### redrawMap()

Redraw map and each layer. Simply re-renders existing layer data, i.e. without reload.
Use refreshMap() instead to reload the data before redrawing.

##### Returns:

Type
void

------------------------------------------------------------------------

#### refreshMap()

Refresh the map and all layers. Forces layers to reload data.

##### Returns:

Type
void

------------------------------------------------------------------------

#### removeAllFeatureLayers()

Remove all vector feature layers

##### Returns:

Type
null

------------------------------------------------------------------------

#### removeLayer(layer)

Remove a specified layer from the map. The layer-deleted event will be fired.

##### Parameters:

| Name    | Type                                | Description          |
|---------|-------------------------------------|----------------------|
| `layer` | [OM.layer.Layer](OM.layer.Layer.md) | The layer to remove. |

##### Returns:

The layer index

Type
number

------------------------------------------------------------------------

#### removeMapDecoration(mapDeco)

Remove a map decoration from the current map.

##### Parameters:

| Name      | Type                                                    | Description                            |
|-----------|---------------------------------------------------------|----------------------------------------|
| `mapDeco` | [OM.control.MapDecoration](OM.control.MapDecoration.md) | The MapDecoration object to be removed |

##### Returns:

Type
null

------------------------------------------------------------------------

#### removeToolbar(toolbar)

Remove a toolbar from map

##### Parameters:

| Name      | Type               | Description            |
|-----------|--------------------|------------------------|
| `toolbar` | OM.control.Toolbar | The toolbar to remove. |

------------------------------------------------------------------------

#### setEnabledZoomLevels(levels)

Specify a subset of the zoom levels defined
in TileLayerConfig that will be enabled and visible. By default all zoom levels defined in
the TileLayerConfig object are enabled and visible on the map.

##### Parameters:

| Name     | Type  | Description                      |
|----------|-------|----------------------------------|
| `levels` | Array | An integer array of zoom levels. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setHomeMap(center, zoomlevel)

Set the home map location and zoom level. When the
home map location and zoom level is set, the user can click on the center
button of the navigation panel bar to bring the map back to the initial location
and zoom level that were set on initialization.

##### Parameters:

| Name        | Type                                      | Description                                            |
|-------------|-------------------------------------------|--------------------------------------------------------|
| `center`    | [OM.geometry.Point](OM.geometry.Point.md) | The point specifies the home/original center.          |
| `zoomlevel` | number                                    | An integer that specifies the home/original zoom level |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setInfoWindowStyle(options)

Set the info-window style's properties.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object, or object literal, specifying various info-window properties.<br>• ellipsis {boolean} Whether to truncate a title which will not fit and display ... at the end. Default is true.<br>• width {number} The width of the information window in pixels.<br>• height {number} The height of the information window in pixels.<br>• infoWindowStyle {Object} The css object that specifies the custom infoWindow style parameters<br>• titleStyle {Object} The css object that specifies the infoWindow title style parameters<br>• contentStyle {Object} The css object that specifies the infoWindow content style parameters<br>• tailStyle {Object} The object that specifies the infoWindow tail style parameters<br>The parameters object contains 2 attributes.<br><br>• offset {number} An integer-valued parameter defining the offset of tail.<br>• background {string} A string parameter defining the background of tail<br>• <br><br>• closeButtonStyle {Object} The object that specifies the infoWindow close button style parameters<br>The parameters object contains 6 attributes.<br><br>• mouseOutButton {object} This parameter defining the mouse out image src of the close button.<br>The parameters object contains 1 attribute.<br><br>• src {string} A parameter defining the mouse out image src of the close button.<br>• <br><br>• mouseOverButton {object} This parameter defining the mouse over image src of the close button.<br>The parameters object contains 1 attribute.<br><br>• src {string} A parameter defining the mouse over image src of the close button.<br>• <br><br>• width {number} An integer-valued parameter defining the width of close button.<br>• height {number} An integer-valued defining the height of close button.<br>• xOffset {number} An integer-valued defining the xOffset of close button.<br>• yOffset {number} An integer-valued defining the yOffset of close button.<br>• <br> |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setMapCenter(p, smooth)

Set the map center

##### Parameters:

| Name     | Type                                      | Description                            |
|----------|-------------------------------------------|----------------------------------------|
| `p`      | [OM.geometry.Point](OM.geometry.Point.md) | The point to set as the map center     |
| `smooth` | Boolean                                   | If true then use a smooth pan or zoom. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMapCenterAndZoomLevel(p, zoom, smoothPan)

Set the map center and zoom level.

##### Parameters:

| Name        | Type                                      | Description                           |
|-------------|-------------------------------------------|---------------------------------------|
| `p`         | [OM.geometry.Point](OM.geometry.Point.md) | The desired center point of the map   |
| `zoom`      | Number                                    | The desired zoom level of the map     |
| `smoothPan` | Boolean                                   | Whether to use a smooth animated pan. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setMapDataBounds(geomRect)

Set map bounds. When the map is panned, the map center is checked against this bounding box.
The constraint is that the map center is not allowed to fall outside of the bounds.

##### Parameters:

| Name       | Type                                              | Description            |
|------------|---------------------------------------------------|------------------------|
| `geomRect` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | A rectangular geometry |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setMapScale(scale)

Set map scale. Used for a map without predefined zoom levels

##### Parameters:

| Name    | Type  | Description                                                                                                                                |
|---------|-------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `scale` | float | The map scale to use. Assumes a ratio scale. For instance, if the desired scale is 1:10000 then<br>set 10000 as the scale parameter value. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMapZoomLevel(zoom)

Set map zoom level

##### Parameters:

| Name   | Type   | Description                                                                   |
|--------|--------|-------------------------------------------------------------------------------|
| `zoom` | number | The zoom level to set for the map. The map will zoom in or out to this level. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMaskOutInfoWindow(flag)

Set the maskOutInfoWindow flag. When set to true, such as when a redline tool is selected,
mouse events will not trigger the info window.

##### Parameters:

| Name   | Type    | Description                  |
|--------|---------|------------------------------|
| `flag` | Boolean | Boolean value, true or false |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMouseCursorStyle(cursorStyle, cursorType)

Set the mouse cursor style when the mouse is inside the map
container and not over any map content other than map tiles.

##### Parameters:

| Name          | Type   | Description                                                                                                                                                                                                                                                                                                                |
|---------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cursorStyle` | String | A string that specifies the cursor style to<br>be used, which must be one of the standard CSS cursor style names<br>such as "crosshair", "pointer" and "move".                                                                                                                                                             |
| `cursorType`  | String | A string that specifies when the cursor style<br>should be used. Its value can be one of the following:<br><br>• <br>default {string} Cursor style to be used when the mouse is on the map<br>and no mouse key has been pressed.<br><br>• <br>dragging {string} Cursor style to be used when the map is being dragged.<br> |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setMouseWheelZoomBehavior(One)

Set the desired behavior when zooming with the mouse wheel. Posible parameters are one of
OM.Map.ZOOM_KEEP_MOUSE_POINT (the default behavior),
OM.Map.ZOOM_CENTER_ON_MOUSE, or OM.Map.ZOOM_KEEP_CENTER.

##### Parameters:

| Name  | Type   | Description                      |
|-------|--------|----------------------------------|
| `One` | Number | of the three parameter contants. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setOverviewMapOptions(options)

Set the options for the overview window.
The overview window is created when the map is initialized. However you can set various properties--
such as visibility, scale, rectangle and cursor style-- using this method.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object, or object literal, with the following properties:<br>• {number} scaleRatio Must be greater than 1. scaleRatio means that if the resolution of the main map is X units per pixel<br>then the resolution of the Overview map will be scaleRatio\*X units per pixel. E.g. if the main map is at 1Km/pixel and the<br>scaleRatio is 2 then the Overview map will be at 2Km per pixel. Similarly if the main map is at scale 1:25000 and the<br>scaleRatio is 2 then the Overview map will be at 1:50000.<br>• {OM.layer.Layer} overviewLayer The layer object that will be displayed in the overview window<br>• {object} panelOptions An object, or literal, which specifies the rectangle and cursor style<br>• {OM.style.Style} style A color, or area, style used in displaying the current extent, or bounds, of the main map<br>• {String} defaultCursorStyle The cursor style used when the mouse is inside this rectangular area<br>• {String} draggingCursorStyle The cursor style used when drag rectangular area<br>• {Boolean} display If true, show overview map panel. If false, no overview map panel is displayed<br>• {Boolean} collapse If true the overview map panel is collapsible. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setTooltipStyle(options)

Set the tooltip style. This affects tooltips displayed on all map controls and layers.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | Specifies the style properties. It may have the following attributes:<br><br>• background {String}. The background style such as \#rrggbbaa. Default value is "#ffffe1"<br>• opacity {Number} A floating number between 0 and 1 indicating background opacity<br>• borderColor {String}. The stroke color of the border<br>• borderThickness {number} the width or thickness of the border<br>• rx {number} rounded corner size x; 0 if prefer square corners<br>• ry {number} rounded corner size y; 0 if perfer square corners<br>• padding {Object}. Specify the padding (in pixels) between the background of the tooltip and its content.<br>• textColor {String}: The color of the text<br>• fontWeight {String} The font weight for the tooltip text<br>• fontSize {number} The font size for the tooltip text<br>• titleStyle {OM.style.Text} The style for the tooltip titles<br>• headerStyle {OM.style.Text} The style for the tooltip headers<br>• contentStyle {OM.style.Text} The style for the tooltip content |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setUTFGridMouseEType(triggerType)

set the UTFGrid enabled layers' trigger type.

##### Parameters:

| Name          | Type | Description                                                                                        |
|---------------|------|----------------------------------------------------------------------------------------------------|
| `triggerType` |      | An OM.event.MouseEvent.MOUSE_CLICK, or MOUSE_OVER type. Default is OM.event.MouseEvent.MOUSE_CLICK |

------------------------------------------------------------------------

#### setVectorLayerInfoWindowTrigger(evtType)

Set the vector layer infowindow trigger. Two built-in mouse event, OM.event.MouseEvent.MOUSE_CLICK and
OM.event.MouseEvent.MOUSE_OVER are supported. Default is OM.event.MouseEvent.MOUSE_CLICK.

##### Parameters:

| Name      | Type                                          | Description           |
|-----------|-----------------------------------------------|-----------------------|
| `evtType` | [OM.event.MouseEvent](OM.event.MouseEvent.md) | The mouse event type. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setZoomLevelRange(minLevel, maxLevel)

Set the min and max zoom levels.

##### Parameters:

| Name       | Type    | Description                                                                                                                                                                                                                           |
|------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `minLevel` | Integer | The minimum zoom level allowed for the map.                                                                                                                                                                                           |
| `maxLevel` | Integer | The maximum zoom level allowed for the map. Optional, the default is the maximum zoom<br>level defined in the map's universe.<br>The min and max zoom levels should be within the valid map zoom level range defined in its universe. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### showOverviewMap()

Show the existing Overview map

##### Returns:

Type
null

------------------------------------------------------------------------

#### zoomIn()

Zoom in by one level, i.e. current zoom level + 1

##### Returns:

Type
void

------------------------------------------------------------------------

#### zoomOut()

Zoom out by one level, i.e. current zoom level - 1

##### Returns:

void

------------------------------------------------------------------------

#### zoomToExtent(p)

Zoom to the level required to display the expected rectangular area or bounds of the map.
The bounds will be fully contained in the current map extent, so area outside the defined rectangle may also
be displayed depending on the predefined zoom levels.

##### Parameters:

| Name | Type                                              | Description                                                    |
|------|---------------------------------------------------|----------------------------------------------------------------|
| `p`  | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | A Rectangle defining the expected bounds of the displayed map. |

##### Returns:

Type
void
