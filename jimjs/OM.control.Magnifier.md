------------------------------------------------------------------------

#### new Magnifier(options)

The Magnifier class
The magnifier displays the current map content at a higher zoom level, i.e. zoomed in further by the specified zoom increment.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object, or literal, specifying the Magnifier. The object has the following properties.<br>• zoomIncrement {int} : The zoom level increment between the main map and the Magnifier<br>• width {int} : The width of the Magnifier panel<br>• height {int}: The height of the Magnifier panel<br>• draggable {boolean} True if draggable, false if fixed.<br>• collapsible {boolean} defines the collapsible value true/false<br>• offsetX {int} in pixels to the dock icon<br>• offsetY {int} in pixels to the dock icon<br>• anchorPosition {int}: Specify where a collapsed magnifier will be docked, and where the magnifier docker icon is positioned.<br>A set of 6 predefined positions for the panel. The 6 values are: 1--upper left,2--upper center,<br>3--upper right,4--lower left,5--lower center,6--lower right<br> |

##### Returns:

An instance of OM.control.Magnifier

Type
OM.control.Magnifier

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
