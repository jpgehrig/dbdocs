------------------------------------------------------------------------

#### new NavigationPanelBar(options)

This class defines the NavigationPanelBar

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object specifying the navigation panel. It can have the following attributes.<br>• style {int}: Specifies the display mode of NavigationPanelBar, Can be one of four pre-defined options.<br>1--display all, 2--slide bar and zoom buttons only, 3--zoom buttons only, 4--navigation panel only.<br>Default is 3.<br>• anchorPosition {int} : Location of the navigation panel. Can be one of 6 pre-defined options.<br>1--upper left,2--upper center,3--upper right,4--lower left,5--lower center,6--lower right.<br>Default is 1. |

##### Returns:

An instance of OM.control.NavigationPanelBar

Type
OM.control.NavigationPanelBar

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

#### setStyle(mainStyle)

Customize the navigationPanelBar style.

##### Parameters:

| Name        | Type   | Description                                                                                                                                                                                                                                                 |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mainStyle` | Object | An object with four optional attributes.<br>• backgroundColor {String} : The background color for the panel. Specified as \#rrggbb, e.g. "#d3d3d3"<br>• borderColor {String }: The color for the border in the panel. Specified as \#rrggbb, e.g. "#ccd3ca" |

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

------------------------------------------------------------------------

#### setZoomLevelInfoTips(infoTips)

Set zoom level info tips

##### Parameters:

| Name       | Type   | Description                                                     |
|------------|--------|-----------------------------------------------------------------|
| `infoTips` | Object | e.g. {zoomLevel01:"level01Name",zoomLevel02:"level02Name", ...} |
