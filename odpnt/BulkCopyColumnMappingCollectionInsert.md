This method inserts a new `OracleBulkCopyColumnMapping` object in the collection, at the index specified.

### Declaration

    // C#
    public void Insert(int index, OracleBulkCopyColumnMapping value);

### Parameters

- `index`

  The integer value of the location within the `OracleBulkCopyColumnMappingCollection` at which the new `OracleBulkCopyColumnMapping` is inserted.

- `value`

  The `OracleBulkCopyColumnMapping` object to be inserted in the collection.

### Exceptions

`InvalidOperationException` - The bulk copy operation is in progress.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMappingCollection Class](OracleBulkCopyColumnMappingCollectionClass.md)

- [OracleBulkCopyColumnMappingCollection Members](OracleBulkCopyColumnMappingCollectionMembers.md)
