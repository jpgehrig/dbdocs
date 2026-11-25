------------------------------------------------------------------------

#### new Style(config)

Style is an abstract base class of all style types. All other style types
extend this class. This will be called by subclass constructors.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                             |
|----------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | An optional config object with the following attributes:<br><br>• styleName {String} The style name<br>• animationStyle {Object} The animation style such as PulseAnimation<br>• effects {Array} An array of visual effects, i.e. of OM.visualfilter.VisualFilter, which specify one or more<br>visual effects (such as gradient or drop-shadow) to apply to the style. |

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

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### getBindables()

Returns a list of bindable style attributes. A bindable attribute is
a certain aspect of a style (such as its fill color, stroke width or
overall size) that can be changed based on some business data value
associated with each feature. It is typically bound to a Column data
set.

##### Returns:

an array containing names of bindable attributes; if
no bindable attribute exists then an empty array is
returned.

Type
Array

------------------------------------------------------------------------

#### getConfig()

Gets the config of style.

##### Returns:

the config object

------------------------------------------------------------------------

#### getStyleName()

Return the style name

##### Returns:

the style name

------------------------------------------------------------------------

#### hasBinding()

Checks if this style has associated data bindings.

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

##### Returns:

true if the argument is bindable; false otherwise

Type
Boolean

------------------------------------------------------------------------

#### isBound()

Checks whether a specified (bindable) attribute is already bound to some
Column data set.

------------------------------------------------------------------------

#### isFeatureBound(feature)

Checks whether the given feature is bound to any of the bindings in
this style.

##### Parameters:

| Name      | Type                        | Description                        |
|-----------|-----------------------------|------------------------------------|
| `feature` | [OM.Feature](OM.Feature.md) | the feature instance to be checked |

##### Returns:

returns true if the feature has associated values from
any of the style bindings' Column instances. Returns false if there
is no values associated with this feature, or there is no bindings
at all in this style.

Type
Boolean

------------------------------------------------------------------------

#### isServerSide()

Checks if this style is a server side style.

##### Returns:

true if is a style loaded from server; false otherwise

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

------------------------------------------------------------------------

#### unbindData(attribute)

Un-binds all Column data set for the given attribute.

##### Parameters:

| Name        | Type   | Description                                         |
|-------------|--------|-----------------------------------------------------|
| `attribute` | String | name of the style attribute (such as 'Fill', 'Size' |
