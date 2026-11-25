------------------------------------------------------------------------

#### new Event(type, target)

This is an abstract class that all events must extend.

##### Parameters:

| Name     | Type   | Description      |
|----------|--------|------------------|
| `type`   | String | The event type   |
| `target` | Object | The event target |

##### Returns:

An Event object

Type
OM.event.Event

### Members

------------------------------------------------------------------------

#### evt :Object

The original event, if applicable

##### Type:

- Object

------------------------------------------------------------------------

#### target :Object

The component that dispatches the event.

##### Type:

- Object

------------------------------------------------------------------------

#### type :String

Type of the event.

##### Type:

- String
