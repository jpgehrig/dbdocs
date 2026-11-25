This constructor takes a queue name, connection and message type enumeration to initialize a queue object. The connection does not need to be open during the queue object construction.

### Declaration

    // C#
    public OracleAQQueue(string name, OracleConnection con, OracleAQMessageType
      messageType);

### Parameters

- `name`

  The name of the queue as specified in the database.

- `con`

  An `OracleConnection` object that is used to connect to the queue.

- `messageType`

  An `OracleAQMessageType` enumeration specifying the type of the message that is enqueued or dequeued from this queue.

### Exceptions

`ArgumentNullException` - Either the connection is `null` or queue name is `null`.

`ArgumentException` - Queue name is empty or the specified message type is not valid.

### Remarks

Creating an `OracleAQQueue` object does not check for the existence of the queue in the database.

You need to set the `UdtTypeName` property before using the queue object if the `messageType` is a UDT. Another approach is to create a queue using the other constructor overload by supplying the `udtTypeName`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
