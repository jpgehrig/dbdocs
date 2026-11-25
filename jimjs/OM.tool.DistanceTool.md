------------------------------------------------------------------------

#### new DistanceTool(map, options)

A DistanceTool can be used to measure linear distances on the map by drawing
a series of connected line segments. It is a subclass of OM.tool.Tool.

##### Parameters:

| Name      | Type                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `map`     | [OM.Map](OM.Map.md) | The map instance to be associated with this tool                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `options` | object              | This is an object literal that specifies the initial DistanceTool options. It can have the following properties.<br>• unit {String} Optional. The unit for the distance tool.<br><br>• transformToGeodetic {boolean} Optional. If true, transform To Geodetic; default value is true.<br><br>• dataSource {String} Optional. The datasource for the distance tool.If client side supports the srid transform,this param is not required,<br>if client side does not support the srid transform,this param is required.<br> |

##### Returns:

An instance of OM.tool.DistanceTool

Type
OM.tool.DistanceTool

### Extends

- [OM.tool.Tool](OM.tool.Tool.md)

### Methods

------------------------------------------------------------------------

#### clear()

Clear the tool's generated shapes and state.

------------------------------------------------------------------------

#### getSegmentsArray()

Get the line segments distance between each neighboring point.The sequence of the segments distance array is the same as the point you add in sequence.

##### Returns:

An array of the line segments distance.

Type
Array

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

#### getTotalDistance()

Get the total distance of the line.

##### Returns:

The total distance of the line.

Type
float

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.tool.Tool#on](OM.tool.Tool.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### setDrawingStyle(options)

Set a drawing style for the tool. The style used to display the vertices and line segments.
This function should be called once to set the style for the vertices (i.e. the point style) and
once to set the style for the line segments.

##### Parameters:

| Name      | Type | Description                                                                                                                                                                                                                                                                                                    |
|-----------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | int  | An object with two properties, type and style, which<br>defines the geometry type and the style.<br><br>• type Specifies the geometry type. Must be one of two pre-defined constants:<br>OM.tool.DistanceTool.TYPE_POINT or OM.tool.DistanceTool.TYPE_LINESTRING.<br>• style {OM.style.Style} The style to use |

Overrides:
- [OM.tool.Tool#setDrawingStyle](OM.tool.Tool.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setStyle(style)

Set rendering style for the completed linestring

##### Parameters:

| Name    | Type                              | Description            |
|---------|-----------------------------------|------------------------|
| `style` | [OM.style.Line](OM.style.Line.md) | The line style to use. |

Overrides:
- [OM.tool.Tool#setStyle](OM.tool.Tool.md)

##### Returns:

Type
OM.tool.DistanceTool

------------------------------------------------------------------------

#### start()

Start the tool.

##### Returns:

Type
void
