Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](MessageProducer.md)
- [Next Class](Queue.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

javax.jms

## Interface ObjectMessage

- All Superinterfaces:
  [Message](Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsObjectMessage](../../oracle/jms/AQjmsObjectMessage.md)

  ------------------------------------------------------------------------



      public interface ObjectMessage
      extends Message

  An `ObjectMessage` object is used to send a message that contains a serializable object in the Java programming language ("Java object"). It inherits from the `Message` interface and adds a body containing a single reference to an object. Only `Serializable` Java objects can be used.
  If a collection of Java objects must be sent, one of the `Collection` classes provided since JDK 1.2 can be used.

  When a client receives an `ObjectMessage`, it is in read-only mode. If a client attempts to write to the message at this point, a `MessageNotWriteableException` is thrown. If `clearBody` is called, the message can now be both read from and written to.

  See Also:
  [`Session.createObjectMessage()`](Session.md), [`Session.createObjectMessage(Serializable)`](Session.md), [`BytesMessage`](BytesMessage.md), [`MapMessage`](MapMessage.md), [`Message`](Message.md), [`StreamMessage`](StreamMessage.md), [`TextMessage`](TextMessage.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](Message.md)

      [`DEFAULT_DELIVERY_MODE`](Message.md)`, `[`DEFAULT_PRIORITY`](Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type      | Method and Description                                                                                     |
    |------------------------|------------------------------------------------------------------------------------------------------------|
    | `java.io.Serializable` | `getObject``()`<br>Gets the serializable object containing this message's data.                            |
    | `void`                 | `setObject``(java.io.Serializable object)`<br>Sets the serializable object containing this message's data. |

    - ### Methods inherited from interface javax.jms.[Message](Message.md)

      [`acknowledge`](Message.md)`, `[`clearBody`](Message.md)`, `[`clearProperties`](Message.md)`, `[`getBooleanProperty`](Message.md)`, `[`getByteProperty`](Message.md)`, `[`getDoubleProperty`](Message.md)`, `[`getFloatProperty`](Message.md)`, `[`getIntProperty`](Message.md)`, `[`getJMSCorrelationID`](Message.md)`, `[`getJMSCorrelationIDAsBytes`](Message.md)`, `[`getJMSDeliveryMode`](Message.md)`, `[`getJMSDestination`](Message.md)`, `[`getJMSExpiration`](Message.md)`, `[`getJMSMessageID`](Message.md)`, `[`getJMSPriority`](Message.md)`, `[`getJMSRedelivered`](Message.md)`, `[`getJMSReplyTo`](Message.md)`, `[`getJMSTimestamp`](Message.md)`, `[`getJMSType`](Message.md)`, `[`getLongProperty`](Message.md)`, `[`getObjectProperty`](Message.md)`, `[`getPropertyNames`](Message.md)`, `[`getShortProperty`](Message.md)`, `[`getStringProperty`](Message.md)`, `[`propertyExists`](Message.md)`, `[`setBooleanProperty`](Message.md)`, `[`setByteProperty`](Message.md)`, `[`setDoubleProperty`](Message.md)`, `[`setFloatProperty`](Message.md)`, `[`setIntProperty`](Message.md)`, `[`setJMSCorrelationID`](Message.md)`, `[`setJMSCorrelationIDAsBytes`](Message.md)`, `[`setJMSDeliveryMode`](Message.md)`, `[`setJMSDestination`](Message.md)`, `[`setJMSExpiration`](Message.md)`, `[`setJMSMessageID`](Message.md)`, `[`setJMSPriority`](Message.md)`, `[`setJMSRedelivered`](Message.md)`, `[`setJMSReplyTo`](Message.md)`, `[`setJMSTimestamp`](Message.md)`, `[`setJMSType`](Message.md)`, `[`setLongProperty`](Message.md)`, `[`setObjectProperty`](Message.md)`, `[`setShortProperty`](Message.md)`, `[`setStringProperty`](Message.md)

<!-- -->

- - ### Method Detail

    - #### setObject

          void setObject(java.io.Serializable object)
                  throws JMSException

      Sets the serializable object containing this message's data. It is important to note that an `ObjectMessage` contains a snapshot of the object at the time `setObject()` is called; subsequent modifications of the object will have no effect on the `ObjectMessage` body.
      Parameters:
      `object` - the message's data

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the object due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if object serialization fails.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### getObject

          java.io.Serializable getObject()
                                  throws JMSException

      Gets the serializable object containing this message's data. The default value is null.
      Returns:
      the serializable object containing this message's data

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the object due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if object deserialization fails.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](MessageProducer.md)
- [Next Class](Queue.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
