`OracleAQQueue` properties are listed in Table 12-26.

Table 12-26 OracleAQQueue Properties

| Property                                                 | Description                                                                                                                                 |
|:---------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| [Connection](AQQueueConnection.md)                       | Specifies the `OracleConnection` object associated with the queue.                                                                          |
| [DequeueOptions](AQQueueDequeueOptions.md)               | Specifies the dequeueing options to use when dequeuing a message from a queue.                                                              |
| [EnqueueOptions](AQQueueEnqueueOptions.md)               | Specifies the enqueueing options used to enqueue a message to a queue.                                                                      |
| [MessageType](AQQueueMessageType.md)                     | Specifies the type of queue table associated with this queue.                                                                               |
| [Name](AQQueueName.md)                                   | Returns the name of the queue.                                                                                                              |
| [Notification](AQQueueNotification.md)                   | Specifies the various notification options for notifications that are registered using the `MessageAvailable` event.                        |
| [NotificationConsumers](AQQueueNotificationConsumers.md) | Specifies the array of consumers, for a multiconsumer queue, that are to be notified asynchronously for any incoming messages on the queue. |
| [UdtTypeName](AQQueueUdtTypeName.md)                     | Specifies the type name on which the queue and the corresponding queue table is based if the `MessageType` is `OracleAQMessageType.UDT`.    |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
