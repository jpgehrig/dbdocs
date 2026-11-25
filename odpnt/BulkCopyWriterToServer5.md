This method copies all rows from the specified `OracleRefCursor` to a destination table specified by the `DestinationTableName` property of the `OracleBulkCopy` object.

### Declaration

    // C#
    public void WriteToServer(OracleRefCursor refCursor);

### Parameters

- `refCursor`

  An `OracleRefCursor` object containing rows to be copied to the destination table.

### Exceptions

`ArgumentNullException` - The `refCursor` parameter is null

`InvalidOperationException` - The connection is not in an open state.

### Remarks

The `ColumnMappings` collection maps from the `OracleRefCursor` columns to the destination database table.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
