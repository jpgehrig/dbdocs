### Methods

------------------------------------------------------------------------

#### addTab(config)

Create and add tab/content to the Drawer

##### Parameters:

| Name     | Type   | Description                                                                                |
|----------|--------|--------------------------------------------------------------------------------------------|
| `config` | Object | Settings for the new panel.<br>An OM.control.DrawerPanel is created with the given config. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### addToBaseSelArray(f:, opt)

Add a single feature into active selection array

##### Parameters:

| Name  | Type    | Description                                                             |
|-------|---------|-------------------------------------------------------------------------|
| `f:`  | Feature | a feature to be added, single or cluster                                |
| `opt` | Object  | Optional for internal use. Examples: {"origin":"selectActiveSelection"} |

##### Returns:

true if added successfully, false otherwise

Type
Boolean

------------------------------------------------------------------------

#### attachTab(newPanel)

Attach a tab/content pair to the Drawer

##### Parameters:

| Name       | Type                   | Description                  |
|------------|------------------------|------------------------------|
| `newPanel` | OM.control.DrawerPanel | The drawer panel to be added |

##### Returns:

Type
void

------------------------------------------------------------------------

#### clearBaseSelArray()

clear the feature selection array

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### getAllSelectedFeatures()

All visible features. They are clusters and stand-alone (not clusters) features.
The invisible features are single features that are included in a cluster.

##### Returns:

an object contains key-value pairs. Key is the feature's id, the value is an object containing
two properties, the 'f' property for the feature object, and the Boolean 'c' property, true if the feature is a cluster,
false otherwise.

Type
object

------------------------------------------------------------------------

#### getBaseSelArray()

get the currently selected feature array. Features may be grouped in a cluster or stand alone individual features

##### Returns:

------------------------------------------------------------------------

#### getID()

Returns the ID generated for the tab

##### Returns:

Type
Integer

------------------------------------------------------------------------

#### getPanelContent()

Returns the content panel

##### Returns:

Type
Object

------------------------------------------------------------------------

#### getPanelTab()

Returns the tab object

##### Returns:

Type
Object

------------------------------------------------------------------------

#### getSingleTabContainer()

Returns the div container for the tab

##### Returns:

Type
Object

------------------------------------------------------------------------

#### getTabHeaderTitle()

Returns the span object that contains the title text

##### Returns:

Type
Object

------------------------------------------------------------------------

#### getTitle()

Returns the tab title

##### Returns:

Type
String

------------------------------------------------------------------------

#### getVectorLayer()

It returns the vectorlayer object of this cluster.

##### Returns:

the vector layer of this cluster

Type
[OM.layer.VectorLayer](OM.layer.VectorLayer.md)

------------------------------------------------------------------------

#### hideDrawer()

Display the drawer when the user clicks in the drawer icon.

##### Returns:

Type
void

------------------------------------------------------------------------

#### initialize(map)

##### Parameters:

| Name  | Type | Description         |
|-------|------|---------------------|
| `map` | type | A map to attach to. |

##### Returns:

progressBar - A ui feedback element.

Type
OM.util.ProgressBar

------------------------------------------------------------------------

#### initialize()

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### initialize(reportTo, taskTipe)

##### Parameters:

| Name       | Type             | Description                                            |
|------------|------------------|--------------------------------------------------------|
| `reportTo` | OM.util.Progress | A subscriber to bind to. Usually the Progress service. |
| `taskTipe` | String           | Optional type of task.                                 |

##### Returns:

- A task.

Type
OM.util.Task

------------------------------------------------------------------------

#### isVisible()

Used to check if the drawer is visible or not.

##### Returns:

true if the drawer is visible, false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### moveTabsToLeft()

Scroll to the left across to the tab bar

##### Returns:

Type
void

------------------------------------------------------------------------

#### moveTabsToRight()

Scroll to the right across to the tab bar

##### Returns:

Type
void

------------------------------------------------------------------------

#### publish(publication, type)

Alerts subscribers of the passed type and provides a message to them.

##### Parameters:

| Name          | Type | Description           |
|---------------|------|-----------------------|
| `publication` | type | The message to pass   |
| `type`        | type | The subscription type |

##### Returns:

Type
void

------------------------------------------------------------------------

#### removeFromBaseSelArray(f, opt)

Remove a single feature or a clsuter from the active selection array

##### Parameters:

| Name  | Type                        | Description                                                                                                                                                  |
|-------|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `f`   | [OM.Feature](OM.Feature.md) | A feature to be removed from the active selection array.<br>If it is a cluster, then all features contained will be removed from the active selection array. |
| `opt` | Object                      | Optional for internal use. Examples: {"origin":"selectActiveSelection"}                                                                                      |

##### Returns:

true if removed successfully, false otherwise

Type
Boolean

------------------------------------------------------------------------

#### setBaseSelArray()

set the currently selected feature array. Features may be grouped in a cluster or stand alone individual features

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setPosition(dir)

Set the position of the drawer in the right or left side of the parent div

##### Parameters:

| Name  | Type    | Description                                   |
|-------|---------|-----------------------------------------------|
| `dir` | Integer | The position where the drawer will be placed. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### showDrawer()

Display the drawer when the user clicks in the drawer icon.

------------------------------------------------------------------------

#### subscribe(fn, type)

used to subscribe some function to our updates.

##### Parameters:

| Name   | Type     | Description                                                         |
|--------|----------|---------------------------------------------------------------------|
| `fn`   | function | The subscribing function                                            |
| `type` | String   | The type of updates that will notify the function. Default is 'any' |

##### Returns:

Type
void

------------------------------------------------------------------------

#### switchMode(mode)

##### Parameters:

| Name   | Type                      | Description                    |
|--------|---------------------------|--------------------------------|
| `mode` | OM.util.ProgressBar.modes | Type of progress to represent. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### update(update)

##### Parameters:

| Name     | Type   | Description                               |
|----------|--------|-------------------------------------------|
| `update` | Number | Any number between 0 and 1, non inclusive |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### updateProgress()

Polls all tasks and returs global advance.

##### Returns:

Type
Number

------------------------------------------------------------------------

#### updateScrollButtons()

Scroll to the right across to the tab bar

##### Returns:

Type
void

------------------------------------------------------------------------

#### updateUi(update)

##### Parameters:

| Name     | Type | Description |
|----------|------|-------------|
| `update` | type |             |

##### Returns:

Type
undefined
