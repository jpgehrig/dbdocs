A message is the unit that is enqueued dequeued. A `Message` object holds both its content, or payload, and its properties. This class provides methods to get and set message properties.

Table 13-25 Enumerated Values Used by Message Class

| Attribute      | Options                                                                                                                                                                                                                                                                                                                        |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MessageState` | • `MSG_WAITING `indicates that the message delay time has not been reached<br>• `MSG_READY` indicates that the message is ready to be processed<br>• `MSG_PROCESSED` indicates that the message has been processed, and is being retained<br>• `MSG_EXPIRED` indicates that the message has been moved to the exception queue. |
| `PayloadType`  | • `RAW`<br>• `ANYDATA`<br>• `OBJECT`                                                                                                                                                                                                                                                                                           |

Table 13-26 Summary of Message Methods

| Method                   | Summary                                                                                           |
|:-------------------------|:--------------------------------------------------------------------------------------------------|
| Message()                | `Message` class constructor.                                                                      |
| getAnyData()             | Retrieves `AnyData` payload of the message.                                                       |
| getAttemptsToDequeue()   | Retrieves the number of attempts made to dequeue the message.                                     |
| getBytes()               | Retrieves `Bytes` payload of the message.                                                         |
| getCorrelationId()       | Retrieves the identification string.                                                              |
| getDelay()               | Retrieves delay with which message was enqueued.                                                  |
| getExceptionQueueName()  | Retrieves name of queue to which `Message` is moved when it cannot be processed.                  |
| getExpiration()          | Retrieves the expiration of the message.                                                          |
| getMessageEnqueuedTime() | Retrieves time at which message was enqueued.                                                     |
| getMessageState()        | Retrieves state of the message at time of enqueuing.                                              |
| getObject()              | Retrieves object payload of the message.                                                          |
| getOriginalMessageId()   | Retrieves the Id of the message that generated this message on the last queue.                    |
| getPayloadType()         | Retrieves the type of the payload.                                                                |
| getPriority()            | Retrieves the priority of the message.                                                            |
| getSenderId()            | Retrieves the agent who send the `Message`.                                                       |
| isNull()                 | Tests whether the `Message` object is `NULL`.                                                     |
| operator=()              | Assignment operator for `Message`.                                                                |
| setAnyData()             | Specifies `AnyData` payload of the message.                                                       |
| setBytes()               | Specifies `Bytes` payload of the message.                                                         |
| setCorrelationId()       | Specifies the identification string.                                                              |
| setDelay()               | Specifies the number of seconds to delay the enqueued `Message`.                                  |
| setExceptionQueueName()  | Specifies the name of the queue to which the `Message` object is moved if it cannot be precessed. |
| setExpiration()          | Specifies the duration of time that `Message` can be dequeued before it expires.                  |
| setNull()                | Sets the `Message` object to `NULL`.                                                              |
| setObject()              | Specifies object payload of the message.                                                          |
| setOriginalMessageId()   | Specifies id of last queue that generated the `Message`.                                          |
| setPriority()            | Specifies priority of the `Message` object.                                                       |
| setRecipientList()       | Specifies the list of agents for whom the message is intended.                                    |
| setSenderId()            | Specifies the sender of the `Message`.                                                            |

### 13.19.1 Message()

`Message` class constructor.

| Syntax                                       | Description                                                    |
|:---------------------------------------------|:---------------------------------------------------------------|
| `Message(`<br>`    const Environment *env);` | Creates a `Message` object within the specified `Environment`. |
| `Message(`<br>`   const Message& mes);`      | Copy constructor.                                              |

| Parameter | Description                       |
|:----------|:----------------------------------|
| `env`     | The environment of the `Message`. |
| `mes`     | The original `Message`.           |

### 13.19.2 getAnyData()

Retrieves the `AnyData` payload of the `Message`.

#### Syntax

    AnyData getAnyData() const;

### 13.19.3 getAttemptsToDequeue()

Retrieves the number of attempts made to dequeue the message. This property cannot be retrieved while enqueuing.

#### Syntax

    int getAttemptsToDequeue() const;

### 13.19.4 getBytes()

Retrieves `Bytes` payload of the `Message`.

#### Syntax

    Bytes getBytes() const;

### 13.19.5 getCorrelationId()

Retrieves the identification string.

#### Syntax

    string getCorrelationId() const;

### 13.19.6 getDelay()

Retrieves the delay (in seconds) with which the `Message` was enqueued.

#### Syntax

    int getDelay() const;

### 13.19.7 getExceptionQueueName()

Retrieves the name of the queue to which the `Message` is moved, in cases when the `Message` cannot be processed successfully.

#### Syntax

    string getExceptionQueueName() const;

### 13.19.8 getExpiration()

Retrieves the expiration time of the `Message` (in seconds). This is the duration for which the message is available for dequeuing.

#### Syntax

    int getExpiration() const;

### 13.19.9 getMessageEnqueuedTime()

Retrieves the time at which the message was enqueued, in `Date` format. This value is determined by the system, and cannot be set by the user.

#### Syntax

    Date getMessageEnqueuedTime() const;

### 13.19.10 getMessageState()

Retrieves the state of the message at the time of enqueuing. This parameter cannot be set an enqueuing time. `MessageState` is defined in Table 13-25.

#### Syntax

    MessageState getMessageState() const;

### 13.19.11 getObject()

Retrieves object payload of the `Message`.

#### Syntax

    PObject* getObject();

### 13.19.12 getOriginalMessageId()

Retrieves the original message Id. When a message is propagated from one queue to another, gets the ID to the last queue that generated this message.

#### Syntax

    Bytes getOriginalMessageId() const;

### 13.19.13 getPayloadType()

Retrieves the type of the payload, as defined for `PayloadType` in Table 13-25.

#### Syntax

    PayloadType getPayloadType( ) const;

### 13.19.14 getPriority()

Retrieves the priority of the `Message`.

#### Syntax

    int getPriority() const;

### 13.19.15 getSenderId()

Retrieves the agent who send the `Message`.

#### Syntax

    Agent getSenderId() const;

### 13.19.16 isNull()

Tests whether the `Message` object is `NULL`. If the `Message` object is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.19.17 operator=()

Assignment operator for `Message`.

    void operator=(
       const Message& mes);

| Parameter | Description       |
|:----------|:------------------|
| `mes`     | Original message. |

### 13.19.18 setAnyData()

Specifies `AnyData` payload of the `Message`.

#### Syntax

    void setAnyData(
       const AnyData& anydata);

| Parameter | Description                    |
|:----------|:-------------------------------|
| `anydata` | Data content of the `Message`. |

### 13.19.19 setBytes()

Specifies `Bytes` payload of the `Message`.

#### Syntax

    void setBytes(
       const Bytes& bytes);

| Parameter | Description                    |
|:----------|:-------------------------------|
| `bytes`   | Data content of the `Message`. |

### 13.19.20 setCorrelationId()

Specifies the identification string. This parameter is set at enqueuing time by the `Producer`. Messages can be dequeued with this id. The id can contain wildcard characters.

#### Syntax

    void setCorrelationId(
       const string& id);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `id`      | The id; upper limit of `128` bytes. |

### 13.19.21 setDelay()

Specifies the time (in seconds) to delay the enqueued `Message`. After the delay ends, the `Message` is available for dequeuing.

Note that dequeuing by `msgid` overrides the delay specification. A `Message` enqueued with delay is in the `WAITING` state. Delay is set by the producer of the `Message`.

#### Syntax

    void setDelay(
       int delay);

| Parameter | Description |
|:----------|:------------|
| `delay`   | The delay.  |

### 13.19.22 setExceptionQueueName()

Specifies the name of the queue to which the `Message` object is moved if it cannot be processed successfully. The queue name must be valid.

Note that if the exception queue does not exist at the time of the move, the `Message `is moved to the default exception queue associated with the queue table; a warning is logged in the alert log.

Also note that if the default exception queue is used, the parameter returns a `NULL` value at enqueuing time; the attribute must refer to a valid queue name.

#### Syntax

    void setExceptionQueueName(
       const string& queue);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `queue`   | The name of the exception queue. |

### 13.19.23 setExpiration()

Specifies the duration time (in seconds) that the `Message` object is available for dequeuing. A `Message` expires after this time.

#### Syntax

    void setExpiration(
       int exp);

| Parameter | Description                 |
|:----------|:----------------------------|
| `exp`     | The duration of expiration. |

### 13.19.24 setNull()

Sets the `Message` object to `NULL`. Before the `Connection` is destroyed by the [terminateConnection()](environment-class.md) call of the [Environment Class](environment-class.md), all `Message` objects must be set to `NULL`.

#### Syntax

    void setNull();

### 13.19.25 setObject()

Specifies object payload of the `Message`.

#### Syntax

    void setObject(
       PObject& pobj);

| Parameter | Description         |
|:----------|:--------------------|
| `pobj`    | Content of the data |

### 13.19.26 setOriginalMessageId()

Sets the Id of the last queue that generated the message, when a message is propagated from one queue to another.

#### Syntax

    void setOriginalMessageId(
       const Bytes& queue);

| Parameter | Description     |
|:----------|:----------------|
| `queue`   | The last queue. |

### 13.19.27 setPriority()

Specifies the priority of the `Message` object. This property is set during enqueuing time, and can be negative. Default is `0`.

#### Syntax

    void setPriority(
       int priority);

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `priority` | The priority of the `Message`. |

### 13.19.28 setRecipientList()

Specifies the list of `Agent`s for whom the `Message` is intended. These recipients are not identical to subscribers of the queue. The property is set during enqueuing. All `Agent`s in the list must be valid. The recipient list overrides the default subscriber list.

#### Syntax

    void setRecipientList(
       vector<Agent>& agentList);

| Parameter   | Description           |
|:------------|:----------------------|
| `agentList` | The list of `Agent`s. |

### 13.19.29 setSenderId()

Specifies the sender of the `Message`.

#### Syntax

    void setSenderId(
       const Agent& sender);

| Parameter | Description |
|:----------|:------------|
| `sender`  | Sender id.  |
