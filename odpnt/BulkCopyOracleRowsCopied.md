This event is triggered every time the number of rows specified by the `OracleBulkCopy.NotifyAfter` property has been processed.

### Declaration

    // C#
    public event OracleRowsCopiedEventHandler OracleRowsCopied;

### Exceptions

`InvalidOperationException` - The `Close` method is called inside this event.

### Remarks

This event is raised when the number of rows specified by the `NotifyAfter` property has been processed. It does not imply that the rows have been sent to the database or committed.

To cancel the operation from this event, use the `Abort` property of `OracleRowsCopiedEventArgs` class.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[NotifyAfter](BulkCopyNotifyAfter.md)"
