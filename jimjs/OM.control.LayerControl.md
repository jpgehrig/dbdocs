------------------------------------------------------------------------

#### new LayerControl(options)

The LayerControl class
A LayerControl is a map decoration used to list the currently displayed map layers and optionally show or hide them.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object, or literal, with the following attributes.<br>• anchorPosition {int} Specify where a collapsed layer control will be docked,<br>as well as where the docker icon is positioned.<br>A set of 6 predefined positions for the panel. The 6 values are: 1--upper left,2--upper center,<br>3--upper right,4--lower left,5--lower center,6--lower right<br>• offsetX {int} in pixels to the dock icon<br>• offsetY {int} in pixels to the dock icon<br>• layerDeleteEnable {boolean} true:the delete icon will show up when a vector is highlighted. The default value is false.<br>• contentStyle {Object} Specifies the minimum width and maximum height of the panel, and the font used to display the<br>layer names. This object has the following attributes:<br><br>• minWidth {int} The minimum width of the panel (in pixels)<br>• maxHeight {int} The maximum height of the panel (in pixels)<br>• font_size (int} Font size in points<br>• font_family {String} Font family name (e.g. Arial)<br>• <br><br>• titleStyle {Object} Specify the font to use for the title text.<br>This object has the folowing attributes:<br><br>• font_size (int} Font size in points<br>• font_family {String} Font family name (e.g. Arial)<br>• <br> |

##### Returns:

An instance of OM.control.LayerControl

### Extends

- [OM.control.MapDecoration](OM.control.MapDecoration.md)

### Methods

------------------------------------------------------------------------

#### isVisible()

Get the visibility of the decoration.

Inherited From:
- [OM.control.MapDecoration#isVisible](OM.control.MapDecoration.md)

##### Returns:

True if the decoration is currently visible,
False if the decoration is currently not visible.

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

#### setDraggable()

Set whether the decoration should be draggable

##### Parameters:

| Name         | Type    | Description                      |
|--------------|---------|----------------------------------|
| `draggable.` | Boolean | True if draggable, false if not. |

Inherited From:
- [OM.control.MapDecoration#setDraggable](OM.control.MapDecoration.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setPosition(offsetX, offsetY)

Set the map decoration position

##### Parameters:

| Name      | Type  | Description                                                                                    |
|-----------|-------|------------------------------------------------------------------------------------------------|
| `offsetX` | Float | in pixels to the dock icon if the value is greater than 1, or percentage if it is less than 1. |
| `offsetY` | Float | in pixels to the dock icon if the value is greater than 1, or percentage if it is less than 1. |

Inherited From:
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

Set the visibility.

##### Parameters:

| Name      | Type    | Description                    |
|-----------|---------|--------------------------------|
| `visible` | Boolean | True if visible, false if not. |

Inherited From:
- [OM.control.MapDecoration#setVisible](OM.control.MapDecoration.md)

##### Returns:

Type
void
