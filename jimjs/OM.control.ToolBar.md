------------------------------------------------------------------------

#### new ToolBar(toolBarID, options)

The ToolBar class defines a draggable toolbar that is a container for
multiple control buttons. Each button controls an Oracle Maps
built-in tool (such as the Circle, Rectangle, or Redline tool)
or a custom/user-defined one. Each button must also have associated event handlers for
responding to mouse, touch, or other events.
The toolbar can be displayed in two orientations, vertical or horizontal.

The built-in tools are : Redline, Distance,
Circle, Rectangle, and Marquee Zoom. The application can choose
to display control buttons for all or some of these built-in tools in the toolbar.

The tool bar can also hold custom tool buttons for application
specific operations.

A tool button has one of the following two types:

- COMMAND: A command button has only one state, UP, and always reacts to mouse
  clicks by invoking the same BUTTON_DOWN event listener.
- TOGGLE: A toggle button has two states, DOWN and UP. The initial state of
  the button is UP. Its state changes to DOWN after it is clicked.
  It stays DOWN until it is clicked again, after which its state
  changes to UP. The BUTTON_DOWN event listener is invoked when the
  button state changes from UP to DOWN. The BUTTON_UP event listener
  is invoked when the button state changes from DOWN to UP.
- SEPERATOR: A seperator simply displays a static seperator icon that does not
  react to any user actions.

Multiple buttons are organized as a button group,
and only one button can be in the DOWN (or enabled) state at any time. Enabling a
button will automatically disable (i.e. change state from DOWN to UP) the other currently enabled button if any.
All built-in tool buttons, except the Marquee Zoom button, are TOGGLE type buttons organized in the
same button group. The Marquee Zoom button is a TOGGLE type button, but does not belong to any
button group.

##### Parameters:

| Name        | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `toolBarID` | String | A string that specifies the id of the toolbar.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `options`   | Object | An object, or literal, specifying the toolbar. It contains the following attributes:<br><br>• builtInButtons {Array}: An array that specifies the built-in tool buttons to be<br>included in the tool bar. Each array element identifies a built-in tool to be included. The values can be<br>one or more of the followng pre-defind constants:<br>OM.control.ToolBar.BUILTIN_CIRCLE,<br>OM.control.ToolBar.BUILTIN_RECTANGLE,<br>OM.control.ToolBar.BUILTIN_REDLINE,<br>OM.control.ToolBar.BUILTIN_DISTANCE,<br>OM.control.ToolBar.BUILTIN_MARQUEE_ZOOM,<br>OM.control.ToolBar.BUILTIN_ALL.<br>To include all built-in tool buttons, you can use an array with a single<br>OM.control.ToolBar.BUILTIN_ALL element.<br>e.g builtInButtons:\[OM.control.ToolBar.BUILTIN_MARQUEE_ZOOM, OM.control.ToolBar.BUILTIN_DISTANCE\]<br>will include the MarqueZoom and Distance tools only.<br><br>• orientation {int} : One or two pre-defined constants,<br>OM.control.ToolBar.VERTICAL or OM.control.ToolBar.HORIZONTAL.<br><br>• enableClear {boolean} : If true,clear button will be add ,false will not<br> |

##### Returns:

The newly created toolbar object.

Type
OM.control.ToolBar

### Extends

- [OM.control.MapDecoration](OM.control.MapDecoration.md)

### Methods

------------------------------------------------------------------------

#### addButton(btObject)

Add a button to the tool bar.

##### Parameters:

| Name       | Type                                              | Description        |
|------------|---------------------------------------------------|--------------------|
| `btObject` | [OM.control.ToolButton](OM.control.ToolButton.md) | The button to add. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### addSeparator(buttonID)

Add a separator to the tool bar. It creates a button of type SEPARATOR and adds it to the tool bar.

##### Parameters:

| Name       | Type   | Description                                                                                                          |
|------------|--------|----------------------------------------------------------------------------------------------------------------------|
| `buttonID` | String | The id of the newly created SEPARATOR button.<br>This id is used to delete this SEPARATOR button instance if needed. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableBuiltInButton(builtInButtons)

Add built-in buttons to the tool bar

##### Parameters:

| Name             | Type  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `builtInButtons` | Array | An array that specifies the built-in tool buttons to be<br>included in the tool bar. Each array element specifies one<br>built-in tool bar to be included. It can be one of the following values,<br>OM.control.ToolBar.BUILTIN_CIRCLE,<br>OM.control.ToolBar.BUILTIN_RECTANGLE,<br>OM.control.ToolBar.BUILTIN_REDLINE,<br>OM.control.ToolBar.BUILTIN_DISTANCE,<br>OM.control.ToolBar.BUILTIN_MARQUEE_ZOOM,<br>OM.control.ToolBar.BUILTIN_ALL.<br>To include all built-in buttons, use an array with a single<br>OM.control.ToolBar.BUILTIN_ALL element. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### getBuiltInTool(name)

