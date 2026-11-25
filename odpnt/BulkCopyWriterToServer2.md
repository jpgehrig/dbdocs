This method copies all rows in the supplied `DataTable` to a destination table specified by the `DestinationTableName` property of the `OracleBulkCopy` object.

### Declaration

    // C#
    public void WriteToServer(DataTable table);

### Parameters

- `table`

  The source `DataTable` containing rows to be copied to the destination table.

### Exceptions

`ArgumentNullException` - The `table` parameter is null.

`InvalidOperationException` - The connection is not in an open state.

### Remarks

All rows in the `DataTable` are copied to the destination table except those that have been deleted.

The `ColumnMappings` collection maps from the `DataTable` columns to the destination database table.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
