This property specifies the `OracleConnection` object associated with the queue.

### Declaration

    // C#
    public OracleConnection Connection {get; set;}

### Property Value

An `OracleConnection` object that indicates the connection associated with the queue.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This connection must be opened before calling methods like `Enqueue` and `Dequeue`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
