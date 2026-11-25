------------------------------------------------------------------------

#### new LayerEvent(type, target)

Defines the class of event objects fired by map layers.

It also defines the constants representing various layer event types.

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `type`   | String | The event type   |
| `target` | Object | The event target |

##### Returns:

Type
OM.event.LayerEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> AFTER_REFRESH :String

The type of events fired when a layer has just been refreshed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> BEFORE_REFRESH :String

The type of events fired when a layer is about to be refreshed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURE_DESELECTED :String

The type of events fired when a feature has been un-selected
in a VectorLayer.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURE_EDITED :String

The type of events fired when a specific feature of a VectorLayer
has been edited by user.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURE_MOVED :String

The type of events fired when a specific feature of a VectorLayer
has moved.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURE_MOVING :String

The type of events fired when a specific feature of a VectorLayer
is being moved.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURE_SELECTED :String

The type of events fired when a feature has been selected in
a VectorLayer.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURES_DISPLAYED :String

The type of events fired when the features of a VectorLayer has been
displayed on the map.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> FEATURES_LOADED :String

The type of events fired when the features of a VectorLayer has been
loaded (typically from a remote source or URL).

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> HOVER_STYLE_CHANGED :String

The type of events fired when the hover style of a VectorLayer has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LABELING_STYLE_CHANGED :String

The type of events fired when the labeling style of a VectorLayer
has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LAYER_REMOVED :String

The type of events fired when a layer has been removed from the map.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LAYER_VISIBILITY_CHANGED :String

The type of events fired when a layer's visibility has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> LAYER_Z_INDEX_CHANGED :String

The type of events fired when a layer's Z-index has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> RENDERING_STYLE_CHANGED :String

The type of events fired when the rendering style of a VectorLayer
has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> SELECTION_STYLE_CHANGED :String

The type of events fired when the selection style of a VectorLayer
has changed.

##### Type:

- String

------------------------------------------------------------------------

#### affectedFeature :[OM.Feature](OM.Feature.md)

the feature affected by a FEATURE_SELECTED or FEATURE_UNSELECTED event.

##### Type:

- [OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### evt :Object

The original event, if applicable

##### Type:

- Object

Inherited From:
- [OM.event.Event#evt](OM.event.Event.md)

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
