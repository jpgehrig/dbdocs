This instance method enqueues messages to a queue using the supplied enqueue options.

### Declaration

    // C#
    public void Enqueue(OracleAQMessage message, OracleAQEnqueueOptions enqueueOptions);

### Parameters

- `message`

  An `OracleAQMessage` object.

- `enqueueOptions`

  An `OracleAQEnqueueOptions` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The connection is not open.

`ArgumentNullException` - The message parameter is `null`.

`ArgumentException` - The message payload is `OracleXmlType` and the connection used to create `OracleXmlType` is different from the queue's connection.

### Remarks

If the supplied `enqueueOptions` object is `null`, then the enqueue options default values are used. The `EnqueueOptions` property of the queue object is ignored in this operation.

The `MessageId` of the enqueued message is populated after the call to `Enqueue` completes. Enqueued buffered messages always have `null MessageId` values. Calling this method does not change the `EnqueueOptions` property of the queue.

The `MessageType` property must be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must also be set.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
