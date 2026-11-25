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

- [Prev Class](AQjmsStreamMessage.md)
- [Next Class](AQjmsTopicBrowser.md)

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

oracle.jms

## Class AQjmsTextMessage

- java.lang.Object

- - [oracle.jms.AQjmsMessage](AQjmsMessage.md)

  - - oracle.jms.AQjmsTextMessage

<!-- -->

- All Implemented Interfaces:
  [Message](../../javax/jms/Message.md), [TextMessage](../../javax/jms/TextMessage.md)

  ------------------------------------------------------------------------



      public class AQjmsTextMessage
      extends AQjmsMessage
      implements TextMessage

  This is an Oracle class which implements `javax.jms.TextMessage`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                  |
    |--------------------|-----------------------------------------------------------------------------------------|
    | `void`             | `clearBody``()`<br>Clears out the message body.                                         |
    | `java.lang.String` | `getText``()`<br>Gets the string containing this message's data.                        |
    | `void`             | `setText``(java.lang.String string)`<br>Sets the string containing this message's data. |

    - ### Methods inherited from class oracle.jms.[AQjmsMessage](AQjmsMessage.md)

      [`acknowledge`](AQjmsMessage.md)`, `[`clearProperties`](AQjmsMessage.md)`, `[`getAttempts`](AQjmsMessage.md)`, `[`getBodyLength`](AQjmsMessage.md)`, `[`getBooleanProperty`](AQjmsMessage.md)`, `[`getByteProperty`](AQjmsMessage.md)`, `[`getDoubleProperty`](AQjmsMessage.md)`, `[`getFloatProperty`](AQjmsMessage.md)`, `[`getIntProperty`](AQjmsMessage.md)`, `[`getJMSCorrelationID`](AQjmsMessage.md)`, `[`getJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`getJMSDeliveryMode`](AQjmsMessage.md)`, `[`getJMSDestination`](AQjmsMessage.md)`, `[`getJMSExpiration`](AQjmsMessage.md)`, `[`getJMSMessageID`](AQjmsMessage.md)`, `[`getJMSMessageIDAsBytes`](AQjmsMessage.md)`, `[`getJMSPriority`](AQjmsMessage.md)`, `[`getJMSRedelivered`](AQjmsMessage.md)`, `[`getJMSReplyTo`](AQjmsMessage.md)`, `[`getJMSTimestamp`](AQjmsMessage.md)`, `[`getJMSType`](AQjmsMessage.md)`, `[`getLongProperty`](AQjmsMessage.md)`, `[`getObjectProperty`](AQjmsMessage.md)`, `[`getPropertyNames`](AQjmsMessage.md)`, `[`getSenderID`](AQjmsMessage.md)`, `[`getShortProperty`](AQjmsMessage.md)`, `[`getStringProperty`](AQjmsMessage.md)`, `[`getUserPropertyNames`](AQjmsMessage.md)`, `[`isLargeBody`](AQjmsMessage.md)`, `[`propertyExists`](AQjmsMessage.md)`, `[`setBooleanProperty`](AQjmsMessage.md)`, `[`setByteProperty`](AQjmsMessage.md)`, `[`setDoubleProperty`](AQjmsMessage.md)`, `[`setFloatProperty`](AQjmsMessage.md)`, `[`setIntProperty`](AQjmsMessage.md)`, `[`setJMSCorrelationID`](AQjmsMessage.md)`, `[`setJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`setJMSDeliveryMode`](AQjmsMessage.md)`, `[`setJMSDestination`](AQjmsMessage.md)`, `[`setJMSExpiration`](AQjmsMessage.md)`, `[`setJMSMessageID`](AQjmsMessage.md)`, `[`setJMSPriority`](AQjmsMessage.md)`, `[`setJMSRedelivered`](AQjmsMessage.md)`, `[`setJMSReplyTo`](AQjmsMessage.md)`, `[`setJMSTimestamp`](AQjmsMessage.md)`, `[`setJMSType`](AQjmsMessage.md)`, `[`setLongProperty`](AQjmsMessage.md)`, `[`setObjectProperty`](AQjmsMessage.md)`, `[`setSenderID`](AQjmsMessage.md)`, `[`setShortProperty`](AQjmsMessage.md)`, `[`setStringProperty`](AQjmsMessage.md)`, `[`test_getUserProperties`](AQjmsMessage.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`acknowledge`](../../javax/jms/Message.md)`, `[`clearProperties`](../../javax/jms/Message.md)`, `[`getBooleanProperty`](../../javax/jms/Message.md)`, `[`getByteProperty`](../../javax/jms/Message.md)`, `[`getDoubleProperty`](../../javax/jms/Message.md)`, `[`getFloatProperty`](../../javax/jms/Message.md)`, `[`getIntProperty`](../../javax/jms/Message.md)`, `[`getJMSCorrelationID`](../../javax/jms/Message.md)`, `[`getJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`getJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`getJMSDestination`](../../javax/jms/Message.md)`, `[`getJMSExpiration`](../../javax/jms/Message.md)`, `[`getJMSMessageID`](../../javax/jms/Message.md)`, `[`getJMSPriority`](../../javax/jms/Message.md)`, `[`getJMSRedelivered`](../../javax/jms/Message.md)`, `[`getJMSReplyTo`](../../javax/jms/Message.md)`, `[`getJMSTimestamp`](../../javax/jms/Message.md)`, `[`getJMSType`](../../javax/jms/Message.md)`, `[`getLongProperty`](../../javax/jms/Message.md)`, `[`getObjectProperty`](../../javax/jms/Message.md)`, `[`getPropertyNames`](../../javax/jms/Message.md)`, `[`getShortProperty`](../../javax/jms/Message.md)`, `[`getStringProperty`](../../javax/jms/Message.md)`, `[`propertyExists`](../../javax/jms/Message.md)`, `[`setBooleanProperty`](../../javax/jms/Message.md)`, `[`setByteProperty`](../../javax/jms/Message.md)`, `[`setDoubleProperty`](../../javax/jms/Message.md)`, `[`setFloatProperty`](../../javax/jms/Message.md)`, `[`setIntProperty`](../../javax/jms/Message.md)`, `[`setJMSCorrelationID`](../../javax/jms/Message.md)`, `[`setJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`setJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`setJMSDestination`](../../javax/jms/Message.md)`, `[`setJMSExpiration`](../../javax/jms/Message.md)`, `[`setJMSMessageID`](../../javax/jms/Message.md)`, `[`setJMSPriority`](../../javax/jms/Message.md)`, `[`setJMSRedelivered`](../../javax/jms/Message.md)`, `[`setJMSReplyTo`](../../javax/jms/Message.md)`, `[`setJMSTimestamp`](../../javax/jms/Message.md)`, `[`setJMSType`](../../javax/jms/Message.md)`, `[`setLongProperty`](../../javax/jms/Message.md)`, `[`setObjectProperty`](../../javax/jms/Message.md)`, `[`setShortProperty`](../../javax/jms/Message.md)`, `[`setStringProperty`](../../javax/jms/Message.md)

<!-- -->

- - ### Method Detail

    - #### setText

          public void setText(java.lang.String string)
                       throws JMSException

      Sets the string containing this message's data.
      Specified by:
      [`setText`](../../javax/jms/TextMessage.md) in interface [`TextMessage`](../../javax/jms/TextMessage.md)

      Parameters:
      `string` - the `String` containing the message's data

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to set the text due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### getText

          public java.lang.String getText()
                                   throws JMSException

      Gets the string containing this message's data. The default value is null.
      Specified by:
      [`getText`](../../javax/jms/TextMessage.md) in interface [`TextMessage`](../../javax/jms/TextMessage.md)

      Returns:
      the `String` containing the message's data

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to get the text due to some internal error.

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Clears out the message body. All other parts of the message are left untouched.
      Specified by:
      [`clearBody`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`clearBody`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message body is not cleared due to some error.

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

- [Prev Class](AQjmsStreamMessage.md)
- [Next Class](AQjmsTopicBrowser.md)

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
