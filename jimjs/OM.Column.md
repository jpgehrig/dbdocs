------------------------------------------------------------------------

#### new Column(options)

This class represents a Column data set. The raw data can be
of any object type, as long as they are in a JavaScript array, with each
element representing a feature or row.

Two functions named keyGetter and valueGetter must be provided. Within
the function, 'this' will be pointing to an element of the raw data array.
keyGetter must return the key for the element, while valueGetter must return
the value for the element.

A number of convenience methods exist to provide such information as
min/max values and size of the Column data set.

An internal hashmap is created based on the keys and their values, to enable
fast retrieval of value by key.

The keyGetter and valueGetter methods are called with 'this' referencing the current
row of the Column.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|-----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | An object containing the properties and methods of a Column.<br>The object should contain the following properties:<br><br>• data {Object\[\]}. Required. Array of objects containing at least a key and measure properties.<br>There may be additional properties but the keyGetter() should return the key<br>property's value and valueGetter() should return the measure property's value.<br><br>• keyGetter {Function}. Required. A function which returns the<br>key value for a data row. e.g. getStoreId.<br><br>• valueGetter {Function}. Required. A function which returns the<br>measure (or value column's) value for a data row. e.g. getStoreSales.<br><br>• type {String}. The type ("number", "float", "double") of the measure, or value,<br>column of a data row.<br><br>• measureName {String}. Name of the measure column (e.g. "Measure" or "Revenue").<br><br>• measureIndex {Number}. Index of the column in the data array which should be<br>treated as the measure value.<br> |

##### Returns:

An instance of OM.Column

Type
Object

##### Example

A usage example:

    var myData = {"type":"FeatureCollection",
                   "collectionName":"wind10",
       "features":[
           {"type":"Feature","_id":"8663457104553265893",
            "geometry": {"type":"Point", "coordinates":[-96.85, 37.82]},
            "properties":{"YEAR":"1950", "MONTH":"5", "DAY":"19", "STATE":"KS",
                          "FSCALE":"0", "INJURIES":"1", "FATALITIES":"1", "LOSS":"3",
                          "CROPLOSS":"0"}
           },
           ...
           {"type":"Feature","_id":"5455892240754670407",
            "geometry": {"type":"Point", "coordinates":[-84.15, 33.03]},
            "properties":{"YEAR":"1950", "MONTH":"6", "DAY":"7", "STATE":"GA",
                          "FSCALE":"1", "INJURIES":"3", "FATALITIES":"1", "LOSS":"3",
                          "CROPLOSS":"0"}
           }
          ]};

     var propertyLoss = new OM.Column(
                       {data:myData.features,
                        keyGetter:function(){return this._id;},
                        valueGetter: function() {return parseFloat(this.properties["LOSS"]);}
                     });

### Methods

------------------------------------------------------------------------

#### getMax()

Gets the maximum value of this Column instance.

##### Returns:

the maximum value of this measure

Type
Number

------------------------------------------------------------------------

#### getMin()

Gets the minimum value of this Column instance.

##### Returns:

the minimum value of this measure

Type
Number

------------------------------------------------------------------------

#### getSize()

Return the number of rows in this Column data set.

------------------------------------------------------------------------

#### getValueOfRow(key, returns)

An interface method for returning the column data of the specified
row key.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                              |
|-----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `key`     | Object | the key column(s). This must be a literal object<br>containing a single property named 'key'. The value<br>for this property must be an array containing one<br>or more values comprising the actual key. For example<br>{key:\["California", "Marin"\]} |
| `returns` | Object | the value; or null if no row matching the key<br>can be found.                                                                                                                                                                                           |
