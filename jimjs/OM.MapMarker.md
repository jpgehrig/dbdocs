------------------------------------------------------------------------

#### new MapMarker(mObj)

##### Parameters:

| Name   | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mObj` | Object | An object that specifies the attributes of a marker. It may contain the following attributes.<br>• id {String}: The unique id for the map marker.<br>• label {String}: Optional. The marker's label text.<br>• labelStyle {OM.style.Text}: Optional. The label style of the marker.<br>• markerText {String}: Optional. The text on the marker.<br>• markerTextStyle {OM.style.Text}: Optional. The text style on the marker.<br>• draggable {Boolean}: Optional. If set to true, the marker is draggable.<br>• renderingStyle {OM.style.Marker}: Optional. The rendering style for the marker.<br>A default marker style will be used if the rendering style is not specified.<br>• position {Object}: An object specifying the marker's point location. It may contain the following attributes.<br>• x {Number}: The marker's x coordinate<br>• y {Number}: The marker's y coordinate<br>• srid {Integer}: Optional. The coordinate system for the above x,y values. Default is 8307<br>• dragStart {Function}: Optional. The drag start event listener function.<br>• dragging {Function}: Optional. The dragging event listener function.<br>• dragEnd {Function}: Optional. The drag end event listener function. |

##### Returns:

An instance of OM.MapMarker.

Type
OM.MapMarker

### Extends

- [OM.Feature](OM.Feature.md)

### Members

------------------------------------------------------------------------

#### clipMap

A map of rectangle geometries in data coordinates to be used in clipping feature geometry elements.
Clip area is defined by tile (zoom, x index, and y index)

Inherited From:
- [OM.Feature#clipMap](OM.Feature.md)

------------------------------------------------------------------------

#### tiledFeature

Ideintifies if feature geometries are part of a vector tile layer.

Inherited From:
- [OM.Feature#tiledFeature](OM.Feature.md)

------------------------------------------------------------------------

#### tileGeometries

For vector tile layers: the feature geometry is defined by tile (zoom, x index, and y index)
Each tile stores the feature geometry elements.

Inherited From:
- [OM.Feature#tileGeometries](OM.Feature.md)

------------------------------------------------------------------------

#### tooltipCache

Cached tooltip definition

Inherited From:
- [OM.Feature#tooltipCache](OM.Feature.md)

------------------------------------------------------------------------

#### zoomLevelsGeomClipArea

The clip area for each element of vector tile layer feature by zoom level.
A feature geometry in vector tile is build as a geometry collection, with each element
being part of a different tile.
This is used when rendering the full feature geometry which can have pieces in different tiles.

Inherited From:
- [OM.Feature#zoomLevelsGeomClipArea](OM.Feature.md)

------------------------------------------------------------------------

#### zoomLevelsGeometries

Store the feature geometry for a scpecifi level.
For tiled features, a geometry collection can have parts from different tiles.

Inherited From:
- [OM.Feature#zoomLevelsGeometries](OM.Feature.md)

### Methods

------------------------------------------------------------------------

#### animateToNewLocation(newLocation, options)

Move the FOI to a new location using an animation

##### Parameters:

| Name          | Type                                            | Description                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `newLocation` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | a point or polyline geometry that specifies<br>the path along which the FOI moves. If it is a point geometry, the FOI will<br>move along the straight line from its current location to the new location.<br>If it is a polyline geometry, the FOI will move along the path defined by the polyline.                                                                                             |
| `options`     | Object                                          | This can have the following attributes:<br><br>• time {int} I milliseconds. It affects the feature moving speed. The default value is 300. A larger<br>value results in a slower movement.<br>• loop {Boolean} If true, restart the animation from the origin after it is completed<br>• bounce {Boolean} If true, the feature will bounce back to the origin after the initial animated motion. |

Inherited From:
- [OM.Feature#animateToNewLocation](OM.Feature.md)

------------------------------------------------------------------------

#### bringForward()

Brings the feature to the front by one z-index level
( i.e. closer to the top of the displayed feature layers).

Inherited From:
- [OM.Feature#bringForward](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### bringToTop()

Brings the feature all the way to the top of the displayed features or layers.
(i.e. this becomes the topmost feature

Inherited From:
- [OM.Feature#bringToTop](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableMarkerDraggable(b)

set draggable status (for map markers)

##### Parameters:

| Name | Type    | Description                         |
|------|---------|-------------------------------------|
| `b`  | boolean | true for draggable, false otherwise |

Inherited From:
- [OM.Feature#enableMarkerDraggable](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### getAliasColumnName(column)

Gets the attribute map name for the specified data column in this feature.

##### Parameters:

| Name     | Type   | Description                                |
|----------|--------|--------------------------------------------|
| `column` | String | the name of the data column to find a map. |

Inherited From:
- [OM.Feature#getAliasColumnName](OM.Feature.md)

##### Returns:

the mapped attribute name, or null if no
map for the input column is found.

Type
String

------------------------------------------------------------------------

#### getAttributes()

Returns all the attributes for this feature. You can look
up each attribute's value based on its name. Note that all
attribute names are stored in uppercase internally.

Inherited From:
- [OM.Feature#getAttributes](OM.Feature.md)

##### Returns:

the attributes object e.g. {"NAME":"Super Store", "SALES":5000}

Type
Object

------------------------------------------------------------------------

#### getAttributeValue(name)

Gets the current value for the specified attribute in this feature.

##### Parameters:

| Name   | Type   | Description                               |
|--------|--------|-------------------------------------------|
| `name` | String | the name of the attribute to be returned. |

Inherited From:
- [OM.Feature#getAttributeValue](OM.Feature.md)

##### Returns:

the value for the given attribute, or null if no
attribute with the given name was found.

Type
Object

------------------------------------------------------------------------

#### getClusteredFeatures()

Returns the clustered features that are in this clustered feature, null if this feature is not a cluster feature

Inherited From:
- [OM.Feature#getClusteredFeatures](OM.Feature.md)

##### Returns:

a arrays of features. .

Type
Array

------------------------------------------------------------------------

#### getClusterFeature()

Returns the cluster feature where this primitive feature is grouped in.

Inherited From:
- [OM.Feature#getClusterFeature](OM.Feature.md)

##### Returns:

a cluster feature where the current feature is included;
null if this primitive feature is not in a cluster.

Type
[OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### getClusterId()

Returns its cluster ID, if in a cluster; null otherwise

Inherited From:
- [OM.Feature#getClusterId](OM.Feature.md)

##### Returns:

a cluster ID.

Type
String

------------------------------------------------------------------------

#### getFeaturesInCluster()

For a clustered feature, all features in it will be returned.
For a normal (single) feature, null will be returned.

Inherited From:
- [OM.Feature#getFeaturesInCluster](OM.Feature.md)

##### Returns:

\[Array\] feature array or null.

------------------------------------------------------------------------

#### getGeometry()

Return the feature's geometry

Inherited From:
- [OM.Feature#getGeometry](OM.Feature.md)

##### Returns:

the current feature geometry

Type
[OM.geometry.Geometry](OM.geometry.Geometry.md)

------------------------------------------------------------------------

#### getID()

Gets the marker id

##### Returns:

the marker id

Type
String

------------------------------------------------------------------------

#### getLabel()

Gets the marker label value

##### Returns:

the marker label value

Type
String

------------------------------------------------------------------------

#### getLabelingStyle()

Gets the current labeling style.

Inherited From:
- [OM.Feature#getLabelingStyle](OM.Feature.md)

##### Returns:

The label style

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getMarkerSRID()

Gets the marker's spatial reference (coordinate system) id.

##### Returns:

the srid

Type
Number

------------------------------------------------------------------------

#### getMarkerText()

Gets text on a Marker feature.

Inherited From:
- [OM.Feature#getMarkerText](OM.Feature.md)

##### Returns:

Type
String

------------------------------------------------------------------------

#### getMarkerX()

Gets the marker's x coordinate

##### Returns:

the x coordinate

Type
Number

------------------------------------------------------------------------

#### getMarkerY()

Gets the marker's y coordinate

##### Returns:

the y coordinate

Type
Number

------------------------------------------------------------------------

#### getPosition()

Gets the marker's position.

##### Returns:

an Object containing x, y, and srid

Type
Object

------------------------------------------------------------------------

#### getRealColumnName(attr)

Gets the real, original column name for the specified attribute in this feature.

##### Parameters:

| Name   | Type   | Description        |
|--------|--------|--------------------|
| `attr` | String | the attribute name |

Inherited From:
- [OM.Feature#getRealColumnName](OM.Feature.md)

##### Returns:

the real, original column name, or null if the input attribute name
is not mapped to one.

Type
String

------------------------------------------------------------------------

#### getRenderingStyle()

Get the rendering style

Inherited From:
- [OM.Feature#getRenderingStyle](OM.Feature.md)

##### Returns:

the current rendering style for the feature

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getStyle()

Gets the map marker's rendering style

##### Returns:

the map marker's rendering style

Type
[OM.style.Marker](OM.style.Marker.md)

------------------------------------------------------------------------

#### hasAttributes()

Check if the feature has the optional attributes object

Inherited From:
- [OM.Feature#hasAttributes](OM.Feature.md)

##### Returns:

true if it does, false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### isCluster()

This method checks whether this is a clustered feature.

Inherited From:
- [OM.Feature#isCluster](OM.Feature.md)

##### Returns:

true if feature is clustered and false if not.

Type
Boolean

------------------------------------------------------------------------

#### isDraggable()

Checks if the map marker is draggable.

##### Returns:

true if the marker is draggable, false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### isEditable()

This method checks whether the feature is editable or not.

Inherited From:
- [OM.Feature#isEditable](OM.Feature.md)

##### Returns:

true if feature is editable and false if not.

Type
Boolean

------------------------------------------------------------------------

#### isInCluster()

Returns a Boolean value to indicate if the current feature is in a cluster.

Inherited From:
- [OM.Feature#isInCluster](OM.Feature.md)

##### Returns:

true if this feature in in a cluster; false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### isVisible()

Checks whether the feature is currently visible.

Inherited From:
- [OM.Feature#isVisible](OM.Feature.md)

##### Returns:

true it is visible, false if not.

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.Feature#on](OM.Feature.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### sendBackward()

Sends the feature to the back by one z-index level
(i.e. closer to the bottom of the displayed feature layers).

Inherited From:
- [OM.Feature#sendBackward](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### sendToBottom()

Sends the feature all the way to the bottom of the displayed features or layers

Inherited From:
- [OM.Feature#sendToBottom](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDragEndListener(endListener)

Sets the end-drag event listener

##### Parameters:

| Name          | Type     | Description           |
|---------------|----------|-----------------------|
| `endListener` | function | the drag-end listener |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDraggable(draggable)

Sets the map marker's draggable status: true for draggable, flase otherwise.

##### Parameters:

| Name        | Type    | Description                               |
|-------------|---------|-------------------------------------------|
| `draggable` | Boolean | Set to true to make the marker draggable. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDraggingListener(draggingListener)

Sets the dragging event listener

##### Parameters:

| Name               | Type     | Description            |
|--------------------|----------|------------------------|
| `draggingListener` | function | the dragStart listener |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDragStartListener(dragStart)

Sets the start-drag event listener

##### Parameters:

| Name        | Type     | Description             |
|-------------|----------|-------------------------|
| `dragStart` | function | the drag-start listener |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setGeometry(geom)

Sets a geometry for the feature. The new geometry should be of the same type
as the existing one, otherwise this call does nothing and returns false.

##### Parameters:

| Name   | Type                                            | Description                |
|--------|-------------------------------------------------|----------------------------|
| `geom` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | the new geometry to be set |

Inherited From:
- [OM.Feature#setGeometry](OM.Feature.md)

##### Returns:

returns true if geometry is set; false otherwise

Type
Boolean

------------------------------------------------------------------------

#### setID(id)

Sets the id

##### Parameters:

| Name | Type   | Description   |
|------|--------|---------------|
| `id` | String | the marker id |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setInfoWindowContent(html)

Sets the info window (html) content

##### Parameters:

| Name   | Type   | Description              |
|--------|--------|--------------------------|
| `html` | String | the info window content. |

Inherited From:
- [OM.Feature#setInfoWindowContent](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setLabel(label)

Sets the label text on the feature.

##### Parameters:

| Name    | Type   | Description               |
|---------|--------|---------------------------|
| `label` | String | The label text to be set. |

Inherited From:
- [OM.Feature#setLabel](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setLabelingStyle(style)

Sets the labeling style to be used when rendering label text.

##### Parameters:

| Name    | Type                                | Description                   |
|---------|-------------------------------------|-------------------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The style used for label text |

Inherited From:
- [OM.Feature#setLabelingStyle](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMarkerText(text)

Sets text on Marker feature.

##### Parameters:

| Name   | Type   | Description                         |
|--------|--------|-------------------------------------|
| `text` | String | the text string to add on a marker. |

Inherited From:
- [OM.Feature#setMarkerText](OM.Feature.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMarkerTextStyle(style)

Sets the map marker's text style

##### Parameters:

| Name    | Type                              | Description                  |
|---------|-----------------------------------|------------------------------|
| `style` | [OM.style.Text](OM.style.Text.md) | A OM.style.Text style object |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setPosition(x, y, srid)

Sets the marker's position.

##### Parameters:

| Name   | Type   | Description                            |
|--------|--------|----------------------------------------|
| `x`    | Number | the x value to set                     |
| `y`    | Number | the y value to set                     |
| `srid` | Number | the srid value to set, default is 8307 |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setRenderingStyle(style)

Set a style

##### Parameters:

| Name    | Type                                | Description                                |
|---------|-------------------------------------|--------------------------------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The rendering style to use for the feature |

Inherited From:
- [OM.Feature#setRenderingStyle](OM.Feature.md)

------------------------------------------------------------------------

#### setStyle(sty)

Sets a map marker's rendering style

##### Parameters:

| Name  | Type                                  | Description                     |
|-------|---------------------------------------|---------------------------------|
| `sty` | [OM.style.Marker](OM.style.Marker.md) | The map marker rendering style. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setVisible(visible)

Sets the visibility of the feature.

##### Parameters:

| Name      | Type    | Description |
|-----------|---------|-------------|
| `visible` | Boolean |             |

Inherited From:
- [OM.Feature#setVisible](OM.Feature.md)

##### Returns:

Type
void
