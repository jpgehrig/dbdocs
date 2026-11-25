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

- [Prev Class](AdtMessage.md)
- [Next Class](AQjmsBytesMessage.md)

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

## Class AQjmsAdtMessage

- java.lang.Object

- - [oracle.jms.AQjmsMessage](AQjmsMessage.md)

  - - oracle.jms.AQjmsAdtMessage

<!-- -->

- All Implemented Interfaces:
  [Message](../../javax/jms/Message.md), [AdtMessage](AdtMessage.md)

  ------------------------------------------------------------------------



      public class AQjmsAdtMessage
      extends AQjmsMessage
      implements AdtMessage

  This is an Oracle class which implements `oracle.jms.AdtMessage`. Allows use of the JMS api for messages stored in AQ queues containing Oracle ADT payloads.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `clearBody``()`<br>Clear out the message body.                                                                                                                                                                            |
    | `java.lang.Object`                              | `getAdtPayload``()`<br>Get the `CustomDatum`/`ORAData` object containing this Adt message's data **Important:** `CustomDatum` support will be deprecated in a future release.                                             |
    | `boolean`                                       | `getBooleanProperty``(java.lang.String name)`<br>Return the `boolean` property value with the given name.                                                                                                                 |
    | `byte`                                          | `getByteProperty``(java.lang.String name)`<br>Return the `byte` property value with the given name.                                                                                                                       |
    | `double`                                        | `getDoubleProperty``(java.lang.String name)`<br>Return the `double` property value with the given name.                                                                                                                   |
    | `float`                                         | `getFloatProperty``(java.lang.String name)`<br>Return the `float` property value with the given name.                                                                                                                     |
    | `int`                                           | `getIntProperty``(java.lang.String name)`<br>Return the `int` property value with the given name.                                                                                                                         |
    | `java.lang.String`                              | `getJMSMessageID``()`<br>Get the message ID.                                                                                                                                                                              |
    | [`Destination`](../../javax/jms/Destination.md) | `getJMSReplyTo``()`<br>Get where a reply to this message should be sent.                                                                                                                                                  |
    | `long`                                          | `getJMSTimestamp``()`<br>Get the message timestamp.                                                                                                                                                                       |
    | `java.lang.String`                              | `getJMSType``()`<br>Get the message type.                                                                                                                                                                                 |
    | `long`                                          | `getLongProperty``(java.lang.String name)`<br>Return the `long` property value with the given name.                                                                                                                       |
    | `java.lang.Object`                              | `getObjectProperty``(java.lang.String name)`<br>Return the Java object property value with the given name.                                                                                                                |
    | `java.util.Enumeration`                         | `getPropertyNames``()`<br>Return an Enumeration of all the property names.                                                                                                                                                |
    | `short`                                         | `getShortProperty``(java.lang.String name)`<br>Return the `short` property value with the given name.                                                                                                                     |
    | `java.lang.String`                              | `getStringProperty``(java.lang.String name)`<br>Return the `String` property value with the given name.                                                                                                                   |
    | `boolean`                                       | `propertyExists``(java.lang.String name)`<br>Check if a property value exists.                                                                                                                                            |
    | `void`                                          | `setAdtPayload``(oracle.sql.CustomDatum payload)`<br>set the `CustomDatum` object containing this Adt message's data **Important:** `CustomDatum` support (and hence this method) will be deprecated in a future release. |
    | `void`                                          | `setAdtPayload``(oracle.jdbc.OracleData payload)`<br>set the `OracleData` object containing this Adt message's data                                                                                                       |
    | `void`                                          | `setAdtPayload``(oracle.sql.ORAData payload)`<br>set the `ORAData` object containing this Adt message's data                                                                                                              |
    | `void`                                          | `setBooleanProperty``(java.lang.String name, boolean value)`<br>Set a `boolean` property value with the given name into the Message.                                                                                      |
    | `void`                                          | `setByteProperty``(java.lang.String name, byte value)`<br>Set a `byte` property value with the given name into the Message.                                                                                               |
    | `void`                                          | `setDoubleProperty``(java.lang.String name, double value)`<br>Set a `double` property value with the given name into the Message.                                                                                         |
    | `void`                                          | `setFloatProperty``(java.lang.String name, float value)`<br>Set a `float` property value with the given name into the Message.                                                                                            |
    | `void`                                          | `setIntProperty``(java.lang.String name, int value)`<br>Set an `int` property value with the given name into the Message.                                                                                                 |
    | `void`                                          | `setJMSReplyTo``(`[`Destination`](../../javax/jms/Destination.md)` replyTo)`<br>Set where a reply to this message should be sent.                                                                                         |
    | `void`                                          | `setJMSTimestamp``(long timestamp)`<br>Set the message timestamp.                                                                                                                                                         |
    | `void`                                          | `setJMSType``(java.lang.String type)`<br>Set the message type.                                                                                                                                                            |
    | `void`                                          | `setLongProperty``(java.lang.String name, long value)`<br>Set a `long` property value with the given name into the Message.                                                                                               |
    | `void`                                          | `setObjectProperty``(java.lang.String name, java.lang.Object value)`<br>Set a Java object property value with the given name, into the Message.                                                                           |
    | `void`                                          | `setShortProperty``(java.lang.String name, short value)`<br>Set a `short` property value with the given name into the Message.                                                                                            |
    | `void`                                          | `setStringProperty``(java.lang.String name, java.lang.String value)`<br>Set a `String` property value with the given name into the Message.                                                                               |

    - ### Methods inherited from class oracle.jms.[AQjmsMessage](AQjmsMessage.md)

      [`acknowledge`](AQjmsMessage.md)`, `[`clearProperties`](AQjmsMessage.md)`, `[`getAttempts`](AQjmsMessage.md)`, `[`getBodyLength`](AQjmsMessage.md)`, `[`getJMSCorrelationID`](AQjmsMessage.md)`, `[`getJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`getJMSDeliveryMode`](AQjmsMessage.md)`, `[`getJMSDestination`](AQjmsMessage.md)`, `[`getJMSExpiration`](AQjmsMessage.md)`, `[`getJMSMessageIDAsBytes`](AQjmsMessage.md)`, `[`getJMSPriority`](AQjmsMessage.md)`, `[`getJMSRedelivered`](AQjmsMessage.md)`, `[`getSenderID`](AQjmsMessage.md)`, `[`getUserPropertyNames`](AQjmsMessage.md)`, `[`isLargeBody`](AQjmsMessage.md)`, `[`setJMSCorrelationID`](AQjmsMessage.md)`, `[`setJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`setJMSDeliveryMode`](AQjmsMessage.md)`, `[`setJMSDestination`](AQjmsMessage.md)`, `[`setJMSExpiration`](AQjmsMessage.md)`, `[`setJMSMessageID`](AQjmsMessage.md)`, `[`setJMSPriority`](AQjmsMessage.md)`, `[`setJMSRedelivered`](AQjmsMessage.md)`, `[`setSenderID`](AQjmsMessage.md)`, `[`test_getUserProperties`](AQjmsMessage.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`acknowledge`](../../javax/jms/Message.md)`, `[`clearProperties`](../../javax/jms/Message.md)`, `[`getJMSCorrelationID`](../../javax/jms/Message.md)`, `[`getJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`getJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`getJMSDestination`](../../javax/jms/Message.md)`, `[`getJMSExpiration`](../../javax/jms/Message.md)`, `[`getJMSPriority`](../../javax/jms/Message.md)`, `[`getJMSRedelivered`](../../javax/jms/Message.md)`, `[`setJMSCorrelationID`](../../javax/jms/Message.md)`, `[`setJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`setJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`setJMSDestination`](../../javax/jms/Message.md)`, `[`setJMSExpiration`](../../javax/jms/Message.md)`, `[`setJMSMessageID`](../../javax/jms/Message.md)`, `[`setJMSPriority`](../../javax/jms/Message.md)`, `[`setJMSRedelivered`](../../javax/jms/Message.md)

