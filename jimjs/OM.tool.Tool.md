------------------------------------------------------------------------

#### new Tool(map)

Tool is the base class for various types of map tools such as those used
for distance measuring, marquee zooming and drawing custom shapes.

All Tool instances fire various events which are instances of [`OM.event.ToolEvent`](OM.event.ToolEvent.md).
Application can listen on any of the applicable events to customize the
behavior of the tool instance.

##### Parameters:

| Name  | Type                | Description                                       |
|-------|---------------------|---------------------------------------------------|
| `map` | [OM.Map](OM.Map.md) | The map instance to be associated with this tool. |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

##### Fires:

- event:ToolEvent

### Methods

------------------------------------------------------------------------

#### getGeometry()

Get the generated geometry. This should typically be called from
inside an event listener that is registered to the tool's life cycle
event such as OM.event.ToolEvent.TOOL_END.

##### Returns:

the geometry created by the tool

Type
[OM.geometry.Geometry](OM.geometry.Geometry.md)

------------------------------------------------------------------------

#### getStatus()

Get the tool's status. Can be one of OM.tool.Tool.STARTED, OM.tool.Tool.STOPPED, or OM.tool.Tool.FINISHED

##### Returns:

tool status

Type
int

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### setDrawingStyle(style)

Set the line drawing style

##### Parameters:

| Name    | Type                              | Description                                                                   |
|---------|-----------------------------------|-------------------------------------------------------------------------------|
| `style` | [OM.style.Line](OM.style.Line.md) | A line style used to<br>display the shape boundary as the user is drawing it. |

##### Returns:

The tool instance

Type
OM.tool.Tool

------------------------------------------------------------------------

#### setStyle(style)

Set rendering style for the completed feature

##### Parameters:

| Name    | Type     | Description                                  |
|---------|----------|----------------------------------------------|
| `style` | OM.Style | The style to be used for the completed shape |

##### Returns:

The tool instance

Type
OM.tool.Tool