Get a built-in tool

##### Parameters:

| Name   | Type | Description                                                                                                                                                                                                                                                                                      |
|--------|------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | int  | Identifies the required tool name. It can be one of the following pre-defined constants<br>OM.control.ToolBar.BUILTIN_CIRCLE,<br>OM.control.ToolBar.BUILTIN_RECTANGLE,<br>OM.control.ToolBar.BUILTIN_REDLINE,<br>OM.control.ToolBar.BUILTIN_DISTANCE,<br>OM.control.ToolBar.BUILTIN_MARQUEE_ZOOM |

##### Returns:

Type
OM.control.Tool

------------------------------------------------------------------------

#### getBuiltInToolButton(name)

Get a built-in tool button

##### Parameters:

| Name   | Type | Description                                                                                                                                                                                                                                                                                                                           |
|--------|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | int  | Identifies the required tool name. It can be one of the following pre-defined constants<br>OM.control.ToolBar.BUILTIN_CLEAR,<br>OM.control.ToolBar.BUILTIN_CIRCLE,<br>OM.control.ToolBar.BUILTIN_RECTANGLE,<br>OM.control.ToolBar.BUILTIN_REDLINE,<br>OM.control.ToolBar.BUILTIN_DISTANCE,<br>OM.control.ToolBar.BUILTIN_MARQUEE_ZOOM |

##### Returns:

Type
[OM.control.ToolButton](OM.control.ToolButton.md)

------------------------------------------------------------------------

#### isVisible()

Get the visibility of the map toolbar.

Overrides:
- [OM.control.MapDecoration#isVisible](OM.control.MapDecoration.md)

##### Returns:

True if the toolbar is currently visible,
False if the toolbar is currently not visible

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.control.MapDecoration#on](OM.control.MapDecoration.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### removeButton(btObject)

Delete a button from the tool bar.

##### Parameters:

| Name       | Type                                              | Description           |
|------------|---------------------------------------------------|-----------------------|
| `btObject` | [OM.control.ToolButton](OM.control.ToolButton.md) | The button to remove. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### removeSeparator(buttonID)

Delete a separator from the tool bar.

##### Parameters:

| Name       | Type   | Description                     |
|------------|--------|---------------------------------|
| `buttonID` | String | The id of the SEPARATOR button. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDraggable(draggable)

Set the map toolbar draggable.

##### Parameters:

| Name        | Type    | Description                                                                                |
|-------------|---------|--------------------------------------------------------------------------------------------|
| `draggable` | Boolean | If true the toolbar is draggable. If false it is not draggable, the default value is true. |

Overrides:
- [OM.control.MapDecoration#setDraggable](OM.control.MapDecoration.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setPosition(left, top)

Set the position of the map toolbar object.
The positioning of the toolbar object is specified by its position relative to the upper-left corner of the map.
The relative position, or offset, is not specified in pixels, but instead as a
percentage relative to the map window size.
The parameter, left, determines the horizontal position.
The parameter, top, determines the verical position.
Both left and top are of type float and must be a value between 0 and 1.
The absolute offset (in pixels) of the toolbar object center is calculated as follows:
left*map_window_width
top*map_window_height

For example, setPosition(0.2, 0.2) for a map window of size 640x480 will center the
toolbar at 128 pixels from the left and 96 pixels from the top of the map window.

##### Parameters:

| Name   | Type  | Description                                                                                         |
|--------|-------|-----------------------------------------------------------------------------------------------------|
| `left` | float | The horizontal position of the map toolbar object relative<br>to the left border of the map window. |
| `top`  | float | The vertical position of the map toolbar<br>object relative to the top border of the map window.    |

Overrides:
- [OM.control.MapDecoration#setPosition](OM.control.MapDecoration.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setSize(width, height)

Set the map decoration size

##### Parameters:

| Name     | Type | Description |
|----------|------|-------------|
| `width`  | int  |             |
| `height` | int  |             |

Inherited From:
- [OM.control.MapDecoration#setSize](OM.control.MapDecoration.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setVisible(visible)

Set the map toolbar visibility.

##### Parameters:

| Name      | Type    | Description                                                |
|-----------|---------|------------------------------------------------------------|
| `visible` | Boolean | If true the toolbar is visble. If false it is not visible. |

Overrides:
- [OM.control.MapDecoration#setVisible](OM.control.MapDecoration.md)

##### Returns:

Type
void
