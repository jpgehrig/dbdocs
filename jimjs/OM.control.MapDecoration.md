------------------------------------------------------------------------

#### new MapDecoration(content, options)

An abstract class for map decorations.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `content` | String | An html string defines the decoration content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `options` | Object | An object, or literal, with either of the following attributes:<br>• offsetX {int} in pixels to the dock icon<br>• offsetY {int} in pixels to the dock icon<br>• draggable {boolean} True if draggable, false if fixed.<br>• collapsible {boolean} defines the collapsible value true/false<br>• width {int} Decoration width in pixels<br>• height {int} Decoration height in pixels<br>• title {Sting} the title of the decoration<br>• titleStyle {Object}: A CSS definition for the Decoration title style. For example:<br>titleStyle:{"border-style":"solid",<br>"border-color":"#391EA6",<br>"border-width":"1px",<br>"backgroundColor":"#0D0D0D",<br>"font-size":"18px",<br>"font-weight":"bold",<br>"color":"#FDFDFD"<br>}<br><br>• contentStyle {Object}: A CSS definition for the Decoration content style. For example:<br>contentStyle: {"border-style":"solid",<br>"border-color":"#101418",<br>"border-width":"2px",<br>"padding":"0px",<br>"font-size":"16px",<br>"color":"#000000",<br>"backgroundColor":"#FDFDFD"<br>}<br> |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

##### Returns:

An instance of OM.control.MapDecoration

Type
OM.control.MapDecoration

### Methods

------------------------------------------------------------------------

#### isVisible()

Get the visibility of the decoration.

##### Returns:

True if the decoration is currently visible,
False if the decoration is currently not visible.

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### setDraggable()

Set whether the decoration should be draggable

##### Parameters:

| Name         | Type    | Description                      |
|--------------|---------|----------------------------------|
| `draggable.` | Boolean | True if draggable, false if not. |

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

##### Returns:

Type
void
