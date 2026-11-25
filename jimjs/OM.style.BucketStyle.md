------------------------------------------------------------------------

#### new BucketStyle(config)

This class represents a bucket style that can be used for thematic
mapping of numeric or categorical data.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|----------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A configuration with the following attributes:<br>• styleName {String} A name for this style (e.g. 'revenueRanges'). Required.<br>• numClasses {int} The number of classes or buckets. Required.<br>• defaultStyle {OM.style.Style} The default style. The style used when a feature's attribute<br>value does not fall in any bucket. Required.<br>• styles {Array} An array that corresponds to the array of buckets.<br>That is, style\[0\] is used for buckets\[0\].<br>The array must contain only one of these two object types<br><br>• OM.style.Style<br>• {url, dataSource, style}<br>• <br>Required.<br><br>• buckets {Array} An array of OM.style.Bucket. Must be of the same length as the styles array. Optional.<br>• classification {String} The classification scheme. Can be "equal", "quantile", "logarithmic" or "custom". Optional.<br>Default is "equal". If "custom" is specified, then, either the algorithm or the buckets attribute<br>needs to be specified.<br>• algorithm {function} A custom (user-defined) function to be used for generating the buckets.<br>Used when the classification scheme is set to "custom".<br>The function should expect and accept three parameters: features, column and numClasses.<br><br>• features {Array} An array of OM.Feature<br>• column {String} The name of the attribute column used for generating the buckets<br>• numClasses {int} The number of classes or buckets<br>• <br>It should return the array of buckets, i.e. array on OM.style.Bucket. Optional.<br><br>• low {float} Optional. The value is used to create equal bucket style.<br>• high {float} Optional. The value is used to create equal bucket style.<br>• isNumeric {Boolean} Indicates whether the values to be evaluated are numeric. Set to true by default. Optional.<br>• gradient {String} Whether a gradient effect should be used on all buckets.<br>The value can be "linear", "on", or "off". Default is "off". Optional.<br>• effects {Array} An array of OM.visualfilter.VisualFilter specifying effects (gradient or drop-shadow) for the buckets. Optional. |

##### Returns:

An instance of OM.style.BucketStyle

Type
OM.style.BucketStyle

##### Examples

    new OM.style.BucketStyle({
      styleName: 'Tornados 2010',
      numClasses : 5,
      classification: 'equal',               //'logarithmic', 'custom',
      defaultStyle: style,
      styles: [
          {url: baseURL, dataSource:'ds', style:'remote_stile_name1'},
          {url: baseURL, dataSource:'ds', style:'remote_stile_name2'},
          ...
          {url: baseURL, dataSource:'ds', style:"remote_stile_nameN"}
        ],
      buckets : [bucket0, bucket1, ..., bucket4 ],    //optional
      effects: [dropShadow1],                //optional
      isNumeric : true,                      //optional
      gradient: 'off'                       //on, linear; optional
    })

    new OM.style.BucketStyle({
     styleName: 'CustomExample',
     numClasses: 5,
     classification: 'custom',
     algorithm: myClassificationAlgorithm, // generate the buckets using this function
     defaultStyle: myDefaultStyle,
     styles: [myStyle0, ..., myStyle4],
     isNumeric: true,
     gradient: 'linear'
     })

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

#### getBindables()

Returns a list of bindable style attributes. A bindable attribute is
a certain aspect of a style (such as its fill color, stroke width or
overall size) that can be changed based on some business data value
associated with each feature. It is typically bound to a Column data
set.

Inherited From:
- [OM.style.Style#getBindables](OM.style.Style.md)

##### Returns:

an array containing names of bindable attributes; if
no bindable attribute exists then an empty array is
returned.

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

#### getDefaultStyle()

Get the default style used to display features whose value do not
fall within any of the buckets in this BucketStyle.

##### Returns:

The default style

Type
[OM.style.Style](OM.style.Style.md)

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

#### setDefaultStyle(style)

Set the default style used to display features whose value do not
fall within any of the buckets in this BucketStyle.

##### Parameters:

| Name    | Type                                | Description       |
|---------|-------------------------------------|-------------------|
| `style` | [OM.style.Style](OM.style.Style.md) | the default style |

##### Returns:

Type
void

------------------------------------------------------------------------

#### toXMLString()

------------------------------------------------------------------------

#### toXMLString_substyles()

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
