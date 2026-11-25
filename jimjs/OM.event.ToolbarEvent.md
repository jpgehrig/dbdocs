------------------------------------------------------------------------

#### new ToolbarEvent(type, target)

This class defines the ToolbarEvent that can be fired by the builtin toolbar buttons.

##### Parameters:

| Name     | Type   | Description                                               |
|----------|--------|-----------------------------------------------------------|
| `type`   | String | The event type, such as `OM.event.ToolbarEvent.BUTTON_UP` |
| `target` | Object | The event target                                          |

##### Returns:

Type
OM.event.ToolbarEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> BUTTON_DOWN :String

The type of events fired when the button just went into the 'down' state.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> BUTTON_STATE_CHANGE :String

The type of events fired when the button state has changed.

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> BUTTON_UP :String

The type of events fired when the button just went into the 'up' state.

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
