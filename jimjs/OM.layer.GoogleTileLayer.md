------------------------------------------------------------------------

#### new GoogleTileLayer(name, config)

OM.layer.GoogleTileLayer defines a map tile layer that displays Google Maps using
Google Maps JavaScript API V3.

To use the Google Maps tiles, you must have obtained a Google Maps API Key from Google.
You will be prompted to enter your API Key and, when applicable, your Google "Client ID".
Usage of the tiles must meet the terms of service specified by Google (see https://developers.google.com/readme/terms).

Google Maps tiles are rendered in a projection system known as Spherical Mercator.
If you need to overlay your own spatial data on top of the Google Maps tile layer, you
must setup the database to properly handle coordinate system transformation between
the Google Maps coordinate system and your own data coordinate system if they are not
the same. Please refer to MapViewer User's guide for more information.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`   | String | A unique tile layer name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `config` | Object | The Google tile layer configuration. It can have the following<br>attributes:<br>• mapTypeList {Array} An array of available map types. Can be one or more of the following pre-defined values:<br>OM.layer.GoogleTileLayer.TYPE_ROAD;OM.layer.GoogleTileLayer.TYPE_SATELLITE;<br>OM.layer.GoogleTileLayer.TYPE_SHADED;OM.layer.GoogleTileLayer.TYPE_HYBRID<br>• mapTypeVisible {Boolean} Show or hide the map type list<br>• tilt {number} The only allowed values are 0 and 45. The value 0 causes the map to always use an overhead view<br>regardless of the zoom level and viewport. The value 45 causes the tilt angle to automatically switch to 45 whenever<br>45-degree imagery is available for the current zoom level and viewport, and switch back to 0 whenever 45-degree imagery is not available<br>(this is the default behavior).<br>• libURL {String} The Google maps javascript lib url. If not provided, a built in urlLib will be used.<br>• mapType {String} Specifies the default map type<br>• key {String} your Google Maps key.<br>• clientID {String} Your client ID identifies you as a Maps API for Business customer:<br>Application must import the following scripts to allow URL signing:<br>http://crypto-js.googlecode.com/svn/tags/3.1.2/build/rollups/hmac-sha1.js<br>http://crypto-js.googlecode.com/svn/tags/3.0.2/build/components/enc-base64-min.js |

##### Returns:

A instance of OM.layer.GoogleTileLayer

Type
OM.layer.GoogleTileLayer

### Extends

- [OM.layer.BuiltinExternalTileLayer](OM.layer.BuiltinExternalTileLayer.md)

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

#### getMapType()

Get the current type of the map. It can be one of the following predefined
map types: OM.layer.GoogleTileLayer.TYPE_ROAD, OM.layer.GoogleTileLayer.TYPE_SATELLITE,
OM.layer.GoogleTileLayer.TYPE_HYBRID and OM.layer.GoogleTileLayer.TYPE_SHADED.

##### Returns:

The current map type

Type
String

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

#### setMapCenterAndZoomlevel()

Set or change the map center and zoom level.
The new or modified center and zoom level are stored in and subsequently retrieved from the map context.
you can call "this.parentMap.getMapContext()" to get the map context.
To transfrom the coordinate you can call "this.parentMap.getMapContext().getCenterPoint().transform(8307)" at client side
or call "this.parentMap.getMapContext().getCenterPoint().transform(8307, function(geom){})" at server side;

Inherited From:
- [OM.layer.BuiltinExternalTileLayer#setMapCenterAndZoomlevel](OM.layer.BuiltinExternalTileLayer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMapType(mapType)

Set the map type. It can be one of the following predefined values (i.e.
Google Map types): OM.layer.GoogleTileLayer.TYPE_ROAD, OM.layer.GoogleTileLayer.TYPE_SATELLITE,
OM.layer.GoogleTileLayer.TYPE_SHADED and OM.layer.GoogleTileLayer.TYPE_HYBRID

##### Parameters:

| Name      | Type    | Description             |
|-----------|---------|-------------------------|
| `mapType` | mapType | specifies the map type. |

Overrides:
- OM.layer.BuiltinExternalTileLayer#setMapType

##### Returns:

void}

Type
None

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
