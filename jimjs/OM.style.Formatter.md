------------------------------------------------------------------------

#### new Formatter(options)

Creates a new style Formatter.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | object | The options parameter is a JSON object containing several optional<br>properties, such as:<br><br>• scale the bucketing algorithm used to format or classify data values.<br>If not specified the default logarithm scale is used.<br><br>• numClasses the number of buckets or classes to use during formatting.<br><br>• style the original style that this Formatter is affecting. Optional.<br> |

### Methods

------------------------------------------------------------------------

#### getNumClasses()

Gets the desired classes or buckets for dividing the data item values.

------------------------------------------------------------------------

#### getScale()

gets the scale (such as linear or logarithmic) used to classify data item
values.

------------------------------------------------------------------------

#### getStyle()

Gets the original style for which this Formatter might be affecting one
of its visual attributes.

------------------------------------------------------------------------

#### resolve(itemValue, column, feature)

The main function of a Formatter. It computes and returns a style attribute
value based on the specified data item value and the set of all possible
data item values (captured as a Column).

##### Parameters:

| Name        | Type   | Description                                                                                                                                     |
|-------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `itemValue` | object | the value of a specific data item, against<br>which the optimal style attribute value (such as fill color or marker size)<br>is determined.     |
| `column`    | object | the OM.Column instance that contains the set of<br>all possible data items. itemValue is the value of one of the data items<br>from the column. |
| `feature`   | object | the feature object being resolved.                                                                                                              |

##### Returns:

the determined style attribute value

Type
object
