------------------------------------------------------------------------

#### new SizeFormatter()

Creates a new style Formatter that returns a proper size value for
any given data value.
The options parameter is a JSON object containing several optional
properties, such as:

- scale the scale used to format or classify data values.
  If not specified, the default logarithm scale is used.
- numClasses the number of classes or buckets to use.
- startingSize The minimum or starting size; for any computed size, if it's smaller
  than this value, then use this instead.
- delta the delta in size between any two adjacent classes
- defaultSize the default size to use when the data value is null
  or a proper color cannot be determined. This color is typically
  used to render shapes with no data. Default is 0 (which means
  the marker will not be displayed).
- style the (Marker) style which this formatter is applied to. Optional.
- lengthUnit {String} the unit of the size, value can be "pixel" or "kilometer"; the default unit is pixel

### Methods

------------------------------------------------------------------------

#### resolve(itemValue, column, feature)

The main function of the SizeFormatter. It computes and returns a size
value based on the specified data item value and the set of all possible
data item values (captured as a Column).

##### Parameters:

| Name        | Type   | Description                                                                                                                                     |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `itemValue` | object | the value of a specific data item, against<br>which the optimal style attribute value (such as fill color or marker size)<br>is determined.     |
| `column`    | object | the OM.Column instance that contains the set of<br>all possible data items. itemValue is the value of one of the data items<br>from the column. |
| `feature`   | object | the feature object being resolved.                                                                                                              |

##### Returns:

the determined style size value

Type
object
