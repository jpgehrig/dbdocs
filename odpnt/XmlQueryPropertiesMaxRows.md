This property specifies the maximum number of rows from the result set of the query that can be represented in the result XML document.

### Declaration

    // C#
    public int MaxRows {get; set;}

### Property Value

The maximum number of rows.

### Exceptions

`ArgumentException` - The new value for `MaxRows` is not valid.

### Remarks

Default value is `-1`.

Possible values are:

- `-1` (all rows).

- A number greater than or equal to `0`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlQueryProperties Class](OracleXmlQueryPropertiesClass.md)

- [OracleXmlQueryProperties Members](XmlQueryPropertiesMembers.md)
