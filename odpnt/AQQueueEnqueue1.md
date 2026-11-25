This instance method enqueues messages to a queue using the `EnqueueOptions` of the instance.

### Declaration

    // C#
    public void Enqueue(OracleAQMessage message);

### Parameters

- `message`

  An `OracleAQMessage` object.

Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The connection is not open.

`ArgumentNullException` - The message parameter is `null`.

`ArgumentException` - The message payload is `OracleXmlType` and the connection used to create `OracleXmlType` is different from the queue's connection.

### Remarks

`MessageId` of the enqueued message is populated after the call to `Enqueue` completes. Enqueued buffered messages always have `null MessageId` values.

The `MessageType` property needs to be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must be set as well.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
