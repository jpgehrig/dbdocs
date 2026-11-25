This method creates and adds an `OracleBulkCopyColumnMapping` object to the collection using the supplied source and destination column ordinal positions.

### Declaration

    // C#
    public OracleBulkCopyColumnMapping Add(int sourceColumnIndex,
        int destinationColumnIndex);

### Parameters

- `sourceColumnIndex`

  The ordinal position of the source column within the data source.

- `destinationColumnIndex`

  The ordinal position of the destination column within the destination table.

### Exceptions

`InvalidOperationException` - The bulk copy operation is in progress.

### Return Value

The newly created `OracleBulkCopyColumnMapping` object that was added to the collection.

### Remarks

It is not necessary to specify column mappings for all the columns in the data source. If a `ColumnMapping` is not specified, then, by default, columns are mapped based on the ordinal position. This succeeds only if the source and destination table schema match. If there is a mismatch, an `InvalidOperationException` is thrown.

All the mappings in a mapping collection must be by name or ordinal position.

**Note:**

Oracle Data Provider for .NET makes one or more round-trips to the database to determine the column name if the mapping is specified by ordinal position. To avoid this performance overhead, specify the mapping by column name.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMappingCollection Class](OracleBulkCopyColumnMappingCollectionClass.md)

- [OracleBulkCopyColumnMappingCollection Members](OracleBulkCopyColumnMappingCollectionMembers.md)
