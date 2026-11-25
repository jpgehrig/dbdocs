------------------------------------------------------------------------

#### new WMTSTileLayer(name, options)

This class represents the Oracle Map tile layer. It extends TileLayer with
WMTS related parameters.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | String | A unique name for WMTS tile layer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `options` | Object | A JSON object that specifies WMTS tile layer related parameters. It may have the following attributes.<br><br>• url {String}: The WMTS server URL for fetching the capabilites xml document. The URL may point to<br>any WMTS compliant server.<br>For example, url:"http://server.mygisonline.com/MyGIS/rest/services/World_Topo_Map/MapServer/wmts",<br>or url:"http://localhost:8080/mapviewer/wmts/WMTSCapabilities.xml".<br>Alternatively, you may download the XML document and save it into a folder which is accessible by your application.<br>For example, url:"../wmtstilelayers/WMTSCapabilities.xml"<br>• layerID {String}: The WMTS tile layer's ID.<br>For example: layerID: 'World_Topo_Map' or layerID: 'MVDEMO2:WMTS_E4'.<br>• tileMatrixSetID {String}: The ID for the tile matrixset. For example, tileMatrixSetID:"default028mm", or tileMatrixSetID:"MVDEMO2:WMTS_E4:EPSG:3857".<br>• getTileTemplate {String}: Optional. The template for fetching a map tile.<br>For example: getTileTemplate:"http://?SERVICE=WMTS&REQUEST=GetTile&VERSION=1.0.0&LAYER=ORTOFOTOMAPA&STYLE={style}&format=image/jpeg&TileMatrixSet={TileMatrixSet}&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}" |

##### Returns:

an instance of OM.layer.WMTSTileLayer

Type
OM.layer.WMTSTileLayer

### Extends

- [OM.layer.TileLayer](OM.layer.TileLayer.md)

### Methods

------------------------------------------------------------------------

#### bringForward()

Bring the layer to the front by one step (closer to the top of the map).

