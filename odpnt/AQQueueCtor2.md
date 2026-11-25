This constructor takes a queue name and connection to initialize a queue object. The connection does not need to be open during the queue object construction.

### Declaration

    // C#
    public OracleAQQueue(string name, OracleConnection con);

### Parameters

- `name`

  Name of the queue as specified in the database.

- `con`

  An `OracleConnection` object that connects to the queue.

### Exceptions

`ArgumentNullException` - Either the connection is null or queue name is `null`.

`ArgumentException` - Queue name is empty.

### Remarks

The connection can be accessed using the `Connection` property, and it must be opened before calling any operational APIs such as `Enqueue` and `Dequeue`.

Creating an `OracleAQQueue` object does not check for the existence of the queue in the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
