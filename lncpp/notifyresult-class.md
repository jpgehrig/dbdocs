A NotifyResult object holds the notification information in the Database AQ notification callback. It is created by OCCI before invoking a user-callback, and is destroyed after the user-callback returns.

Table 13-29 Summary of NotifyResult Methods

| Method            | Summary                                        |
|:------------------|:-----------------------------------------------|
| getConsumerName() | Returns the name of the notification consumer. |
| getMessage()      | Returns the message.                           |
| getMessageId()    | Returns the message ID.                        |
| getPayload()      | Returns the payload.                           |
| getQueueName()    | Returns the name of the queue.                 |

### 13.21.1 getConsumerName()

Gets the name of the consumer for which the message has been enqueued. In a single consumer queue, this is a empty string.

    string getConsumerName() const;

### 13.21.2 getMessage()

Gets the message which has been enqueued into the non-persistent queue.

    Message getMessage() const;

### 13.21.3 getMessageId()

Gets the id of the message which has been enqueued.

    Bytes getMessageId() const;

### 13.21.4 getPayload()

Gets the payload in case of a notification from `NS_ANONYMOUS` namespace.

    Bytes getPayload() const;

### 13.21.5 getQueueName()

Gets the name of the queue on which the enqueue has happened

    string getQueueName() const;
