------------------------------------------------------------------------

#### new ScaleBar(options)

This class defines the ScaleBar

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object, or literal, specifying the scale bar. It can contain the following attributes.<br>• format {String}: Specifies the display format (or mode) of ScaleBar.<br>Can be one of three pre-defined options; "BOTH", "METRIC", or "IMPERIAL"<br>• anchorPosition {int}: Specifies where thw scalebar is placed. Can be one of 6 pre-defined options:<br>1--upper left,2--upper center,3--upper right,4--lower left,5--lower center,6--lower right<br>• style {Object}: An object with the following attributes:<br>fontSize {int} The font size in points<br>fontColor {String} The color for the scale bar text. Specified as \#rrggbb e.g. "#cccccc"<br>fontWeight {int} The font weight<br>scaleBarColor {String} The color for the scale bar<br>boxShadow {String} The shadow of the scale bar. e.g "1px 1px 5px \#000000"<br>maxLength {int} the maximum length of the scale bar in pixels<br> |

##### Returns:

Type
OM.control.ScaleBar

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

#### setFormat(format:)

Set the ScaleBar format

##### Parameters:

| Name      | Type   | Description                                                                                                                     |
|-----------|--------|---------------------------------------------------------------------------------------------------------------------------------|
| `format:` | String | Specifies the display format (or mode) of ScaleBar.<br>Can be one of three pre-defined options; "BOTH", "METRIC", or "IMPERIAL" |

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

Set the ScaleBar style

##### Parameters:

| Name           | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `contentStyle` | Object | An object with the following attributes:<br>fontSize {int} The font size in points<br>fontColor {String} The color for the scale bar text. Specified as \#rrggbb e.g. "#cccccc"<br>fontWeight {int} The font weight<br>scaleBarColor {String} The color for the scale bar<br>boxShadow {String} The shadow of the scale bar. e.g "1px 1px 5px \#000000"<br>maxLength {int} the maximum length of the scale bar in pixels |

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
