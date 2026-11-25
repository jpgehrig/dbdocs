This instance method is used to dequeue a message from a queue using the `DequeueOptions` for the instance.

### Declaration

    // C#
    public OracleAQMessage Dequeue();

### Return Value

An `OracleAQMessage` instance representing the dequeued message.

### Exceptions

`InvalidOperationException` - The connection is not open.

`ObjectDisposedException` - The object is already disposed.

`OracleException` - In case of timeout, an exception is thrown with the message, `ORA-25228: timeout or end-of-fetch during message dequeue from queue_name.`Timeout may happen if `DequeueOptions.Wait` is set to a value other than `-1`.

### Remarks

The `MessageType` property must be set appropriately before calling this function. If the `MessageType` is `OracleAQMessageType.UDT`, then the `UdtTypeName` property must also be set.

Dequeued buffered messages always have `null` `MessageId` values.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
