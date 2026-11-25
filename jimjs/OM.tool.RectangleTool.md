------------------------------------------------------------------------

#### new RectangleTool(map)

##### Parameters:

| Name  | Type                | Description                             |
|-------|---------------------|-----------------------------------------|
| `map` | [OM.Map](OM.Map.md) | the map instance to be associated with. |

##### Returns:

An instance of OM.tool.RectangleTool

### Extends

- [OM.tool.Tool](OM.tool.Tool.md)

### Methods

------------------------------------------------------------------------

#### clear()

Clears the tool's generated shapes and restores its state to pre-start.

------------------------------------------------------------------------

#### getDraggingHeight()

Gets the current rectangle height in map units.

##### Returns:

the rectangle height when dragging (0 if not in dragging mode).

Type
float

------------------------------------------------------------------------

#### getDraggingWidth()

Gets the current rectangle width in map units.

##### Returns:

the rectangle width when dragging (0 if not in dragging mode).

Type
float

------------------------------------------------------------------------

#### getGeometry()

Get the generated geometry. This should typically be called from
inside an event listener that is registered to the tool's life cycle
event such as OM.event.ToolEvent.TOOL_END.

Inherited From:
- [OM.tool.Tool#getGeometry](OM.tool.Tool.md)

##### Returns:

the geometry created by the tool

Type
[OM.geometry.Geometry](OM.geometry.Geometry.md)

------------------------------------------------------------------------

#### getStatus()

Get the tool's status. Can be one of OM.tool.Tool.STARTED, OM.tool.Tool.STOPPED, or OM.tool.Tool.FINISHED

Inherited From:
- [OM.tool.Tool#getStatus](OM.tool.Tool.md)

##### Returns:

tool status

Type
int

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.tool.Tool#on](OM.tool.Tool.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### setDrawingStyle(style)

Set the line drawing style

##### Parameters:

| Name    | Type                              | Description                                                                   |
|---------|-----------------------------------|-------------------------------------------------------------------------------|
| `style` | [OM.style.Line](OM.style.Line.md) | A line style used to<br>display the shape boundary as the user is drawing it. |

Inherited From:
- [OM.tool.Tool#setDrawingStyle](OM.tool.Tool.md)

##### Returns:

The tool instance

Type
[OM.tool.Tool](OM.tool.Tool.md)

------------------------------------------------------------------------

#### setStyle(style)

Set rendering style for the completed feature

##### Parameters:

| Name    | Type     | Description                                  |
|---------|----------|----------------------------------------------|
| `style` | OM.Style | The style to be used for the completed shape |

Inherited From:
- [OM.tool.Tool#setStyle](OM.tool.Tool.md)

##### Returns:

The tool instance

Type
[OM.tool.Tool](OM.tool.Tool.md)

------------------------------------------------------------------------

#### setZeroSizeAllowed(flag)

Sets whether this tool allows creation of zero-sized rectangles.
Default is disabled with a warning dialog shown to user.

##### Parameters:

| Name   | Type    | Description                                                         |
|--------|---------|---------------------------------------------------------------------|
| `flag` | boolean | if true then zero-sized rectangles are allowed;<br>false otherwise. |

------------------------------------------------------------------------

#### start()

This is the start method. It's an entrance to draw a tool

##### Returns:

The tool itself
