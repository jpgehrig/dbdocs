------------------------------------------------------------------------

#### new Feature(id, geometry, options)

##### Parameters:

| Name       | Type                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------|-------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `id`       | String                                          | A unique identifier for the feature                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `geometry` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | The feature's geometry                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `options`  | Object                                          | An object containing the client theme options. The object can contain the following:<br>• attributes {Object}. *Optional*. An object specifying the feature attributes. e.g attributes:{name:"myStore", sales:"5000"}<br>• renderingStyle {OM.style.Style}. The rendering style to use. e.g. renderingStyle:myMarkerStyle<br>• label {String}. The label value<br>• labelStyle {OM.style.Style}. Style to use for labeling. e.g. labelStyle:myTextStyle<br>• draggable {Boolean}. *Optional*. Set to true if draggable false if not. Default is *false*<br>• customContent {Object}. An *optional* object for application specific content which is otherwise ignored. /li\><br> |

Mixes In:
- [OM.event.EventSource](OM.event.EventSource.md)

##### Returns:

An instance of OM.Feature

Type
OM.Feature

### Members

------------------------------------------------------------------------

#### clipMap

A map of rectangle geometries in data coordinates to be used in clipping feature geometry elements.
Clip area is defined by tile (zoom, x index, and y index)

------------------------------------------------------------------------

#### tiledFeature

Ideintifies if feature geometries are part of a vector tile layer.

------------------------------------------------------------------------

#### tileGeometries

For vector tile layers: the feature geometry is defined by tile (zoom, x index, and y index)
Each tile stores the feature geometry elements.

------------------------------------------------------------------------

#### tooltipCache

Cached tooltip definition

------------------------------------------------------------------------

#### zoomLevelsGeomClipArea

The clip area for each element of vector tile layer feature by zoom level.
A feature geometry in vector tile is build as a geometry collection, with each element
being part of a different tile.
This is used when rendering the full feature geometry which can have pieces in different tiles.

------------------------------------------------------------------------

#### zoomLevelsGeometries

Store the feature geometry for a scpecifi level.
For tiled features, a geometry collection can have parts from different tiles.

### Methods

------------------------------------------------------------------------

#### animateToNewLocation(newLocation, options)

Move the FOI to a new location using an animation

##### Parameters:

| Name          | Type                                            | Description                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `newLocation` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | a point or polyline geometry that specifies<br>the path along which the FOI moves. If it is a point geometry, the FOI will<br>move along the straight line from its current location to the new location.<br>If it is a polyline geometry, the FOI will move along the path defined by the polyline.                                                                                             |
| `options`     | Object                                          | This can have the following attributes:<br><br>• time {int} I milliseconds. It affects the feature moving speed. The default value is 300. A larger<br>value results in a slower movement.<br>• loop {Boolean} If true, restart the animation from the origin after it is completed<br>• bounce {Boolean} If true, the feature will bounce back to the origin after the initial animated motion. |

------------------------------------------------------------------------

#### bringForward()

Brings the feature to the front by one z-index level
( i.e. closer to the top of the displayed feature layers).

##### Returns:

Type
void

------------------------------------------------------------------------

#### bringToTop()

Brings the feature all the way to the top of the displayed features or layers.
(i.e. this becomes the topmost feature

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

##### Returns:

the value for the given attribute, or null if no
attribute with the given name was found.

Type
Object

------------------------------------------------------------------------

#### getClusteredFeatures()

Returns the clustered features that are in this clustered feature, null if this feature is not a cluster feature

##### Returns:

a arrays of features. .

Type
Array

------------------------------------------------------------------------

#### getClusterFeature()

Returns the cluster feature where this primitive feature is grouped in.

##### Returns:

a cluster feature where the current feature is included;
null if this primitive feature is not in a cluster.

Type
OM.Feature

------------------------------------------------------------------------

#### getClusterId()

Returns its cluster ID, if in a cluster; null otherwise

##### Returns:

a cluster ID.

Type
String

------------------------------------------------------------------------

#### getFeaturesInCluster()

For a clustered feature, all features in it will be returned.
For a normal (single) feature, null will be returned.

##### Returns:

\[Array\] feature array or null.

------------------------------------------------------------------------

#### getGeometry()

Return the feature's geometry

##### Returns:

the current feature geometry

Type
[OM.geometry.Geometry](OM.geometry.Geometry.md)

------------------------------------------------------------------------

#### getLabelingStyle()

Gets the current labeling style.

##### Returns:

The label style

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getMarkerText()

Gets text on a Marker feature.

##### Returns:

Type
String

------------------------------------------------------------------------

#### getRealColumnName(attr)

Gets the real, original column name for the specified attribute in this feature.

##### Parameters:

| Name   | Type   | Description        |
|--------|--------|--------------------|
| `attr` | String | the attribute name |

##### Returns:

the real, original column name, or null if the input attribute name
is not mapped to one.

Type
String

------------------------------------------------------------------------

#### getRenderingStyle()

Get the rendering style

##### Returns:

the current rendering style for the feature

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### hasAttributes()

Check if the feature has the optional attributes object

##### Returns:

true if it does, false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### isCluster()

This method checks whether this is a clustered feature.

##### Returns:

true if feature is clustered and false if not.

Type
Boolean

------------------------------------------------------------------------

#### isEditable()

This method checks whether the feature is editable or not.

##### Returns:

true if feature is editable and false if not.

Type
Boolean

------------------------------------------------------------------------

#### isInCluster()

Returns a Boolean value to indicate if the current feature is in a cluster.

##### Returns:

true if this feature in in a cluster; false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### isVisible()

Checks whether the feature is currently visible.

##### Returns:

true it is visible, false if not.

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### sendBackward()

Sends the feature to the back by one z-index level
(i.e. closer to the bottom of the displayed feature layers).

##### Returns:

Type
void

------------------------------------------------------------------------

#### sendToBottom()

Sends the feature all the way to the bottom of the displayed features or layers

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

##### Returns:

returns true if geometry is set; false otherwise

Type
Boolean

------------------------------------------------------------------------

#### setInfoWindowContent(html)

Sets the info window (html) content

##### Parameters:

| Name   | Type   | Description              |
|--------|--------|--------------------------|
| `html` | String | the info window content. |

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

------------------------------------------------------------------------

#### setVisible(visible)

Sets the visibility of the feature.

##### Parameters:

| Name      | Type    | Description |
|-----------|---------|-------------|
| `visible` | Boolean |             |

##### Returns:

Type
void
