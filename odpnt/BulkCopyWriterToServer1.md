This method copies all rows from the supplied `DataRow` array to a destination table specified by the `DestinationTableName` property of the `OracleBulkCopy` object.

### Declaration

    // C#
    public void WriteToServer(DataRow[] rows);

### Parameters

- `rows`

  An array of `DataRow` objects to be copied to the destination table.

### Exceptions

`ArgumentNullException` - The `rows` parameter is null.

`InvalidOperationException` - The connection is not in an open state.

### Remarks

The `ColumnMappings` collection maps from the `DataRow` columns to the destination database table.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
