The `OracleRowsCopiedEventHandler` delegate represents the method that handles the `OracleRowsCopied` event of an `OracleBulkCopy` object.

### Declaration

    // C#
    public delegate void OracleRowsCopiedEventHandler (object sender,    OracleRowsCopiedEventArgs eventArgs);

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Parameters

- `sender`

  The source of the event.

- `eventArgs`

  The `OracleRowsCopiedEventArgs` object that contains the event data.

### Remarks

Event callbacks can be registered through this event delegate for applications that wish to be notified every time the number of rows specified by the `OracleBulkCopy.NotifyAfter` property has been processed.

If the event handler calls the `OracleBulkCopy.Close` method, an exception is generated, and the `OracleBulkCopy` object state does not change.

The event handler can also set the `OracleRowsCopiedEventArgs.Abort` property to `true` to indicate that the bulk copy operation must be aborted. If the bulk copy operation is part of an external transaction, an exception is generated and the transaction is not rolled back. The application is responsible for either committing or rolling back the external transaction.

If there is no external transaction, the internal transaction for the current batch of rows is automatically rolled back. However the previous batches of imported rows are unaffected, as their transactions have already been committed.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleRowsCopied](BulkCopyOracleRowsCopied.md)"

- "[NotifyAfter](BulkCopyNotifyAfter.md)"
