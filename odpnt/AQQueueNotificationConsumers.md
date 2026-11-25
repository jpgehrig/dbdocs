This instance property specifies the array of consumers, for a multiconsumer queue, that are to be notified asynchronously for any incoming messages on the queue.

### Declaration

    // C#
    public string[] NotificationConsumers {get; set;}

### Property Value

Specifies an array of consumer name strings for which the notifications are delivered.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - `MessageAvailable` registration is active.

### Remarks

The consumer names must be in uppercase. This functionality only supports queues with uppercase names.

The list of consumers is used in the `MessageAvailable` event. The list must be set before registering for the event. This property cannot be modified after registering for the `MessageAvailable` event. This property can be modified again only after unregistering from `MessageAvailable` event.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
