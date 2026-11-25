This instance method enqueues multiple messages to a queue using the `EnqueueOptions` of the instance.

### Declaration

    // C#
    public int EnqueueArray(OracleAQMessage[] messages);

### Parameters

- `messages`

  An array of `OracleAQMessage` objects.

### Return Value

An `integer` representing the number of messages actually enqueued.

### Exceptions

`ArgumentNullException` - The message parameter is `null`.

`ArgumentException` - At least one of the `OracleAQMessage[]` elements is `null,` or at least one of the `OracleAQMessage[]` elements has a payload of `OracleXmlType`, which is created using a connection that is different from the queue's connection.

`InvalidOperationException` - The `OracleAQMessage` array is empty or the connection is not open.

`ObjectDisposedException` - The object is already disposed.

### Remarks

This method is supported by Oracle Database 10g and higher releases. The `MessageId` properties of the enqueued messages are populated after the call to `Enqueue` completes. Enqueued buffered messages always have `null MessageId` values.

The `MessageType` property must be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must also be set.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