<!-- -->

- - ### Method Detail

    - #### getJMSMessageID

          public java.lang.String getJMSMessageID()
                                           throws JMSException

      Get the message ID. The messageID header field contains a value that uniquely identifies each message sent by a provider. When the send method returns it contains a provider-assigned value.
      Specified by:
      [`getJMSMessageID`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getJMSMessageID`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      the message ID as a string

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the message Id due to internal JMS error.

      See Also:
      [`Message.setJMSMessageID(String)`](../../javax/jms/Message.md), [`MessageProducer.setDisableMessageID(boolean)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### getJMSReplyTo

          public Destination getJMSReplyTo()
                                    throws JMSException

      Get where a reply to this message should be sent.
      Specified by:
      [`getJMSReplyTo`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getJMSReplyTo`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      the destination where replies to this message should be sent (an `AQjmsAgent`)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED` for `AdtMessage`

      See Also:
      [`Message.setJMSReplyTo(Destination)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSReplyTo

          public void setJMSReplyTo(Destination replyTo)
                             throws JMSException

      Set where a reply to this message should be sent.
      Specified by:
      [`setJMSReplyTo`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setJMSReplyTo`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `replyTo` - destination where replies to this message should be sent. Must be an `AQjmsAgent` object (with consumer name and queue/topic address).

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED` for `AdtMessage`

      See Also:
      [`Message.getJMSReplyTo()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSType

          public java.lang.String getJMSType()
                                      throws JMSException

      Get the message type.
      Specified by:
      [`getJMSType`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getJMSType`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      the message type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED` for `AdtMessage`

      See Also:
      [`Message.setJMSType(String)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSType

          public void setJMSType(java.lang.String type)
                          throws JMSException

      Set the message type.
      Specified by:
      [`setJMSType`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setJMSType`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `type` - of the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED` for `AdtMessage`

      See Also:
      [`Message.getJMSType()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSTimestamp

          public long getJMSTimestamp()
                               throws JMSException

      Get the message timestamp. The JMSTimestamp header field contains the time a message was handed off to a provider to be sent. When a message is sent, JMSTimestamp is ignored. When the send is complete - this method will contain the time the message was enqueued.
      Specified by:
      [`getJMSTimestamp`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getJMSTimestamp`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      timestamp (format is a normal Java millis time value)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the Timestamp

      See Also:
      [`Message.setJMSTimestamp(long)`](../../javax/jms/Message.md), [`MessageProducer.setDisableMessageTimestamp(boolean)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### setJMSTimestamp

          public void setJMSTimestamp(long timestamp)
                               throws JMSException

      Set the message timestamp. Providers set this field when a message is sent.
      Specified by:
      [`setJMSTimestamp`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setJMSTimestamp`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `timestamp` - the timestamp for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the timestamp due to some internal JMS error.

      See Also:
      [`Message.getJMSTimestamp()`](../../javax/jms/Message.md)

    <!-- -->

    - #### propertyExists

          public boolean propertyExists(java.lang.String name)
                                 throws JMSException

      Check if a property value exists.
      Specified by:
      [`propertyExists`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`propertyExists`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the property to test

      Returns:
      `true` if the property does exist.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to check if property exists due to some internal JMS error.

    <!-- -->

    - #### getBooleanProperty

          public boolean getBooleanProperty(java.lang.String name)
                                     throws JMSException

      Return the `boolean` property value with the given name.
      Specified by:
      [`getBooleanProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getBooleanProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `boolean` property

      Returns:
      the `boolean` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getByteProperty

          public byte getByteProperty(java.lang.String name)
                               throws JMSException

      Return the `byte` property value with the given name.
      Specified by:
      [`getByteProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getByteProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `byte` property

      Returns:
      the `byte` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getShortProperty

          public short getShortProperty(java.lang.String name)
                                 throws JMSException

      Return the `short` property value with the given name.
      Specified by:
      [`getShortProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getShortProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `short` property

      Returns:
      the `short` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getIntProperty

          public int getIntProperty(java.lang.String name)
                             throws JMSException

      Return the `int` property value with the given name.
      Specified by:
      [`getIntProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getIntProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `int` property

      Returns:
      the `int` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getLongProperty

          public long getLongProperty(java.lang.String name)
                               throws JMSException

      Return the `long` property value with the given name.
      Specified by:
      [`getLongProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getLongProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `long` property

      Returns:
      the `long` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getFloatProperty

          public float getFloatProperty(java.lang.String name)
                                 throws JMSException

      Return the `float` property value with the given name.
      Specified by:
      [`getFloatProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getFloatProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `float` property

      Returns:
      the `float` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getDoubleProperty

          public double getDoubleProperty(java.lang.String name)
                                   throws JMSException

      Return the `double` property value with the given name.
      Specified by:
      [`getDoubleProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getDoubleProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `double` property

      Returns:
      the `double` property value with the given name.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getStringProperty

          public java.lang.String getStringProperty(java.lang.String name)
                                             throws JMSException

      Return the `String` property value with the given name.
      Specified by:
      [`getStringProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getStringProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `String` property

      Returns:
      the `String` property value with the given name. If there is no property by this name, a `null` value is returned.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getObjectProperty

          public java.lang.Object getObjectProperty(java.lang.String name)
                                             throws JMSException

      Return the Java object property value with the given name.
      Note that this method can be used to return in objectified format, an object that had been stored as a property in the Message with the equivalent `setObject` method call, or it's equivalent primitive set\<type\> method.

      Specified by:
      [`getObjectProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getObjectProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the Java object property

      Returns:
      the Java object property value with the given name, in objectified format (ie. if it set as an `int`, then a `Integer` is returned). If there is no property by this name, a `null` value is returned.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property due to some internal JMS error.

    <!-- -->

    - #### getPropertyNames

          public java.util.Enumeration getPropertyNames()
                                                 throws JMSException

      Return an Enumeration of all the property names.
      Specified by:
      [`getPropertyNames`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`getPropertyNames`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      an enumeration of all the names of property values.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the property names due to some internal JMS error.

    <!-- -->

    - #### setBooleanProperty

          public void setBooleanProperty(java.lang.String name,
                                         boolean value)
                                  throws JMSException

      Set a `boolean` property value with the given name into the Message.
      Specified by:
      [`setBooleanProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setBooleanProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `boolean` property

      `value` - the `boolean` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setByteProperty

          public void setByteProperty(java.lang.String name,
                                      byte value)
                               throws JMSException

      Set a `byte` property value with the given name into the Message.
      Specified by:
      [`setByteProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setByteProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `byte` property

      `value` - the `byte` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setShortProperty

          public void setShortProperty(java.lang.String name,
                                       short value)
                                throws JMSException

      Set a `short` property value with the given name into the Message.
      Specified by:
      [`setShortProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setShortProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `short` property

      `value` - the `short` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setIntProperty

          public void setIntProperty(java.lang.String name,
                                     int value)
                              throws JMSException

      Set an `int` property value with the given name into the Message.
      Specified by:
      [`setIntProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setIntProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `int` property

      `value` - the `int` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setLongProperty

          public void setLongProperty(java.lang.String name,
                                      long value)
                               throws JMSException

      Set a `long` property value with the given name into the Message.
      Specified by:
      [`setLongProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setLongProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `long` property

      `value` - the `long` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setFloatProperty

          public void setFloatProperty(java.lang.String name,
                                       float value)
                                throws JMSException

      Set a `float` property value with the given name into the Message.
      Specified by:
      [`setFloatProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setFloatProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `float` property

      `value` - the `float` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setDoubleProperty

          public void setDoubleProperty(java.lang.String name,
                                        double value)
                                 throws JMSException

      Set a `double` property value with the given name into the Message.
      Specified by:
      [`setDoubleProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setDoubleProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `double` property

      `value` - the `double` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setStringProperty

          public void setStringProperty(java.lang.String name,
                                        java.lang.String value)
                                 throws JMSException

      Set a `String` property value with the given name into the Message.
      Specified by:
      [`setStringProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setStringProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the `String` property

      `value` - the `String` property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setObjectProperty

          public void setObjectProperty(java.lang.String name,
                                        java.lang.Object value)
                                 throws JMSException

      Set a Java object property value with the given name, into the Message.
      Note that this method only works for the objectified primitive object types (`Integer`, `Double`, `Long` ...) and `String`'s.

      Specified by:
      [`setObjectProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`setObjectProperty`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Parameters:
      `name` - the name of the Java object property.

      `value` - the Java object property value to set in the Message.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the property due to some internal JMS error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if object is invalid

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Clear out the message body. All other parts of the message are left untouched.
      Specified by:
      [`clearBody`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`clearBody`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to due to some internal JMS error.

    <!-- -->

    - #### setAdtPayload

          public void setAdtPayload(oracle.sql.CustomDatum payload)
                             throws JMSException

      Description copied from interface: [`AdtMessage`](AdtMessage.md)
      set the `CustomDatum` object containing this Adt message's data
      **Important:** `CustomDatum` support (and hence this method) will be deprecated in a future release.

      Use setAdtPayload (OracleData payload) instead.

      Specified by:
      [`setAdtPayload`](AdtMessage.md) in interface [`AdtMessage`](AdtMessage.md)

      Parameters:
      `payload` - the message's data (the object must implement the `CustomDatum` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

      See Also:
      [`AdtMessage.setAdtPayload(OracleData)`](AdtMessage.md)

    <!-- -->

    - #### setAdtPayload

          public void setAdtPayload(oracle.jdbc.OracleData payload)
                             throws JMSException

      Description copied from interface: [`AdtMessage`](AdtMessage.md)
      set the `OracleData` object containing this Adt message's data
      Specified by:
      [`setAdtPayload`](AdtMessage.md) in interface [`AdtMessage`](AdtMessage.md)

      Parameters:
      `payload` - the message's data (the object must implement the `ORAData` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

    <!-- -->

    - #### setAdtPayload

          public void setAdtPayload(oracle.sql.ORAData payload)
                             throws JMSException

      Description copied from interface: [`AdtMessage`](AdtMessage.md)
      set the `ORAData` object containing this Adt message's data
      Specified by:
      [`setAdtPayload`](AdtMessage.md) in interface [`AdtMessage`](AdtMessage.md)

      Parameters:
      `payload` - the message's data (the object must implement the `ORAData` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

    <!-- -->

    - #### getAdtPayload

          public java.lang.Object getAdtPayload()
                                         throws JMSException

      Description copied from interface: [`AdtMessage`](AdtMessage.md)
      Get the `CustomDatum`/`ORAData` object containing this Adt message's data
      **Important:** `CustomDatum` support will be deprecated in a future release.

      Specified by:
      [`getAdtPayload`](AdtMessage.md) in interface [`AdtMessage`](AdtMessage.md)

      Returns:
      the object containing this message's data

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get object due to some internal JMS error.

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

- [Prev Class](AdtMessage.md)
- [Next Class](AQjmsBytesMessage.md)

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
