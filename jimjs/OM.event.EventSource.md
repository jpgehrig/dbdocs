Provides methods used for event handling. It is typically mixed in by concrete classes
such as OM.Map or OM.Layer which generates events. It's not meant to be used directly.

### Methods

------------------------------------------------------------------------

#### \<static\> on()

A shorthand name for the member function addListener.

------------------------------------------------------------------------

#### addListener(eventType, f, context)

Attaches an event listener for the given event type under the given
context.

##### Parameters:

| Name        | Type     | Description                                                                            |
|-------------|----------|----------------------------------------------------------------------------------------|
| `eventType` | String   | The event type, which is typically specific to the class<br>that mixes in EventSource. |
| `f`         | function | The listener function                                                                  |
| `context`   | Object   | An optional context; The default is this.                                              |

------------------------------------------------------------------------

#### deleteAllListeners()

removes all listeners currently registered on this instance, regardless
of their type.

------------------------------------------------------------------------

#### deleteListener(eventType, f, context)

Removes the given listener function previously registered.

##### Parameters:

| Name        | Type     | Description            |
|-------------|----------|------------------------|
| `eventType` | String   | type of listener event |
| `f`         | function | the listener function  |
| `context`   | Object   | An optional context    |

------------------------------------------------------------------------

#### deleteListeners()

Removes all listeners of the specified type from this instance.

------------------------------------------------------------------------

#### getListeners(eventType)

Returns an array of listeners for the specified event type.

##### Parameters:

| Name        | Type   | Description    |
|-------------|--------|----------------|
| `eventType` | String | The event type |

------------------------------------------------------------------------

#### hasListener(eventType, handler, ctx)

Checks if any listeners have been registered for the given type.

##### Parameters:

| Name        | Type   | Description                           |
|-------------|--------|---------------------------------------|
| `eventType` | String | The event type to check for listeners |
| `handler`   | Object | The event type handler. Optional      |
| `ctx`       | Object | The handler context. Optional         |

##### Returns:

True if listener exists, false otherwise.

Type
Boolean
