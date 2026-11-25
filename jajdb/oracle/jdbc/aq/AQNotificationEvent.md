Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQMessageProperties.MessageState.md)
- [Next Class](AQNotificationEvent.AdditionalEventType.md)

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

## Class AQNotificationEvent

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.util.EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

  - - oracle.jdbc.aq.AQNotificationEvent

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public abstract class AQNotificationEvent
      extends EventObject

  An AQNotificationEvent will be created whenever a new message is enqueued in a queue for which you have registered your interest (see OracleConnection.registerAQNotification).
  The AQNotificationEvent provides information about the new message that has been enqueued.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                    |
    |-------------------|------------------------------------------------------------------------------------------|
    | `static class `   | [`AQNotificationEvent.AdditionalEventType`](AQNotificationEvent.AdditionalEventType.md)  |
    | `static class `   | [`AQNotificationEvent.EventType`](AQNotificationEvent.EventType.md)                      |

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`source`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#source)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                        |
    |-------------|------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `AQNotificationEvent``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` source)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                          | Method and Description                                                                                                                                                         |
    |------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`AQNotificationEvent.AdditionalEventType`](AQNotificationEvent.AdditionalEventType.md)         | `getAdditionalEventType``()`<br>Retrieve the additional event type.                                                                                                            |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getConnectionInformation``()`<br>Retrieves a description of the TCP connection on which the notification was received.                                                        |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getConsumerName``()`<br>Retrieves the name of the consumer.                                                                                                                   |
    | `abstract `[`AQNotificationEvent.EventType`](AQNotificationEvent.EventType.md)                             | `getEventType``()`<br>Retrieve the event type.                                                                                                                                 |
    | `abstract byte[]`                                                                                          | `getMessageId``()`<br>Retrieves the ID of the new message.                                                                                                                     |
    | `abstract `[`AQMessageProperties`](AQMessageProperties.md)                                                 | `getMessageProperties``()`<br>Retrieves the properties of the new message.                                                                                                     |
    | `abstract byte[]`                                                                                          | `getPayload``()`<br>Retrieves the payload of the new message.                                                                                                                  |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getQueueName``()`<br>Retrieves the name of the queue.                                                                                                                         |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getRegistration``()`<br>Retrieves the registration name which is the name that you provided when you registered for AQ notification with the `registerAQNotification` method. |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`                                                                                                                                                                 |

    - ### Methods inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`getSource`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#getSource__)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### AQNotificationEvent

          protected AQNotificationEvent(Object source)

  <!-- -->

  - ### Method Detail

    - #### getMessageProperties

          public abstract AQMessageProperties getMessageProperties()
                                                            throws SQLException

      Retrieves the properties of the new message.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRegistration

          public abstract String getRegistration()
                                          throws SQLException

      Retrieves the registration name which is the name that you provided when you registered for AQ notification with the `registerAQNotification` method.
      In the case of a single consumer queue, the registration name is the name of the queue whereas in the case of a multi-consumer queue, it's the name of the queue plus the name of the consumer ("SCOTT.MY_QUEUE:RECEIVER").

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPayload

          public abstract byte[] getPayload()
                                     throws SQLException

      Retrieves the payload of the new message. Note that this feature only works with RAW queues and that it needs to be activated with the OracleConnection.NTF_AQ_PAYLOAD option during registration.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getQueueName

          public abstract String getQueueName()
                                       throws SQLException

      Retrieves the name of the queue.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMessageId

          public abstract byte[] getMessageId()
                                       throws SQLException

      Retrieves the ID of the new message.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConsumerName

          public abstract String getConsumerName()
                                          throws SQLException

      Retrieves the name of the consumer. In the case of a multi-consumer queue, this retrieves the name of the consumer upon which you register for AQ notification.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionInformation

          public abstract String getConnectionInformation()

      Retrieves a description of the TCP connection on which the notification was received.

    <!-- -->

    - #### getEventType

          public abstract AQNotificationEvent.EventType getEventType()

      Retrieve the event type.

    <!-- -->

    - #### getAdditionalEventType

          public abstract AQNotificationEvent.AdditionalEventType getAdditionalEventType()

      Retrieve the additional event type.

    <!-- -->

    - #### toString

          public abstract String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#toString__) in class [`EventObject`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQMessageProperties.MessageState.md)
- [Next Class](AQNotificationEvent.AdditionalEventType.md)

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
