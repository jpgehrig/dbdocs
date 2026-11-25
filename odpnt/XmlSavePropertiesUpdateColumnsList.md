This property specifies the list of columns to update or insert.

### Declaration

    // C#
    public string[] UpdateColumnsList {get; set;}

### Property Value

A list of columns.

### Remarks

Default value is null.

The first null value (if any) terminates the list.

`UpdateColumnList` usage with `XMLCommandType` property values:

- `Insert` - `UpdateColumnList` indicates which columns are assigned values when a new row is created. If `UpdateColumnList` is null, then all columns are assigned values. If a column is on the `UpdateColumnList`, but no value is specified for the row in the XML file, then `NULL` is used. If a column is not on the `UpdateColumnList`, then the default value for that column is used.

- `Update` - `UpdateColumnList` specifies columns to modify for each row of data in the XML document. If `UpdateColumnList` is null, all the values in each XML element in the XML document are used to modify the columns.

- `Delete` - `UpdateColumnsList` is ignored and can be null.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlSaveProperties Class](OracleXmlSavePropertiesClass.md)

- [OracleXmlSaveProperties Members](XmlSavePropertiesMembers.md)
