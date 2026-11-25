------------------------------------------------------------------------

#### new Marker(config)

This class represents a Marker or symbol style that can be applied to geometry features, typical points.

For example, the following code can be used to create a simple marker style based on the Oracle logo:

    var myMarker = new OM.style.Marker({src:"http://www.oracleimg.com/us/assets/oralogo-small.gif"});

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A configuration object for the marker. It can have the following attributes:<br><br>• styleName {String} A style name<br>• width {float} The marker width<br>• height {float} The marker height<br>• xOffset {int} The horizontal offset in pixels. Optional.<br>When specified, the marker will be shifted horizontally. A positive value means shift towards the right of the screen.<br>• yOffset {int} vThe ertical offset in pixels. Optional.<br>When specified, the marker will be shifted vertically. A positive value means shift downward and negative value upward.<br>• lengthUnit {String} The size unit. Optional.<br>The value can be "pixel", "meter", "kilometer", "feet", or "mile". Default value is "pixel".<br>• src {String} The marker image URL. Optional. Either src or vectorDef should be specified.<br>• textStyle {OM.style.Text} The text style will apply to the text on marker feature.<br>• textOffset {Object} The text offset, like {x:15, y:15}.<br>• vectorDef {Array} Defines the vector marker. It is an array of vector shapes.<br>Each array element can have the following properties:<br><br>• shape {Object} The shape definition object of the vector marker.<br>It has the following attributes:<br><br>• type {String} The type of the vector shape. Valid values are "circle", "path" or "rectangle".<br>• coords {Array} An array of coordinates (numbers) for the shape type "path" only.<br>• cx {float} The circle's center X ordinate. For "circle" only.<br>• cy {float} The circle's center Y ordinate. For "circle" only.<br>• x {float} The minimum X ordinate for the shape type "rectangle" only.<br>• y {float} The minimum Y ordinate for the shape type "rectangle" only.<br>• width {float} The width. Valid for shape types "circle" and "rectangle" only.<br>• height {float} The height. Valid for shape types "circle" and "rectangle" only.<br>• scale {float} The scale. Valid for shape type "path" only.<br>• <br><br>• <br>style {Object} The style definition. It has these attributes:<br><br>• stroke {String} The stroke color in rgb, i.e. in the format "#rrggbb".<br>• strokeThickness (float} The stroke width.<br>• strokeOpacity {float} The stroke opacity. A value between 0 (transparent) and 1 (opaque).<br>• fill {String} The fill color in rgb, i.e. in the format "#rrggbb".<br>• fillOpacity {float} The fill opacity. A value between 0 and 1.<br>• visibility (Boolean} Whether the marker is visible (when true) or not (when false) on initialization.<br>• filter {OM.visualfilter.VisualFilter} The visual effect to apply if any. Optional.<br>• <br><br>• <br><br>• <br>nullFillSrc {String} An optional image source to use as a fill pattern when no fill is set up for the marker.<br> |

##### Returns:

An instance of OM.style.Marker

### Extends

- [OM.style.Style](OM.style.Style.md)

### Methods

------------------------------------------------------------------------

#### bindData(attribute, column, formatter)

Binds a Column data set to a specified aspect of this style. This creates
a single binding on this style instance. Check individual sub-styles to
see how many bindings they support.
Each binding is comprised of three key pieces: the style attribute being
bound, the Column data set that drives the style attribute, and a resolver
function that computes and returns an effective style attribute for any
given data value from the Column.

##### Parameters:

| Name        | Type   | Description                                                                                                                                                                                                                                           |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `attribute` | string | the name of the style attribute to be bound to a data Column. An<br>attribute is a visual aspect of the style, such as "Fill",<br>"Size" etc.                                                                                                         |
| `column`    | object | A data column (typically an instance of OM.Column) that will<br>format the specified visual attribute of the style. If a String type<br>value is passed in, then it is assumed to be the name of<br>an property in the target VectorLayer's features. |
| `formatter` | object | an instance of OM.style.Formatter; it<br>maps an individual item's value (such as sales volume) to a<br>particular visual style attribute value (such as a color).                                                                                    |

