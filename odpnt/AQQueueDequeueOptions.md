This instance property specifies the dequeueing options to use when dequeuing a message from a queue.

### Declaration

    // C#
    public OracleAQDequeueOptions DequeueOptions {get; set}

### Property Value

An `OracleAQDequeueOptions` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is an `OracleAQDequeueOptions` object with default property values. Setting this property to `null` resets all dequeue options to their default values.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
