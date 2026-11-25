------------------------------------------------------------------------

#### new ToolButton(buttonID, buttonType, options)

The class defines a toolbar button.

It fires various events which are instances of [`OM.event.ToolbarEvent`](OM.event.ToolbarEvent.md).
Applications wish to customize a built-in toolbar button's behavior or add a
custom toolbar button should add listeners to such events such as when a toolbar button
is in 'up' or 'down' state.

##### Parameters:

| Name         | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|--------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `buttonID`   | String | A button id                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `buttonType` | int    | The button type. One of three pre-defined values<br>OM.control.ToolButton.COMMAND, OM.control.ToolButton.TOGGLE, or OM.control.ToolButton.SEPARATOR                                                                                                                                                                                                                                                                                                                 |
| `options`    | Object | An object, or literal, specifying the button parameters. It can have the following attributes:<br><br>• buttonName {String} : Optional. The button name<br>• buttonIcon {String} : Optional. The button icon url<br>• buttonSelectedIcon {String} : The button selected icon url<br>• width {int} : Optional. Button width in pixels<br>• height {int} : Optional. Button height in pixels<br>• tooltip {String}: The tool-tip string displayed on mouseover/hover. |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

##### Fires:

- event:ToolbarEvent

##### Returns:

The newly created ToolButton object.

Type
OM.control.ToolButton

### Members

------------------------------------------------------------------------

#### \<static, constant\> COMMAND :Number

Represents a COMMAND type toolbar button.

##### Type:

- Number

------------------------------------------------------------------------

#### \<static, constant\> SEPARATOR :Number

Represents a SEPARATOR type toolbar button.

##### Type:

- Number

------------------------------------------------------------------------

#### \<static, constant\> TOGGLE :Number

Represents a TOGGLE type toolbar button.

##### Type:

- Number

### Methods

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### setToolTip(tooltip)

Set the button's tooltip. It is the text displayed on hover or mouseover.

##### Parameters:

| Name      | Type   | Description          |
|-----------|--------|----------------------|
| `tooltip` | String | The tooltip content. |

##### Returns:

Type
void
