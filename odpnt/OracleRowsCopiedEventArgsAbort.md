This property retrieves or sets a value that indicates whether or not the bulk copy operation is aborted.

### Declaration

    // C#
    public bool Abort{get; set;}

### Property Value

Returns `true` if the bulk copy operation is to be aborted; otherwise, returns `false`.

### Remarks

Set the `Abort` property to `true` to cancel the bulk copy operation.

If the `Close` method is called from `OracleRowsCopied`, an exception is generated, and the `OracleBulkCopy` object state does not change.

If the application does not create a transaction, the internal transaction corresponding to the current batch is automatically rolled back. However, changes related to previous batches within the bulk copy operation are retained, because the transactions in those batches are committed. This case is applicable only when `UseInternalTransaction` bulk copy option is chosen.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowsCopiedEventArgs Class](OracleRowsCopiedEventArgsClass.md)

- [OracleRowsCopiedEventArgs Members](OracleRowsCopiedEventArgsMembers.md)
