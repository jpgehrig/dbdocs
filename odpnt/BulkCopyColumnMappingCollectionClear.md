This method clears the contents of the collection.

### Declaration

    // C#
    public void Clear();

### Exceptions

`InvalidOperationException` - The bulk copy operation is in progress.

### Remarks

The `Clear` method is most commonly used when an application uses a single `OracleBulkCopy` instance to process more than one bulk copy operation. If column mappings are created for one bulk copy operation, the `OracleBulkCopyColumnMappingCollection` must be cleared after the `WriteToServer` method invocation and before the next bulk copy is processed.

It is usually more efficient to perform several bulk copies using the same `OracleBulkCopy` instance than to use a separate `OracleBulkCopy` for each operation.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMappingCollection Class](OracleBulkCopyColumnMappingCollectionClass.md)

- [OracleBulkCopyColumnMappingCollection Members](OracleBulkCopyColumnMappingCollectionMembers.md)
