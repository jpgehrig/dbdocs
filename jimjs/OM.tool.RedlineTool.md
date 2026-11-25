------------------------------------------------------------------------

#### new RedlineTool(map, geoType, options)

This is a sub class of OM.tool.Tool that can be used to draw arbitrary
shape(s) on the map. It is similar to the traditional red-lining function.

##### Parameters:

| Name      | Type                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-----------|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `map`     | [OM.Map](OM.Map.md) | A map object                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `geoType` | int                 | The geometry type. Must be one of the following pre-defined constants<br>OM.tool.RedlineTool.TYPE_POINT,<br>OM.tool.RedlineTool.TYPE_LINESTRING, or<br>OM.tool.RedlineTool.TYPE_POLYGON defined in this class.                                                                                                                                                                                                                                                                                                           |
| `options` | Object              | It may contain the following attributes that specify the redline tool mode.<br><br>• finishMode {Boolean}: default is OM.tool.Redline.FINISH_ON_CLICK, meaning you must click on the initial<br>polygon vertex once to finish/complete the tool's drawing operation. If set to OM.tool.Redline.FINISH_ON_RELEASE, then<br>the tool will complete the drawing on the very first mouse-up.<br>• simplified {Boolean}: default is true. true: simplify the result of the redline; false: not simplify the result of redline |

##### Returns:

An instance of OM.tool.RedlineTool

Type
OM.tool.RedlineTool

### Extends

- [OM.tool.Tool](OM.tool.Tool.md)

### Methods

------------------------------------------------------------------------

#### addVertex(index, vertex, isRedo)

This method adds a new shape point.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                    |
|----------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `index`  | int    | Indicates the position, starting from 0, to put the new point in. If null, the point will be added to the end of the shape.                                                                                                    |
| `vertex` | Object | Either an OM.geometry.Point or any object with x and y member variables. If it is the former, the coordinates will be read as ground coordinates (srid transformation applied if necessary), the latter as screen coordinates. |
| `isRedo` | bool   | Optional If set to true the edit won't generate an entry in the undo manager.                                                                                                                                                  |

------------------------------------------------------------------------

#### clear()

Clear the tool's generated shapes and resets the state.

##### Returns:

Type
void

------------------------------------------------------------------------

#### getGeometry()

Returns the geometry that has been created by this tool.

Overrides:
- [OM.tool.Tool#getGeometry](OM.tool.Tool.md)

##### Returns:

The geometry created by this tool; or null if none has been created.

Type
[OM.geometry.Geometry](OM.geometry.Geometry.md)

------------------------------------------------------------------------

#### getGeometryType()

Returns the type of geometry that can be created by this Redline Tool instance.

##### Returns:

an geometry type such as RedlineTool.TYPE_POINT, TYPE_LINESTRING or TYPE_POLYGON.

Type
number

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

#### removeVertex(index, isRedo)

This method removes a shape point.

##### Parameters:

| Name     | Type | Description                                                                    |
|----------|------|--------------------------------------------------------------------------------|
| `index`  | int  | Indicates the position of the point to remove, starting from 0.                |
| `isRedo` | bool | Optional If set to true, the edit won't generate an entry in the undo manager. |

------------------------------------------------------------------------

#### setDrawingStyle(options)

Set a drawing style for the tool. Should be called twice, once to set the point style for vertices
and once to set the line style for the segments.

##### Parameters:

| Name      | Type | Description                                                                                                                                                                                                                                                                                                 |
|-----------|------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | int  | An object with two properties, type and style, which<br>define the geometry type and the style.<br><br>• type Specifies the geometry type. Must be one of two pre-defined constants:<br>OM.tool.RedlineTool.TYPE_POINT or OM.tool.RedlineTool.TYPE_LINESTRING.<br>• style {OM.style.Style} The style to use |

Overrides:
- [OM.tool.Tool#setDrawingStyle](OM.tool.Tool.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setStyle(options)

Set rendering style for the completed feature.

##### Parameters:

| Name      | Type | Description                                                                                                                                                                                                                                                                                                                                        |
|-----------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | int  | An object with two properties, type and style, which<br>define the geometry type and the style.<br><br>• type Specifies the geometry type. Must be one of three pre-defined constants:<br>OM.tool.RedlineTool.TYPE_POINT, OM.tool.RedlineTool.TYPE_LINESTRING, or<br>OM.tool.RedlineTool.TYPE_POLYGON<br>• style {OM.style.Style} The style to use |

Overrides:
- [OM.tool.Tool#setStyle](OM.tool.Tool.md)

##### Returns:

Type
OM.tool.RedlineTool
