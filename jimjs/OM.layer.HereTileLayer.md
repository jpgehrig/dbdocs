------------------------------------------------------------------------

#### new HereTileLayer(name, config)

OM.layer.HereTileLayer defines a map tile layer that displays HERE Maps using
HERE Map Tile API 3.0.

To use HERE Maps as a tile layer, your usage of the maps must meet the Terms
of Service defined by HERE.

HERE Map tiles are rendered in a projection system known as Spherical Mercator.
If you need to overlay your own spatial data on top of the HERE Maps tile layer, you
must set up the database to properly handle coordinate system transformation between
the HERE Maps coordinate system and your own data coordinate system if they are not
the same. Please refer to MapViewer User's Guide for more information.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`   | String | The layer name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `config` | Object | The HERE tile layer configuration. It can have the following<br>attributes:<br>• mapTypeList {Array} An array of available map types. Can be one or more of the pre-defined given<br>in mapType below.<br>• mapTypeVisible {Boolean} Show or hide the map type list<br>• libURL {String} The javascript lib url<br>• appID {String} The HERE maps appID<br>• appCode {String} The HERE maps appCode<br>• useHTTPS {Boolean} true or false<br>• useCIT {Boolean} true or false. The CIT environment is not intended for general production use.<br>• mapType {String} The default map type. One of pre-defined values:<br>OM.layer.HereTileLayer.TYPE_NORMAL_MAP="NORMAL_MAP";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_MAP="SATELLITE_MAP";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_MAP="TERRAIN_MAP";<br>OM.layer.HereTileLayer.TYPE_NORMAL_TRAFFIC="NORMAL_TRAFFIC";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_TRAFFIC="SATELLITE_TRAFFIC";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_TRAFFIC="TERRAIN_TRAFFIC";<br>OM.layer.HereTileLayer.TYPE_NORMAL_PANORAMA="NORMAL_PANORAMA";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_PANORAMA="SATELLITE_PANORAMA";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_PANORAMA="TERRAIN_PANORAMA";<br>OM.layer.HereTileLayer.TYPE_NORMAL_TRANSIT="NORMAL_TRANSIT";<br>OM.layer.HereTileLayer.TYPE_NORMAL_XBASE="NORMAL_XBASE";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_XBASE="SATELLITE_XBASE";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_XBASE="TERRAIN_XBASE";<br>OM.layer.HereTileLayer.TYPE_NORMAL_BASE="NORMAL_BASE";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_BASE="SATELLITE_BASE";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_BASE="TERRAIN_BASE";<br>OM.layer.HereTileLayer.TYPE_NORMAL_LABELS="NORMAL_LABELS";<br>OM.layer.HereTileLayer.TYPE_SATELLITE_LABELS="SATELLITE_LABELS";<br>OM.layer.HereTileLayer.TYPE_TERRAIN_LABELS="TERRAIN_LABELS";<br> |

##### Returns:

an instance of OM.layer.HereTileLayer

Type
OM.layer.HereTileLayer

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

