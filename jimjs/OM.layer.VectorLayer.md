------------------------------------------------------------------------

#### new VectorLayer(name, options)

This class defines an interactive layer comprised of vector features of the same type (e.g. customers).
A vector feature layer provides means for user to both interactively select and de-select features
or search features using a circle, rectangle or polygon filters. Features of a vector layer can
be rendered using styles with visual effects such as shadow or gradient. A
feature can also be rendered differently depending on whether it is currently
selected or being hovered on.

The feature data of a vector layer can come from many different sources such as:

- a predefined MapViewer theme
- a JDBC (dynamic SQL) MapViewer theme
- a datapack, which is a geo-json like file.
- a local theme where the vector features are programatically created and added o the layer by the application.
- a GeoRSS feed
- a WFS (Web Feature Service) layer

**Event listeners**

A vector layer may fire various events throughout its life cycle. Applications
can attach event listeners to the layer instance to handle them.
For instance the following statement registers a listener to be invoked
when the layer *myLayer* finishes displaying its feature data:

     myLayer.addListener(OM.event.LayerEvent.FEATURES_DISPLAYED, onFeatureDisplayed);

or using the short handed method *on*:

     myLayer.on(OM.event.LayerEvent.FEATURES_DISPLAYED, onFeatureDisplayed);

In the above code, *OM.event.LayerEvent.FEATURES_DISPLAYED* refers to the type
of event the *onFeatureLoaded* listener is listening for.

