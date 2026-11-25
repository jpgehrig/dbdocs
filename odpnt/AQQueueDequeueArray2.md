This instance method dequeues multiple messages from a queue using the supplied dequeue options.

### Declaration

    // C#
    public OracleAQMessage[] DequeueArray(int dequeueCount, OracleAQDequeueOptions dequeueOptions);

### Parameters

- `dequeueCount`

  An `integer` specifying the numbers of messages to dequeue.

- `dequeueOptions`

  An `OracleAQDequeueOptions` object.

### Return Value

An array of `OracleAQMessage` instances representing the dequeued messages.

### Exceptions

`ArgumentOutOfRangeException` - `dequeueCount` is less than or equal to 0.

`InvalidOperationException` - The connection is not open.

`ObjectDisposedException` - The object is already disposed.

`OracleException` - In case of timeout, an exception is thrown with the message, `ORA-25228: timeout or end-of-fetch during message dequeue from queue_name. `Timeout may happen if `DequeueOptions.Wait` is set to a value other than `-1`.

### Remarks

This method is supported for Oracle Database 10g Release 1 (10.1) and higher releases. Calling this method does not change the `DequeueOptions` property of the queue.

If the supplied `dequeueOptions` object is `null`, then the dequeue options default values are used. The `DequeueOptions` property of the queue object is ignored in this operation.

The `MessageType` property must be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must be set as well.

The size of the returned array may be less than the `dequeueCount`. It dependes on the actual number of messages present in the queue.

For database versions earlier than Oracle Database 12c Release 2 (12.2), the `MessageId` property of persistent `OracleAQMessage` objects retrieved using `DequeueArray` is always `null`.

Dequeued buffered messages always have `null` `MessageId` values irrespective of the database version.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