Get the current type of the map, which can be one of the following predefined
map types:
OM.layer.HereTileLayer.TYPE_NORMAL_MAP="NORMAL_MAP";
OM.layer.HereTileLayer.TYPE_SATELLITE_MAP="SATELLITE_MAP";
OM.layer.HereTileLayer.TYPE_TERRAIN_MAP="TERRAIN_MAP";
OM.layer.HereTileLayer.TYPE_NORMAL_TRAFFIC="NORMAL_TRAFFIC";
OM.layer.HereTileLayer.TYPE_SATELLITE_TRAFFIC="SATELLITE_TRAFFIC";
OM.layer.HereTileLayer.TYPE_TERRAIN_TRAFFIC="TERRAIN_TRAFFIC";
OM.layer.HereTileLayer.TYPE_NORMAL_PANORAMA="NORMAL_PANORAMA";
OM.layer.HereTileLayer.TYPE_SATELLITE_PANORAMA="SATELLITE_PANORAMA";
OM.layer.HereTileLayer.TYPE_TERRAIN_PANORAMA="TERRAIN_PANORAMA";
OM.layer.HereTileLayer.TYPE_NORMAL_TRANSIT="NORMAL_TRANSIT";
OM.layer.HereTileLayer.TYPE_NORMAL_XBASE="NORMAL_XBASE";
OM.layer.HereTileLayer.TYPE_SATELLITE_XBASE="SATELLITE_XBASE";
OM.layer.HereTileLayer.TYPE_TERRAIN_XBASE="TERRAIN_XBASE";
OM.layer.HereTileLayer.TYPE_NORMAL_BASE="NORMAL_BASE";
OM.layer.HereTileLayer.TYPE_SATELLITE_BASE="SATELLITE_BASE";
OM.layer.HereTileLayer.TYPE_TERRAIN_BASE="TERRAIN_BASE";
OM.layer.HereTileLayer.TYPE_NORMAL_LABELS="NORMAL_LABELS";
OM.layer.HereTileLayer.TYPE_SATELLITE_LABELS="SATELLITE_LABELS";
OM.layer.HereTileLayer.TYPE_TERRAIN_LABELS="TERRAIN_LABELS";

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

#### resize()

Abstract method. Resize the map.

Inherited From:
- [OM.layer.BuiltinExternalTileLayer#resize](OM.layer.BuiltinExternalTileLayer.md)

##### Returns:

Type
void

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

Set the type of the map, which can be one of the following predefined
Here Map types:
OM.layer.HereTileLayer.TYPE_NORMAL_MAP="NORMAL_MAP";
OM.layer.HereTileLayer.TYPE_SATELLITE_MAP="SATELLITE_MAP";
OM.layer.HereTileLayer.TYPE_TERRAIN_MAP="TERRAIN_MAP";
OM.layer.HereTileLayer.TYPE_NORMAL_TRAFFIC="NORMAL_TRAFFIC";
OM.layer.HereTileLayer.TYPE_SATELLITE_TRAFFIC="SATELLITE_TRAFFIC";
OM.layer.HereTileLayer.TYPE_TERRAIN_TRAFFIC="TERRAIN_TRAFFIC";
OM.layer.HereTileLayer.TYPE_NORMAL_PANORAMA="NORMAL_PANORAMA";
OM.layer.HereTileLayer.TYPE_SATELLITE_PANORAMA="SATELLITE_PANORAMA";
OM.layer.HereTileLayer.TYPE_TERRAIN_PANORAMA="TERRAIN_PANORAMA";
OM.layer.HereTileLayer.TYPE_NORMAL_TRANSIT="NORMAL_TRANSIT";
OM.layer.HereTileLayer.TYPE_NORMAL_XBASE="NORMAL_XBASE";
OM.layer.HereTileLayer.TYPE_SATELLITE_XBASE="SATELLITE_XBASE";
OM.layer.HereTileLayer.TYPE_TERRAIN_XBASE="TERRAIN_XBASE";
OM.layer.HereTileLayer.TYPE_NORMAL_BASE="NORMAL_BASE";
OM.layer.HereTileLayer.TYPE_SATELLITE_BASE="SATELLITE_BASE";
OM.layer.HereTileLayer.TYPE_TERRAIN_BASE="TERRAIN_BASE";
OM.layer.HereTileLayer.TYPE_NORMAL_LABELS="NORMAL_LABELS";
OM.layer.HereTileLayer.TYPE_SATELLITE_LABELS="SATELLITE_LABELS";
OM.layer.HereTileLayer.TYPE_TERRAIN_LABELS="TERRAIN_LABELS";

##### Parameters:

| Name      | Type   | Description             |
|-----------|--------|-------------------------|
| `mapType` | String | specifies the map type. |

Overrides:
- OM.layer.BuiltinExternalTileLayer#setMapType

##### Returns:

void

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
