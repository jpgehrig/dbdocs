This constructor takes a queue name, connection, message type enumeration, and UDT type name to initialize a queue object. The connection does not need to be open during the queue object construction.

### Declaration

    // C#
    public OracleAQQueue(string name, OracleConnection con, OracleAQMessageType
      messageType, string udtTypeName);

### Parameters

- `name`

  The name of the queue as specified in the database.

- `con`

  An `OracleConnection` object that is used to connect to the queue.

- `messageType`

  An `OracleAQMessageType` enumeration specifying the type of the message that is enqueued or dequeued from this queue.

- `udtTypeName`

  The name of the database object type used if the `messageType` is UDT. The `udtTypeName` parameter represents the type on which the queue is based.

### Exceptions

`ArgumentNullException` - The connection is `null` or the queue name is `null`.

`ArgumentException` - The queue name is empty or the specified `messageType` is not valid.

### Remarks

Creating an `OracleAQQueue` object does not check for the existence of the queue in the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
