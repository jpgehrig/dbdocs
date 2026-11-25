------------------------------------------------------------------------

#### new ColorFormatter()

Creates a new style Formatter that returns a proper image source (url) for
any given data value.
The options parameter is a JSON object containing several optional
properties, such as:

- scale the scale used to format or classify data values.
  If not specified the default logarithm scale is used.
- numClasses the number of classes or buckets to use; if not specified then
  is is the same as the number of colors in the colors array.
- sources an array of sources to be used as base source stops or ramps. The lowest
  possible data value is mapped to the first source in the array,
  while the highest possible data value is mapped to the last
  source in the array.
- defaultSource the default image source to use when the data value is null
  or a proper source cannot be determined. This source is typically
  used to render shapes with no data.
- style the Marker style which this formatter will be applied to.
  This is optional.

### Methods

------------------------------------------------------------------------

#### getBaseColors()

Returns the list of base colors used as color stops.

------------------------------------------------------------------------

#### getBaseSources()

Returns the list of base sources used as color stops.

------------------------------------------------------------------------

#### getDefaultColor()

returns the default

------------------------------------------------------------------------

#### getDefaultSource()

returns the default

------------------------------------------------------------------------

#### resolve(itemValue, column)

The main function of the ColorFormatter. It computes and returns a color
value based on the specified data item value and the set of all possible
data item values (captured as a Column).

##### Parameters:

| Name        | Type   | Description                                                                                                                                     |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `itemValue` | object | the value of a specific data item, against<br>which the optimal style attribute value (such as fill color or marker size)<br>is determined.     |
| `column`    | object | the OM.Column instance that contains the set of<br>all possible data items. itemValue is the value of one of the data items<br>from the column. |

##### Returns:

the determined style color value

Type
object

------------------------------------------------------------------------

#### resolve(itemValue, column, feature)

The main function of the SourceFormatter. It computes and returns a source
value based on the specified data item value and the set of all possible
data item values (captured as a Column).

##### Parameters:

| Name        | Type   | Description                                                                                                                                     |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `itemValue` | object | the value of a specific data item, against<br>which the optimal style attribute value (such as fill color or marker size)<br>is determined.     |
| `column`    | object | the OM.Column instance that contains the set of<br>all possible data items. itemValue is the value of one of the data items<br>from the column. |
| `feature`   | object | the feature object being resolved.                                                                                                              |

##### Returns:

the determined style image source value

Type
object

------------------------------------------------------------------------

#### setColors(colors)

Sets the list of base colors to be used as color stops.

##### Parameters:

| Name     | Type  | Description        |
|----------|-------|--------------------|
| `colors` | array | an array of colors |

------------------------------------------------------------------------

#### setDefaultColor()

sets the default color

------------------------------------------------------------------------

#### setDefaultSource()

sets the default color

------------------------------------------------------------------------

#### setSources(colors)

Sets the list of base colors to be used as color stops.

##### Parameters:

| Name     | Type  | Description        |
|----------|-------|--------------------|
| `colors` | array | an array of colors |
