The `Consumer` class supports dequeuing of `Message`s and controls the dequeuing options.

Table 13-14 Enumerated Values Used by Consumer Class

| Attribute         | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DequeMode`       | • `DEQ_BROWSE `indicates that the message should be read without acquiring a lock; equivalent to a `SELECT`.<br>• `DEQ_LOCKED` indicates that the message should be read. Get its write lock, which lasts s for the duration of the transaction; equivalent to a `SELECT FOR UPDATE`.<br>• `DEQ_REMOVE` indicates that the message should be read. Update or delete it; the message can be retained in the queue table based on the retention properties. This is the default setting.<br>• `DEQ_REMOVE_NODATA` indicates that the receipt of the message should be confirmed, but its actual content should not be delivered.                                                                                                                                                              |
| `Navigation`      | • `DEQ_FIRST_MSG` indicates that the first available message on the queue that matches the search criteria must be retrieved. Resets the position to the beginning of the queue.<br>• `DEQ_NEXT_TRANSACTION` indicates that the next available message on the queue that matches the search criteria must be retrieved. If the previous message belongs to a message group, AQ retrieves the next available message that matches the search criteria and belongs to the message group. This is the default setting.<br>• `DEQ_NEXT_MSG` indicates that the remainder of the current transaction group, if any, should be skipped. The first message of the next transaction group may then be retrieved. This option can only be used if message grouping is enabled for the current queue. |
| `Visibility`      | • `DEQ_IMMEDIATE `indicates that the dequeued message is not part of the current transaction. It constitutes a transaction on its own.<br>• `DEQ_ON_COMMIT` indicates that the dequeue is part of the current transaction. This is the default setting.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `DequeWaitOption` | • `DEQ_WAIT_FOREVER` indicates that the consumer waits for the `Message` indefinitely.<br>• `DEQ_NO_WAIT` indicates that there should be not wait if there are no messages on the queue.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

Table 13-15 Summary of Consumer Methods

| Method                  | Description                                                                                                    |
|:------------------------|:---------------------------------------------------------------------------------------------------------------|
| Consumer()              | `Consumer` class constructor.                                                                                  |
| getConsumerName()       | Retrieves the name of the `Consumer`.                                                                          |
| getCorrelationId()      | Retrieves she correlation id of the message that is to be dequeued.                                            |
| getDequeueMode()        | Retrieves the dequeue mode of the `Consumer`.                                                                  |
| getMessageIdToDequeue() | Retrieves the id of the message that is dequeued.                                                              |
| getQueueName()          | Gets the name of the queue used by the consumer.                                                               |
| getPositionOfMessage()  | Retrieves the position of the Message that is dequeued.                                                        |
| getTransformation()     | Retrieves the transformation applied before a `Message` is dequeued.                                           |
| getVisibility()         | Retrieves the transactional behavior of the dequeue operation.                                                 |
| getWaitTime()           | Retrieves the specified behavior of the `Consumer` when waiting for a `Message` with matching search criteria. |
| isNull()                | Tests whether the `Consumer` object is `NULL`.                                                                 |
| operator=()             | Assignment operator for the `Consumer` class.                                                                  |
| receive()               | Receives and dequeues a `Message`                                                                              |
| setAgent()              | Sets the `Agent`'s name and address (queue name) on the consumer.                                              |
| setConsumerName()       | Sets the `Consumer` name.                                                                                      |
| setCorrelationId()      | Specifies the correlation identifier of the message to be dequeued.                                            |
| setDequeueMode()        | Specifies the locking behavior associated with dequeuing.                                                      |
| setMessageIdToDequeue() | Specifies the identifier of the `Message` to be dequeued.                                                      |
| setNull()               | Nullifies the `Consumer`; frees the memory associated with this object.                                        |
| setPositionOfMessage()  | Specifies position of the `Message` to be retrieved.                                                           |
| setQueueName()          | Specifies the name of a queue before dequeuing `Message`s.                                                     |
| setTransformation()     | Specifies transformation applied before dequeuing a `Message`.                                                 |
| setVisibility()         | Specifies if `Message` should be dequeued as part of the current transaction.                                  |
| setWaitTime()           | Specifies wait conditions if there are no `Message`s with matching criteria.                                   |

### 13.12.1 Consumer()

Consumer class constructor.

| Syntax                                                                    | Description                                                                                          |
|:--------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| `Consumer(`<br>`   const Connection *conn);`                              | Creates a new `Consumer` object with the specified `Connection` handle.                              |
| `Consumer(`<br>`   const Connection *conn`<br>`   const Agent& agent);`   | Creates a new `Consumer` object with specified `Connection` and properties of the specified `Agent`. |
| `Consumer(`<br>`   const Connection *conn,`<br>`   const string& queue);` | Creates a new `Consumer` object with specified `Connection` and queue.                               |
| `Consumer(`<br>`   const Consumer& consumer);`                            | Copy constructor.                                                                                    |

| Parameter  | Description                                        |
|:-----------|:---------------------------------------------------|
| `conn`     | The connection in which the` Consumer` is created. |
| `agent`    | Agent assigned to the `Consumer`.                  |
| `queue`    | Queue at which the `Consumer` retrieves messages.  |
| `consumer` | Original `Consumer` object.                        |

### 13.12.2 getConsumerName()

Retrieves the name of the `Consumer`.

#### Syntax

    string getConsumerName() const;

### 13.12.3 getCorrelationId()

Retrieves she correlation id of the message that is to be dequeued

#### Syntax

    string geCorrelationId() const;

### 13.12.4 getDequeueMode()

Retrieves the dequeue mode of the `Consumer`. `DequeueMode` is defined in Table 13-14.

#### Syntax

    DequeueMode getDequeueMode() const;

### 13.12.5 getMessageIdToDequeue()

Retrieves the id of the message that is dequeued.

#### Syntax

    Bytes getMessageToDequeue() const;

### 13.12.6 getPositionOfMessage()

Retrieves the position, or navigation, of the message that is dequeued. `Navigation` is defined in Table 13-14.

#### Syntax

    Navigation getPositionOfMessage() const;

### 13.12.7 getQueueName()

Gets the name of the queue used by the consumer.

#### Syntax

    string getQueueName() const;

### 13.12.8 getTransformation()

Retrieves the transformation applied before a `Message` is dequeued.

#### Syntax

    string getTransformation() const;

### 13.12.9 getVisibility()

Retrieves the transactional behavior of the dequeue operation, or visibility. `Visibility` is defined in Table 13-14.

#### Syntax

    Visibility getVisibility() const;

### 13.12.10 getWaitTime()

Retrieves the specified behavior of the `Consumer` when waiting for a `Message` with matching search criteria. `DequeWaitOption` is defined in Table 13-14.

#### Syntax

    DequeWaitOption getWaitTime() const;

### 13.12.11 isNull()

Tests whether the `Consumer` object is `NULL`. If the `Consumer` object is `NULL`, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.12.12 operator=()

Assignment operator for `Consumer` class.

#### Syntax

    void operator=(
       const Consumer& consumer);

| Parameter  | Description              |
|:-----------|:-------------------------|
| `consumer` | The original `Consumer`. |

### 13.12.13 receive()

Receives and dequeues a `Message`.

#### Syntax

    Message receive(
       Message::PayloadType pType,
       const string& type="",
       const string& schema="");

| Parameter | Description                                                           |
|:----------|:----------------------------------------------------------------------|
| `pType`   | The type of payload expected. Payload Type is defined in Table 13-14. |
| `type`    | The type of the payload when `type` is `OBJECT`.                      |
| `schema`  | The schema in which the type is defined when `pType` is `OBJECT`.     |

### 13.12.14 setAgent()

Sets the `Agent`'s name and address (queue name) on the consumer.

#### Syntax

    void setAgent(
       const Agent& agent);

| Parameter | Description          |
|:----------|:---------------------|
| `agent`   | Name of the `Agent`. |

### 13.12.15 setConsumerName()

Sets the `Consumer` name. Only messages with matching consumer name can be accessed. If a queue is not set up for multiple consumer, this option should be set to `NULL`.

#### Syntax

    void setConsumerName(
       const string& name);

| Parameter | Description             |
|:----------|:------------------------|
| `name`    | Name of the `Consumer`. |

### 13.12.16 setCorrelationId()

Specifies the correlation identifier of the message to be dequeued. Special pattern matching characters, such as the percent sign (%) and the underscore(\_) can be used. If several messages satisfy the pattern, the order of dequeuing is undetermined.

#### Syntax

    void setCorrelationId
       const string& id);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `id`      | The identifier of the `Message`. |

### 13.12.17 setDequeueMode()

Specifies the locking behavior associated with dequeuing.

#### Syntax

    void setDequeueMode(
       DequeueMode mode);

| Parameter | Description                                                   |
|:----------|:--------------------------------------------------------------|
| `mode`    | Behavior of enqueuing. `DequeMode` is defined in Table 13-14. |

### 13.12.18 setMessageIdToDequeue()

Specifies the identifier of the `Message` to be dequeued.

#### Syntax

    void setMessageIdToDequeue(
       const Bytes& msgid);

| Parameter | Description                                 |
|:----------|:--------------------------------------------|
| `msgid`   | Identifier of the `Message` to be dequeued. |

### 13.12.19 setNull()

Nullifies the `Consumer`; frees the memory associated with this object.

#### Syntax

    void setNull();

### 13.12.20 setPositionOfMessage()

Specifies position of the `Message` to be retrieved.

#### Syntax

    void setPositionOfMessage(
       Navigation pos);

| Parameter | Description                                                       |
|:----------|:------------------------------------------------------------------|
| `pos`     | Position of the message, `Navigation`, is defined in Table 13-14. |

### 13.12.21 setQueueName()

Specifies the name of a queue before dequeuing `Message`s. Typically used when dequeuing multiple messages from the same queue.

#### Syntax

    void setQueueName(
       const string& queue);

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `queue`   | The name of a valid queue in the database. |

### 13.12.22 setTransformation()

Specifies transformation applied before dequeuing the `Message`.

#### Syntax

    void setTransformation(
       string &fName);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `fName`   | SQL transformation function. |

### 13.12.23 setVisibility()

Specifies if `Message` should be dequeued as part of the current transaction. Visibility parameter is ignored when in `DEQ_BROWSE` mode.

#### Syntax

    void setVisibility(
       Visibility option);

| Parameter | Description                                          |
|:----------|:-----------------------------------------------------|
| `option`  | Visibility option being set, defined in Table 13-14. |

### 13.12.24 setWaitTime()

Specifies wait conditions if there are no `Message`s with matching criteria. The `wait` parameter is ignored if messages in the same group are being dequeued.

#### Syntax

    void setWaitTime(
       DequeWaitOption wait);

| Parameter | Description                                                      |
|:----------|:-----------------------------------------------------------------|
| `wait`    | Waiting conditions. `DequeWaitOption` is defined in Table 13-14. |
