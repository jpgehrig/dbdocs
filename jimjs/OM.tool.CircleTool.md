------------------------------------------------------------------------

#### new CircleTool(map)

This is a subclass of OM.tool.Tool that allows the user to draw a circle
on the map.

##### Parameters:

| Name  | Type                | Description  |
|-------|---------------------|--------------|
| `map` | [OM.Map](OM.Map.md) | A map object |

##### Returns:

An instance of OM.tool.CircleTool

Type
OM.tool.CircleTool

### Extends

- [OM.tool.Tool](OM.tool.Tool.md)

### Methods

------------------------------------------------------------------------

#### clear()

Clears the tool's generated shapes and restores its state to that at initialization.

##### Returns:

Type
void

------------------------------------------------------------------------

#### getCenter()

Get the center point of the circle geometry created by this tool.

##### Returns:

The center point.

Type
[OM.geometry.Point](OM.geometry.Point.md)

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

#### getRadius(unit, callBack)

This method returns the proximate radius of the circle in the specified unit.

##### Parameters:

| Name       | Type | Description                                                                                                                                                                                                                                       |
|------------|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `unit`     |      | a string that specifies the name of the distance unit. It is required. It could be meter or kilometer.                                                                                                                                            |
| `callBack` |      | a callback function that deals with the radius if the client cannot deal with the computation.<br>callBack is a function look like :<br>function callBack(finalResult) ;<br>client support local getlength for srid: 3857,8307, 8265, 4326, 4269) |

##### Returns:

Radius of the circle

Type
float

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

#### start()

The start method activates this tool. Once a tool is started, the user
can hold down and drag the mouse to create a shape, in this case a circle.

##### Returns:

The tool itself

Type
OM.tool.CircleTool
