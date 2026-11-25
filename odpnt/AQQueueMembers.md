`OracleAQQueue` members are listed in the following tables.

### OracleAQQueue Constructors

`OracleAQQueue` constructors are listed in Table 12-20.

Table 12-20 OracleAQQueue Constructors

| Constructor                                          | Description                                                           |
|:-----------------------------------------------------|:----------------------------------------------------------------------|
| [OracleAQQueue Constructors](AQQueueConstructors.md) | Instantiate a new instance of the `OracleAQQueue` class (Overloaded). |

### OracleAQQueue Static Methods

The `OracleAQQueue` static method is listed in Table 12-21.

Table 12-21 OracleAQQueue Static Methods

| Static Method                       | Description                                                                                                                              |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| [Listen](AQQueueListenOverloads.md) | Listens for messages on one or more queues for one or more consumers, as specified in the array of `OracleAQAgent` objects (Overloaded). |

### OracleAQQueue Properties

`OracleAQQueue` properties are listed in Table 12-22.

Table 12-22 OracleAQQueue Properties

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

### OracleAQQueue Public Methods

The `OracleAQQueue` public methods are listed in Table 12-23.

Table 12-23 OracleAQQueue Public Methods

| Public Method                                   | Description                                                                    |
|:------------------------------------------------|:-------------------------------------------------------------------------------|
| [Dequeue](AQQueueDequeueOverloads.md)           | Dequeues messages from queues (Overloaded).                                    |
| [DequeueArray](AQQueueDequeueArrayOverloads.md) | Dequeues multiple messages from queues (Overloaded).                           |
| [Dispose](AQQueueDispose.md)                    | Releases any resources or memory allocated by the object                       |
| [Enqueue](AQQueueEnqueueOverloads.md)           | Enqueues messages to queues (Overloaded).                                      |
| [EnqueueArray](AQQueueEnqueueArrayOverloads.md) | Enqueues multiple messages to a queue (Overloaded).                            |
| [Listen](AQQueueListenOverloads001.md)          | Listens for messages on the queue on behalf of `listenConsumers` (Overloaded). |

### OracleAQQueue Events

The `OracleAQQueue` event is listed in Table 12-24.

Table 12-24 OracleAQQueue Events

| Event Name                                                | Description                                                                    |
|:----------------------------------------------------------|:-------------------------------------------------------------------------------|
| [MessageAvailable Event](AQQueueMessageAvailableEvent.md) | Notifies when a message is available in the queue for `NotificationConsumers`. |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)
