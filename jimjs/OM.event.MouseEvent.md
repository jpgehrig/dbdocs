------------------------------------------------------------------------

#### new MouseEvent(type, target)

This class defines mouse events that may be dispatched by the map or map layers and
handled by an application via listeners.

It also defines the various constants representing different types of mouse events.

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `type`   | String | The event type   |
| `target` | Object | The event target |

##### Returns:

Type
OM.event.MouseEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_CLICK :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_DOUBLE_CLICK :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_DOWN :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_MOVE :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_OUT :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_OVER :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_RIGHT_CLICK :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> MOUSE_UP :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> WHEEL_SCROLL :String

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

#### feature :FOI

The theme feature upon which the event occurs.

##### Type:

- FOI

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
