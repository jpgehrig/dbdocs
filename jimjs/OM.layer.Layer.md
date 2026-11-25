------------------------------------------------------------------------

#### new Layer(name, config)

Layer is an abstract base class for various types of map layers that can be
displayed. The two main sub-classes are [`OM.layer.TileLayer`](OM.layer.TileLayer.md) and
[`OM.layer.VectorLayer`](OM.layer.VectorLayer.md).

A map layer typically fires many different types of events throughout
its life cycle. Most events are are instances of [`OM.event.LayerEvent`](OM.event.LayerEvent.md).

##### Parameters:

| Name     | Type   | Description                                         |
|----------|--------|-----------------------------------------------------|
| `name`   | String | The name of the layer to be created                 |
| `config` | Object | An optional configuration object for the new layer. |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

### Methods

------------------------------------------------------------------------

#### bringForward()

Bring the layer to the front by one step (closer to the top of the map).

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### bringToTop()

Bring the layer all the way to the top of the map

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

##### Returns:

Type
void

------------------------------------------------------------------------

#### getEnableInfoWindow()

get the enable infowindow status: true for enabled and false otherwise
the info window is enabled.

##### Returns:

true or false

Type
boolean

------------------------------------------------------------------------

#### getName()

Get the layer name.

##### Returns:

The layer name

Type
String

------------------------------------------------------------------------

#### getOpacity()

Get the layer's current opacity setting.

##### Returns:

The layer's opacity. Is a value between 0 and 1.

Type
float

------------------------------------------------------------------------

#### getZIndex()

Get the layer's z-index.

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

##### Returns:

True if the theme-based FOI layer is currently visible,
False if the theme-based FOI layer is currently not visible

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### redraw()

Refresh the display of the layer's existing data.

##### Returns:

None

------------------------------------------------------------------------

#### refresh()

Refresh or reload layer data then redraws the data on the map.

##### Returns:

void}

Type
None

------------------------------------------------------------------------

#### sendBackward()

Sendthe layer to the back by one step (closer to the bottom of the map).

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### sendToBottom()

Send the layer all the way to the bottom of the map

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### setName(newName)

Set the layer name with the given name.

##### Parameters:

| Name      | Type   | Description                                      |
|-----------|--------|--------------------------------------------------|
| `newName` | String | The new layer name to be assigned to this layer. |

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

##### Returns:

Type
None
