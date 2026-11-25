`OracleAQMessage` members are listed in the following tables.

### OracleAQMessage Constructor

`OracleAQMessage` constructors are listed in Table 12-14.

Table 12-14 OracleAQMessage Constructors

| Constructor                                              | Description                                                              |
|:---------------------------------------------------------|:-------------------------------------------------------------------------|
| [OracleAQMessage Constructors](AQMessageConstructors.md) | Instantiates a new instance of the `OracleAQMessage` class (Overloaded). |

### OracleAQMessage Properties

`OracleAQMessage` properties are listed in Table 12-15.

Table 12-15 OracleAQMessage Properties

| Property                                           | Description                                                                                                 |
|:---------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| [Correlation](AQMessageCorrelation.md)             | Specifies an identification for the message.                                                                |
| [Delay](AQMessageDelay.md)                         | Specifies the duration, in seconds, after which an enqueued message is available for dequeuing.             |
| [DeliveryMode](AQMessageDeliveryMode.md)           | Specifies the delivery mode of the dequeued message.                                                        |
| [DequeueAttempts](AQMessageDequeueAttempts.md)     | Returns the number of attempts that have been made to dequeue the message.                                  |
| [EnqueueTime](AQMessageEnqueueTime.md)             | Specifies the time when the message was enqueued.                                                           |
| [ExceptionQueue](AQMessageExceptionQueue.md)       | Specifies the name of the queue that the message should be moved to if it cannot be processed successfully. |
| [Expiration](AQMessageExpiration.md)               | Specifies the duration, in seconds, for which an enqueued message is available for dequeuing.               |
| [MessageId](AQMessageMessageId.md)                 | Returns the message identifier.                                                                             |
| [OriginalMessageId](AQMessageOriginalMessageId.md) | Specifies the identifier of the message in the last queue that generated this message.                      |
| [Payload](AQMessagePayload.md)                     | Specifies the payload of the message.                                                                       |
| [Priority](AQMessagePriority.md)                   | Specifies the priority of the message.                                                                      |
| [Recipients](AQMessageRecipients.md)               | Specifies the list of recipients that overrides the default queue subscribers.                              |
| [SenderId](AQMessageSenderId.md)                   | Identifies the original sender of the message.                                                              |
| [State](AQMessageState.md)                         | Specifies the state of the message at the time of dequeue.                                                  |
| [TransactionGroup](AQMessageTransactionGroup.md)   | Specifies the transaction group for the dequeued message.                                                   |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)