Inherited From:
- [OM.layer.Layer#bringForward](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### bringToTop()

Bring the layer all the way to the top of the map

Inherited From:
- [OM.layer.Layer#bringToTop](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### enableInfoWindow(enable)

Enable or disable the feature info window.

##### Parameters:

| Name     | Type    | Description                                                                       |
|----------|---------|-----------------------------------------------------------------------------------|
| `enable` | boolean | Enable or disable feature info window. By default,<br>the info window is enabled. |

Inherited From:
- [OM.layer.Layer#enableInfoWindow](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableUTFGridInfoWindow(status)

Enable or disable the UTFGrid Info Window when applicable

##### Parameters:

| Name     | Type    | Description                                                                   |
|----------|---------|-------------------------------------------------------------------------------|
| `status` | boolean | true or false to enable or disable the default (built-in) utfgrid info window |

Inherited From:
- [OM.layer.TileLayer#enableUTFGridInfoWindow](OM.layer.TileLayer.md)

------------------------------------------------------------------------

#### getCustomTags()

Get custom tags from tile layer

Inherited From:
- [OM.layer.TileLayer#getCustomTags](OM.layer.TileLayer.md)

##### Returns:

An object defined custom tags if any

Type
Object

------------------------------------------------------------------------

#### getEnableInfoWindow()

get the enable infowindow status: true for enabled and false otherwise
the info window is enabled.

Inherited From:
- [OM.layer.Layer#getEnableInfoWindow](OM.layer.Layer.md)

##### Returns:

true or false

Type
boolean

------------------------------------------------------------------------

#### getName()

Get the layer name.

Inherited From:
- [OM.layer.Layer#getName](OM.layer.Layer.md)

##### Returns:

The layer name

Type
String

------------------------------------------------------------------------

#### getOpacity()

Get the layer's current opacity setting.

Inherited From:
- [OM.layer.Layer#getOpacity](OM.layer.Layer.md)

##### Returns:

The layer's opacity. Is a value between 0 and 1.

Type
float

------------------------------------------------------------------------

#### getTileLayerConfig(callBack)

Get the tile layer configuration.

##### Parameters:

| Name       | Type     | Description                                                                                  |
|------------|----------|----------------------------------------------------------------------------------------------|
| `callBack` | function | Getting tile layer config is asynchronous. So<br>you need a callback fucntion to get result. |

Inherited From:
- [OM.layer.TileLayer#getTileLayerConfig](OM.layer.TileLayer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### getUTFGridResolution(res)

parse and return the utfgrid resolution

##### Parameters:

| Name  | Type   | Description                                                |
|-------|--------|------------------------------------------------------------|
| `res` | string | The utfgrid resolution. Can be either a string or a number |

Inherited From:
- [OM.layer.TileLayer#getUTFGridResolution](OM.layer.TileLayer.md)

##### Returns:

the utfgrid resolution

Type
number

------------------------------------------------------------------------

#### getWMTS_URL(x, y, z)

##### Parameters:

| Name | Type   | Description                       |
|------|--------|-----------------------------------|
| `x`  | Number | Tile coordinate x.                |
| `y`  | Number | Tile coordinate y.                |
| `z`  | Number | Tile zoom level.<br>z: zoom level |

##### Returns:

the image url

------------------------------------------------------------------------

#### getZIndex()

Get the layer's z-index.

Inherited From:
- [OM.layer.Layer#getZIndex](OM.layer.Layer.md)

##### Returns:

The z-index value. Returns -1 if the layer was not added to the map.

Type
int

------------------------------------------------------------------------

#### isInZoomLevelRange(curLevel)

Checks if the current map zoom level is within this layer's visible zoom-level range.

##### Parameters:

| Name       | Type | Description                                                                                                                                                |
|------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `curLevel` | int  | Optional, the zoom level to check if it is within the minVisibleLevel and maxVisibleLevel<br>range. If not specified, then the current zoom level is used. |

Inherited From:
- [OM.layer.Layer#isInZoomLevelRange](OM.layer.Layer.md)

##### Returns:

true if the current map level is within the layer's zoom level range for
it to be visible.

Type
Boolean

------------------------------------------------------------------------

#### isVisible(curLevel)

Get the visibility of the layer.

##### Parameters:

| Name       | Type | Description                                                                                                                                                |
|------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `curLevel` | int  | Optional, the zoom level to check if it is within the minVisibleLevel and maxVisibleLevel<br>range. If not specified, then the current zoom level is used. |

Inherited From:
- [OM.layer.Layer#isVisible](OM.layer.Layer.md)

##### Returns:

True if the theme-based FOI layer is currently visible,
False if the theme-based FOI layer is currently not visible

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.layer.Layer#on](OM.layer.Layer.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### redraw()

Refresh the display of the layer's existing data.

Inherited From:
- [OM.layer.Layer#redraw](OM.layer.Layer.md)

##### Returns:

None

------------------------------------------------------------------------

#### sendBackward()

Sendthe layer to the back by one step (closer to the bottom of the map).

Inherited From:
- [OM.layer.Layer#sendBackward](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### sendToBottom()

Send the layer all the way to the bottom of the map

Inherited From:
- [OM.layer.Layer#sendToBottom](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### setInfoWindowTrigger(status)

Enable or disable the UTFGridInfoWindow when applicable

##### Parameters:

| Name     | Type    | Description                                                                   |
|----------|---------|-------------------------------------------------------------------------------|
| `status` | boolean | true or false to enable or disable the default (built-in) utfgrid info window |

Inherited From:
- [OM.layer.TileLayer#setInfoWindowTrigger](OM.layer.TileLayer.md)

------------------------------------------------------------------------

#### setName(newName)

Set the layer name with the given name.

##### Parameters:

| Name      | Type   | Description                                      |
|-----------|--------|--------------------------------------------------|
| `newName` | String | The new layer name to be assigned to this layer. |

Inherited From:
- [OM.layer.Layer#setName](OM.layer.Layer.md)

##### Returns:

Type
None

------------------------------------------------------------------------

#### setOpacity(opacity)

Set the layer's opacity. A value between 0 (transparnet) and 1 (opaque).

##### Parameters:

| Name      | Type  | Description                                                        |
|-----------|-------|--------------------------------------------------------------------|
| `opacity` | float | It should be a number between 0 and 1. e.g. 0.5 means 50% opacity. |

Inherited From:
- [OM.layer.Layer#setOpacity](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setVisible(visibility)

Sets the visibility of the layer.
Note that the visibility change will NOT be made if the current map zoom level is
outside the layer's 'visible zoom level range' which is set by setZoomLevelRange() method.

##### Parameters:

| Name         | Type    | Description                                                                         |
|--------------|---------|-------------------------------------------------------------------------------------|
| `visibility` | Boolean | A Boolean true (show the layer, i.e. make it visible) or false<br>(hide the layer). |

Inherited From:
- [OM.layer.Layer#setVisible](OM.layer.Layer.md)

##### Returns:

void}

Type
None

------------------------------------------------------------------------

#### setVisibleBound(bound)

Set a bound (MBR) for the layer visibility. Only content within the supplied bound will be rendered.
That is, the map client will only fetch and display map content within this bound.

##### Parameters:

| Name    | Type                                              | Description                  |
|---------|---------------------------------------------------|------------------------------|
| `bound` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | Specifies the layer boundary |

Inherited From:
- [OM.layer.Layer#setVisibleBound](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setZIndex()

Set the z-index for the layer.

Note: A valid layer z-index should be a number between 1 and n, where n is
the number of layers that are currently displayed in the map. When the newIndex
parameter of setZIndex is less than 1, it will be set to 1. If it is
greater than n, it will be set to n. If z-Index value, newIndex, is already assigned
to another layer, then it will still be assigned to the current layer (on which this function is invoked).
One or more of the other layer will be assigned a different z-index value. The changes will depend on
whether this layer was inserted into the current layer stack or just moved within the layer stack.

Inherited From:
- [OM.layer.Layer#setZIndex](OM.layer.Layer.md)

##### Returns:

The old z-index

Type
int

------------------------------------------------------------------------

#### setZoomLevelRange(minLevel, maxLevel)

Set the zoom level range within which this layer is visible. By default
a layer is set to be visible between a minmum zoom level of 0 and a maximum
(theoretical) zoom level of 100.

##### Parameters:

| Name       | Type | Description                                                                                            |
|------------|------|--------------------------------------------------------------------------------------------------------|
| `minLevel` | int  | Specifies the min level. The layer will not be<br>visible if the zoom level is lower than this vlaue.  |
| `maxLevel` | int  | Specifies the max level. The layer will not be<br>visible if the zoom level is higher than this value. |

Inherited From:
- [OM.layer.Layer#setZoomLevelRange](OM.layer.Layer.md)

##### Returns:

Type
None