Inherited From:
- [OM.style.Style#bindData](OM.style.Style.md)

------------------------------------------------------------------------

#### draw(feature, mapContext, options)

The actual logic for drawing a feature using a style is implemented in this method.
Must be overidden by sub-classes.

##### Parameters:

| Name         | Type                              | Description                                         |
|--------------|-----------------------------------|-----------------------------------------------------|
| `feature`    | [OM.Feature](OM.Feature.md)       | the feature to be applied with this style           |
| `mapContext` | [OM.MapContext](OM.MapContext.md) | the current map context                             |
| `options`    | Object                            | the rendering options, typically the graphics group |

Inherited From:
- [OM.style.Style#draw](OM.style.Style.md)

Overrides:
- [OM.style.Style#draw](OM.style.Style.md)

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### enableNullFillPattern(imageSource)

Sets an image pattern to fill with in the marker whenever a fill is not
set in the marker style. If null is passed, then no fill pattern is to be
used.

##### Parameters:

| Name          | Type           | Description            |
|---------------|----------------|------------------------|
| `imageSource` | string \| null | The fill pattern's URL |

------------------------------------------------------------------------

#### getBindables()

Returns a list of bindable style attributes.

Overrides:
- [OM.style.Style#getBindables](OM.style.Style.md)

##### Returns:

an array containing names of bindable attributes

Type
Array

------------------------------------------------------------------------

#### getConfig()

Gets the config of style.

Inherited From:
- [OM.style.Style#getConfig](OM.style.Style.md)

##### Returns:

the config object

------------------------------------------------------------------------

#### getStyleName()

Return the style name

Inherited From:
- [OM.style.Style#getStyleName](OM.style.Style.md)

##### Returns:

the style name

------------------------------------------------------------------------

#### hasBinding()

Checks if this style has associated data bindings.

Inherited From:
- [OM.style.Style#hasBinding](OM.style.Style.md)

##### Returns:

true if there is one or more data bindings; false otherwise

Type
Boolean

------------------------------------------------------------------------

#### isBindable(attr)

Checks whether a specified style attribute is bindable.

##### Parameters:

| Name   | Type   | Description                             |
|--------|--------|-----------------------------------------|
| `attr` | String | the name of the attribute to be checked |

Inherited From:
- [OM.style.Style#isBindable](OM.style.Style.md)

##### Returns:

true if the argument is bindable; false otherwise

Type
Boolean

------------------------------------------------------------------------

#### isBound()

Checks whether a specified (bindable) attribute is already bound to some
Column data set.

Inherited From:
- [OM.style.Style#isBound](OM.style.Style.md)

------------------------------------------------------------------------

#### isFeatureBound(feature)

Checks whether the given feature is bound to any of the bindings in
this style.

##### Parameters:

| Name      | Type                        | Description                        |
|-----------|-----------------------------|------------------------------------|
| `feature` | [OM.Feature](OM.Feature.md) | the feature instance to be checked |

Inherited From:
- [OM.style.Style#isFeatureBound](OM.style.Style.md)

##### Returns:

returns true if the feature has associated values from
any of the style bindings' Column instances. Returns false if there
is no values associated with this feature, or there is no bindings
at all in this style.

Type
Boolean

------------------------------------------------------------------------

#### resolveBinding(b, feature)

Resolves a specified binding for a given feature.
When a Style object has one or more of its visual attributes (such as Size
for a Marker style or Fill for a Color style) bound to an external data
column, then such visual attributes must be resolved for each and every feature
using the feature's associated data column value. The resolved visual
attribute values are then used to apply the style to that feature.

In other words, each time this method is called against a specific feature,
the following process always takes place:

- the feature's unique id is obtained
- the id is then used by the binding to find the corresponding data
  value from the associated Column instance
- the data value is used to determine or resolve the visual attribute
  of this style such as Size or Fill color.
- the visual attribute value is set on this Style instance for the
  duration of rendering the feature.

##### Parameters:

| Name      | Type   | Description                     |
|-----------|--------|---------------------------------|
| `b`       | Object | the binding object              |
| `feature` | Object | the feature to be resolved with |

Inherited From:
- [OM.style.Style#resolveBinding](OM.style.Style.md)

##### Returns:

the resolved style attribute

Type
Object

------------------------------------------------------------------------

#### unbindAllData(attribute)

Un-binds all Column data sets currently bound to the specified style attribute.

##### Parameters:

| Name        | Type   | Description                     |
|-------------|--------|---------------------------------|
| `attribute` | String | the name of the style attribute |

Inherited From:
- [OM.style.Style#unbindAllData](OM.style.Style.md)

------------------------------------------------------------------------

#### unbindData(attribute)

Un-binds all Column data set for the given attribute.

##### Parameters:

| Name        | Type   | Description                                         |
|-------------|--------|-----------------------------------------------------|
| `attribute` | String | name of the style attribute (such as 'Fill', 'Size' |

Inherited From:
- [OM.style.Style#unbindData](OM.style.Style.md)
