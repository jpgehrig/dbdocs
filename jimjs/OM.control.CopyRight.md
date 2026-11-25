------------------------------------------------------------------------

#### new CopyRight()

This class defines the CopyRight object

##### Parameters:

| Name       | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options.` | Object | An object, or literal, specifying the content and style. It has the following attributes.<br>• textValue {String}:The copyright text<br>• anchorPosition {int}: One of 6 predefined locations for the copyright text. Possible values (and locatons) are 1--upper left,<br>2--upper center,3--upper right,4--lower left,5--lower center,6--lower right<br>• fontSize {int} The font size in points.<br>• fontFamily {String} The fontFamily e.g. Arial.<br>• fontColor {String} The fontColor e.g. Yellow. |

##### Returns:

An instance of OM.control.CopyRight

Type
OM.control.CopyRight

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

#### setStyle(contentStyle)

Set the text style for the copyright content

##### Parameters:

| Name           | Type   | Description                                                                                                                                                              |
|----------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `contentStyle` | Object | : Object, or literal specifying the font family and size.<br><br>• fontSize {int} The fon t size in points<br>• fontFamily {String} The font-family name, e.g. Helvetica |

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
