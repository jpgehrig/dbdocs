------------------------------------------------------------------------

#### new WMSTileLayer(name, options)

This class represents the Oracle Map tile layer. It extends DynamicTileLayer with
WMS related parameters.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | String | A unique WMS tile layer name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `options` | Object | A JSON object that specifies WMS tile layer related parameters. It may have the following attributes.<br><br>• universe {OM.universe.Universe}: The WMS tile layer universe object<br>• tileLayerConfig {OM.layer.TileLayerConfig}: The WMS tile layer configuration object.<br>• wmsServerURL {String}: The WMS server URL. For example, "http://maps.oracle.com/mapviewer/wms".<br>This URL may point to any WMS compliant server.<br>• urlBuilderOptions {Object}: Optional. A JSON object that contains the parameters for a WMS request.<br>An example is given below:<br>urlBuilderOptions: {<br>"dataSource": "ELOCATION_MERCATOR",<br>"version":"1.1.1",<br>"srs":"EPSG:4326",<br>"format":"image/png",<br>"bgcolor" : "#a6cae0",<br>"antialiase" : "false",<br>"layers": "M_ADMIN_AREA1_S01,M_STATE_BORDER_S05,M_CITIES_POINTS_S10"<br>} |

##### Returns:

an instance of OM.layer.WMSTileLayer

Type
OM.layer.WMSTileLayer

### Extends

- [OM.layer.DynamicTileLayer](OM.layer.DynamicTileLayer.md)

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

#### getCustomURL(x, y, z)

##### Parameters:

| Name | Type   | Description                       |
|------|--------|-----------------------------------|
| `x`  | Number | Tile coordinate x.                |
| `y`  | Number | Tile coordinate y.                |
| `z`  | Number | Tile zoom level.<br>z: zoom level |

Inherited From:
- [OM.layer.DynamicTileLayer#getCustomURL](OM.layer.DynamicTileLayer.md)

##### Returns:

the image url

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

#### getStaticMapURL(width)

This method returns a static URL of the displayed map.
This URL may be used to print the map in a dimention specified by the width and height arguments.

##### Parameters:

| Name    | Type | Description                                                |
|---------|------|------------------------------------------------------------|
| `width` | int  | The image width in pixels to contain the current map view. |

Inherited From:
- [OM.layer.DynamicTileLayer#getStaticMapURL](OM.layer.DynamicTileLayer.md)

##### Returns:

An XML map request. This reques can be used to fetch the map in current map view.
The fetched map will fit into the given image dimension specified by the width and height arguments.

Type
String

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

#### setBindingParameters(bp)

Set the binding parameters of a predefined theme in a dynamic tile layer.

##### Parameters:

| Name | Type   | Description                                                                                                                                                   |
|------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bp` | object | An array of JSON object containing themes' binding parameters.<br>For example \[{'WIND_THEME', \[{value:0.0, type:'Double'}, {value:'CA', type:'String'}\]}\] |

Inherited From:
- [OM.layer.DynamicTileLayer#setBindingParameters](OM.layer.DynamicTileLayer.md)

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

#### setZoomLevelOffset(offset)

set the offset for zoom level for configuration zoom level shift.
If the config's zoom level 0 matches 1 in the tile image provider, set it to 1
If the config's zoom level 1 matches 0 in the tile image provider, set it to -1

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `offset` | Number | The offset value |

Inherited From:
- [OM.layer.DynamicTileLayer#setZoomLevelOffset](OM.layer.DynamicTileLayer.md)

##### Returns:

null

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
