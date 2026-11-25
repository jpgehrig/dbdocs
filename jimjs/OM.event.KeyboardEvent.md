------------------------------------------------------------------------

#### new KeyboardEvent(type, target)

The class defines all keyboard events that might occur inside the map, and
dispatched by the map or any visual map component.

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `type`   | String | The event type   |
| `target` | Object | The event target |

##### Returns:

An object of KeyboardEvent

Type
OM.event.KeyboardEvent

### Extends

- [OM.event.Event](OM.event.Event.md)

### Members

------------------------------------------------------------------------

#### \<static, constant\> KEY_DOWN :String

##### Type:

- String

------------------------------------------------------------------------

#### \<static, constant\> KEY_UP :String

##### Type:

- String

------------------------------------------------------------------------

#### event :KeyboardEvent

The actual system keyboard event Object

##### Type:

- KeyboardEvent

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
