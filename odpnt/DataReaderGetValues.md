This method gets all the column values as .NET types.

### Declaration

    // C#
    public override int GetValues(object[ ] values);

### Parameters

- `values`

  An array of objects to hold the .NET types as the column values.

### Return Value

The number of objects in the `values` array.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

### Remarks

This method provides a way to retrieve all column values rather than retrieving each column value individually.

The number of column values retrieved is the minimum of the length of the values array and the number of columns in the result set.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