For a list of possible event types supported by a layer, please refer to
the constants defined in the class [`OM.event.LayerEvent`](OM.event.LayerEvent.md).

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-----------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | String | The unique layer name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `options` | Object | The layer options object. It may contain the<br>following attributes that define the layer to be created.<br>• renderingStyle {OM.style.Style}: The rendering style for the layer (e.g. a color or marker style)<br>• styleAttributes {Array}: Required only when renderingStyle is an advanced style.<br>It is a list of attribute names used to determine the actual rendering style. For example, the renderingStyle may<br>be a bucket style named salesByRegion with 4 ranges and color styles for each range. Then<br>styleAttributes:\['Revenue'\] means the color used for a specific feature will depend on within which range its<br>Revenue value falls.<br>• boundingTheme {Boolean}: Whether the theme is a bounding theme. Default value is false<br>• infoWindow {Boolean}: Enable (if true), or disable (if false), the feature info window. Default value is true<br>• The following *four optional* attributes are only valid for Predefined and JDBC layers.<br>• dadp {Integer}: Optional. The number of digits after the decimal to use in the co-ordinate values. Example dadp:4 means the oridnate 5.178976 will be truncated to 4 digits after the decimal and output as 5.1789<br>• simplify {Boolean\|: Optional. Whether of not to apply the specification line simplification algorithm on the features.<br>• simplifyAlgorithm {Integer}: Optional. Required when simplify is true. Value can only be either 1 (for Douglas-Peucker) or 2 (for Visvalingam-Whyatt).<br>• threshold {float}: Optional. Required if simplify is true. The value is specific to the algorithm.<br>For Douglas-Peucker Threshold it should be a positive number. (Zero causes the input geometry to be returned.)<br>If the input geometry is geodetic, the value is the number of meters; if the input geometry is non-geodetic, the value is the number of units associated with the data.<br>For Visvalingam-Whyatt it is a percentage value between 0 and 100. As the value is decreased, the returned geometry is likely to be closer to the input geometry; as the value is increased, fewer points are likely to be in the returned geometry.<br><br>• def {Object}: An object literal that specifies the source of the vector data.<br>• type {String}: Use the pre-defined constant OM.layer.VectorLayer.TYPE_PREDEFINED<br>• dataSource {String}: The MapViewer data source name (e.g. 'mvdemo')<br>• theme {String}: Name of the predefined theme (e.g. 'customers')<br>• loadOnDemand {Boolean}: If true, load theme data on demand. If false, load all theme data at one time.<br>Default value is true. If true, then the current map extent is used to filter the theme content. Additional data<br>is loaded as need on pan or zoom.<br>• url {String}: The MapViewer URL (e.g. http://localhost:8888/mapviewer)<br>• xRatio {float}: the factor to increase the internal data buffer width for retrieving features.<br>Value must be 1 or higher. Value 1 means that the features will be retrieved for current map width.<br>Default value is 2. Does not apply to heat map rendering, where this value is fixed to 1.2<br>• yRatio {float}: the factor to increase the internal data buffer height for retrieving features.<br>Value must be 1 or higher. Value 1 means that the features will be retrieved for current map height.<br>Default value is 2. Dos not apply to heat map rendering, where this value is fixed to 1.2<br>• workspace {String}: Oracle Workspace name to access versioned data.<br>• type {String}: Use the pre-defined constant OM.layer.VectorLayer.TYPE_JDBC<br>• dataSource {String}: The MapViewer data source name (e.g. 'mvdemo')<br>• sql {String}: The SQL query (e.g. 'select id, name, revenue, location from customers')<br>• url {String}: The MapViewer URL (e.g. http://localhost:8888/mapviewer)<br>• geometryColumn {String}: The name of the geometry column (e.g. 'location').<br>• labelColumn {String}: The name of the label column (e.g. 'name').<br>• keyColumn {String}: The name of the label column (e.g. 'name').<br>• jdbcSrid {Integer}: The SRID of this layer. Default is 8307.<br>• loadOnDemand{boolean}: If true, load theme data on demand. If false, load all theme data at one time.<br>Default value is true. If true, then the current visible map extent is used to filter the theme content. Additional data<br>is loaded as need on pan or zoom.<br>• workspace {String}: Oracle Workspace name to access versioned data.<br>• type {String}: Use the pre-defined constant OM.layer.VectorLayer.TYPE_DATA_PACK<br>• url {String}: Data pack file URL (e.g. '/mapviewer/datapacks/counties.json')<br>• labelColumn{String}: The name of the label column (e.g. 'countyName').<br>• type {String}: Use the pre-defined constant OM.layer.VectorLayer.TYPE_LOCAL<br>• features {Array}: An array of feature objects. Each element is a OM.Feature.<br>• type {String}: Use the pre-defined constant OM.layer.VectorLayer.TYPE_GEORSS<br>• url {String}: The URL for the GeoRSS feed. |

### Extends

- [OM.layer.Layer](OM.layer.Layer.md)

### Methods

------------------------------------------------------------------------

#### addFeature(feature)

Add a feature to the layer.

##### Parameters:

| Name      | Type                        | Description        |
|-----------|-----------------------------|--------------------|
| `feature` | [OM.Feature](OM.Feature.md) | The feature to add |

##### Returns:

Type
void

------------------------------------------------------------------------

#### addFeatures(features)

Add a feature array to the layer. If the map is displayed, these
features will not be displayed immediately. Call redraw to show them.

##### Parameters:

| Name       | Type  | Description       |
|------------|-------|-------------------|
| `features` | Array | The feature array |

##### Returns:

Type
void

------------------------------------------------------------------------

#### addSecondaryStyle(style)

Add a secondary style to vector layer. A secondary style is typically
a marker or pie/bar chart style that is to be displayed on a feature that's already
being rendered using a (primary) style. If no primary style is set (via the
setRenderingStyle method) the behaviour of secondary style is not defined.

in one vector layer.

##### Parameters:

| Name    | Type                                | Description     |
|---------|-------------------------------------|-----------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The added style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### applyFilter(filter, replace)

Apply a relational filter to layer. A filtered layer will be returned. According to the replace parameter, the filtered
layer may replace the existing layer or as a new layer.

##### Parameters:

| Name      | Type                                    | Description                                                                                                                                                                                                    |
|-----------|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `filter`  | [OM.filter.Filter](OM.filter.Filter.md) | The filter to be applied                                                                                                                                                                                       |
| `replace` | Boolean                                 | If replace is true, then the original layer is removed and<br>replaced with the result layer; If replace is false, the original<br>layer is kept, and the result is returned as a new layer. Default is false. |

##### Returns:

The filtered layer. According to the replace paramter, this retured layer could be either
the same layer with the filter applied or a new layer with the filter applied on the original layer.

Type
OM.layer.VectorLayer

------------------------------------------------------------------------

#### bringForward()

Bring the layer to the front by one step (closer to the top of the map).

Inherited From:
- [OM.layer.Layer#bringForward](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### bringSelectedFeaturesToTop()

Gets all the selected features to the top.

##### Returns:

Type
void

------------------------------------------------------------------------

#### bringToTop()

Bring the layer all the way to the top of the map

Inherited From:
- [OM.layer.Layer#bringToTop](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### centerToTheme()

Center the map to the theme's center point. It automatically pans the map so that it is centered
at the center of the theme's minimum bounding box.

##### Returns:

None

------------------------------------------------------------------------

#### clearSelectedFeatures()

Clear all currently selected features. All features are then displayed
with the default rendering style.

##### Returns:

Type
void

------------------------------------------------------------------------

#### deHover(the)

This method removes the hover effect from a given feature

##### Parameters:

| Name  | Type                        | Description             |
|-------|-----------------------------|-------------------------|
| `the` | [OM.Feature](OM.Feature.md) | feature to be dehovered |

##### Returns:

none

------------------------------------------------------------------------

#### deselectFeature(feature)

Unhighlight/de-select a feature;

##### Parameters:

| Name      | Type                        | Description                  |
|-----------|-----------------------------|------------------------------|
| `feature` | [OM.Feature](OM.Feature.md) | The feature to be deselected |

##### Returns:

The deselected feature object

Type
[OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### deselectFeatures()

since version 12.2.1.3
de-select the already selected features
Note, in the current architecture, an event on a graphics (DOM component) is
processed first in fortknox. Later, the event pops up to the Map object.
Regardless a mouse event (e.g. a click) hits a feature within the vector layer(s), it always eventually
be bubbled up to the Map object. In a no-hit case, if there are any already selected
vector features in a previous click/selection, they need to be de-selected.
But if the event hit features, then the layer has taken care of the de-select and then select.

------------------------------------------------------------------------

#### enableClustering()

Enable client side clustering for point features.

##### Parameters:

| Name       | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enable.`  | Boolean | Whether to enable point clustering.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `options.` | Object  | An object that specifies various clustering options.<br>• threshold {int} The cluster radius in pixesl. Default value is 30 (i.e. points within 30 pixels of each other will be<br>aggregated into a cluster)<br>• clusterStyle {OM.style.Style} The cluster feature rendering style<br>• minPointCount {int} Enable clustering if the number of features in cluster is<br>greater than or equal to this value.<br>• maxClusteringLevel: {int} Enable clustering if current zoom level is less than or equal to<br>this value<br>• enableZoomIn: {boolean} Enable/disable default zoom in behavior when click on a cluster marker.<br>By default, it's enabled.<br>• zoomInLevels: {int} this parameter determines map zoom in levels when click on a cluster marker.<br>By default, mapviewer will calculate a proper zoom level to zoom into.<br>• clickBehavior: {String} two options, either 'zoom' or 'select', default is 'zoom'<br>For 'zoom', a mouse-click on a cluster feature will trigger a zoom-in process to zoom into the cluster features' MBR.<br>For 'select', this cluster will be selected. |

------------------------------------------------------------------------

#### enableDisplayInBatch()

Enable client side batch loading for a vector layer

##### Parameters:

| Name       | Type    | Description                                                                                                                                                   |
|------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enable.`  | Boolean | Whether to enable batch loading.                                                                                                                              |
| `options.` | Object  | An object that specifies two batch loading parameters.<br>• interval {int} The interval between batch loading<br>• numberInBatch {int} The loading batch size |

##### Returns:

None

------------------------------------------------------------------------

#### enableEditingMenuContext(enabled)

Enables or not the showing of editing menu context (applies to when layer is in edit mode)

##### Parameters:

| Name      | Type    | Description                            |
|-----------|---------|----------------------------------------|
| `enabled` | boolean | if set to true. Default value is true. |

------------------------------------------------------------------------

#### enableFeatureEditing(enable)

Enable or disable feature editing.

##### Parameters:

| Name     | Type    | Description                       |
|----------|---------|-----------------------------------|
| `enable` | Boolean | Enable or disable feature editing |

##### Returns:

Type
Boolean

------------------------------------------------------------------------

#### enableFeatureHover(enable)

Enable or disable the feature hover effect.

##### Parameters:

| Name     | Type    | Description                                                         |
|----------|---------|---------------------------------------------------------------------|
| `enable` | boolean | Enable (when true) or disable (when false) the feature hover effect |

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableFeatureSelection(enable, mode)

Enable (if true) or disable (if false) feature selection, and set the selection mode.

##### Parameters:

| Name     | Type    | Description                                                                                                                                                                                                                                                                                                                  |
|----------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enable` | boolean | Enable (when true) or disable (when false) feature selection                                                                                                                                                                                                                                                                 |
| `mode`   | int     | optional If feature selection is enabled, the selection mode can be either<br>OM.layer.VectorLayer.SINGLE_SELECTION (i.e. only one feature at a time can be selected)<br>or OM.layer.VectorLayer.MULTIPLE_SELECTION (i.e. multiple features can be selected).<br>The default value is OM.layer.VectorLayer.SINGLE_SELECTION. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableIndicatorFeatures()

This method enables or disables "indicator features" on this layer. An indicator
feature is simply a box or rectangle representing a (polygon-type)
feature that is too small to be labeled. Indicator features share the same
attributes and selection/mouse-over behaviour as the main features. Once
enabled, the layer will automatically generate/remove indicator features as
needed.

##### Parameters:

| Name       | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enable.`  | Boolean | Whether to enable indicator feautres.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `options.` | Object  | Various properties for indicator features, listed below.<br>• leadLine {Boolean} Whether to display the lead lines. Default value is false<br>• maxIndicators {int} maximum number of indicator features allowed. Default value is 8<br>• enabledZoomLevels {Object} It can have two properties: min and max.<br>• indicatorSize{Object} indicator feature size in pixel. It can have two properties: width and height. Default<br>size is 40\*30<br>• position {OM.geometry.Point} Specifies the starting position<br>(upper-left corner) of the area<br>where indicator features are to be<br>displayed |

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableInfoWindow(enable)

Enable or disable the feature info window.

##### Parameters:

| Name     | Type    | Description                                                                       |
|----------|---------|-----------------------------------------------------------------------------------|
| `enable` | boolean | Enable or disable feature info window. By default,<br>the info window is enabled. |

Inherited From:
- [OM.layer.Layer#enableInfoWindow](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### enableToolTip(enable)

Set whether the features in this layer will display a tool tip on mouse over.
Tool tip is enabled by default.

##### Parameters:

| Name     | Type    | Description                                                   |
|----------|---------|---------------------------------------------------------------|
| `enable` | boolean | if set to false, no tooltip will be displayed for this layer. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### getAllFeatures()

Get all features in this layer. Each element in the returned array is an
instance of OM.Feature.

##### Returns:

All features in the layer.

Type
Array

------------------------------------------------------------------------

#### getAttributeNames()

Get all attributes names for the features.

##### Returns:

An array of attributes names;

Type
Array

------------------------------------------------------------------------

#### getAttributeType(name)

Gets the the specified attribute type.

##### Parameters:

| Name   | Type   | Description                               |
|--------|--------|-------------------------------------------|
| `name` | String | the name of the attribute to be returned. |

##### Returns:

the type 9"string", "double", ...) for the given attribute,
or null if no attribute type with the given name was found.

Type
Object

------------------------------------------------------------------------

#### getEnableInfoWindow()

get the enable infowindow status: true for enabled and false otherwise
the info window is enabled.

Inherited From:
- [OM.layer.Layer#getEnableInfoWindow](OM.layer.Layer.md)

##### Returns:

true or false

Type
boolean

------------------------------------------------------------------------

#### getExtent()

Get the layer's minimum bounding rectangle (MBR) by combining all the MBRs of
its geometries.

##### Returns:

The layer MBR

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getFeature(id)

Get the OM.Feature object with specified ID.

##### Parameters:

| Name | Type   | Description                                           |
|------|--------|-------------------------------------------------------|
| `id` | string | A string that uniquely identifies the feature object. |

##### Returns:

The feature with the specified ID if it exists, null otherwise.

Type
[OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### getFeatureGeometryType()

Get the geometry type for all the features in this theme.
It can be "POLYGON", "LINESTRING" or "POINT".

##### Returns:

The geometry type

Type
string

------------------------------------------------------------------------

#### getFeaturesByAttribute(attrName, attrValues)

Given an attribute name and one or more values, find all the features in this layer
that have a matching value for that attribute or property.
The attribute name must be in the list returned by calling getAttributeNames().
The attribute values can be passed either as an array, or a
regular expression (to be implemented).

##### Parameters:

| Name         | Type           | Description                      |
|--------------|----------------|----------------------------------|
| `attrName`   | String         | the name of the attribute        |
| `attrValues` | Array \| regEx | an array or a regular expression |

##### Returns:

an array of the features with the given value; or null if none
was found.

Type
Array

------------------------------------------------------------------------

#### getHoverStyle()

Get the onHover style for a feature.

##### Returns:

The hover style object

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getLabelColumn()

Gets the currently set labeling column name

##### Returns:

The labeling column name

Type
String

------------------------------------------------------------------------

#### getLabelingStyle()

Get the labeling style

##### Returns:

The labeling style object

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getName()

Get the layer name.

Inherited From:
- [OM.layer.Layer#getName](OM.layer.Layer.md)

##### Returns:

The layer name

Type
String

------------------------------------------------------------------------

#### getOpacity()

Get the layer's current opacity setting.

Inherited From:
- [OM.layer.Layer#getOpacity](OM.layer.Layer.md)

##### Returns:

The layer's opacity. Is a value between 0 and 1.

Type
float

------------------------------------------------------------------------

#### getPointerSensitivity()

Gets the current pointer sensitivity.

##### Returns:

\[description\]

Type
boolean

------------------------------------------------------------------------

#### getRenderingStyle()

Get the rendering style.

##### Returns:

The rendering style object

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getSelectedFeatures()

Get the selected Features (array of OM.Feature).

##### Returns:

The currently selected features

Type
Array

------------------------------------------------------------------------

#### getSelectionChecker()

##### Returns:

currently set feature selection checker.

------------------------------------------------------------------------

#### getSelectionMode()

Returns the current feature selection mode.

##### Returns:

the current selection mode, which is either OM.layer.VectorLayer.SINGLE_SELECTION or
OM.layer.VectorLayer.MULTIPLE_SELECTION.

Type
String

------------------------------------------------------------------------

#### getSelectStyle()

Get the highlight style for user selected features.

##### Returns:

The highlight style object

Type
[OM.style.Style](OM.style.Style.md)

------------------------------------------------------------------------

#### getSelectVisualFilter()

Get the currently set visual filter for selected features.

##### Returns:

The visual filter

Type
[OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md)

------------------------------------------------------------------------

#### getVisualFilter()

Get the current visual filter for the whole layer.

##### Returns:

The current visual filter

Type
[OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md)

------------------------------------------------------------------------

#### getZIndex()

Get the layer's z-index.

Inherited From:
- [OM.layer.Layer#getZIndex](OM.layer.Layer.md)

##### Returns:

The z-index value. Returns -1 if the layer was not added to the map.

Type
int

------------------------------------------------------------------------

#### hasSharedBoundary()

Returns if adjacent boundaries share "common" vertexes when editing.
If true some vertexes operations (add, remove and move) will be applied to
the base feature and other features that "shares" the boundary.

##### Returns:

true or false

Type
booelan

------------------------------------------------------------------------

#### hover(the)

This method shows the hover effect on a feature;

##### Parameters:

| Name  | Type                        | Description           |
|-------|-----------------------------|-----------------------|
| `the` | [OM.Feature](OM.Feature.md) | feature to be hovered |

##### Returns:

the feature being hovered over

------------------------------------------------------------------------

#### isClusterSelectable()

Note: when a vector layer has clustering enabled and 'clickBehavior' set to 'select', then
this layer's clusters are selectable.

##### Returns:

True if clusters are selectable, false otherwise

Type
Boolean

------------------------------------------------------------------------

#### isDisplayFeaturesTaskEnabled()

Returns if contribution to the display task bar status is set when displaying this layer features.

##### Returns:

Type
boolean

------------------------------------------------------------------------

#### isEditingMenuContextEnabled()

Returns id editing menu context showing is enabled (applies to when layer is in edit mode)

##### Returns:

true or false

Type
booelan

------------------------------------------------------------------------

#### isFeatureEditable()

Check if features are editable.

##### Returns:

True, if the features are editable, false if not.

Type
Boolean

------------------------------------------------------------------------

#### isInZoomLevelRange(curLevel)

Checks if the current map zoom level is within this layer's visible zoom-level range.

##### Parameters:

| Name       | Type | Description                                                                                                                                                |
|------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `curLevel` | int  | Optional, the zoom level to check if it is within the minVisibleLevel and maxVisibleLevel<br>range. If not specified, then the current zoom level is used. |

Inherited From:
- [OM.layer.Layer#isInZoomLevelRange](OM.layer.Layer.md)

##### Returns:

true if the current map level is within the layer's zoom level range for
it to be visible.

Type
Boolean

------------------------------------------------------------------------

#### isVisible(curLevel)

Get the visibility of the layer.

##### Parameters:

| Name       | Type | Description                                                                                                                                                |
|------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `curLevel` | int  | Optional, the zoom level to check if it is within the minVisibleLevel and maxVisibleLevel<br>range. If not specified, then the current zoom level is used. |

Inherited From:
- [OM.layer.Layer#isVisible](OM.layer.Layer.md)

##### Returns:

True if the theme-based FOI layer is currently visible,
False if the theme-based FOI layer is currently not visible

Type
Boolean

------------------------------------------------------------------------

#### labelsVisible()

Check if feature labels will be rendered, i.e. should be visible.

##### Returns:

true (features labels visible) or false (feature labels not visible).

Type
Boolean

------------------------------------------------------------------------

#### on()

A shorthand name for the member function addListener.

Inherited From:
- [OM.layer.Layer#on](OM.layer.Layer.md)

Mixes In:
- [OM.event.EventSource.on](OM.event.EventSource.md)

------------------------------------------------------------------------

#### removeAllFeatures()

Removes all features from a layer

##### Returns:

The number of features removed

Type
int

------------------------------------------------------------------------

#### removeFeature(feature)

Removes a feature from the layer

##### Parameters:

| Name      | Type                        | Description           |
|-----------|-----------------------------|-----------------------|
| `feature` | [OM.Feature](OM.Feature.md) | The feature to remove |

##### Returns:

The feature, if found in the layer, else returns null.

Type
[OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### removeSecondaryStyle(style)

Remove a specified secondary style from the vector layer.

##### Parameters:

| Name    | Type                                | Description                   |
|---------|-------------------------------------|-------------------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The secondary style to remove |

##### Returns:

Type
void

------------------------------------------------------------------------

#### saveEditing(call)

Save current data editing (Predefined or JDBC layer types).
Check logging for additonal information related this method execution.

##### Parameters:

| Name   | Type     | Description                                                                                                                                                                                                                                                                                                                                 |
|--------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `call` | function | back function name that can be used to get the return value (true or false).<br>function saveCallBack(result)<br>{<br>if(OM.notNull(result))<br>{<br>// result can be true or false //alert("Save result: " + result);<br>}<br>}<br>`            // application code`<br>`            layer.saveEditing(saveCallBack);`<br>`            //` |

------------------------------------------------------------------------

#### selectFeature(feature)

Highlight a feature using its selection style. Valid only when
feature selection is enabled.

##### Parameters:

| Name      | Type                        | Description                |
|-----------|-----------------------------|----------------------------|
| `feature` | [OM.Feature](OM.Feature.md) | The feature to be selected |

##### Returns:

The selected feature object

Type
[OM.Feature](OM.Feature.md)

------------------------------------------------------------------------

#### selectFeatureByFilter(filter)

Highlight features that pass the specified filter

##### Parameters:

| Name     | Type                                    | Description          |
|----------|-----------------------------------------|----------------------|
| `filter` | [OM.filter.Filter](OM.filter.Filter.md) | The specified filter |

##### Returns:

Type
void

------------------------------------------------------------------------

#### sendBackward()

Sendthe layer to the back by one step (closer to the bottom of the map).

Inherited From:
- [OM.layer.Layer#sendBackward](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### sendToBottom()

Send the layer all the way to the bottom of the map

Inherited From:
- [OM.layer.Layer#sendToBottom](OM.layer.Layer.md)

##### Returns:

The new z-index

Type
int

------------------------------------------------------------------------

#### setBoundingTheme(flag)

Specify whether this theme is a bounding theme.

##### Parameters:

| Name   | Type    | Description                                    |
|--------|---------|------------------------------------------------|
| `flag` | Boolean | True, if it is a bounding theme, false if not. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setBringToTopOnMouseOver(flag)

Specify whether to bring feature images to the top of the map when the mouse
moves over features in the layer. By default, a feature image will be
brought to the top on hover or mouseover..

##### Parameters:

| Name   | Type    | Description                                                                                                 |
|--------|---------|-------------------------------------------------------------------------------------------------------------|
| `flag` | boolean | True, bring feature images to the top, or false otherwise<br>(i.e. do not bring feature images to the top). |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setDisplayFeaturesTaskEnabled()

Enables or not the contribution to the display task bar status when displaying this layer features.

##### Returns:

Type
void

------------------------------------------------------------------------

#### setHoverStyle(style)

Set the onHover style for a feature.

##### Parameters:

| Name    | Type                                | Description     |
|---------|-------------------------------------|-----------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The hover style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setKeepSelected(enable)

If set to true, clicking on a feature that is already selected will keep it selected.
The default value is false, meaning clicking on a selected feature will un-select it.

##### Parameters:

| Name     | Type    | Description                                                        |
|----------|---------|--------------------------------------------------------------------|
| `enable` | boolean | flag indicating whether to keep features selected on mouse clicks. |

------------------------------------------------------------------------

#### setLabelColumn(col)

Sets the attribute column whose value is used for the labels.

##### Parameters:

| Name  | Type   | Description               |
|-------|--------|---------------------------|
| `col` | String | The attribute column name |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setLabelingStyle(style)

Set the labeling style. Usually a text or a marker style.

##### Parameters:

| Name    | Type                                | Description            |
|---------|-------------------------------------|------------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The new labeling style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setLabelsVisible(visible)

Specify whether or not to render feature labels. The default value is false

##### Parameters:

| Name      | Type    | Description                                                   |
|-----------|---------|---------------------------------------------------------------|
| `visible` | Boolean | If true, render feature labels. If false, do not render them. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setMouseCursorStyle(cursorStyle)

This method sets the mouse cursor style when the mouse is over a feature of this
vector layer.
To set a non-standard cursor using a custom image, you can pass in a json object
specifying these properties:

    <UL>
    <LI> src : the URL of the cusor image in PNG or GIT format
    <LI> hotspotX :  the hotspot x offset relative to the image coordinates
    <LI> hotspotY : the hotspot y offset relative to the image coordinates
    </UL>

##### Parameters:

| Name          | Type   | Description                                                                                                                                                    |
|---------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cursorStyle` | String | A string that specifies the cursor style to<br>be used, which must be one of the standard CSS cursor style names<br>such as "crosshair", "pointer" and "move". |

##### Returns:

None

------------------------------------------------------------------------

#### setMultiFeatureMarker(marker)

Set mult feature marker. The marker will be used when multi marker features
are the same location.

##### Parameters:

| Name     | Type                                  | Description  |
|----------|---------------------------------------|--------------|
| `marker` | [OM.style.Marker](OM.style.Marker.md) | marker style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setName(newName)

Set the layer name with the given name.

##### Parameters:

| Name      | Type   | Description                                      |
|-----------|--------|--------------------------------------------------|
| `newName` | String | The new layer name to be assigned to this layer. |

Inherited From:
- [OM.layer.Layer#setName](OM.layer.Layer.md)

##### Returns:

Type
None

------------------------------------------------------------------------

#### setNSDP(nsdp)

Set the Non-Spatial Data Provider for the vector layer.

##### Parameters:

| Name   | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `nsdp` | Object | The Non-Spatial Data Provider object containing info needed<br>by the FOI server to join Non-Spatial data and the associated layer's spatial table.<br>It has these attributes.<br>• keyColumn {String}. Required. The column to match non-spatial data with<br>spatial data (e.g. 'iso_country_code' or 'state_abbrv').<br>• xml {String}. Optional. The non-spatial data in the nsdp xml format<br>• json {String}. Optional. The non-spatial data in the nsdp JSON format<br>• keyAttr {String}. Optional. Ihe attribute is used to match with spatial data when non-spatial<br>data is JSON format.<br>• url {String}. Optional. A URL for non-spatial data.<br>• fullDisplay {Boolean}. Optional. Whether to display all spatial features (i.e. fullDisplay:true) or<br>only those features which match the supplied keyColumn values in the NSDP document (i.e. fullDisplay:false).<br>Default value is false. Only matching features are displayed<br>• ignoreCase {Boolean}. Optional. Use case-insensitive (if true) or case-sensitive (if false) matching.<br>Default value is true. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setOpacity(opacity)

Set the layer's opacity. A value between 0 (transparnet) and 1 (opaque).

##### Parameters:

| Name      | Type  | Description                                                        |
|-----------|-------|--------------------------------------------------------------------|
| `opacity` | float | It should be a number between 0 and 1. e.g. 0.5 means 50% opacity. |

Inherited From:
- [OM.layer.Layer#setOpacity](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setPartialSelectStyleForCluster(style)

Set the highlight style for partially selected cluster features.
Re-clustering process can be triggered by a zoom in or zoom out, and a newly formed cluster
may contain a collection of features that a portion of the whole collection is repviously selected.
For example, if a new cluster contains 5 features and 2 of them were previously selecte, then this
cluster is a partially selected cluster. From another perspective, if cluster is clicked, it is fully
selected (it if has not been selected), or it is deselected (if it has been selected).

##### Parameters:

| Name    | Type                                | Description         |
|---------|-------------------------------------|---------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The highlight style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setPointerSensitivity(enabled)

Sets the vector layer's sensitivity to mouse pointer events. By default a vector layer
will always respond to mouse pointer events, thus preventing any layer behind it
from doing so. If set to false, then it will let mouse pointer events pass through without
responding to it.

##### Parameters:

| Name      | Type    | Description                                                                                                     |
|-----------|---------|-----------------------------------------------------------------------------------------------------------------|
| `enabled` | boolean | if set to false, then this vector layer will not handle mouse pointer<br>events. Default is always set to true. |

------------------------------------------------------------------------

#### setQueryParameters(vararg)

This method sets the query parameters for the vector layer that is based on
a templated predefined theme. The number of parameters is corresponding to
the theme definition. Each parameter can be a number, a string, a [`OM.geometry.Geometry`](OM.geometry.Geometry.md)
object, or a JSON object with these properties:value, type and sqlType.

##### Parameters:

| Name     | Type | Description                                                                                               |
|----------|------|-----------------------------------------------------------------------------------------------------------|
| `vararg` |      | a list of parameters corresponding to the required number of binding<br>variables in the predefined theme |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setRenderingStyle(style, attributes)

Set the layer's rendering style.

##### Parameters:

| Name         | Type                                | Description                                                                                                                                 |
|--------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| `style`      | [OM.style.Style](OM.style.Style.md) | The new rendering style                                                                                                                     |
| `attributes` | Array                               | The list of attribute names used to determine the actual rendering style.<br>It is effective only when renderingStyle is an advanced style. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setSelectionChecker(checkerFunc)

Sets a custom function that checks if a feature should be selectable.
This provides application with a finer level of control on a feature by feature basis
when the layer itself allows selections. One use case is to disable user from being
able to select/highlight features that have no measure data associated.

The custom function should expect an instance of the OM.Feature class, and should
return a boolean value indicating whether the feature is selectable. Return true
if the feature can be selected, and false if it should not be selected.

This function is always called just prior to a feature is going to be selected.

##### Parameters:

| Name          | Type     | Description                                              |
|---------------|----------|----------------------------------------------------------|
| `checkerFunc` | function | a function that is passed in the feature to be selected. |

------------------------------------------------------------------------

#### setSelectStyle(style)

Set the highlight style for user selected features.

##### Parameters:

| Name    | Type                                | Description         |
|---------|-------------------------------------|---------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | The highlight style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setSelectVisualFilter(filter)

Set the visual filter (such as drop shadow) to be applied to
currently selected features.

##### Parameters:

| Name     | Type                                                            | Description              |
|----------|-----------------------------------------------------------------|--------------------------|
| `filter` | [OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md) | The visual effect to use |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setSharedBoundary(true)

Sets if adjacent boundaries should share "common" vertexes when editing.
If true some vertexes operations (add, remove and move) will be applied to
the base feature and other features that "shares" the boundary.

##### Parameters:

| Name   | Type    | Description |
|--------|---------|-------------|
| `true` | booelan | or false    |

------------------------------------------------------------------------

#### setToolTipCustomizer(customizer)

Set a tool tip customizer function on this layer. Use this function
to return a customized tool-tip text for the features.

If no customizer function is set, then the tooltip is based on the label
text set on each feature.

##### Parameters:

| Name         | Type     | Description                                                                                              |
|--------------|----------|----------------------------------------------------------------------------------------------------------|
| `customizer` | function | The tool tip customizer function. The function<br>should expect a single OM.Feature object as parameter. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setVisible(visibility)

Sets the visibility of the layer.
Note that the visibility change will NOT be made if the current map zoom level is
outside the layer's 'visible zoom level range' which is set by setZoomLevelRange() method.

##### Parameters:

| Name         | Type    | Description                                                                         |
|--------------|---------|-------------------------------------------------------------------------------------|
| `visibility` | Boolean | A Boolean true (show the layer, i.e. make it visible) or false<br>(hide the layer). |

Inherited From:
- [OM.layer.Layer#setVisible](OM.layer.Layer.md)

##### Returns:

void}

Type
None

------------------------------------------------------------------------

#### setVisibleBound(bound)

Set a bound (MBR) for the layer visibility. Only content within the supplied bound will be rendered.
That is, the map client will only fetch and display map content within this bound.

##### Parameters:

| Name    | Type                                              | Description                  |
|---------|---------------------------------------------------|------------------------------|
| `bound` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | Specifies the layer boundary |

Inherited From:
- [OM.layer.Layer#setVisibleBound](OM.layer.Layer.md)

##### Returns:

Type
void

------------------------------------------------------------------------

#### setVisualFilter(filter)

Set the visual filter (such as drop-shadow) to be applied for all
the features in this layer.

##### Parameters:

| Name     | Type                                                            | Description              |
|----------|-----------------------------------------------------------------|--------------------------|
| `filter` | [OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md) | The visual effect to use |

##### Returns:

Type
void

------------------------------------------------------------------------

#### setZIndex()

Set the z-index for the layer.

Note: A valid layer z-index should be a number between 1 and n, where n is
the number of layers that are currently displayed in the map. When the newIndex
parameter of setZIndex is less than 1, it will be set to 1. If it is
greater than n, it will be set to n. If z-Index value, newIndex, is already assigned
to another layer, then it will still be assigned to the current layer (on which this function is invoked).
One or more of the other layer will be assigned a different z-index value. The changes will depend on
whether this layer was inserted into the current layer stack or just moved within the layer stack.

Inherited From:
- [OM.layer.Layer#setZIndex](OM.layer.Layer.md)

##### Returns:

The old z-index

Type
int

------------------------------------------------------------------------

#### setZoomLevelRange(minLevel, maxLevel)

Set the zoom level range within which this layer is visible. By default
a layer is set to be visible between a minmum zoom level of 0 and a maximum
(theoretical) zoom level of 100.

##### Parameters:

| Name       | Type | Description                                                                                            |
|------------|------|--------------------------------------------------------------------------------------------------------|
| `minLevel` | int  | Specifies the min level. The layer will not be<br>visible if the zoom level is lower than this vlaue.  |
| `maxLevel` | int  | Specifies the max level. The layer will not be<br>visible if the zoom level is higher than this value. |

Inherited From:
- [OM.layer.Layer#setZoomLevelRange](OM.layer.Layer.md)

##### Returns:

Type
None

------------------------------------------------------------------------

#### size()

Get the count of the number of features in this layer.

##### Returns:

The count of the number of features

Type
int

------------------------------------------------------------------------

#### zoomToTheme()

Zoom to the theme's full extent. It automatically adjusts the map center and zoom level so that all
theme features can be displayed inside the map window.

##### Returns:

Type
void
