This instance property specifies the enqueueing options used to enqueue a message to a queue.

### Declaration

    // C#
    public OracleAQEnqueueOptions EnqueueOptions {get; set}

### Property Value

An `OracleAQEnqueueOptions` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is an `OracleAQEnqueueOptions` object with default property values. Setting this property to `null` resets all enqueue options to their default values.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
