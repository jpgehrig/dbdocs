------------------------------------------------------------------------

#### new MapEvent(type, target)

The class defines events that may be fired by an instance of OM.Map.

It also defines constants representing event types.

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `type`   | String | The event type   |
| `target` | Object | The event target |

##### Returns:

An object of MapEvent

Type
OM.event.MapEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> LAYER_ADDED :String

The type of events fired when a map layer has been added to the map.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LAYER_DELETED :String

The type of events fired when a map layer has been removed from
the map.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LAYER_REORDERED :String

The type of events fired when the display order of a map
layer has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_AFTER_REFRESH :String

The type of events fired when the map has been refreshed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_AFTER_ZOOM :String

The type of events fired when the map has just zoomed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_BEFORE_REFRESH :String

The type of events fired when the map is about to be refreshed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_BEFORE_ZOOM :String

The type of events fired when the map is just about to zoom (in or out).

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_DESTROY :String

The type of event fired when the map is destroyed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_INITIALIZED :String

The type of event fired when the map has been initialized.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_RECENTERED :String

The type of events fired when the map has just been re-centered.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_REDRAW :String

The type of events fired when the map has been redrawn (where the map
layers do not refresh or reload their feature data).

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_RESET_UNIVERSE :String

The type of events fired when the map's universe has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MAP_RESIZED :String

The type of events fired when the map's container DIV has been resized.

##### Type:

- String

------------------------------------------------------------------------

#### affectedLayer :Layer

The newly added, removed or reordered layer(s), only valid with LAYER_ADDED, LAYER_DELETED and LAYERS_REORDERED events.

##### Type:

- Layer

------------------------------------------------------------------------

#### beforeZoomLevel :int

The zoom level before zoom level change, only valid with the zoom events.

##### Type:

- int

------------------------------------------------------------------------

#### evt :Object

The original event, if applicable

##### Type:

- Object

Inherited From:
- [OM.event.Event#evt](OM.event.Event.md)

------------------------------------------------------------------------

#### preMapCenter :Point

The current map center, only valid with the recenter event.

##### Type:

- Point

------------------------------------------------------------------------

#### target :Object

The component that dispatches the event.

##### Type:

- Object

Inherited From:
- [OM.event.Event#target](OM.event.Event.md)

------------------------------------------------------------------------

#### type :String

Type of the event.

##### Type:

- String

Inherited From:
- [OM.event.Event#type](OM.event.Event.md)
