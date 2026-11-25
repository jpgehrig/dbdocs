------------------------------------------------------------------------

#### new ToolEvent(type, target)

This class defines the types of events that may be fired by an
interactive map tool such as the DistanceTool or RedlineTool.

##### Parameters:

| Name     | Type   | Description                                              |
|----------|--------|----------------------------------------------------------|
| `type`   | String | The event type, such as `OM.event.ToolEvent.TOOL_START`. |
| `target` | Object | The event target, typically the Tool instance itself.    |

##### Returns:

An object of ToolEvent

Type
OM.event.ToolEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> CIRCLE_DRAG :String

The type of events fired when a circle tool is being dragged by the user.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_RIGHT_CLICK :String

The type of events fired when user just did a right-click when using
the current RedlineTool instance.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> RECTANGLE_DRAG :String

The type of events fired when a rectangle tool is being dragged by the user.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> REDLINE_EDITED :String

The type of events fired when the shape geometry of the
current RedlineTool instance has just been modified by the user.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> REDLINE_POINT_CREATE :String

The type of events fired when a new vertex point has jsut been created
by the current RedlineTool instance.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> SNAP_POINT :String

The type of events fired by the current RedlineTool instance
as part of the mouse move event. Application can listen
on this event to obtain snap point (from a separate layer).

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> TOOL_CLEAR :String

The type of events fired when a tool has cleared its internal state.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> TOOL_END :String

The type of events fired when an interactive tool has just ended.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> TOOL_START :String

The type of events fired when an interactive tool has just started.

##### Type:

- String

------------------------------------------------------------------------

#### evt :Object

The original event, if applicable

##### Type:

- Object

Inherited From:
- [OM.event.Event#evt](OM.event.Event.md)

------------------------------------------------------------------------

#### location :Point

The ground location where the event occurs

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
