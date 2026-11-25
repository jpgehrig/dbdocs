This method copies all rows in the supplied `IDataReader` to a destination table specified by the `DestinationTableName` property of the `OracleBulkCopy` object.

### Declaration

    // C#
    public void WriteToServer(IDataReader reader);

### Parameters

- `reader`

  A `IDataReader` instance containing rows to be copied to the destination table.

### Exceptions

`ArgumentNullException` - The `reader` parameter is null.

`InvalidOperationException` - The connection is not in an open state.

### Remarks

The bulk copy operation starts with the next available row of the data reader. Typically, the `reader` returned by a call to the `ExecuteReader` method is passed to the `WriteToServer` method so that the next row becomes the first row. To copy multiple result sets, the application must call `NextResult` on the `reader` and then call the `WriteToServer` method again.

This `WriteToServer` method changes the state of the reader as it calls `reader.Read` internally to get the source rows. Thus, at the end of the `WriteToServer` operation, the `reader` is at the end of the result set.

The `ColumnMappings` collection maps from the data reader columns to the destination database table.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
