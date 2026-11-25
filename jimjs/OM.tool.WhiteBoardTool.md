------------------------------------------------------------------------

#### new WhiteBoardTool(map)

A subclass of OM.tool.Tool that can be used in a white-boarding scenario. The main
use case is for adding dynamic text annotations to any location on the map. Once
added, the text can be edited, rotated, or repositioned on the map.

Note that in order to use the WhiteBoardTool, you must manually include the following
CSS and script tags to the header section of your page.
Specifically, add these two lines before the script tag that imports the oraclemapsv2.js file:

     <link rel='stylesheet' type='text/css' href='/mapviewer/jslib/v2/jquery/css/redmond/jquery-ui-1.8.16.custom.css'/>
     <link rel='stylesheet' type='text/css' href='/mapviewer/jslib/v2/jquery/colorpicker/css/colorpicker.css'/>

Add the following tags after the script tag that imports the oraclemapsv2.js file:

    <script type='text/javascript' src='/mapviewer/jslib/v2/jquery/jquery-ui-1.8.16.min.js'></script>
    <script type='text/javascript' src='/mapviewer/jslib/v2/jquery/colorpicker/js/colorpicker.js'></script>
    <script type='text/javascript' src='/mapviewer/jslib/v2/jquery/colorpicker/js/eye.js'></script>
    <script type='text/javascript' src='/mapviewer/jslib/v2/jquery/colorpicker/js/layout.js'></script>
    <script type='text/javascript' src='/mapviewer/jslib/v2/jquery/colorpicker/js/utils.js'></script>

##### Parameters:

| Name  | Type                | Description  |
|-------|---------------------|--------------|
| `map` | [OM.Map](OM.Map.md) | A map object |

##### Returns:

An instance of OM.tool.WhiteBoardTool

Type
OM.tool.WhiteBoardTool

### Extends

- [OM.tool.Tool](OM.tool.Tool.md)

### Methods

------------------------------------------------------------------------

#### clear()

Clear all text features created by this tool

##### Returns:

Type
OM.tool.WhiteBoardTool

------------------------------------------------------------------------

#### finish()

Finish the whiteboard tool.

##### Returns:

Type
OM.tool.WhiteBoardTool

------------------------------------------------------------------------

#### getAllTextFeatures()

Gets all text features which are added by this white board tool

##### Returns:

all added text features

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

#### saveToLS(name)

This method saves all text features to localStorage.

##### Parameters:

| Name   | Type   | Description                                                                              |
|--------|--------|------------------------------------------------------------------------------------------|
| `name` | String | specify the name in localStorage. If not set,<br>a name will be generated automatically. |

##### Returns:

Type
void

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

Start the whiteboard tool.

##### Returns:

Type
OM.tool.WhiteBoardTool
