The `Producer` enqueues `Message`s into a queue and defines the enqueue options.

Table 13-33 Enumerated Values Used by Producer Class

| Attribute         | Options                                                                                                                                                                                                                                                                                                           |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EnqueueSequence` | • `ENQ_BEFORE` indicates that the message is enqueued before the message specified by the related message id.<br>• `ENQ_TOP` indicates that the message is enqueued before any other messages.                                                                                                                    |
| `Visibility`      | • `ENQ_IMMEDIATE` indicates that the enqueue is not part of the current transaction. The operation constitutes a transaction of its own.<br>• `ENQ_ON_COMMIT` indicates that the enqueue is part of the current transaction. The operation is complete when the transaction commits. This is the default setting. |

Table 13-34 Summary of Producer Methods

| Method                 | Summary                                                                                                          |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------|
| Producer()             | `Producer` class constructor.                                                                                    |
| getQueueName()         | Retrieves the name of a queue on which the `Message`s is enqueued.                                               |
| getRelativeMessageId() | Retrieves the `Message` id that is referenced in a sequence deviation operation.                                 |
| getSequenceDeviation() | Retrieves information regarding whether the `Message` should be dequeued ahead of other `Message`s in the queue. |
| getTransformation()    | Retrieves the transformation applied before a `Message` is enqueued.                                             |
| getVisibility()        | Retrieves the transactional behavior of the enqueue request.                                                     |
| isNull()               | Tests whether the `Producer` is `NULL`.                                                                          |
| send()                 | Enqueues and sends a `Message`.                                                                                  |
| operator=()            | Assignment operator for `Producer`.                                                                              |
| setNull()              | Frees memory if the scope of the `Producer `extends beyond the `Connection` on which it was created.             |
| setQueueName()         | Specifies the name of a queue on which the `Message`s is enqueued.                                               |
| setRelativeMessageId() | Specifies the `Message` id to be referenced in the sequence deviation operation.                                 |
| setSequenceDeviation() | Specifies whether `Message` should be dequeued before other `Message`s in the queue.                             |
| setTransformation()    | Specifies transformation applied before enqueuing a `Message`.                                                   |
| setVisibility()        | Specifies transaction behavior of the enqueue request.                                                           |

### 13.24.1 Producer()

`Producer` object constructor.

| Syntax                                                                    | Description                                                                 |
|:--------------------------------------------------------------------------|:----------------------------------------------------------------------------|
| `Producer(`<br>`   const Connection *conn);`                              | Creates a `Producer` object with the specified `Connection`.                |
| `Producer(`<br>`   const Connection *conn,`<br>`   const string& queue);` | Creates a `Producer` object with the specified `Connection` and queue name. |

| Parameter | Description                                          |
|:----------|:-----------------------------------------------------|
| `conn`    | The connection of the new `Producer` object.         |
| `queue`   | The queue that is used by the new `Producer` object. |

### 13.24.2 getQueueName()

Retrieves the name of a queue on which the `Message`s are enqueued.

#### Syntax

    string getQueueName() cosnt;

### 13.24.3 getRelativeMessageId()

Retrieves the `Message` id that is referenced in a sequence deviation operation. Used only if a sequence deviation is specified; ignored otherwise.

#### Syntax

    Bytes getRelativeMessageId() const;

### 13.24.4 getSequenceDeviation()

Retrieves information regarding whether the `Message` should be dequeued ahead of other `Message`s in the queue. Valid return values are `ENQ_BEFORE` and `ENQ_TOP`, as defined in Table 13-33.

#### Syntax

    EnqueueSequence getSequenceDeviation() const;

### 13.24.5 getTransformation()

Retrieves the transformation applied before a `Message` is enqueued.

#### Syntax

    string getTransformation() const;

### 13.24.6 getVisibility()

Retrieves the transactional behavior of the enqueue request. `Visibility` is defined in Table 13-33.

#### Syntax

    Visibility getVisibility() const;

### 13.24.7 isNull()

Tests whether the `Producer` is `NULL`. If the `Producer` is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.24.8 operator=()

The assignment operator for `Producer`.

#### Syntax

    void operator=(
       const Producer& prod);

| Parameter | Description             |
|:----------|:------------------------|
| `prod`    | The original `Producer` |

### 13.24.9 send()

Enqueues and sends a `Message`.

| Syntax                                                      | Description                                                                 |
|:------------------------------------------------------------|:----------------------------------------------------------------------------|
| `Bytes send(`<br>`   Message& msg);`                        | Used when `queueName` has been previously set by the setQueueName() method. |
| `Bytes send(`<br>`   Message& msg,`<br>`   string& queue);` | Enqueue the `Message` to the specified `queueName`.                         |

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `msg`     | The `Message` that is enqueued.            |
| `queue`   | The name of a valid queue in the database. |

### 13.24.10 setNull()

Frees memory associated with the `Producer`. Unless working in inner scope, this call should be made before terminating the `Connection`.

#### Syntax

    void setNull();

### 13.24.11 setQueueName()

Specifies the name of a queue on which the `Message`s are enqueued. Typically used when enqueuing multiple messages to the same queue.

#### Syntax

    void setQueueName(
       const string& queue);

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `queue`   | The name of a valid queue in the database, to which the `Message`s are enqueued. |

### 13.24.12 setRelativeMessageId()

Specifies the `Message` id to be referenced in the sequence deviation operation. If the sequence deviation is not specified, this parameter is ignored. Can be set for each enqueuing of a `Message`.

#### Syntax

    void setRelativeMessageId(
       const Bytes& msgid);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `msgid`   | The id of the relative `Message`. |

### 13.24.13 setSequenceDeviation()

Specifies whether `Message` being enqueued should be dequeued before other `Message`(s) in the queue. Can be set for each enqueuing of a `Message`.

#### Syntax

    void setSequenceDeviation(
       EnqueueSequence option);

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `option`  | The enqueue sequence being set, defined in Table 13-33. |

### 13.24.14 setTransformation()

Specifies transformation function applied before enqueuing the `Message`.

#### Syntax

    void setTransformation(
       string &fName);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `fName`   | SQL transformation function. |

### 13.24.15 setVisibility()

Specifies transaction behavior of the enqueue request. Can be set for each enqueuing of a `Message`.

#### Syntax

    void setVisibility(
       Visibility option);

| Parameter | Description                                          |
|:----------|:-----------------------------------------------------|
| `option`  | Visibility option being set, defined in Table 13-33. |
