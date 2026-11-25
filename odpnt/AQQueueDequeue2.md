This instance method dequeues messages from a queue using the supplied dequeue options.

### Declaration

    // C#
    public OracleAQMessage Dequeue(OracleAQDequeueOptions dequeueOptions);

### Parameters

- `dequeueOptions`

  An `OracleAQDequeueOptions` object.

### Return Value

An `OracleAQMessage` instance representing the dequeued message.

### Exceptions

`InvalidOperationException` - The connection is not open.

`ObjectDisposedException` - The object is already disposed.

`OracleException` - In case of timeout, an exception is thrown with the message, `ORA-25228: timeout or end-of-fetch during message dequeue from queue_name. `Timeout may happen if `DequeueOptions.Wait` is set to a value other than `-1`.

### Remarks

If the supplied `dequeueOptions` object is `null,` then the dequeue options default values are used. The queue object's `DequeueOptions` property is ignored for this operation.

Calling this method does not change the `DequeueOptions` property of the queue.

The `MessageType` property must be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must also be set.

Dequeued buffered messages always have `null` `MessageId` values.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
