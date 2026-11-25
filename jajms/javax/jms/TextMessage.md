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

- [Prev Class](TemporaryTopic.md)
- [Next Class](Topic.md)

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

## Interface TextMessage

- All Superinterfaces:
  [Message](Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsTextMessage](../../oracle/jms/AQjmsTextMessage.md)

  ------------------------------------------------------------------------



      public interface TextMessage
      extends Message

  A `TextMessage` object is used to send a message containing a `java.lang.String`. It inherits from the `Message` interface and adds a text message body.
  This message type can be used to transport text-based messages, including those with XML content.

  When a client receives a `TextMessage`, it is in read-only mode. If a client attempts to write to the message at this point, a `MessageNotWriteableException` is thrown. If `clearBody` is called, the message can now be both read from and written to.

  See Also:
  [`Session.createTextMessage()`](Session.md), [`Session.createTextMessage(String)`](Session.md), [`BytesMessage`](BytesMessage.md), [`MapMessage`](MapMessage.md), [`Message`](Message.md), [`ObjectMessage`](ObjectMessage.md), [`StreamMessage`](StreamMessage.md), `String`

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](Message.md)

      [`DEFAULT_DELIVERY_MODE`](Message.md)`, `[`DEFAULT_PRIORITY`](Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                  |
    |--------------------|-----------------------------------------------------------------------------------------|
    | `java.lang.String` | `getText``()`<br>Gets the string containing this message's data.                        |
    | `void`             | `setText``(java.lang.String string)`<br>Sets the string containing this message's data. |

    - ### Methods inherited from interface javax.jms.[Message](Message.md)

      [`acknowledge`](Message.md)`, `[`clearBody`](Message.md)`, `[`clearProperties`](Message.md)`, `[`getBooleanProperty`](Message.md)`, `[`getByteProperty`](Message.md)`, `[`getDoubleProperty`](Message.md)`, `[`getFloatProperty`](Message.md)`, `[`getIntProperty`](Message.md)`, `[`getJMSCorrelationID`](Message.md)`, `[`getJMSCorrelationIDAsBytes`](Message.md)`, `[`getJMSDeliveryMode`](Message.md)`, `[`getJMSDestination`](Message.md)`, `[`getJMSExpiration`](Message.md)`, `[`getJMSMessageID`](Message.md)`, `[`getJMSPriority`](Message.md)`, `[`getJMSRedelivered`](Message.md)`, `[`getJMSReplyTo`](Message.md)`, `[`getJMSTimestamp`](Message.md)`, `[`getJMSType`](Message.md)`, `[`getLongProperty`](Message.md)`, `[`getObjectProperty`](Message.md)`, `[`getPropertyNames`](Message.md)`, `[`getShortProperty`](Message.md)`, `[`getStringProperty`](Message.md)`, `[`propertyExists`](Message.md)`, `[`setBooleanProperty`](Message.md)`, `[`setByteProperty`](Message.md)`, `[`setDoubleProperty`](Message.md)`, `[`setFloatProperty`](Message.md)`, `[`setIntProperty`](Message.md)`, `[`setJMSCorrelationID`](Message.md)`, `[`setJMSCorrelationIDAsBytes`](Message.md)`, `[`setJMSDeliveryMode`](Message.md)`, `[`setJMSDestination`](Message.md)`, `[`setJMSExpiration`](Message.md)`, `[`setJMSMessageID`](Message.md)`, `[`setJMSPriority`](Message.md)`, `[`setJMSRedelivered`](Message.md)`, `[`setJMSReplyTo`](Message.md)`, `[`setJMSTimestamp`](Message.md)`, `[`setJMSType`](Message.md)`, `[`setLongProperty`](Message.md)`, `[`setObjectProperty`](Message.md)`, `[`setShortProperty`](Message.md)`, `[`setStringProperty`](Message.md)

<!-- -->

- - ### Method Detail

    - #### setText

          void setText(java.lang.String string)
                throws JMSException

      Sets the string containing this message's data.
      Parameters:
      `string` - the `String` containing the message's data

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the text due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### getText

          java.lang.String getText()
                            throws JMSException

      Gets the string containing this message's data. The default value is null.
      Returns:
      the `String` containing the message's data

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the text due to some internal error.

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

- [Prev Class](TemporaryTopic.md)
- [Next Class](Topic.md)

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
