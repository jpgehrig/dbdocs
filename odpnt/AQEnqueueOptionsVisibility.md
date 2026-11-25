This instance property specifies whether or not the new message is enqueued as part of the current transaction.

### Declaration

    // C#
    public OracleAQVisibilityMode Visibility {get;set;}

### Property Value

An `OracleAQVisibilityMode` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The specified `Visibility` value is invalid.

### Remarks

The default value is `OracleAQVisibilityMode.OnCommit`. You must use transactions when using the default value. If transactions are not used when using the default visibility mode of `OracleAQVisibilityMode.OnCommit`, then messages are not enqueued to the queue.

Using the alternative visibility mode value, `OracleAQVisibilityMode.Immediate` eliminates the need to use a transaction. The queue is not affected in case the enqueue operation fails. The message does not get enqueued to the queue for such cases.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQEnqueueOptions Class](OracleAQEnqueueOptionsClass.md)

- [OracleAQEnqueueOptions Members](AQEnqueueOptionsMembers.md)
