`OracleAQMessageAvailableEventArgs` properties are listed in Table 12-19.

Table 12-19 OracleAQMessageAvailableEventArgs Properties

| Property                                                             | Description                                                                                                   |
|:---------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| [AvailableMessages](AQMessageAvailableEventArgsAvailableMessages.md) | Specifies the number of messages that raised this notification.                                               |
| [ConsumerName](AQMessageAvailableEventArgsConsumerName.md)           | Provides the name of the consumer for which the message is available for dequeuing.                           |
| [Correlation](AQMessageAvailableEventArgsCorrelation.md)             | Provides the name of the consumer for which the message is available for dequeuing.                           |
| [Delay](AQMessageAvailableEventArgsDelay.md)                         | Specifies the duration, in seconds, after which an enqueued message is available for dequeuing.               |
| [DeliveryMode](AQMessageAvailableEventArgsDeliveryMode.md)           | Specifies the delivery mode of the message.                                                                   |
| [EnqueueTime](AQMessageAvailableEventArgsEnqueueTime.md)             | Specifies the time when the message was enqueued.                                                             |
| [ExceptionQueue](AQMessageAvailableEventArgsExceptionQueue.md)       | Specifies the name of the queue that the message is moved to if it cannot be processed successfully.          |
| [Expiration](AQMessageAvailableEventArgsExpiration.md)               | Specifies the duration, in seconds, for which an enqueued message is available for dequeuing before expiring. |
| [MessageId](AQMessageAvailableEventArgsMessageId.md)                 | Returns an array of message identifiers.                                                                      |
| [NotificationType](AQMessageAvailableEventArgsNotificationType.md)   | Indicates the type of notification such as regular, grouping, or timeout.                                     |
| [OriginalMessageId](AQMessageAvailableEventArgsOriginalMessageId.md) | Specifies the ID of the message, in the last queue, that generated this message.                              |
| [Priority](AQMessageAvailableEventArgsPriority.md)                   | Specifies the priority of the message.                                                                        |
| [QueueName](AQMessageAvailableEventArgsQueueName.md)                 | Indicates the name of the queue that contains the message to be dequeued.                                     |
| [SenderId](MessageAvailableEventArgsSenderId.md)                     | Identifies the original sender of the message.                                                                |
| [State](AQMessageAvailableEventArgsState.md)                         | Specifies the state of the message.                                                                           |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessageAvailableEventArgs Class](OracleAQMessageAvailableEventArgsClass.md)

- [OracleAQMessageAvailableEventArgs Members](AQMessageAvailableEventArgsMembers.md)
