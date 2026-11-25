This method removes the specified `OracleBulkCopyColumnMapping` element from the `OracleBulkCopyColumnMappingCollection`.

### Declaration

    // C#
    public void Remove(OracleBulkCopyColumnMapping value);

### Parameters

- `value`

  The `OracleBulkCopyColumnMapping` object to be removed from the collection.

### Exceptions

`InvalidOperationException` - The bulk copy operation is in progress.

### Remarks

The `Remove` method is most commonly used when a single `OracleBulkCopy` instance processes more than one bulk copy operation. If column mappings are created for one bulk copy operation, mappings that no longer apply must be removed after the `WriteToServer` method invocation and before mappings are defined for the next bulk copy. The `Clear` method can clear the entire collection, and the `Remove` and the `RemoveAt` methods can remove mappings individually.

It is usually more efficient to perform several bulk copies using the same `OracleBulkCopy` instance than to use a separate `OracleBulkCopy` for each operation.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMappingCollection Class](OracleBulkCopyColumnMappingCollectionClass.md)

- [OracleBulkCopyColumnMappingCollection Members](OracleBulkCopyColumnMappingCollectionMembers.md)
