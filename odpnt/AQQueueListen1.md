This static method listens for messages on one or more queues for one or more consumers as specified in the array of `OracleAQAgent` objects.

### Declaration

    // C#
    public static OracleAQAgent Listen(OracleConnection con, OracleAQAgent[]
      listenConsumers);

### Parameters

- `con`

  An `OracleConnection` instance.

- `listenConsumers`

  The array of consumers being listened for. The name of the `OracleAQAgent` object must be `null` or empty for single consumer queues.

### Return Value

An `OracleAQAgent` object.

### Exceptions

`ArgumentNullException` - The `con` or `listenConsumers` parameter is null.

`InvalidOperationException` - The connection is not open.

### Remarks

`Listen` is useful in situations where one needs to monitor multiple queues until a message is available for a consumer in one of the queues. The `Name` property of the `OracleAQAgent` object represents the name of the consumer and the `Address` property represents the name of the queue.

This call blocks the calling thread until there is a message ready for consumption for a consumer in the list. It returns an `OracleAQAgent` object which specifies the consumer and queue for which a message is ready to be dequeued.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
