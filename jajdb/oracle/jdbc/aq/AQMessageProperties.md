Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQMessageProperties.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQMessage.md)
- [Next Class](AQMessageProperties.DeliveryMode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.aq

## Interface AQMessageProperties

-

  ------------------------------------------------------------------------



      public interface AQMessageProperties

  This interface contains the message properties such as Correlation, Sender, Delay and Expiration, Recipients, and Priority and Ordering. Some of these properties such as the enqueue timestamp or the count of dequeue attempts cannot be set by the user: they are retrieved from the server during a dequeue operation.
  When enqueuing a new message in a queue, you first need to retrieve a new instance of this interface by calling `AQFactory.createAQMessageProperties()`. Fill the message properties and then call `AQFactory.createAQMessage(props)` to create a new AQ message with `props` being the message properties. Finally set the payload and then enqueue the message.

  Since:
  11.1

  See Also:
  `AQFactory.createAQMessageProperties`

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                  |
    |-------------------|----------------------------------------------------------------------------|
    | `static class `   | [`AQMessageProperties.DeliveryMode`](AQMessageProperties.DeliveryMode.md)  |
    | `static class `   | [`AQMessageProperties.MessageState`](AQMessageProperties.MessageState.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                     |
    |-------------------|-----------------------------------------------------------|
    | `static int`      | `MESSAGE_NO_DELAY`<br>Possible value for setDelay.        |
    | `static int`      | `MESSAGE_NO_EXPIRATION`<br>The message will never expire. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                              |
    |------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getCorrelation``()`                                                                                                                                                                                                                                |
    | `int`                                                                                                | `getDelay``()`                                                                                                                                                                                                                                      |
    | [`AQMessageProperties.DeliveryMode`](AQMessageProperties.DeliveryMode.md)                            | `getDeliveryMode``()`<br>After a dequeue operation, call this method to find out if the message was enqueued in a persistent manner or not.                                                                                                         |
    | `int`                                                                                                | `getDequeueAttemptsCount``()`<br>Returns the number of attempts that have been made to dequeue the message.                                                                                                                                         |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `getEnqueueTime``()`<br>Returns the time the message was enqueued.                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getExceptionQueue``()`                                                                                                                                                                                                                             |
    | `int`                                                                                                | `getExpiration``()`                                                                                                                                                                                                                                 |
    | `byte[]`                                                                                             | `getPreviousQueueMessageId``()`<br>The ID of the message in the last queue that generated this message.                                                                                                                                             |
    | `int`                                                                                                | `getPriority``()`                                                                                                                                                                                                                                   |
    | [`AQAgent`](AQAgent.md)`[]`                                                                          | `getRecipientList``()`                                                                                                                                                                                                                              |
    | [`AQAgent`](AQAgent.md)                                                                              | `getSender``()`                                                                                                                                                                                                                                     |
    | [`AQMessageProperties.MessageState`](AQMessageProperties.MessageState.md)                            | `getState``()`<br>Returns the state of the message at the time of the dequeue.                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getTransactionGroup``()`<br>For transaction-grouped queues, this identifies the transaction group of the message.                                                                                                                                  |
    | `void`                                                                                               | `setCorrelation``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` correlation)`<br>Specifies the identification supplied by the producer for a message at enqueuing.                              |
    | `void`                                                                                               | `setDelay``(int delay)`<br>Specifies the number of seconds to delay the enqueued message.                                                                                                                                                           |
    | `void`                                                                                               | `setExceptionQueue``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` exceptionQueue)`<br>Specifies the name of the queue to which the message is moved to if it cannot be processed successfully. |
    | `void`                                                                                               | `setExpiration``(int seconds)`<br>Specifies the expiration of the message.                                                                                                                                                                          |
    | `void`                                                                                               | `setPriority``(int priority)`<br>Specifies the priority of the message.                                                                                                                                                                             |
    | `void`                                                                                               | `setRecipientList``(`[`AQAgent`](AQAgent.md)`[] agents)`<br>This parameter is only valid for queues which allow multiple consumers.                                                                                                                 |
    | `void`                                                                                               | `setSender``(`[`AQAgent`](AQAgent.md)` sender)`<br>Identifies the original sender of a message.                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``()`                                                                                                                                                                                                                                      |

<!-- -->

- - ### Field Detail

    - #### MESSAGE_NO_DELAY

          static final int MESSAGE_NO_DELAY

      Possible value for setDelay. Indicates the message is available for immediate dequeuing.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MESSAGE_NO_EXPIRATION

          static final int MESSAGE_NO_EXPIRATION

      The message will never expire. Can be used for setExpiration().
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getDequeueAttemptsCount

          int getDequeueAttemptsCount()

      Returns the number of attempts that have been made to dequeue the message.

    <!-- -->

    - #### setCorrelation

          void setCorrelation(String correlation)
                       throws SQLException

      Specifies the identification supplied by the producer for a message at enqueuing.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCorrelation

          String getCorrelation()

    <!-- -->

    - #### setDelay

          void setDelay(int delay)
                 throws SQLException

      Specifies the number of seconds to delay the enqueued message. The delay represents the number of seconds after which a message is available for dequeuing. Dequeuing by msgid overrides the delay specification. A message enqueued with delay set will be in the WAITING state, when the delay expires the messages goes to the READY state. DELAY processing requires the queue monitor to be started. Note that delay is set by the producer who enqueues the message.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDelay

          int getDelay()

    <!-- -->

    - #### getEnqueueTime

          Timestamp getEnqueueTime()

      Returns the time the message was enqueued. This value is determined by the system and cannot be set by the user.

    <!-- -->

    - #### setExceptionQueue

          void setExceptionQueue(String exceptionQueue)
                          throws SQLException

      Specifies the name of the queue to which the message is moved to if it cannot be processed successfully. Messages are moved in two cases: If the number of unsuccessful dequeue attempts has exceeded max_retries; or if the message has expired. All messages in the exception queue are in the EXPIRED state. The default is the exception queue associated with the queue table. If the exception queue specified does not exist at the time of the move the message will be moved to the default exception queue associated with the queue table and a warning will be logged in the alert file. If the default exception queue is used, the parameter will return a NULL value at dequeue time. This attribute must refer to a valid queue name.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getExceptionQueue

          String getExceptionQueue()

    <!-- -->

    - #### setExpiration

          void setExpiration(int seconds)
                      throws SQLException

      Specifies the expiration of the message. It determines, in seconds, the duration the message is available for dequeuing. This parameter is an offset from the delay. Expiration processing requires the queue monitor to be running. While waiting for expiration, the message remains in the READY state. If the message is not dequeued before it expires, it will be moved to the exception queue in the EXPIRED state.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getExpiration

          int getExpiration()

    <!-- -->

    - #### getState

          AQMessageProperties.MessageState getState()

      Returns the state of the message at the time of the dequeue. This parameter cannot be set at enqueue time.

    <!-- -->

    - #### setPriority

          void setPriority(int priority)
                    throws SQLException

      Specifies the priority of the message. A smaller number indicates higher priority. The priority can be any number, including negative numbers. The default value is zero.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPriority

          int getPriority()

    <!-- -->

    - #### setRecipientList

          void setRecipientList(AQAgent[] agents)
                         throws SQLException

      This parameter is only valid for queues which allow multiple consumers. The default recipients are the queue subscribers but they can be overriden using this method. This parameter is not returned to a consumer at dequeue time.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRecipientList

          AQAgent[] getRecipientList()

    <!-- -->

    - #### setSender

          void setSender(AQAgent sender)
                  throws SQLException

      Identifies the original sender of a message.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSender

          AQAgent getSender()

    <!-- -->

    - #### getTransactionGroup

          String getTransactionGroup()

      For transaction-grouped queues, this identifies the transaction group of the message. This attribute is populated after a successful dequeueArray() call. All messages in a group have the same value for this attribute. This attribute cannot be used by the enqueueArray() call to set the transaction group for an enqueued message.

    <!-- -->

    - #### getPreviousQueueMessageId

          byte[] getPreviousQueueMessageId()

      The ID of the message in the last queue that generated this message. When a message is propagated from one queue to another, this attribute identifies the ID of the queue from which it was last propagated. When a message has been propagated through multiple queues, this attribute identifies the ID of the message in the last queue that generated this message, not the first queue.

    <!-- -->

    - #### getDeliveryMode

          AQMessageProperties.DeliveryMode getDeliveryMode()

      After a dequeue operation, call this method to find out if the message was enqueued in a persistent manner or not.
      Note that this is set at dequeue time by the driver. There is an enqueue option to enqueue a buffered message.

    <!-- -->

    - #### toString

          String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQMessageProperties.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQMessage.md)
- [Next Class](AQMessageProperties.DeliveryMode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
