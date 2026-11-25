This method copies rows that match the supplied row state in the supplied `DataTable` to a destination table specified by the `DestinationTableName` property of the `OracleBulkCopy` object.

### Declaration

    // C#
    public void WriteToServer(DataTable table, DataRowState rowState);

### Parameters

- `table`

  A `DataTable` containing rows to be copied to the destination table.

- `rowState`

  The `DataRowState` enumeration value. Only rows matching the row state are copied to the destination.

### Exceptions

`ArgumentNullException` - The `table` or `rowState` parameter is null.

`InvalidOperationException` - The connection is not in an open state.

### Remarks

Only rows in the `DataTable` that are in the state indicated in the `rowState` argument and have not been deleted are copied to the destination table.

The `ColumnMappings` collection maps from the `DataTable` columns to the destination database table.

`DataRowState.Deleted` is not supported and the behavior would be that all the rows except the deleted ones are copied.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
