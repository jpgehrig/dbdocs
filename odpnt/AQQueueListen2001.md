This method listens for messages on behalf of `listenConsumers` for a specified time.

### Declaration

    // C#
    public string Listen(string[] listenConsumers, int waitTime);

### Parameters

- `listenConsumers`

  Array of consumers for which to listen on this queue.

- `waitTime`

  Wait time in seconds.

### Return Value

A `string`

### Exceptions

`InvalidOperationException` - The connection is not open.

ArgumentException - `waitTime` is less than `-1`.

`ObjectDisposedException` - The object is already disposed.

### Remarks

`Listen` is useful in situations that require waiting until a message is available in the queue for consumers whose names are specified in `listenConsumers`.

This call blocks the calling thread until there is a message ready for consumption for a consumer in the `listenConsumers` array. It returns a `string` representing the consumer name for which the message is ready.The method returns `null` if a timeout occurs.

The `listenConsumers` parameter should be `null` for single consumer queues. An empty string is returned in such cases.

A `waitTime` of `-1` implies infinite wait time.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
