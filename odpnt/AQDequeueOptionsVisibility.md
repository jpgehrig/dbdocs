This instance property specifies whether or not the new message is dequeued as part of the current transaction.

### Declaration

    // C#
    public OracleAQVisibilityMode Visibility {get;set;}

### Property Value

An `OracleAQVisibilityMode` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The `Visibility` value specified is invalid.

### Remarks

The default value is `OracleAQVisibilityMode.OnCommit`. You must use transactions when using the default value for this property. This ensures that applications do not lose messages and the messages are appropriately removed from the queue after the dequeue operation is successful. If transactions are not used when using the default visibility mode of `OracleAQVisibilityMode.OnCommit`, then messages are not removed from the queue.

Using the alternative visibility mode value, `OracleAQVisibilityMode.Immediate` can eliminate the need to create, commit, and rollback a transaction. However, if an error occurs during the dequeue operation, then the message may be lost.

The visibility parameter is ignored when `DequeueMode` is set to `OracleAQDequeueMode.Browse`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
